---
title: Игнорирование свойств с помощью System.Text.Json
description: Узнайте, как игнорировать свойства при сериализации с помощью System.Text.Json в .NET.
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
ms.openlocfilehash: 6d703156d50a3e00a33cea5e15be2df911ed7c1b
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008816"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="fa300-103">Игнорирование свойств с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="fa300-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="fa300-104">По умолчанию при сериализации объектов C# в JSON сериализуются все открытые свойства.</span><span class="sxs-lookup"><span data-stu-id="fa300-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="fa300-105">Если вы не хотите, чтобы некоторые из них отображались в итоговом коде JSON, у вас есть несколько вариантов.</span><span class="sxs-lookup"><span data-stu-id="fa300-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="fa300-106">Из этой статьи вы узнаете, как игнорировать свойства в зависимости от различных критериев.</span><span class="sxs-lookup"><span data-stu-id="fa300-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="fa300-107">[отдельных свойств](#ignore-individual-properties);</span><span class="sxs-lookup"><span data-stu-id="fa300-107">[Individual properties](#ignore-individual-properties)</span></span>
* <span data-ttu-id="fa300-108">[всех свойств только для чтения](#ignore-all-read-only-properties);</span><span class="sxs-lookup"><span data-stu-id="fa300-108">[All read-only properties](#ignore-all-read-only-properties)</span></span>
* <span data-ttu-id="fa300-109">[всех свойств со значением NULL](#ignore-all-null-value-properties).</span><span class="sxs-lookup"><span data-stu-id="fa300-109">[All null-value properties](#ignore-all-null-value-properties)</span></span>
* <span data-ttu-id="fa300-110">[всех свойств значений по умолчанию](#ignore-all-default-value-properties);</span><span class="sxs-lookup"><span data-stu-id="fa300-110">[All default-value properties](#ignore-all-default-value-properties)</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="fa300-111">[отдельных свойств](#ignore-individual-properties);</span><span class="sxs-lookup"><span data-stu-id="fa300-111">[Individual properties](#ignore-individual-properties)</span></span>
* <span data-ttu-id="fa300-112">[всех свойств только для чтения](#ignore-all-read-only-properties);</span><span class="sxs-lookup"><span data-stu-id="fa300-112">[All read-only properties](#ignore-all-read-only-properties)</span></span>
* <span data-ttu-id="fa300-113">[всех свойств со значением NULL](#ignore-all-null-value-properties).</span><span class="sxs-lookup"><span data-stu-id="fa300-113">[All null-value properties](#ignore-all-null-value-properties)</span></span>
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="fa300-114">Игнорирование индивидуальных свойств</span><span class="sxs-lookup"><span data-stu-id="fa300-114">Ignore individual properties</span></span>

<span data-ttu-id="fa300-115">Чтобы игнорировать отдельные свойства, используйте атрибут [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute).</span><span class="sxs-lookup"><span data-stu-id="fa300-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="fa300-116">Ниже приведен пример типа для сериализации и вывода JSON.</span><span class="sxs-lookup"><span data-stu-id="fa300-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa300-117">Можно указать условное исключение, задав свойство `Condition` атрибута [ [JsonIgnore] ](xref:System.Text.Json.Serialization.JsonIgnoreAttribute).</span><span class="sxs-lookup"><span data-stu-id="fa300-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="fa300-118">Перечисление <xref:System.Text.Json.Serialization.JsonIgnoreCondition> предоставляет следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="fa300-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="fa300-119">`Always` — свойство всегда игнорируется.</span><span class="sxs-lookup"><span data-stu-id="fa300-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="fa300-120">Если свойство `Condition` не указано, предполагается этот параметр.</span><span class="sxs-lookup"><span data-stu-id="fa300-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="fa300-121">`Never` — свойство всегда сериализуется и десериализуется, независимо от глобальных параметров `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties` и `IgnoreReadOnlyFields`.</span><span class="sxs-lookup"><span data-stu-id="fa300-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="fa300-122">`WhenWritingDefault` — свойство не учитывается при сериализации, если оно является ссылочным типом `null`, типом значения `default`, допускающим NULL, или типом значения `null`.</span><span class="sxs-lookup"><span data-stu-id="fa300-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="fa300-123">`WhenWritingNull` — свойство не учитывается при сериализации, если оно является ссылочным типом `null` или типом значения `null`, допускающим значение NULL.</span><span class="sxs-lookup"><span data-stu-id="fa300-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="fa300-124">В следующем примере показано использование свойства `Condition` атрибута [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute):</span><span class="sxs-lookup"><span data-stu-id="fa300-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="fa300-125">Игнорирование всех свойств "только для чтения"</span><span class="sxs-lookup"><span data-stu-id="fa300-125">Ignore all read-only properties</span></span>

<span data-ttu-id="fa300-126">Свойство доступно только для чтения, если оно содержит открытый метод получения, но не является общим методом задания.</span><span class="sxs-lookup"><span data-stu-id="fa300-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="fa300-127">Чтобы игнорировать при сериализации все свойства "только для чтения", задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> значение `true`, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="fa300-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="fa300-128">Ниже приведен пример типа для сериализации и вывода JSON.</span><span class="sxs-lookup"><span data-stu-id="fa300-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="fa300-129">Этот параметр применяется только к сериализации.</span><span class="sxs-lookup"><span data-stu-id="fa300-129">This option applies only to serialization.</span></span> <span data-ttu-id="fa300-130">Во время десериализации свойства, доступные только для чтения, по умолчанию игнорируются.</span><span class="sxs-lookup"><span data-stu-id="fa300-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa300-131">Этот параметр применяется только к свойствам.</span><span class="sxs-lookup"><span data-stu-id="fa300-131">This option applies only to properties.</span></span> <span data-ttu-id="fa300-132">Чтобы пропустить при [сериализации полей](system-text-json-how-to.md#include-fields) поля, предназначенные только для чтения, используйте глобальный параметр <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa300-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="fa300-133">Игнорировать все свойства со значением NULL</span><span class="sxs-lookup"><span data-stu-id="fa300-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa300-134">Чтобы игнорировать все свойства со значением NULL, задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> значение <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="fa300-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fa300-135">Чтобы игнорировать при сериализации все свойства со значением NULL, задайте для параметра <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> значение `true`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="fa300-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="fa300-136">Ниже приведен пример объекта для сериализации и вывода JSON.</span><span class="sxs-lookup"><span data-stu-id="fa300-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="fa300-137">Свойство.</span><span class="sxs-lookup"><span data-stu-id="fa300-137">Property</span></span>             | <span data-ttu-id="fa300-138">Значение</span><span class="sxs-lookup"><span data-stu-id="fa300-138">Value</span></span>                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="fa300-139">Игнорирование всех свойств со значениями по умолчанию</span><span class="sxs-lookup"><span data-stu-id="fa300-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa300-140">Чтобы предотвратить сериализацию значений по умолчанию в свойствах типа значения, присвойте свойству <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> значение <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="fa300-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="fa300-141">Параметр <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> также предотвращает сериализацию свойств ссылочного типа со значением NULL и типа значения, допускающим значение NULL.</span><span class="sxs-lookup"><span data-stu-id="fa300-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fa300-142">Для .NET Core 3.1. не существует встроенного способа предотвращения сериализации свойств с типом значения "по умолчанию" в `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="fa300-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="fa300-143">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fa300-143">See also</span></span>

* [<span data-ttu-id="fa300-144">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="fa300-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="fa300-145">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="fa300-145">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="fa300-146">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="fa300-146">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="fa300-147">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="fa300-147">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="fa300-148">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="fa300-148">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="fa300-149">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="fa300-149">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="fa300-150">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="fa300-150">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="fa300-151">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="fa300-151">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="fa300-152">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="fa300-152">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="fa300-153">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="fa300-153">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="fa300-154">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="fa300-154">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="fa300-155">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="fa300-155">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="fa300-156">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="fa300-156">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="fa300-157">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="fa300-157">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="fa300-158">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="fa300-158">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="fa300-159">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="fa300-159">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="fa300-160">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="fa300-160">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
