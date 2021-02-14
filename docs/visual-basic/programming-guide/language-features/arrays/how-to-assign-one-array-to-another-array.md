---
description: Дополнительные сведения см. в статье как присвоить один массив другому массиву (Visual Basic).
title: Практическое руководство. Присвоение одного массива другому
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: dc86225c1f25c207e793e33a048d948646ac77b6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434736"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="d7cad-103">Практическое руководство. Присвоение одного массива другому (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7cad-103">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="d7cad-104">Поскольку массивы являются объектами, их можно использовать в инструкциях присваивания, например в других типах объектов.</span><span class="sxs-lookup"><span data-stu-id="d7cad-104">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="d7cad-105">Переменная массива содержит указатель на данные, образующей элементы массива, и сведения о ранге и длине, и присваивание копирует только этот указатель.</span><span class="sxs-lookup"><span data-stu-id="d7cad-105">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="d7cad-106">Назначение одного массива другому массиву</span><span class="sxs-lookup"><span data-stu-id="d7cad-106">To assign one array to another array</span></span>

1. <span data-ttu-id="d7cad-107">Убедитесь, что два массива имеют одинаковый ранг (число измерений) и совместимые типы данных элементов.</span><span class="sxs-lookup"><span data-stu-id="d7cad-107">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="d7cad-108">Используйте стандартную инструкцию присваивания, чтобы присвоить исходный массив целевому массиву.</span><span class="sxs-lookup"><span data-stu-id="d7cad-108">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="d7cad-109">Не используйте имя массива с круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="d7cad-109">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="d7cad-110">При назначении одного массива другому применяются следующие правила.</span><span class="sxs-lookup"><span data-stu-id="d7cad-110">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="d7cad-111">**Равные ранги.**</span><span class="sxs-lookup"><span data-stu-id="d7cad-111">**Equal Ranks.**</span></span> <span data-ttu-id="d7cad-112">Ранг (количество измерений) массива назначения должен быть таким же, как и у исходного массива.</span><span class="sxs-lookup"><span data-stu-id="d7cad-112">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="d7cad-113">При условии, что ранги двух массивов равны, измерения не обязательно должны быть равны.</span><span class="sxs-lookup"><span data-stu-id="d7cad-113">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="d7cad-114">Количество элементов в заданном измерении может изменяться во время назначения.</span><span class="sxs-lookup"><span data-stu-id="d7cad-114">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="d7cad-115">**Типы элементов.**</span><span class="sxs-lookup"><span data-stu-id="d7cad-115">**Element Types.**</span></span> <span data-ttu-id="d7cad-116">Оба массива должны иметь элементы *ссылочного типа* либо оба массива должны иметь элементы *типа значения* .</span><span class="sxs-lookup"><span data-stu-id="d7cad-116">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="d7cad-117">Дополнительные сведения см. в разделе [типы значений и ссылочные типы](../data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="d7cad-117">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="d7cad-118">Если оба массива имеют элементы типа значения, то типы данных элементов должны быть одинаковыми.</span><span class="sxs-lookup"><span data-stu-id="d7cad-118">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="d7cad-119">Единственным исключением является то, что массив элементов можно назначить `Enum` массиву базового типа `Enum` .</span><span class="sxs-lookup"><span data-stu-id="d7cad-119">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="d7cad-120">Если оба массива имеют элементы ссылочного типа, тип исходного элемента должен быть производным от типа целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="d7cad-120">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="d7cad-121">В этом случае два массива имеют те же отношения наследования, что и их элементы.</span><span class="sxs-lookup"><span data-stu-id="d7cad-121">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="d7cad-122">Это называется *ковариацией массивов*.</span><span class="sxs-lookup"><span data-stu-id="d7cad-122">This is called *array covariance*.</span></span>

<span data-ttu-id="d7cad-123">Компилятор сообщает об ошибке, если приведенные выше правила нарушаются, например, если типы данных несовместимы или ранги не равны.</span><span class="sxs-lookup"><span data-stu-id="d7cad-123">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="d7cad-124">В код можно добавить обработку ошибок, чтобы убедиться, что массивы совместимы, прежде чем пытаться выполнить назначение.</span><span class="sxs-lookup"><span data-stu-id="d7cad-124">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="d7cad-125">Можно также использовать ключевое слово [оператора TryCast](../../../language-reference/operators/trycast-operator.md) , если необходимо избежать возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="d7cad-125">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7cad-126">См. также</span><span class="sxs-lookup"><span data-stu-id="d7cad-126">See also</span></span>

- [<span data-ttu-id="d7cad-127">Массивы</span><span class="sxs-lookup"><span data-stu-id="d7cad-127">Arrays</span></span>](index.md)
- [<span data-ttu-id="d7cad-128">Устранение неполадок, связанных с массивами</span><span class="sxs-lookup"><span data-stu-id="d7cad-128">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="d7cad-129">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="d7cad-129">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="d7cad-130">Преобразования массивов</span><span class="sxs-lookup"><span data-stu-id="d7cad-130">Array Conversions</span></span>](../data-types/array-conversions.md)
