---
description: Дополнительные сведения о инструкции Function (Visual Basic)
title: Оператор Function
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: e8a05b02c3a214f0572e85c1fc973cb9f03118ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769069"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="10310-103">Оператор Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10310-103">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="10310-104">Объявляет имя, параметры и код, определяющие `Function` процедуру.</span><span class="sxs-lookup"><span data-stu-id="10310-104">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="10310-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="10310-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="10310-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="10310-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="10310-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-107">Optional.</span></span> <span data-ttu-id="10310-108">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="10310-108">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="10310-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-109">Optional.</span></span> <span data-ttu-id="10310-110">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="10310-110">Can be one of the following:</span></span>

  - [<span data-ttu-id="10310-111">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="10310-111">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="10310-112">Защищенный</span><span class="sxs-lookup"><span data-stu-id="10310-112">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="10310-113">Friend</span><span class="sxs-lookup"><span data-stu-id="10310-113">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="10310-114">Частная</span><span class="sxs-lookup"><span data-stu-id="10310-114">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="10310-115">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="10310-115">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="10310-116">Частный защищенный</span><span class="sxs-lookup"><span data-stu-id="10310-116">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="10310-117">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="10310-117">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="10310-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-118">Optional.</span></span> <span data-ttu-id="10310-119">Может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="10310-119">Can be one of the following:</span></span>

  - [<span data-ttu-id="10310-120">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="10310-120">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="10310-121">Переопределения</span><span class="sxs-lookup"><span data-stu-id="10310-121">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="10310-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="10310-122">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="10310-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="10310-123">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="10310-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="10310-124">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="10310-125">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-125">Optional.</span></span> <span data-ttu-id="10310-126">См. раздел [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="10310-126">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="10310-127">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-127">Optional.</span></span> <span data-ttu-id="10310-128">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="10310-128">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="10310-129">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-129">Optional.</span></span> <span data-ttu-id="10310-130">См. статью [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="10310-130">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="10310-131">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-131">Optional.</span></span> <span data-ttu-id="10310-132">См. [итератор](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="10310-132">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="10310-133">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-133">Required.</span></span> <span data-ttu-id="10310-134">Имя процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-134">Name of the procedure.</span></span> <span data-ttu-id="10310-135">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="10310-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="10310-136">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-136">Optional.</span></span> <span data-ttu-id="10310-137">Список параметров типа для универсальной процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="10310-138">См. [список типов](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="10310-138">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="10310-139">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-139">Optional.</span></span> <span data-ttu-id="10310-140">Список имен локальных переменных, представляющих параметры этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="10310-141">См. [список параметров](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="10310-141">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="10310-142">Обязательный `Option Strict` , если имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="10310-142">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="10310-143">Тип данных значения, возвращаемого этой процедурой.</span><span class="sxs-lookup"><span data-stu-id="10310-143">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="10310-144">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-144">Optional.</span></span> <span data-ttu-id="10310-145">Указывает, что эта процедура реализует одну или несколько `Function` процедур, каждая из которых определена в интерфейсе, реализованном классом или структурой этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-145">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="10310-146">См. [инструкцию Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10310-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="10310-147">Является обязательным, если предоставлен параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="10310-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="10310-148">Список реализуемых процедур `Function`.</span><span class="sxs-lookup"><span data-stu-id="10310-148">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="10310-149">Каждый элемент `implementedprocedure` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="10310-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="10310-150">Отделение</span><span class="sxs-lookup"><span data-stu-id="10310-150">Part</span></span>|<span data-ttu-id="10310-151">Описание</span><span class="sxs-lookup"><span data-stu-id="10310-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="10310-152">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-152">Required.</span></span> <span data-ttu-id="10310-153">Имя интерфейса, реализованного классом или структурой, содержащейся в этой процедуре.</span><span class="sxs-lookup"><span data-stu-id="10310-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="10310-154">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-154">Required.</span></span> <span data-ttu-id="10310-155">Имя, под которым процедура определена в `interface`.</span><span class="sxs-lookup"><span data-stu-id="10310-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="10310-156">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-156">Optional.</span></span> <span data-ttu-id="10310-157">Указывает, что эта процедура может управлять одним или несколькими конкретными событиями.</span><span class="sxs-lookup"><span data-stu-id="10310-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="10310-158">См. раздел [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="10310-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="10310-159">Является обязательным, если предоставлен параметр `Handles`.</span><span class="sxs-lookup"><span data-stu-id="10310-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="10310-160">Список событий, обрабатываемых этой процедурой.</span><span class="sxs-lookup"><span data-stu-id="10310-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="10310-161">Каждый элемент `eventspecifier` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="10310-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="10310-162">Отделение</span><span class="sxs-lookup"><span data-stu-id="10310-162">Part</span></span>|<span data-ttu-id="10310-163">Описание</span><span class="sxs-lookup"><span data-stu-id="10310-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="10310-164">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-164">Required.</span></span> <span data-ttu-id="10310-165">Объектная переменная, объявленная с типом данных класса или структуры, которая вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="10310-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="10310-166">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-166">Required.</span></span> <span data-ttu-id="10310-167">Имя события, обрабатываемого этой процедурой.</span><span class="sxs-lookup"><span data-stu-id="10310-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="10310-168">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="10310-168">Optional.</span></span> <span data-ttu-id="10310-169">Блок инструкций для выполнения в рамках этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-169">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="10310-170">Завершает определение этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="10310-171">Remarks</span><span class="sxs-lookup"><span data-stu-id="10310-171">Remarks</span></span>

<span data-ttu-id="10310-172">Весь исполняемый код должен находиться внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="10310-173">Каждая процедура, в свою очередь, объявляется в классе, структуре или модуле, который называется содержащим классом, структурой или модулем.</span><span class="sxs-lookup"><span data-stu-id="10310-173">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="10310-174">Чтобы вернуть значение в вызывающий код, используйте `Function` процедуру; в противном случае используйте `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="10310-174">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="10310-175">Определение функции</span><span class="sxs-lookup"><span data-stu-id="10310-175">Defining a Function</span></span>

<span data-ttu-id="10310-176">Процедуру можно определить `Function` только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="10310-176">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="10310-177">Таким образом, контекст объявления для функции должен быть классом, структурой, модулем или интерфейсом и не может быть исходным файлом, пространством имен, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="10310-177">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="10310-178">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="10310-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="10310-179">`Function` процедуры по умолчанию имеют открытый доступ.</span><span class="sxs-lookup"><span data-stu-id="10310-179">`Function` procedures default to public access.</span></span> <span data-ttu-id="10310-180">Уровни доступа можно изменить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="10310-180">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="10310-181">`Function`Процедура может объявлять тип данных возвращаемого процедурой значения.</span><span class="sxs-lookup"><span data-stu-id="10310-181">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="10310-182">Можно указать любой тип данных или имя перечисления, структуру, класс или интерфейс.</span><span class="sxs-lookup"><span data-stu-id="10310-182">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="10310-183">Если параметр не указан `returntype` , процедура возвращает `Object` .</span><span class="sxs-lookup"><span data-stu-id="10310-183">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="10310-184">Если в этой процедуре используется `Implements` ключевое слово, содержащий класс или структуру также должны иметь `Implements` оператор, который сразу следует `Class` за `Structure` оператором или.</span><span class="sxs-lookup"><span data-stu-id="10310-184">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="10310-185">`Implements`Инструкция должна включать каждый интерфейс, указанный в `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="10310-185">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="10310-186">Однако имя, по которому интерфейс определяет `Function` (в `definedname` ), не обязательно должно совпадать с именем этой процедуры (в `name` ).</span><span class="sxs-lookup"><span data-stu-id="10310-186">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="10310-187">Лямбда-выражения можно использовать для определения выражений функций встроенным.</span><span class="sxs-lookup"><span data-stu-id="10310-187">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="10310-188">Дополнительные сведения см. в разделе [выражение функции](../operators/function-expression.md) и [лямбда-выражения](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="10310-188">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="10310-189">Возврат из функции</span><span class="sxs-lookup"><span data-stu-id="10310-189">Returning from a Function</span></span>

<span data-ttu-id="10310-190">Когда `Function` процедура возвращается в вызывающий код, выполнение переходит к инструкции, следующей за инструкцией, вызвавшей процедуру.</span><span class="sxs-lookup"><span data-stu-id="10310-190">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="10310-191">Чтобы вернуть значение из функции, можно либо присвоить значение имени функции, либо включить его в `Return` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="10310-191">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="10310-192">`Return`Оператор одновременно назначает возвращаемое значение и завершает функцию, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="10310-192">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="10310-193">В следующем примере возвращаемое значение присваивается имени функции `myFunction` , а затем используется `Exit Function` оператор для возврата.</span><span class="sxs-lookup"><span data-stu-id="10310-193">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="10310-194">`Exit Function`Операторы и `Return` вызывают немедленный выход из `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-194">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="10310-195">Любое количество `Exit Function` инструкций и `Return` может использоваться в любом месте процедуры, и можно смешивать `Exit Function` `Return` операторы и.</span><span class="sxs-lookup"><span data-stu-id="10310-195">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="10310-196">Если вы используете `Exit Function` без присвоения значения `name` , процедура возвращает значение по умолчанию для типа данных, указанного в параметре `returntype` .</span><span class="sxs-lookup"><span data-stu-id="10310-196">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="10310-197">Если параметр `returntype` не указан, процедура возвращает `Nothing` значение, которое является значением по умолчанию для `Object` .</span><span class="sxs-lookup"><span data-stu-id="10310-197">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="10310-198">Вызов функции</span><span class="sxs-lookup"><span data-stu-id="10310-198">Calling a Function</span></span>

<span data-ttu-id="10310-199">Процедура вызывается с `Function` использованием имени процедуры, за которым следует список аргументов в выражении в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="10310-199">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="10310-200">Скобки можно опустить, только если вы не предоставляете никаких аргументов.</span><span class="sxs-lookup"><span data-stu-id="10310-200">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="10310-201">Однако код является более удобочитаемым, если всегда включать круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="10310-201">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="10310-202">Процедура вызывается `Function` так же, как и любая библиотечная функция, такая как `Sqrt` , `Cos` или `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="10310-202">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="10310-203">Функцию можно также вызвать с помощью `Call` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="10310-203">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="10310-204">В этом случае возвращаемое значение игнорируется.</span><span class="sxs-lookup"><span data-stu-id="10310-204">In that case, the return value is ignored.</span></span> <span data-ttu-id="10310-205">`Call`В большинстве случаев использование ключевого слова не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="10310-205">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="10310-206">Дополнительные сведения см. в разделе [оператор Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10310-206">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="10310-207">Visual Basic иногда переупорядочивает арифметические выражения для повышения внутренней эффективности.</span><span class="sxs-lookup"><span data-stu-id="10310-207">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="10310-208">По этой причине не следует использовать `Function` процедуру в арифметическом выражении, если функция изменяет значение переменных в том же выражении.</span><span class="sxs-lookup"><span data-stu-id="10310-208">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="10310-209">Асинхронные функции</span><span class="sxs-lookup"><span data-stu-id="10310-209">Async Functions</span></span>

<span data-ttu-id="10310-210">Функция *Async* позволяет вызывать асинхронные функции без использования явных обратных вызовов или вручную разделять код между несколькими функциями или лямбда-выражениями.</span><span class="sxs-lookup"><span data-stu-id="10310-210">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="10310-211">Если вы помечаете функцию модификатором [Async](../modifiers/async.md) , то можете использовать оператор [await](../operators/await-operator.md) в функции.</span><span class="sxs-lookup"><span data-stu-id="10310-211">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="10310-212">Когда управление достигает `Await` выражения в `Async` функции, управление возвращается вызывающему объекту, и ход выполнения функции приостанавливается до тех пор, пока не завершится ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="10310-212">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="10310-213">После завершения задачи выполнение может возобновиться в функции.</span><span class="sxs-lookup"><span data-stu-id="10310-213">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="10310-214">`Async`Процедура возвращается к вызывающему объекту, когда он встречает первый ожидающий объект, который еще не завершен, или на конец процедуры, в зависимости от того, что `Async` происходит раньше.</span><span class="sxs-lookup"><span data-stu-id="10310-214">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="10310-215">`Async`Функция может иметь тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> или <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="10310-215">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="10310-216">Ниже приведен пример `Async` функции, имеющей тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="10310-216">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="10310-217">`Async`Функция не может объявлять никакие параметры [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="10310-217">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="10310-218">[Оператор](sub-statement.md) подвыражения также может быть помечен `Async` модификатором.</span><span class="sxs-lookup"><span data-stu-id="10310-218">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="10310-219">Это в основном используется для обработчиков событий, где значение не может быть возвращено.</span><span class="sxs-lookup"><span data-stu-id="10310-219">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="10310-220">`Async` `Sub` Процедуру нельзя ожидать, и вызывающая `Async` `Sub` процедура не может перехватывать исключения, создаваемые `Sub` процедурой.</span><span class="sxs-lookup"><span data-stu-id="10310-220">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="10310-221">Дополнительные сведения о `Async` функциях см. в разделе [Асинхронное программирование с использованием Async и await](../../programming-guide/concepts/async/index.md), [поток управления в асинхронных программах](../../programming-guide/concepts/async/control-flow-in-async-programs.md)и [асинхронные типы возвращаемых](../../programming-guide/concepts/async/async-return-types.md)данных.</span><span class="sxs-lookup"><span data-stu-id="10310-221">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="10310-222">Функции итератора</span><span class="sxs-lookup"><span data-stu-id="10310-222">Iterator Functions</span></span>

<span data-ttu-id="10310-223">Функция *итератора* выполняет настраиваемую итерацию для коллекции, например списка или массива.</span><span class="sxs-lookup"><span data-stu-id="10310-223">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="10310-224">Функция итератора использует оператор [yield](yield-statement.md) для возвращения каждого элемента по одному за раз.</span><span class="sxs-lookup"><span data-stu-id="10310-224">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="10310-225">При достижении оператора [yield](yield-statement.md) текущее расположение в коде запоминается.</span><span class="sxs-lookup"><span data-stu-id="10310-225">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="10310-226">При следующем вызове функции итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="10310-226">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="10310-227">Итератор вызывается из клиентского кода с помощью метода [For Each... Следующий](for-each-next-statement.md) оператор.</span><span class="sxs-lookup"><span data-stu-id="10310-227">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="10310-228">Тип возвращаемого значения функции итератора может быть <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="10310-228">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="10310-229">Дополнительные сведения см. в разделе [Итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="10310-229">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="10310-230">Пример</span><span class="sxs-lookup"><span data-stu-id="10310-230">Example</span></span>

<span data-ttu-id="10310-231">В следующем примере оператор используется `Function` для объявления имени, параметров и кода, образующих тело `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-231">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="10310-232">`ParamArray`Модификатор позволяет функции принимать переменное число аргументов.</span><span class="sxs-lookup"><span data-stu-id="10310-232">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="10310-233">Пример</span><span class="sxs-lookup"><span data-stu-id="10310-233">Example</span></span>

<span data-ttu-id="10310-234">В следующем примере вызывается функция, объявленная в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="10310-234">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="10310-235">Пример</span><span class="sxs-lookup"><span data-stu-id="10310-235">Example</span></span>

<span data-ttu-id="10310-236">В следующем примере `DelayAsync` — это, `Async` `Function` имеющий тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="10310-236">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="10310-237">`DelayAsync` имеет инструкцию `Return` , которая возвращает целое число.</span><span class="sxs-lookup"><span data-stu-id="10310-237">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="10310-238">Поэтому объявление функции `DelayAsync` должно иметь тип возвращаемого значения `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="10310-238">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="10310-239">Так как тип возвращаемого значения — `Task(Of Integer)` , вычисление `Await` выражения в `DoSomethingAsync` создает целое число.</span><span class="sxs-lookup"><span data-stu-id="10310-239">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="10310-240">Это продемонстрировано в этой инструкции: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="10310-240">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="10310-241">`startButton_Click`Процедура является примером `Async Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="10310-241">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="10310-242">Поскольку `DoSomethingAsync` является `Async` функцией, задача для вызова `DoSomethingAsync` должна быть ожидаемой, как показано в следующей инструкции: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="10310-242">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="10310-243">`startButton_Click` `Sub` Процедура должна быть определена с `Async` модификатором, так как содержит `Await` выражение.</span><span class="sxs-lookup"><span data-stu-id="10310-243">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="10310-244">См. также</span><span class="sxs-lookup"><span data-stu-id="10310-244">See also</span></span>

- [<span data-ttu-id="10310-245">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="10310-245">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="10310-246">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="10310-246">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="10310-247">Список параметров</span><span class="sxs-lookup"><span data-stu-id="10310-247">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="10310-248">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="10310-248">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="10310-249">Оператор Call</span><span class="sxs-lookup"><span data-stu-id="10310-249">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="10310-250">Окна</span><span class="sxs-lookup"><span data-stu-id="10310-250">Of</span></span>](of-clause.md)
- [<span data-ttu-id="10310-251">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="10310-251">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="10310-252">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="10310-252">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="10310-253">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="10310-253">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="10310-254">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="10310-254">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="10310-255">Выражение function</span><span class="sxs-lookup"><span data-stu-id="10310-255">Function Expression</span></span>](../operators/function-expression.md)
