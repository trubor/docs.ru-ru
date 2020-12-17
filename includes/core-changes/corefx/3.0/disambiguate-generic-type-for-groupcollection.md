---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366866"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a><span data-ttu-id="6d1ff-101">Передача GroupCollection в методы расширения, принимающие IEnumerable\<T>, требует устранения неоднозначности</span><span class="sxs-lookup"><span data-stu-id="6d1ff-101">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>

<span data-ttu-id="6d1ff-102">При вызове метода расширения, который принимает `IEnumerable<T>` в <xref:System.Text.RegularExpressions.GroupCollection>, необходимо устранить неоднозначность типа с помощью приведения.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-102">When calling an extension method that takes an `IEnumerable<T>` on a <xref:System.Text.RegularExpressions.GroupCollection>, you must disambiguate the type using a cast.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6d1ff-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="6d1ff-103">Change description</span></span>

<span data-ttu-id="6d1ff-104">Начиная с .NET Core 3.0 <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> реализует `IEnumerable<KeyValuePair<String,Group>>` в дополнение к другим реализуемым типам, включая `IEnumerable<Group>`.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-104">Starting in .NET Core 3.0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implements `IEnumerable<KeyValuePair<String,Group>>` in addition to the other types it implements, including `IEnumerable<Group>`.</span></span> <span data-ttu-id="6d1ff-105">Это приводит к неоднозначности при вызове метода расширения, который принимает <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-105">This results in ambiguity when calling an extension method that takes an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6d1ff-106">При вызове такого метода расширения в экземпляре <xref:System.Text.RegularExpressions.GroupCollection>, например <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, вы увидите следующую ошибку компилятора:</span><span class="sxs-lookup"><span data-stu-id="6d1ff-106">If you call such an extension method on a <xref:System.Text.RegularExpressions.GroupCollection> instance, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, you'll see the following compiler error:</span></span>

<span data-ttu-id="6d1ff-107">**CS1061: "GroupCollection" не содержит определение для "Count", и не удается найти метод расширения "Count", принимающий первый аргумент типа "GroupCollection" (возможно, пропущена директива using или ссылка на сборку)**</span><span class="sxs-lookup"><span data-stu-id="6d1ff-107">**CS1061: 'GroupCollection' does not contain a definition for 'Count' and no accessible extension method 'Count' accepting a first argument of type 'GroupCollection' could be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="6d1ff-108">В предыдущих версиях .NET не существовало неоднозначности и не было таких ошибок компилятора.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-108">In previous versions of .NET, there was no ambiguity and no compiler error.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6d1ff-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="6d1ff-109">Version introduced</span></span>

<span data-ttu-id="6d1ff-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6d1ff-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6d1ff-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="6d1ff-111">Reason for change</span></span>

<span data-ttu-id="6d1ff-112">Это было [непреднамеренное критическое изменение](https://github.com/dotnet/corefx/pull/30077).</span><span class="sxs-lookup"><span data-stu-id="6d1ff-112">This was an [unintentional breaking change](https://github.com/dotnet/corefx/pull/30077).</span></span> <span data-ttu-id="6d1ff-113">Так как все это уже существовало некоторое время, мы не планируем отменять его.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-113">Because it has been like this for some time, we don't plan to revert it.</span></span> <span data-ttu-id="6d1ff-114">Кроме того, такое изменение само по себе будет критическим.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-114">In addition, such a change would itself be breaking.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6d1ff-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="6d1ff-115">Recommended action</span></span>

<span data-ttu-id="6d1ff-116">Для экземпляров <xref:System.Text.RegularExpressions.GroupCollection> устраните неоднозначность вызовов методов расширения, которые принимают `IEnumerable<T>`, путем приведения.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-116">For <xref:System.Text.RegularExpressions.GroupCollection> instances, disambiguate calls to extension methods that accept an `IEnumerable<T>` with a cast.</span></span>

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a><span data-ttu-id="6d1ff-117">Категория</span><span class="sxs-lookup"><span data-stu-id="6d1ff-117">Category</span></span>

<span data-ttu-id="6d1ff-118">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="6d1ff-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d1ff-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="6d1ff-119">Affected APIs</span></span>

<span data-ttu-id="6d1ff-120">Затрагиваются все методы расширения, принимающие <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-120">Any extension method that accepts an <xref:System.Collections.Generic.IEnumerable%601> is affected.</span></span> <span data-ttu-id="6d1ff-121">Пример:</span><span class="sxs-lookup"><span data-stu-id="6d1ff-121">For example:</span></span>

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- <span data-ttu-id="6d1ff-122">Большинство методов `System.Linq.Enumerable`, например <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6d1ff-122">Most of the `System.Linq.Enumerable` methods, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span></span>
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->
