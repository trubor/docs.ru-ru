---
title: Критическое изменение. Параметры PropertyNamingPolicy, PropertyNameCaseInsensitive и Encoder учитываются при сериализации пар "ключ-значение"
description: Сведения о критическом изменении в .NET 5, где параметры PropertyNamingPolicy, PropertyNameCaseInsensitive и Encoder учитываются при сериализации и десериализации имен свойств Key и Value экземпляра пары "ключ-значение".
ms.date: 10/18/2020
ms.openlocfilehash: fe6298a677488574fdd7bdc7e887ed3b244ba8d6
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256326"
---
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a>Параметры PropertyNamingPolicy, PropertyNameCaseInsensitive и Encoder учитываются при сериализации и десериализации пар "ключ-значение"

<xref:System.Text.Json.JsonSerializer> теперь учитывает параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.Encoder> при сериализации имен свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> экземпляра <xref:System.Collections.Generic.KeyValuePair%602>. Кроме того, <xref:System.Text.Json.JsonSerializer> учитывает параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> при десериализации экземпляров <xref:System.Collections.Generic.KeyValuePair%602>.

## <a name="change-description"></a>Описание изменений

### <a name="serialization"></a>Сериализация

В версиях .NET Core 3.x и версиях [пакета NuGet System.Text.Json](https://www.nuget.org/packages/System.Text.Json) с 4.6.0 по 4.7.2 свойства экземпляров <xref:System.Collections.Generic.KeyValuePair%602> всегда сериализуются точно как "ключ" и "значение", независимо от значений параметров <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> и <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType>. В следующем примере кода показано, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> *не* задаются в "верблюжьем" стиле, несмотря на то, что такое поведение предписывается действующей политикой именования свойств.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

Начиная с .NET 5 параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.Encoder> учитываются при сериализации экземпляров <xref:System.Collections.Generic.KeyValuePair%602>. В следующем примере кода показано, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> после сериализации задаются в "верблюжьем" стиле в соответствии с действующей политикой именования свойств.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a>Десериализация

В версиях .NET Core 3.x и версиях 4.7.x [пакета NuGet System.Text.Json](https://www.nuget.org/packages/System.Text.Json) возникает исключение <xref:System.Text.Json.JsonException>, если имена свойств JSON не задаются в точности как `Key` и `Value`, например, если они не начинаются с прописной буквы. Исключение создается, даже если действующая политика именования свойств явно разрешает это.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

Начиная с .NET 5 параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> учитываются при десериализации с использованием <xref:System.Text.Json.JsonSerializer>. Например, в следующем фрагменте кода показана успешная десериализация имен свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> в нижнем регистре, поскольку это допускается действующей политикой именования свойств.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

Чтобы обеспечить соответствие полезных данных, которые были сериализованы с использованием предыдущих версий, "ключ" и "значение" имеют особый регистр для сопоставления при десериализации. Несмотря на то, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> не заданы в "верблюжьем" стиле в соответствии с параметром <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> в следующем примере кода, они успешно десериализуются.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="reason-for-change"></a>Причина изменения

Получено большое количество отзывов клиентов о необходимости учитывать <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>. Для полноты также учитываются параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> и <xref:System.Text.Json.JsonSerializerOptions.Encoder>, благодаря чему экземпляры <xref:System.Collections.Generic.KeyValuePair%602> обрабатываются так же, как и любой другой традиционный объект среды CLR (POCO).

## <a name="recommended-action"></a>Рекомендованное действие

Если это изменение нарушает работу, можно использовать [настраиваемый преобразователь](../../../../standard/serialization/system-text-json-converters-how-to.md), который реализует нужную семантику.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
