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
ms.openlocfilehash: 2d663ac8c1c15d61959a62c40d9a3b0993484032
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599080"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="236b7-103">Как включить сопоставление имен свойств без учета регистра с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="236b7-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="236b7-104">Из этой статьи вы узнаете, как включить сопоставление имен свойств без учета регистра с помощью пространства имен .`System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="236b7-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="236b7-105">Сопоставление свойств без учета регистра</span><span class="sxs-lookup"><span data-stu-id="236b7-105">Case-insensitive property matching</span></span>

<span data-ttu-id="236b7-106">По умолчанию десериализация выполняет поиск совпадения имен свойств с учетом регистра между кодом JSON и свойствами целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="236b7-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="236b7-107">Чтобы изменить это поведение, задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="236b7-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="236b7-108">В [стандартных параметрах веб-приложений](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) регистр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="236b7-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="236b7-109">Ниже приведен пример JSON с именами свойств в "верблюжьем" стиле.</span><span class="sxs-lookup"><span data-stu-id="236b7-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="236b7-110">Его можно десериализовать в следующий тип, который содержит имена свойств в регистре Pascal.</span><span class="sxs-lookup"><span data-stu-id="236b7-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="236b7-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="236b7-111">See also</span></span>

* [<span data-ttu-id="236b7-112">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="236b7-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="236b7-113">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="236b7-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="236b7-114">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="236b7-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="236b7-115">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="236b7-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="236b7-116">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="236b7-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="236b7-117">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="236b7-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="236b7-118">Сохранение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="236b7-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="236b7-119">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="236b7-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="236b7-120">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="236b7-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="236b7-121">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="236b7-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
