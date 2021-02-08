---
description: 'Дополнительные сведения: математические функции'
title: Математические функции
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 6bf1f116d6d88a8a188dc31cab91fbf26bdaea36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795031"
---
# <a name="mathematical-functions"></a><span data-ttu-id="ab800-103">Математические функции</span><span class="sxs-lookup"><span data-stu-id="ab800-103">Mathematical Functions</span></span>

<span data-ttu-id="ab800-104">Поставщик данных для SQL Server платформы .NET Framework (SqlClient) предоставляет математические функции, производящие вычисления на входящих значениях, предоставляемых в качестве аргументов, и возвращающие результат в виде числовых значений.</span><span class="sxs-lookup"><span data-stu-id="ab800-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="ab800-105">Эти функции находятся в пространстве имен SqlServer, которое доступно при использовании SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ab800-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="ab800-106">Свойство пространства имен поставщика позволяет платформе Entity Framework узнать, какой префикс используется поставщиком для конкретных конструкций, таких как типы или функции.</span><span class="sxs-lookup"><span data-stu-id="ab800-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="ab800-107">В следующей таблице описаны математические функции SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ab800-107">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="ab800-108">ABS (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-108">ABS(expression)</span></span>

<span data-ttu-id="ab800-109">Возвращает абсолютное значение.</span><span class="sxs-lookup"><span data-stu-id="ab800-109">Performs the absolute value function.</span></span>

<span data-ttu-id="ab800-110">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-110">**Arguments**</span></span>

<span data-ttu-id="ab800-111">`expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ab800-111">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-112">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-112">**Return Value**</span></span>

<span data-ttu-id="ab800-113">Абсолютное значение заданного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-113">The absolute value of the specified expression.</span></span>

<span data-ttu-id="ab800-114">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-114">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="ab800-115">ACOS (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-115">ACOS(expression)</span></span>

<span data-ttu-id="ab800-116">Возвращает значение арккосинуса указанного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-116">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="ab800-117">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-117">**Arguments**</span></span>

<span data-ttu-id="ab800-118">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-118">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-119">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-119">**Return Value**</span></span>

<span data-ttu-id="ab800-120">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-120">A `Double`.</span></span>

<span data-ttu-id="ab800-121">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-121">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="ab800-122">ASIN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-122">ASIN(expression)</span></span>

<span data-ttu-id="ab800-123">Возвращает значение арксинуса указанного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-123">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="ab800-124">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-124">**Arguments**</span></span>

<span data-ttu-id="ab800-125">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-125">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-126">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-126">**Return Value**</span></span>

<span data-ttu-id="ab800-127">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-127">A `Double`.</span></span>

<span data-ttu-id="ab800-128">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-128">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="ab800-129">ATAN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-129">ATAN(expression)</span></span>

<span data-ttu-id="ab800-130">Возвращает значение арктангенса указанного числового выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-130">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="ab800-131">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-131">**Arguments**</span></span>

<span data-ttu-id="ab800-132">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-132">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-133">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-133">**Return Value**</span></span>

<span data-ttu-id="ab800-134">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-134">A `Double`.</span></span>

<span data-ttu-id="ab800-135">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-135">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="ab800-136">ATN2 (выражение, выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-136">ATN2(expression, expression)</span></span>

<span data-ttu-id="ab800-137">Возвращает угол в радианах, тангенс которого находится в диапазоне между двумя заданными числовыми выражениями.</span><span class="sxs-lookup"><span data-stu-id="ab800-137">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="ab800-138">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-138">**Arguments**</span></span>

<span data-ttu-id="ab800-139">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-139">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-140">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-140">**Return Value**</span></span>

<span data-ttu-id="ab800-141">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-141">A `Double`.</span></span>

<span data-ttu-id="ab800-142">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-142">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="ab800-143">CEILING (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-143">CEILING(expression)</span></span>

<span data-ttu-id="ab800-144">Преобразует указанное выражение в наименьшее целое число, большее или равное данному выражению.</span><span class="sxs-lookup"><span data-stu-id="ab800-144">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="ab800-145">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-145">**Arguments**</span></span>

<span data-ttu-id="ab800-146">`expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ab800-146">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-147">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-147">**Return Value**</span></span>

<span data-ttu-id="ab800-148">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-148">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-149">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-149">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="ab800-150">COS (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-150">COS(expression)</span></span>

<span data-ttu-id="ab800-151">Вычисляет тригонометрический косинус указанного угла в радианах.</span><span class="sxs-lookup"><span data-stu-id="ab800-151">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="ab800-152">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-152">**Arguments**</span></span>

<span data-ttu-id="ab800-153">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-153">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-154">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-154">**Return Value**</span></span>

<span data-ttu-id="ab800-155">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-155">A `Double`.</span></span>

<span data-ttu-id="ab800-156">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-156">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="ab800-157">COT (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-157">COT(expression)</span></span>

<span data-ttu-id="ab800-158">Вычисляет тригонометрический котангенс указанного угла в радианах.</span><span class="sxs-lookup"><span data-stu-id="ab800-158">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="ab800-159">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-159">**Arguments**</span></span>

<span data-ttu-id="ab800-160">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-160">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-161">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-161">**Return Value**</span></span>

<span data-ttu-id="ab800-162">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-162">A `Double`.</span></span>

<span data-ttu-id="ab800-163">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-163">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="ab800-164">ГРАДУСы (радианы)</span><span class="sxs-lookup"><span data-stu-id="ab800-164">DEGREES(radians)</span></span>

<span data-ttu-id="ab800-165">Возвращает соответствующее значение угла в градусах.</span><span class="sxs-lookup"><span data-stu-id="ab800-165">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="ab800-166">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-166">**Arguments**</span></span>

<span data-ttu-id="ab800-167">`expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ab800-167">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-168">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-168">**Return Value**</span></span>

<span data-ttu-id="ab800-169">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-169">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-170">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-170">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="ab800-171">EXP (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-171">EXP(expression)</span></span>

<span data-ttu-id="ab800-172">Вычисляет экспоненту заданного числового выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-172">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="ab800-173">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-173">**Arguments**</span></span>

<span data-ttu-id="ab800-174">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-174">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-175">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-175">**Return Value**</span></span>

<span data-ttu-id="ab800-176">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-176">A `Double`.</span></span>

<span data-ttu-id="ab800-177">**Пример**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="ab800-177">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="ab800-178">FLOOR (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-178">FLOOR(expression)</span></span>

<span data-ttu-id="ab800-179">Преобразует указанное выражение в наибольшее целое число, меньшее или равное данному выражению.</span><span class="sxs-lookup"><span data-stu-id="ab800-179">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="ab800-180">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-180">**Arguments**</span></span>

<span data-ttu-id="ab800-181">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-181">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-182">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-182">**Return Value**</span></span>

<span data-ttu-id="ab800-183">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-183">A `Double`.</span></span>

<span data-ttu-id="ab800-184">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-184">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="ab800-185">LOG (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-185">LOG(expression)</span></span>

<span data-ttu-id="ab800-186">Вычисляет натуральный логарифм заданного выражения типа `float`.</span><span class="sxs-lookup"><span data-stu-id="ab800-186">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="ab800-187">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-187">**Arguments**</span></span>

<span data-ttu-id="ab800-188">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-188">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-189">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-189">**Return Value**</span></span>

<span data-ttu-id="ab800-190">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-190">A `Double`.</span></span>

<span data-ttu-id="ab800-191">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-191">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="ab800-192">LOG10 (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-192">LOG10(expression)</span></span>

<span data-ttu-id="ab800-193">Возвращает десятичный логарифм указанного выражения типа `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-193">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="ab800-194">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-194">**Arguments**</span></span>

<span data-ttu-id="ab800-195">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-195">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-196">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-196">**Return Value**</span></span>

<span data-ttu-id="ab800-197">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-197">A `Double`.</span></span>

<span data-ttu-id="ab800-198">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-198">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="ab800-199">PI ()</span><span class="sxs-lookup"><span data-stu-id="ab800-199">PI()</span></span>

<span data-ttu-id="ab800-200">Возвращает константу «пи» в виде значения типа `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-200">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="ab800-201">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-201">**Return Value**</span></span>

<span data-ttu-id="ab800-202">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-202">A `Double`.</span></span>

<span data-ttu-id="ab800-203">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-203">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="ab800-204">МОЩНОСТЬ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="ab800-204">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="ab800-205">Вычисляет значение указанного выражения, возведенного в заданную степень.</span><span class="sxs-lookup"><span data-stu-id="ab800-205">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="ab800-206">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-206">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ab800-207">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-207">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="ab800-208">Объект `Double` , представляющий степень, до которой вызывается `numeric_expression` .</span><span class="sxs-lookup"><span data-stu-id="ab800-208">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="ab800-209">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-209">**Return Value**</span></span>

<span data-ttu-id="ab800-210">Значение заданного выражения `numeric_expression` в указанной степени `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="ab800-210">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="ab800-211">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-211">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="ab800-212">РАДИАНы (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-212">RADIANS(expression)</span></span>

<span data-ttu-id="ab800-213">Преобразует градусы в радианы.</span><span class="sxs-lookup"><span data-stu-id="ab800-213">Converts degrees to radians.</span></span>

<span data-ttu-id="ab800-214">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-214">**Arguments**</span></span>

<span data-ttu-id="ab800-215">`expression`: значение типа `Int32`, `Int64`, `Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ab800-215">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-216">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-216">**Return Value**</span></span>

<span data-ttu-id="ab800-217">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-217">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-218">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-218">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="ab800-219">RAND ([начальное значение])</span><span class="sxs-lookup"><span data-stu-id="ab800-219">RAND([seed])</span></span>

<span data-ttu-id="ab800-220">Возвращает случайное значение от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="ab800-220">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="ab800-221">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-221">**Arguments**</span></span>

<span data-ttu-id="ab800-222">Начальное значение в виде `Int32` .</span><span class="sxs-lookup"><span data-stu-id="ab800-222">The seed value as an `Int32`.</span></span> <span data-ttu-id="ab800-223">Если начальное значение не задано, то компонент SQL Server Database Engine присваивает случайно выбранное начальное значение.</span><span class="sxs-lookup"><span data-stu-id="ab800-223">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="ab800-224">Для указанного начального значения возвращаемый результат всегда будет один и тот же.</span><span class="sxs-lookup"><span data-stu-id="ab800-224">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="ab800-225">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-225">**Return Value**</span></span>

<span data-ttu-id="ab800-226">Случайное значение типа `Double` от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="ab800-226">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="ab800-227">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-227">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="ab800-228">ROUND (numeric_expression, длина [, функция])</span><span class="sxs-lookup"><span data-stu-id="ab800-228">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="ab800-229">Возвращает числовое выражение, округленное до указанной длины или точности.</span><span class="sxs-lookup"><span data-stu-id="ab800-229">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="ab800-230">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-230">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ab800-231">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-231">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="ab800-232">Значение типа `Int32`, указывающее точность, до которой должно быть округлено значение аргумента `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="ab800-232">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="ab800-233">Если аргумент `length` является положительным числом, значение `numeric_expression` округляется до числа десятичных разрядов, указанных аргументом `length`.</span><span class="sxs-lookup"><span data-stu-id="ab800-233">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="ab800-234">Если аргумент `length` является отрицательным числом, значение `numeric_expression` округляется слева от десятичной запятой, как указано аргументом `length`.</span><span class="sxs-lookup"><span data-stu-id="ab800-234">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="ab800-235">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ab800-235">Optional.</span></span> <span data-ttu-id="ab800-236">Объект `Int32` , представляющий тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="ab800-236">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="ab800-237">Если функция опущена или имеет значение 0 (по умолчанию), `numeric_expression` то параметр округляется.</span><span class="sxs-lookup"><span data-stu-id="ab800-237">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="ab800-238">Если указано значение, отличное от 0, `numeric_expression` усекается.</span><span class="sxs-lookup"><span data-stu-id="ab800-238">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="ab800-239">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-239">**Return Value**</span></span>

<span data-ttu-id="ab800-240">Значение заданного выражения `numeric_expression` в указанной степени `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="ab800-240">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="ab800-241">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-241">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="ab800-242">SIGN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-242">SIGN(expression)</span></span>

<span data-ttu-id="ab800-243">Возвращает положительное (+1), нулевое (0) или отрицательное (-1) значение, обозначающее знак заданного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-243">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="ab800-244">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-244">**Arguments**</span></span>

<span data-ttu-id="ab800-245">`expression`: `Int32`, `Int64`, `Double` или `Decimal`</span><span class="sxs-lookup"><span data-stu-id="ab800-245">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="ab800-246">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-246">**Return Value**</span></span>

<span data-ttu-id="ab800-247">`Int32`,, `Int64` `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab800-247">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ab800-248">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-248">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="ab800-249">SIN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-249">SIN(expression)</span></span>

<span data-ttu-id="ab800-250">Вычисляет тригонометрический синус заданного угла в радианах и возвращает выражение типа `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-250">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="ab800-251">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-251">**Arguments**</span></span>

<span data-ttu-id="ab800-252">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-252">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-253">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-253">**Return Value**</span></span>

<span data-ttu-id="ab800-254">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-254">A `Double`.</span></span>

<span data-ttu-id="ab800-255">**Пример**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="ab800-255">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="ab800-256">SQRT (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-256">SQRT(expression)</span></span>

<span data-ttu-id="ab800-257">Возвращает квадратный корень указанного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-257">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="ab800-258">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-258">**Arguments**</span></span>

<span data-ttu-id="ab800-259">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-259">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-260">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-260">**Return Value**</span></span>

<span data-ttu-id="ab800-261">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-261">A `Double`.</span></span>

<span data-ttu-id="ab800-262">**Пример**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="ab800-262">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="ab800-263">SQUARE (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-263">SQUARE(expression)</span></span>

<span data-ttu-id="ab800-264">Возвращает значение указанного выражения в квадрате.</span><span class="sxs-lookup"><span data-stu-id="ab800-264">Returns the square of the specified expression.</span></span>

<span data-ttu-id="ab800-265">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-265">**Arguments**</span></span>

<span data-ttu-id="ab800-266">`expression` — значение в формате `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-266">`expression`: A `Double`.</span></span>

<span data-ttu-id="ab800-267">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-267">**Return Value**</span></span>

<span data-ttu-id="ab800-268">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ab800-268">A `Double`.</span></span>

<span data-ttu-id="ab800-269">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-269">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="ab800-270">TAN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ab800-270">TAN(expression)</span></span>

<span data-ttu-id="ab800-271">Вычисляет тангенс заданного выражения.</span><span class="sxs-lookup"><span data-stu-id="ab800-271">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="ab800-272">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ab800-272">**Arguments**</span></span>

<span data-ttu-id="ab800-273">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="ab800-273">`expression`: `Double`</span></span>

<span data-ttu-id="ab800-274">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ab800-274">**Return Value**</span></span>

`Double`

<span data-ttu-id="ab800-275">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ab800-275">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="ab800-276">См. также</span><span class="sxs-lookup"><span data-stu-id="ab800-276">See also</span></span>

- [<span data-ttu-id="ab800-277">Математические функции (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab800-277">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="ab800-278">Функции SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ab800-278">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
