---
description: Дополнительные сведения см. в статье преобразования массивов (Visual Basic).
title: Преобразования массивов
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 1600042e1d41cbc2bd52468544db0e806e776d9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466410"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="5e79e-103">Преобразование массивов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e79e-103">Array Conversions (Visual Basic)</span></span>

<span data-ttu-id="5e79e-104">Тип массива можно преобразовать в другой тип массива при условии соблюдения следующих условий.</span><span class="sxs-lookup"><span data-stu-id="5e79e-104">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="5e79e-105">**Равный ранг.**</span><span class="sxs-lookup"><span data-stu-id="5e79e-105">**Equal Rank.**</span></span> <span data-ttu-id="5e79e-106">Ранги двух массивов должны быть одинаковыми, то есть они должны иметь одинаковое количество измерений.</span><span class="sxs-lookup"><span data-stu-id="5e79e-106">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="5e79e-107">Однако длины соответствующих измерений не обязательно должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="5e79e-107">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="5e79e-108">**Тип данных элемента.**</span><span class="sxs-lookup"><span data-stu-id="5e79e-108">**Element Data Type.**</span></span> <span data-ttu-id="5e79e-109">Типы данных элементов обоих массивов должны быть ссылочными типами.</span><span class="sxs-lookup"><span data-stu-id="5e79e-109">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="5e79e-110">Нельзя преобразовать `Integer` массив в `Long` массив или даже в `Object` массив, поскольку задействован хотя бы один тип значения.</span><span class="sxs-lookup"><span data-stu-id="5e79e-110">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="5e79e-111">Дополнительные сведения см. в разделе [типы значений и ссылочные типы](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="5e79e-111">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="5e79e-112">**Вариантное.**</span><span class="sxs-lookup"><span data-stu-id="5e79e-112">**Convertibility.**</span></span> <span data-ttu-id="5e79e-113">Преобразование (расширяющее или сужение) должно быть возможным между типами элементов двух массивов.</span><span class="sxs-lookup"><span data-stu-id="5e79e-113">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="5e79e-114">Пример, в котором не выполняется это требование — попытка преобразования между `String` массивом и массивом класса, производного от <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e79e-114">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e79e-115">Эти два типа не имеют ничего общего, и между ними не существует каких либо преобразований.</span><span class="sxs-lookup"><span data-stu-id="5e79e-115">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="5e79e-116">Преобразование одного типа массива в другой может расширяться или уменьшаться в зависимости от того, является ли преобразование соответствующих элементов расширяющим или узким.</span><span class="sxs-lookup"><span data-stu-id="5e79e-116">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="5e79e-117">Для получения дополнительной информации см. [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="5e79e-117">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="5e79e-118">Преобразование в массив объектов</span><span class="sxs-lookup"><span data-stu-id="5e79e-118">Conversion to an Object Array</span></span>  

 <span data-ttu-id="5e79e-119">Если массив объявляется `Object` без инициализации, его тип элемента будет таким, `Object` пока он остается неинициализированным.</span><span class="sxs-lookup"><span data-stu-id="5e79e-119">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="5e79e-120">При присвоении значения массиву определенного класса он принимает тип этого класса.</span><span class="sxs-lookup"><span data-stu-id="5e79e-120">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="5e79e-121">Однако его базовый тип по-прежнему остается `Object` , и впоследствии его можно установить в другой массив несвязанного класса.</span><span class="sxs-lookup"><span data-stu-id="5e79e-121">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="5e79e-122">Поскольку все классы являются производными от `Object` , можно изменить тип элемента массива с любого класса на любой другой класс.</span><span class="sxs-lookup"><span data-stu-id="5e79e-122">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="5e79e-123">В следующем примере не существует преобразования между типами `student` и `String` , но оба являются производными от `Object` , поэтому все назначения являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="5e79e-123">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="5e79e-124">Базовый тип массива</span><span class="sxs-lookup"><span data-stu-id="5e79e-124">Underlying Type of an Array</span></span>  

 <span data-ttu-id="5e79e-125">Если изначально был объявлен массив с конкретным классом, его базовым типом элемента является этот класс.</span><span class="sxs-lookup"><span data-stu-id="5e79e-125">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="5e79e-126">Если впоследствии задать для него массив другого класса, необходимо выполнить преобразование между двумя классами.</span><span class="sxs-lookup"><span data-stu-id="5e79e-126">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="5e79e-127">В следующем примере `students` — это `student` массив.</span><span class="sxs-lookup"><span data-stu-id="5e79e-127">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="5e79e-128">Так как преобразование между и не существует `String` `student` , последняя инструкция завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5e79e-128">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e79e-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5e79e-129">See also</span></span>

- [<span data-ttu-id="5e79e-130">Типы данных</span><span class="sxs-lookup"><span data-stu-id="5e79e-130">Data Types</span></span>](index.md)
- [<span data-ttu-id="5e79e-131">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e79e-131">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5e79e-132">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="5e79e-132">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5e79e-133">Преобразования значений между строковыми и другими типами</span><span class="sxs-lookup"><span data-stu-id="5e79e-133">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="5e79e-134">Практическое руководство. Преобразование объекта к другому типу в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e79e-134">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="5e79e-135">Типы данных</span><span class="sxs-lookup"><span data-stu-id="5e79e-135">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5e79e-136">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5e79e-136">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5e79e-137">Массивы</span><span class="sxs-lookup"><span data-stu-id="5e79e-137">Arrays</span></span>](../arrays/index.md)
