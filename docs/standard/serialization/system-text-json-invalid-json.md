---
title: Разрешение некоторых недопустимых объектов JSON с помощью System.Text.Json
description: Узнайте, как в .NET разрешить комментарии, конечные запятые и числа в кавычках при сериализации в JSON и десериализации из JSON.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 60cbb98bb65ee5c1ffdd3043e42a04004530a115
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439819"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="af7fa-103">Разрешение некоторых недопустимых объектов JSON с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="af7fa-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="af7fa-104">Из этой статьи вы узнаете, как разрешить комментарии, конечные запятые и числа в кавычках при сериализации в JSON и как записывать числа в виде строк.</span><span class="sxs-lookup"><span data-stu-id="af7fa-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="af7fa-105">Разрешение комментариев и завершающих запятых</span><span class="sxs-lookup"><span data-stu-id="af7fa-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="af7fa-106">По умолчанию комментарии и завершающие запятые в JSON не допускаются.</span><span class="sxs-lookup"><span data-stu-id="af7fa-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="af7fa-107">Чтобы разрешить комментарии в JSON, задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> значение `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="af7fa-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="af7fa-108">Чтобы разрешить завершающие запятые, задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="af7fa-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="af7fa-109">В следующем примере показано, как разрешить оба варианта:</span><span class="sxs-lookup"><span data-stu-id="af7fa-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="af7fa-110">Ниже приведен пример JSON с комментариями и завершающей запятой:</span><span class="sxs-lookup"><span data-stu-id="af7fa-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="af7fa-111">Разрешение или запись чисел в кавычках</span><span class="sxs-lookup"><span data-stu-id="af7fa-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="af7fa-112">Некоторые сериализаторы кодируют числа в виде строк JSON (заключены в кавычки).</span><span class="sxs-lookup"><span data-stu-id="af7fa-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="af7fa-113">Пример.</span><span class="sxs-lookup"><span data-stu-id="af7fa-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="af7fa-114">Вместо:</span><span class="sxs-lookup"><span data-stu-id="af7fa-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="af7fa-115">Для сериализации или принятия чисел в кавычках во всех входных данных графа объектов задайте свойство <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType>, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="af7fa-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="af7fa-116">Если вы используете `System.Text.Json` косвенно через ASP.NET Core, тогда заключенные в кавычки числа будут разрешены при десериализации, поскольку ASP.NET Core определяет [стандартные параметры веб-приложений](xref:System.Text.Json.JsonSerializerDefaults.Web).</span><span class="sxs-lookup"><span data-stu-id="af7fa-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="af7fa-117">Чтобы разрешить или записать заключенные в кавычки числа для конкретных свойств, полей или типов, используйте атрибут [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute).</span><span class="sxs-lookup"><span data-stu-id="af7fa-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="af7fa-118">`System.Text.Json` в .NET Core 3.1 не поддерживает сериализацию или десериализацию чисел, заключенных в кавычки.</span><span class="sxs-lookup"><span data-stu-id="af7fa-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="af7fa-119">Дополнительные сведения см. в разделе [Разрешение или запись чисел в кавычках](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="af7fa-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="af7fa-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="af7fa-120">See also</span></span>

* [<span data-ttu-id="af7fa-121">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="af7fa-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="af7fa-122">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="af7fa-122">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="af7fa-123">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="af7fa-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="af7fa-124">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="af7fa-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="af7fa-125">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="af7fa-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="af7fa-126">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="af7fa-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="af7fa-127">Сохранение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="af7fa-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="af7fa-128">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="af7fa-128">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="af7fa-129">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="af7fa-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="af7fa-130">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="af7fa-130">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
