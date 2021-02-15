---
description: Дополнительные сведения см. в статье как объявить пользовательские события, чтобы избежать блокировки (Visual Basic)
title: Практическое руководство. Объявление пользовательских событий для предотвращения блокировки
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a4ad3162e8f95ebbf7567d427ea00060b19b2235
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469725"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="33426-103">Практическое руководство. Объявление пользовательских событий для предотвращения блокировки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33426-103">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>

<span data-ttu-id="33426-104">Существует несколько ситуаций, когда важно, чтобы один обработчик событий не блокировал последующие обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="33426-104">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="33426-105">Пользовательские события позволяют событию вызывать свои обработчики событий асинхронно.</span><span class="sxs-lookup"><span data-stu-id="33426-105">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="33426-106">По умолчанию поле резервного хранилища для объявления события является многоадресным делегатом, который последовательно объединяет все обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="33426-106">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="33426-107">Это означает, что если один обработчик занимает много времени, он блокирует другие обработчики до завершения его выполнения.</span><span class="sxs-lookup"><span data-stu-id="33426-107">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="33426-108">(Правильно работающие обработчики событий не должны выполнять длительные или потенциально блокирующие операции.)</span><span class="sxs-lookup"><span data-stu-id="33426-108">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="33426-109">Вместо использования реализации по умолчанию событий, предоставляемых Visual Basic, можно использовать пользовательское событие для асинхронного выполнения обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="33426-109">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33426-110">Пример</span><span class="sxs-lookup"><span data-stu-id="33426-110">Example</span></span>  

 <span data-ttu-id="33426-111">В этом примере `AddHandler` метод доступа добавляет делегат для каждого обработчика `Click` события в объект, <xref:System.Collections.ArrayList> хранящийся в `EventHandlerList` поле.</span><span class="sxs-lookup"><span data-stu-id="33426-111">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="33426-112">Когда код вызывает `Click` событие, `RaiseEvent` метод доступа вызывает все делегаты обработчика событий асинхронно с помощью <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="33426-112">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="33426-113">Этот метод вызывает каждый обработчик в рабочем потоке и сразу же возвращает, поэтому обработчики не могут блокировать друг друга.</span><span class="sxs-lookup"><span data-stu-id="33426-113">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="33426-114">См. также</span><span class="sxs-lookup"><span data-stu-id="33426-114">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="33426-115">События</span><span class="sxs-lookup"><span data-stu-id="33426-115">Events</span></span>](index.md)
- [<span data-ttu-id="33426-116">Практическое руководство. Объявление пользовательских событий для экономии памяти</span><span class="sxs-lookup"><span data-stu-id="33426-116">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)
