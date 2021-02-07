---
description: 'Дополнительные сведения о: оператор RemoveHandler'
title: Оператор RemoveHandler
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 699db9edfc029b4149246e8b654645040ae6d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741306"
---
# <a name="removehandler-statement"></a><span data-ttu-id="9fa3e-103">Оператор RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="9fa3e-103">RemoveHandler Statement</span></span>

<span data-ttu-id="9fa3e-104">Удаляет связь между событием и обработчиком событий.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-104">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa3e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9fa3e-105">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="9fa3e-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="9fa3e-106">Parts</span></span>  
  
|<span data-ttu-id="9fa3e-107">Термин</span><span class="sxs-lookup"><span data-stu-id="9fa3e-107">Term</span></span>|<span data-ttu-id="9fa3e-108">Определение</span><span class="sxs-lookup"><span data-stu-id="9fa3e-108">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="9fa3e-109">Имя обрабатываемого события.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-109">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="9fa3e-110">Имя процедуры, которая в настоящее время обрабатывает событие.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-110">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fa3e-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9fa3e-111">Remarks</span></span>  

 <span data-ttu-id="9fa3e-112">`AddHandler`Инструкции и `RemoveHandler` позволяют запускать и прекращать обработку событий для определенного события в любое время во время выполнения программы.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-112">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fa3e-113">Для пользовательских событий `RemoveHandler` оператор вызывает `RemoveHandler` метод доступа события.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-113">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="9fa3e-114">Дополнительные сведения о пользовательских событиях см. в разделе [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9fa3e-114">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fa3e-115">Пример</span><span class="sxs-lookup"><span data-stu-id="9fa3e-115">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="9fa3e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9fa3e-116">See also</span></span>

- [<span data-ttu-id="9fa3e-117">Оператор AddHandler</span><span class="sxs-lookup"><span data-stu-id="9fa3e-117">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="9fa3e-118">Маркеры</span><span class="sxs-lookup"><span data-stu-id="9fa3e-118">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="9fa3e-119">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="9fa3e-119">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="9fa3e-120">События</span><span class="sxs-lookup"><span data-stu-id="9fa3e-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
