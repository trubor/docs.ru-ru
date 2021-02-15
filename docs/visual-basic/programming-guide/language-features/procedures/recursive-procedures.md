---
description: 'Дополнительные сведения: Рекурсивные процедуры (Visual Basic)'
title: Рекурсивные процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 378b279a6664cd494fb2e26ff3276afcea56cc16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466566"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="f79e3-103">Рекурсивные процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79e3-103">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="f79e3-104">*Рекурсивная* процедура вызывает саму себя.</span><span class="sxs-lookup"><span data-stu-id="f79e3-104">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="f79e3-105">Как правило, это не самый эффективный способ написания кода Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f79e3-105">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="f79e3-106">В следующей процедуре используется рекурсия для вычисления факториала исходного аргумента.</span><span class="sxs-lookup"><span data-stu-id="f79e3-106">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="f79e3-107">Рекомендации по рекурсивным процедурам</span><span class="sxs-lookup"><span data-stu-id="f79e3-107">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="f79e3-108">**Ограничение условий**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-108">**Limiting Conditions**.</span></span> <span data-ttu-id="f79e3-109">Необходимо разработать рекурсивную процедуру для проверки по крайней мере одного условия, которое может завершить рекурсию, и необходимо также обработать случай, когда ни одно из таких условий не будет удовлетворено разумным числом рекурсивных вызовов.</span><span class="sxs-lookup"><span data-stu-id="f79e3-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="f79e3-110">При отсутствии хотя бы одного условия, которое может быть выполнено без ошибок, ваша процедура выполняет высокий риск выполнения в бесконечном цикле.</span><span class="sxs-lookup"><span data-stu-id="f79e3-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="f79e3-111">**Использование памяти**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-111">**Memory Usage**.</span></span> <span data-ttu-id="f79e3-112">Приложение имеет ограниченный объем пространства для локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="f79e3-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="f79e3-113">Каждый раз, когда процедура вызывает саму себя, она использует больше пространства для дополнительных копий своих локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="f79e3-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="f79e3-114">Если этот процесс будет продолжаться неограниченно, он приводит к <xref:System.StackOverflowException> ошибке.</span><span class="sxs-lookup"><span data-stu-id="f79e3-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="f79e3-115">**Эффективность**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-115">**Efficiency**.</span></span> <span data-ttu-id="f79e3-116">Почти всегда можно заменить цикл для рекурсии.</span><span class="sxs-lookup"><span data-stu-id="f79e3-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="f79e3-117">Цикл не имеет дополнительной нагрузки на передачу аргументов, инициализацию дополнительного хранилища и возврат значений.</span><span class="sxs-lookup"><span data-stu-id="f79e3-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="f79e3-118">Производительность может быть значительно выше без рекурсивных вызовов.</span><span class="sxs-lookup"><span data-stu-id="f79e3-118">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="f79e3-119">**Взаимная рекурсия**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-119">**Mutual Recursion**.</span></span> <span data-ttu-id="f79e3-120">Вы можете столкнуться с очень низкой производительностью или даже с бесконечным циклом, если две процедуры вызывают друг друга.</span><span class="sxs-lookup"><span data-stu-id="f79e3-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="f79e3-121">Такой проект представляет те же проблемы, что и одна Рекурсивная процедура, но может быть труднее для обнаружения и отладки.</span><span class="sxs-lookup"><span data-stu-id="f79e3-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="f79e3-122">**Вызов с круглыми скобками**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="f79e3-123">При `Function` рекурсивном вызове процедуры необходимо следовать имени процедуры с круглыми скобками, даже если нет списка аргументов.</span><span class="sxs-lookup"><span data-stu-id="f79e3-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="f79e3-124">В противном случае имя функции берется, как представляет возвращаемое значение функции.</span><span class="sxs-lookup"><span data-stu-id="f79e3-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="f79e3-125">**Тестирование**.</span><span class="sxs-lookup"><span data-stu-id="f79e3-125">**Testing**.</span></span> <span data-ttu-id="f79e3-126">При написании рекурсивной процедуры следует тщательно протестировать ее, чтобы убедиться, что она всегда соответствует определенному ограничению.</span><span class="sxs-lookup"><span data-stu-id="f79e3-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="f79e3-127">Также следует убедиться, что не хватает памяти из-за слишком большого количества рекурсивных вызовов.</span><span class="sxs-lookup"><span data-stu-id="f79e3-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="f79e3-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f79e3-128">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="f79e3-129">Процедуры</span><span class="sxs-lookup"><span data-stu-id="f79e3-129">Procedures</span></span>](index.md)
- [<span data-ttu-id="f79e3-130">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="f79e3-130">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="f79e3-131">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="f79e3-131">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="f79e3-132">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="f79e3-132">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="f79e3-133">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="f79e3-133">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="f79e3-134">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="f79e3-134">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f79e3-135">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="f79e3-135">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="f79e3-136">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="f79e3-136">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="f79e3-137">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="f79e3-137">Loop Structures</span></span>](../control-flow/loop-structures.md)
