---
title: Разрешение некоторых недопустимых объектов JSON с помощью System.Text.Json
description: Узнайте, как в .NET разрешить комментарии, конечные запятые и числа в кавычках при сериализации в JSON и десериализации из JSON.
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2559b081010fb0a2fa208b121cb095efdeb8da2e
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009814"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="aa43b-103">Разрешение некоторых недопустимых объектов JSON с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="aa43b-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="aa43b-104">Из этой статьи вы узнаете, как разрешить комментарии, конечные запятые и числа в кавычках при сериализации в JSON и как записывать числа в виде строк.</span><span class="sxs-lookup"><span data-stu-id="aa43b-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="aa43b-105">Разрешение комментариев и завершающих запятых</span><span class="sxs-lookup"><span data-stu-id="aa43b-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="aa43b-106">По умолчанию комментарии и завершающие запятые в JSON не допускаются.</span><span class="sxs-lookup"><span data-stu-id="aa43b-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="aa43b-107">Чтобы разрешить комментарии в JSON, задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> значение `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="aa43b-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="aa43b-108">Чтобы разрешить завершающие запятые, задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="aa43b-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="aa43b-109">В следующем примере показано, как разрешить оба варианта:</span><span class="sxs-lookup"><span data-stu-id="aa43b-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="aa43b-110">Ниже приведен пример JSON с комментариями и завершающей запятой:</span><span class="sxs-lookup"><span data-stu-id="aa43b-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="aa43b-111">Разрешение или запись чисел в кавычках</span><span class="sxs-lookup"><span data-stu-id="aa43b-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="aa43b-112">Некоторые сериализаторы кодируют числа в виде строк JSON (заключены в кавычки).</span><span class="sxs-lookup"><span data-stu-id="aa43b-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="aa43b-113">Пример.</span><span class="sxs-lookup"><span data-stu-id="aa43b-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="aa43b-114">Вместо:</span><span class="sxs-lookup"><span data-stu-id="aa43b-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="aa43b-115">Для сериализации или принятия чисел в кавычках во всех входных данных графа объектов задайте свойство <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType>, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="aa43b-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="aa43b-116">Если вы используете `System.Text.Json` косвенно через ASP.NET Core, тогда заключенные в кавычки числа будут разрешены при десериализации, поскольку ASP.NET Core определяет [стандартные параметры веб-приложений](xref:System.Text.Json.JsonSerializerDefaults.Web).</span><span class="sxs-lookup"><span data-stu-id="aa43b-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="aa43b-117">Чтобы разрешить или записать заключенные в кавычки числа для конкретных свойств, полей или типов, используйте атрибут [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute).</span><span class="sxs-lookup"><span data-stu-id="aa43b-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="aa43b-118">`System.Text.Json` в .NET Core 3.1 не поддерживает сериализацию или десериализацию чисел, заключенных в кавычки.</span><span class="sxs-lookup"><span data-stu-id="aa43b-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="aa43b-119">Дополнительные сведения см. в разделе [Разрешение или запись чисел в кавычках](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="aa43b-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="aa43b-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="aa43b-120">See also</span></span>

* [<span data-ttu-id="aa43b-121">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="aa43b-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="aa43b-122">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="aa43b-122">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="aa43b-123">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="aa43b-123">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="aa43b-124">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="aa43b-124">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="aa43b-125">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="aa43b-125">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="aa43b-126">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="aa43b-126">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="aa43b-127">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="aa43b-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="aa43b-128">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="aa43b-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="aa43b-129">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="aa43b-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="aa43b-130">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="aa43b-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="aa43b-131">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="aa43b-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="aa43b-132">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="aa43b-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="aa43b-133">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="aa43b-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="aa43b-134">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="aa43b-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="aa43b-135">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="aa43b-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="aa43b-136">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="aa43b-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="aa43b-137">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="aa43b-137">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
