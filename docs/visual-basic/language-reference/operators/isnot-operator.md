---
description: 'Дополнительные сведения: оператор IsNot (Visual Basic)'
title: IsNot - оператор
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ac3e127676dfa57d14e07838152022de62fc336b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665670"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="8d621-103">Оператор IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d621-103">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="8d621-104">Сравнивает две переменные ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="8d621-104">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d621-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d621-105">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="8d621-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="8d621-106">Parts</span></span>

- `result`

  <span data-ttu-id="8d621-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8d621-107">Required.</span></span> <span data-ttu-id="8d621-108">Значение `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8d621-108">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="8d621-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8d621-109">Required.</span></span> <span data-ttu-id="8d621-110">Любая `Object` переменная или выражение.</span><span class="sxs-lookup"><span data-stu-id="8d621-110">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="8d621-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8d621-111">Required.</span></span> <span data-ttu-id="8d621-112">Любая `Object` переменная или выражение.</span><span class="sxs-lookup"><span data-stu-id="8d621-112">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d621-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d621-113">Remarks</span></span>

<span data-ttu-id="8d621-114">`IsNot`Оператор определяет, ссылаются ли две объектные ссылки на разные объекты.</span><span class="sxs-lookup"><span data-stu-id="8d621-114">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="8d621-115">Однако сравнение значений не выполняется.</span><span class="sxs-lookup"><span data-stu-id="8d621-115">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="8d621-116">Если `object1` и `object2` оба ссылаются на один и тот же экземпляр объекта, `result` имеет значение `False` ; Если нет, `result` то имеет значение `True` .</span><span class="sxs-lookup"><span data-stu-id="8d621-116">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="8d621-117">`IsNot` является противоположностью `Is` оператора.</span><span class="sxs-lookup"><span data-stu-id="8d621-117">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="8d621-118">Преимущество заключается в том `IsNot` , что можно избежать неудобного синтаксиса с `Not` и `Is` , что может быть трудно читать.</span><span class="sxs-lookup"><span data-stu-id="8d621-118">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="8d621-119">Операторы и можно использовать `Is` `IsNot` для тестирования объектов с ранней и поздней привязкой.</span><span class="sxs-lookup"><span data-stu-id="8d621-119">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="8d621-120">Пример</span><span class="sxs-lookup"><span data-stu-id="8d621-120">Example</span></span>

<span data-ttu-id="8d621-121">В следующем примере кода используются `Is` оператор и `IsNot` оператор для выполнения одинакового сравнения.</span><span class="sxs-lookup"><span data-stu-id="8d621-121">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="8d621-122">Использование оператора TypeOf с оператором IsNot</span><span class="sxs-lookup"><span data-stu-id="8d621-122">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="8d621-123">Начиная с Visual Basic 14 можно использовать `TypeOf` оператор с `IsNot` оператором, чтобы проверить, несовместим ли объект с типом  данных.</span><span class="sxs-lookup"><span data-stu-id="8d621-123">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="8d621-124">Пример:</span><span class="sxs-lookup"><span data-stu-id="8d621-124">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="8d621-125">См. также</span><span class="sxs-lookup"><span data-stu-id="8d621-125">See also</span></span>

- [<span data-ttu-id="8d621-126">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="8d621-126">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="8d621-127">Оператор TypeOf</span><span class="sxs-lookup"><span data-stu-id="8d621-127">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="8d621-128">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d621-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="8d621-129">Практическое руководство. Проверка совпадения двух объектов</span><span class="sxs-lookup"><span data-stu-id="8d621-129">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
