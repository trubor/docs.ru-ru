---
description: 'Дополнительные сведения о: BC30594: события общих переменных WithEvents не могут обрабатываться методами, не являющимися общими'
title: События общих переменных WithEvents не могут обрабатываться не используемыми совместно методами
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f9e8bf6e0d365c4ee747deb6be0e809904d87117
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796422"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="435ea-103">BC30594: события общих переменных WithEvents не могут обрабатываться методами, не являющимися общими</span><span class="sxs-lookup"><span data-stu-id="435ea-103">BC30594: Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>

<span data-ttu-id="435ea-104">Переменная, объявленная с `Shared` модификатором, является общей переменной.</span><span class="sxs-lookup"><span data-stu-id="435ea-104">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="435ea-105">Общая переменная определяет ровно одно место хранения.</span><span class="sxs-lookup"><span data-stu-id="435ea-105">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="435ea-106">Переменная, объявленная с `WithEvents` модификатором, утверждает, что тип, которому принадлежит переменная, обрабатывает набор событий, которые создает переменная.</span><span class="sxs-lookup"><span data-stu-id="435ea-106">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="435ea-107">Если переменной присвоено значение, то свойство, созданное `WithEvents` объявлением, отсоединяется от любого существующего обработчика событий и подключается к новому обработчику событий с помощью `Add` метода.</span><span class="sxs-lookup"><span data-stu-id="435ea-107">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>

 <span data-ttu-id="435ea-108">**Идентификатор ошибки:** BC30594</span><span class="sxs-lookup"><span data-stu-id="435ea-108">**Error ID:** BC30594</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="435ea-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="435ea-109">To correct this error</span></span>

- <span data-ttu-id="435ea-110">Объявите обработчик событий `Shared` .</span><span class="sxs-lookup"><span data-stu-id="435ea-110">Declare your event handler `Shared`.</span></span>

## <a name="see-also"></a><span data-ttu-id="435ea-111">См. также</span><span class="sxs-lookup"><span data-stu-id="435ea-111">See also</span></span>

- [<span data-ttu-id="435ea-112">Общий</span><span class="sxs-lookup"><span data-stu-id="435ea-112">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="435ea-113">WithEvents</span><span class="sxs-lookup"><span data-stu-id="435ea-113">WithEvents</span></span>](../modifiers/withevents.md)
