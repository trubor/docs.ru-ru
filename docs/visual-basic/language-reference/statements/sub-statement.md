---
description: 'Дополнительные сведения о: подоператоре (Visual Basic)'
title: Оператор Sub
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 9be40c8284c677a151e4b1665f0b49e5f852bf00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740994"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="baeb2-103">Оператор Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baeb2-103">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="baeb2-104">Объявляет имя, параметры и код, определяющие `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="baeb2-104">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="baeb2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="baeb2-105">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="baeb2-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="baeb2-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="baeb2-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-107">Optional.</span></span> <span data-ttu-id="baeb2-108">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-108">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="baeb2-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-109">Optional.</span></span> <span data-ttu-id="baeb2-110">Указывает определение разделяемого метода.</span><span class="sxs-lookup"><span data-stu-id="baeb2-110">Indicates definition of a partial method.</span></span> <span data-ttu-id="baeb2-111">См. раздел [разделяемые методы](../../programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-111">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="baeb2-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-112">Optional.</span></span> <span data-ttu-id="baeb2-113">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="baeb2-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="baeb2-114">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="baeb2-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="baeb2-115">Защищенный</span><span class="sxs-lookup"><span data-stu-id="baeb2-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="baeb2-116">Friend</span><span class="sxs-lookup"><span data-stu-id="baeb2-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="baeb2-117">Частная</span><span class="sxs-lookup"><span data-stu-id="baeb2-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="baeb2-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="baeb2-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="baeb2-119">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="baeb2-119">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="baeb2-120">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-120">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="baeb2-121">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-121">Optional.</span></span> <span data-ttu-id="baeb2-122">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="baeb2-122">Can be one of the following:</span></span>

  - [<span data-ttu-id="baeb2-123">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="baeb2-123">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="baeb2-124">Переопределения</span><span class="sxs-lookup"><span data-stu-id="baeb2-124">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="baeb2-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="baeb2-125">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="baeb2-126">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="baeb2-126">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="baeb2-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="baeb2-127">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="baeb2-128">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-128">Optional.</span></span> <span data-ttu-id="baeb2-129">См. раздел [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-129">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="baeb2-130">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-130">Optional.</span></span> <span data-ttu-id="baeb2-131">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-131">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="baeb2-132">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-132">Optional.</span></span> <span data-ttu-id="baeb2-133">См. статью [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-133">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="baeb2-134">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-134">Required.</span></span> <span data-ttu-id="baeb2-135">Имя процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-135">Name of the procedure.</span></span> <span data-ttu-id="baeb2-136">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="baeb2-137">Чтобы создать процедуру конструктора для класса, задайте в качестве имени `Sub` процедуры `New` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="baeb2-137">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="baeb2-138">Дополнительные сведения см. в разделе [время существования объекта: как создаются и уничтожаются объекты](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-138">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="baeb2-139">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-139">Optional.</span></span> <span data-ttu-id="baeb2-140">Список параметров типа для универсальной процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-140">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="baeb2-141">См. [список типов](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-141">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="baeb2-142">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-142">Optional.</span></span> <span data-ttu-id="baeb2-143">Список имен локальных переменных, представляющих параметры этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-143">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="baeb2-144">См. [список параметров](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-144">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="baeb2-145">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-145">Optional.</span></span> <span data-ttu-id="baeb2-146">Указывает, что эта процедура реализует одну или несколько `Sub` процедур, каждая из которых определена в интерфейсе, реализованном классом или структурой этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-146">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="baeb2-147">См. [инструкцию Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-147">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="baeb2-148">Является обязательным, если предоставлен параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="baeb2-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="baeb2-149">Список реализуемых процедур `Sub`.</span><span class="sxs-lookup"><span data-stu-id="baeb2-149">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="baeb2-150">Каждый элемент `implementedprocedure` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="baeb2-150">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="baeb2-151">Отделение</span><span class="sxs-lookup"><span data-stu-id="baeb2-151">Part</span></span>|<span data-ttu-id="baeb2-152">Описание</span><span class="sxs-lookup"><span data-stu-id="baeb2-152">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="baeb2-153">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-153">Required.</span></span> <span data-ttu-id="baeb2-154">Имя интерфейса, реализованного классом или структурой, содержащейся в этой процедуре.</span><span class="sxs-lookup"><span data-stu-id="baeb2-154">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="baeb2-155">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-155">Required.</span></span> <span data-ttu-id="baeb2-156">Имя, под которым процедура определена в `interface`.</span><span class="sxs-lookup"><span data-stu-id="baeb2-156">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="baeb2-157">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-157">Optional.</span></span> <span data-ttu-id="baeb2-158">Указывает, что эта процедура может управлять одним или несколькими конкретными событиями.</span><span class="sxs-lookup"><span data-stu-id="baeb2-158">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="baeb2-159">См. раздел [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-159">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="baeb2-160">Является обязательным, если предоставлен параметр `Handles`.</span><span class="sxs-lookup"><span data-stu-id="baeb2-160">Required if `Handles` is supplied.</span></span> <span data-ttu-id="baeb2-161">Список событий, обрабатываемых этой процедурой.</span><span class="sxs-lookup"><span data-stu-id="baeb2-161">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="baeb2-162">Каждый элемент `eventspecifier` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="baeb2-162">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="baeb2-163">Отделение</span><span class="sxs-lookup"><span data-stu-id="baeb2-163">Part</span></span>|<span data-ttu-id="baeb2-164">Описание</span><span class="sxs-lookup"><span data-stu-id="baeb2-164">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="baeb2-165">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-165">Required.</span></span> <span data-ttu-id="baeb2-166">Объектная переменная, объявленная с типом данных класса или структуры, которая вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="baeb2-166">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="baeb2-167">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-167">Required.</span></span> <span data-ttu-id="baeb2-168">Имя события, обрабатываемого этой процедурой.</span><span class="sxs-lookup"><span data-stu-id="baeb2-168">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="baeb2-169">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="baeb2-169">Optional.</span></span> <span data-ttu-id="baeb2-170">Блок инструкций для выполнения в рамках этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-170">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="baeb2-171">Завершает определение этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-171">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="baeb2-172">Remarks</span><span class="sxs-lookup"><span data-stu-id="baeb2-172">Remarks</span></span>

<span data-ttu-id="baeb2-173">Весь исполняемый код должен находиться внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-173">All executable code must be inside a procedure.</span></span> <span data-ttu-id="baeb2-174">Используйте `Sub` процедуру, если не нужно возвращать значение в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="baeb2-174">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="baeb2-175">Используйте `Function` процедуру, если требуется вернуть значение.</span><span class="sxs-lookup"><span data-stu-id="baeb2-175">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="baeb2-176">Определение подпроцедуры</span><span class="sxs-lookup"><span data-stu-id="baeb2-176">Defining a Sub Procedure</span></span>

<span data-ttu-id="baeb2-177">Процедуру можно определить `Sub` только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="baeb2-177">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="baeb2-178">Контекст объявления для процедуры, следовательно, должен быть классом, структурой, модулем или интерфейсом и не может быть исходным файлом, пространством имен, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="baeb2-178">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="baeb2-179">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="baeb2-180">`Sub` процедуры по умолчанию имеют открытый доступ.</span><span class="sxs-lookup"><span data-stu-id="baeb2-180">`Sub` procedures default to public access.</span></span> <span data-ttu-id="baeb2-181">Уровни доступа можно изменить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="baeb2-181">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="baeb2-182">Если в процедуре используется `Implements` ключевое слово, содержащий класс или структуру должны иметь `Implements` оператор, который сразу следует за `Class` `Structure` оператором или.</span><span class="sxs-lookup"><span data-stu-id="baeb2-182">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="baeb2-183">`Implements`Инструкция должна включать каждый интерфейс, указанный в `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="baeb2-183">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="baeb2-184">Однако имя, по которому интерфейс определяет `Sub` (в `definedname` ), не обязательно должен совпадать с именем этой процедуры (в `name` ).</span><span class="sxs-lookup"><span data-stu-id="baeb2-184">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="baeb2-185">Возврат из подпроцедуры</span><span class="sxs-lookup"><span data-stu-id="baeb2-185">Returning from a Sub Procedure</span></span>

<span data-ttu-id="baeb2-186">Когда `Sub` процедура возвращается в вызывающий код, выполнение переходит к инструкции после оператора, вызвавшего ее.</span><span class="sxs-lookup"><span data-stu-id="baeb2-186">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="baeb2-187">В следующем примере показан возврат из `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-187">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="baeb2-188">`Exit Sub`Операторы и `Return` вызывают немедленный выход из `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-188">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="baeb2-189">Любое количество `Exit Sub` инструкций и `Return` может использоваться в любом месте процедуры, и можно смешивать `Exit Sub` `Return` операторы и.</span><span class="sxs-lookup"><span data-stu-id="baeb2-189">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="baeb2-190">Вызов процедуры подпрограммы</span><span class="sxs-lookup"><span data-stu-id="baeb2-190">Calling a Sub Procedure</span></span>

<span data-ttu-id="baeb2-191">Процедура вызывается с `Sub` помощью имени процедуры в инструкции и затем после этого имени вместе со списком аргументов в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="baeb2-191">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="baeb2-192">Скобки можно опустить, только если не указаны аргументы.</span><span class="sxs-lookup"><span data-stu-id="baeb2-192">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="baeb2-193">Однако код является более удобочитаемым, если всегда включать круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="baeb2-193">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="baeb2-194">`Sub`Процедура и `Function` процедура могут иметь параметры и выполнять ряд инструкций.</span><span class="sxs-lookup"><span data-stu-id="baeb2-194">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="baeb2-195">Однако `Function` процедура возвращает значение, а `Sub` процедура — нет.</span><span class="sxs-lookup"><span data-stu-id="baeb2-195">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="baeb2-196">Поэтому нельзя использовать `Sub` процедуру в выражении.</span><span class="sxs-lookup"><span data-stu-id="baeb2-196">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="baeb2-197">`Call`Ключевое слово можно использовать при вызове `Sub` процедуры, но это ключевое слово не рекомендуется для большинства случаев использования.</span><span class="sxs-lookup"><span data-stu-id="baeb2-197">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="baeb2-198">Дополнительные сведения см. в разделе [оператор Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="baeb2-198">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="baeb2-199">Visual Basic иногда переупорядочивает арифметические выражения для повышения внутренней эффективности.</span><span class="sxs-lookup"><span data-stu-id="baeb2-199">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="baeb2-200">По этой причине, если список аргументов содержит выражения, вызывающие другие процедуры, не следует рассчитывать на то, что эти выражения будут вызываться в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="baeb2-200">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="baeb2-201">Процедуры Async</span><span class="sxs-lookup"><span data-stu-id="baeb2-201">Async Sub Procedures</span></span>

<span data-ttu-id="baeb2-202">С помощью функции Async можно вызывать асинхронные функции без использования явных обратных вызовов или вручную разделить код по нескольким функциям или лямбда-выражениям.</span><span class="sxs-lookup"><span data-stu-id="baeb2-202">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="baeb2-203">Если вы пометите процедуру с модификатором [Async](../modifiers/async.md) , то можете использовать оператор [await](../operators/await-operator.md) в процедуре.</span><span class="sxs-lookup"><span data-stu-id="baeb2-203">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="baeb2-204">Когда управление достигает `Await` выражения в `Async` процедуре, управление возвращается вызывающему объекту, и ход выполнения процедуры приостанавливается до тех пор, пока не завершится ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="baeb2-204">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="baeb2-205">После завершения задачи выполнение может быть возобновлено в процедуре.</span><span class="sxs-lookup"><span data-stu-id="baeb2-205">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="baeb2-206">`Async`Процедура возвращается к вызывающему объекту, когда происходит либо первый ожидающий объект, который еще не завершен, либо `Async` достигнут конец процедуры, в зависимости от того, что произойдет раньше.</span><span class="sxs-lookup"><span data-stu-id="baeb2-206">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="baeb2-207">Можно также пометить [оператор Function](function-statement.md) с помощью `Async` модификатора.</span><span class="sxs-lookup"><span data-stu-id="baeb2-207">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="baeb2-208">`Async`Функция может иметь тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> или <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="baeb2-208">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="baeb2-209">В примере далее в этом разделе показана `Async` функция, имеющая тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="baeb2-209">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="baeb2-210">`Async``Sub`процедуры в основном используются для обработчиков событий, где значение не может быть возвращено.</span><span class="sxs-lookup"><span data-stu-id="baeb2-210">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="baeb2-211">`Async` `Sub` Процедуру нельзя ожидать, и вызывающая `Async` `Sub` процедура не может перехватывать исключения, которые `Sub` создает процедура.</span><span class="sxs-lookup"><span data-stu-id="baeb2-211">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="baeb2-212">`Async`Процедура не может объявлять параметры [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="baeb2-212">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="baeb2-213">Дополнительные сведения о `Async` процедурах см. в разделе [Асинхронное программирование с использованием Async и await](../../programming-guide/concepts/async/index.md), [поток управления в асинхронных программах](../../programming-guide/concepts/async/control-flow-in-async-programs.md)и [асинхронные типы возвращаемых](../../programming-guide/concepts/async/async-return-types.md)данных.</span><span class="sxs-lookup"><span data-stu-id="baeb2-213">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="baeb2-214">Пример</span><span class="sxs-lookup"><span data-stu-id="baeb2-214">Example</span></span>

<span data-ttu-id="baeb2-215">В следующем примере оператор используется `Sub` для определения имени, параметров и кода, образующих тело `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-215">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="baeb2-216">Пример</span><span class="sxs-lookup"><span data-stu-id="baeb2-216">Example</span></span>

<span data-ttu-id="baeb2-217">В следующем примере `DelayAsync` — это, `Async` `Function` имеющий тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="baeb2-217">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="baeb2-218">`DelayAsync` имеет инструкцию `Return` , которая возвращает целое число.</span><span class="sxs-lookup"><span data-stu-id="baeb2-218">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="baeb2-219">Поэтому объявление функции `DelayAsync` должно иметь тип возвращаемого значения `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="baeb2-219">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="baeb2-220">Так как тип возвращаемого значения — `Task(Of Integer)` , вычисление `Await` выражения в `DoSomethingAsync` создает целое число, как показано в следующей инструкции: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="baeb2-220">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="baeb2-221">`startButton_Click`Процедура является примером `Async Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="baeb2-221">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="baeb2-222">Поскольку `DoSomethingAsync` является `Async` функцией, задача для вызова `DoSomethingAsync` должна быть ожидаемой, как показано в следующей инструкции: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="baeb2-222">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="baeb2-223">`startButton_Click` `Sub` Процедура должна быть определена с `Async` модификатором, так как содержит `Await` выражение.</span><span class="sxs-lookup"><span data-stu-id="baeb2-223">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="baeb2-224">См. также</span><span class="sxs-lookup"><span data-stu-id="baeb2-224">See also</span></span>

- [<span data-ttu-id="baeb2-225">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="baeb2-225">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="baeb2-226">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="baeb2-226">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="baeb2-227">Список параметров</span><span class="sxs-lookup"><span data-stu-id="baeb2-227">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="baeb2-228">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="baeb2-228">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="baeb2-229">Оператор Call</span><span class="sxs-lookup"><span data-stu-id="baeb2-229">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="baeb2-230">Окна</span><span class="sxs-lookup"><span data-stu-id="baeb2-230">Of</span></span>](of-clause.md)
- [<span data-ttu-id="baeb2-231">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="baeb2-231">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="baeb2-232">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="baeb2-232">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="baeb2-233">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="baeb2-233">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="baeb2-234">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="baeb2-234">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
