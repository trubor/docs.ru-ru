---
description: 'Дополнительные сведения о: BC32128: операнд "IsNot" типа "typename" можно сравнивать только с "Nothing", поскольку "typename" является типом, допускающим значение null'
title: Операнд IsNot типа  можно сравнить только с Nothing, так как  является типом, допускающим значение NULL
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 732c8bee2ae352824c7d50bba8b2b35598d6f53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795993"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="e6dec-103">BC32128: операнд "IsNot" типа "typename" может сравниваться только с "Nothing", поскольку "typename" является типом, допускающим значение null</span><span class="sxs-lookup"><span data-stu-id="e6dec-103">BC32128: 'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="e6dec-104">Переменная, объявленная как тип значения, допускающего значение null, была сравнена с выражением, отличным от `Nothing` `IsNot` оператора.</span><span class="sxs-lookup"><span data-stu-id="e6dec-104">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="e6dec-105">**Идентификатор ошибки:** BC32128</span><span class="sxs-lookup"><span data-stu-id="e6dec-105">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e6dec-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e6dec-106">To correct this error</span></span>

<span data-ttu-id="e6dec-107">Чтобы сравнить тип, допускающий значение null, с выражением, отличным от `Nothing` , с помощью оператора `IsNot` , вызовите метод `GetType` для типа, допускающего значение null, и сравните результат с выражением, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e6dec-107">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="e6dec-108">См. также</span><span class="sxs-lookup"><span data-stu-id="e6dec-108">See also</span></span>

- [<span data-ttu-id="e6dec-109">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="e6dec-109">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="e6dec-110">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="e6dec-110">IsNot Operator</span></span>](../operators/isnot-operator.md)
