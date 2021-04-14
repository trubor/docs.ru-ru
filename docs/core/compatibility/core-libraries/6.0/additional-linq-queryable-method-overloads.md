---
title: 'Критическое изменение в .NET 6: дополнительные перегрузки методов LINQ Queryable'
description: Узнайте о критическом изменении в .NET 6 в базовых библиотеках .NET, где в тип System.Linq.Queryable были добавлены дополнительные перегрузки методов.
ms.date: 03/31/2021
ms.openlocfilehash: 15a4e480f7d1b4e110084e736fc920a522439e69
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123564"
---
# <a name="new-systemlinqqueryable-method-overloads"></a>Новые перегрузки методов System.Linq.Queryable

В <xref:System.Linq.Queryable?displayProperty=fullName> добавлены дополнительные перегрузки открытых методов как часть новых возможностей, реализованных в <https://github.com/dotnet/runtime/pull/47231>. Если код отражения недостаточно надежен при поиске методов, эти добавления могут нарушить реализации поставщика запросов.

## <a name="change-description"></a>Описание изменений

В .NET 6 были добавлены новые перегрузки к методам, перечисленным в разделе [Затронутые API](#affected-apis). В результате этих добавлений может быть нарушена работа кода отражения, как показано в следующем примере.

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

Этот код отражения теперь будет создавать исключение <xref:System.InvalidOperationException> примерно с таким сообщением: **Последовательность содержит более одного элемента**.

## <a name="version-introduced"></a>Представленная версия

6.0 (предварительная версия 3 и предварительная версия 4)

## <a name="reason-for-change"></a>Причина изменения

Новые перегрузки были добавлены для расширения API `Queryable` LINQ.

## <a name="recommended-action"></a>Рекомендованное действие

Если вы создаете библиотеки для поставщика запросов, убедитесь, что ваш код отражения устойчив к добавлению перегрузок методов. Например, используйте перегрузку <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, которая явным образом принимает типы параметров метода.

## <a name="affected-apis"></a>Затронутые API

Новые перегрузки были добавлены в следующие методы расширения <xref:System.Linq.Queryable>:

- <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Zip%2A?displayProperty=fullName>

<!--

### Category

- Core .NET libraries
- LINQ

### Affected APIs

- `Overload:System.Linq.Queryable.ElementAt`
- `Overload:System.Linq.Queryable.ElementAtOrDefault`
- `Overload:System.Linq.Queryable.Take`
- `Overload:System.Linq.Queryable.Min`
- `Overload:System.Linq.Queryable.Max`
- `Overload:System.Linq.Queryable.FirstOrDefault`
- `Overload:System.Linq.Queryable.LastOrDefault`
- `Overload:System.Linq.Queryable.SingleOrDefault`
- `Overload:System.Linq.Queryable.Zip`

-->
