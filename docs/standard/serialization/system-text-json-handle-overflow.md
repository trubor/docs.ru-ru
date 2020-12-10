---
title: Как обрабатывать переполнения JSON с помощью System.Text.Json
description: Узнайте, как в .NET обрабатывать переполнения JSON при сериализации в JSON и десериализации из JSON.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439849"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="5ff3f-103">Как обрабатывать переполнения JSON с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5ff3f-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="5ff3f-104">Из этой статьи вы узнаете, как обрабатывать переполнения JSON с помощью пространства имен `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="5ff3f-105">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="5ff3f-105">Handle overflow JSON</span></span>

<span data-ttu-id="5ff3f-106">При десериализации в JSON могут быть получены данные, которые не представлены свойствами целевого типа.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="5ff3f-107">Предположим у вас есть следующий целевой тип:</span><span class="sxs-lookup"><span data-stu-id="5ff3f-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="5ff3f-108">А десериализируемым кодом JSON является:</span><span class="sxs-lookup"><span data-stu-id="5ff3f-108">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="5ff3f-109">При десериализации кода JSON, показанного в указанном типе, свойства `DatesAvailable` и `SummaryWords` никуда не переходят и будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="5ff3f-110">Для записи дополнительных данных, таких как эти свойства, примените атрибут [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) к свойству типа `Dictionary<string,object>` или `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="5ff3f-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="5ff3f-111">При десериализации показанного ранее JSON в этот тип данных дополнительные данные становятся парами "ключ-значение" свойства `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="5ff3f-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="5ff3f-112">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-112">Property</span></span> | <span data-ttu-id="5ff3f-113">Значение</span><span class="sxs-lookup"><span data-stu-id="5ff3f-113">Value</span></span> | <span data-ttu-id="5ff3f-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="5ff3f-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="5ff3f-115">Несовпадение с учетом регистра (`temperatureCelsius` в коде JSON), поэтому свойство не задано.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="5ff3f-116">Так как регистр не совпадает, это свойство JSON является лишним и становится парой "ключ-значение" в словаре.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="5ff3f-117">Дополнительное свойство из кода JSON преобразуется в пару "ключ-значение" с массивом в качестве объекта значения.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="5ff3f-118">Дополнительное свойство из кода JSON преобразуется в пару "ключ-значение" с массивом в качестве объекта значения.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="5ff3f-119">Когда целевой объект сериализуется, пары "ключ-значение" данных расширения становятся свойствами JSON точно так же, как они были во входящем коде JSON:</span><span class="sxs-lookup"><span data-stu-id="5ff3f-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="5ff3f-120">Обратите внимание, что имя свойства `ExtensionData` не отображается в коде JSON.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="5ff3f-121">Такое поведение позволяет JSON выполнить круговой путь без потери дополнительных данных, которые в противном случае не будут десериализованы.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ff3f-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5ff3f-122">See also</span></span>

* [<span data-ttu-id="5ff3f-123">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5ff3f-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="5ff3f-124">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="5ff3f-124">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="5ff3f-125">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="5ff3f-125">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="5ff3f-126">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="5ff3f-126">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="5ff3f-127">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="5ff3f-127">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="5ff3f-128">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="5ff3f-128">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="5ff3f-129">Сохранение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="5ff3f-129">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="5ff3f-130">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="5ff3f-130">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="5ff3f-131">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="5ff3f-131">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="5ff3f-132">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="5ff3f-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
