---
title: Реализация повторных попыток вызова HTTP с экспоненциальной выдержкой с помощью библиотеки Polly
description: Сведения о том, как обрабатывать сбои HTTP-запросов с помощью Polly и IHttpClientFactory.
ms.date: 01/13/2021
ms.openlocfilehash: 8cffc644d73eaec5019e00c6a83de8635b569cde
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189054"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="d858a-103">Реализация повторных попыток вызова HTTP с экспоненциальной задержкой с помощью IHttpClientFactory и политик Polly</span><span class="sxs-lookup"><span data-stu-id="d858a-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="d858a-104">Рекомендуемый подход к выполнению повторных попыток с экспоненциальной выдержкой заключается в использовании расширенных библиотек .NET, таких как [библиотека Polly](https://github.com/App-vNext/Polly) с открытым кодом.</span><span class="sxs-lookup"><span data-stu-id="d858a-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="d858a-105">Polly — это библиотека .NET, которая предоставляет возможности обеспечения отказоустойчивости и обработки временных сбоев.</span><span class="sxs-lookup"><span data-stu-id="d858a-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="d858a-106">Эти возможности можно реализовать путем применения политик Polly, таких как политики повтора, размыкателя цепи, изоляции отсеков, времени ожидания и отката.</span><span class="sxs-lookup"><span data-stu-id="d858a-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="d858a-107">Polly используется с .NET Framework 4.x, а также .NET Standard 1.0, 1.1 и 2.0 (с поддержкой .NET Core и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="d858a-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core and later).</span></span>

<span data-ttu-id="d858a-108">Ниже показано, как можно использовать повторные HTTP-запросы через Polly с интеграцией `IHttpClientFactory`, как описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d858a-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="d858a-109">**Ссылка на пакеты ASP.NET Core 3.1**</span><span class="sxs-lookup"><span data-stu-id="d858a-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="d858a-110">Решение `IHttpClientFactory` доступно с версии .NET Core 2.1, но мы рекомендуем использовать в проекте последние пакеты ASP.NET Core 3.1 из NuGet.</span><span class="sxs-lookup"><span data-stu-id="d858a-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="d858a-111">Обычно также требуется ссылка на пакет расширения `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="d858a-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="d858a-112">**Настройка клиента с помощью политики повтора Polly в параметрах запуска**</span><span class="sxs-lookup"><span data-stu-id="d858a-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="d858a-113">Как показано в предыдущих разделах, необходимо определить конфигурацию HttpClient именованного или типизированного клиента в стандартном методе Startup.ConfigureServices(...), но теперь вам потребуется добавочный код, указывающий политику для повторных HTTP-запросов с экспоненциальной выдержкой, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="d858a-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="d858a-114">Метод **AddPolicyHandler()** добавляет политики для объектов `HttpClient`, которые вы будете использовать.</span><span class="sxs-lookup"><span data-stu-id="d858a-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="d858a-115">В этом случае он добавляет политику Polly для повторных HTTP-запросов с экспоненциальной задержкой.</span><span class="sxs-lookup"><span data-stu-id="d858a-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="d858a-116">Для реализации более модульного подхода политику повтора HTTP-запросов можно определить в отдельном методе в файле `Startup.cs`, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d858a-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

<span data-ttu-id="d858a-117">С помощью Polly вы определяете политику повтора с числом повторных попыток, конфигурацией экспоненциальной задержки и действиями, которые необходимо выполнить в случае исключения HTTP (например, запись ошибки в журнал).</span><span class="sxs-lookup"><span data-stu-id="d858a-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="d858a-118">В этом случае политика настроена на шесть попыток с экспоненциальной выдержкой, начиная с двух секунд.</span><span class="sxs-lookup"><span data-stu-id="d858a-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="d858a-119">Добавление стратегии обработки колебания задержки в политику повтора</span><span class="sxs-lookup"><span data-stu-id="d858a-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="d858a-120">Обычная политика повтора может влиять на работу системы в случае высокого уровня параллелизма и масштабируемости, а также в условиях интенсивного состязания за ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d858a-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="d858a-121">Чтобы решить проблему с большим числом повторных запросов, поступающих от множества клиентов в случае частичного отказа системы, можно добавить стратегию в отношении колебания задержки в алгоритм или политику повтора.</span><span class="sxs-lookup"><span data-stu-id="d858a-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="d858a-122">Это может повысить общую производительность всей системы благодаря тому, что экспоненциальная задержка становится более случайной.</span><span class="sxs-lookup"><span data-stu-id="d858a-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="d858a-123">При возникновении проблем пики размываются.</span><span class="sxs-lookup"><span data-stu-id="d858a-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="d858a-124">Этот принцип проиллюстрирован в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d858a-124">The principle is illustrated by the following example:</span></span>

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

<span data-ttu-id="d858a-125">Polly предоставляет готовые к работе алгоритмы дрожания с помощью веб-сайта проекта.</span><span class="sxs-lookup"><span data-stu-id="d858a-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d858a-126">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d858a-126">Additional resources</span></span>

- <span data-ttu-id="d858a-127">**Шаблон повтора**</span><span class="sxs-lookup"><span data-stu-id="d858a-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="d858a-128">**Использование Polly и IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="d858a-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="d858a-129">**Polly (библиотека для обеспечения отказоустойчивости .NET и обработки временных сбоев)**</span><span class="sxs-lookup"><span data-stu-id="d858a-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="d858a-130">**Polly: повторная попытка с дрожанием**</span><span class="sxs-lookup"><span data-stu-id="d858a-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="d858a-131">**Марк Брукер (Marc Brooker). Колебания. Оптимизация с помощью случайности**</span><span class="sxs-lookup"><span data-stu-id="d858a-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="d858a-132">[Назад](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[Вперед](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="d858a-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
