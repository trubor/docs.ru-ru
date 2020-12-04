---
title: Критическое изменение. Приложения ASP.NET Core поддерживают десериализацию заключенных в кавычки чисел
description: Узнайте о критическом изменении в .NET 5.0, после которого приложения ASP.NET Core будут успешно выполнять десериализацию чисел, представленных в виде строк JSON, вместо того, чтобы создавать исключение.
ms.date: 10/21/2020
ms.openlocfilehash: fc8a4c6638be391c22c7cfb2fc7c216c88377f29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759673"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="41fe6-103">Приложения ASP.NET Core поддерживают десериализацию заключенных в кавычки чисел</span><span class="sxs-lookup"><span data-stu-id="41fe6-103">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="41fe6-104">Начиная с версии .NET 5.0, приложения ASP.NET Core используют параметры десериализации по умолчанию, которые задаются в <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-104">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41fe6-105">Набор параметров <xref:System.Text.Json.JsonSerializerDefaults.Web> включает параметр <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> для <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-105">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41fe6-106">Это изменение означает, что приложения ASP.NET Core будут успешно выполнять десериализацию чисел, представленных в виде строк JSON, вместо того, чтобы создавать исключение.</span><span class="sxs-lookup"><span data-stu-id="41fe6-106">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings instead of throwing an exception.</span></span>

## <a name="change-description"></a><span data-ttu-id="41fe6-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="41fe6-107">Change description</span></span>

<span data-ttu-id="41fe6-108">В .NET Core версий с 3.0 по 3.1 <xref:System.Text.Json.JsonSerializer> во время десериализации вызывает исключение <xref:System.Text.Json.JsonException>, если в полезных данных JSON обнаруживается число в кавычках.</span><span class="sxs-lookup"><span data-stu-id="41fe6-108">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="41fe6-109">Заключенные в кавычки числа используются для сопоставления с числовыми свойствами в графах объектов.</span><span class="sxs-lookup"><span data-stu-id="41fe6-109">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="41fe6-110">В .NET Core версий с 3.0 по 3.1 числа считываются только из токенов <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-110">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="41fe6-111">Начиная с версии .NET 5.0, заключенные в кавычки числа в полезных данных JSON считаются допустимыми по умолчанию для приложений ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="41fe6-111">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="41fe6-112">Во время десериализации заключенных в кавычки чисел исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="41fe6-112">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="41fe6-113">При этом не изменяется поведение для заданного по умолчанию изолированного <xref:System.Text.Json.JsonSerializer> или <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-113">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="41fe6-114">С технической точки зрения это изменение не является критическим, поскольку оно снижает, а не повышает степень строгости сценария (т. е. в результате этого изменения приведение числа из строки JSON завершается успешно и не приводит к созданию исключения).</span><span class="sxs-lookup"><span data-stu-id="41fe6-114">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="41fe6-115">Тем не менее, это изменение поведения является существенным и затрагивает многие приложения ASP.NET Core, в связи с чем мы приводим его описание.</span><span class="sxs-lookup"><span data-stu-id="41fe6-115">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="41fe6-116">Методы расширения <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> и <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> также используют набор параметров сериализации <xref:System.Text.Json.JsonSerializerDefaults.Web>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-116">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="41fe6-117">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="41fe6-117">Version introduced</span></span>

<span data-ttu-id="41fe6-118">5.0</span><span class="sxs-lookup"><span data-stu-id="41fe6-118">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="41fe6-119">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="41fe6-119">Reason for change</span></span>

<span data-ttu-id="41fe6-120">Несколько пользователей запросили возможность менее ограничивающей обработки чисел в <xref:System.Text.Json.JsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-120">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="41fe6-121">Это указывает на то, что многие поставщики объектов JSON (например, служб в Интернете) используют заключенные в кавычки числа.</span><span class="sxs-lookup"><span data-stu-id="41fe6-121">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="41fe6-122">Поддержка чтения (десериализации) заключенных в кавычки чисел в приложениях .NET позволяет по умолчанию успешно анализировать эти полезные данные в веб-контексте.</span><span class="sxs-lookup"><span data-stu-id="41fe6-122">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="41fe6-123">Эта конфигурация предоставляется с помощью <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>, что позволяет указывать одни и те же параметры на разных уровнях приложения, например для клиента, сервера и общедоступного уровня.</span><span class="sxs-lookup"><span data-stu-id="41fe6-123">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="41fe6-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="41fe6-124">Recommended action</span></span>

<span data-ttu-id="41fe6-125">Если это изменение приводит к нарушениям в работе, например, если в вашем приложении используется строгая обработка чисел для проверки, вы можете включить предыдущее поведение.</span><span class="sxs-lookup"><span data-stu-id="41fe6-125">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="41fe6-126">Присвойте параметру <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> значение <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41fe6-126">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="41fe6-127">Для приложений MVC и приложений веб-API ASP.NET Core этот параметр можно настроить в `Startup` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="41fe6-127">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a><span data-ttu-id="41fe6-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="41fe6-128">Affected APIs</span></span>

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
