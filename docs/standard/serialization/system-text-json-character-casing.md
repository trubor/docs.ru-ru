---
title: Как включить сопоставление имен свойств без учета регистра с помощью System.Text.Json
description: Узнайте, как в .NET включить сопоставление имен свойств без учета регистра при сериализации в JSON и десериализации из JSON.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3e2fb8cbdd35e772b5e97c731199f69aa834bd0a
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009746"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="a4dad-103">Как включить сопоставление имен свойств без учета регистра с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a4dad-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="a4dad-104">Из этой статьи вы узнаете, как включить сопоставление имен свойств без учета регистра с помощью пространства имен .`System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="a4dad-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="a4dad-105">Сопоставление свойств без учета регистра</span><span class="sxs-lookup"><span data-stu-id="a4dad-105">Case-insensitive property matching</span></span>

<span data-ttu-id="a4dad-106">По умолчанию десериализация выполняет поиск совпадения имен свойств с учетом регистра между кодом JSON и свойствами целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="a4dad-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="a4dad-107">Чтобы изменить это поведение, задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a4dad-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="a4dad-108">В [стандартных параметрах веб-приложений](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) регистр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="a4dad-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="a4dad-109">Ниже приведен пример JSON с именами свойств в "верблюжьем" стиле.</span><span class="sxs-lookup"><span data-stu-id="a4dad-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="a4dad-110">Его можно десериализовать в следующий тип, который содержит имена свойств в регистре Pascal.</span><span class="sxs-lookup"><span data-stu-id="a4dad-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="a4dad-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4dad-111">See also</span></span>

* [<span data-ttu-id="a4dad-112">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a4dad-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a4dad-113">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="a4dad-113">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="a4dad-114">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="a4dad-114">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="a4dad-115">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="a4dad-115">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="a4dad-116">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="a4dad-116">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="a4dad-117">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="a4dad-117">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="a4dad-118">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="a4dad-118">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="a4dad-119">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="a4dad-119">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="a4dad-120">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="a4dad-120">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="a4dad-121">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="a4dad-121">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="a4dad-122">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a4dad-122">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="a4dad-123">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="a4dad-123">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="a4dad-124">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="a4dad-124">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="a4dad-125">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="a4dad-125">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="a4dad-126">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="a4dad-126">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="a4dad-127">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a4dad-127">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a4dad-128">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a4dad-128">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
