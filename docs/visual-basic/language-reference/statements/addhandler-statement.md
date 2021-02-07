---
description: 'Дополнительные сведения о: оператор AddHandler'
title: Оператор AddHandler
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c0c34abd7ff225765ab36278825a555e2b84b0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674107"
---
# <a name="addhandler-statement"></a><span data-ttu-id="c20a2-103">Оператор AddHandler</span><span class="sxs-lookup"><span data-stu-id="c20a2-103">AddHandler Statement</span></span>

<span data-ttu-id="c20a2-104">Связывает событие с обработчиком событий во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c20a2-104">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c20a2-105">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="c20a2-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="c20a2-106">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="c20a2-107">event</span><span class="sxs-lookup"><span data-stu-id="c20a2-107">event</span></span>|<span data-ttu-id="c20a2-108">Имя обрабатываемого события.</span><span class="sxs-lookup"><span data-stu-id="c20a2-108">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="c20a2-109">Имя процедуры, которая обрабатывает событие.</span><span class="sxs-lookup"><span data-stu-id="c20a2-109">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="c20a2-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c20a2-110">Remarks</span></span>  

 <span data-ttu-id="c20a2-111">`AddHandler`Инструкции и `RemoveHandler` позволяют запускать и прекращать обработку событий в любое время во время выполнения программы.</span><span class="sxs-lookup"><span data-stu-id="c20a2-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="c20a2-112">Сигнатура `eventhandler` процедуры должна соответствовать сигнатуре события `event` .</span><span class="sxs-lookup"><span data-stu-id="c20a2-112">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="c20a2-113">Как ключевое слово `Handles` так и оператор `AddHandler` позволяют задать обработку определенных событий конкретными процедурами, но между ними существуют различия.</span><span class="sxs-lookup"><span data-stu-id="c20a2-113">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="c20a2-114">Оператор `AddHandler` подключает процедуры к событиям во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c20a2-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="c20a2-115">Используйте ключевое слово `Handles` при определении процедуры, чтобы указать, что она обрабатывает определенное событие.</span><span class="sxs-lookup"><span data-stu-id="c20a2-115">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="c20a2-116">Дополнительные сведения см. в разделе [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c20a2-116">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c20a2-117">Для пользовательских событий `AddHandler` оператор вызывает `AddHandler` метод доступа события.</span><span class="sxs-lookup"><span data-stu-id="c20a2-117">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="c20a2-118">Дополнительные сведения о пользовательских событиях см. в разделе [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c20a2-118">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c20a2-119">Пример</span><span class="sxs-lookup"><span data-stu-id="c20a2-119">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="c20a2-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c20a2-120">See also</span></span>

- [<span data-ttu-id="c20a2-121">Оператор RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="c20a2-121">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="c20a2-122">Маркеры</span><span class="sxs-lookup"><span data-stu-id="c20a2-122">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="c20a2-123">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="c20a2-123">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="c20a2-124">События</span><span class="sxs-lookup"><span data-stu-id="c20a2-124">Events</span></span>](../../programming-guide/language-features/events/index.md)
