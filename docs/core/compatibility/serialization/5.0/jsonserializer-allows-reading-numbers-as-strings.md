---
title: Критическое изменение. Приложения ASP.NET Core поддерживают десериализацию заключенных в кавычки чисел
description: Узнайте о критическом изменении в .NET 5, после которого приложения ASP.NET Core будут успешно выполнять десериализацию чисел, представленных в виде строк JSON, вместо того, чтобы создавать исключение.
ms.date: 10/21/2020
ms.openlocfilehash: bc1531bb9b159bfd9e80eafacafb50aa509973cc
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624153"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a>Приложения ASP.NET Core поддерживают десериализацию заключенных в кавычки чисел

Начиная с версии .NET 5 приложения ASP.NET Core используют параметры десериализации по умолчанию, которые задаются в <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>. Набор параметров <xref:System.Text.Json.JsonSerializerDefaults.Web> включает параметр <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> для <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>. Это изменение означает, что приложения ASP.NET Core будут успешно выполнять десериализацию чисел, представленных в виде строк JSON, вместо того, чтобы создавать исключение.

## <a name="change-description"></a>Описание изменений

В .NET Core версий с 3.0 по 3.1 <xref:System.Text.Json.JsonSerializer> во время десериализации вызывает исключение <xref:System.Text.Json.JsonException>, если в полезных данных JSON обнаруживается число в кавычках. Заключенные в кавычки числа используются для сопоставления с числовыми свойствами в графах объектов. В .NET Core версий с 3.0 по 3.1 числа считываются только из токенов <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType>.

Начиная с версии .NET 5 заключенные в кавычки числа в полезных данных JSON считаются допустимыми по умолчанию для приложений ASP.NET Core. Во время десериализации заключенных в кавычки чисел исключение не создается.

> [!TIP]
>
> - При этом не изменяется поведение для заданного по умолчанию изолированного <xref:System.Text.Json.JsonSerializer> или <xref:System.Text.Json.JsonSerializerOptions>.
> - С технической точки зрения это изменение не является критическим, поскольку оно снижает, а не повышает степень строгости сценария (т. е. в результате этого изменения приведение числа из строки JSON завершается успешно и не приводит к созданию исключения). Тем не менее, это изменение поведения является существенным и затрагивает многие приложения ASP.NET Core, в связи с чем мы приводим его описание.
> - Методы расширения <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> и <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> также используют набор параметров сериализации <xref:System.Text.Json.JsonSerializerDefaults.Web>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="reason-for-change"></a>Причина изменения

Несколько пользователей запросили возможность менее ограничивающей обработки чисел в <xref:System.Text.Json.JsonSerializer>. Это указывает на то, что многие поставщики объектов JSON (например, служб в Интернете) используют заключенные в кавычки числа. Поддержка чтения (десериализации) заключенных в кавычки чисел в приложениях .NET позволяет по умолчанию успешно анализировать эти полезные данные в веб-контексте. Эта конфигурация предоставляется с помощью <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>, что позволяет указывать одни и те же параметры на разных уровнях приложения, например для клиента, сервера и общедоступного уровня.

## <a name="recommended-action"></a>Рекомендованное действие

Если это изменение приводит к нарушениям в работе, например, если в вашем приложении используется строгая обработка чисел для проверки, вы можете включить предыдущее поведение. Присвойте параметру <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> значение <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.

Для приложений MVC и приложений веб-API ASP.NET Core этот параметр можно настроить в `Startup` с помощью следующего кода:

```csharp
services.AddControllers()
   .AddJsonOptions(options => options.JsonSerializerOptions.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
