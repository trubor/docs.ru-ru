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
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a><span data-ttu-id="755f5-103">Параметры PropertyNamingPolicy, PropertyNameCaseInsensitive и Encoder учитываются при сериализации и десериализации пар "ключ-значение"</span><span class="sxs-lookup"><span data-stu-id="755f5-103">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>

<span data-ttu-id="755f5-104"><xref:System.Text.Json.JsonSerializer> теперь учитывает параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.Encoder> при сериализации имен свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> экземпляра <xref:System.Collections.Generic.KeyValuePair%602>.</span><span class="sxs-lookup"><span data-stu-id="755f5-104"><xref:System.Text.Json.JsonSerializer> now honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options when serializing the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names of a <xref:System.Collections.Generic.KeyValuePair%602> instance.</span></span> <span data-ttu-id="755f5-105">Кроме того, <xref:System.Text.Json.JsonSerializer> учитывает параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> при десериализации экземпляров <xref:System.Collections.Generic.KeyValuePair%602>.</span><span class="sxs-lookup"><span data-stu-id="755f5-105">Additionally, <xref:System.Text.Json.JsonSerializer> honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options when deserializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span>

## <a name="change-description"></a><span data-ttu-id="755f5-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="755f5-106">Change description</span></span>

### <a name="serialization"></a><span data-ttu-id="755f5-107">Сериализация</span><span class="sxs-lookup"><span data-stu-id="755f5-107">Serialization</span></span>

<span data-ttu-id="755f5-108">В версиях .NET Core 3.x и версиях [пакета NuGet System.Text.Json](https://www.nuget.org/packages/System.Text.Json) с 4.6.0 по 4.7.2 свойства экземпляров <xref:System.Collections.Generic.KeyValuePair%602> всегда сериализуются точно как "ключ" и "значение", независимо от значений параметров <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> и <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="755f5-108">In .NET Core 3.x versions and in the 4.6.0-4.7.2 versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), the properties of <xref:System.Collections.Generic.KeyValuePair%602> instances are always serialized as "Key" and "Value" exactly, regardless of any <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> and <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="755f5-109">В следующем примере кода показано, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> *не* задаются в "верблюжьем" стиле, несмотря на то, что такое поведение предписывается действующей политикой именования свойств.</span><span class="sxs-lookup"><span data-stu-id="755f5-109">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are *not* camel-cased after serialization, even though the specified property-naming policy dictates so.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

<span data-ttu-id="755f5-110">Начиная с .NET 5 параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.Encoder> учитываются при сериализации экземпляров <xref:System.Collections.Generic.KeyValuePair%602>.</span><span class="sxs-lookup"><span data-stu-id="755f5-110">Starting in .NET 5, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are honored when serializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span> <span data-ttu-id="755f5-111">В следующем примере кода показано, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> после сериализации задаются в "верблюжьем" стиле в соответствии с действующей политикой именования свойств.</span><span class="sxs-lookup"><span data-stu-id="755f5-111">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are camel-cased after serialization, in accordance with the specified property-naming policy.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a><span data-ttu-id="755f5-112">Десериализация</span><span class="sxs-lookup"><span data-stu-id="755f5-112">Deserialization</span></span>

<span data-ttu-id="755f5-113">В версиях .NET Core 3.x и версиях 4.7.x [пакета NuGet System.Text.Json](https://www.nuget.org/packages/System.Text.Json) возникает исключение <xref:System.Text.Json.JsonException>, если имена свойств JSON не задаются в точности как `Key` и `Value`, например, если они не начинаются с прописной буквы.</span><span class="sxs-lookup"><span data-stu-id="755f5-113">In .NET Core 3.x versions and in the 4.7.x versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), a <xref:System.Text.Json.JsonException> is thrown when the JSON property names are not precisely `Key` and `Value`, for example, if they don't start with an uppercase letter.</span></span> <span data-ttu-id="755f5-114">Исключение создается, даже если действующая политика именования свойств явно разрешает это.</span><span class="sxs-lookup"><span data-stu-id="755f5-114">The exception is thrown even if a specified property-naming policy expressly permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

<span data-ttu-id="755f5-115">Начиная с .NET 5 параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> и <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> учитываются при десериализации с использованием <xref:System.Text.Json.JsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="755f5-115">Starting in .NET 5, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options are honored when deserializing using <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="755f5-116">Например, в следующем фрагменте кода показана успешная десериализация имен свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> в нижнем регистре, поскольку это допускается действующей политикой именования свойств.</span><span class="sxs-lookup"><span data-stu-id="755f5-116">For example, the following code snippet shows successful deserialization of lowercased <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names because the specified property-naming policy permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

<span data-ttu-id="755f5-117">Чтобы обеспечить соответствие полезных данных, которые были сериализованы с использованием предыдущих версий, "ключ" и "значение" имеют особый регистр для сопоставления при десериализации.</span><span class="sxs-lookup"><span data-stu-id="755f5-117">To accommodate payloads that were serialized with previous versions, "Key" and "Value" are special-cased to match when deserializing.</span></span> <span data-ttu-id="755f5-118">Несмотря на то, что имена свойств <xref:System.Collections.Generic.KeyValuePair%602.Key> и <xref:System.Collections.Generic.KeyValuePair%602.Value> не заданы в "верблюжьем" стиле в соответствии с параметром <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> в следующем примере кода, они успешно десериализуются.</span><span class="sxs-lookup"><span data-stu-id="755f5-118">Even though the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names aren't camel-cased according to the in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in the following code example, they deserialize successfully.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a><span data-ttu-id="755f5-119">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="755f5-119">Version introduced</span></span>

<span data-ttu-id="755f5-120">5.0</span><span class="sxs-lookup"><span data-stu-id="755f5-120">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="755f5-121">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="755f5-121">Reason for change</span></span>

<span data-ttu-id="755f5-122">Получено большое количество отзывов клиентов о необходимости учитывать <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy>.</span><span class="sxs-lookup"><span data-stu-id="755f5-122">Substantial customer feedback indicated that the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> should be honored.</span></span> <span data-ttu-id="755f5-123">Для полноты также учитываются параметры <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> и <xref:System.Text.Json.JsonSerializerOptions.Encoder>, благодаря чему экземпляры <xref:System.Collections.Generic.KeyValuePair%602> обрабатываются так же, как и любой другой традиционный объект среды CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="755f5-123">For completeness, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are also honored, so that <xref:System.Collections.Generic.KeyValuePair%602> instances are treated the same as any other plain old CLR object (POCO).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="755f5-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="755f5-124">Recommended action</span></span>

<span data-ttu-id="755f5-125">Если это изменение нарушает работу, можно использовать [настраиваемый преобразователь](../../../../standard/serialization/system-text-json-converters-how-to.md), который реализует нужную семантику.</span><span class="sxs-lookup"><span data-stu-id="755f5-125">If this change is disruptive to you, you can use a [custom converter](../../../../standard/serialization/system-text-json-converters-how-to.md) that implements the desired semantics.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="755f5-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="755f5-126">Affected APIs</span></span>

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
