---
description: 'Дополнительные сведения о: BC30269: " <methodname> " имеет несколько определений с одинаковыми сигнатурами'
title: Метод <methodname> несколько раз определен с одинаковыми подписями
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 7364ee7a308fab96afce268ff0c92cd45717f1bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795811"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="c1bce-103">BC30269: " \<methodname> " имеет несколько определений с одинаковыми сигнатурами</span><span class="sxs-lookup"><span data-stu-id="c1bce-103">BC30269: '\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="c1bce-104">В `Function` `Sub` объявлении процедуры или используется то же имя процедуры и список аргументов, что и в предыдущем объявлении.</span><span class="sxs-lookup"><span data-stu-id="c1bce-104">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="c1bce-105">Одной из возможных причин является попытка перегрузки исходной процедуры.</span><span class="sxs-lookup"><span data-stu-id="c1bce-105">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="c1bce-106">Перегруженные процедуры должны иметь разные списки аргументов.</span><span class="sxs-lookup"><span data-stu-id="c1bce-106">Overloaded procedures must have different argument lists.</span></span>

 <span data-ttu-id="c1bce-107">**Идентификатор ошибки:** BC30269</span><span class="sxs-lookup"><span data-stu-id="c1bce-107">**Error ID:** BC30269</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c1bce-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c1bce-108">To correct this error</span></span>

- <span data-ttu-id="c1bce-109">Измените имя процедуры или список аргументов или удалите повторяющееся объявление.</span><span class="sxs-lookup"><span data-stu-id="c1bce-109">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1bce-110">См. также</span><span class="sxs-lookup"><span data-stu-id="c1bce-110">See also</span></span>

- [<span data-ttu-id="c1bce-111">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="c1bce-111">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c1bce-112">Вопросы, связанные с перегрузкой процедур</span><span class="sxs-lookup"><span data-stu-id="c1bce-112">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
