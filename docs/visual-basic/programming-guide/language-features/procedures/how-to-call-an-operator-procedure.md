---
description: Дополнительные сведения см. в статье как вызвать процедуру оператора (Visual Basic).
title: Практическое руководство. Вызов процедуры оператора
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: f58d12ac5e4c9071646073184f7824946c00b39b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472609"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="01f0d-103">Практическое руководство. Вызов процедуры оператора (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01f0d-103">How to: Call an Operator Procedure (Visual Basic)</span></span>

<span data-ttu-id="01f0d-104">Для вызова процедуры оператора используется символ оператора в выражении.</span><span class="sxs-lookup"><span data-stu-id="01f0d-104">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="01f0d-105">В случае оператора преобразования вызывается [Функция CType](../../../language-reference/functions/ctype-function.md) для преобразования значения из одного типа данных в другой.</span><span class="sxs-lookup"><span data-stu-id="01f0d-105">In the case of a conversion operator, you call the [CType Function](../../../language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="01f0d-106">Процедуры оператора не вызываются явным образом.</span><span class="sxs-lookup"><span data-stu-id="01f0d-106">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="01f0d-107">Вы просто используете оператор или `CType` функцию в операторе присваивания или выражении так же, как обычно используется оператор.</span><span class="sxs-lookup"><span data-stu-id="01f0d-107">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="01f0d-108">Visual Basic выполняет вызов процедуры оператора.</span><span class="sxs-lookup"><span data-stu-id="01f0d-108">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="01f0d-109">Определение оператора для класса или структуры также называется *перегрузкой* оператора.</span><span class="sxs-lookup"><span data-stu-id="01f0d-109">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="01f0d-110">Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="01f0d-110">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="01f0d-111">Используйте символ оператора в выражении обычным образом.</span><span class="sxs-lookup"><span data-stu-id="01f0d-111">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="01f0d-112">Убедитесь, что типы данных операндов подходят для оператора, и в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="01f0d-112">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="01f0d-113">Оператор влияет на значение выражения, как и ожидалось.</span><span class="sxs-lookup"><span data-stu-id="01f0d-113">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="01f0d-114">Вызов процедуры оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="01f0d-114">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="01f0d-115">Используйте `CType` внутри выражения.</span><span class="sxs-lookup"><span data-stu-id="01f0d-115">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="01f0d-116">Убедитесь, что типы данных операндов подходят для преобразования, и в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="01f0d-116">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="01f0d-117">`CType` вызывает процедуру оператора преобразования и возвращает преобразованное значение.</span><span class="sxs-lookup"><span data-stu-id="01f0d-117">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f0d-118">Пример</span><span class="sxs-lookup"><span data-stu-id="01f0d-118">Example</span></span>  

 <span data-ttu-id="01f0d-119">Следующий пример создает две <xref:System.TimeSpan> структуры, добавляет их вместе и сохраняет результат в третьей <xref:System.TimeSpan> структуре.</span><span class="sxs-lookup"><span data-stu-id="01f0d-119">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="01f0d-120"><xref:System.TimeSpan>Структура определяет процедуры операторов для перегрузки нескольких стандартных операторов.</span><span class="sxs-lookup"><span data-stu-id="01f0d-120">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="01f0d-121">Поскольку <xref:System.TimeSpan> перегружает Стандартный `+` оператор, предыдущий пример вызывает процедуру оператора при вычислении значения `combinedSpan` .</span><span class="sxs-lookup"><span data-stu-id="01f0d-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="01f0d-122">Пример вызова процедуры оператора диалога см. [в разделе как использовать класс, определяющий операторы](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="01f0d-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="01f0d-123">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="01f0d-123">Compile the code</span></span>  

 <span data-ttu-id="01f0d-124">Убедитесь, что используемый класс или структура определяет оператор, который вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="01f0d-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f0d-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="01f0d-125">See also</span></span>

- [<span data-ttu-id="01f0d-126">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="01f0d-126">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="01f0d-127">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="01f0d-127">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="01f0d-128">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="01f0d-128">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="01f0d-129">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="01f0d-129">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="01f0d-130">Widening</span><span class="sxs-lookup"><span data-stu-id="01f0d-130">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="01f0d-131">Narrowing</span><span class="sxs-lookup"><span data-stu-id="01f0d-131">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="01f0d-132">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="01f0d-132">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="01f0d-133">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="01f0d-133">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="01f0d-134">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="01f0d-134">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="01f0d-135">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="01f0d-135">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
