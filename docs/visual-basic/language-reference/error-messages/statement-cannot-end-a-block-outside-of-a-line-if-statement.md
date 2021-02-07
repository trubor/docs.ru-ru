---
description: 'Дополнительные сведения о: BC32005: оператор не может заканчивать блок за пределами строки оператора if'
title: Оператор не может завершить блок за пределами однострочной инструкции If
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: afe856b2c2ea3fa1db029d35c5b876f5d67da411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731156"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="02bd8-103">BC32005: оператор не может заканчивать блок за пределами однострочного оператора if</span><span class="sxs-lookup"><span data-stu-id="02bd8-103">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="02bd8-104">Однострочный `If` оператор содержит несколько операторов, разделенных двоеточиями (:), одна из которых является `End` оператором для блока управления за пределами однострочного `If` .</span><span class="sxs-lookup"><span data-stu-id="02bd8-104">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="02bd8-105">Однострочные `If` операторы не используют `End If` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="02bd8-105">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="02bd8-106">**Идентификатор ошибки:** BC32005</span><span class="sxs-lookup"><span data-stu-id="02bd8-106">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="02bd8-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="02bd8-107">To correct this error</span></span>

- <span data-ttu-id="02bd8-108">Переместите однострочный `If` оператор за пределы блока управления, содержащего `End If` оператор.</span><span class="sxs-lookup"><span data-stu-id="02bd8-108">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="02bd8-109">См. также</span><span class="sxs-lookup"><span data-stu-id="02bd8-109">See also</span></span>

- [<span data-ttu-id="02bd8-110">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="02bd8-110">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
