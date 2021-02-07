---
description: 'Дополнительные сведения о: Shadows (Visual Basic)'
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 4a455a78c36e15db977936b81c22e7a5b03d107e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700849"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="5951c-103">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5951c-103">Shadows (Visual Basic)</span></span>

<span data-ttu-id="5951c-104">Указывает, что объявленный программный элемент повторно объявляет и скрывает элемент с идентичным именем или набор перегруженных элементов в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="5951c-104">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="5951c-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="5951c-105">Remarks</span></span>

<span data-ttu-id="5951c-106">Основное назначение теневого копирования (которое также называется *скрытием по имени*) — сохранение определения членов класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-106">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="5951c-107">Базовый класс может быть подвергнут изменениям, создающим элемент с тем же именем, что и у уже определенного.</span><span class="sxs-lookup"><span data-stu-id="5951c-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="5951c-108">В этом случае `Shadows` Модификатор принудительно определяет ссылки через класс на определенный член, а не на новый элемент базового класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="5951c-109">Сокрытие и переопределение заменяют наследуемый элемент, но между этими подходами существуют значительные различия.</span><span class="sxs-lookup"><span data-stu-id="5951c-109">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="5951c-110">Дополнительные сведения см. [в разделе теневая поддержка в Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="5951c-110">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="5951c-111">Правила</span><span class="sxs-lookup"><span data-stu-id="5951c-111">Rules</span></span>

- <span data-ttu-id="5951c-112">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="5951c-112">**Declaration Context.**</span></span> <span data-ttu-id="5951c-113">Можно использовать `Shadows` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-113">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="5951c-114">Это означает, что контекст объявления для `Shadows` элемента должен быть классом и не может быть исходным файлом, пространством имен, интерфейсом, модулем, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="5951c-114">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="5951c-115">В одном операторе объявления можно объявить только один элемент с тенью.</span><span class="sxs-lookup"><span data-stu-id="5951c-115">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="5951c-116">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="5951c-116">**Combined Modifiers.**</span></span> <span data-ttu-id="5951c-117">Нельзя указывать `Shadows` вместе с `Overloads` , `Overrides` или `Static` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="5951c-117">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="5951c-118">**Типы элементов.**</span><span class="sxs-lookup"><span data-stu-id="5951c-118">**Element Types.**</span></span> <span data-ttu-id="5951c-119">Можно скрыть любой тип объявленного элемента, используя любой другой тип.</span><span class="sxs-lookup"><span data-stu-id="5951c-119">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="5951c-120">При скрытии свойства или процедуры с другим свойством или процедурой параметры и тип возвращаемого значения не должны совпадать с параметрами в свойстве или процедуре базового класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-120">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="5951c-121">**Данному.**</span><span class="sxs-lookup"><span data-stu-id="5951c-121">**Accessing.**</span></span> <span data-ttu-id="5951c-122">Затененный элемент в базовом классе обычно недоступен в производном классе, который его затеняет.</span><span class="sxs-lookup"><span data-stu-id="5951c-122">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="5951c-123">Однако применимы следующие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="5951c-123">However, the following considerations apply.</span></span>

  - <span data-ttu-id="5951c-124">Если элемент теневого копирования недоступен из кода, ссылающегося на него, ссылка разрешается в затененный элемент.</span><span class="sxs-lookup"><span data-stu-id="5951c-124">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="5951c-125">Например, если `Private` элемент затеняет элемент базового класса, код, который не имеет разрешения на доступ к `Private` элементу, обращается к элементу базового класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-125">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="5951c-126">При скрытии элемента доступ к затененному элементу по-прежнему можно получить через объект, объявленный с типом базового класса.</span><span class="sxs-lookup"><span data-stu-id="5951c-126">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="5951c-127">Доступ к нему также можно получить с помощью `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="5951c-127">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="5951c-128">Модификатор `Shadows` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="5951c-128">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="5951c-129">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="5951c-129">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="5951c-130">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="5951c-130">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="5951c-131">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="5951c-131">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="5951c-132">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="5951c-132">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="5951c-133">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="5951c-133">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="5951c-134">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="5951c-134">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="5951c-135">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="5951c-135">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="5951c-136">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="5951c-136">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="5951c-137">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="5951c-137">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="5951c-138">Property Statement</span><span class="sxs-lookup"><span data-stu-id="5951c-138">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="5951c-139">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="5951c-139">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="5951c-140">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="5951c-140">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="5951c-141">См. также</span><span class="sxs-lookup"><span data-stu-id="5951c-141">See also</span></span>

- [<span data-ttu-id="5951c-142">Общий</span><span class="sxs-lookup"><span data-stu-id="5951c-142">Shared</span></span>](shared.md)
- [<span data-ttu-id="5951c-143">статически.</span><span class="sxs-lookup"><span data-stu-id="5951c-143">Static</span></span>](static.md)
- [<span data-ttu-id="5951c-144">Частная</span><span class="sxs-lookup"><span data-stu-id="5951c-144">Private</span></span>](private.md)
- [<span data-ttu-id="5951c-145">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="5951c-145">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="5951c-146">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="5951c-146">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="5951c-147">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5951c-147">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="5951c-148">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5951c-148">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="5951c-149">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="5951c-149">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="5951c-150">Overridable</span><span class="sxs-lookup"><span data-stu-id="5951c-150">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="5951c-151">Переопределения</span><span class="sxs-lookup"><span data-stu-id="5951c-151">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="5951c-152">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5951c-152">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
