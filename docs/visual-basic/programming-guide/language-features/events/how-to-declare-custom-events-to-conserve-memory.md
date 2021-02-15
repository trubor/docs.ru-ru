---
description: Дополнительные сведения см. в статье как объявить пользовательские события для экономии памяти (Visual Basic)
title: Практическое руководство. Объявление пользовательских событий для экономии памяти
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 7371ec3df41ad0efd4598e0902f6937881d1e1a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460089"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="2c9ca-103">Практическое руководство. Объявление пользовательских событий для экономии памяти (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c9ca-103">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>

<span data-ttu-id="2c9ca-104">Существует несколько ситуаций, когда важно, чтобы приложение продолжало использовать память в низком объеме.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-104">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="2c9ca-105">Пользовательские события позволяют приложению использовать память только для обрабатываемых событий.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-105">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="2c9ca-106">По умолчанию, когда класс объявляет событие, компилятор выделяет память для поля, в котором хранятся сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-106">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="2c9ca-107">Если класс содержит много неиспользуемых событий, они не занимают память.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-107">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="2c9ca-108">Вместо использования реализации по умолчанию событий, предоставляемых Visual Basic, можно использовать пользовательские события для более тщательного управления использованием памяти.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-108">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c9ca-109">Пример</span><span class="sxs-lookup"><span data-stu-id="2c9ca-109">Example</span></span>  

 <span data-ttu-id="2c9ca-110">В этом примере класс использует один экземпляр <xref:System.ComponentModel.EventHandlerList> класса, хранящийся в `Events` поле, для хранения сведений об используемых событиях.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-110">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="2c9ca-111"><xref:System.ComponentModel.EventHandlerList>Класс является оптимизированным классом списка, предназначенным для хранения делегатов.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-111">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="2c9ca-112">Все события в классе используют `Events` поле для наблюдения за тем, какие методы обрабатывают каждое событие.</span><span class="sxs-lookup"><span data-stu-id="2c9ca-112">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="2c9ca-113">См. также</span><span class="sxs-lookup"><span data-stu-id="2c9ca-113">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="2c9ca-114">События</span><span class="sxs-lookup"><span data-stu-id="2c9ca-114">Events</span></span>](index.md)
- [<span data-ttu-id="2c9ca-115">Практическое руководство. Объявление пользовательских событий для предотвращения блокировки</span><span class="sxs-lookup"><span data-stu-id="2c9ca-115">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
