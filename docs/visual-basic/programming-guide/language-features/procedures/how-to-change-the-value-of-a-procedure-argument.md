---
description: Дополнительные сведения см. в статье как изменить значение аргумента процедуры (Visual Basic).
title: Практическое руководство. Изменение значения аргумента процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: f8ccc80f7a9cb5d2b090fbc6b7f7e3423e5a1cae
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472583"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="c8fcf-103">Практическое руководство. Изменение значения аргумента процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fcf-103">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>

<span data-ttu-id="c8fcf-104">При вызове процедуры каждый указываемый аргумент соответствует одному из параметров, определенных в процедуре.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-104">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="c8fcf-105">В некоторых случаях код процедуры может изменить значение, которое является базовым для аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-105">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="c8fcf-106">В других случаях процедура может изменить только локальную копию аргумента.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-106">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="c8fcf-107">При вызове процедуры Visual Basic создает локальную копию каждого аргумента, который передается по [значению ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="c8fcf-107">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="c8fcf-108">Для каждого аргумента, переданного по [ссылке ByRef](../../../language-reference/modifiers/byref.md), Visual Basic предоставляет коду процедуры прямую ссылку на программный элемент, лежащий в основе аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-108">For each argument passed [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="c8fcf-109">Если базовый элемент в вызывающем коде является изменяемым и передается аргумент `ByRef` , то код процедуры может использовать прямую ссылку для изменения значения элемента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-109">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="c8fcf-110">Изменение базового значения</span><span class="sxs-lookup"><span data-stu-id="c8fcf-110">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="c8fcf-111">Изменение базового значения аргумента процедуры в вызывающем коде</span><span class="sxs-lookup"><span data-stu-id="c8fcf-111">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="c8fcf-112">В объявлении процедуры укажите [ByRef](../../../language-reference/modifiers/byref.md) для параметра, соответствующего аргументу.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-112">In the procedure declaration, specify [ByRef](../../../language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="c8fcf-113">В вызывающем коде передайте изменяемый программный элемент в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-113">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="c8fcf-114">В вызывающем коде не заключайте аргумент в круглые скобки в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-114">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="c8fcf-115">В коде процедуры используйте имя параметра, чтобы присвоить значение базовому элементу в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-115">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="c8fcf-116">Для демонстрации см. пример ниже.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-116">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="c8fcf-117">Изменение локальных копий</span><span class="sxs-lookup"><span data-stu-id="c8fcf-117">Changing Local Copies</span></span>  

 <span data-ttu-id="c8fcf-118">Если базовый элемент в вызывающем коде является неизменяемым или передается аргумент `ByVal` , процедура не может изменить его значение в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-118">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="c8fcf-119">Однако процедура может изменить локальную копию такого аргумента.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-119">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="c8fcf-120">Изменение копии аргумента процедуры в коде процедуры</span><span class="sxs-lookup"><span data-stu-id="c8fcf-120">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="c8fcf-121">В объявлении процедуры укажите [ByVal](../../../language-reference/modifiers/byval.md) для параметра, соответствующего аргументу.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-121">In the procedure declaration, specify [ByVal](../../../language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="c8fcf-122">-или-</span><span class="sxs-lookup"><span data-stu-id="c8fcf-122">-or-</span></span>  
  
     <span data-ttu-id="c8fcf-123">В вызывающем коде заключите аргумент в круглые скобки в список аргументов.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-123">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="c8fcf-124">Это заставляет Visual Basic передавать аргумент по значению, даже если соответствующий параметр указывает `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="c8fcf-124">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="c8fcf-125">В коде процедуры используйте имя параметра, чтобы присвоить значение локальной копии аргумента.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-125">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="c8fcf-126">Базовое значение в вызывающем коде не изменяется.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-126">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8fcf-127">Пример</span><span class="sxs-lookup"><span data-stu-id="c8fcf-127">Example</span></span>  

 <span data-ttu-id="c8fcf-128">В следующем примере показаны две процедуры, которые принимают переменную массива и работают с ее элементами.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-128">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="c8fcf-129">`increase`Процедура просто добавляет по одной к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-129">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="c8fcf-130">`replace`Процедура присваивает параметру новый массив `a()` , а затем добавляет его к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-130">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="c8fcf-131">Первый `MsgBox` вызов выводит "после увеличения (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="c8fcf-131">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="c8fcf-132">Поскольку массив `n` является ссылочным типом, `replace` может изменить его члены, даже если используется механизм передачи `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="c8fcf-132">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="c8fcf-133">Во втором `MsgBox` вызове отображается "After Replace (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="c8fcf-133">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="c8fcf-134">Поскольку `n` передается `ByRef` , `replace` может изменить переменную `n` в вызывающем коде и присвоить ей новый массив.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-134">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="c8fcf-135">Поскольку `n` является ссылочным типом, `replace` может также изменять его члены.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-135">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="c8fcf-136">Можно запретить процедуре изменять саму переменную в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-136">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="c8fcf-137">См. раздел [как защитить аргумент процедуры от изменения значения](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c8fcf-137">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="c8fcf-138">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="c8fcf-138">Compile the code</span></span>  

 <span data-ttu-id="c8fcf-139">При передаче переменной по ссылке необходимо использовать `ByRef` ключевое слово, чтобы указать этот механизм.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-139">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="c8fcf-140">По умолчанию в Visual Basic передаются аргументы по значению.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-140">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="c8fcf-141">Однако рекомендуется включать ключевое слово [ByVal](../../../language-reference/modifiers/byval.md) или [ByRef](../../../language-reference/modifiers/byref.md) с каждым объявленным параметром.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-141">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="c8fcf-142">Это упрощает чтение кода.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-142">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c8fcf-143">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c8fcf-143">.NET Framework Security</span></span>  

 <span data-ttu-id="c8fcf-144">Всегда существует потенциальный риск, позволяющий процедуре изменять значение, которое является базовым для аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-144">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="c8fcf-145">Убедитесь, что это значение было изменено, и будьте готовы проверить его на допустимость перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-145">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fcf-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c8fcf-146">See also</span></span>

- [<span data-ttu-id="c8fcf-147">Процедуры</span><span class="sxs-lookup"><span data-stu-id="c8fcf-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c8fcf-148">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="c8fcf-148">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c8fcf-149">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="c8fcf-149">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="c8fcf-150">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="c8fcf-150">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c8fcf-151">Различия между изменяемыми и неизменяемыми аргументами</span><span class="sxs-lookup"><span data-stu-id="c8fcf-151">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="c8fcf-152">Различия между передачей аргумента по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="c8fcf-152">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="c8fcf-153">Практическое руководство. Защита аргумента процедуры от изменений значения</span><span class="sxs-lookup"><span data-stu-id="c8fcf-153">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="c8fcf-154">Практическое руководство. Принудительная передача аргумента по значению</span><span class="sxs-lookup"><span data-stu-id="c8fcf-154">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="c8fcf-155">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="c8fcf-155">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="c8fcf-156">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c8fcf-156">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
