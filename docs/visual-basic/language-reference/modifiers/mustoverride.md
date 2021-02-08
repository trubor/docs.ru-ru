---
description: 'Дополнительные сведения о: MustOverride (Visual Basic)'
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: df7200a7f7ec4bfda34765747d6318bc50a38dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774529"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="36549-103">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36549-103">MustOverride (Visual Basic)</span></span>

<span data-ttu-id="36549-104">Указывает, что свойство или процедура не реализованы в этом классе и должны быть переопределены в производном классе, прежде чем его можно будет использовать.</span><span class="sxs-lookup"><span data-stu-id="36549-104">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36549-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="36549-105">Remarks</span></span>  

 <span data-ttu-id="36549-106">Можно использовать `MustOverride` только в операторе объявления свойства или процедуры.</span><span class="sxs-lookup"><span data-stu-id="36549-106">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="36549-107">Свойство или процедура, указывающие, `MustOverride` должен быть членом класса, а класс должен быть помечен как [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="36549-107">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="36549-108">Правила</span><span class="sxs-lookup"><span data-stu-id="36549-108">Rules</span></span>  
  
- <span data-ttu-id="36549-109">**Неполное объявление.**</span><span class="sxs-lookup"><span data-stu-id="36549-109">**Incomplete Declaration.**</span></span> <span data-ttu-id="36549-110">При указании `MustOverride` не предоставляется никаких дополнительных строк кода для свойства или процедуры, а не `End Function` `End Property` инструкции, или `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="36549-110">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="36549-111">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="36549-111">**Combined Modifiers.**</span></span> <span data-ttu-id="36549-112">Нельзя указывать `MustOverride` вместе с `NotOverridable` , `Overridable` или `Shared` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="36549-112">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="36549-113">**Сокрытие и переопределение.**</span><span class="sxs-lookup"><span data-stu-id="36549-113">**Shadowing and Overriding.**</span></span> <span data-ttu-id="36549-114">Сокрытие и переопределение заменяют наследуемый элемент, но между этими подходами существуют значительные различия.</span><span class="sxs-lookup"><span data-stu-id="36549-114">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="36549-115">Дополнительные сведения см. [в разделе теневая поддержка в Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="36549-115">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="36549-116">**Альтернативные условия.**</span><span class="sxs-lookup"><span data-stu-id="36549-116">**Alternate Terms.**</span></span> <span data-ttu-id="36549-117">Элемент, который нельзя использовать, за исключением переопределения, иногда называют *чисто виртуальным* элементом.</span><span class="sxs-lookup"><span data-stu-id="36549-117">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="36549-118">Модификатор `MustOverride` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="36549-118">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="36549-119">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="36549-119">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="36549-120">Property Statement</span><span class="sxs-lookup"><span data-stu-id="36549-120">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="36549-121">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="36549-121">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="36549-122">См. также</span><span class="sxs-lookup"><span data-stu-id="36549-122">See also</span></span>

- [<span data-ttu-id="36549-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="36549-123">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="36549-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="36549-124">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="36549-125">Переопределения</span><span class="sxs-lookup"><span data-stu-id="36549-125">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="36549-126">MustInherit</span><span class="sxs-lookup"><span data-stu-id="36549-126">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="36549-127">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="36549-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="36549-128">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36549-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
