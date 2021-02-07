---
description: 'Дополнительные сведения о: protected (Visual Basic)'
title: Защищенный
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 74a695e7c8ff06543a7118c935365e31af258171
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700940"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="c9fe1-103">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9fe1-103">Protected (Visual Basic)</span></span>

<span data-ttu-id="c9fe1-104">Модификатор доступа к члену, указывающий, что один или несколько объявленных программных элементов доступны только в своем собственном классе или производном классе.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-104">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9fe1-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9fe1-105">Remarks</span></span>

<span data-ttu-id="c9fe1-106">Иногда программный элемент, объявленный в классе, содержит конфиденциальные данные или ограниченный код и требуется ограничить доступ к элементу.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-106">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="c9fe1-107">Однако если класс является наследуемым и предполагается иерархия производных классов, то эти производные классы могут быть необходимы для доступа к данным или коду в этих производных классах.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-107">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="c9fe1-108">В этом случае необходимо, чтобы элемент был доступен как из базового класса, так и из всех производных классов.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-108">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="c9fe1-109">Чтобы ограничить доступ к элементу таким образом, его можно объявить с помощью `Protected` .</span><span class="sxs-lookup"><span data-stu-id="c9fe1-109">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="c9fe1-110">`Protected`Модификатор доступа можно сочетать с двумя другими модификаторами:</span><span class="sxs-lookup"><span data-stu-id="c9fe1-110">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="c9fe1-111">Модификатор [Protected Friend](protected-friend.md) делает член класса доступным из этого класса, из производных классов и из той же сборки, в которой определен класс.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-111">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="c9fe1-112">Модификатор [Private protected](private-protected.md) делает член класса доступным для производных типов, но только внутри его содержащей сборки.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-112">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="c9fe1-113">Правила</span><span class="sxs-lookup"><span data-stu-id="c9fe1-113">Rules</span></span>

<span data-ttu-id="c9fe1-114">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="c9fe1-114">**Declaration Context.**</span></span> <span data-ttu-id="c9fe1-115">Можно использовать `Protected` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-115">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="c9fe1-116">Это означает, что контекст объявления для `Protected` элемента должен быть классом и не может быть исходным файлом, пространством имен, интерфейсом, модулем, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-116">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="c9fe1-117">Поведение</span><span class="sxs-lookup"><span data-stu-id="c9fe1-117">Behavior</span></span>

- <span data-ttu-id="c9fe1-118">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="c9fe1-118">**Access Level.**</span></span> <span data-ttu-id="c9fe1-119">Весь код в классе может обращаться к его элементам.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-119">All code in a class can access its elements.</span></span> <span data-ttu-id="c9fe1-120">Код в любом классе, производном от базового класса, может обращаться ко всем `Protected` элементам базового класса.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="c9fe1-121">Это справедливо для всех поколений наследования.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="c9fe1-122">Это означает, что класс может обращаться к `Protected` элементам базового класса базового класса и т. д.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="c9fe1-123">Защищенный доступ не является надмножеством или подмножеством дружественного доступа.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-123">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="c9fe1-124">**Модификаторы доступа.**</span><span class="sxs-lookup"><span data-stu-id="c9fe1-124">**Access Modifiers.**</span></span> <span data-ttu-id="c9fe1-125">Ключевые слова, определяющие уровень доступа, называются *модификаторами доступа*.</span><span class="sxs-lookup"><span data-stu-id="c9fe1-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c9fe1-126">Сравнение модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c9fe1-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="c9fe1-127">Модификатор `Protected` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="c9fe1-127">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="c9fe1-128">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="c9fe1-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="c9fe1-129">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="c9fe1-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="c9fe1-130">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c9fe1-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="c9fe1-131">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="c9fe1-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="c9fe1-132">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="c9fe1-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="c9fe1-133">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="c9fe1-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="c9fe1-134">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="c9fe1-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="c9fe1-135">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c9fe1-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="c9fe1-136">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="c9fe1-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="c9fe1-137">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c9fe1-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="c9fe1-138">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="c9fe1-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="c9fe1-139">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c9fe1-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="c9fe1-140">См. также</span><span class="sxs-lookup"><span data-stu-id="c9fe1-140">See also</span></span>

- [<span data-ttu-id="c9fe1-141">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="c9fe1-141">Public</span></span>](public.md)
- [<span data-ttu-id="c9fe1-142">Friend</span><span class="sxs-lookup"><span data-stu-id="c9fe1-142">Friend</span></span>](friend.md)
- [<span data-ttu-id="c9fe1-143">Частная</span><span class="sxs-lookup"><span data-stu-id="c9fe1-143">Private</span></span>](private.md)
- [<span data-ttu-id="c9fe1-144">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="c9fe1-144">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="c9fe1-145">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c9fe1-145">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="c9fe1-146">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9fe1-146">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c9fe1-147">Процедуры</span><span class="sxs-lookup"><span data-stu-id="c9fe1-147">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c9fe1-148">Структуры</span><span class="sxs-lookup"><span data-stu-id="c9fe1-148">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c9fe1-149">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="c9fe1-149">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
