---
description: 'Дополнительные сведения о: этот массив фиксирован или временно заблокирован (Visual Basic)'
title: Этот массив имеет фиксированную длину или временно заблокирован
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 034bcc23055f7fb3f707e1105589a4526e6f9009
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641217"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="77466-103">Массив имеет фиксированный размер или временно заблокирован (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77466-103">This array is fixed or temporarily locked (Visual Basic)</span></span>

<span data-ttu-id="77466-104">Эта ошибка может быть вызвана следующими причинами.</span><span class="sxs-lookup"><span data-stu-id="77466-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="77466-105">Использование `ReDim` для изменения количества элементов массива фиксированного размера.</span><span class="sxs-lookup"><span data-stu-id="77466-105">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="77466-106">Переизмерение динамического массива на уровне модуля, в котором один элемент был передан в процедуру в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="77466-106">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="77466-107">Если передается элемент, массив блокируется, чтобы предотвратить освобождение памяти для параметра ссылки в процедуре.</span><span class="sxs-lookup"><span data-stu-id="77466-107">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="77466-108">Попытка присвоить значение `Variant` переменной, содержащей массив, но в `Variant` настоящий момент заблокирована.</span><span class="sxs-lookup"><span data-stu-id="77466-108">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77466-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="77466-109">To correct this error</span></span>  
  
1. <span data-ttu-id="77466-110">Сделайте исходный массив динамическим, а не фиксированным, объявив его с помощью `ReDim` (если массив объявляется в процедуре) или объявив его без указания количества элементов (если массив объявлен на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="77466-110">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="77466-111">Определите, действительно ли нужно передать элемент, так как он видим во всех процедурах в модуле.</span><span class="sxs-lookup"><span data-stu-id="77466-111">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="77466-112">Определите, что блокирует и исследует `Variant` его.</span><span class="sxs-lookup"><span data-stu-id="77466-112">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77466-113">См. также</span><span class="sxs-lookup"><span data-stu-id="77466-113">See also</span></span>

- [<span data-ttu-id="77466-114">Массивы</span><span class="sxs-lookup"><span data-stu-id="77466-114">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
