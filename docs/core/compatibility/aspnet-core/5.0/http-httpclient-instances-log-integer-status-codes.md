---
title: Критическое изменение. HTTP. Экземпляры HttpClient, созданные с помощью целочисленных кодов состояния журнала IHttpClientFactory
description: Сведения о критическом изменении в ASP.NET Core 5.0 — HTTP. Экземпляры HttpClient, созданные с помощью целочисленных кодов состояния журнала IHttpClientFactory
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 59e64c7127a97b1c11587d13803e4a085dbc090b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497688"
---
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="c46b6-103">HTTP. Экземпляры HttpClient, созданные с помощью целочисленных кодов состояния журнала IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="c46b6-103">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="c46b6-104">Экземпляры <xref:System.Net.Http.HttpClient>, создаваемые <xref:System.Net.Http.IHttpClientFactory>, регистрируют коды состояния HTTP как целые числа вместо имен кодов состояния.</span><span class="sxs-lookup"><span data-stu-id="c46b6-104"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c46b6-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c46b6-105">Version introduced</span></span>

<span data-ttu-id="c46b6-106">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="c46b6-106">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c46b6-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="c46b6-107">Old behavior</span></span>

<span data-ttu-id="c46b6-108">Ведение журнала использует текстовые описания кодов состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="c46b6-108">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="c46b6-109">Рассмотрим следующее сообщение журнала:</span><span class="sxs-lookup"><span data-stu-id="c46b6-109">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a><span data-ttu-id="c46b6-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="c46b6-110">New behavior</span></span>

<span data-ttu-id="c46b6-111">Ведение журнала использует целочисленные значения кодов состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="c46b6-111">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="c46b6-112">Рассмотрим следующее сообщение журнала:</span><span class="sxs-lookup"><span data-stu-id="c46b6-112">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a><span data-ttu-id="c46b6-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c46b6-113">Reason for change</span></span>

<span data-ttu-id="c46b6-114">Исходная настройка такого ведения журнала не согласуется с другими частями ASP.NET Core, которые всегда использовали целые значения.</span><span class="sxs-lookup"><span data-stu-id="c46b6-114">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="c46b6-115">Несогласованность усложняет запросы к журналам с помощью структурированных систем ведения журналов, таких как [Elasticsearch](https://www.elastic.co/elasticsearch/).</span><span class="sxs-lookup"><span data-stu-id="c46b6-115">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="c46b6-116">Дополнительный контекст см. в [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="c46b6-116">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="c46b6-117">Целочисленные значения дают больше гибкости по сравнению с текстом, так как позволяют выполнять запросы к диапазонам значений.</span><span class="sxs-lookup"><span data-stu-id="c46b6-117">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="c46b6-118">Рассматривалось добавление еще одного значения журнала для записи целочисленного кода состояния.</span><span class="sxs-lookup"><span data-stu-id="c46b6-118">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="c46b6-119">К сожалению, это могло привести к несогласованности с остальной частью ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c46b6-119">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="c46b6-120">При ведении журнала HttpClient и сервера/хостинга HTTP уже используется одно и то же имя ключа `StatusCode`.</span><span class="sxs-lookup"><span data-stu-id="c46b6-120">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c46b6-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c46b6-121">Recommended action</span></span>

<span data-ttu-id="c46b6-122">Лучшим вариантом является обновление запросов журнала для использования целочисленных значений кодов состояния.</span><span class="sxs-lookup"><span data-stu-id="c46b6-122">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="c46b6-123">Этот вариант может вызвать некоторые трудности при записи запросов в нескольких версиях ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c46b6-123">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="c46b6-124">Однако использование целых чисел для этой цели предоставляет больше возможностей для запросов журналов.</span><span class="sxs-lookup"><span data-stu-id="c46b6-124">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="c46b6-125">Если необходимо обеспечить совместимость со старым поведением и использовать текстовые коды состояния, замените `IHttpClientFactory` собственными:</span><span class="sxs-lookup"><span data-stu-id="c46b6-125">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="c46b6-126">Скопируйте в проект версии .NET Core 3.1 следующих классов:</span><span class="sxs-lookup"><span data-stu-id="c46b6-126">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="c46b6-127">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="c46b6-127">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="c46b6-128">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="c46b6-128">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="c46b6-129">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="c46b6-129">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="c46b6-130">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="c46b6-130">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="c46b6-131">Переименуйте классы, чтобы избежать конфликтов с открытыми типами в пакете NuGet [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http).</span><span class="sxs-lookup"><span data-stu-id="c46b6-131">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="c46b6-132">Замените встроенную реализацию `LoggingHttpMessageHandlerBuilderFilter` собственной в методе `Startup.ConfigureServices` проекта.</span><span class="sxs-lookup"><span data-stu-id="c46b6-132">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="c46b6-133">Пример:</span><span class="sxs-lookup"><span data-stu-id="c46b6-133">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="c46b6-134">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c46b6-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
