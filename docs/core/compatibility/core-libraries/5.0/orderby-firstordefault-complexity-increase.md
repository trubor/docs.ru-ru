---
title: Критическое изменение. Увеличена сложность LINQ OrderBy.First{OrDefault}
description: Ознакомьтесь с критическим изменением .NET 5 в основных библиотеках .NET, где изменилась реализация OrderBy.First.
ms.date: 11/01/2020
ms.openlocfilehash: 4cd2dda5f60976f935505d6a6cb1e4c23d150d09
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257275"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a>Увеличена сложность LINQ OrderBy.First{OrDefault}

Реализация <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> и <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> изменилась, что привело к увеличению сложности операции.

## <a name="change-description"></a>Описание изменений

В .NET Core версий 1.x–3.x вызов <xref:System.Linq.Enumerable.OrderBy%2A> или <xref:System.Linq.Enumerable.OrderByDescending%2A>, за которым следовал вызов <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> или <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>, выполнялся с уровнем сложности `O(N)`. Так как требуется только первый элемент (элемент по умолчанию), для его поиска требуется только одно перечисление. Однако предикат, передаваемый в <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> или <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>, вызывается ровно `N` раз, где `N` — длина последовательности.

В .NET 5 и более поздних версиях было [внесено изменение](https://github.com/dotnet/runtime/pull/36643), вследствие которого вызов <xref:System.Linq.Enumerable.OrderBy%2A> или <xref:System.Linq.Enumerable.OrderByDescending%2A>, за которым следует <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> или <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>, выполняется с уровнем сложности `O(N log N)`, а не `O(N)`. Однако предикат, который передается в <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> или <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>, может вызываться *менее* чем `N` раз, что более важно для общей производительности.

> [!NOTE]
> Это изменение соответствует реализации и сложности операции в .NET Framework.

## <a name="reason-for-change"></a>Причина изменения

Преимущество вызова предиката меньшее число раз перевешивает общее снижение сложности, поэтому реализация, появившаяся в .NET Core 1.0, была отменена. Дополнительные сведения в описании [этой проблемы dotnet/runtime](https://github.com/dotnet/runtime/issues/31554).

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

От разработчика не требуется никаких действий.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
