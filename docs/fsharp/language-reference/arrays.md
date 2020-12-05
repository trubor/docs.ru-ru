---
title: Массивы
description: 'Узнайте, как создавать и использовать массивы на языке программирования F #.'
ms.date: 08/13/2020
ms.openlocfilehash: 96b0d7eaf10d5afcd9a647681d5c2ef2d2fba335
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739755"
---
# <a name="arrays"></a><span data-ttu-id="9752b-103">Массивы</span><span class="sxs-lookup"><span data-stu-id="9752b-103">Arrays</span></span>

<span data-ttu-id="9752b-104">Массивы — это изменяемые коллекции последовательных элементов данных с фиксированным размером (от нуля), которые имеют один и тот же тип.</span><span class="sxs-lookup"><span data-stu-id="9752b-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="9752b-105">Создание массивов</span><span class="sxs-lookup"><span data-stu-id="9752b-105">Create arrays</span></span>

<span data-ttu-id="9752b-106">Массивы можно создавать несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="9752b-106">You can create arrays in several ways.</span></span> <span data-ttu-id="9752b-107">Можно создать небольшой массив, перечисляя последовательные значения между `[|` и `|]` и разделив их точкой с запятой, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="9752b-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="9752b-108">Можно также разместить каждый элемент на отдельной строке, в этом случае разделитель точкой с запятой является необязательным.</span><span class="sxs-lookup"><span data-stu-id="9752b-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="9752b-109">Тип элементов массива выводится из используемых литералов и должен быть единообразным.</span><span class="sxs-lookup"><span data-stu-id="9752b-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="9752b-110">Следующий код вызывает ошибку, поскольку 1,0 является числом с плавающей запятой и 2, а 3 — целыми числами.</span><span class="sxs-lookup"><span data-stu-id="9752b-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="9752b-111">Для создания массивов также можно использовать выражения последовательности.</span><span class="sxs-lookup"><span data-stu-id="9752b-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="9752b-112">Ниже приведен пример, создающий массив квадратов целых чисел от 1 до 10.</span><span class="sxs-lookup"><span data-stu-id="9752b-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="9752b-113">Чтобы создать массив, в котором все элементы инициализируются нулем, используйте `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="9752b-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="9752b-114">Элементы доступа</span><span class="sxs-lookup"><span data-stu-id="9752b-114">Access elements</span></span>

<span data-ttu-id="9752b-115">Доступ к элементам массива можно получить с помощью оператора-точки ( `.` ) и квадратных скобок ( `[` и `]` ).</span><span class="sxs-lookup"><span data-stu-id="9752b-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="9752b-116">Индексы массива начинаются с 0.</span><span class="sxs-lookup"><span data-stu-id="9752b-116">Array indexes start at 0.</span></span>

<span data-ttu-id="9752b-117">Можно также получить доступ к элементам массива с помощью нотации среза, что позволяет указать поддиапазон массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="9752b-118">Ниже приведены примеры нотаций среза.</span><span class="sxs-lookup"><span data-stu-id="9752b-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="9752b-119">При использовании нотации среза создается новая копия массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="9752b-120">Типы массивов и модули</span><span class="sxs-lookup"><span data-stu-id="9752b-120">Array types and modules</span></span>

<span data-ttu-id="9752b-121">Тип всех массивов F # является типом .NET Framework <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9752b-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9752b-122">Таким образом, массивы F # поддерживают все функциональные возможности, доступные в <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9752b-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9752b-123">[ `Array` Модуль](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) поддерживает операции с одномерные массивами.</span><span class="sxs-lookup"><span data-stu-id="9752b-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="9752b-124">Модули `Array2D` , `Array3D` и `Array4D` содержат функции, поддерживающие операции с массивами из двух, трех и четырех измерений соответственно.</span><span class="sxs-lookup"><span data-stu-id="9752b-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="9752b-125">Массивы с рангом более четырех можно создать с помощью <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9752b-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="9752b-126">Простые функции</span><span class="sxs-lookup"><span data-stu-id="9752b-126">Simple functions</span></span>

<span data-ttu-id="9752b-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Возвращает элемент.</span><span class="sxs-lookup"><span data-stu-id="9752b-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="9752b-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) Задает длину массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="9752b-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Задает для элемента указанное значение.</span><span class="sxs-lookup"><span data-stu-id="9752b-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="9752b-130">В следующем примере кода показано использование этих функций.</span><span class="sxs-lookup"><span data-stu-id="9752b-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="9752b-131">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="9752b-132">Функции, создающие массивы</span><span class="sxs-lookup"><span data-stu-id="9752b-132">Functions that create arrays</span></span>

<span data-ttu-id="9752b-133">Несколько функций создают массивы, не требуя наличия существующего массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="9752b-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) создает новый массив, который не содержит элементов.</span><span class="sxs-lookup"><span data-stu-id="9752b-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="9752b-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) создает массив указанного размера и задает для всех элементов указанные значения.</span><span class="sxs-lookup"><span data-stu-id="9752b-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="9752b-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) создает массив с учетом измерения и функции для создания элементов.</span><span class="sxs-lookup"><span data-stu-id="9752b-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="9752b-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) создает массив, в котором все элементы инициализируются значением нулевого значения для типа массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="9752b-138">Эти функции показаны в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="9752b-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="9752b-139">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="9752b-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) создает новый массив, содержащий элементы, скопированные из существующего массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="9752b-141">Обратите внимание, что копия является неполной копией, что означает, что если тип элемента является ссылочным, копируется только ссылка, а не базовый объект.</span><span class="sxs-lookup"><span data-stu-id="9752b-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="9752b-142">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="9752b-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="9752b-143">Результат выполнения приведенного выше кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9752b-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="9752b-144">Строка `Test1` отображается только в первом массиве, так как операция создания нового элемента перезаписывает ссылку в `firstArray` , но не влияет на исходную ссылку на пустую строку, которая все еще присутствует в `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="9752b-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="9752b-145">Строка `Test2` отображается в обоих массивах, так как `Insert` операция с <xref:System.Text.StringBuilder?displayProperty=nameWithType> типом влияет на базовый <xref:System.Text.StringBuilder?displayProperty=nameWithType> объект, на который имеется ссылка в обоих массивах.</span><span class="sxs-lookup"><span data-stu-id="9752b-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="9752b-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) создает новый массив из поддиапазона массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="9752b-147">Укажите поддиапазон, указав начальный индекс и длину.</span><span class="sxs-lookup"><span data-stu-id="9752b-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="9752b-148">В следующем коде показано использование функции `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="9752b-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="9752b-149">Выходные данные показывают, что подмассив начинается в элементе 5 и содержит 10 элементов.</span><span class="sxs-lookup"><span data-stu-id="9752b-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="9752b-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) создает новый массив, объединяя два существующих массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="9752b-151">В следующем примере кода демонстрируется **массив. append**.</span><span class="sxs-lookup"><span data-stu-id="9752b-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="9752b-152">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="9752b-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) выбирает элементы массива для включения в новый массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="9752b-154">В следующем коде демонстрируется `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="9752b-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="9752b-155">Обратите внимание, что тип элемента массива не обязательно должен совпадать с типом значения, возвращаемого в типе параметра.</span><span class="sxs-lookup"><span data-stu-id="9752b-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="9752b-156">В этом примере тип элемента —, `int` а параметр — результат функции полинома, в `elem*elem - 1` виде числа с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="9752b-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="9752b-157">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="9752b-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) выполняет указанную функцию для каждого элемента массива существующего массива, а затем собирает элементы, созданные функцией, и объединяет их в новый массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="9752b-159">В следующем коде демонстрируется `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="9752b-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="9752b-160">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="9752b-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) принимает последовательность массивов и объединяет их в один массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="9752b-162">В следующем коде демонстрируется `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="9752b-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="9752b-163">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="9752b-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) принимает логическую функцию-условие и создает новый массив, содержащий только те элементы из входного массива, для которых условие имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="9752b-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="9752b-165">В следующем коде демонстрируется `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="9752b-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="9752b-166">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="9752b-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) создает новый массив, переменяя порядок существующего массива на другой.</span><span class="sxs-lookup"><span data-stu-id="9752b-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="9752b-168">В следующем коде демонстрируется `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="9752b-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="9752b-169">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="9752b-170">В модуле массива можно легко объединить функции, которые преобразуют массивы с помощью конвейерного оператора ( `|>` ), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9752b-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="9752b-171">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="9752b-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="9752b-172">Многомерные массивы</span><span class="sxs-lookup"><span data-stu-id="9752b-172">Multidimensional arrays</span></span>

<span data-ttu-id="9752b-173">Можно создать многомерный массив, но для записи литерала многомерного массива нет синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="9752b-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="9752b-174">Используйте оператор, [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) чтобы создать массив из последовательности последовательностей элементов массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="9752b-175">Последовательности могут быть литералами массива или списка.</span><span class="sxs-lookup"><span data-stu-id="9752b-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="9752b-176">Например, следующий код создает двумерный массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="9752b-177">Можно также использовать функцию [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) для инициализации массивов двух измерений, а аналогичные функции доступны для массивов из трех и четырех измерений.</span><span class="sxs-lookup"><span data-stu-id="9752b-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="9752b-178">Эти функции принимают функцию, которая используется для создания элементов.</span><span class="sxs-lookup"><span data-stu-id="9752b-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="9752b-179">Чтобы создать двумерный массив, содержащий элементы, для которых задано начальное значение вместо указания функции, используйте [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) функцию, которая также доступна для массивов, размер которых не превышает четырех.</span><span class="sxs-lookup"><span data-stu-id="9752b-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="9752b-180">В следующем примере кода сначала показано, как создать массив массивов, содержащих нужные элементы, а затем использовать `Array2D.init` для создания требуемого двумерного массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="9752b-181">Синтаксис индексирования и среза массива поддерживается для массивов вплоть до ранга 4.</span><span class="sxs-lookup"><span data-stu-id="9752b-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="9752b-182">При указании индекса в нескольких измерениях для разделения индексов используются запятые, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="9752b-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="9752b-183">Тип двумерного массива записывается как `<type>[,]` (например, `int[,]` , `double[,]` ), а тип трехмерного массива записывается как `<type>[,,]` , и т. д. для массивов с большими размерами.</span><span class="sxs-lookup"><span data-stu-id="9752b-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="9752b-184">Для многомерных массивов также доступен только подмножество функций, доступных для одномерных массивов.</span><span class="sxs-lookup"><span data-stu-id="9752b-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="9752b-185">Создание срезов массива и многомерных массивов</span><span class="sxs-lookup"><span data-stu-id="9752b-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="9752b-186">В двухмерном массиве (матрице) можно извлечь подматрицу, указав диапазоны и используя символ-шаблон ( `*` ) для указания целых строк или столбцов.</span><span class="sxs-lookup"><span data-stu-id="9752b-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="9752b-187">Можно разбить многомерный массив на подмассивы того же или более низкого измерения.</span><span class="sxs-lookup"><span data-stu-id="9752b-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="9752b-188">Например, можно получить вектор из матрицы, указав одну строку или столбец.</span><span class="sxs-lookup"><span data-stu-id="9752b-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="9752b-189">Этот синтаксис среза можно использовать для типов, реализующих операторы доступа к элементам и перегруженные `GetSlice` методы.</span><span class="sxs-lookup"><span data-stu-id="9752b-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="9752b-190">Например, следующий код создает тип матрицы, который служит оболочкой для 2D-массива F #, реализует свойство Item для обеспечения поддержки индексации массива и реализует три версии `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="9752b-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="9752b-191">Если этот код можно использовать в качестве шаблона для типов матриц, можно использовать все операции по фрагментированию, описанные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="9752b-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn $"{submatrix}"

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn $"{firstCol}"
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="9752b-192">Логические функции в массивах</span><span class="sxs-lookup"><span data-stu-id="9752b-192">Boolean functions on arrays</span></span>

<span data-ttu-id="9752b-193">Функции [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) и [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) элементы теста в одном или двух массивах соответственно.</span><span class="sxs-lookup"><span data-stu-id="9752b-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="9752b-194">Эти функции принимают тестовую функцию и возвращают `true` , если существует элемент (или пара элементов для `Array.exists2` ), удовлетворяющий условию.</span><span class="sxs-lookup"><span data-stu-id="9752b-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="9752b-195">В следующем коде демонстрируется использование `Array.exists` и `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="9752b-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="9752b-196">В этих примерах новые функции создаются путем применения только одного из аргументов, в таких случаях аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="9752b-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="9752b-197">Результат приведенного выше кода выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="9752b-198">Аналогичным образом функция [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) проверяет массив, чтобы определить, удовлетворяет ли каждый элемент логическому условию.</span><span class="sxs-lookup"><span data-stu-id="9752b-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="9752b-199">Этот вариант [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) выполняет ту же функцию с помощью логической функции, включающей элементы двух массивов с одинаковой длиной.</span><span class="sxs-lookup"><span data-stu-id="9752b-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="9752b-200">В следующем коде показано использование этих функций.</span><span class="sxs-lookup"><span data-stu-id="9752b-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="9752b-201">Выходные данные для этих примеров выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="9752b-202">Поиск по массивам</span><span class="sxs-lookup"><span data-stu-id="9752b-202">Search arrays</span></span>

<span data-ttu-id="9752b-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) принимает логическую функцию и возвращает первый элемент, для которого возвращается функция `true` , или вызывает, <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> если не найден элемент, удовлетворяющий условию.</span><span class="sxs-lookup"><span data-stu-id="9752b-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="9752b-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) функция похожа на `Array.find` , за исключением того, что она возвращает индекс элемента, а не сам элемент.</span><span class="sxs-lookup"><span data-stu-id="9752b-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="9752b-205">Следующий код использует `Array.find` и `Array.findIndex` для того, чтобы узнать число, которое является как идеальным квадратом, так и идеальным кубом.</span><span class="sxs-lookup"><span data-stu-id="9752b-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="9752b-206">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="9752b-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) функция похожа `Array.find` на, за исключением того, что его результат является типом параметра и возвращается, `None` Если элемент не найден.</span><span class="sxs-lookup"><span data-stu-id="9752b-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="9752b-208">`Array.tryFind` следует использовать вместо, `Array.find` Если неизвестно, находится ли соответствующий элемент в массиве.</span><span class="sxs-lookup"><span data-stu-id="9752b-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="9752b-209">Аналогично, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) он похож на, `Array.findIndex` за исключением того, что тип параметра является возвращаемым значением.</span><span class="sxs-lookup"><span data-stu-id="9752b-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="9752b-210">Если элемент не найден, параметр имеет значение `None` .</span><span class="sxs-lookup"><span data-stu-id="9752b-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="9752b-211">В следующем коде показано использование функции `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="9752b-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="9752b-212">Этот код зависит от предыдущего кода.</span><span class="sxs-lookup"><span data-stu-id="9752b-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="9752b-213">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="9752b-214">Используется [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) , если необходимо преобразовать элемент в дополнение к его поиску.</span><span class="sxs-lookup"><span data-stu-id="9752b-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="9752b-215">Результатом является первый элемент, для которого функция возвращает преобразованный элемент в виде значения параметра или значение, `None` Если такой элемент не найден.</span><span class="sxs-lookup"><span data-stu-id="9752b-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="9752b-216">В следующем коде показано использование `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="9752b-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="9752b-217">В этом случае вместо лямбда-выражения для упрощения кода определены несколько локальных вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="9752b-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="9752b-218">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="9752b-219">Выполнение вычислений на массивах</span><span class="sxs-lookup"><span data-stu-id="9752b-219">Perform computations on arrays</span></span>

<span data-ttu-id="9752b-220">[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)Функция возвращает среднее значение каждого элемента в массиве.</span><span class="sxs-lookup"><span data-stu-id="9752b-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="9752b-221">Ограничены типами элементов, которые поддерживают точное деление на целое число, которое включает типы с плавающей запятой, но не целочисленные типы.</span><span class="sxs-lookup"><span data-stu-id="9752b-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="9752b-222">[`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)Функция возвращает среднее значение для результатов вызова функции для каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="9752b-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="9752b-223">Для массива целочисленного типа можно использовать `Array.averageBy` функцию и преобразовать каждый элемент в тип с плавающей запятой для вычисления.</span><span class="sxs-lookup"><span data-stu-id="9752b-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="9752b-224">Используйте [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) или [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) для получения максимального или минимального элемента, если тип элемента поддерживает его.</span><span class="sxs-lookup"><span data-stu-id="9752b-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="9752b-225">Аналогично, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) и [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) позволяет сначала выполнить функцию, например, для преобразования в тип, поддерживающий сравнение.</span><span class="sxs-lookup"><span data-stu-id="9752b-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="9752b-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Добавляет элементы массива и [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) вызывает функцию для каждого элемента и добавляет результаты вместе.</span><span class="sxs-lookup"><span data-stu-id="9752b-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="9752b-227">Чтобы выполнить функцию для каждого элемента в массиве без сохранения возвращаемых значений, используйте [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) .</span><span class="sxs-lookup"><span data-stu-id="9752b-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="9752b-228">Для функции, включающей два массива одинаковой длины, используйте [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) .</span><span class="sxs-lookup"><span data-stu-id="9752b-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="9752b-229">Если необходимо также разместить массив результатов функции, используйте [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) или [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , который работает с двумя массивами за раз.</span><span class="sxs-lookup"><span data-stu-id="9752b-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="9752b-230">Вариации [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) и [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) позволяют индекс элемента участвовать в вычислении; то же самое справедливо [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) и для, и [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .</span><span class="sxs-lookup"><span data-stu-id="9752b-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="9752b-231">Функции [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) ,, [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) , [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) и [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) выполняют алгоритмы, которые используют все элементы массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="9752b-232">Аналогичным образом, вариации [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) и [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) вычисления для двух массивов.</span><span class="sxs-lookup"><span data-stu-id="9752b-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="9752b-233">Эти функции для выполнения вычислений соответствуют функциям с одинаковыми именами в [модуле List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="9752b-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="9752b-234">Примеры использования см. в разделе [списки](lists.md).</span><span class="sxs-lookup"><span data-stu-id="9752b-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="9752b-235">Изменение массивов</span><span class="sxs-lookup"><span data-stu-id="9752b-235">Modify arrays</span></span>

<span data-ttu-id="9752b-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Задает для элемента указанное значение.</span><span class="sxs-lookup"><span data-stu-id="9752b-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="9752b-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) Задает для диапазона элементов в массиве указанное значение.</span><span class="sxs-lookup"><span data-stu-id="9752b-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="9752b-238">В следующем коде приведен пример `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="9752b-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="9752b-239">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9752b-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="9752b-240">Можно использовать [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) для копирования подраздела одного массива в другой массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="9752b-241">Преобразование в другие типы и из других типов</span><span class="sxs-lookup"><span data-stu-id="9752b-241">Convert to and from other types</span></span>

<span data-ttu-id="9752b-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) создает массив из списка.</span><span class="sxs-lookup"><span data-stu-id="9752b-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="9752b-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) создает массив из последовательности.</span><span class="sxs-lookup"><span data-stu-id="9752b-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="9752b-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) и [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) преобразуются в другие типы коллекций из типа массива.</span><span class="sxs-lookup"><span data-stu-id="9752b-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="9752b-245">Сортировка массивов</span><span class="sxs-lookup"><span data-stu-id="9752b-245">Sort arrays</span></span>

<span data-ttu-id="9752b-246">Используйте [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) для сортировки массива с помощью универсальной функции сравнения.</span><span class="sxs-lookup"><span data-stu-id="9752b-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="9752b-247">Используйте [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) для указания функции, которая создает значение, называемое *ключом*, для сортировки с помощью универсальной функции сравнения для ключа.</span><span class="sxs-lookup"><span data-stu-id="9752b-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="9752b-248">Используйте [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) , если требуется предоставить пользовательскую функцию сравнения.</span><span class="sxs-lookup"><span data-stu-id="9752b-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="9752b-249">`Array.sort`, `Array.sortBy` и `Array.sortWith` все возвращают отсортированный массив как новый массив.</span><span class="sxs-lookup"><span data-stu-id="9752b-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="9752b-250">Варианты [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) и [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) изменяют существующий массив вместо того, чтобы возвращать новый.</span><span class="sxs-lookup"><span data-stu-id="9752b-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="9752b-251">Массивы и кортежи</span><span class="sxs-lookup"><span data-stu-id="9752b-251">Arrays and tuples</span></span>

<span data-ttu-id="9752b-252">Функции [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) и [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) преобразуют массивы пар кортежей в кортежи массивов и наоборот.</span><span class="sxs-lookup"><span data-stu-id="9752b-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="9752b-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) и [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) похожи, за исключением того, что они работают с кортежами из трех элементов или кортежей из трех массивов.</span><span class="sxs-lookup"><span data-stu-id="9752b-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="9752b-254">Параллельные вычисления на массивах</span><span class="sxs-lookup"><span data-stu-id="9752b-254">Parallel computations on arrays</span></span>

<span data-ttu-id="9752b-255">Модуль [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) содержит функции для выполнения параллельных вычислений с массивами.</span><span class="sxs-lookup"><span data-stu-id="9752b-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="9752b-256">Этот модуль недоступен в приложениях, предназначенных для версий .NET Framework до версии 4.</span><span class="sxs-lookup"><span data-stu-id="9752b-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="9752b-257">См. также</span><span class="sxs-lookup"><span data-stu-id="9752b-257">See also</span></span>

- [<span data-ttu-id="9752b-258">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="9752b-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9752b-259">Типы языка F#</span><span class="sxs-lookup"><span data-stu-id="9752b-259">F# Types</span></span>](fsharp-types.md)
