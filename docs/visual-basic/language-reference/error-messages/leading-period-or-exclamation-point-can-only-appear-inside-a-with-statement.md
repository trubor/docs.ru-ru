---
description: 'Дополнительные сведения о: BC30157: ведущие "." или "!" могут использоваться только в операторе "with"'
title: Символ "." или "!", стоящий в начале оператора, может использоваться только внутри оператора "With"
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e0325ac3c54046718d71df37edaac1edaf12f43e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795902"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="ed875-103">BC30157: ведущие "." или "!" могут использоваться только в операторе "with"</span><span class="sxs-lookup"><span data-stu-id="ed875-103">BC30157: Leading '.' or '!' can only appear inside a 'With' statement</span></span>

<span data-ttu-id="ed875-104">Точка (.) или восклицательный знак (!), не находящиеся внутри `With` блока, происходит без выражения слева.</span><span class="sxs-lookup"><span data-stu-id="ed875-104">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="ed875-105">Для доступа к членам ( `.` ) и доступа к членам словаря ( `!` ) требуется выражение, указывающее элемент, содержащий элемент.</span><span class="sxs-lookup"><span data-stu-id="ed875-105">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="ed875-106">Он должен располагаться непосредственно слева от метода доступа или являться целевым объектом блока, `With` содержащего доступ к члену.</span><span class="sxs-lookup"><span data-stu-id="ed875-106">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>

 <span data-ttu-id="ed875-107">**Идентификатор ошибки:** BC30157</span><span class="sxs-lookup"><span data-stu-id="ed875-107">**Error ID:** BC30157</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ed875-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ed875-108">To correct this error</span></span>

1. <span data-ttu-id="ed875-109">Убедитесь, что `With` блок имеет правильный формат.</span><span class="sxs-lookup"><span data-stu-id="ed875-109">Ensure that the `With` block is correctly formatted.</span></span>

2. <span data-ttu-id="ed875-110">Если `With` блок отсутствует, добавьте выражение слева от метода доступа, результатом которого является определенный элемент, содержащий элемент.</span><span class="sxs-lookup"><span data-stu-id="ed875-110">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed875-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ed875-111">See also</span></span>

- [<span data-ttu-id="ed875-112">Специальные символы в коде</span><span class="sxs-lookup"><span data-stu-id="ed875-112">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="ed875-113">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="ed875-113">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
