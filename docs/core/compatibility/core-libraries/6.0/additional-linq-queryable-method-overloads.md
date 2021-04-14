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
# <a name="new-systemlinqqueryable-method-overloads"></a><span data-ttu-id="d501d-103">Новые перегрузки методов System.Linq.Queryable</span><span class="sxs-lookup"><span data-stu-id="d501d-103">New System.Linq.Queryable method overloads</span></span>

<span data-ttu-id="d501d-104">В <xref:System.Linq.Queryable?displayProperty=fullName> добавлены дополнительные перегрузки открытых методов как часть новых возможностей, реализованных в <https://github.com/dotnet/runtime/pull/47231>.</span><span class="sxs-lookup"><span data-stu-id="d501d-104">Additional public method overloads have been added to <xref:System.Linq.Queryable?displayProperty=fullName> as part of the new features implemented in <https://github.com/dotnet/runtime/pull/47231>.</span></span> <span data-ttu-id="d501d-105">Если код отражения недостаточно надежен при поиске методов, эти добавления могут нарушить реализации поставщика запросов.</span><span class="sxs-lookup"><span data-stu-id="d501d-105">If your reflection code isn't sufficiently robust when looking up methods, these additions can break your query provider implementations.</span></span>

## <a name="change-description"></a><span data-ttu-id="d501d-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d501d-106">Change description</span></span>

<span data-ttu-id="d501d-107">В .NET 6 были добавлены новые перегрузки к методам, перечисленным в разделе [Затронутые API](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="d501d-107">In .NET 6, new overloads were added to the methods listed in the [Affected APIs](#affected-apis) section.</span></span> <span data-ttu-id="d501d-108">В результате этих добавлений может быть нарушена работа кода отражения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d501d-108">Reflection code, such as that shown in the following example, may break as a result of these additions:</span></span>

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

<span data-ttu-id="d501d-109">Этот код отражения теперь будет создавать исключение <xref:System.InvalidOperationException> примерно с таким сообщением: **Последовательность содержит более одного элемента**.</span><span class="sxs-lookup"><span data-stu-id="d501d-109">This reflection code will now throw an <xref:System.InvalidOperationException> with a message similar to: **Sequence contains more than one element**.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d501d-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d501d-110">Version introduced</span></span>

<span data-ttu-id="d501d-111">6.0 (предварительная версия 3 и предварительная версия 4)</span><span class="sxs-lookup"><span data-stu-id="d501d-111">6.0 Preview 3 and Preview 4</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d501d-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d501d-112">Reason for change</span></span>

<span data-ttu-id="d501d-113">Новые перегрузки были добавлены для расширения API `Queryable` LINQ.</span><span class="sxs-lookup"><span data-stu-id="d501d-113">The new overloads were added to extend the LINQ `Queryable` API.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d501d-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d501d-114">Recommended action</span></span>

<span data-ttu-id="d501d-115">Если вы создаете библиотеки для поставщика запросов, убедитесь, что ваш код отражения устойчив к добавлению перегрузок методов.</span><span class="sxs-lookup"><span data-stu-id="d501d-115">If you're a query-provider library author, ensure that your reflection code is tolerant of method overload additions.</span></span> <span data-ttu-id="d501d-116">Например, используйте перегрузку <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, которая явным образом принимает типы параметров метода.</span><span class="sxs-lookup"><span data-stu-id="d501d-116">For example, use a <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> overload that explicitly accepts the method's parameter types.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d501d-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d501d-117">Affected APIs</span></span>

<span data-ttu-id="d501d-118">Новые перегрузки были добавлены в следующие методы расширения <xref:System.Linq.Queryable>:</span><span class="sxs-lookup"><span data-stu-id="d501d-118">New overloads were added for the following <xref:System.Linq.Queryable> extension methods:</span></span>

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
