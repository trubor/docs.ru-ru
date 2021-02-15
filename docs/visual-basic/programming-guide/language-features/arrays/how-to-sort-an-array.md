---
description: Дополнительные сведения см. в статье как сортировать массив в Visual Basic
title: Практическое руководство. Сортировка массива
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: ea030b63dbbb5f5ea1d6160757afe2e9b58f7c21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462767"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="e38be-103">Как сортировать массив в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e38be-103">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="e38be-104">В этой статье показан пример сортировки массива строк в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e38be-104">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="e38be-105">Пример</span><span class="sxs-lookup"><span data-stu-id="e38be-105">Example</span></span>

<span data-ttu-id="e38be-106">В этом примере объявляется массив `String` объектов с именем `zooAnimals` , заполняется, а затем сортируется по алфавиту:</span><span class="sxs-lookup"><span data-stu-id="e38be-106">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="e38be-107">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="e38be-107">Robust programming</span></span>

<span data-ttu-id="e38be-108">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="e38be-108">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e38be-109">Массив пуст ( <xref:System.ArgumentNullException> класс).</span><span class="sxs-lookup"><span data-stu-id="e38be-109">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="e38be-110">Массив является многомерным ( <xref:System.RankException> классом).</span><span class="sxs-lookup"><span data-stu-id="e38be-110">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="e38be-111">Один или несколько элементов массива не реализуют <xref:System.IComparable> интерфейс ( <xref:System.InvalidOperationException> класс).</span><span class="sxs-lookup"><span data-stu-id="e38be-111">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="e38be-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e38be-112">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e38be-113">Массивы</span><span class="sxs-lookup"><span data-stu-id="e38be-113">Arrays</span></span>](index.md)
- [<span data-ttu-id="e38be-114">Устранение неполадок, связанных с массивами</span><span class="sxs-lookup"><span data-stu-id="e38be-114">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="e38be-115">Коллекции</span><span class="sxs-lookup"><span data-stu-id="e38be-115">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="e38be-116">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="e38be-116">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
