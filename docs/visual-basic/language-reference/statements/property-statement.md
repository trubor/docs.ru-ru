---
description: 'Дополнительные сведения: Оператор Property'
title: Property Statement
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 95f2ac1f993fc8698d2033dfe50d925cd55a7dc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741397"
---
# <a name="property-statement"></a><span data-ttu-id="95766-103">Property Statement</span><span class="sxs-lookup"><span data-stu-id="95766-103">Property Statement</span></span>

<span data-ttu-id="95766-104">Объявляет имя свойства и процедуры свойства, используемые для хранения и извлечения значения свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-104">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="95766-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95766-105">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="95766-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="95766-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="95766-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-107">Optional.</span></span> <span data-ttu-id="95766-108">Список атрибутов, применяемых к этому свойству `Get` или `Set` процедуре.</span><span class="sxs-lookup"><span data-stu-id="95766-108">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="95766-109">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="95766-109">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="95766-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-110">Optional.</span></span> <span data-ttu-id="95766-111">Указывает, что это свойство является свойством по умолчанию для класса или структуры, в которой он определен.</span><span class="sxs-lookup"><span data-stu-id="95766-111">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="95766-112">Свойства по умолчанию должны принимать параметры и могут быть заданы и получены без указания имени свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-112">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="95766-113">Если объявить свойство как `Default` , нельзя использовать `Private` для свойства или для любой из его процедур свойств.</span><span class="sxs-lookup"><span data-stu-id="95766-113">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="95766-114">Необязательно для инструкции и не более чем с `Property` одним из `Get` `Set` операторов и.</span><span class="sxs-lookup"><span data-stu-id="95766-114">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="95766-115">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="95766-115">Can be one of the following:</span></span>

  - [<span data-ttu-id="95766-116">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="95766-116">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="95766-117">Защищенный</span><span class="sxs-lookup"><span data-stu-id="95766-117">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="95766-118">Friend</span><span class="sxs-lookup"><span data-stu-id="95766-118">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="95766-119">Частная</span><span class="sxs-lookup"><span data-stu-id="95766-119">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="95766-120">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="95766-120">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="95766-121">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="95766-121">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="95766-122">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="95766-122">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="95766-123">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-123">Optional.</span></span> <span data-ttu-id="95766-124">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="95766-124">Can be one of the following:</span></span>

  - [<span data-ttu-id="95766-125">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="95766-125">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="95766-126">Переопределения</span><span class="sxs-lookup"><span data-stu-id="95766-126">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="95766-127">Overridable</span><span class="sxs-lookup"><span data-stu-id="95766-127">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="95766-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="95766-128">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="95766-129">MustOverride</span><span class="sxs-lookup"><span data-stu-id="95766-129">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="95766-130">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-130">Optional.</span></span> <span data-ttu-id="95766-131">См. раздел [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="95766-131">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="95766-132">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-132">Optional.</span></span> <span data-ttu-id="95766-133">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="95766-133">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="95766-134">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-134">Optional.</span></span> <span data-ttu-id="95766-135">См. раздел [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="95766-135">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="95766-136">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-136">Optional.</span></span> <span data-ttu-id="95766-137">См. раздел [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="95766-137">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="95766-138">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-138">Optional.</span></span> <span data-ttu-id="95766-139">См. [итератор](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="95766-139">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="95766-140">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-140">Required.</span></span> <span data-ttu-id="95766-141">Имя свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-141">Name of the property.</span></span> <span data-ttu-id="95766-142">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="95766-142">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="95766-143">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-143">Optional.</span></span> <span data-ttu-id="95766-144">Список имен локальных переменных, представляющих параметры этого свойства, и возможные дополнительные параметры `Set` процедуры.</span><span class="sxs-lookup"><span data-stu-id="95766-144">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="95766-145">См. [список параметров](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="95766-145">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="95766-146">Обязательный `Option Strict` , если имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="95766-146">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="95766-147">Тип данных значения, возвращаемого этим свойством.</span><span class="sxs-lookup"><span data-stu-id="95766-147">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="95766-148">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-148">Optional.</span></span> <span data-ttu-id="95766-149">Указывает, что это свойство реализует одно или несколько свойств, каждое из которых определено в интерфейсе, реализуемом классом или структурой этого свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-149">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="95766-150">См. [инструкцию Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95766-150">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="95766-151">Является обязательным, если предоставлен параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="95766-151">Required if `Implements` is supplied.</span></span> <span data-ttu-id="95766-152">Список реализуемых свойств.</span><span class="sxs-lookup"><span data-stu-id="95766-152">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="95766-153">Каждый элемент `implementedproperty` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="95766-153">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="95766-154">Отделение</span><span class="sxs-lookup"><span data-stu-id="95766-154">Part</span></span>|<span data-ttu-id="95766-155">Описание</span><span class="sxs-lookup"><span data-stu-id="95766-155">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="95766-156">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-156">Required.</span></span> <span data-ttu-id="95766-157">Имя интерфейса, реализованного в классе или структуре этого свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-157">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="95766-158">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-158">Required.</span></span> <span data-ttu-id="95766-159">Имя, по которому определено свойство `interface` .</span><span class="sxs-lookup"><span data-stu-id="95766-159">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="95766-160">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-160">Optional.</span></span> <span data-ttu-id="95766-161">Требуется, если свойство помечено как `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="95766-161">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="95766-162">Запускает `Get` процедуру свойства, которая используется для возврата значения свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-162">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="95766-163">`Get`Инструкция не используется с [автоматической реализацией свойств](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="95766-163">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="95766-164">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-164">Optional.</span></span> <span data-ttu-id="95766-165">Блок инструкций для выполнения в `Get` `Set` процедуре или.</span><span class="sxs-lookup"><span data-stu-id="95766-165">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="95766-166">Завершает `Get` процедуру свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-166">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="95766-167">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="95766-167">Optional.</span></span> <span data-ttu-id="95766-168">Требуется, если свойство помечено как `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="95766-168">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="95766-169">Запускает `Set` процедуру свойства, используемую для хранения значения свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-169">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="95766-170">`Set`Инструкция не используется с [автоматической реализацией свойств](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="95766-170">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="95766-171">Завершает `Set` процедуру свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-171">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="95766-172">Завершает определение этого свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-172">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="95766-173">Remarks</span><span class="sxs-lookup"><span data-stu-id="95766-173">Remarks</span></span>

<span data-ttu-id="95766-174">`Property`Оператор вводит объявление свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-174">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="95766-175">Свойство может иметь `Get` процедуру (только для чтения), `Set` процедуру (только для записи) или и то, и другое (чтение и запись).</span><span class="sxs-lookup"><span data-stu-id="95766-175">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="95766-176">Процедуру и можно опустить `Get` `Set` при использовании автоматического реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-176">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="95766-177">Дополнительные сведения см. в разделе [Автоматически реализуемые свойства](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="95766-177">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="95766-178">Можно использовать `Property` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="95766-178">You can use `Property` only at class level.</span></span> <span data-ttu-id="95766-179">Это означает, что *контекст объявления* для свойства должен быть классом, структурой, модулем или интерфейсом и не может быть исходным файлом, пространством имен, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="95766-179">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="95766-180">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="95766-180">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="95766-181">По умолчанию свойства используют общий доступ.</span><span class="sxs-lookup"><span data-stu-id="95766-181">By default, properties use public access.</span></span> <span data-ttu-id="95766-182">Можно настроить уровень доступа свойства с помощью модификатора доступа в `Property` инструкции, и при необходимости можно настроить одну из его процедур свойств на более ограниченный уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="95766-182">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="95766-183">Visual Basic передает параметр в `Set` процедуру во время назначения свойств.</span><span class="sxs-lookup"><span data-stu-id="95766-183">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="95766-184">Если параметр для не указан `Set` , в интегрированной среде разработки (IDE) используется неявный параметр с именем `value` .</span><span class="sxs-lookup"><span data-stu-id="95766-184">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="95766-185">Этот параметр содержит значение, присваиваемое свойству.</span><span class="sxs-lookup"><span data-stu-id="95766-185">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="95766-186">Обычно это значение сохраняется в закрытой локальной переменной и возвращается при каждом `Get` вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="95766-186">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="95766-187">Правила</span><span class="sxs-lookup"><span data-stu-id="95766-187">Rules</span></span>

- <span data-ttu-id="95766-188">**Уровни смешанного доступа.**</span><span class="sxs-lookup"><span data-stu-id="95766-188">**Mixed Access Levels.**</span></span> <span data-ttu-id="95766-189">При определении свойства для чтения и записи можно дополнительно указать другой уровень доступа для `Get` `Set` процедуры или, но не для обоих.</span><span class="sxs-lookup"><span data-stu-id="95766-189">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="95766-190">В этом случае уровень доступа процедуры должен быть более четким, чем уровень доступа свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-190">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="95766-191">Например, если свойство объявлено `Friend` , можно объявить `Set` процедуру `Private` , но не `Public` .</span><span class="sxs-lookup"><span data-stu-id="95766-191">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="95766-192">При определении `ReadOnly` `WriteOnly` свойства или процедура с одним свойством ( `Get` или `Set` соответственно) представляет все свойство.</span><span class="sxs-lookup"><span data-stu-id="95766-192">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="95766-193">Для такой процедуры нельзя объявить другой уровень доступа, поскольку в этом случае для свойства будет задано два уровня доступа.</span><span class="sxs-lookup"><span data-stu-id="95766-193">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="95766-194">**Тип возвращаемого значения.**</span><span class="sxs-lookup"><span data-stu-id="95766-194">**Return Type.**</span></span> <span data-ttu-id="95766-195">`Property`Оператор может объявить тип данных возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="95766-195">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="95766-196">Можно указать любой тип данных или имя перечисления, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="95766-196">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="95766-197">Если не указать `returntype` , свойство возвращает значение `Object` .</span><span class="sxs-lookup"><span data-stu-id="95766-197">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="95766-198">**Реализации.**</span><span class="sxs-lookup"><span data-stu-id="95766-198">**Implementation.**</span></span> <span data-ttu-id="95766-199">Если это свойство использует `Implements` ключевое слово, содержащий класс или структуру должны иметь `Implements` оператор, непосредственно следующий за `Class` `Structure` оператором или.</span><span class="sxs-lookup"><span data-stu-id="95766-199">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="95766-200">`Implements`Инструкция должна включать каждый интерфейс, указанный в `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="95766-200">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="95766-201">Однако имя, по которому интерфейс определяет `Property` (in `definedname` ), не обязательно должно совпадать с именем этого свойства (в `name` ).</span><span class="sxs-lookup"><span data-stu-id="95766-201">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="95766-202">Поведение</span><span class="sxs-lookup"><span data-stu-id="95766-202">Behavior</span></span>

- <span data-ttu-id="95766-203">**Возврат из процедуры свойства.**</span><span class="sxs-lookup"><span data-stu-id="95766-203">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="95766-204">Когда `Get` процедура или `Set` возвращает в вызывающий код, выполнение продолжится с оператора, следующего за оператором, вызвавшим ее.</span><span class="sxs-lookup"><span data-stu-id="95766-204">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="95766-205">`Exit Property`Операторы и `Return` вызывают немедленный выход из процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-205">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="95766-206">Любое количество `Exit Property` инструкций и `Return` может использоваться в любом месте процедуры, и можно смешивать `Exit Property` `Return` операторы и.</span><span class="sxs-lookup"><span data-stu-id="95766-206">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="95766-207">**Возвращаемое значение.**</span><span class="sxs-lookup"><span data-stu-id="95766-207">**Return Value.**</span></span> <span data-ttu-id="95766-208">Чтобы вернуть значение из `Get` процедуры, можно либо присвоить значение имени свойства, либо включить его в `Return` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="95766-208">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="95766-209">В следующем примере возвращаемое значение присваивается имени свойства `quoteForTheDay` , а затем используется `Exit Property` оператор для возврата.</span><span class="sxs-lookup"><span data-stu-id="95766-209">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="95766-210">Если вы используете `Exit Property` без присвоения значения `name` , `Get` процедура возвращает значение по умолчанию для типа данных свойства.</span><span class="sxs-lookup"><span data-stu-id="95766-210">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="95766-211">`Return`Инструкция в то же время присваивает `Get` возвращаемое значение процедуры и завершает процедуру.</span><span class="sxs-lookup"><span data-stu-id="95766-211">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="95766-212">В следующем примере приведена иллюстрация этого.</span><span class="sxs-lookup"><span data-stu-id="95766-212">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="95766-213">Пример</span><span class="sxs-lookup"><span data-stu-id="95766-213">Example</span></span>

<span data-ttu-id="95766-214">В следующем примере объявляется свойство в классе.</span><span class="sxs-lookup"><span data-stu-id="95766-214">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="95766-215">См. также</span><span class="sxs-lookup"><span data-stu-id="95766-215">See also</span></span>

- [<span data-ttu-id="95766-216">Автоматически реализуемые свойства</span><span class="sxs-lookup"><span data-stu-id="95766-216">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="95766-217">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="95766-217">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="95766-218">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="95766-218">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="95766-219">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="95766-219">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="95766-220">Список параметров</span><span class="sxs-lookup"><span data-stu-id="95766-220">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="95766-221">Default</span><span class="sxs-lookup"><span data-stu-id="95766-221">Default</span></span>](../modifiers/default.md)
