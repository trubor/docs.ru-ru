---
title: Как настроить имена и значения свойств с помощью System.Text.Json
description: Узнайте, как настроить имена и значения свойств при сериализации с использованием System.Text.Json в .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b88509313e719ea993e00d889bc6145f4976a2d
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008907"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a><span data-ttu-id="09578-103">Как настроить имена и значения свойств с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="09578-103">How to customize property names and values with System.Text.Json</span></span>

<span data-ttu-id="09578-104">По умолчанию имена и ключи словарей не изменяются в выходных данных JSON, включая регистр.</span><span class="sxs-lookup"><span data-stu-id="09578-104">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="09578-105">Значения перечисления представлены в виде чисел.</span><span class="sxs-lookup"><span data-stu-id="09578-105">Enum values are represented as numbers.</span></span> <span data-ttu-id="09578-106">В этой статье вы узнаете, как выполнять следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="09578-106">In this article, you'll learn how to:</span></span>

> [!NOTE]
> <span data-ttu-id="09578-107">[Стандартный параметр веб-приложения](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) представлен в "верблюжем" стиле.</span><span class="sxs-lookup"><span data-stu-id="09578-107">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is camel case.</span></span>

* <span data-ttu-id="09578-108">[Настраивать отдельные имена свойств](#customize-individual-property-names).</span><span class="sxs-lookup"><span data-stu-id="09578-108">[Customize individual property names](#customize-individual-property-names)</span></span>
* <span data-ttu-id="09578-109">[Преобразовывать все имена свойств в неоднородный регистр](#use-camel-case-for-all-json-property-names).</span><span class="sxs-lookup"><span data-stu-id="09578-109">[Convert all property names to camel case](#use-camel-case-for-all-json-property-names)</span></span>
* <span data-ttu-id="09578-110">[Реализовывать политики именования пользовательских свойств](#use-a-custom-json-property-naming-policy).</span><span class="sxs-lookup"><span data-stu-id="09578-110">[Implement a custom property naming policy](#use-a-custom-json-property-naming-policy)</span></span>
* <span data-ttu-id="09578-111">[Преобразовывать ключи словаря в "верблюжий" стиль](#camel-case-dictionary-keys).</span><span class="sxs-lookup"><span data-stu-id="09578-111">[Convert dictionary keys to camel case](#camel-case-dictionary-keys)</span></span>
* <span data-ttu-id="09578-112">[Преобразовывать перечисления в строки и "верблюжий" стиль](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="09578-112">[Convert enums to strings and camel case](#enums-as-strings)</span></span>

<span data-ttu-id="09578-113">Для других сценариев, требующих специальной обработки имен и значений свойств JSON, можно [реализовать пользовательские преобразователи](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="09578-113">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

## <a name="customize-individual-property-names"></a><span data-ttu-id="09578-114">Настройка отдельных имен свойств</span><span class="sxs-lookup"><span data-stu-id="09578-114">Customize individual property names</span></span>

<span data-ttu-id="09578-115">Чтобы задать имена отдельных свойств, используйте атрибут [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="09578-115">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="09578-116">Ниже приведен пример типа для сериализации и полученный код JSON:</span><span class="sxs-lookup"><span data-stu-id="09578-116">Here's an example type to serialize and resulting JSON:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="09578-117">Имя свойства, заданное этим атрибутом:</span><span class="sxs-lookup"><span data-stu-id="09578-117">The property name set by this attribute:</span></span>

* <span data-ttu-id="09578-118">Применяется в обоих направлениях для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="09578-118">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="09578-119">Имеет приоритет над политиками именования свойств.</span><span class="sxs-lookup"><span data-stu-id="09578-119">Takes precedence over property naming policies.</span></span>

## <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="09578-120">Использование "верблюжьего" стиля для всех имен свойств JSON</span><span class="sxs-lookup"><span data-stu-id="09578-120">Use camel case for all JSON property names</span></span>

<span data-ttu-id="09578-121">Чтобы использовать "верблюжий" стиль для всех имен свойств JSON, задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> значение `JsonNamingPolicy.CamelCase`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="09578-121">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

<span data-ttu-id="09578-122">Ниже приведен пример класса для сериализации и вывода JSON.</span><span class="sxs-lookup"><span data-stu-id="09578-122">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="09578-123">Политика именования свойств "верблюжьего" стиля:</span><span class="sxs-lookup"><span data-stu-id="09578-123">The camel case property naming policy:</span></span>

* <span data-ttu-id="09578-124">Применяется к сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="09578-124">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="09578-125">Переопределяется атрибутами `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="09578-125">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="09578-126">Именно поэтому имя свойства JSON, `Wind` в примере, не указано в "верблюжьем" стиле.</span><span class="sxs-lookup"><span data-stu-id="09578-126">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

## <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="09578-127">Использование настраиваемой политики именования свойств JSON</span><span class="sxs-lookup"><span data-stu-id="09578-127">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="09578-128">Чтобы использовать настраиваемую политику именования свойств JSON, создайте класс, производный от <xref:System.Text.Json.JsonNamingPolicy>, и переопределите метод <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="09578-128">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

<span data-ttu-id="09578-129">Затем задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> экземпляр класса политики именования:</span><span class="sxs-lookup"><span data-stu-id="09578-129">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

<span data-ttu-id="09578-130">Ниже приведен пример класса для сериализации и вывода JSON.</span><span class="sxs-lookup"><span data-stu-id="09578-130">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="09578-131">Политика именования свойств JSON:</span><span class="sxs-lookup"><span data-stu-id="09578-131">The JSON property naming policy:</span></span>

* <span data-ttu-id="09578-132">Применяется к сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="09578-132">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="09578-133">Переопределяется атрибутами `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="09578-133">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="09578-134">Именно поэтому имя свойства JSON, `Wind` в примере, не указано в верхнем регистре.</span><span class="sxs-lookup"><span data-stu-id="09578-134">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

## <a name="camel-case-dictionary-keys"></a><span data-ttu-id="09578-135">Ключи словаря в "верблюжьем" стиле.</span><span class="sxs-lookup"><span data-stu-id="09578-135">Camel case dictionary keys</span></span>

<span data-ttu-id="09578-136">Если свойство сериализуемого объекта имеет тип `Dictionary<string,TValue>`, ключи `string` можно преобразовать в "верблюжий" стиль.</span><span class="sxs-lookup"><span data-stu-id="09578-136">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="09578-137">Для этого задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> значение `JsonNamingPolicy.CamelCase`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="09578-137">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

<span data-ttu-id="09578-138">Сериализация объекта с помощью словаря с именем `TemperatureRanges`, имеющего пары "ключ-значение" `"ColdMinTemp", 20` и `"HotMinTemp", 40`, приведет к выходным данным JSON, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="09578-138">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="09578-139">Политика именования в "верблюжьем" стиле для ключей словаря применяется только к сериализации.</span><span class="sxs-lookup"><span data-stu-id="09578-139">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="09578-140">При десериализации словаря ключи будут соответствовать JSON-файлу, даже если для параметра `DictionaryKeyPolicy` указано значение `JsonNamingPolicy.CamelCase`.</span><span class="sxs-lookup"><span data-stu-id="09578-140">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

## <a name="enums-as-strings"></a><span data-ttu-id="09578-141">Перечисление в виде строк</span><span class="sxs-lookup"><span data-stu-id="09578-141">Enums as strings</span></span>

<span data-ttu-id="09578-142">По умолчанию перечисления сериализуются как числа.</span><span class="sxs-lookup"><span data-stu-id="09578-142">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="09578-143">Чтобы сериализовать имена перечислений как строки, используйте <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="09578-143">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="09578-144">Например, предположим, что необходимо сериализовать следующий класс, имеющий перечисление:</span><span class="sxs-lookup"><span data-stu-id="09578-144">For example, suppose you need to serialize the following class that has an enum:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

<span data-ttu-id="09578-145">Если параметр "Сводка" имеет значение `Hot`, то по умолчанию сериализованный код JSON имеет числовое значение 3:</span><span class="sxs-lookup"><span data-stu-id="09578-145">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="09578-146">Следующий пример кода сериализует имена перечислений вместо числовых значений и преобразует имена в "верблюжий" стиль:</span><span class="sxs-lookup"><span data-stu-id="09578-146">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

<span data-ttu-id="09578-147">Итоговый код JSON выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="09578-147">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="09578-148">Имена строк перечисления можно также десериализовать, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="09578-148">Enum string names can be deserialized as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a><span data-ttu-id="09578-149">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="09578-149">See also</span></span>

* [<span data-ttu-id="09578-150">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="09578-150">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="09578-151">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="09578-151">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="09578-152">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="09578-152">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="09578-153">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="09578-153">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="09578-154">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="09578-154">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="09578-155">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="09578-155">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="09578-156">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="09578-156">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="09578-157">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="09578-157">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="09578-158">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="09578-158">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="09578-159">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="09578-159">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="09578-160">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="09578-160">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="09578-161">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="09578-161">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="09578-162">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="09578-162">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="09578-163">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="09578-163">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="09578-164">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="09578-164">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="09578-165">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="09578-165">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="09578-166">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="09578-166">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
