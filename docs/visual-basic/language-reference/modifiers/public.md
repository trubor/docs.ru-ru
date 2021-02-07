---
description: 'Дополнительные сведения о: public (Visual Basic)'
title: Открытый
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 1083ca877cf99917291523fe10f6561784ff06a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700927"
---
# <a name="public-visual-basic"></a><span data-ttu-id="ec4fa-103">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec4fa-103">Public (Visual Basic)</span></span>

<span data-ttu-id="ec4fa-104">Указывает, что один или несколько объявленных программных элементов не имеют ограничений доступа.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-104">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4fa-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="ec4fa-105">Remarks</span></span>  

 <span data-ttu-id="ec4fa-106">При публикации компонента или набора компонентов, таких как библиотека классов, обычно требуется, чтобы элементы программирования были доступны любому коду, взаимодействующему со сборкой.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-106">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="ec4fa-107">Чтобы обеспечить такой неограниченный доступ к элементу, его можно объявить с помощью `Public` .</span><span class="sxs-lookup"><span data-stu-id="ec4fa-107">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="ec4fa-108">Открытый доступ является обычным уровнем для программного элемента, если нет необходимости ограничивать доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-108">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="ec4fa-109">Обратите внимание, что уровень доступа элемента, объявленного в интерфейсе, модуле, классе или структуре, по умолчанию имеет значение `Public` , если вы не объявили его в противном случае.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-109">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ec4fa-110">Правила</span><span class="sxs-lookup"><span data-stu-id="ec4fa-110">Rules</span></span>  
  
- <span data-ttu-id="ec4fa-111">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="ec4fa-111">**Declaration Context.**</span></span> <span data-ttu-id="ec4fa-112">Можно использовать `Public` только на уровне модуля, интерфейса или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-112">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="ec4fa-113">Это означает, что контекст объявления для `Public` элемента должен быть исходным файлом, пространством имен, интерфейсом, модулем, классом или структурой и не может быть процедурой.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-113">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ec4fa-114">Поведение</span><span class="sxs-lookup"><span data-stu-id="ec4fa-114">Behavior</span></span>  
  
- <span data-ttu-id="ec4fa-115">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="ec4fa-115">**Access Level.**</span></span> <span data-ttu-id="ec4fa-116">Весь код, который может получить доступ к модулю, классу или структуре, может получить доступ к его `Public` элементам.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-116">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="ec4fa-117">**Доступ по умолчанию.**</span><span class="sxs-lookup"><span data-stu-id="ec4fa-117">**Default Access.**</span></span> <span data-ttu-id="ec4fa-118">Локальные переменные в процедуре по умолчанию имеют открытый доступ, и в них нельзя использовать какие-либо модификаторы доступа.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-118">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="ec4fa-119">**Модификаторы доступа.**</span><span class="sxs-lookup"><span data-stu-id="ec4fa-119">**Access Modifiers.**</span></span> <span data-ttu-id="ec4fa-120">Ключевые слова, определяющие уровень доступа, называются *модификаторами доступа*.</span><span class="sxs-lookup"><span data-stu-id="ec4fa-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ec4fa-121">Сравнение модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ec4fa-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="ec4fa-122">Модификатор `Public` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="ec4fa-122">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ec4fa-123">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="ec4fa-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="ec4fa-124">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="ec4fa-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="ec4fa-125">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="ec4fa-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="ec4fa-126">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="ec4fa-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="ec4fa-127">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="ec4fa-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="ec4fa-128">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="ec4fa-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="ec4fa-129">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="ec4fa-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="ec4fa-130">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="ec4fa-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="ec4fa-131">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="ec4fa-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="ec4fa-132">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="ec4fa-132">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="ec4fa-133">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="ec4fa-133">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="ec4fa-134">Property Statement</span><span class="sxs-lookup"><span data-stu-id="ec4fa-134">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="ec4fa-135">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="ec4fa-135">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="ec4fa-136">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="ec4fa-136">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec4fa-137">См. также</span><span class="sxs-lookup"><span data-stu-id="ec4fa-137">See also</span></span>

- [<span data-ttu-id="ec4fa-138">Защищенный</span><span class="sxs-lookup"><span data-stu-id="ec4fa-138">Protected</span></span>](protected.md)
- [<span data-ttu-id="ec4fa-139">Friend</span><span class="sxs-lookup"><span data-stu-id="ec4fa-139">Friend</span></span>](friend.md)
- [<span data-ttu-id="ec4fa-140">Частная</span><span class="sxs-lookup"><span data-stu-id="ec4fa-140">Private</span></span>](private.md)
- [<span data-ttu-id="ec4fa-141">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="ec4fa-141">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="ec4fa-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="ec4fa-142">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="ec4fa-143">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec4fa-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ec4fa-144">Процедуры</span><span class="sxs-lookup"><span data-stu-id="ec4fa-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ec4fa-145">Структуры</span><span class="sxs-lookup"><span data-stu-id="ec4fa-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ec4fa-146">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="ec4fa-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
