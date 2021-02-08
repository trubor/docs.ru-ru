---
description: 'Дополнительные сведения о: BC30043: " <keyword> " допустимо только в методе экземпляра'
title: <keyword> разрешено использовать только в методе экземпляра
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 0bca2df44e096da016c9cb0c2031a8ef6faeb2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795980"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="a2e1c-103">BC30043: " \<keyword> " является допустимым только в пределах метода экземпляра</span><span class="sxs-lookup"><span data-stu-id="a2e1c-103">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="a2e1c-104">`Me` `MyClass` Ключевые слова, и `MyBase` относятся к конкретным экземплярам класса.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-104">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="a2e1c-105">Их нельзя использовать в общей `Function` или `Sub` процедурной среде.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-105">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="a2e1c-106">*Идентификатор ошибки:*\* BC30043</span><span class="sxs-lookup"><span data-stu-id="a2e1c-106">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a2e1c-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a2e1c-107">To correct this error</span></span>

- <span data-ttu-id="a2e1c-108">Удалите ключевое слово из процедуры или удалите `Shared` ключевое слово из объявления процедуры.</span><span class="sxs-lookup"><span data-stu-id="a2e1c-108">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e1c-109">См. также</span><span class="sxs-lookup"><span data-stu-id="a2e1c-109">See also</span></span>

- [<span data-ttu-id="a2e1c-110">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="a2e1c-110">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="a2e1c-111">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="a2e1c-111">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="a2e1c-112">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="a2e1c-112">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
