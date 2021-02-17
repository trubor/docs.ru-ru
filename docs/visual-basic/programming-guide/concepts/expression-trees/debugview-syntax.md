---
title: Синтаксис, используемый свойством DebugView
description: В этой статье описывается специальный синтаксис, используемый свойством DebugView для получения строкового представления деревьев выражений.
author: zspitz
ms.author: wiwagn
ms.date: 14/02/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 8a4feac72c2cd79485f5733b16d65b52cc50ee6c
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584888"
---
# <a name="debugview-syntax"></a><span data-ttu-id="57fd4-103">Синтаксис **DebugView**</span><span class="sxs-lookup"><span data-stu-id="57fd4-103">**DebugView** syntax</span></span>

<span data-ttu-id="57fd4-104">Свойство **DebugView** (доступно только при отладке) обеспечивает отрисовку строк деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="57fd4-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="57fd4-105">Большая часть синтаксиса достаточно проста для понимания; особые случаи описаны в разделах ниже.</span><span class="sxs-lookup"><span data-stu-id="57fd4-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="57fd4-106">За каждым примером следует блок комментариев, содержащий **DebugView**.</span><span class="sxs-lookup"><span data-stu-id="57fd4-106">Each example is followed by a comment block containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="57fd4-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="57fd4-107">ParameterExpression</span></span>

<span data-ttu-id="57fd4-108">В начале имен переменных <xref:System.Linq.Expressions.ParameterExpression> отображается символ "$".</span><span class="sxs-lookup"><span data-stu-id="57fd4-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="57fd4-109">Если параметр не имеет имени, оно назначается автоматически, например `$var1` или `$var2`.</span><span class="sxs-lookup"><span data-stu-id="57fd4-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="57fd4-110">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="57fd4-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="57fd4-111">ConstantExpressions</span></span>

<span data-ttu-id="57fd4-112">Для объектов <xref:System.Linq.Expressions.ConstantExpression>, представляющих целочисленные значения, строки и `null`, отображается значение константы.</span><span class="sxs-lookup"><span data-stu-id="57fd4-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="57fd4-113">Для некоторых числовых типов суффикс добавляется к значению:</span><span class="sxs-lookup"><span data-stu-id="57fd4-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="57fd4-114">Type</span><span class="sxs-lookup"><span data-stu-id="57fd4-114">Type</span></span> | <span data-ttu-id="57fd4-115">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="57fd4-115">Keyword</span></span> | <span data-ttu-id="57fd4-116">Суффикс</span><span class="sxs-lookup"><span data-stu-id="57fd4-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="57fd4-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="57fd4-118">U</span><span class="sxs-lookup"><span data-stu-id="57fd4-118">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-119">Long</span><span class="sxs-lookup"><span data-stu-id="57fd4-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="57fd4-120">L</span><span class="sxs-lookup"><span data-stu-id="57fd4-120">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-121">ULong</span><span class="sxs-lookup"><span data-stu-id="57fd4-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="57fd4-122">UL</span><span class="sxs-lookup"><span data-stu-id="57fd4-122">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-123">Double</span><span class="sxs-lookup"><span data-stu-id="57fd4-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="57fd4-124">D</span><span class="sxs-lookup"><span data-stu-id="57fd4-124">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-125">Single</span><span class="sxs-lookup"><span data-stu-id="57fd4-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="57fd4-126">F</span><span class="sxs-lookup"><span data-stu-id="57fd4-126">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="57fd4-127">Десятичное число</span><span class="sxs-lookup"><span data-stu-id="57fd4-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="57fd4-128">M</span><span class="sxs-lookup"><span data-stu-id="57fd4-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="57fd4-129">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="57fd4-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="57fd4-130">BlockExpression</span></span>

<span data-ttu-id="57fd4-131">Если тип объекта <xref:System.Linq.Expressions.BlockExpression> отличается от типа последнего выражения в блоке, то тип отображается в угловых скобках (`<` и `>`).</span><span class="sxs-lookup"><span data-stu-id="57fd4-131">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="57fd4-132">В противном случае тип объекта <xref:System.Linq.Expressions.BlockExpression> не отображается.</span><span class="sxs-lookup"><span data-stu-id="57fd4-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="57fd4-133">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="57fd4-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="57fd4-134">LambdaExpression</span></span>

<span data-ttu-id="57fd4-135">Объекты <xref:System.Linq.Expressions.LambdaExpression> отображаются вместе со своими типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="57fd4-135"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="57fd4-136">Если лямбда-выражение не имеет имени, оно назначается автоматически, например `#Lambda1` или `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="57fd4-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="57fd4-137">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="57fd4-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="57fd4-138">LabelExpression</span></span>

<span data-ttu-id="57fd4-139">Если указать значение по умолчанию для объекта <xref:System.Linq.Expressions.LabelExpression>, оно будет отображаться перед объектом <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="57fd4-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="57fd4-140">Маркер `.Label` указывает начало метки.</span><span class="sxs-lookup"><span data-stu-id="57fd4-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="57fd4-141">Маркер `.LabelTarget` задает конечную цель перехода для целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="57fd4-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="57fd4-142">Если метка не имеет имени, оно назначается автоматически, например `#Label1` или `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="57fd4-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="57fd4-143">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="57fd4-144">Проверяемые операторы</span><span class="sxs-lookup"><span data-stu-id="57fd4-144">Checked Operators</span></span>

<span data-ttu-id="57fd4-145">Проверяемые операторы отображаются с символом `#` перед оператором.</span><span class="sxs-lookup"><span data-stu-id="57fd4-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="57fd4-146">Например, проверяемый оператор сложения отображается как `#+`.</span><span class="sxs-lookup"><span data-stu-id="57fd4-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="57fd4-147">Примеры</span><span class="sxs-lookup"><span data-stu-id="57fd4-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
