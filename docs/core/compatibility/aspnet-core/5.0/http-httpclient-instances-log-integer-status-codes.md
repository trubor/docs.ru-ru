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
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a>HTTP. Экземпляры HttpClient, созданные с помощью целочисленных кодов состояния журнала IHttpClientFactory

Экземпляры <xref:System.Net.Http.HttpClient>, создаваемые <xref:System.Net.Http.IHttpClientFactory>, регистрируют коды состояния HTTP как целые числа вместо имен кодов состояния.

## <a name="version-introduced"></a>Представленная версия

5.0 Предварительная версия 1

## <a name="old-behavior"></a>Старое поведение

Ведение журнала использует текстовые описания кодов состояния HTTP. Рассмотрим следующее сообщение журнала:

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a>Новое поведение

Ведение журнала использует целочисленные значения кодов состояния HTTP. Рассмотрим следующее сообщение журнала:

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a>Причина изменения

Исходная настройка такого ведения журнала не согласуется с другими частями ASP.NET Core, которые всегда использовали целые значения. Несогласованность усложняет запросы к журналам с помощью структурированных систем ведения журналов, таких как [Elasticsearch](https://www.elastic.co/elasticsearch/). Дополнительный контекст см. в [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).

Целочисленные значения дают больше гибкости по сравнению с текстом, так как позволяют выполнять запросы к диапазонам значений.

Рассматривалось добавление еще одного значения журнала для записи целочисленного кода состояния. К сожалению, это могло привести к несогласованности с остальной частью ASP.NET Core. При ведении журнала HttpClient и сервера/хостинга HTTP уже используется одно и то же имя ключа `StatusCode`.

## <a name="recommended-action"></a>Рекомендованное действие

Лучшим вариантом является обновление запросов журнала для использования целочисленных значений кодов состояния. Этот вариант может вызвать некоторые трудности при записи запросов в нескольких версиях ASP.NET Core. Однако использование целых чисел для этой цели предоставляет больше возможностей для запросов журналов.

Если необходимо обеспечить совместимость со старым поведением и использовать текстовые коды состояния, замените `IHttpClientFactory` собственными:

1. Скопируйте в проект версии .NET Core 3.1 следующих классов:

    * [LoggingHttpMessageHandlerBuilderFilter](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [LoggingHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [LoggingScopeHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [HttpHeadersLogValue](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. Переименуйте классы, чтобы избежать конфликтов с открытыми типами в пакете NuGet [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http).

1. Замените встроенную реализацию `LoggingHttpMessageHandlerBuilderFilter` собственной в методе `Startup.ConfigureServices` проекта. Пример:

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

## <a name="affected-apis"></a>Затронутые API

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
