---
description: 'Дополнительные сведения о: Protected Friend (Visual Basic)'
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: dcc8fd2b1aa99f910f002ac05178d379532fb73d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700979"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="036a7-103">Protected Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="036a7-103">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="036a7-104">Комбинация ключевых слов `Protected Friend` является модификатором доступа к члену.</span><span class="sxs-lookup"><span data-stu-id="036a7-104">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="036a7-105">Он предоставляет [дружественный](friend.md) доступ и [защищенный](protected.md) доступ к объявленным элементам, поэтому они доступны из любого места в одной сборке, из их собственного класса и из производных классов.</span><span class="sxs-lookup"><span data-stu-id="036a7-105">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="036a7-106">Можно указать `Protected Friend` только для членов классов. нельзя применять `Protected Friend` к членам структуры, поскольку структуры не наследуются.</span><span class="sxs-lookup"><span data-stu-id="036a7-106">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="036a7-107">В Visual Studio выберите Справка F1 в справке `protected friend` для [защищенного](protected.md) или [дружественного](friend.md)доступа.</span><span class="sxs-lookup"><span data-stu-id="036a7-107">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="036a7-108">Интегрированная среда разработки выбирает один маркер под курсором, а не составное слово.</span><span class="sxs-lookup"><span data-stu-id="036a7-108">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="036a7-109">Правила</span><span class="sxs-lookup"><span data-stu-id="036a7-109">Rules</span></span>

<span data-ttu-id="036a7-110">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="036a7-110">**Declaration Context.**</span></span> <span data-ttu-id="036a7-111">Можно использовать `Protected Friend` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="036a7-111">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="036a7-112">Это означает, что контекст объявления для `Protected` элемента должен быть классом и не может быть исходным файлом, пространством имен, интерфейсом, модулем, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="036a7-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="036a7-113">См. также</span><span class="sxs-lookup"><span data-stu-id="036a7-113">See also</span></span>

- [<span data-ttu-id="036a7-114">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="036a7-114">Public</span></span>](public.md)
- [<span data-ttu-id="036a7-115">Защищенный</span><span class="sxs-lookup"><span data-stu-id="036a7-115">Protected</span></span>](protected.md)
- [<span data-ttu-id="036a7-116">Friend</span><span class="sxs-lookup"><span data-stu-id="036a7-116">Friend</span></span>](friend.md)
- [<span data-ttu-id="036a7-117">Частная</span><span class="sxs-lookup"><span data-stu-id="036a7-117">Private</span></span>](private.md)
- [<span data-ttu-id="036a7-118">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="036a7-118">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="036a7-119">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="036a7-119">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="036a7-120">Процедуры</span><span class="sxs-lookup"><span data-stu-id="036a7-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="036a7-121">Структуры</span><span class="sxs-lookup"><span data-stu-id="036a7-121">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="036a7-122">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="036a7-122">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
