---
description: 'Дополнительные сведения о: как принудительно передавать аргумент по значению (Visual Basic)'
title: Практическое руководство. Принудительная передача аргумента по значению
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 471ddbf8993ad671dc4285729a11f5b17a5b19dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475426"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="38bb7-103">Практическое руководство. Принудительная передача аргумента по значению (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38bb7-103">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>

<span data-ttu-id="38bb7-104">Объявление процедуры определяет механизм передачи.</span><span class="sxs-lookup"><span data-stu-id="38bb7-104">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="38bb7-105">Если параметр объявлен как [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic предполагался передать соответствующий аргумент по ссылке.</span><span class="sxs-lookup"><span data-stu-id="38bb7-105">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="38bb7-106">Это позволяет процедуре изменять значение программного элемента, лежащего в основе аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="38bb7-106">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="38bb7-107">Если вы хотите защитить базовый элемент от таких изменений, можно переопределить `ByRef` механизм передачи в вызове процедуры, заключив имя аргумента в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="38bb7-107">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="38bb7-108">Эти скобки являются дополнением к круглым скобкам, включающим список аргументов в вызове.</span><span class="sxs-lookup"><span data-stu-id="38bb7-108">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="38bb7-109">Вызывающий код не может переопределить механизм [ByVal](../../../language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="38bb7-109">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="38bb7-110">Принудительная передача аргумента по значению</span><span class="sxs-lookup"><span data-stu-id="38bb7-110">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="38bb7-111">Если соответствующий параметр объявлен `ByVal` в процедуре, вам не нужно предпринимать никаких дополнительных действий.</span><span class="sxs-lookup"><span data-stu-id="38bb7-111">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="38bb7-112">Visual Basic уже ждет передачи аргумента по значению.</span><span class="sxs-lookup"><span data-stu-id="38bb7-112">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="38bb7-113">Если соответствующий параметр объявлен `ByRef` в процедуре, заключите аргумент в круглые скобки в вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="38bb7-113">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38bb7-114">Пример</span><span class="sxs-lookup"><span data-stu-id="38bb7-114">Example</span></span>  

 <span data-ttu-id="38bb7-115">В следующем примере переопределяется `ByRef` объявление параметра.</span><span class="sxs-lookup"><span data-stu-id="38bb7-115">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="38bb7-116">В вызове, который вызывает принудительное выполнение `ByVal` , обратите внимание на два уровня круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="38bb7-116">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="38bb7-117">Если `str` аргумент заключен в круглые скобки в списке аргументов, `setNewString` процедура не может изменить ее значение в вызывающем коде и `MsgBox` выводит "не может быть заменен, если передано ByVal".</span><span class="sxs-lookup"><span data-stu-id="38bb7-117">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="38bb7-118">Если `str` не заключен в круглые скобки, процедура может изменить ее и `MsgBox` выводит "это новое значение для аргумента строки".</span><span class="sxs-lookup"><span data-stu-id="38bb7-118">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="38bb7-119">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="38bb7-119">Compile the code</span></span>  

 <span data-ttu-id="38bb7-120">При передаче переменной по ссылке необходимо использовать `ByRef` ключевое слово, чтобы указать этот механизм.</span><span class="sxs-lookup"><span data-stu-id="38bb7-120">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="38bb7-121">По умолчанию в Visual Basic передаются аргументы по значению.</span><span class="sxs-lookup"><span data-stu-id="38bb7-121">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="38bb7-122">Однако рекомендуется включать ключевое слово [ByVal](../../../language-reference/modifiers/byval.md) или [ByRef](../../../language-reference/modifiers/byref.md) с каждым объявленным параметром.</span><span class="sxs-lookup"><span data-stu-id="38bb7-122">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="38bb7-123">Это упрощает чтение кода.</span><span class="sxs-lookup"><span data-stu-id="38bb7-123">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="38bb7-124">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="38bb7-124">Robust Programming</span></span>  

 <span data-ttu-id="38bb7-125">Если процедура объявляет параметр [ByRef](../../../language-reference/modifiers/byref.md), правильное выполнение кода может зависеть от возможности изменения базового элемента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="38bb7-125">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="38bb7-126">Если вызывающий код переопределяет этот механизм вызова, заключив аргумент в круглые скобки или передавая неизменяемый аргумент, процедура не может изменить базовый элемент.</span><span class="sxs-lookup"><span data-stu-id="38bb7-126">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="38bb7-127">Это может привести к непредвиденным результатам в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="38bb7-127">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="38bb7-128">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38bb7-128">.NET Framework Security</span></span>  

 <span data-ttu-id="38bb7-129">Всегда существует потенциальный риск, позволяющий процедуре изменять значение, которое является базовым для аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="38bb7-129">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="38bb7-130">Убедитесь, что это значение было изменено, и будьте готовы проверить его на допустимость перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="38bb7-130">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bb7-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="38bb7-131">See also</span></span>

- [<span data-ttu-id="38bb7-132">Процедуры</span><span class="sxs-lookup"><span data-stu-id="38bb7-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="38bb7-133">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="38bb7-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="38bb7-134">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="38bb7-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="38bb7-135">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="38bb7-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="38bb7-136">Различия между изменяемыми и неизменяемыми аргументами</span><span class="sxs-lookup"><span data-stu-id="38bb7-136">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="38bb7-137">Различия между передачей аргумента по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="38bb7-137">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="38bb7-138">Практическое руководство. Изменение значения аргумента процедуры</span><span class="sxs-lookup"><span data-stu-id="38bb7-138">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="38bb7-139">Практическое руководство. Защита аргумента процедуры от изменений значения</span><span class="sxs-lookup"><span data-stu-id="38bb7-139">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="38bb7-140">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="38bb7-140">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="38bb7-141">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="38bb7-141">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
