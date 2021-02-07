---
description: 'Дополнительные сведения: оператор Const (Visual Basic)'
title: Оператор Const
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 61d898823c7697c91b207a502417b49cdeaf5eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673860"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="60aa6-103">Оператор Const (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60aa6-103">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="60aa6-104">Объявляет и определяет одну или несколько констант.</span><span class="sxs-lookup"><span data-stu-id="60aa6-104">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="60aa6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60aa6-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="60aa6-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="60aa6-106">Parts</span></span>

`attributelist`  
<span data-ttu-id="60aa6-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-107">Optional.</span></span> <span data-ttu-id="60aa6-108">Список атрибутов, которые применяются ко всем константам, объявленным в этой инструкции.</span><span class="sxs-lookup"><span data-stu-id="60aa6-108">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="60aa6-109">См. [список атрибутов](attribute-list.md) в угловых скобках (" `<` " и " `>` ").</span><span class="sxs-lookup"><span data-stu-id="60aa6-109">See [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="60aa6-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-110">Optional.</span></span> <span data-ttu-id="60aa6-111">Используйте его, чтобы указать, какой код может получить доступ к этим константам.</span><span class="sxs-lookup"><span data-stu-id="60aa6-111">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="60aa6-112">Может быть [общедоступным](../modifiers/public.md), [защищенным](../modifiers/protected.md), [дружественным](../modifiers/friend.md), [защищенным дружественным](../modifiers/protected-friend.md), [частным](../modifiers/private.md)или [частным](../modifiers/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="60aa6-112">Can be [Public](../modifiers/public.md), [Protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md), or [Private Protected](../modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="60aa6-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-113">Optional.</span></span> <span data-ttu-id="60aa6-114">Используйте его для повторного объявления и скрытия программного элемента в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="60aa6-114">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="60aa6-115">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="60aa6-115">See [Shadows](../modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="60aa6-116">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-116">Required.</span></span> <span data-ttu-id="60aa6-117">Список констант, объявляемых в этой инструкции.</span><span class="sxs-lookup"><span data-stu-id="60aa6-117">List of constants being declared in this statement.</span></span>

<span data-ttu-id="60aa6-118">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="60aa6-118">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="60aa6-119">Каждый элемент `constant` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="60aa6-119">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="60aa6-120">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="60aa6-120">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="60aa6-121">Отделение</span><span class="sxs-lookup"><span data-stu-id="60aa6-121">Part</span></span>|<span data-ttu-id="60aa6-122">Описание</span><span class="sxs-lookup"><span data-stu-id="60aa6-122">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="60aa6-123">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-123">Required.</span></span> <span data-ttu-id="60aa6-124">Имя константы.</span><span class="sxs-lookup"><span data-stu-id="60aa6-124">Name of the constant.</span></span> <span data-ttu-id="60aa6-125">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="60aa6-125">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="60aa6-126">Обязательный `Option Strict` , если имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-126">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="60aa6-127">Тип данных константы.</span><span class="sxs-lookup"><span data-stu-id="60aa6-127">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="60aa6-128">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="60aa6-128">Required.</span></span> <span data-ttu-id="60aa6-129">Выражение, которое вычисляется во время компиляции и присваивается константе.</span><span class="sxs-lookup"><span data-stu-id="60aa6-129">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="60aa6-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="60aa6-130">Remarks</span></span>

<span data-ttu-id="60aa6-131">Если у вас есть значение, которое никогда не изменяется в приложении, можно определить именованную константу и использовать ее вместо литерального значения.</span><span class="sxs-lookup"><span data-stu-id="60aa6-131">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="60aa6-132">Имя проще запомнить, чем значение.</span><span class="sxs-lookup"><span data-stu-id="60aa6-132">A name is easier to remember than a value.</span></span> <span data-ttu-id="60aa6-133">Вы можете определить константу только один раз и использовать ее во многих местах кода.</span><span class="sxs-lookup"><span data-stu-id="60aa6-133">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="60aa6-134">Если в более поздней версии необходимо переопределить значение, то единственным местом, которое необходимо `Const` внести в изменение, является только инструкция.</span><span class="sxs-lookup"><span data-stu-id="60aa6-134">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="60aa6-135">Можно использовать `Const` только на уровне модуля или процедуры.</span><span class="sxs-lookup"><span data-stu-id="60aa6-135">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="60aa6-136">Это означает, что *контекст объявления* для переменной должен быть классом, структурой, модулем, процедурой или блоком и не может быть исходным файлом, пространством имен или интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="60aa6-136">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="60aa6-137">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="60aa6-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="60aa6-138">Локальные константы (внутри процедуры) по умолчанию имеют открытый доступ, и в них нельзя использовать какие-либо модификаторы доступа.</span><span class="sxs-lookup"><span data-stu-id="60aa6-138">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="60aa6-139">Константы класса и члена модуля (вне любой процедуры) по умолчанию имеют частный доступ, а константы членов структуры по умолчанию имеют открытый доступ.</span><span class="sxs-lookup"><span data-stu-id="60aa6-139">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="60aa6-140">Уровни доступа можно изменить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="60aa6-140">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="60aa6-141">Правила</span><span class="sxs-lookup"><span data-stu-id="60aa6-141">Rules</span></span>

- <span data-ttu-id="60aa6-142">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-142">**Declaration Context.**</span></span> <span data-ttu-id="60aa6-143">Константа, объявленная на уровне модуля вне любой процедуры, является *константой-членом*; Он является членом класса, структуры или модуля, объявляющего его.</span><span class="sxs-lookup"><span data-stu-id="60aa6-143">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="60aa6-144">Константа, объявленная на уровне процедуры, является *локальной константой*; Он является локальным для процедуры или блока, объявляющего ее.</span><span class="sxs-lookup"><span data-stu-id="60aa6-144">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="60aa6-145">**Атрибута.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-145">**Attributes.**</span></span> <span data-ttu-id="60aa6-146">Атрибуты можно применять только к константам членов, а не к локальным константам.</span><span class="sxs-lookup"><span data-stu-id="60aa6-146">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="60aa6-147">Атрибут вносит сведения в метаданные сборки, что не имеет смысла для временного хранения, например локальных констант.</span><span class="sxs-lookup"><span data-stu-id="60aa6-147">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="60aa6-148">**Модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-148">**Modifiers.**</span></span> <span data-ttu-id="60aa6-149">По умолчанию все константы имеют значение `Shared` , `Static` и `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-149">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="60aa6-150">При объявлении константы нельзя использовать какие-либо из этих ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="60aa6-150">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="60aa6-151">На уровне процедуры нельзя использовать `Shadows` модификаторы доступа или для объявления локальных констант.</span><span class="sxs-lookup"><span data-stu-id="60aa6-151">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="60aa6-152">**Несколько констант.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-152">**Multiple Constants.**</span></span> <span data-ttu-id="60aa6-153">Можно объявить несколько констант в одном операторе объявления, указав `constantname` часть для каждого из них.</span><span class="sxs-lookup"><span data-stu-id="60aa6-153">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="60aa6-154">Несколько констант разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="60aa6-154">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="60aa6-155">Правила типов данных</span><span class="sxs-lookup"><span data-stu-id="60aa6-155">Data Type Rules</span></span>

- <span data-ttu-id="60aa6-156">**Типы данных.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-156">**Data Types.**</span></span> <span data-ttu-id="60aa6-157">`Const`Оператор может объявлять тип данных переменной.</span><span class="sxs-lookup"><span data-stu-id="60aa6-157">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="60aa6-158">Можно указать любой тип данных или имя перечисления.</span><span class="sxs-lookup"><span data-stu-id="60aa6-158">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="60aa6-159">**Тип по умолчанию.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-159">**Default Type.**</span></span> <span data-ttu-id="60aa6-160">Если не указать `datatype` , константа принимает тип данных `initializer` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-160">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="60aa6-161">Если заданы оба параметра `datatype` и `initializer` , тип данных `initializer` должен быть преобразован в `datatype` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-161">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="60aa6-162">Если оба `datatype` `initializer` параметра и не указаны, по умолчанию используется тип данных `Object` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-162">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="60aa6-163">**Различные типы.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-163">**Different Types.**</span></span> <span data-ttu-id="60aa6-164">Можно указать различные типы данных для разных констант, используя отдельное `As` предложение для каждой объявляемой переменной.</span><span class="sxs-lookup"><span data-stu-id="60aa6-164">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="60aa6-165">Однако нельзя объявить несколько констант, имеющих один и тот же тип, с помощью общего `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="60aa6-165">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="60aa6-166">**Инициализации.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-166">**Initialization.**</span></span> <span data-ttu-id="60aa6-167">Необходимо инициализировать значение каждой константы в `constantlist` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-167">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="60aa6-168">Используется `initializer` для предоставления выражения, присваиваемого константе.</span><span class="sxs-lookup"><span data-stu-id="60aa6-168">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="60aa6-169">Выражение может быть любым сочетанием литералов, других уже определенных констант и уже определенных элементов перечисления.</span><span class="sxs-lookup"><span data-stu-id="60aa6-169">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="60aa6-170">Для объединения таких элементов можно использовать арифметические и логические операторы.</span><span class="sxs-lookup"><span data-stu-id="60aa6-170">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="60aa6-171">В нельзя использовать переменные или функции `initializer` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-171">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="60aa6-172">Однако можно использовать ключевые слова преобразования, такие как `CByte` и `CShort` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-172">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="60aa6-173">Можно также использовать `AscW` , если вы вызываете его с константой `String` или `Char` аргументом, так как это может быть вычислено во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="60aa6-173">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="60aa6-174">Поведение</span><span class="sxs-lookup"><span data-stu-id="60aa6-174">Behavior</span></span>

- <span data-ttu-id="60aa6-175">**Которых.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-175">**Scope.**</span></span> <span data-ttu-id="60aa6-176">Локальные константы доступны только в пределах их процедуры или блока.</span><span class="sxs-lookup"><span data-stu-id="60aa6-176">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="60aa6-177">Константы членов доступны из любого места в своем классе, структуре или модуле.</span><span class="sxs-lookup"><span data-stu-id="60aa6-177">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="60aa6-178">**Квалификацию.**</span><span class="sxs-lookup"><span data-stu-id="60aa6-178">**Qualification.**</span></span> <span data-ttu-id="60aa6-179">Код за пределами класса, структуры или модуля должен уточнять имя константы-члена именем этого класса, структуры или модуля.</span><span class="sxs-lookup"><span data-stu-id="60aa6-179">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="60aa6-180">Код за пределами процедуры или блока не может ссылаться на любые локальные константы в этой процедуре или блоке.</span><span class="sxs-lookup"><span data-stu-id="60aa6-180">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="60aa6-181">Пример</span><span class="sxs-lookup"><span data-stu-id="60aa6-181">Example</span></span>

<span data-ttu-id="60aa6-182">В следующем примере оператор используется `Const` для объявления констант для использования вместо литеральных значений.</span><span class="sxs-lookup"><span data-stu-id="60aa6-182">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="60aa6-183">Пример</span><span class="sxs-lookup"><span data-stu-id="60aa6-183">Example</span></span>

<span data-ttu-id="60aa6-184">При определении константы с типом данных `Object` компилятор Visual Basic присваивает ему тип `initializer` , а не `Object` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-184">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="60aa6-185">В следующем примере константа `naturalLogBase` имеет тип времени выполнения `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-185">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="60aa6-186">В предыдущем примере метод используется <xref:System.Type.ToString%2A> для <xref:System.Type> объекта, возвращаемого [оператором GetType](../operators/gettype-operator.md), поскольку <xref:System.Type> не может быть преобразован в `String` using `CStr` .</span><span class="sxs-lookup"><span data-stu-id="60aa6-186">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="60aa6-187">См. также</span><span class="sxs-lookup"><span data-stu-id="60aa6-187">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="60aa6-188">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="60aa6-188">Enum Statement</span></span>](enum-statement.md)
- [<span data-ttu-id="60aa6-189">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="60aa6-189">#Const Directive</span></span>](../directives/const-directive.md)
- [<span data-ttu-id="60aa6-190">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="60aa6-190">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="60aa6-191">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="60aa6-191">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="60aa6-192">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="60aa6-192">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="60aa6-193">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="60aa6-193">Constants and Enumerations</span></span>](../../programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="60aa6-194">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="60aa6-194">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="60aa6-195">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="60aa6-195">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
