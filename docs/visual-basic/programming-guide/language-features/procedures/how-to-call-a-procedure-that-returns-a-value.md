---
description: Дополнительные сведения см. в статье как вызвать процедуру, возвращающую значение (Visual Basic).
title: Практическое руководство. Вызов процедуры, возвращающей значение
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 74c7b6c9340537088ac631fc47f9ebf7b1a203cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466748"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="dfff2-103">Практическое руководство. Вызов процедуры, возвращающей значение (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfff2-103">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="dfff2-104">`Function`Процедура возвращает значение в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="dfff2-104">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="dfff2-105">Его можно вызвать, указав его имя и аргументы в правой части оператора присваивания или в выражении.</span><span class="sxs-lookup"><span data-stu-id="dfff2-105">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="dfff2-106">Вызов процедуры Function в выражении</span><span class="sxs-lookup"><span data-stu-id="dfff2-106">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="dfff2-107">Используйте `Function` имя процедуры так же, как и переменную.</span><span class="sxs-lookup"><span data-stu-id="dfff2-107">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="dfff2-108">Можно использовать `Function` вызов процедуры в любом месте, где можно использовать переменную или константу в выражении.</span><span class="sxs-lookup"><span data-stu-id="dfff2-108">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="dfff2-109">Чтобы заключить список аргументов, выполните имя процедуры с круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="dfff2-109">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="dfff2-110">Если аргументы отсутствуют, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="dfff2-110">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="dfff2-111">Однако использование круглых скобок упрощает чтение кода.</span><span class="sxs-lookup"><span data-stu-id="dfff2-111">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="dfff2-112">Поместите аргументы в список аргументов в круглых скобках, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="dfff2-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="dfff2-113">Убедитесь, что аргументы указываются в том же порядке, в котором `Function` процедура определяет соответствующие параметры.</span><span class="sxs-lookup"><span data-stu-id="dfff2-113">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="dfff2-114">Кроме того, можно передать один или несколько аргументов по имени.</span><span class="sxs-lookup"><span data-stu-id="dfff2-114">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="dfff2-115">Дополнительные сведения см. в разделе [Передача аргументов по положению и по имени](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="dfff2-115">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="dfff2-116">Значение, возвращаемое процедурой, участвует в выражении точно так же, как значение переменной или константы.</span><span class="sxs-lookup"><span data-stu-id="dfff2-116">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="dfff2-117">Вызов процедуры Function в операторе присваивания</span><span class="sxs-lookup"><span data-stu-id="dfff2-117">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="dfff2-118">Используйте `Function` имя процедуры после знака равенства ( `=` ) в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="dfff2-118">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="dfff2-119">Чтобы заключить список аргументов, выполните имя процедуры с круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="dfff2-119">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="dfff2-120">Если аргументы отсутствуют, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="dfff2-120">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="dfff2-121">Однако использование круглых скобок упрощает чтение кода.</span><span class="sxs-lookup"><span data-stu-id="dfff2-121">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="dfff2-122">Поместите аргументы в список аргументов в круглых скобках, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="dfff2-122">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="dfff2-123">Убедитесь, что аргументы указываются в том же порядке, в котором `Function` процедура определяет соответствующие параметры, если не передать их по имени.</span><span class="sxs-lookup"><span data-stu-id="dfff2-123">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="dfff2-124">Значение, возвращаемое процедурой, хранится в переменной или свойстве в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="dfff2-124">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfff2-125">Пример</span><span class="sxs-lookup"><span data-stu-id="dfff2-125">Example</span></span>  

 <span data-ttu-id="dfff2-126">В следующем примере вызывается Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> для получения значения переменной среды операционной системы.</span><span class="sxs-lookup"><span data-stu-id="dfff2-126">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="dfff2-127">Первая строка вызывает `Environ` в выражении, а вторая строка вызывает его в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="dfff2-127">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="dfff2-128">`Environ` принимает имя переменной в качестве единственного аргумента.</span><span class="sxs-lookup"><span data-stu-id="dfff2-128">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="dfff2-129">Он возвращает значение переменной в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="dfff2-129">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="dfff2-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dfff2-130">See also</span></span>

- [<span data-ttu-id="dfff2-131">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="dfff2-131">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="dfff2-132">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="dfff2-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="dfff2-133">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="dfff2-133">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="dfff2-134">Практическое руководство. Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="dfff2-134">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="dfff2-135">Практическое руководство. Возврат значения из процедуры</span><span class="sxs-lookup"><span data-stu-id="dfff2-135">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="dfff2-136">Практическое руководство. Вызов процедуры, которая не возвращает значение</span><span class="sxs-lookup"><span data-stu-id="dfff2-136">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
