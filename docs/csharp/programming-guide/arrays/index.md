---
title: Руководство по программированию на C#. Массивы
description: Храните несколько переменных одного типа в структуре данных массива на C#. Объявите массив, указав тип или указав объект для хранения любого типа.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794768"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="0155c-104">Массивы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="0155c-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="0155c-105">В структуре данных массива можно хранить несколько переменных одного типа.</span><span class="sxs-lookup"><span data-stu-id="0155c-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="0155c-106">Чтобы объявить массив, следует указать тип его элементов.</span><span class="sxs-lookup"><span data-stu-id="0155c-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="0155c-107">Если требуется, чтобы массив мог хранить элементы любого типа, можно указать `object` в качестве его типа.</span><span class="sxs-lookup"><span data-stu-id="0155c-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="0155c-108">В унифицированной системе типов C# все типы, стандартные и определяемые пользователем, ссылочные типы и типы значений напрямую или косвенно наследуются из <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0155c-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="0155c-109">Пример</span><span class="sxs-lookup"><span data-stu-id="0155c-109">Example</span></span>

<span data-ttu-id="0155c-110">В следующих примерах создаются одномерные массивы, многомерные массивы и массивы массивов:</span><span class="sxs-lookup"><span data-stu-id="0155c-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="0155c-111">Общие сведения о массивах</span><span class="sxs-lookup"><span data-stu-id="0155c-111">Array overview</span></span>

<span data-ttu-id="0155c-112">Массив имеет следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="0155c-112">An array has the following properties:</span></span>

- <span data-ttu-id="0155c-113">Массив может быть [одномерным](single-dimensional-arrays.md), [многомерным](multidimensional-arrays.md) или [массивом массивов](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="0155c-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="0155c-114">Количество измерений и длина каждого из измерений задаются, когда создается экземпляр массива.</span><span class="sxs-lookup"><span data-stu-id="0155c-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="0155c-115">Эти значения нельзя изменить во время существования экземпляра.</span><span class="sxs-lookup"><span data-stu-id="0155c-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="0155c-116">Используемые по умолчанию значения числовых элементов массива равны нулю, и элементам ссылки присвоено значение NULL.</span><span class="sxs-lookup"><span data-stu-id="0155c-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="0155c-117">В массиве массивов элементы являются ссылочными типами и инициализируются значением `null`.</span><span class="sxs-lookup"><span data-stu-id="0155c-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="0155c-118">Массивы индексируются от нуля: массив с `n` элементами индексируется от `0` до `n-1`.</span><span class="sxs-lookup"><span data-stu-id="0155c-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="0155c-119">Элементы массива могут иметь любой тип, в том числе тип массива.</span><span class="sxs-lookup"><span data-stu-id="0155c-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="0155c-120">Типы массивов — это [ссылочные типы](../../language-reference/keywords/reference-types.md), производные от абстрактного базового типа <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="0155c-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="0155c-121">Поскольку этот тип реализует <xref:System.Collections.IEnumerable> и <xref:System.Collections.Generic.IEnumerable%601>, вы можете просматривать в цикле [foreach](../../language-reference/keywords/foreach-in.md) любые массивы C#.</span><span class="sxs-lookup"><span data-stu-id="0155c-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="0155c-122">Массивы как объекты</span><span class="sxs-lookup"><span data-stu-id="0155c-122">Arrays as Objects</span></span>

<span data-ttu-id="0155c-123">В C# массивы представляют собой реальные объекты, а не просто адресуемые области непрерывной памяти, как в C и C++.</span><span class="sxs-lookup"><span data-stu-id="0155c-123">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="0155c-124"><xref:System.Array> — это абстрактный базовый тип для всех типов массивов.</span><span class="sxs-lookup"><span data-stu-id="0155c-124"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="0155c-125">Вы можете использовать свойства и другие члены класса, входящие в <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="0155c-125">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="0155c-126">Например, с помощью свойства <xref:System.Array.Length%2A> можно получить длину массива.</span><span class="sxs-lookup"><span data-stu-id="0155c-126">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="0155c-127">В следующем коде значение длины массива `numbers` (`5`) присваивается переменной с именем `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="0155c-127">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="0155c-128">В классе <xref:System.Array> представлено множество других полезных методов и свойств для сортировки, поиска и копирования массивов.</span><span class="sxs-lookup"><span data-stu-id="0155c-128">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="0155c-129">В следующем примере свойство <xref:System.Array.Rank%2A> используется для отображения количества измерений массива.</span><span class="sxs-lookup"><span data-stu-id="0155c-129">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="0155c-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0155c-130">See also</span></span>

- [<span data-ttu-id="0155c-131">Как использовать одномерные массивы</span><span class="sxs-lookup"><span data-stu-id="0155c-131">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="0155c-132">Как использовать многомерные массивы</span><span class="sxs-lookup"><span data-stu-id="0155c-132">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="0155c-133">Как использовать массивы массивов</span><span class="sxs-lookup"><span data-stu-id="0155c-133">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="0155c-134">Использование оператора foreach с массивами</span><span class="sxs-lookup"><span data-stu-id="0155c-134">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="0155c-135">Передача массивов в качестве аргументов</span><span class="sxs-lookup"><span data-stu-id="0155c-135">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="0155c-136">Неявно типизированные массивы</span><span class="sxs-lookup"><span data-stu-id="0155c-136">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="0155c-137">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="0155c-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0155c-138">Коллекции</span><span class="sxs-lookup"><span data-stu-id="0155c-138">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
