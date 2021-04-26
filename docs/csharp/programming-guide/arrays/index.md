---
title: Руководство по программированию на C#. Массивы
description: Храните несколько переменных одного типа в структуре данных массива на C#. Объявите массив, указав тип или указав объект для хранения любого типа.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: d55e177d18c0dc483f3419966042e42f1e41ed26
ms.sourcegitcommit: 178ccefa8c454bfae844ce12ed222a54913df157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2021
ms.locfileid: "107883310"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="4423f-104">Массивы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="4423f-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="4423f-105">В структуре данных массива можно хранить несколько переменных одного типа.</span><span class="sxs-lookup"><span data-stu-id="4423f-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="4423f-106">Чтобы объявить массив, следует указать тип его элементов.</span><span class="sxs-lookup"><span data-stu-id="4423f-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="4423f-107">Если требуется, чтобы массив мог хранить элементы любого типа, можно указать `object` в качестве его типа.</span><span class="sxs-lookup"><span data-stu-id="4423f-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="4423f-108">В унифицированной системе типов C# все типы, стандартные и определяемые пользователем, ссылочные типы и типы значений напрямую или косвенно наследуются из <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4423f-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="4423f-109">Пример</span><span class="sxs-lookup"><span data-stu-id="4423f-109">Example</span></span>

<span data-ttu-id="4423f-110">В следующих примерах создаются одномерные массивы, многомерные массивы и массивы массивов:</span><span class="sxs-lookup"><span data-stu-id="4423f-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="4423f-111">Общие сведения о массивах</span><span class="sxs-lookup"><span data-stu-id="4423f-111">Array overview</span></span>

<span data-ttu-id="4423f-112">Массив имеет следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="4423f-112">An array has the following properties:</span></span>

- <span data-ttu-id="4423f-113">Массив может быть [одномерным](single-dimensional-arrays.md), [многомерным](multidimensional-arrays.md) или [массивом массивов](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="4423f-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="4423f-114">Количество измерений и длина каждого из измерений задаются, когда создается экземпляр массива.</span><span class="sxs-lookup"><span data-stu-id="4423f-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="4423f-115">Эти значения нельзя изменить во время существования экземпляра.</span><span class="sxs-lookup"><span data-stu-id="4423f-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="4423f-116">Используемые по умолчанию значения числовых элементов массива равны нулю, и элементам ссылки присвоено значение NULL.</span><span class="sxs-lookup"><span data-stu-id="4423f-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="4423f-117">В массиве массивов элементы являются ссылочными типами и инициализируются значением `null`.</span><span class="sxs-lookup"><span data-stu-id="4423f-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="4423f-118">Массивы индексируются от нуля: массив с `n` элементами индексируется от `0` до `n-1`.</span><span class="sxs-lookup"><span data-stu-id="4423f-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="4423f-119">Элементы массива могут иметь любой тип, в том числе тип массива.</span><span class="sxs-lookup"><span data-stu-id="4423f-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="4423f-120">Типы массивов — это [ссылочные типы](../../language-reference/keywords/reference-types.md), производные от абстрактного базового типа <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="4423f-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="4423f-121">Все массивы реализуют <xref:System.Collections.IList> и <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4423f-121">All arrays implement <xref:System.Collections.IList>, and <xref:System.Collections.IEnumerable>.</span></span>  <span data-ttu-id="4423f-122">Вы можете использовать массивы итерации [foreach](../../language-reference/keywords/foreach-in.md) в C#,</span><span class="sxs-lookup"><span data-stu-id="4423f-122">You can use [foreach](../../language-reference/keywords/foreach-in.md) iteration arrays in C# .</span></span>  <span data-ttu-id="4423f-123">так как одномерные массивы также реализуют <xref:System.Collections.Generic.IList%601> и <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4423f-123">Since single-dimension arrays also implement <xref:System.Collections.Generic.IList%601>,  and <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="4423f-124">Массивы как объекты</span><span class="sxs-lookup"><span data-stu-id="4423f-124">Arrays as Objects</span></span>

<span data-ttu-id="4423f-125">В C# массивы представляют собой реальные объекты, а не просто адресуемые области непрерывной памяти, как в C и C++.</span><span class="sxs-lookup"><span data-stu-id="4423f-125">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="4423f-126"><xref:System.Array> — это абстрактный базовый тип для всех типов массивов.</span><span class="sxs-lookup"><span data-stu-id="4423f-126"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="4423f-127">Вы можете использовать свойства и другие члены класса, входящие в <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="4423f-127">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="4423f-128">Например, с помощью свойства <xref:System.Array.Length%2A> можно получить длину массива.</span><span class="sxs-lookup"><span data-stu-id="4423f-128">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="4423f-129">В следующем коде значение длины массива `numbers` (`5`) присваивается переменной с именем `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="4423f-129">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="4423f-130">В классе <xref:System.Array> представлено множество других полезных методов и свойств для сортировки, поиска и копирования массивов.</span><span class="sxs-lookup"><span data-stu-id="4423f-130">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="4423f-131">В следующем примере свойство <xref:System.Array.Rank%2A> используется для отображения количества измерений массива.</span><span class="sxs-lookup"><span data-stu-id="4423f-131">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="4423f-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4423f-132">See also</span></span>

- [<span data-ttu-id="4423f-133">Как использовать одномерные массивы</span><span class="sxs-lookup"><span data-stu-id="4423f-133">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="4423f-134">Как использовать многомерные массивы</span><span class="sxs-lookup"><span data-stu-id="4423f-134">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="4423f-135">Как использовать массивы массивов</span><span class="sxs-lookup"><span data-stu-id="4423f-135">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="4423f-136">Использование оператора foreach с массивами</span><span class="sxs-lookup"><span data-stu-id="4423f-136">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="4423f-137">Передача массивов в качестве аргументов</span><span class="sxs-lookup"><span data-stu-id="4423f-137">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="4423f-138">Неявно типизированные массивы</span><span class="sxs-lookup"><span data-stu-id="4423f-138">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="4423f-139">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="4423f-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4423f-140">Коллекции</span><span class="sxs-lookup"><span data-stu-id="4423f-140">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
