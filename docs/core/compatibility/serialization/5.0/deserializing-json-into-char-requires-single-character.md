---
title: Критическое изменение. Для десериализации требуется строка из одного символа
description: Сведения о критическом изменении в .NET 5.0, где для JsonSerializer.Deserialize требуется строка из одного символа.
ms.date: 10/18/2020
ms.openlocfilehash: 780f2928d776ecb6db9a7fc05a720e889eb363e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759970"
---
# <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="b6899-103">Для JsonSerializer.Deserialize требуется строка из одного символа</span><span class="sxs-lookup"><span data-stu-id="b6899-103">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="b6899-104">Если параметр типа имеет значение <xref:System.Char>, строковый аргумент для <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> должен содержать один символ для выполнения десериализации.</span><span class="sxs-lookup"><span data-stu-id="b6899-104">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

## <a name="change-description"></a><span data-ttu-id="b6899-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="b6899-105">Change description</span></span>

<span data-ttu-id="b6899-106">В предыдущих версиях .NET, если строка с несколькими символами передается в <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> и параметр типа равен <xref:System.Char>, десериализация выполняется успешно, но десериализуется только первый символ.</span><span class="sxs-lookup"><span data-stu-id="b6899-106">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="b6899-107">В .NET 5.0 и более поздних версиях, когда параметр типа равен <xref:System.Char>, передача любой, кроме односимвольной, строки приводит к вызову исключения <xref:System.Text.Json.JsonException>.</span><span class="sxs-lookup"><span data-stu-id="b6899-107">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="b6899-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="b6899-108">Version introduced</span></span>

<span data-ttu-id="b6899-109">5.0</span><span class="sxs-lookup"><span data-stu-id="b6899-109">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b6899-110">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="b6899-110">Reason for change</span></span>

<span data-ttu-id="b6899-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> выполняет синтаксический анализ текста, представляющего одно значение JSON, в экземпляр типа, заданного параметром универсального типа.</span><span class="sxs-lookup"><span data-stu-id="b6899-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="b6899-112">Синтаксический анализ должен выполняться только тогда, когда предоставленные полезные данные допустимы для указанного параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="b6899-112">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="b6899-113">Для типа значения <xref:System.Char> допустимые полезные данные представляют собой строку из одного символа.</span><span class="sxs-lookup"><span data-stu-id="b6899-113">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b6899-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="b6899-114">Recommended action</span></span>

<span data-ttu-id="b6899-115">При синтаксическом анализе строки в тип <xref:System.Char> с помощью <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>убедитесь, что строка состоит из одного символа.</span><span class="sxs-lookup"><span data-stu-id="b6899-115">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b6899-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="b6899-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
