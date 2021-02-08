---
description: 'Дополнительные сведения о: BC32022: " <eventname> " является событием и не может вызываться напрямую'
title: <eventname> является событием, поэтому его прямой вызов невозможен
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: f9d4b8fe54e1101e7963933f871cf5af2c1af903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796448"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="9f816-103">BC32022: " \<eventname> " является событием и не может вызываться напрямую</span><span class="sxs-lookup"><span data-stu-id="9f816-103">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="9f816-104">"<`eventname`>" является событием, поэтому его нельзя вызывать напрямую.</span><span class="sxs-lookup"><span data-stu-id="9f816-104">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="9f816-105">`RaiseEvent`Для вызова события используйте инструкцию.</span><span class="sxs-lookup"><span data-stu-id="9f816-105">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="9f816-106">Вызов процедуры задает событие для имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="9f816-106">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="9f816-107">Обработчик событий — это процедура, но само событие является сигнальным устройством, которое должно быть вызвано и обработано.</span><span class="sxs-lookup"><span data-stu-id="9f816-107">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="9f816-108">**Идентификатор ошибки:** BC32022</span><span class="sxs-lookup"><span data-stu-id="9f816-108">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9f816-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9f816-109">To correct this error</span></span>

- <span data-ttu-id="9f816-110">Используйте `RaiseEvent` оператор, чтобы сообщить о событии и вызвать процедуру или процедуры, которые ее обработают.</span><span class="sxs-lookup"><span data-stu-id="9f816-110">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f816-111">См. также</span><span class="sxs-lookup"><span data-stu-id="9f816-111">See also</span></span>

- [<span data-ttu-id="9f816-112">Оператор RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="9f816-112">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
