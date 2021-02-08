---
description: 'Дополнительные сведения о: Friend (Visual Basic)'
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: ef2444555c05d6a4b24048316e282d269d4b7f1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774594"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="c0657-103">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0657-103">Friend (Visual Basic)</span></span>

<span data-ttu-id="c0657-104">Указывает, что один или несколько объявленных программных элементов доступны только в пределах сборки, содержащей их объявление.</span><span class="sxs-lookup"><span data-stu-id="c0657-104">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0657-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="c0657-105">Remarks</span></span>  

 <span data-ttu-id="c0657-106">Во многих случаях требуется, чтобы элементы программирования, такие как классы и структуры, использовались целой сборкой, а не только компонентом, который их объявляет.</span><span class="sxs-lookup"><span data-stu-id="c0657-106">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="c0657-107">Однако может быть нежелательно, чтобы они были доступны коду за пределами сборки (например, если приложение является собственным).</span><span class="sxs-lookup"><span data-stu-id="c0657-107">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="c0657-108">Если требуется ограничить доступ к элементу таким образом, его можно объявить с помощью `Friend` модификатора.</span><span class="sxs-lookup"><span data-stu-id="c0657-108">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="c0657-109">Код в других классах, структурах и модулях, компилируемых в одну и ту же сборку, может обращаться ко всем `Friend` элементам в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="c0657-109">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="c0657-110">`Friend` доступ часто является предпочтительным уровнем для программных элементов приложения, а `Friend` также уровнем доступа по умолчанию для интерфейса, модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c0657-110">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="c0657-111">Можно использовать `Friend` только на уровне модуля, интерфейса или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="c0657-111">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="c0657-112">Таким образом, контекст объявления для `Friend` элемента должен быть исходным файлом, пространством имен, интерфейсом, модулем, классом или структурой. он не может быть процедурой.</span><span class="sxs-lookup"><span data-stu-id="c0657-112">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="c0657-113">Можно также использовать модификатор доступа [Protected Friend](protected-friend.md) , который делает член класса доступным из этого класса, из производных классов и из той же сборки, в которой определен класс.</span><span class="sxs-lookup"><span data-stu-id="c0657-113">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="c0657-114">Для ограничения доступа к члену из его класса и из производных классов в той же сборке используется модификатор [закрытого](private-protected.md) доступа.</span><span class="sxs-lookup"><span data-stu-id="c0657-114">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="c0657-115">Сравнение `Friend` и других модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c0657-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0657-116">Можно указать, что другая сборка является дружественной, что позволяет ей получить доступ ко всем типам и членам, помеченным как `Friend` .</span><span class="sxs-lookup"><span data-stu-id="c0657-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="c0657-117">Дополнительные сведения см. в разделе [Дружественные сборки](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="c0657-117">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0657-118">Пример</span><span class="sxs-lookup"><span data-stu-id="c0657-118">Example</span></span>  

 <span data-ttu-id="c0657-119">Следующий класс использует `Friend` модификатор, чтобы разрешить другим элементам программирования в той же сборке доступ к определенным элементам.</span><span class="sxs-lookup"><span data-stu-id="c0657-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="c0657-120">Использование</span><span class="sxs-lookup"><span data-stu-id="c0657-120">Usage</span></span>  

 <span data-ttu-id="c0657-121">Модификатор можно использовать `Friend` в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="c0657-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="c0657-122">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="c0657-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="c0657-123">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="c0657-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="c0657-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c0657-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="c0657-125">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="c0657-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="c0657-126">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="c0657-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="c0657-127">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="c0657-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="c0657-128">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="c0657-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="c0657-129">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c0657-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="c0657-130">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="c0657-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="c0657-131">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="c0657-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="c0657-132">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c0657-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="c0657-133">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="c0657-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="c0657-134">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c0657-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0657-135">См. также</span><span class="sxs-lookup"><span data-stu-id="c0657-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="c0657-136">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="c0657-136">Public</span></span>](public.md)
- [<span data-ttu-id="c0657-137">Защищенный</span><span class="sxs-lookup"><span data-stu-id="c0657-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="c0657-138">Частная</span><span class="sxs-lookup"><span data-stu-id="c0657-138">Private</span></span>](private.md)
- [<span data-ttu-id="c0657-139">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="c0657-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="c0657-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c0657-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="c0657-141">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0657-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c0657-142">Процедуры</span><span class="sxs-lookup"><span data-stu-id="c0657-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c0657-143">Структуры</span><span class="sxs-lookup"><span data-stu-id="c0657-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c0657-144">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="c0657-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
