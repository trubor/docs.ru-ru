---
description: Дополнительные сведения о том, как создать процедуру (Visual Basic).
title: Практическое руководство. Создание процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: bca5ad24e845600642429273f6053787dd290b88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472544"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="65188-103">Практическое руководство. Создание процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65188-103">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="65188-104">Процедура заключается в заключении между операторами начального объявления ( `Sub` или `Function` ) и завершающим оператором объявления ( `End Sub` или `End Function` ).</span><span class="sxs-lookup"><span data-stu-id="65188-104">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="65188-105">Весь код процедуры находится между этими операторами.</span><span class="sxs-lookup"><span data-stu-id="65188-105">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="65188-106">Процедура не может содержать другую процедуру, поэтому ее начальные и конечные операторы должны находиться за пределами любой другой процедуры.</span><span class="sxs-lookup"><span data-stu-id="65188-106">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="65188-107">Если у вас есть код, выполняющий одну и ту же задачу в разных местах, можно написать задачу один раз как процедуру, а затем вызвать ее из различных мест в коде.</span><span class="sxs-lookup"><span data-stu-id="65188-107">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="65188-108">Создание процедуры, которая не возвращает значение</span><span class="sxs-lookup"><span data-stu-id="65188-108">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="65188-109">За пределами любой другой процедуры используйте `Sub` оператор, за которым следует `End Sub` оператор.</span><span class="sxs-lookup"><span data-stu-id="65188-109">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="65188-110">В `Sub` инструкции используйте `Sub` ключевое слово с именем процедуры, а затем список параметров в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="65188-110">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="65188-111">Поместите операторы кода процедуры между `Sub` `End Sub` операторами и.</span><span class="sxs-lookup"><span data-stu-id="65188-111">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="65188-112">Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="65188-112">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="65188-113">За пределами любой другой процедуры используйте `Function` оператор, за которым следует `End Function` оператор.</span><span class="sxs-lookup"><span data-stu-id="65188-113">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="65188-114">В `Function` инструкции используйте `Function` ключевое слово с именем процедуры, затем список параметров в круглых скобках, а затем `As` предложение, указывающее тип данных возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="65188-114">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="65188-115">Поместите операторы кода процедуры между `Function` `End Function` операторами и.</span><span class="sxs-lookup"><span data-stu-id="65188-115">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="65188-116">Используйте `Return` оператор, чтобы вернуть значение в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="65188-116">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="65188-117">Подключение новой процедуры к старым и повторяющимся блокам кода</span><span class="sxs-lookup"><span data-stu-id="65188-117">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="65188-118">Убедитесь, что вы определили новую процедуру в том месте, где старый код имеет к ней доступ.</span><span class="sxs-lookup"><span data-stu-id="65188-118">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="65188-119">В старом и повторяющемся блоке кода замените инструкции, выполняющие повторяющуюся задачу, на одну инструкцию, которая вызывает `Sub` `Function` процедуру или.</span><span class="sxs-lookup"><span data-stu-id="65188-119">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="65188-120">Если процедура `Function` возвращает значение, убедитесь, что вызывающая инструкция выполняет действие с возвращаемым значением, например, сохраняя его в переменной, или, в противном случае, значение будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="65188-120">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="65188-121">Пример</span><span class="sxs-lookup"><span data-stu-id="65188-121">Example</span></span>

 <span data-ttu-id="65188-122">Следующая `Function` процедура вычисляет самую длинную сторону (гипотенузу) правого треугольника, учитывая значения двух других сторон:</span><span class="sxs-lookup"><span data-stu-id="65188-122">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="65188-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="65188-123">See also</span></span>

- [<span data-ttu-id="65188-124">Процедуры</span><span class="sxs-lookup"><span data-stu-id="65188-124">Procedures</span></span>](index.md)
- [<span data-ttu-id="65188-125">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="65188-125">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="65188-126">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="65188-126">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="65188-127">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="65188-127">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="65188-128">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="65188-128">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="65188-129">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="65188-129">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="65188-130">Рекурсивные процедуры</span><span class="sxs-lookup"><span data-stu-id="65188-130">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="65188-131">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="65188-131">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="65188-132">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="65188-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- <span data-ttu-id="65188-133">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md) (Объектно-ориентированное программирование на языке Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65188-133">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md)</span></span>
