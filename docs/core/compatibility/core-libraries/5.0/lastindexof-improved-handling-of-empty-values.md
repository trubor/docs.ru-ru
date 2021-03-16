---
title: Критическое изменение. Улучшена обработка пустых строк поиска с помощью LastIndexOf
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где LastIndexOf и связанные API теперь возвращают правильные значения при поиске подстроки нулевой длины.
ms.date: 11/01/2020
ms.openlocfilehash: 9dc34300d867fe1bb9264494b3f2261bad2c1eea
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257431"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>Улучшена обработка пустых строк поиска с помощью LastIndexOf

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> и связанные API теперь возвращают правильные значения при поиске подстроки нулевой длины (или эквивалентной нулевой длины) в более длинной строке.

## <a name="change-description"></a>Описание изменений

В .NET Framework и .NET Core 1.0–3.1 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> и связанные API могут возвращать неправильное значение, когда вызывающий объект выполняет поиск подстроки нулевой длины.

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

Начиная с .NET 5 эти API возвращают правильное значение для `LastIndexOf`.

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

В этих примерах `5` является правильным ответом, поскольку и `"Hello".Substring(5)`, и `"Hello".AsSpan().Slice(5)` создают пустую строку, которая является эквивалентной по отношению к искомой пустой подстроке.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было внесено в рамках устранения ошибок, связанных с обработкой строк для .NET 5. Это также помогает унифицировать поведение платформы Windows и платформ, отличных от Windows. Дополнительные сведения см. в статьях [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) и [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Никаких дополнительных действий от вас не требуется. Среда выполнения .NET 5 автоматически предоставляет новые варианты поведения.

Отсутствует параметр совместимости для восстановления старого поведения.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
