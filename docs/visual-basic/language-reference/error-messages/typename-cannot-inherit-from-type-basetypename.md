---
description: 'Дополнительные сведения о: BC30910: " <typename> " не может наследовать от <type> " <basetypename> ", так как он расширяет доступ к базе <type> за пределами сборки'
title: <typename> не может наследоваться от <type><basetypename>, поскольку он расширяет доступ базового типа <type> за пределы сборки
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 332bfcbe9345f03605d6e1d6ded4a3e931ed491f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641100"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="e8b0a-103">BC30910: " \<typename> " не может наследовать от \<type> " \<basetypename> ", так как он расширяет доступ к базе \<type> за пределами сборки</span><span class="sxs-lookup"><span data-stu-id="e8b0a-103">BC30910: '\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="e8b0a-104">Класс или интерфейс наследует от базового класса или интерфейса, но имеет менее четкий уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-104">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>

 <span data-ttu-id="e8b0a-105">Например, `Public` интерфейс наследует от `Friend` интерфейса, или `Protected` класс наследует от `Private` класса.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-105">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="e8b0a-106">Это предоставляет базовый класс или интерфейс для доступа за пределами предполагаемого уровня.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-106">This exposes the base class or interface to access beyond the intended level.</span></span>

 <span data-ttu-id="e8b0a-107">**Идентификатор ошибки:** BC30910</span><span class="sxs-lookup"><span data-stu-id="e8b0a-107">**Error ID:** BC30910</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e8b0a-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e8b0a-108">To correct this error</span></span>

- <span data-ttu-id="e8b0a-109">Измените уровень доступа производного класса или интерфейса, чтобы он был по крайней мере максимальным по отношению к базовому классу или интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-109">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>

     <span data-ttu-id="e8b0a-110">-или-</span><span class="sxs-lookup"><span data-stu-id="e8b0a-110">-or-</span></span>

- <span data-ttu-id="e8b0a-111">Если требуется менее четкий уровень доступа, удалите `Inherits` оператор.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-111">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="e8b0a-112">Наследование от более ограниченного базового класса или интерфейса невозможно.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-112">You cannot inherit from a more restricted base class or interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8b0a-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e8b0a-113">See also</span></span>

- [<span data-ttu-id="e8b0a-114">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="e8b0a-114">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="e8b0a-115">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="e8b0a-115">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="e8b0a-116">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="e8b0a-116">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="e8b0a-117">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8b0a-117">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
