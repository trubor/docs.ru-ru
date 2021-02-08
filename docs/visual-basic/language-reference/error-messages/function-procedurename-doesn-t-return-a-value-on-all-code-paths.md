---
description: 'Дополнительные сведения о: BC42105: функция " <procedurename> " не возвращает значение для всех ветвей кода'
title: Функция <procedurename> возвращает значение не для всех путей выполнения
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 2d0fa99906606228595a0c0d45f58dae0b269b77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796175"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="93282-103">BC42105: функция " \<procedurename> " не возвращает значение для всех ветвей кода</span><span class="sxs-lookup"><span data-stu-id="93282-103">BC42105: Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="93282-104">Функция " \<procedurename> " не возвращает значение для всех ветвей кода.</span><span class="sxs-lookup"><span data-stu-id="93282-104">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="93282-105">У вас отсутствует оператор "return"?</span><span class="sxs-lookup"><span data-stu-id="93282-105">Are you missing a 'Return' statement?</span></span>

 <span data-ttu-id="93282-106">`Function`Процедура имеет по крайней мере один возможный путь в коде, который не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="93282-106">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="93282-107">Получить значение из `Function` процедуры можно одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="93282-107">You can return a value from a `Function` procedure in any of the following ways:</span></span>

- <span data-ttu-id="93282-108">Включите значение в [оператор return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="93282-108">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

- <span data-ttu-id="93282-109">Присвойте значение `Function` имени процедуры, а затем выполните `Exit Function` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="93282-109">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>

- <span data-ttu-id="93282-110">Присвойте значение `Function` имени процедуры, а затем выполните `End Function` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="93282-110">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>

 <span data-ttu-id="93282-111">Если элемент управления передается в `Exit Function` или `End Function` и вы не назначили какое бы то ни было значение имени процедуры, процедура возвращает значение по умолчанию для возвращаемого типа данных.</span><span class="sxs-lookup"><span data-stu-id="93282-111">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="93282-112">Дополнительные сведения см. в разделе «поведение» в [операторе Function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="93282-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

 <span data-ttu-id="93282-113">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="93282-113">By default, this message is a warning.</span></span> <span data-ttu-id="93282-114">Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="93282-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="93282-115">**Идентификатор ошибки:** BC42105</span><span class="sxs-lookup"><span data-stu-id="93282-115">**Error ID:** BC42105</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="93282-116">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="93282-116">To correct this error</span></span>

- <span data-ttu-id="93282-117">Проверьте логику потока управления и убедитесь, что значение присваивается перед каждой инструкцией, которая вызывает возврат.</span><span class="sxs-lookup"><span data-stu-id="93282-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

     <span data-ttu-id="93282-118">Проще гарантировать, что каждый возврат из процедуры возвращает значение, если всегда используется `Return` оператор.</span><span class="sxs-lookup"><span data-stu-id="93282-118">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="93282-119">В этом случае последняя инструкция `End Function` должна быть `Return` оператором.</span><span class="sxs-lookup"><span data-stu-id="93282-119">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="93282-120">См. также</span><span class="sxs-lookup"><span data-stu-id="93282-120">See also</span></span>

- [<span data-ttu-id="93282-121">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="93282-121">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="93282-122">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="93282-122">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="93282-123">Страница "Компиляция" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93282-123">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
