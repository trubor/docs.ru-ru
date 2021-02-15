---
description: 'Дополнительные сведения: типы значений, допускающие значение null (Visual Basic)'
title: Типы значений, допускающие значение NULL
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: acc91d98a3ed288a9bf0bcf6abbd3d8a516bd699
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483889"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="5d96b-103">Типы значения, допускающие Null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d96b-103">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="5d96b-104">Иногда вы работаете с типом значения, который не имеет определенного значения в определенных обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="5d96b-104">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="5d96b-105">Например, поле в базе данных может отличаться от присвоенного значения, которое является осмысленным и не имеет присвоенного значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-105">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="5d96b-106">Типы значений могут быть расширены для получения их нормальных значений или значения NULL.</span><span class="sxs-lookup"><span data-stu-id="5d96b-106">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="5d96b-107">Такое расширение называется *типом, допускающим значение NULL*.</span><span class="sxs-lookup"><span data-stu-id="5d96b-107">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="5d96b-108">Каждый тип значения, допускающий значение null, создается из универсальной <xref:System.Nullable%601> структуры.</span><span class="sxs-lookup"><span data-stu-id="5d96b-108">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="5d96b-109">Рассмотрим базу данных, которая отслеживает действия, связанные с работой.</span><span class="sxs-lookup"><span data-stu-id="5d96b-109">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="5d96b-110">В следующем примере создается тип, допускающий значение NULL `Boolean` , и объявляется переменная этого типа.</span><span class="sxs-lookup"><span data-stu-id="5d96b-110">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="5d96b-111">Объявление можно написать тремя способами:</span><span class="sxs-lookup"><span data-stu-id="5d96b-111">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="5d96b-112">Переменная `ridesBusToWork` может содержать значение `True` , значение `False` или вообще не иметь значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-112">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="5d96b-113">Его начальное значение по умолчанию — вообще не имеет значения, что в данном случае может означать, что данные еще не были получены для этого пользователя.</span><span class="sxs-lookup"><span data-stu-id="5d96b-113">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="5d96b-114">В отличие от этого, это `False` может означать, что информация получена и пользователь не передается на работу.</span><span class="sxs-lookup"><span data-stu-id="5d96b-114">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="5d96b-115">Можно объявить переменные и свойства с типами значений, допускающими значение null, и можно объявить массив с элементами типа значения, допускающего значение null.</span><span class="sxs-lookup"><span data-stu-id="5d96b-115">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="5d96b-116">Можно объявлять процедуры с типами значений, допускающими значение null, в качестве параметров, а также возвращать тип значения, допускающий значение null, из `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="5d96b-116">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="5d96b-117">Нельзя создать тип, допускающий значение null, для ссылочного типа, такого как массив, `String` или класс.</span><span class="sxs-lookup"><span data-stu-id="5d96b-117">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="5d96b-118">Базовый тип должен быть типом значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-118">The underlying type must be a value type.</span></span> <span data-ttu-id="5d96b-119">Дополнительные сведения см. в разделе [типы значений и ссылочные типы](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="5d96b-119">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="5d96b-120">Использование переменной типа, допускающей значение null</span><span class="sxs-lookup"><span data-stu-id="5d96b-120">Using a Nullable Type Variable</span></span>

<span data-ttu-id="5d96b-121">Наиболее важными членами типа, допускающего значение null, являются <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> Свойства и.</span><span class="sxs-lookup"><span data-stu-id="5d96b-121">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="5d96b-122">Для переменной типа значения, допускающего значение null, <xref:System.Nullable%601.HasValue%2A> сообщает, содержит ли переменная определенное значение.</span><span class="sxs-lookup"><span data-stu-id="5d96b-122">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="5d96b-123">Если <xref:System.Nullable%601.HasValue%2A> параметр имеет `True` значение, то можно считать значения из <xref:System.Nullable%601.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="5d96b-123">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="5d96b-124">Обратите внимание, что <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> Свойства и являются `ReadOnly` свойствами.</span><span class="sxs-lookup"><span data-stu-id="5d96b-124">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="5d96b-125">Значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="5d96b-125">Default Values</span></span>

<span data-ttu-id="5d96b-126">При объявлении переменной с типом значения, допускающим значение null, ее <xref:System.Nullable%601.HasValue%2A> свойство имеет значение по умолчанию `False` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-126">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="5d96b-127">Это означает, что по умолчанию переменная не имеет определенного значения, а не значения по умолчанию базового типа значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-127">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="5d96b-128">В следующем примере переменная `numberOfChildren` изначально не имеет определенного значения, хотя значение по умолчанию для этого `Integer` типа равно 0.</span><span class="sxs-lookup"><span data-stu-id="5d96b-128">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="5d96b-129">Значение NULL полезно для указания неопределенного или неизвестного значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-129">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="5d96b-130">Если было `numberOfChildren` объявлено как `Integer` , то не будет значения, которое может указывать на то, что информация в настоящее время недоступна.</span><span class="sxs-lookup"><span data-stu-id="5d96b-130">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="5d96b-131">Сохранение значений</span><span class="sxs-lookup"><span data-stu-id="5d96b-131">Storing Values</span></span>

<span data-ttu-id="5d96b-132">Вы сохраняете значение в переменной или свойстве типа значения, допускающего значение null, обычным способом.</span><span class="sxs-lookup"><span data-stu-id="5d96b-132">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="5d96b-133">В следующем примере значение присваивается переменной, `numberOfChildren` объявленной в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="5d96b-133">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="5d96b-134">Если переменная или свойство типа значения, допускающего значение null, содержит определенное значение, можно вернуть его первоначальное состояние, не имеющее присвоенного значения.</span><span class="sxs-lookup"><span data-stu-id="5d96b-134">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="5d96b-135">Для этого нужно задать для переменной или свойства значение `Nothing` , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="5d96b-135">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="5d96b-136">Хотя можно присвоить `Nothing` переменной тип значения, допускающего значение null, его нельзя проверить с `Nothing` помощью знака равенства.</span><span class="sxs-lookup"><span data-stu-id="5d96b-136">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="5d96b-137">При сравнении, в котором используется знак равенства, `someVar = Nothing` всегда вычисляется значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-137">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="5d96b-138">Можно проверить <xref:System.Nullable%601.HasValue%2A> свойство переменной для `False` или проверить с помощью `Is` `IsNot` оператора или.</span><span class="sxs-lookup"><span data-stu-id="5d96b-138">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="5d96b-139">Получение значений</span><span class="sxs-lookup"><span data-stu-id="5d96b-139">Retrieving Values</span></span>

<span data-ttu-id="5d96b-140">Чтобы получить значение переменной типа, допускающего значение null, сначала следует проверить его <xref:System.Nullable%601.HasValue%2A> свойство, чтобы убедиться, что оно имеет значение.</span><span class="sxs-lookup"><span data-stu-id="5d96b-140">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="5d96b-141">Если вы попытаетесь считать значение <xref:System.Nullable%601.HasValue%2A> , то `False` Visual Basic создает <xref:System.InvalidOperationException> исключение.</span><span class="sxs-lookup"><span data-stu-id="5d96b-141">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="5d96b-142">В следующем примере показан рекомендуемый способ чтения переменной `numberOfChildren` из предыдущих примеров.</span><span class="sxs-lookup"><span data-stu-id="5d96b-142">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="5d96b-143">Сравнение типов, допускающих значение null</span><span class="sxs-lookup"><span data-stu-id="5d96b-143">Comparing Nullable Types</span></span>

<span data-ttu-id="5d96b-144">Если `Boolean` в логических выражениях используются допускающие значения NULL переменные, результатом может быть `True` , `False` или `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-144">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="5d96b-145">Ниже приведена таблица истинности для `And` и `Or` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-145">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="5d96b-146">Поскольку `b1` `b2` у и теперь есть три возможных значения, можно вычислить девять комбинаций.</span><span class="sxs-lookup"><span data-stu-id="5d96b-146">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="5d96b-147">B1</span><span class="sxs-lookup"><span data-stu-id="5d96b-147">b1</span></span>|<span data-ttu-id="5d96b-148">ячейк</span><span class="sxs-lookup"><span data-stu-id="5d96b-148">b2</span></span>|<span data-ttu-id="5d96b-149">B1 и B2</span><span class="sxs-lookup"><span data-stu-id="5d96b-149">b1 And b2</span></span>|<span data-ttu-id="5d96b-150">B1 или B2</span><span class="sxs-lookup"><span data-stu-id="5d96b-150">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="5d96b-151">Если значение логической переменной или выражения равно `Nothing` , то оно не равно ни `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-151">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="5d96b-152">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="5d96b-152">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="5d96b-153">В этом примере `b1 And b2` принимает значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-153">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="5d96b-154">В результате `Else` предложение выполняется в каждой `If` инструкции, и выходные данные выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5d96b-154">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="5d96b-155">`AndAlso` и `OrElse` , использующие сокращенную оценку, должны оценивать свои вторые операнды при первом вычислении до `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-155">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="5d96b-156">Распространение</span><span class="sxs-lookup"><span data-stu-id="5d96b-156">Propagation</span></span>

<span data-ttu-id="5d96b-157">Если один или оба операнда арифметических операций, операции сравнения, сдвига или типа имеют тип значения, допускающий значение null, результат операции также является типом значения, допускающим значение null.</span><span class="sxs-lookup"><span data-stu-id="5d96b-157">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="5d96b-158">Если оба операнда имеют значения, которые не являются `Nothing` , операция выполняется с базовыми значениями операндов, как если бы ни был тип значения, допускающий значение null.</span><span class="sxs-lookup"><span data-stu-id="5d96b-158">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="5d96b-159">В следующем примере переменные `compare1` и `sum1` неявно типизированы.</span><span class="sxs-lookup"><span data-stu-id="5d96b-159">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="5d96b-160">Если навести на них указатель мыши, вы увидите, что компилятор определит типы значений, допускающие значение null, для обоих типов.</span><span class="sxs-lookup"><span data-stu-id="5d96b-160">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="5d96b-161">Если один или оба операнда имеют значение `Nothing` , результатом будет `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5d96b-161">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="5d96b-162">Использование типов, допускающих значение null, с данными</span><span class="sxs-lookup"><span data-stu-id="5d96b-162">Using Nullable Types with Data</span></span>

<span data-ttu-id="5d96b-163">База данных является одним из наиболее важных мест для использования типов значений, допускающих значение null.</span><span class="sxs-lookup"><span data-stu-id="5d96b-163">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="5d96b-164">Не все объекты базы данных в настоящее время поддерживают типы значений, допускающие значения NULL, но адаптеры таблиц, созданные конструктором, выполняют.</span><span class="sxs-lookup"><span data-stu-id="5d96b-164">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="5d96b-165">См. раздел [Поддержка TableAdapter для типов, допускающих значение NULL](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="5d96b-165">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d96b-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5d96b-166">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="5d96b-167">Типы данных</span><span class="sxs-lookup"><span data-stu-id="5d96b-167">Data Types</span></span>](index.md)
- [<span data-ttu-id="5d96b-168">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="5d96b-168">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="5d96b-169">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="5d96b-169">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="5d96b-170">Заполнение наборов данных с помощью адаптеров таблицы</span><span class="sxs-lookup"><span data-stu-id="5d96b-170">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="5d96b-171">Оператор If</span><span class="sxs-lookup"><span data-stu-id="5d96b-171">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="5d96b-172">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="5d96b-172">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="5d96b-173">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="5d96b-173">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="5d96b-174">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="5d96b-174">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="5d96b-175">Типы значений, допускающие значение null (C#)</span><span class="sxs-lookup"><span data-stu-id="5d96b-175">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
