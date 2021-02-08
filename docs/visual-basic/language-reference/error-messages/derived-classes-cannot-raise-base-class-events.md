---
description: 'Дополнительные сведения о: BC30029: производные классы не могут создавать события базового класса'
title: Производные классы не могут вызывать события базового класса
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 68546f2654f7c34fcb309d5af68e237d5f1eac79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796604"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="d006d-103">BC30029: производные классы не могут создавать события базового класса</span><span class="sxs-lookup"><span data-stu-id="d006d-103">BC30029: Derived classes cannot raise base class events</span></span>

<span data-ttu-id="d006d-104">Событие может быть вызвано только из области объявления, в которой оно объявлено.</span><span class="sxs-lookup"><span data-stu-id="d006d-104">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="d006d-105">Таким образом, класс не может создавать события из любого другого класса, даже из того, от которого он является производным.</span><span class="sxs-lookup"><span data-stu-id="d006d-105">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>

 <span data-ttu-id="d006d-106">**Идентификатор ошибки:** BC30029</span><span class="sxs-lookup"><span data-stu-id="d006d-106">**Error ID:** BC30029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d006d-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d006d-107">To correct this error</span></span>

- <span data-ttu-id="d006d-108">Переместите `Event` оператор или `RaiseEvent` инструкцию так, чтобы они насовпадали с одним и тем же классом.</span><span class="sxs-lookup"><span data-stu-id="d006d-108">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d006d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="d006d-109">See also</span></span>

- [<span data-ttu-id="d006d-110">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="d006d-110">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="d006d-111">Оператор RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="d006d-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
