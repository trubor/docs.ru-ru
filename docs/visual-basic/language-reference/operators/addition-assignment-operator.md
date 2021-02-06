---
description: 'Дополнительные сведения о operator: + = (Visual Basic)'
title: Оператор +=
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: e5a6b8fcc75e44c00ee18fec9cd57e68b1218de7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640476"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0b50b-103">Оператор += (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b50b-103">+= Operator (Visual Basic)</span></span>

<span data-ttu-id="0b50b-104">Добавляет значение числового выражения к значению числовой переменной или свойства и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="0b50b-104">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="0b50b-105">Также можно использовать для сцепления `String` выражения с `String` переменной или свойством и назначения результата переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="0b50b-105">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b50b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b50b-106">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0b50b-107">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0b50b-107">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="0b50b-108">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0b50b-108">Required.</span></span> <span data-ttu-id="0b50b-109">Любое числовое `String` значение, переменная или свойство.</span><span class="sxs-lookup"><span data-stu-id="0b50b-109">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="0b50b-110">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0b50b-110">Required.</span></span> <span data-ttu-id="0b50b-111">Любое числовое `String` выражение или.</span><span class="sxs-lookup"><span data-stu-id="0b50b-111">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b50b-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b50b-112">Remarks</span></span>  

 <span data-ttu-id="0b50b-113">Элемент в левой части `+=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="0b50b-113">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0b50b-114">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0b50b-114">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0b50b-115">`+=`Оператор добавляет значение справа к переменной или свойству слева и присваивает результат переменной или свойству слева.</span><span class="sxs-lookup"><span data-stu-id="0b50b-115">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="0b50b-116">`+=`Оператор также можно использовать для сцепления `String` выражения непосредственно с `String` переменной или свойством слева и присвоить результат переменной или свойству слева.</span><span class="sxs-lookup"><span data-stu-id="0b50b-116">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b50b-117">При использовании `+=` оператора может быть невозможно определить, будет ли выполняться сложение или объединение строк.</span><span class="sxs-lookup"><span data-stu-id="0b50b-117">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="0b50b-118">Используйте `&=` оператор для объединения, чтобы исключить неоднозначность и предоставить код для самостоятельного документирования.</span><span class="sxs-lookup"><span data-stu-id="0b50b-118">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="0b50b-119">Этот оператор присваивания неявно выполняет расширяющие, но не сужающие преобразования, если среда компиляции применяет строгую семантику.</span><span class="sxs-lookup"><span data-stu-id="0b50b-119">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="0b50b-120">Дополнительные сведения об этих преобразованиях см. в разделе [расширяющие и сужающие преобразования](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0b50b-120">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="0b50b-121">Дополнительные сведения о семантике строгих и неразрешений см. в разделе [оператор Option строгий](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0b50b-121">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="0b50b-122">Если семантика разрешений разрешена, `+=` оператор неявно выполняет различные строковые и числовые преобразования, идентичные выполняемым `+` оператором.</span><span class="sxs-lookup"><span data-stu-id="0b50b-122">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="0b50b-123">Дополнительные сведения об этих преобразованиях см. в разделе [оператор +](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0b50b-123">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0b50b-124">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="0b50b-124">Overloading</span></span>  

 <span data-ttu-id="0b50b-125">`+`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0b50b-125">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0b50b-126">Перегрузка `+` оператора влияет на поведение `+=` оператора.</span><span class="sxs-lookup"><span data-stu-id="0b50b-126">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="0b50b-127">Если ваш код использует `+=` класс или структуру, перегрузки `+` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="0b50b-127">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0b50b-128">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0b50b-128">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b50b-129">Пример</span><span class="sxs-lookup"><span data-stu-id="0b50b-129">Example</span></span>  

 <span data-ttu-id="0b50b-130">В следующем примере оператор используется `+=` для объединения значения одной переменной с другой.</span><span class="sxs-lookup"><span data-stu-id="0b50b-130">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="0b50b-131">Первая часть использует `+=` с числовыми переменными для добавления одного значения в другое.</span><span class="sxs-lookup"><span data-stu-id="0b50b-131">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="0b50b-132">Во второй части используется `+=` с `String` переменными для сцепления одного значения с другим.</span><span class="sxs-lookup"><span data-stu-id="0b50b-132">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="0b50b-133">В обоих случаях результат присваивается первой переменной.</span><span class="sxs-lookup"><span data-stu-id="0b50b-133">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="0b50b-134">`num1`Теперь значение равно 13, а значение `str1` равно "103".</span><span class="sxs-lookup"><span data-stu-id="0b50b-134">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b50b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="0b50b-135">See also</span></span>

- [<span data-ttu-id="0b50b-136">Оператор +</span><span class="sxs-lookup"><span data-stu-id="0b50b-136">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="0b50b-137">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="0b50b-137">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="0b50b-138">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="0b50b-138">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0b50b-139">Операторы объединения</span><span class="sxs-lookup"><span data-stu-id="0b50b-139">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="0b50b-140">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b50b-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0b50b-141">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="0b50b-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0b50b-142">Операторы</span><span class="sxs-lookup"><span data-stu-id="0b50b-142">Statements</span></span>](../../programming-guide/language-features/statements.md)
