---
description: 'Дополнительные сведения о: недостаточно пространства стека (Visual Basic)'
title: Недостаточно места для стека
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: a32ca0d2becade33177596501b7eabde4251e0a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795496"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="136f4-103">Отсутствует место в стеке (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136f4-103">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="136f4-104">Стек — это Рабочая область памяти, которая динамически растет и сжимается с учетом требований к выполненной программе.</span><span class="sxs-lookup"><span data-stu-id="136f4-104">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="136f4-105">Превышены его ограничения.</span><span class="sxs-lookup"><span data-stu-id="136f4-105">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="136f4-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="136f4-106">To correct this error</span></span>  
  
1. <span data-ttu-id="136f4-107">Убедитесь, что процедуры не вложены слишком глубоко.</span><span class="sxs-lookup"><span data-stu-id="136f4-107">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="136f4-108">Убедитесь, что рекурсивные процедуры завершаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="136f4-108">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="136f4-109">Если локальным переменным требуется больше пространства локальных переменных, чем доступно, попробуйте объявить некоторые переменные на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="136f4-109">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="136f4-110">Кроме того, можно объявить все переменные в процедуре статически, выполнив `Property` `Sub` `Function` ключевое слово, или с помощью `Static` .</span><span class="sxs-lookup"><span data-stu-id="136f4-110">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="136f4-111">Или можно использовать `Static` инструкцию для объявления отдельных статических переменных в процедурах.</span><span class="sxs-lookup"><span data-stu-id="136f4-111">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="136f4-112">Переопределите некоторые строки фиксированной длины как строки переменной длины, так как строки фиксированной длины используют больше пространства стека, чем строки переменной длины.</span><span class="sxs-lookup"><span data-stu-id="136f4-112">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="136f4-113">Можно также определить строку на уровне модуля, где не требуется пространство стека.</span><span class="sxs-lookup"><span data-stu-id="136f4-113">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="136f4-114">Проверьте количество вызовов вложенных `DoEvents` функций, используя `Calls` диалоговое окно для просмотра активных процедур в стеке.</span><span class="sxs-lookup"><span data-stu-id="136f4-114">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="136f4-115">Убедитесь, что вы не вызвали "каскадное событие", активируя событие, которое вызывает процедуру события, уже называемую в стеке.</span><span class="sxs-lookup"><span data-stu-id="136f4-115">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="136f4-116">Каскад событий аналогичен вызову незавершенной рекурсивной процедуры, но он менее очевидн, так как вызов выполняется Visual Basic а не явным вызовом в коде.</span><span class="sxs-lookup"><span data-stu-id="136f4-116">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="136f4-117">Используйте `Calls` диалоговое окно для просмотра активных процедур в стеке.</span><span class="sxs-lookup"><span data-stu-id="136f4-117">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136f4-118">См. также</span><span class="sxs-lookup"><span data-stu-id="136f4-118">See also</span></span>

- [<span data-ttu-id="136f4-119">Окно памяти</span><span class="sxs-lookup"><span data-stu-id="136f4-119">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
