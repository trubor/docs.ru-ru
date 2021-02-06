---
description: "Дополнительные сведения о: BC30941: структура ' <structurename> ' должна содержать по крайней мере одну переменную члена экземпляра или хотя бы одно объявление события экземпляра не помечено как Custom"
title: Структура <structurename> должна содержать по крайней мере один экземпляр переменной члена или экземпляр объявления события, не помеченный как Custom
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 08596997decd9d739ac95ad3e4191cb126b3efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641451"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="6ba30-103">BC30941: структура " \<structurename> " должна содержать по крайней мере одну переменную члена экземпляра или хотя бы одно объявление события экземпляра не помечено как "Custom"</span><span class="sxs-lookup"><span data-stu-id="6ba30-103">BC30941: Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="6ba30-104">Определение структуры не содержит никаких общих переменных или необщих нестандартных событий.</span><span class="sxs-lookup"><span data-stu-id="6ba30-104">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>

 <span data-ttu-id="6ba30-105">Каждая структура должна иметь либо переменную, либо событие, которое применяется к каждому конкретному экземпляру (несовместное использование), а не ко всем экземплярам совместно ([Общий](../modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="6ba30-105">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="6ba30-106">Необщие константы, свойства и процедуры не соответствуют этому требованию.</span><span class="sxs-lookup"><span data-stu-id="6ba30-106">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="6ba30-107">Кроме того, если нет необщих переменных и только одно несовместное событие, это событие не может быть `Custom` событием.</span><span class="sxs-lookup"><span data-stu-id="6ba30-107">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>

 <span data-ttu-id="6ba30-108">**Идентификатор ошибки:** BC30941</span><span class="sxs-lookup"><span data-stu-id="6ba30-108">**Error ID:** BC30941</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6ba30-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6ba30-109">To correct this error</span></span>

- <span data-ttu-id="6ba30-110">Определите по крайней мере одну переменную или событие, которое не является `Shared` .</span><span class="sxs-lookup"><span data-stu-id="6ba30-110">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="6ba30-111">Если определено только одно событие, оно должно быть нестандартным, а также не общим.</span><span class="sxs-lookup"><span data-stu-id="6ba30-111">If you define only one event, it must be noncustom as well as nonshared.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba30-112">См. также</span><span class="sxs-lookup"><span data-stu-id="6ba30-112">See also</span></span>

- [<span data-ttu-id="6ba30-113">Структуры</span><span class="sxs-lookup"><span data-stu-id="6ba30-113">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6ba30-114">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="6ba30-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="6ba30-115">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="6ba30-115">Structure Statement</span></span>](../statements/structure-statement.md)
