---
description: 'Дополнительные сведения о: BC31423: событие " <eventname1> " не может реализовывать событие " <eventname2> " для интерфейса " <interface> ", так как их типы делегатов " <delegate1> " и " <delegate2> " не совпадают'
title: Событие <eventname1> не может реализовать событие <eventname2> в интерфейсе <interface>, так как их делегируемые типы <delegate1> и <delegate2> не совпадают
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: cfb967d2b43ce1f34f56f3d019a9a663b000296c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796461"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="aabd5-103">BC31423: событие " \<eventname1> " не может реализовать событие " \<eventname2> " для интерфейса " \<interface> ", так как их типы делегатов " \<delegate1> " и " \<delegate2> " не совпадают</span><span class="sxs-lookup"><span data-stu-id="aabd5-103">BC31423: Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>

<span data-ttu-id="aabd5-104">Visual Basic не может реализовать событие, так как тип делегата события не соответствует типу делегата события в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="aabd5-104">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="aabd5-105">Эта ошибка может возникнуть при определении нескольких событий в интерфейсе и последующей попытке их совместной реализации с использованием одного события.</span><span class="sxs-lookup"><span data-stu-id="aabd5-105">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="aabd5-106">Событие может реализовывать два или более событий, только если все они объявлены с помощью синтаксиса `As` и указывают один и тот же тип делегата.</span><span class="sxs-lookup"><span data-stu-id="aabd5-106">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>

 <span data-ttu-id="aabd5-107">**Идентификатор ошибки:** BC31423</span><span class="sxs-lookup"><span data-stu-id="aabd5-107">**Error ID:** BC31423</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="aabd5-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="aabd5-108">To correct this error</span></span>

- <span data-ttu-id="aabd5-109">Реализуйте события по отдельности.</span><span class="sxs-lookup"><span data-stu-id="aabd5-109">Implement the events separately.</span></span>

     <span data-ttu-id="aabd5-110">—или—</span><span class="sxs-lookup"><span data-stu-id="aabd5-110">—or—</span></span>

- <span data-ttu-id="aabd5-111">Определите события в интерфейсе с помощью `As` синтаксиса и укажите тот же тип делегата.</span><span class="sxs-lookup"><span data-stu-id="aabd5-111">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>

## <a name="see-also"></a><span data-ttu-id="aabd5-112">См. также</span><span class="sxs-lookup"><span data-stu-id="aabd5-112">See also</span></span>

- [<span data-ttu-id="aabd5-113">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="aabd5-113">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="aabd5-114">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="aabd5-114">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="aabd5-115">События</span><span class="sxs-lookup"><span data-stu-id="aabd5-115">Events</span></span>](../../programming-guide/language-features/events/index.md)
