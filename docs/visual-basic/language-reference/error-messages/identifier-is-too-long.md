---
description: 'Дополнительные сведения о: BC30033: слишком длинный идентификатор'
title: Слишком длинный идентификатор
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: f2439c4bfc53f906fdc277b0de1faac0941c8808
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796097"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="efcb6-103">BC30033: слишком длинный идентификатор</span><span class="sxs-lookup"><span data-stu-id="efcb6-103">BC30033: Identifier is too long</span></span>

<span data-ttu-id="efcb6-104">Имя или идентификатор каждого элемента программирования ограничено 1023 символами.</span><span class="sxs-lookup"><span data-stu-id="efcb6-104">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="efcb6-105">Кроме того, полное имя не может содержать более 1023 символов.</span><span class="sxs-lookup"><span data-stu-id="efcb6-105">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="efcb6-106">Это означает, что длина строки идентификатора ( `<namespace>.<...>.<namespace>.<class>.<element>` ) не может превышать 1023 символов, включая символы оператора доступа к членам ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="efcb6-106">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="efcb6-107">**Идентификатор ошибки:** BC30033</span><span class="sxs-lookup"><span data-stu-id="efcb6-107">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="efcb6-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="efcb6-108">To correct this error</span></span>

- <span data-ttu-id="efcb6-109">Уменьшите длину идентификатора.</span><span class="sxs-lookup"><span data-stu-id="efcb6-109">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="efcb6-110">См. также</span><span class="sxs-lookup"><span data-stu-id="efcb6-110">See also</span></span>

- [<span data-ttu-id="efcb6-111">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="efcb6-111">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
