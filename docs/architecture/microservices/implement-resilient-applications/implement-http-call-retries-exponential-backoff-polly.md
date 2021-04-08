---
title: Реализация повторных попыток вызова HTTP с экспоненциальной выдержкой с помощью библиотеки Polly
description: Сведения о том, как обрабатывать сбои HTTP-запросов с помощью Polly и IHttpClientFactory.
ms.date: 01/13/2021
ms.openlocfilehash: cd209aa7f2802ffea80e14f0e3e77cc4fc29b6d5
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122967"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>Реализация повторных попыток вызова HTTP с экспоненциальной задержкой с помощью IHttpClientFactory и политик Polly

Рекомендуемый подход к выполнению повторных попыток с экспоненциальной выдержкой заключается в использовании расширенных библиотек .NET, таких как [библиотека Polly](https://github.com/App-vNext/Polly) с открытым кодом.

Polly — это библиотека .NET, которая предоставляет возможности обеспечения отказоустойчивости и обработки временных сбоев. Эти возможности можно реализовать путем применения политик Polly, таких как политики повтора, размыкателя цепи, изоляции отсеков, времени ожидания и отката. Polly используется с .NET Framework 4.x, а также .NET Standard 1.0, 1.1 и 2.0 (с поддержкой .NET Core и более поздних версий).

Ниже показано, как можно использовать повторные HTTP-запросы через Polly с интеграцией `IHttpClientFactory`, как описано в предыдущем разделе.

**Ссылки на пакеты .NET 5**

Интерфейс `IHttpClientFactory` доступен с версии .NET Core 2.1, но мы рекомендуем использовать в проекте последние пакеты .NET 5 из NuGet. Обычно также требуется ссылка на пакет расширения `Microsoft.Extensions.Http.Polly`.

**Настройка клиента с помощью политики повтора Polly в параметрах запуска**

Как показано в предыдущих разделах, необходимо определить конфигурацию HttpClient именованного или типизированного клиента в стандартном методе Startup.ConfigureServices(...), но теперь вам потребуется добавочный код, указывающий политику для повторных HTTP-запросов с экспоненциальной выдержкой, как показано ниже:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Метод **AddPolicyHandler()** добавляет политики для объектов `HttpClient`, которые вы будете использовать. В этом случае он добавляет политику Polly для повторных HTTP-запросов с экспоненциальной задержкой.

Для реализации более модульного подхода политику повтора HTTP-запросов можно определить в отдельном методе в файле `Startup.cs`, как в следующем примере.

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

С помощью Polly вы определяете политику повтора с числом повторных попыток, конфигурацией экспоненциальной задержки и действиями, которые необходимо выполнить в случае исключения HTTP (например, запись ошибки в журнал). В этом случае политика настроена на шесть попыток с экспоненциальной выдержкой, начиная с двух секунд.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Добавление стратегии обработки колебания задержки в политику повтора

Обычная политика повтора может влиять на работу системы в случае высокого уровня параллелизма и масштабируемости, а также в условиях интенсивного состязания за ресурсы. Чтобы решить проблему с большим числом повторных запросов, поступающих от множества клиентов при частичном отказе системы, можно добавить стратегию в отношении колебания задержки в алгоритм или политику повтора. Эта стратегия может повысить общую производительность всей системы. Как рекомендуется в статье [Polly: повторы с колебаниями задержки](https://github.com/App-vNext/Polly/wiki/Retry-with-jitter), хорошая стратегия должна предусматривать плавный и равномерно распределенный интервал повторов, который применяется с контролируемой средней исходной задержкой повторов на базе экспоненциальной задержки. Такой подход способствует размытию пиков при возникновении проблем. Этот принцип проиллюстрирован в следующем примере.

```csharp

var delay = Backoff.DecorrelatedJitterBackoffV2(medianFirstRetryDelay: TimeSpan.FromSeconds(1), retryCount: 5);

var retryPolicy = Policy
    .Handle<FooException>()
    .WaitAndRetryAsync(delay);
```

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Шаблон повтора**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Использование Polly и IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (библиотека для обеспечения отказоустойчивости .NET и обработки временных сбоев)**  
  <https://github.com/App-vNext/Polly>

- **Polly: повторная попытка с дрожанием**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Марк Брукер (Marc Brooker). Колебания. Оптимизация с помощью случайности**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Назад](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[Вперед](implement-circuit-breaker-pattern.md)
