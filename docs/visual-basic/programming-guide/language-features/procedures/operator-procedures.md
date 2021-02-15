---
description: 'Дополнительные сведения: процедуры оператора (Visual Basic)'
title: Процедуры операторов
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 836eeb2e705a96c49b5fa53e277ccf025d1915b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479963"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="9eeeb-103">Процедуры операторов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9eeeb-103">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="9eeeb-104">Процедура оператора — это ряд инструкций Visual Basic, которые определяют поведение стандартного оператора (например `*` ,, `<>` или `And` ) для определенного класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-104">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="9eeeb-105">Это также называется *перегрузкой операторов*.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-105">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="9eeeb-106">Когда следует определять процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="9eeeb-106">When to Define Operator Procedures</span></span>

<span data-ttu-id="9eeeb-107">Определив класс или структуру, можно объявить переменные, имеющие тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-107">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="9eeeb-108">Иногда такая переменная должна участвовать в операции как часть выражения.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-108">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="9eeeb-109">Для этого он должен быть операндом оператора.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-109">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="9eeeb-110">Visual Basic определяет операторы только для основных типов данных.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-110">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="9eeeb-111">Поведение оператора можно определить, если один или оба операнда имеют тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-111">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="9eeeb-112">Дополнительные сведения см. в разделе Оператор [operator](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9eeeb-112">For more information, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="9eeeb-113">Типы процедур операторов</span><span class="sxs-lookup"><span data-stu-id="9eeeb-113">Types of Operator Procedure</span></span>

<span data-ttu-id="9eeeb-114">Процедура оператора может иметь один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="9eeeb-114">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="9eeeb-115">Определение унарного оператора, где аргумент имеет тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-115">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="9eeeb-116">Определение бинарного оператора, в котором по крайней мере один из аргументов имеет тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-116">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="9eeeb-117">Определение оператора преобразования, в котором аргумент имеет тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-117">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="9eeeb-118">Определение оператора преобразования, возвращающего тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-118">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="9eeeb-119">Операторы преобразования всегда являются унарными, и всегда используются в `CType` качестве оператора, который вы определяете.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-119">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="9eeeb-120">Синтаксис объявления</span><span class="sxs-lookup"><span data-stu-id="9eeeb-120">Declaration Syntax</span></span>

<span data-ttu-id="9eeeb-121">Синтаксис для объявления процедуры оператора выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9eeeb-121">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="9eeeb-122">`Widening` `Narrowing` Ключевое слово или используется только для оператора преобразования типа.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="9eeeb-123">Символ оператора всегда является [функцией CType](../../../language-reference/functions/ctype-function.md) для оператора преобразования типа.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-123">The operator symbol is always [CType Function](../../../language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="9eeeb-124">Вы объявляете два операнда для определения бинарного оператора и объявляете один операнд для определения унарного оператора, включая оператор преобразования типа.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="9eeeb-125">Все операнды должны быть объявлены `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="9eeeb-125">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="9eeeb-126">Каждый операнд объявляется точно так же, как вы объявляете параметры для [процедур подраздела](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9eeeb-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="9eeeb-127">Тип данных</span><span class="sxs-lookup"><span data-stu-id="9eeeb-127">Data Type</span></span>

<span data-ttu-id="9eeeb-128">Поскольку вы определяете оператор для определенного класса или структуры, по крайней мере один из операндов должен иметь тип данных этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="9eeeb-129">Для оператора преобразования типа операнд или возвращаемый тип должен иметь тип данных класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="9eeeb-130">Дополнительные сведения см. в разделе Оператор [operator](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9eeeb-130">For more details, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="9eeeb-131">Синтаксис вызова</span><span class="sxs-lookup"><span data-stu-id="9eeeb-131">Calling Syntax</span></span>

<span data-ttu-id="9eeeb-132">Процедуру оператора можно вызвать неявно, используя символ оператора в выражении.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="9eeeb-133">Операнды указываются так же, как и для предопределенных операторов.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-133">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="9eeeb-134">Для неявного вызова процедуры оператора используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="9eeeb-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="9eeeb-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="9eeeb-135">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="9eeeb-136">`Dim testNewStruct As`  *structurename* `= testStruct` *операторсимбол*      `10`</span><span class="sxs-lookup"><span data-stu-id="9eeeb-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="9eeeb-137">Иллюстрация объявления и вызова</span><span class="sxs-lookup"><span data-stu-id="9eeeb-137">Illustration of Declaration and Call</span></span>

<span data-ttu-id="9eeeb-138">В следующей структуре хранится 128-разрядное целое число со знаком в качестве составляющих элементов высокого и нижнего порядка.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="9eeeb-139">Он определяет `+` оператор для добавления двух `veryLong` значений и формирования результирующего `veryLong` значения.</span><span class="sxs-lookup"><span data-stu-id="9eeeb-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="9eeeb-140">В следующем примере показан типичный вызов оператора, `+` определенного для `veryLong` .</span><span class="sxs-lookup"><span data-stu-id="9eeeb-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="9eeeb-141">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9eeeb-141">See also</span></span>

- [<span data-ttu-id="9eeeb-142">Процедуры</span><span class="sxs-lookup"><span data-stu-id="9eeeb-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9eeeb-143">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="9eeeb-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9eeeb-144">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="9eeeb-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="9eeeb-145">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="9eeeb-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9eeeb-146">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="9eeeb-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9eeeb-147">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="9eeeb-147">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="9eeeb-148">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="9eeeb-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="9eeeb-149">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="9eeeb-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="9eeeb-150">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="9eeeb-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="9eeeb-151">Практическое руководство. Использование класса, в котором определяются операторы</span><span class="sxs-lookup"><span data-stu-id="9eeeb-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
