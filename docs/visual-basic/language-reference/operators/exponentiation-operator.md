---
description: 'Дополнительные сведения о операторе: ^ (Visual Basic)'
title: Оператор ^
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 9333eec7236c363417be7323b673231509da8f1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666047"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0ab34-103">Оператор ^ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ab34-103">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="0ab34-104">Возводит число в степень другого числа.</span><span class="sxs-lookup"><span data-stu-id="0ab34-104">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ab34-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ab34-105">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="0ab34-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0ab34-106">Parts</span></span>

`number`\
<span data-ttu-id="0ab34-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0ab34-107">Required.</span></span> <span data-ttu-id="0ab34-108">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="0ab34-108">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="0ab34-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0ab34-109">Required.</span></span> <span data-ttu-id="0ab34-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="0ab34-110">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="0ab34-111">Результат</span><span class="sxs-lookup"><span data-stu-id="0ab34-111">Result</span></span>

<span data-ttu-id="0ab34-112">Результат возводится в `number` степень `exponent` , всегда как `Double` значение.</span><span class="sxs-lookup"><span data-stu-id="0ab34-112">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="0ab34-113">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="0ab34-113">Supported Types</span></span>

<span data-ttu-id="0ab34-114">`Double`.</span><span class="sxs-lookup"><span data-stu-id="0ab34-114">`Double`.</span></span> <span data-ttu-id="0ab34-115">Операнды любого другого типа преобразуются в `Double` .</span><span class="sxs-lookup"><span data-stu-id="0ab34-115">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ab34-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="0ab34-116">Remarks</span></span>

<span data-ttu-id="0ab34-117">Visual Basic всегда выполняет возведение в степень в [типе данных Double](../data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0ab34-117">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span>

<span data-ttu-id="0ab34-118">Значение `exponent` может быть дробным, отрицательным или обоими.</span><span class="sxs-lookup"><span data-stu-id="0ab34-118">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="0ab34-119">Если в одном выражении выполняется несколько возможного возведения в степень, `^` оператор вычисляется так, как он встретился слева направо.</span><span class="sxs-lookup"><span data-stu-id="0ab34-119">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="0ab34-120">`^`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0ab34-120">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0ab34-121">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="0ab34-121">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0ab34-122">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0ab34-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ab34-123">Пример</span><span class="sxs-lookup"><span data-stu-id="0ab34-123">Example</span></span>

<span data-ttu-id="0ab34-124">В следующем примере оператор используется `^` для возведения числа в степень экспоненты.</span><span class="sxs-lookup"><span data-stu-id="0ab34-124">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="0ab34-125">Результатом является первый операнд, возведенный в степень второго.</span><span class="sxs-lookup"><span data-stu-id="0ab34-125">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="0ab34-126">В предыдущем примере получены следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="0ab34-126">The preceding example produces the following results:</span></span>

<span data-ttu-id="0ab34-127">`exp1` имеет значение 4 (2 в квадрате).</span><span class="sxs-lookup"><span data-stu-id="0ab34-127">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="0ab34-128">`exp2` имеет значение 19683 (3 Куба, затем это значение Cube).</span><span class="sxs-lookup"><span data-stu-id="0ab34-128">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="0ab34-129">`exp3` имеет значение-125 (-5 кубd).</span><span class="sxs-lookup"><span data-stu-id="0ab34-129">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="0ab34-130">`exp4` имеет значение 625 (от-5 до четвертой мощности).</span><span class="sxs-lookup"><span data-stu-id="0ab34-130">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="0ab34-131">`exp5` имеет значение 2 (кубический корень из 8).</span><span class="sxs-lookup"><span data-stu-id="0ab34-131">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="0ab34-132">`exp6` имеет значение 0,5 (1,0, деленное на кубический корень из 8).</span><span class="sxs-lookup"><span data-stu-id="0ab34-132">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="0ab34-133">Обратите внимание на важность круглых скобок в выражениях из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="0ab34-133">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="0ab34-134">Из-за *приоритета операторов* Visual Basic обычно выполняет `^` оператор перед любыми другими, даже унарным `–` оператором.</span><span class="sxs-lookup"><span data-stu-id="0ab34-134">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="0ab34-135">Если `exp4` и `exp6` были вычислены без скобок, они могли бы получить следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="0ab34-135">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="0ab34-136">`exp4 = -5 ^ 4` будет вычисляться как – (от 5 до четвертой мощности), что приведет к появлению-625.</span><span class="sxs-lookup"><span data-stu-id="0ab34-136">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="0ab34-137">`exp6 = 8 ^ -1.0 / 3.0` вычисляется как (от 8 до – 1 или 0,125), деленное на 3,0, что приведет к 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="0ab34-137">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ab34-138">См. также</span><span class="sxs-lookup"><span data-stu-id="0ab34-138">See also</span></span>

- [<span data-ttu-id="0ab34-139">Оператор ^ =</span><span class="sxs-lookup"><span data-stu-id="0ab34-139">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="0ab34-140">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="0ab34-140">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0ab34-141">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ab34-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0ab34-142">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="0ab34-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0ab34-143">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ab34-143">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
