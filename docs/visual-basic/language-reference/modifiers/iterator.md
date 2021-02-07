---
description: 'Дополнительные сведения: итератор (Visual Basic)'
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 7a3329ba23a3f2487343b332f3bb9c4b19c36496
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730529"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="53258-103">Итератор (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53258-103">Iterator (Visual Basic)</span></span>

<span data-ttu-id="53258-104">Указывает, что функция или `Get` метод доступа являются итератором.</span><span class="sxs-lookup"><span data-stu-id="53258-104">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53258-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="53258-105">Remarks</span></span>  

 <span data-ttu-id="53258-106">*Итератор* выполняет настраиваемую итерацию по коллекции.</span><span class="sxs-lookup"><span data-stu-id="53258-106">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="53258-107">Итератор использует оператор [yield](../statements/yield-statement.md) для возвращения каждого элемента в коллекции по одному за раз.</span><span class="sxs-lookup"><span data-stu-id="53258-107">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="53258-108">При `Yield` достижении оператора текущее место в коде сохраняется.</span><span class="sxs-lookup"><span data-stu-id="53258-108">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="53258-109">При следующем вызове функции итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="53258-109">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="53258-110">Итератор может быть реализован в виде функции или `Get` метода доступа к определению свойства.</span><span class="sxs-lookup"><span data-stu-id="53258-110">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="53258-111">`Iterator`Модификатор отображается в объявлении функции итератора или `Get` метода доступа.</span><span class="sxs-lookup"><span data-stu-id="53258-111">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="53258-112">Итератор вызывается из клиентского кода с помощью метода [For Each... Следующий оператор](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="53258-112">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="53258-113">Тип возвращаемого значения функции итератора или `Get` метода доступа может быть <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="53258-113">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="53258-114">Итератор не может иметь `ByRef` параметров.</span><span class="sxs-lookup"><span data-stu-id="53258-114">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="53258-115">Итератор не может использоваться в событии, конструкторе экземпляра, статическом конструкторе или статическом деструкторе.</span><span class="sxs-lookup"><span data-stu-id="53258-115">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="53258-116">Итератор может быть анонимной функцией.</span><span class="sxs-lookup"><span data-stu-id="53258-116">An iterator can be an anonymous function.</span></span> <span data-ttu-id="53258-117">Дополнительные сведения см. в разделе [Итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="53258-117">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="53258-118">Использование</span><span class="sxs-lookup"><span data-stu-id="53258-118">Usage</span></span>  

 <span data-ttu-id="53258-119">Модификатор `Iterator` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="53258-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="53258-120">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="53258-120">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="53258-121">Property Statement</span><span class="sxs-lookup"><span data-stu-id="53258-121">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="53258-122">Пример</span><span class="sxs-lookup"><span data-stu-id="53258-122">Example</span></span>  

 <span data-ttu-id="53258-123">В следующем примере демонстрируется функция итератора.</span><span class="sxs-lookup"><span data-stu-id="53258-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="53258-124">Функция итератора содержит `Yield` оператор, который находится внутри блока [for... Следующий](../statements/for-next-statement.md) цикл.</span><span class="sxs-lookup"><span data-stu-id="53258-124">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="53258-125">Каждая итерация тела оператора [for each](../statements/for-each-next-statement.md) в `Main` создает вызов `Power` функции итератора.</span><span class="sxs-lookup"><span data-stu-id="53258-125">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="53258-126">При каждом вызове функции итератора происходит переход к следующему выполнению оператора `Yield`, которое осуществляется во время следующей итерации цикла `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="53258-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="53258-127">Пример</span><span class="sxs-lookup"><span data-stu-id="53258-127">Example</span></span>  

 <span data-ttu-id="53258-128">В следующем примере демонстрируется метод доступа `Get`, представляющий собой итератор.</span><span class="sxs-lookup"><span data-stu-id="53258-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="53258-129">`Iterator`Модификатор находится в объявлении свойства.</span><span class="sxs-lookup"><span data-stu-id="53258-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="53258-130">Дополнительные примеры см. в разделе [итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="53258-130">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53258-131">См. также</span><span class="sxs-lookup"><span data-stu-id="53258-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="53258-132">Итераторы</span><span class="sxs-lookup"><span data-stu-id="53258-132">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="53258-133">Оператор Yield</span><span class="sxs-lookup"><span data-stu-id="53258-133">Yield Statement</span></span>](../statements/yield-statement.md)
