---
title: Критическое изменение. При сериализации создается исключение, если параметр типа имеет значение NULL
description: Сведения о критическом изменении в .NET 5.0, где методы сериализации JsonSerializer.Serialize с параметром Type теперь вызывают исключение, если этот параметр имеет значение NULL
ms.date: 10/18/2020
ms.openlocfilehash: af2885394418072ad7efec5855490b5b80152fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759946"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="d8bbb-103">JsonSerializer.Serialize вызывает исключение ArgumentNullException, если параметр типа имеет значение null</span><span class="sxs-lookup"><span data-stu-id="d8bbb-103">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="d8bbb-104">Перегрузки <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> и <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> с параметром типа <xref:System.Type> теперь вызывают исключение <xref:System.ArgumentNullException>, когда для параметра передается значение `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bbb-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a parameter of type <xref:System.Type> now throw an <xref:System.ArgumentNullException> whenever `null` is passed for that parameter.</span></span>

## <a name="change-description"></a><span data-ttu-id="d8bbb-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d8bbb-105">Change description</span></span>

<span data-ttu-id="d8bbb-106">В .NET Core 3.1 перегрузки <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> и <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, имеющие параметр <xref:System.Type>, вызывают исключение <xref:System.ArgumentNullException> при передаче для параметра `Type inputType` значение `null`, но не в том случае, если параметр `Object value` также равен `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bbb-106">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="d8bbb-107">Начиная с .NET 5.0 эти методы *всегда* вызывают исключение <xref:System.ArgumentNullException> при передаче для параметра <xref:System.Type> значения `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bbb-107">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="d8bbb-108">Поведение в .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="d8bbb-108">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="d8bbb-109">Поведение в .NET 5.0 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="d8bbb-109">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a><span data-ttu-id="d8bbb-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d8bbb-110">Version introduced</span></span>

<span data-ttu-id="d8bbb-111">5.0</span><span class="sxs-lookup"><span data-stu-id="d8bbb-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d8bbb-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d8bbb-112">Reason for change</span></span>

<span data-ttu-id="d8bbb-113">Передача для параметра `Type inputType` значения `null` неприемлемо и всегда должно вызывать исключение <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="d8bbb-113">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d8bbb-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d8bbb-114">Recommended action</span></span>

<span data-ttu-id="d8bbb-115">Убедитесь, что вы не передаете для параметра `Type inputType` этих методов значение `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bbb-115">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d8bbb-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d8bbb-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
