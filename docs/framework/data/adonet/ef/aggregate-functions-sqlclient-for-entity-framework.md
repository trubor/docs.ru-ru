---
description: 'Дополнительные сведения: агрегатные функции (SqlClient для Entity Framework)'
title: Статистические функции (SqlClient для Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: b9f1ff8c75fc09de7532b459090b0b5cd1d47262
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651084"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="89267-103">Статистические функции (SqlClient для Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="89267-103">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="89267-104">Поставщик данных .NET Framework для SQL Server (SqlClient) предоставляет агрегатные функции.</span><span class="sxs-lookup"><span data-stu-id="89267-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="89267-105">Агрегатные функции выполняют вычисления на наборе входных значений и возвращают значение.</span><span class="sxs-lookup"><span data-stu-id="89267-105">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="89267-106">Эти функции находятся в пространстве имен SqlServer, которое доступно при использовании SqlClient.</span><span class="sxs-lookup"><span data-stu-id="89267-106">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="89267-107">Свойство пространства имен поставщика позволяет платформе Entity Framework узнать, какой префикс используется поставщиком для конкретных конструкций, таких как типы или функции.</span><span class="sxs-lookup"><span data-stu-id="89267-107">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="89267-108">Ниже приведены агрегатные функции SqlClient.</span><span class="sxs-lookup"><span data-stu-id="89267-108">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="89267-109">AVG (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-109">AVG(expression)</span></span>

<span data-ttu-id="89267-110">Возвращает среднее значение для значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="89267-110">Returns the average of the values in a collection.</span></span> <span data-ttu-id="89267-111">Значения NULL пропускаются.</span><span class="sxs-lookup"><span data-stu-id="89267-111">Null values are ignored.</span></span>

<span data-ttu-id="89267-112">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-112">**Arguments**</span></span>

<span data-ttu-id="89267-113">`Int32`,, `Int64` `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="89267-113">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="89267-114">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-114">**Return Value**</span></span>

<span data-ttu-id="89267-115">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="89267-115">The type of `expression`.</span></span>

<span data-ttu-id="89267-116">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-116">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="89267-117">CHECKSUM_AGG (коллекция)</span><span class="sxs-lookup"><span data-stu-id="89267-117">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="89267-118">Возвращает контрольную сумму значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="89267-118">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="89267-119">Значения NULL пропускаются.</span><span class="sxs-lookup"><span data-stu-id="89267-119">Null values are ignored.</span></span>

 <span data-ttu-id="89267-120">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-120">**Arguments**</span></span>

 <span data-ttu-id="89267-121">Коллекция ( `Int32` ).</span><span class="sxs-lookup"><span data-stu-id="89267-121">A Collection(`Int32`).</span></span>

 <span data-ttu-id="89267-122">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-122">**Return Value**</span></span>

 <span data-ttu-id="89267-123">Объект `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89267-123">An `Int32`.</span></span>

 <span data-ttu-id="89267-124">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-124">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="89267-125">COUNT (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-125">COUNT(expression)</span></span>

<span data-ttu-id="89267-126">Возвращает число элементов в коллекции в виде `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89267-126">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="89267-127">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-127">**Arguments**</span></span>

<span data-ttu-id="89267-128">Коллекция \<T> , где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="89267-128">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="89267-129">`Guid` (не возвращается в SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="89267-129">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="89267-130">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-130">**Return Value**</span></span>

<span data-ttu-id="89267-131">Объект `Int32`.</span><span class="sxs-lookup"><span data-stu-id="89267-131">An `Int32`.</span></span>

<span data-ttu-id="89267-132">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-132">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="89267-133">COUNT_BIG (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-133">COUNT_BIG(expression)</span></span>

<span data-ttu-id="89267-134">Возвращает число элементов в коллекции в виде `bigint`.</span><span class="sxs-lookup"><span data-stu-id="89267-134">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="89267-135">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-135">**Arguments**</span></span>

 <span data-ttu-id="89267-136">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="89267-136">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="89267-137">`Guid` (не возвращается в SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="89267-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="89267-138">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-138">**Return Value**</span></span>

<span data-ttu-id="89267-139">Объект `Int64`.</span><span class="sxs-lookup"><span data-stu-id="89267-139">An `Int64`.</span></span>

<span data-ttu-id="89267-140">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-140">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="89267-141">MAX (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-141">MAX(expression)</span></span>

<span data-ttu-id="89267-142">Возвращает максимальное значение, содержащееся в коллекции.</span><span class="sxs-lookup"><span data-stu-id="89267-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="89267-143">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-143">**Arguments**</span></span>

<span data-ttu-id="89267-144">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="89267-144">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="89267-145">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-145">**Return Value**</span></span>

<span data-ttu-id="89267-146">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="89267-146">The type of `expression`.</span></span>

<span data-ttu-id="89267-147">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-147">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="89267-148">MIN (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-148">MIN(expression)</span></span>

<span data-ttu-id="89267-149">Возвращает минимальное значение в коллекции.</span><span class="sxs-lookup"><span data-stu-id="89267-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="89267-150">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-150">**Arguments**</span></span>

<span data-ttu-id="89267-151">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="89267-151">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="89267-152">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-152">**Return Value**</span></span>

<span data-ttu-id="89267-153">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="89267-153">The type of `expression`.</span></span>

<span data-ttu-id="89267-154">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-154">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="89267-155">STDEV (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-155">STDEV(expression)</span></span>

<span data-ttu-id="89267-156">Возвращает статистическое стандартное отклонение всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="89267-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="89267-157">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-157">**Arguments**</span></span>

<span data-ttu-id="89267-158">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="89267-158">A Collection(`Double`).</span></span>

<span data-ttu-id="89267-159">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-159">**Return Value**</span></span>

<span data-ttu-id="89267-160">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="89267-160">A `Double`.</span></span>

<span data-ttu-id="89267-161">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-161">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="89267-162">STDEVP (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-162">STDEVP(expression)</span></span>

<span data-ttu-id="89267-163">Возвращает статистическое стандартное отклонение совокупности всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="89267-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="89267-164">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-164">**Arguments**</span></span>

<span data-ttu-id="89267-165">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="89267-165">A Collection(`Double`).</span></span>

<span data-ttu-id="89267-166">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-166">**Return Value**</span></span>

<span data-ttu-id="89267-167">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="89267-167">A `Double`.</span></span>

<span data-ttu-id="89267-168">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-168">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="89267-169">SUM (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-169">SUM(expression)</span></span>

<span data-ttu-id="89267-170">Возвращает сумму всех значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="89267-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="89267-171">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-171">**Arguments**</span></span>

<span data-ttu-id="89267-172">Коллекция (T), где T — один из следующих типов: `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="89267-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="89267-173">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-173">**Return Value**</span></span>

<span data-ttu-id="89267-174">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="89267-174">The type of `expression`.</span></span>

<span data-ttu-id="89267-175">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-175">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="89267-176">VAR (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-176">VAR(expression)</span></span>

<span data-ttu-id="89267-177">Возвращает статистическую дисперсию всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="89267-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="89267-178">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-178">**Arguments**</span></span>

<span data-ttu-id="89267-179">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="89267-179">A Collection(`Double`).</span></span>

<span data-ttu-id="89267-180">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-180">**Return Value**</span></span>

<span data-ttu-id="89267-181">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="89267-181">A `Double`.</span></span>

<span data-ttu-id="89267-182">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-182">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="89267-183">VARP (выражение)</span><span class="sxs-lookup"><span data-stu-id="89267-183">VARP(expression)</span></span>

<span data-ttu-id="89267-184">Возвращает статистическую дисперсию для заполнения всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="89267-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="89267-185">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="89267-185">**Arguments**</span></span>

<span data-ttu-id="89267-186">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="89267-186">A Collection(`Double`).</span></span>

<span data-ttu-id="89267-187">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="89267-187">**Return Value**</span></span>

<span data-ttu-id="89267-188">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="89267-188">A `Double`.</span></span>

<span data-ttu-id="89267-189">**Пример**</span><span class="sxs-lookup"><span data-stu-id="89267-189">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="89267-190">См. также</span><span class="sxs-lookup"><span data-stu-id="89267-190">See also</span></span>

- [<span data-ttu-id="89267-191">Агрегатные функции (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="89267-191">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="89267-192">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="89267-192">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="89267-193">Статистические канонические функции</span><span class="sxs-lookup"><span data-stu-id="89267-193">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
