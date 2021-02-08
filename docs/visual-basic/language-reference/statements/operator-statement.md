---
description: 'Дополнительные сведения: оператор operator'
title: Operator Statement
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: f6a8ae2ac51e8bc8fe1be0de3549004b9dda4ef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768822"
---
# <a name="operator-statement"></a><span data-ttu-id="1142f-103">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="1142f-103">Operator Statement</span></span>

<span data-ttu-id="1142f-104">Объявляет символ оператора, операнды и код, определяющие процедуру оператора для класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="1142f-104">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="1142f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1142f-105">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="1142f-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="1142f-106">Parts</span></span>

`attrlist`  
<span data-ttu-id="1142f-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-107">Optional.</span></span> <span data-ttu-id="1142f-108">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-108">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="1142f-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-109">Required.</span></span> <span data-ttu-id="1142f-110">Указывает, что эта процедура оператора имеет [открытый](../modifiers/public.md) доступ.</span><span class="sxs-lookup"><span data-stu-id="1142f-110">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="1142f-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-111">Optional.</span></span> <span data-ttu-id="1142f-112">См. раздел [Overloads](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-112">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="1142f-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-113">Required.</span></span> <span data-ttu-id="1142f-114">Указывает, что эта процедура оператора является [общей](../modifiers/shared.md) процедурой.</span><span class="sxs-lookup"><span data-stu-id="1142f-114">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="1142f-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-115">Optional.</span></span> <span data-ttu-id="1142f-116">См. раздел [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-116">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="1142f-117">Требуется для оператора преобразования, если не указано значение `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="1142f-117">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="1142f-118">Указывает, что эта процедура оператора определяет [расширяющее](../modifiers/widening.md) преобразование.</span><span class="sxs-lookup"><span data-stu-id="1142f-118">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="1142f-119">См. раздел "расширяющие и сужающие преобразования" на этой странице справки.</span><span class="sxs-lookup"><span data-stu-id="1142f-119">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="1142f-120">Требуется для оператора преобразования, если не указано значение `Widening` .</span><span class="sxs-lookup"><span data-stu-id="1142f-120">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="1142f-121">Указывает, что эта процедура оператора определяет [понижающие](../modifiers/narrowing.md) преобразования.</span><span class="sxs-lookup"><span data-stu-id="1142f-121">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="1142f-122">См. раздел "расширяющие и сужающие преобразования" на этой странице справки.</span><span class="sxs-lookup"><span data-stu-id="1142f-122">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="1142f-123">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-123">Required.</span></span> <span data-ttu-id="1142f-124">Символ или идентификатор оператора, определяемого данной процедурой оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-124">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="1142f-125">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-125">Required.</span></span> <span data-ttu-id="1142f-126">Имя и тип одного операнда унарного оператора (включая оператор преобразования) или левого операнда бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-126">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="1142f-127">Требуется для бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="1142f-127">Required for binary operators.</span></span> <span data-ttu-id="1142f-128">Имя и тип правого операнда бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-128">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="1142f-129">`operand1` и `operand2` имеют следующий синтаксис и части:</span><span class="sxs-lookup"><span data-stu-id="1142f-129">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="1142f-130">Отделение</span><span class="sxs-lookup"><span data-stu-id="1142f-130">Part</span></span>|<span data-ttu-id="1142f-131">Описание</span><span class="sxs-lookup"><span data-stu-id="1142f-131">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="1142f-132">Необязательно, но механизм передачи должен быть [ByVal](../modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-132">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="1142f-133">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-133">Required.</span></span> <span data-ttu-id="1142f-134">Имя переменной, представляющей этот операнд.</span><span class="sxs-lookup"><span data-stu-id="1142f-134">Name of the variable representing this operand.</span></span> <span data-ttu-id="1142f-135">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="1142f-136">Необязательный `Option Strict` , если не имеет `On` .</span><span class="sxs-lookup"><span data-stu-id="1142f-136">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="1142f-137">Тип данных этого операнда.</span><span class="sxs-lookup"><span data-stu-id="1142f-137">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="1142f-138">Необязательный `Option Strict` , если не имеет `On` .</span><span class="sxs-lookup"><span data-stu-id="1142f-138">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="1142f-139">Тип данных значения, возвращаемого процедурой оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-139">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="1142f-140">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-140">Optional.</span></span> <span data-ttu-id="1142f-141">Блок инструкций, выполняемых процедурой оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-141">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="1142f-142">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-142">Required.</span></span> <span data-ttu-id="1142f-143">Значение, возвращаемое процедурой оператора в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="1142f-143">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="1142f-144">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="1142f-144">`End` `Operator`</span></span>  
<span data-ttu-id="1142f-145">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1142f-145">Required.</span></span> <span data-ttu-id="1142f-146">Завершает определение этой процедуры оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-146">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="1142f-147">Remarks</span><span class="sxs-lookup"><span data-stu-id="1142f-147">Remarks</span></span>

<span data-ttu-id="1142f-148">Можно использовать `Operator` только в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="1142f-148">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="1142f-149">Это означает, что *контекст объявления* для оператора не может быть исходным файлом, пространством имен, модулем, интерфейсом, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="1142f-149">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="1142f-150">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-150">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="1142f-151">Все операторы должны быть `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="1142f-151">All operators must be `Public Shared`.</span></span> <span data-ttu-id="1142f-152">Нельзя указывать `ByRef` , `Optional` или `ParamArray` для любого из операндов.</span><span class="sxs-lookup"><span data-stu-id="1142f-152">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="1142f-153">Нельзя использовать символ оператора или идентификатор для хранения возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="1142f-153">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="1142f-154">Необходимо использовать `Return` инструкцию, и она должна указывать значение.</span><span class="sxs-lookup"><span data-stu-id="1142f-154">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="1142f-155">Любое количество `Return` инструкций может находиться в любом месте процедуры.</span><span class="sxs-lookup"><span data-stu-id="1142f-155">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="1142f-156">Определение оператора таким образом называется *перегрузкой операторов* независимо от того, используется `Overloads` ключевое слово или нет.</span><span class="sxs-lookup"><span data-stu-id="1142f-156">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="1142f-157">В приведенной ниже таблице перечислены операторы, которые можно определить.</span><span class="sxs-lookup"><span data-stu-id="1142f-157">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="1142f-158">Тип</span><span class="sxs-lookup"><span data-stu-id="1142f-158">Type</span></span>|<span data-ttu-id="1142f-159">Операторы</span><span class="sxs-lookup"><span data-stu-id="1142f-159">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="1142f-160">Унарный</span><span class="sxs-lookup"><span data-stu-id="1142f-160">Unary</span></span>|<span data-ttu-id="1142f-161">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="1142f-161">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="1142f-162">Двоичные данные</span><span class="sxs-lookup"><span data-stu-id="1142f-162">Binary</span></span>|<span data-ttu-id="1142f-163">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="1142f-163">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="1142f-164">Преобразование (унарный)</span><span class="sxs-lookup"><span data-stu-id="1142f-164">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="1142f-165">Обратите внимание, что `=` оператор в списке binary является оператором сравнения, а не оператором присваивания.</span><span class="sxs-lookup"><span data-stu-id="1142f-165">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="1142f-166">При определении необходимо `CType` указать либо `Widening` `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="1142f-166">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="1142f-167">Парные пары</span><span class="sxs-lookup"><span data-stu-id="1142f-167">Matched Pairs</span></span>

<span data-ttu-id="1142f-168">Необходимо определить определенные операторы в качестве совпадающих пар.</span><span class="sxs-lookup"><span data-stu-id="1142f-168">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="1142f-169">При определении любого из этих двух операторов такой пары необходимо определить и другое.</span><span class="sxs-lookup"><span data-stu-id="1142f-169">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="1142f-170">Сопоставленные пары являются следующими:</span><span class="sxs-lookup"><span data-stu-id="1142f-170">The matched pairs are the following:</span></span>

- <span data-ttu-id="1142f-171">`=` и `<>`</span><span class="sxs-lookup"><span data-stu-id="1142f-171">`=` and `<>`</span></span>

- <span data-ttu-id="1142f-172">`>` и `<`</span><span class="sxs-lookup"><span data-stu-id="1142f-172">`>` and `<`</span></span>

- <span data-ttu-id="1142f-173">`>=` и `<=`</span><span class="sxs-lookup"><span data-stu-id="1142f-173">`>=` and `<=`</span></span>

- <span data-ttu-id="1142f-174">`IsTrue` и `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="1142f-174">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="1142f-175">Ограничения типов данных</span><span class="sxs-lookup"><span data-stu-id="1142f-175">Data Type Restrictions</span></span>

<span data-ttu-id="1142f-176">Каждый определяемый оператор должен содержать класс или структуру, в которых он определен.</span><span class="sxs-lookup"><span data-stu-id="1142f-176">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="1142f-177">Это означает, что класс или структура должны выглядеть как тип данных следующего:</span><span class="sxs-lookup"><span data-stu-id="1142f-177">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="1142f-178">Операнд унарного оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-178">The operand of a unary operator.</span></span>

- <span data-ttu-id="1142f-179">По крайней мере один из операндов бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-179">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="1142f-180">Либо операнд, либо тип возвращаемого значения оператора преобразования.</span><span class="sxs-lookup"><span data-stu-id="1142f-180">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="1142f-181">Некоторые операторы имеют дополнительные ограничения по типам данных, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="1142f-181">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="1142f-182">При определении `IsTrue` `IsFalse` операторов and они должны возвращать `Boolean` тип.</span><span class="sxs-lookup"><span data-stu-id="1142f-182">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="1142f-183">При определении `<<` `>>` операторов and они должны указывать `Integer` тип для `operandtype` `operand2` .</span><span class="sxs-lookup"><span data-stu-id="1142f-183">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="1142f-184">Тип возвращаемого значения не должен соответствовать типу любого из операндов.</span><span class="sxs-lookup"><span data-stu-id="1142f-184">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="1142f-185">Например, оператор сравнения, например или, `=` `<>` может возвращать значение, `Boolean` даже если ни один из операндов не равен `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1142f-185">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="1142f-186">Логические и побитовые операторы</span><span class="sxs-lookup"><span data-stu-id="1142f-186">Logical and Bitwise Operators</span></span>

<span data-ttu-id="1142f-187">`And`Операторы, `Or` , `Not` и `Xor` могут выполнять логические или побитовые операции в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1142f-187">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="1142f-188">Однако при определении одного из этих операторов для класса или структуры можно определить только его побитовую операцию.</span><span class="sxs-lookup"><span data-stu-id="1142f-188">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="1142f-189">Оператор нельзя определить `AndAlso` непосредственно с помощью `Operator` оператора.</span><span class="sxs-lookup"><span data-stu-id="1142f-189">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="1142f-190">Тем не менее, можно использовать, `AndAlso` если выполнены следующие условия.</span><span class="sxs-lookup"><span data-stu-id="1142f-190">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="1142f-191">Вы определили `And` те же типы операндов, которые вы хотите использовать для `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="1142f-191">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="1142f-192">Определение `And` возвращает тот же тип, что и класс или структура, в которой он определен.</span><span class="sxs-lookup"><span data-stu-id="1142f-192">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="1142f-193">Вы определили `IsFalse` оператор для класса или структуры, в которой вы определили `And` .</span><span class="sxs-lookup"><span data-stu-id="1142f-193">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="1142f-194">Аналогичным образом можно использовать, `OrElse` Если вы определили в `Or` одних и тех же операндах с типом возвращаемого значения класса или структуры и определили `IsTrue` в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="1142f-194">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="1142f-195">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="1142f-195">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="1142f-196">*Расширяющее преобразование* всегда выполняется успешно во время выполнения, в то время как *понижающие преобразования* могут завершиться ошибкой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1142f-196">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="1142f-197">Для получения дополнительной информации см. [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1142f-197">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="1142f-198">Если объявляется процедура преобразования `Widening` , код процедуры не должен создавать ошибок.</span><span class="sxs-lookup"><span data-stu-id="1142f-198">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="1142f-199">Это означает следующее:</span><span class="sxs-lookup"><span data-stu-id="1142f-199">This means the following:</span></span>

- <span data-ttu-id="1142f-200">Он должен всегда возвращать допустимое значение типа `type` .</span><span class="sxs-lookup"><span data-stu-id="1142f-200">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="1142f-201">Он должен поддерживать все возможные исключения и другие условия возникновения ошибок.</span><span class="sxs-lookup"><span data-stu-id="1142f-201">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="1142f-202">Она должна поддерживать любые ошибки, возвращаемые из всех процедур, которые она вызывает.</span><span class="sxs-lookup"><span data-stu-id="1142f-202">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="1142f-203">Если существует вероятность того, что процедура преобразования может быть невозможной или она может вызвать необработанное исключение, необходимо объявить ее как `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="1142f-203">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="1142f-204">Пример</span><span class="sxs-lookup"><span data-stu-id="1142f-204">Example</span></span>

<span data-ttu-id="1142f-205">В следующем примере кода инструкция используется `Operator` для определения структуры структуры, которая включает в себя процедуры операторов для `And` операторов,, `Or` `IsFalse` и `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="1142f-205">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="1142f-206">`And` и `Or` каждый из них принимает два операнда типа `abc` и типа возвращаемого значения `abc` .</span><span class="sxs-lookup"><span data-stu-id="1142f-206">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="1142f-207">`IsFalse``IsTrue`каждый из них принимает один операнд типа `abc` и возвращает значение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1142f-207">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="1142f-208">Эти определения позволяют вызывающему коду использовать `And` , `AndAlso` , `Or` и `OrElse` с операндами типа `abc` .</span><span class="sxs-lookup"><span data-stu-id="1142f-208">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="1142f-209">См. также</span><span class="sxs-lookup"><span data-stu-id="1142f-209">See also</span></span>

- [<span data-ttu-id="1142f-210">Оператор IsFalse</span><span class="sxs-lookup"><span data-stu-id="1142f-210">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="1142f-211">Оператор IsTrue</span><span class="sxs-lookup"><span data-stu-id="1142f-211">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="1142f-212">Widening</span><span class="sxs-lookup"><span data-stu-id="1142f-212">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="1142f-213">Narrowing</span><span class="sxs-lookup"><span data-stu-id="1142f-213">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="1142f-214">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="1142f-214">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="1142f-215">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="1142f-215">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="1142f-216">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="1142f-216">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="1142f-217">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="1142f-217">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1142f-218">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="1142f-218">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="1142f-219">Практическое руководство. Использование класса, в котором определяются операторы</span><span class="sxs-lookup"><span data-stu-id="1142f-219">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
