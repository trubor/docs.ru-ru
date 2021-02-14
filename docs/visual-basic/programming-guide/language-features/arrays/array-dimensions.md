---
description: Дополнительные сведения об измерениях массива см. в Visual Basic
title: Измерения массива
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 055a3efc1410bf80daf3804453adc2c20266733c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486554"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="18396-103">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18396-103">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="18396-104">*Измерение* — это направление, в котором можно изменять спецификацию элементов массива.</span><span class="sxs-lookup"><span data-stu-id="18396-104">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="18396-105">В массиве, содержащем общую сумму продаж за каждый день месяца, должно быть одно измерение (день месяца).</span><span class="sxs-lookup"><span data-stu-id="18396-105">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="18396-106">Массив, содержащий сумму продаж по Отделу для каждого дня месяца, имеет два измерения (номер отдела и день месяца).</span><span class="sxs-lookup"><span data-stu-id="18396-106">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="18396-107">Количество измерений массива называется его *рангом*.</span><span class="sxs-lookup"><span data-stu-id="18396-107">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="18396-108">Свойство можно использовать <xref:System.Array.Rank%2A> для определения количества измерений массива.</span><span class="sxs-lookup"><span data-stu-id="18396-108">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="18396-109">Работа с измерениями</span><span class="sxs-lookup"><span data-stu-id="18396-109">Working with Dimensions</span></span>

<span data-ttu-id="18396-110">Элемент массива указывается путем предоставления *индекса* или *подстрочного скрипта* для каждого из его измерений.</span><span class="sxs-lookup"><span data-stu-id="18396-110">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="18396-111">Элементы являются непрерывными по отношению к каждому измерению от индекса 0 до самого высокого индекса для этого измерения.</span><span class="sxs-lookup"><span data-stu-id="18396-111">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="18396-112">На следующих иллюстрациях показана концептуальная структура массивов с разными рангами.</span><span class="sxs-lookup"><span data-stu-id="18396-112">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="18396-113">Каждый элемент на иллюстрациях показывает значения индекса, к которым он обращается.</span><span class="sxs-lookup"><span data-stu-id="18396-113">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="18396-114">Например, можно получить доступ к первому элементу второй строки двумерного массива, указав индексы `(1, 0)` .</span><span class="sxs-lookup"><span data-stu-id="18396-114">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Схема, на которой показан одномерный массив.](./media/array-dimensions/one-dimensional-array.gif)

![Схема, на которой показан двухмерный массив.](./media/array-dimensions/two-dimensional-array.gif)

![Схема, на которой показан трехмерный массив.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="18396-118">Одно измерение</span><span class="sxs-lookup"><span data-stu-id="18396-118">One Dimension</span></span>

<span data-ttu-id="18396-119">Многие массивы имеют только одно измерение, например число людей каждого возраста.</span><span class="sxs-lookup"><span data-stu-id="18396-119">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="18396-120">Единственным требованием для указания элемента является возраст, для которого этот элемент содержит число.</span><span class="sxs-lookup"><span data-stu-id="18396-120">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="18396-121">Таким образом, такой массив использует только один индекс.</span><span class="sxs-lookup"><span data-stu-id="18396-121">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="18396-122">В следующем примере объявляется переменная для хранения *одномерного массива* счетчиков возраста в возрасте от 0 до 120.</span><span class="sxs-lookup"><span data-stu-id="18396-122">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="18396-123">Два измерения</span><span class="sxs-lookup"><span data-stu-id="18396-123">Two Dimensions</span></span>

<span data-ttu-id="18396-124">Некоторые массивы имеют два измерения, такие как количество офисов на каждом этаже каждого здания на кампусе.</span><span class="sxs-lookup"><span data-stu-id="18396-124">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="18396-125">Спецификация элемента требует как номер здания, так и этаж, и каждый элемент содержит количество для этого сочетания здания и этажа.</span><span class="sxs-lookup"><span data-stu-id="18396-125">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="18396-126">Таким образом, такой массив использует два индекса.</span><span class="sxs-lookup"><span data-stu-id="18396-126">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="18396-127">В следующем примере объявляется переменная для хранения *двумерного массива* счетчиков Office, для зданий от 0 до 40 и этажей от 0 до 5.</span><span class="sxs-lookup"><span data-stu-id="18396-127">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="18396-128">Двумерный массив также называется *прямоугольным массивом*.</span><span class="sxs-lookup"><span data-stu-id="18396-128">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="18396-129">Три измерения</span><span class="sxs-lookup"><span data-stu-id="18396-129">Three Dimensions</span></span>

<span data-ttu-id="18396-130">Несколько массивов имеют три измерения, такие как значения в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="18396-130">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="18396-131">Такой массив использует три индекса, которые в данном случае представляют координаты x, y и z физического пространства.</span><span class="sxs-lookup"><span data-stu-id="18396-131">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="18396-132">В следующем примере объявляется переменная для хранения *трехмерного массива* температур воздуха в различных точках трехмерного тома.</span><span class="sxs-lookup"><span data-stu-id="18396-132">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="18396-133">Более трех измерений</span><span class="sxs-lookup"><span data-stu-id="18396-133">More than Three Dimensions</span></span>

<span data-ttu-id="18396-134">Несмотря на то, что массив может иметь столько же измерений, как 32, редко бывает больше трех.</span><span class="sxs-lookup"><span data-stu-id="18396-134">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="18396-135">При добавлении измерений в массив значительно возрастает объем необходимого для массива хранилища, поэтому используйте многомерные массивы с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="18396-135">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="18396-136">Использование различных измерений</span><span class="sxs-lookup"><span data-stu-id="18396-136">Using Different Dimensions</span></span>

<span data-ttu-id="18396-137">Предположим, что требуется отслеживание объемов продаж за каждый день текущего месяца.</span><span class="sxs-lookup"><span data-stu-id="18396-137">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="18396-138">Вы можете объявить одномерный массив с 31 элементами, по одному на каждый день месяца, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="18396-138">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="18396-139">Теперь предположим, что необходимо отвести одну и ту же информацию не только для каждого дня месяца, но и для каждого месяца года.</span><span class="sxs-lookup"><span data-stu-id="18396-139">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="18396-140">Можно объявить двумерный массив с 12 строками (для месяцев) и 31 столбцами (в днях), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="18396-140">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="18396-141">Теперь предположим, что вы решили, чтобы ваш массив содержал данные в течение более чем одного года.</span><span class="sxs-lookup"><span data-stu-id="18396-141">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="18396-142">Если вы хотите отследить объем продаж в течение 5 лет, можно объявить трехмерный массив с 5 слоями, 12 строками и 31 столбцами, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="18396-142">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="18396-143">Обратите внимание, что, поскольку каждый индекс может иметь значение от 0 до его максимального значения, каждое измерение класса `salesAmounts` объявляется как значение, меньшее, чем требуемая длина для этого измерения.</span><span class="sxs-lookup"><span data-stu-id="18396-143">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="18396-144">Обратите внимание, что размер массива увеличивается с каждым новым измерением.</span><span class="sxs-lookup"><span data-stu-id="18396-144">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="18396-145">Три размера в предыдущих примерах — 31, 372 и 1 860 соответственно.</span><span class="sxs-lookup"><span data-stu-id="18396-145">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="18396-146">Массив можно создать без использования `Dim` оператора или `New` предложения.</span><span class="sxs-lookup"><span data-stu-id="18396-146">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="18396-147">Например, можно вызвать <xref:System.Array.CreateInstance%2A> метод, или другой компонент может передать ваш код массиву, созданному таким образом.</span><span class="sxs-lookup"><span data-stu-id="18396-147">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="18396-148">Такой массив может иметь нижнюю границу, отличную от 0.</span><span class="sxs-lookup"><span data-stu-id="18396-148">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="18396-149">Вы всегда можете проверить нижнюю границу измерения с помощью <xref:System.Array.GetLowerBound%2A> метода или `LBound` функции.</span><span class="sxs-lookup"><span data-stu-id="18396-149">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="18396-150">См. также</span><span class="sxs-lookup"><span data-stu-id="18396-150">See also</span></span>

- [<span data-ttu-id="18396-151">Массивы</span><span class="sxs-lookup"><span data-stu-id="18396-151">Arrays</span></span>](index.md)
- [<span data-ttu-id="18396-152">Устранение неполадок, связанных с массивами</span><span class="sxs-lookup"><span data-stu-id="18396-152">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
