---
description: 'Дополнительные сведения о: BC30481: оператор Class должен заканчиваться соответствующим оператором End'
title: Оператор Class должен заканчиваться соответствующим End Class
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: b0d2d89e9e3549b24f9c923e271b15b3b02026b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796785"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="091cd-103">BC30481: оператор Class должен заканчиваться соответствующим оператором End Class</span><span class="sxs-lookup"><span data-stu-id="091cd-103">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="091cd-104">`Class` используется для запуска `Class` блока, поэтому он может находиться только в начале блока, при этом `End Class` блоку соответствует оператор сопоставления.</span><span class="sxs-lookup"><span data-stu-id="091cd-104">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="091cd-105">Либо имеется избыточный `Class` оператор, либо вы не закончили `Class` блок с помощью `End Class` .</span><span class="sxs-lookup"><span data-stu-id="091cd-105">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="091cd-106">**Идентификатор ошибки:** BC30481</span><span class="sxs-lookup"><span data-stu-id="091cd-106">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="091cd-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="091cd-107">To correct this error</span></span>

- <span data-ttu-id="091cd-108">Найдите и удалите ненужный оператор `Class` .</span><span class="sxs-lookup"><span data-stu-id="091cd-108">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="091cd-109">Заключение `Class` блока с соответствующим `End Class` .</span><span class="sxs-lookup"><span data-stu-id="091cd-109">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="091cd-110">См. также</span><span class="sxs-lookup"><span data-stu-id="091cd-110">See also</span></span>

- [<span data-ttu-id="091cd-111">End, \<keyword> Инструкция</span><span class="sxs-lookup"><span data-stu-id="091cd-111">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="091cd-112">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="091cd-112">Class Statement</span></span>](../statements/class-statement.md)
