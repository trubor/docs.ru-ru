---
description: 'Дополнительные сведения о: Private (Visual Basic)'
title: Частные
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 20dcd943856e20ccb1b7cb5c0603fa5f313d2421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700953"
---
# <a name="private-visual-basic"></a><span data-ttu-id="85e5a-103">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85e5a-103">Private (Visual Basic)</span></span>

<span data-ttu-id="85e5a-104">Указывает, что один или несколько объявленных программных элементов доступны только в контексте объявления, включая из любых содержащихся в них типов.</span><span class="sxs-lookup"><span data-stu-id="85e5a-104">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e5a-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="85e5a-105">Remarks</span></span>  

 <span data-ttu-id="85e5a-106">Если программный элемент представляет собственные функции или содержит конфиденциальные данные, обычно требуется ограничить доступ к нему как можно более строгим.</span><span class="sxs-lookup"><span data-stu-id="85e5a-106">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="85e5a-107">Максимальное ограничение достигается за счет предоставления только модулю, классу или структуре, определяющей его доступ.</span><span class="sxs-lookup"><span data-stu-id="85e5a-107">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="85e5a-108">Чтобы ограничить доступ к элементу таким образом, его можно объявить с помощью `Private` .</span><span class="sxs-lookup"><span data-stu-id="85e5a-108">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="85e5a-109">Можно также использовать модификатор [закрытого](private-protected.md) доступа, который делает член доступным из этого класса и из производных классов, расположенных в содержащей его сборке.</span><span class="sxs-lookup"><span data-stu-id="85e5a-109">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="85e5a-110">Правила</span><span class="sxs-lookup"><span data-stu-id="85e5a-110">Rules</span></span>  

- <span data-ttu-id="85e5a-111">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="85e5a-111">**Declaration Context.**</span></span> <span data-ttu-id="85e5a-112">`Private` можно использовать только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="85e5a-112">You can use `Private` only at module level.</span></span> <span data-ttu-id="85e5a-113">Это означает, что контекст объявления для `Private` элемента должен быть модулем, классом или структурой и не может быть исходным файлом, пространством имен, интерфейсом или процедурой.</span><span class="sxs-lookup"><span data-stu-id="85e5a-113">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="85e5a-114">Поведение</span><span class="sxs-lookup"><span data-stu-id="85e5a-114">Behavior</span></span>  
  
- <span data-ttu-id="85e5a-115">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="85e5a-115">**Access Level.**</span></span> <span data-ttu-id="85e5a-116">Весь код в контексте объявления может обращаться к его `Private` элементам.</span><span class="sxs-lookup"><span data-stu-id="85e5a-116">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="85e5a-117">Сюда входит код внутри содержащегося типа, например вложенный класс или выражение присваивания в перечислении.</span><span class="sxs-lookup"><span data-stu-id="85e5a-117">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="85e5a-118">Ни один код за пределами контекста объявления не может получить доступ к его `Private` элементам.</span><span class="sxs-lookup"><span data-stu-id="85e5a-118">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="85e5a-119">**Модификаторы доступа.**</span><span class="sxs-lookup"><span data-stu-id="85e5a-119">**Access Modifiers.**</span></span> <span data-ttu-id="85e5a-120">Ключевые слова, определяющие уровень доступа, называются *модификаторами доступа*.</span><span class="sxs-lookup"><span data-stu-id="85e5a-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="85e5a-121">Сравнение модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="85e5a-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="85e5a-122">Модификатор `Private` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="85e5a-122">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="85e5a-123">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="85e5a-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="85e5a-124">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="85e5a-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="85e5a-125">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="85e5a-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="85e5a-126">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="85e5a-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="85e5a-127">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="85e5a-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="85e5a-128">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="85e5a-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="85e5a-129">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="85e5a-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="85e5a-130">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="85e5a-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="85e5a-131">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="85e5a-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="85e5a-132">Property Statement</span><span class="sxs-lookup"><span data-stu-id="85e5a-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="85e5a-133">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="85e5a-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="85e5a-134">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="85e5a-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="85e5a-135">См. также</span><span class="sxs-lookup"><span data-stu-id="85e5a-135">See also</span></span>

- [<span data-ttu-id="85e5a-136">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="85e5a-136">Public</span></span>](public.md)
- [<span data-ttu-id="85e5a-137">Защищенный</span><span class="sxs-lookup"><span data-stu-id="85e5a-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="85e5a-138">Friend</span><span class="sxs-lookup"><span data-stu-id="85e5a-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="85e5a-139">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="85e5a-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="85e5a-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="85e5a-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="85e5a-141">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85e5a-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="85e5a-142">Процедуры</span><span class="sxs-lookup"><span data-stu-id="85e5a-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="85e5a-143">Структуры</span><span class="sxs-lookup"><span data-stu-id="85e5a-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="85e5a-144">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="85e5a-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
