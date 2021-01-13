---
title: Руководство по программированию на C#. Массивы массивов
description: Массив массивов в C# — это массив, элементы которого являются массивами различных размеров. Узнайте, как объявлять и инициализировать массивы массивов, а также получать доступ к ним.
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737285"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="1323e-104">Массивы массивов (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="1323e-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1323e-105">Массив массивов — это массив, элементы которого являются массивами и могут быть различных размеров.</span><span class="sxs-lookup"><span data-stu-id="1323e-105">A jagged array is an array whose elements are arrays, possibly of different sizes.</span></span> <span data-ttu-id="1323e-106">Массив массивов иногда называется нерегулярным массивом.</span><span class="sxs-lookup"><span data-stu-id="1323e-106">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="1323e-107">В следующих примерах показано, как объявлять и инициализировать массивы массивов, а также получать доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="1323e-107">The following examples show how to declare, initialize, and access jagged arrays.</span></span>

 <span data-ttu-id="1323e-108">Ниже объявляется одномерный массив из трех элементов, каждый из которых является одномерным массивом целых чисел:</span><span class="sxs-lookup"><span data-stu-id="1323e-108">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 <span data-ttu-id="1323e-109">Прежде чем использовать `jaggedArray`, его элементы необходимо инициализировать.</span><span class="sxs-lookup"><span data-stu-id="1323e-109">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="1323e-110">Это можно сделать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1323e-110">You can initialize the elements like this:</span></span>

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 <span data-ttu-id="1323e-111">Каждый элемент представляет собой одномерный массив целых чисел.</span><span class="sxs-lookup"><span data-stu-id="1323e-111">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="1323e-112">Первый из них содержит 5 целых чисел, второй — 4, а третий — 2.</span><span class="sxs-lookup"><span data-stu-id="1323e-112">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>

 <span data-ttu-id="1323e-113">Кроме того, с помощью инициализаторов можно заполнять элементы массива значениями (при этом вам не потребуется знать размер массива).</span><span class="sxs-lookup"><span data-stu-id="1323e-113">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="1323e-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="1323e-114">For example:</span></span>

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 <span data-ttu-id="1323e-115">Также массив можно инициализировать при объявлении, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="1323e-115">You can also initialize the array upon declaration like this:</span></span>

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 <span data-ttu-id="1323e-116">Можно использовать следующую краткую форму.</span><span class="sxs-lookup"><span data-stu-id="1323e-116">You can use the following shorthand form.</span></span> <span data-ttu-id="1323e-117">Обратите внимание, что при инициализации элементов нельзя опускать оператор `new`, поскольку механизм инициализации по умолчанию для них не предусмотрен:</span><span class="sxs-lookup"><span data-stu-id="1323e-117">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 <span data-ttu-id="1323e-118">В массиве массивов элементы являются ссылочными типами и инициализируются значением `null`.</span><span class="sxs-lookup"><span data-stu-id="1323e-118">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>

 <span data-ttu-id="1323e-119">Доступ к отдельным элементам массива можно получить способами, показанными в следующих примерах:</span><span class="sxs-lookup"><span data-stu-id="1323e-119">You can access individual array elements like these examples:</span></span>

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 <span data-ttu-id="1323e-120">Массивы массивов и многомерные массивы можно смешивать.</span><span class="sxs-lookup"><span data-stu-id="1323e-120">It's possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="1323e-121">Ниже показаны объявление и инициализация одномерного массива массивов, элементами которого являются двухмерные массивы разного размера.</span><span class="sxs-lookup"><span data-stu-id="1323e-121">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="1323e-122">Дополнительные сведения см. в разделе [Многомерные массивы](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1323e-122">For more information, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 <span data-ttu-id="1323e-123">В этом примере демонстрируется доступ к отдельным элементам, для чего отображается значение элемента `[1,0]` первого массива (`5`):</span><span class="sxs-lookup"><span data-stu-id="1323e-123">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 <span data-ttu-id="1323e-124">Метод `Length` возвращает число массивов, содержащихся в массиве массивов.</span><span class="sxs-lookup"><span data-stu-id="1323e-124">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="1323e-125">Допустим, предыдущий массив был объявлен с использованием следующей строки:</span><span class="sxs-lookup"><span data-stu-id="1323e-125">For example, assuming you have declared the previous array, this line:</span></span>

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 <span data-ttu-id="1323e-126">возвращает значение 3.</span><span class="sxs-lookup"><span data-stu-id="1323e-126">returns a value of 3.</span></span>

## <a name="example"></a><span data-ttu-id="1323e-127">Пример</span><span class="sxs-lookup"><span data-stu-id="1323e-127">Example</span></span>

 <span data-ttu-id="1323e-128">В этом примере создается массив, элементы которого являются массивами.</span><span class="sxs-lookup"><span data-stu-id="1323e-128">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="1323e-129">Все элементы массива имеют разный размер.</span><span class="sxs-lookup"><span data-stu-id="1323e-129">Each one of the array elements has a different size.</span></span>

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a><span data-ttu-id="1323e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1323e-130">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="1323e-131">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="1323e-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1323e-132">Массивы</span><span class="sxs-lookup"><span data-stu-id="1323e-132">Arrays</span></span>](./index.md)
- [<span data-ttu-id="1323e-133">Одномерные массивы</span><span class="sxs-lookup"><span data-stu-id="1323e-133">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="1323e-134">Многомерные массивы</span><span class="sxs-lookup"><span data-stu-id="1323e-134">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
