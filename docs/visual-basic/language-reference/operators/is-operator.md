---
description: 'Дополнительные сведения о операторе: is (Visual Basic)'
title: Оператор is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0912ebd9bc9c33149568c6cea0197ef24c305ff2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665689"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="5fa3f-103">Оператор is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fa3f-103">Is operator (Visual Basic)</span></span>

<span data-ttu-id="5fa3f-104">Сравнивает две переменные ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-104">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fa3f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fa3f-105">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="5fa3f-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="5fa3f-106">Parts</span></span>

 `result`  
 <span data-ttu-id="5fa3f-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-107">Required.</span></span> <span data-ttu-id="5fa3f-108">Любое `Boolean` значение.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-108">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="5fa3f-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-109">Required.</span></span> <span data-ttu-id="5fa3f-110">Любое `Object` имя.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-110">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="5fa3f-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-111">Required.</span></span> <span data-ttu-id="5fa3f-112">Любое `Object` имя.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-112">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fa3f-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fa3f-113">Remarks</span></span>

<span data-ttu-id="5fa3f-114">`Is`Оператор определяет, ссылаются ли две объектные ссылки на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-114">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="5fa3f-115">Однако сравнение значений не выполняется.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-115">However, it does not perform value comparisons.</span></span> <span data-ttu-id="5fa3f-116">Если `object1` и `object2` оба ссылаются на один и тот же экземпляр объекта, `result` имеет значение `True` ; Если нет, `result` то имеет значение `False` .</span><span class="sxs-lookup"><span data-stu-id="5fa3f-116">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="5fa3f-117">`Is`Ключевое слово также используется в [SELECT... Case, инструкция](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5fa3f-117">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5fa3f-118">Пример</span><span class="sxs-lookup"><span data-stu-id="5fa3f-118">Example</span></span>

<span data-ttu-id="5fa3f-119">В следующем примере оператор используется `Is` для сравнения пар ссылок на объекты.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="5fa3f-120">Результаты присваиваются `Boolean` значению, представляющему идентичность двух объектов.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="5fa3f-121">Как показано в предыдущем примере, оператор можно использовать `Is` для тестирования объектов с ранней и поздней привязкой.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="5fa3f-122">Использование оператора TypeOf с оператором is</span><span class="sxs-lookup"><span data-stu-id="5fa3f-122">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="5fa3f-123">`Is` Оператор также можно использовать с `TypeOf` ключевым словом для создания `TypeOf` выражения... `Is` , которое проверяет, совместима ли объектная переменная с типом данных.</span><span class="sxs-lookup"><span data-stu-id="5fa3f-123">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="5fa3f-124">Пример:</span><span class="sxs-lookup"><span data-stu-id="5fa3f-124">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="5fa3f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="5fa3f-125">See also</span></span>

- [<span data-ttu-id="5fa3f-126">Оператор TypeOf</span><span class="sxs-lookup"><span data-stu-id="5fa3f-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="5fa3f-127">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="5fa3f-127">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="5fa3f-128">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fa3f-128">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="5fa3f-129">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fa3f-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5fa3f-130">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="5fa3f-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5fa3f-131">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="5fa3f-131">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
