---
description: 'Дополнительные сведения о: объект или класс не поддерживает набор событий'
title: Объект или класс не поддерживает набор событий
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: f13d47a6bb75a5e8394f5344b954afa523bedab3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795604"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="c7940-103">Объект или класс не поддерживает набор событий</span><span class="sxs-lookup"><span data-stu-id="c7940-103">Object or class does not support the set of events</span></span>

<span data-ttu-id="c7940-104">Предпринята попытка использовать `WithEvents` переменную с компонентом, который не может работать в качестве источника событий для указанного набора событий.</span><span class="sxs-lookup"><span data-stu-id="c7940-104">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="c7940-105">Например, необходимо принять события объекта, а затем создать другой объект, который является `Implements` первым объектом.</span><span class="sxs-lookup"><span data-stu-id="c7940-105">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="c7940-106">Хотя можно подумать о том, что вы можете передавать события из реализованного объекта, это не всегда так.</span><span class="sxs-lookup"><span data-stu-id="c7940-106">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="c7940-107">`Implements` реализует интерфейс только для методов и свойств.</span><span class="sxs-lookup"><span data-stu-id="c7940-107">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="c7940-108">`WithEvents` не поддерживается для Private `UserControls` , так как сведения о типе, необходимые для вызова, недоступны `ObjectEvent` во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c7940-108">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c7940-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c7940-109">To correct this error</span></span>

- <span data-ttu-id="c7940-110">Вы не можете заменять события для компонента, который не является источником событий.</span><span class="sxs-lookup"><span data-stu-id="c7940-110">You cannot sink events for a component that does not source events.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7940-111">См. также</span><span class="sxs-lookup"><span data-stu-id="c7940-111">See also</span></span>

- [<span data-ttu-id="c7940-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="c7940-112">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="c7940-113">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="c7940-113">Implements Statement</span></span>](../statements/implements-statement.md)
