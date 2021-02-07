---
description: 'Дополнительные сведения: статистические канонические функции'
title: Статистические канонические функции
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e26888ac15553a592f7d2cb9b1a0941161115615
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697300"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="89ed2-103">Статистические канонические функции</span><span class="sxs-lookup"><span data-stu-id="89ed2-103">Aggregate Canonical Functions</span></span>

<span data-ttu-id="89ed2-104">Статистические выражения - выражения, которые уменьшают количество входных значений, например, до одного значения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-104">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="89ed2-105">Статистические выражения обычно используются совместно с предложением группирования GROUP BY выражения SELECT, а на область их использования накладываются ограничения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-105">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="89ed2-106">Агрегатные Entity SQL канонические функции</span><span class="sxs-lookup"><span data-stu-id="89ed2-106">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="89ed2-107">Ниже приведены агрегатные Entity SQL канонических функциях.</span><span class="sxs-lookup"><span data-stu-id="89ed2-107">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="89ed2-108">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-108">Avg(expression)</span></span>

<span data-ttu-id="89ed2-109">Возвращает среднее для значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-109">Returns the average of the non-null values.</span></span>

<span data-ttu-id="89ed2-110">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-110">**Arguments**</span></span>

<span data-ttu-id="89ed2-111">`Int32`,, `Int64` `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="89ed2-111">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="89ed2-112">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-112">**Return Value**</span></span>

<span data-ttu-id="89ed2-113">Тип или значение `expression` , `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-113">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-114">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-114">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="89ed2-115">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-115">BigCount(expression)</span></span>

<span data-ttu-id="89ed2-116">Возвращает объем данных, подвергаемых статистической обработке, включая значения NULL и повторяющиеся значения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-116">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="89ed2-117">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-117">**Arguments**</span></span>

<span data-ttu-id="89ed2-118">Любой тип.</span><span class="sxs-lookup"><span data-stu-id="89ed2-118">Any type.</span></span>

<span data-ttu-id="89ed2-119">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-119">**Return Value**</span></span>

<span data-ttu-id="89ed2-120">Объект `Int64`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-120">An `Int64`.</span></span>

<span data-ttu-id="89ed2-121">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-121">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="89ed2-122">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-122">Count(expression)</span></span>

<span data-ttu-id="89ed2-123">Возвращает объем данных, подвергаемых статистической обработке, включая значения NULL и повторяющиеся значения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-123">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="89ed2-124">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-124">**Arguments**</span></span>

<span data-ttu-id="89ed2-125">Любой тип.</span><span class="sxs-lookup"><span data-stu-id="89ed2-125">Any type.</span></span>

<span data-ttu-id="89ed2-126">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-126">**Return Value**</span></span>

<span data-ttu-id="89ed2-127">Объект `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-127">An `Int32`.</span></span>

<span data-ttu-id="89ed2-128">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-128">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="89ed2-129">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-129">Max(expression)</span></span>

<span data-ttu-id="89ed2-130">Возвращает максимум для значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-130">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="89ed2-131">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-131">**Arguments**</span></span>

<span data-ttu-id="89ed2-132">Значения типа `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-132">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="89ed2-133">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-133">**Return Value**</span></span>

<span data-ttu-id="89ed2-134">Тип или значение `expression` , `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-134">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-135">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-135">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="89ed2-136">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-136">Min(expression)</span></span>

<span data-ttu-id="89ed2-137">Возвращает минимум для значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-137">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="89ed2-138">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-138">**Arguments**</span></span>

<span data-ttu-id="89ed2-139">Значения типа `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-139">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="89ed2-140">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-140">**Return Value**</span></span>

<span data-ttu-id="89ed2-141">Тип или значение `expression` , `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-141">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-142">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-142">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="89ed2-143">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-143">StDev(expression)</span></span>

<span data-ttu-id="89ed2-144">Возвращает стандартное отклонение для значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-144">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="89ed2-145">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-145">**Arguments**</span></span>

<span data-ttu-id="89ed2-146">Имеют типы `Int32`, `Int64`, `Double` и `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-146">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89ed2-147">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-147">**Return Value**</span></span>

<span data-ttu-id="89ed2-148">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-148">A `Double`.</span></span> <span data-ttu-id="89ed2-149">Возвращает `Null`, если все входные значения представляют собой значения `null`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-149">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-150">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-150">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="89ed2-151">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-151">StDevP(expression)</span></span>

<span data-ttu-id="89ed2-152">Возвращает стандартное отклонение для заполнения по всем значениям.</span><span class="sxs-lookup"><span data-stu-id="89ed2-152">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="89ed2-153">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-153">**Arguments**</span></span>

<span data-ttu-id="89ed2-154">Имеют типы `Int32`, `Int64`, `Double` и `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-154">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89ed2-155">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-155">**Return Value**</span></span>

<span data-ttu-id="89ed2-156">А `Double` или, `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-156">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-157">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-157">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="89ed2-158">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-158">Sum(expression)</span></span>

<span data-ttu-id="89ed2-159">Возвращает сумму для значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-159">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="89ed2-160">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-160">**Arguments**</span></span>

<span data-ttu-id="89ed2-161">Имеют типы `Int32`, `Int64`, `Double` и `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-161">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89ed2-162">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-162">**Return Value**</span></span>

<span data-ttu-id="89ed2-163">А `Double` или, `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-163">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-164">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-164">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="89ed2-165">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-165">Var(expression)</span></span>

<span data-ttu-id="89ed2-166">Возвращает дисперсию всех значений, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-166">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="89ed2-167">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-167">**Arguments**</span></span>

<span data-ttu-id="89ed2-168">Имеют типы `Int32`, `Int64`, `Double` и `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-168">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89ed2-169">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-169">**Return Value**</span></span>

<span data-ttu-id="89ed2-170">А `Double` или, `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-170">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-171">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-171">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="89ed2-172">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="89ed2-172">VarP(expression)</span></span>

<span data-ttu-id="89ed2-173">Возвращает дисперсию для заполнения по всем значениям, отличным от NULL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-173">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="89ed2-174">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89ed2-174">**Arguments**</span></span>

<span data-ttu-id="89ed2-175">Имеют типы `Int32`, `Int64`, `Double` и `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89ed2-175">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89ed2-176">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89ed2-176">**Return Value**</span></span>

<span data-ttu-id="89ed2-177">А `Double` или, `null` Если все входные значения являются `null` значениями.</span><span class="sxs-lookup"><span data-stu-id="89ed2-177">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="89ed2-178">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89ed2-178">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="89ed2-179">Эквивалентную функциональность предоставляет управляемый поставщик клиента Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="89ed2-179">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="89ed2-180">Дополнительные сведения см. в разделе [SqlClient для функций Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="89ed2-180">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="89ed2-181">Статистические выражения на основе коллекций</span><span class="sxs-lookup"><span data-stu-id="89ed2-181">Collection-based aggregates</span></span>

<span data-ttu-id="89ed2-182">Статистические функции на основе коллекций (функции коллекций) работают с коллекциями и возвращают значение.</span><span class="sxs-lookup"><span data-stu-id="89ed2-182">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="89ed2-183">Например, если ORDERs является коллекцией всех заказов, можно вычислить самую раннюю дату отгрузки с помощью следующего выражения:</span><span class="sxs-lookup"><span data-stu-id="89ed2-183">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="89ed2-184">Выражения внутри статистических функций на основе коллекций вычисляются в текущей внешней области разрешения имен.</span><span class="sxs-lookup"><span data-stu-id="89ed2-184">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="89ed2-185">Статистические выражения на основе групп</span><span class="sxs-lookup"><span data-stu-id="89ed2-185">Group-based aggregates</span></span>

<span data-ttu-id="89ed2-186">Статистические функции на основе групп вычисляются для группы, определенной предложением GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="89ed2-186">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="89ed2-187">Для каждой группы результата выполняется отдельное статистическое вычисление с использованием элементов каждой группы в качестве входных значений.</span><span class="sxs-lookup"><span data-stu-id="89ed2-187">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="89ed2-188">Если в выражении SELECT используется предложение группирования, в проекции или предложении сортировки могут употребляться только имена выражений группирования, статистические функции или константные выражения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-188">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="89ed2-189">В следующем примере вычисляется средняя величина заказа для каждого продукта.</span><span class="sxs-lookup"><span data-stu-id="89ed2-189">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="89ed2-190">Можно использовать статистическое выражение на основе групп без явного предложения GROUP-BY в выражении SELECT.</span><span class="sxs-lookup"><span data-stu-id="89ed2-190">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="89ed2-191">В этом случае все элементы рассматриваются как одна группа.</span><span class="sxs-lookup"><span data-stu-id="89ed2-191">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="89ed2-192">Это эквивалентно указанию группирования на основе константы.</span><span class="sxs-lookup"><span data-stu-id="89ed2-192">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="89ed2-193">Например, выражение:</span><span class="sxs-lookup"><span data-stu-id="89ed2-193">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="89ed2-194">Оно эквивалентно следующему выражению:</span><span class="sxs-lookup"><span data-stu-id="89ed2-194">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="89ed2-195">Выражения внутри статистической функции на основе групп вычисляются в области разрешения имен, видимой для выражения предложения WHERE.</span><span class="sxs-lookup"><span data-stu-id="89ed2-195">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="89ed2-196">Как и в Transact-SQL, статистические выражения на основе групп могут также задавать модификатор ALL или DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="89ed2-196">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="89ed2-197">Если задан модификатор DISTINCT, то перед вычислением статистической функции из входного набора исключаются повторяющиеся значения.</span><span class="sxs-lookup"><span data-stu-id="89ed2-197">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="89ed2-198">Если задан модификатор ALL (или не указан никакой модификатор), то исключение повторяющихся значений не выполняется.</span><span class="sxs-lookup"><span data-stu-id="89ed2-198">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="89ed2-199">См. также</span><span class="sxs-lookup"><span data-stu-id="89ed2-199">See also</span></span>

- [<span data-ttu-id="89ed2-200">Канонические функции</span><span class="sxs-lookup"><span data-stu-id="89ed2-200">Canonical Functions</span></span>](canonical-functions.md)
