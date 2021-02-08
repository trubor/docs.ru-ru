---
description: Дополнительные сведения о операторе Module
title: Оператор Module
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 2a19bcfa4521d34b5a91fbc9de412a6d8f6f39c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768874"
---
# <a name="module-statement"></a><span data-ttu-id="deacb-103">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="deacb-103">Module Statement</span></span>

<span data-ttu-id="deacb-104">Объявляет имя модуля и вводит определение переменных, свойств, событий и процедур, которые входят в модуль.</span><span class="sxs-lookup"><span data-stu-id="deacb-104">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="deacb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="deacb-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="deacb-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="deacb-106">Parts</span></span>

`attributelist`  
<span data-ttu-id="deacb-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="deacb-107">Optional.</span></span> <span data-ttu-id="deacb-108">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-108">See [Attribute List](attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="deacb-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="deacb-109">Optional.</span></span> <span data-ttu-id="deacb-110">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="deacb-110">Can be one of the following:</span></span>

- [<span data-ttu-id="deacb-111">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="deacb-111">Public</span></span>](../modifiers/public.md)

- [<span data-ttu-id="deacb-112">Friend</span><span class="sxs-lookup"><span data-stu-id="deacb-112">Friend</span></span>](../modifiers/friend.md)

<span data-ttu-id="deacb-113">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-113">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="deacb-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="deacb-114">Required.</span></span> <span data-ttu-id="deacb-115">Имя этого модуля.</span><span class="sxs-lookup"><span data-stu-id="deacb-115">Name of this module.</span></span> <span data-ttu-id="deacb-116">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-116">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="deacb-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="deacb-117">Optional.</span></span> <span data-ttu-id="deacb-118">Инструкции, которые определяют переменные, свойства, события, процедуры и вложенные типы этого модуля.</span><span class="sxs-lookup"><span data-stu-id="deacb-118">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="deacb-119">Завершает `Module` Определение.</span><span class="sxs-lookup"><span data-stu-id="deacb-119">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="deacb-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="deacb-120">Remarks</span></span>

<span data-ttu-id="deacb-121">`Module`Оператор определяет ссылочный тип, доступный в пределах его пространства имен.</span><span class="sxs-lookup"><span data-stu-id="deacb-121">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="deacb-122">*Модуль* (иногда называемый *стандартным модулем*) аналогичен классу, но с некоторыми важными различиями.</span><span class="sxs-lookup"><span data-stu-id="deacb-122">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="deacb-123">Каждый модуль имеет ровно один экземпляр и не требует создания или назначения переменной.</span><span class="sxs-lookup"><span data-stu-id="deacb-123">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="deacb-124">Модули не поддерживают наследование или реализуют интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="deacb-124">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="deacb-125">Обратите внимание, что модуль не является *типом* в том смысле, что класс или структура — нельзя объявить программный элемент для типа данных модуля.</span><span class="sxs-lookup"><span data-stu-id="deacb-125">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="deacb-126">Можно использовать `Module` только на уровне пространства имен.</span><span class="sxs-lookup"><span data-stu-id="deacb-126">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="deacb-127">Это означает, что *контекст объявления* для модуля должен быть исходным файлом или пространством имен и не может быть классом, структурой, модулем, интерфейсом, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="deacb-127">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="deacb-128">Модуль нельзя вложить в другой модуль или в любой тип.</span><span class="sxs-lookup"><span data-stu-id="deacb-128">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="deacb-129">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-129">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="deacb-130">Модуль имеет то же время, что и программа.</span><span class="sxs-lookup"><span data-stu-id="deacb-130">A module has the same lifetime as your program.</span></span> <span data-ttu-id="deacb-131">Так как все его члены все `Shared` же, они также имеют время существования, равное значению программы.</span><span class="sxs-lookup"><span data-stu-id="deacb-131">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="deacb-132">Модули по умолчанию имеют доступ [Friend](../modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="deacb-132">Modules default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="deacb-133">Уровни доступа можно изменить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="deacb-133">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="deacb-134">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-134">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="deacb-135">Все члены модуля являются неявными `Shared` .</span><span class="sxs-lookup"><span data-stu-id="deacb-135">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="deacb-136">Классы и модули</span><span class="sxs-lookup"><span data-stu-id="deacb-136">Classes and Modules</span></span>

<span data-ttu-id="deacb-137">У этих элементов много сходства, но есть и некоторые важные отличия.</span><span class="sxs-lookup"><span data-stu-id="deacb-137">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="deacb-138">**Терминология.**</span><span class="sxs-lookup"><span data-stu-id="deacb-138">**Terminology.**</span></span> <span data-ttu-id="deacb-139">В предыдущих версиях Visual Basic распознаются два типа модулей: *модули классов* (CLS-файлы) и *стандартные модули* (файлы. BAS).</span><span class="sxs-lookup"><span data-stu-id="deacb-139">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="deacb-140">Текущая версия вызывает эти *классы* и *модули* соответственно.</span><span class="sxs-lookup"><span data-stu-id="deacb-140">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="deacb-141">**Общие члены.**</span><span class="sxs-lookup"><span data-stu-id="deacb-141">**Shared Members.**</span></span> <span data-ttu-id="deacb-142">Можно контролировать, является ли член класса общим или членом экземпляра.</span><span class="sxs-lookup"><span data-stu-id="deacb-142">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="deacb-143">**Объектная ориентация.**</span><span class="sxs-lookup"><span data-stu-id="deacb-143">**Object Orientation.**</span></span> <span data-ttu-id="deacb-144">Классы являются объектно-ориентированными, но модули — нет.</span><span class="sxs-lookup"><span data-stu-id="deacb-144">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="deacb-145">Таким образом, можно создавать экземпляры только классов в виде объектов.</span><span class="sxs-lookup"><span data-stu-id="deacb-145">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="deacb-146">Дополнительные сведения см. в разделе [объекты и классы](../../programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-146">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="deacb-147">Правила</span><span class="sxs-lookup"><span data-stu-id="deacb-147">Rules</span></span>

- <span data-ttu-id="deacb-148">**Модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="deacb-148">**Modifiers.**</span></span> <span data-ttu-id="deacb-149">Все члены модуля неявно являются [общими](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-149">All module members are implicitly [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="deacb-150">Нельзя использовать `Shared` ключевое слово при объявлении члена, и изменить общее состояние любого члена нельзя.</span><span class="sxs-lookup"><span data-stu-id="deacb-150">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="deacb-151">**Цепочк.**</span><span class="sxs-lookup"><span data-stu-id="deacb-151">**Inheritance.**</span></span> <span data-ttu-id="deacb-152">Модуль не может наследовать ни от какого типа <xref:System.Object> , от которого наследуют все модули.</span><span class="sxs-lookup"><span data-stu-id="deacb-152">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="deacb-153">В частности, один модуль не может наследовать от другого.</span><span class="sxs-lookup"><span data-stu-id="deacb-153">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="deacb-154">Нельзя использовать [инструкцию Inherits](inherits-statement.md) в определении модуля, даже для указания <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="deacb-154">You cannot use the [Inherits Statement](inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="deacb-155">**Свойство по умолчанию.**</span><span class="sxs-lookup"><span data-stu-id="deacb-155">**Default Property.**</span></span> <span data-ttu-id="deacb-156">В модуле нельзя определить свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="deacb-156">You cannot define any default properties in a module.</span></span> <span data-ttu-id="deacb-157">Дополнительные сведения см. в разделе [Default](../modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-157">For more information, see [Default](../modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="deacb-158">Поведение</span><span class="sxs-lookup"><span data-stu-id="deacb-158">Behavior</span></span>

- <span data-ttu-id="deacb-159">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="deacb-159">**Access Level.**</span></span> <span data-ttu-id="deacb-160">Внутри модуля можно объявить каждый элемент с собственным уровнем доступа.</span><span class="sxs-lookup"><span data-stu-id="deacb-160">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="deacb-161">Члены модуля по умолчанию имеют [открытый](../modifiers/public.md) доступ, за исключением переменных и констант, которые по умолчанию имеют [частный](../modifiers/private.md) доступ.</span><span class="sxs-lookup"><span data-stu-id="deacb-161">Module members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="deacb-162">Если модуль имеет более ограниченный доступ, чем один из его членов, приоритет имеет указанный уровень доступа к модулю.</span><span class="sxs-lookup"><span data-stu-id="deacb-162">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="deacb-163">**Которых.**</span><span class="sxs-lookup"><span data-stu-id="deacb-163">**Scope.**</span></span> <span data-ttu-id="deacb-164">Модуль находится в пределах пространства имен.</span><span class="sxs-lookup"><span data-stu-id="deacb-164">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="deacb-165">Областью действия каждого члена модуля является весь модуль.</span><span class="sxs-lookup"><span data-stu-id="deacb-165">The scope of every module member is the entire module.</span></span> <span data-ttu-id="deacb-166">Обратите внимание, что все члены проводят *продвижение по типам*, что приводит к повышению уровня их области до пространства имен, содержащего модуль.</span><span class="sxs-lookup"><span data-stu-id="deacb-166">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="deacb-167">Дополнительные сведения см. в разделе [повышение типа](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-167">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="deacb-168">**Квалификацию.**</span><span class="sxs-lookup"><span data-stu-id="deacb-168">**Qualification.**</span></span> <span data-ttu-id="deacb-169">В проекте может быть несколько модулей, и члены с одинаковыми именами можно объявить в двух или более модулях.</span><span class="sxs-lookup"><span data-stu-id="deacb-169">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="deacb-170">Однако необходимо определить любую ссылку на такой элемент с соответствующим именем модуля, если ссылка находится за пределами этого модуля.</span><span class="sxs-lookup"><span data-stu-id="deacb-170">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="deacb-171">Для получения дополнительной информации см. [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="deacb-171">For more information, see [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="deacb-172">Пример</span><span class="sxs-lookup"><span data-stu-id="deacb-172">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="deacb-173">См. также</span><span class="sxs-lookup"><span data-stu-id="deacb-173">See also</span></span>

- [<span data-ttu-id="deacb-174">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="deacb-174">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="deacb-175">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="deacb-175">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="deacb-176">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="deacb-176">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="deacb-177">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="deacb-177">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="deacb-178">Property Statement</span><span class="sxs-lookup"><span data-stu-id="deacb-178">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="deacb-179">Повышение типа</span><span class="sxs-lookup"><span data-stu-id="deacb-179">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
