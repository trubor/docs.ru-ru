---
title: Срезы
description: 'Узнайте, как использовать срезы для существующих типов данных F # и как определять собственные срезы для других типов данных.'
ms.date: 11/20/2020
ms.openlocfilehash: b776058df5a174dfe48dbf513bf17281036dd83e
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740384"
---
# <a name="slices"></a><span data-ttu-id="64cbb-103">Срезы</span><span class="sxs-lookup"><span data-stu-id="64cbb-103">Slices</span></span>

<span data-ttu-id="64cbb-104">В этой статье объясняется, как создавать срезы из существующих типов F # и как определять собственные срезы.</span><span class="sxs-lookup"><span data-stu-id="64cbb-104">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="64cbb-105">В F # срез является подмножеством любого типа данных.</span><span class="sxs-lookup"><span data-stu-id="64cbb-105">In F#, a slice is a subset of any data type.</span></span>  <span data-ttu-id="64cbb-106">Срезы похожи на [индексаторы](./members/indexed-properties.md), но вместо получения одного значения из базовой структуры данных они получают несколько.</span><span class="sxs-lookup"><span data-stu-id="64cbb-106">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span> <span data-ttu-id="64cbb-107">Срезы используют `..` синтаксис оператора для выбора диапазона указанных индексов в типе данных.</span><span class="sxs-lookup"><span data-stu-id="64cbb-107">Slices use the `..` operator syntax to select the range of specified indices in a data type.</span></span> <span data-ttu-id="64cbb-108">Дополнительные сведения см. в [статье Справочник по выражениям циклов](./loops-for-in-expression.md).</span><span class="sxs-lookup"><span data-stu-id="64cbb-108">For more information, see the [looping expression reference article](./loops-for-in-expression.md).</span></span>

<span data-ttu-id="64cbb-109">В настоящее время F # поддерживает встроенную поддержку для срезов строк, списков, массивов и многомерных массивов (двумерных, трехмерных, 4D).</span><span class="sxs-lookup"><span data-stu-id="64cbb-109">F# currently has intrinsic support for slicing strings, lists, arrays, and multidimensional (2D, 3D, 4D) arrays.</span></span> <span data-ttu-id="64cbb-110">Срезы чаще всего используются с массивами и списками F #.</span><span class="sxs-lookup"><span data-stu-id="64cbb-110">Slicing is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="64cbb-111">Можно добавить срез к пользовательским типам данных с помощью `GetSlice` метода в определении типа или в [расширении типа](type-extensions.md)в области.</span><span class="sxs-lookup"><span data-stu-id="64cbb-111">You can add slicing to your custom data types by using the `GetSlice` method in your type definition or in an in-scope [type extension](type-extensions.md).</span></span>

## <a name="slicing-f-lists-and-arrays"></a><span data-ttu-id="64cbb-112">Фрагментирование списков и массивов F #</span><span class="sxs-lookup"><span data-stu-id="64cbb-112">Slicing F# lists and arrays</span></span>

<span data-ttu-id="64cbb-113">Наиболее распространенными типами данных, которые являются срезами, являются списки и массивы F #.</span><span class="sxs-lookup"><span data-stu-id="64cbb-113">The most common data types that are sliced are F# lists and arrays.</span></span>  <span data-ttu-id="64cbb-114">В следующем примере показано, как разделить списки.</span><span class="sxs-lookup"><span data-stu-id="64cbb-114">The following example demonstrates how to slice lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

<span data-ttu-id="64cbb-115">Массивы срезов так же, как и списки срезов:</span><span class="sxs-lookup"><span data-stu-id="64cbb-115">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="64cbb-116">Многомерные массивы с срезами</span><span class="sxs-lookup"><span data-stu-id="64cbb-116">Slicing multidimensional arrays</span></span>

<span data-ttu-id="64cbb-117">F # поддерживает многомерные массивы в основной библиотеке F #.</span><span class="sxs-lookup"><span data-stu-id="64cbb-117">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="64cbb-118">Как и в случае с одномерным массивами, можно также использовать срезы многомерных массивов.</span><span class="sxs-lookup"><span data-stu-id="64cbb-118">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="64cbb-119">Однако введение дополнительных измерений требует немного другого синтаксиса, чтобы можно было создавать срезы конкретных строк и столбцов.</span><span class="sxs-lookup"><span data-stu-id="64cbb-119">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="64cbb-120">В следующих примерах показано, как выполнить срез 2D-массива:</span><span class="sxs-lookup"><span data-stu-id="64cbb-120">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn $"Full matrix:\n {A}"

// Take the first row
let row0 = A.[0,*]
printfn $"{row0}"

// Take the first column
let col0 = A.[*,0]
printfn $"{col0}"

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn $"{subA}"

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn $"{subA}"

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn $"{twoByTwo}"
```

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="64cbb-121">Определение срезов для других структур данных</span><span class="sxs-lookup"><span data-stu-id="64cbb-121">Defining slices for other data structures</span></span>

<span data-ttu-id="64cbb-122">Основная библиотека F # определяет срезы для ограниченного набора типов.</span><span class="sxs-lookup"><span data-stu-id="64cbb-122">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="64cbb-123">Если вы хотите определить срезы для большего числа типов данных, это можно сделать либо в самом определении типа, либо в расширении типа.</span><span class="sxs-lookup"><span data-stu-id="64cbb-123">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="64cbb-124">Например, ниже показано, как можно определить срезы для класса, <xref:System.ArraySegment%601> чтобы обеспечить удобную обработку данных:</span><span class="sxs-lookup"><span data-stu-id="64cbb-124">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

<span data-ttu-id="64cbb-125">Еще один пример использования <xref:System.Span%601> <xref:System.ReadOnlySpan%601> типов и:</span><span class="sxs-lookup"><span data-stu-id="64cbb-125">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn $"{arr}"

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="64cbb-126">Встроенные срезы F # являются конечными включительно</span><span class="sxs-lookup"><span data-stu-id="64cbb-126">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="64cbb-127">Все внутренние срезы в F # являются конечными включительно. то есть верхняя граница включается в срез.</span><span class="sxs-lookup"><span data-stu-id="64cbb-127">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="64cbb-128">Для данного среза с начальным индексом `x` и конечным индексом `y` результирующий срез будет включать значение *ИС* .</span><span class="sxs-lookup"><span data-stu-id="64cbb-128">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn $"{xs.[2..5]}" // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="64cbb-129">Встроенные пустые срезы F #</span><span class="sxs-lookup"><span data-stu-id="64cbb-129">Built-in F# empty slices</span></span>

<span data-ttu-id="64cbb-130">Списки F #, массивы, последовательности, строки, многомерные массивы (2D, 3D, 4D) будут создавать пустой срез, если синтаксис может привести к несуществующему срезу.</span><span class="sxs-lookup"><span data-stu-id="64cbb-130">F# lists, arrays, sequences, strings, multidimensional (2D, 3D, 4D) arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="64cbb-131">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="64cbb-131">Consider the following example:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> <span data-ttu-id="64cbb-132">Разработчики на C# могут вызывать исключение, а не создавать пустой срез.</span><span class="sxs-lookup"><span data-stu-id="64cbb-132">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="64cbb-133">Это решение проекта основано на том, что пустые коллекции состоят в F #.</span><span class="sxs-lookup"><span data-stu-id="64cbb-133">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="64cbb-134">Пустой список F # можно составить с помощью другого списка F #, в существующую строку можно добавить пустую строку и т. д.</span><span class="sxs-lookup"><span data-stu-id="64cbb-134">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="64cbb-135">Можно считать, что срезы основаны на значениях, переданных в качестве параметров, а также о неограниченных границах > путем создания пустой коллекции в составе природы кода F #.</span><span class="sxs-lookup"><span data-stu-id="64cbb-135">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds > by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="64cbb-136">Срезы с фиксированным индексом для массивов трехмерных и 4D</span><span class="sxs-lookup"><span data-stu-id="64cbb-136">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="64cbb-137">Для массивов 3D и 4D можно «исправить» определенный индекс и срез других измерений с фиксированным индексом.</span><span class="sxs-lookup"><span data-stu-id="64cbb-137">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="64cbb-138">Чтобы проиллюстрировать это, рассмотрим следующий трехмерный массив:</span><span class="sxs-lookup"><span data-stu-id="64cbb-138">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="64cbb-139">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="64cbb-139">*z = 0*</span></span>

| <span data-ttu-id="64cbb-140">кс\и</span><span class="sxs-lookup"><span data-stu-id="64cbb-140">x\y</span></span>   | <span data-ttu-id="64cbb-141">0</span><span class="sxs-lookup"><span data-stu-id="64cbb-141">0</span></span> | <span data-ttu-id="64cbb-142">1</span><span class="sxs-lookup"><span data-stu-id="64cbb-142">1</span></span> |
|-------|---|---|
| <span data-ttu-id="64cbb-143">**0**;</span><span class="sxs-lookup"><span data-stu-id="64cbb-143">**0**</span></span> | <span data-ttu-id="64cbb-144">0</span><span class="sxs-lookup"><span data-stu-id="64cbb-144">0</span></span> | <span data-ttu-id="64cbb-145">1</span><span class="sxs-lookup"><span data-stu-id="64cbb-145">1</span></span> |
| <span data-ttu-id="64cbb-146">**1**</span><span class="sxs-lookup"><span data-stu-id="64cbb-146">**1**</span></span> | <span data-ttu-id="64cbb-147">2</span><span class="sxs-lookup"><span data-stu-id="64cbb-147">2</span></span> | <span data-ttu-id="64cbb-148">3</span><span class="sxs-lookup"><span data-stu-id="64cbb-148">3</span></span> |

<span data-ttu-id="64cbb-149">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="64cbb-149">*z = 1*</span></span>

| <span data-ttu-id="64cbb-150">кс\и</span><span class="sxs-lookup"><span data-stu-id="64cbb-150">x\y</span></span>   | <span data-ttu-id="64cbb-151">0</span><span class="sxs-lookup"><span data-stu-id="64cbb-151">0</span></span> | <span data-ttu-id="64cbb-152">1</span><span class="sxs-lookup"><span data-stu-id="64cbb-152">1</span></span> |
|-------|---|---|
| <span data-ttu-id="64cbb-153">**0**;</span><span class="sxs-lookup"><span data-stu-id="64cbb-153">**0**</span></span> | <span data-ttu-id="64cbb-154">4</span><span class="sxs-lookup"><span data-stu-id="64cbb-154">4</span></span> | <span data-ttu-id="64cbb-155">5</span><span class="sxs-lookup"><span data-stu-id="64cbb-155">5</span></span> |
| <span data-ttu-id="64cbb-156">**1**</span><span class="sxs-lookup"><span data-stu-id="64cbb-156">**1**</span></span> | <span data-ttu-id="64cbb-157">6</span><span class="sxs-lookup"><span data-stu-id="64cbb-157">6</span></span> | <span data-ttu-id="64cbb-158">7</span><span class="sxs-lookup"><span data-stu-id="64cbb-158">7</span></span> |

<span data-ttu-id="64cbb-159">Если необходимо извлечь срез `[| 4; 5 |]` из массива, используйте срез фиксированного индекса.</span><span class="sxs-lookup"><span data-stu-id="64cbb-159">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

```fsharp
let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

<span data-ttu-id="64cbb-160">Последняя строка исправляет `y` `z` индексы и массив трехмерного массива и принимает остальные `x` значения, соответствующие матрице.</span><span class="sxs-lookup"><span data-stu-id="64cbb-160">The last line fixes the `y` and `z` indices of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="64cbb-161">См. также</span><span class="sxs-lookup"><span data-stu-id="64cbb-161">See also</span></span>

- [<span data-ttu-id="64cbb-162">Индексированные свойства</span><span class="sxs-lookup"><span data-stu-id="64cbb-162">Indexed properties</span></span>](./members/indexed-properties.md)
