---
description: Дополнительные сведения о математических канонических функциях
title: Математические канонические функции
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 55072099f5766d48ea3067a2e9eaa187a8b3f111
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739369"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="8243d-103">Математические канонические функции</span><span class="sxs-lookup"><span data-stu-id="8243d-103">Math Canonical Functions</span></span>

<span data-ttu-id="8243d-104">Entity SQL включает следующие математические канонические функции:</span><span class="sxs-lookup"><span data-stu-id="8243d-104">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="8243d-105">Abs(значение)</span><span class="sxs-lookup"><span data-stu-id="8243d-105">Abs(value)</span></span>

<span data-ttu-id="8243d-106">Возвращает абсолютное значение `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-106">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="8243d-107">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-107">**Arguments**</span></span>

<span data-ttu-id="8243d-108">`Int16`,, `Int32` , `Int64` `Byte` ,, `Single` И `Double` `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8243d-108">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="8243d-109">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-109">**Return Value**</span></span>

<span data-ttu-id="8243d-110">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-110">The type of `value`.</span></span>

<span data-ttu-id="8243d-111">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-111">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="8243d-112">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="8243d-112">Ceiling(value)</span></span>

<span data-ttu-id="8243d-113">Возвращает наименьшее целое число, которое не меньше значения `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-113">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="8243d-114">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-114">**Arguments**</span></span>

<span data-ttu-id="8243d-115">`Single`, `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8243d-115">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="8243d-116">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-116">**Return Value**</span></span>

<span data-ttu-id="8243d-117">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-117">The type of `value`.</span></span>

<span data-ttu-id="8243d-118">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-118">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="8243d-119">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="8243d-119">Floor(value)</span></span>

<span data-ttu-id="8243d-120">Возвращает наибольшее целое число, которое не больше значения `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-120">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="8243d-121">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-121">**Arguments**</span></span>

<span data-ttu-id="8243d-122">`Single`, `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8243d-122">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="8243d-123">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-123">**Return Value**</span></span>

<span data-ttu-id="8243d-124">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-124">The type of `value`.</span></span>

<span data-ttu-id="8243d-125">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-125">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="8243d-126">Power(значение, показатель степени)</span><span class="sxs-lookup"><span data-stu-id="8243d-126">Power(value, exponent)</span></span>

<span data-ttu-id="8243d-127">Возвращает результат для заданного значения `value` по заданному показателю `exponent`.</span><span class="sxs-lookup"><span data-stu-id="8243d-127">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="8243d-128">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-128">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="8243d-129">`Int32, Int64, Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8243d-129">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="8243d-130">`Int64`, `Double` Или `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8243d-130">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="8243d-131">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-131">**Return Value**</span></span>

<span data-ttu-id="8243d-132">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-132">The type of `value`.</span></span>

<span data-ttu-id="8243d-133">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-133">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="8243d-134">Round(value)</span><span class="sxs-lookup"><span data-stu-id="8243d-134">Round(value)</span></span>

<span data-ttu-id="8243d-135">Возвращает целую часть `value`, округленную до ближайшего целого значения.</span><span class="sxs-lookup"><span data-stu-id="8243d-135">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="8243d-136">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-136">**Arguments**</span></span>

<span data-ttu-id="8243d-137">`Single`, `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8243d-137">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="8243d-138">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-138">**Return Value**</span></span>

<span data-ttu-id="8243d-139">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-139">The type of `value`.</span></span>

<span data-ttu-id="8243d-140">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-140">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="8243d-141">Round(значение, количество знаков)</span><span class="sxs-lookup"><span data-stu-id="8243d-141">Round(value, digits)</span></span>

<span data-ttu-id="8243d-142">Возвращает значение `value`, округленное до ближайшего указанного знака `digits`.</span><span class="sxs-lookup"><span data-stu-id="8243d-142">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="8243d-143">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-143">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="8243d-144">`Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8243d-144">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="8243d-145">`Int16` или `Int32`.</span><span class="sxs-lookup"><span data-stu-id="8243d-145">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="8243d-146">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-146">**Return Value**</span></span>

<span data-ttu-id="8243d-147">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-147">The type of `value`.</span></span>

<span data-ttu-id="8243d-148">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-148">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="8243d-149">Truncate(значение, количество знаков)</span><span class="sxs-lookup"><span data-stu-id="8243d-149">Truncate(value, digits)</span></span>

<span data-ttu-id="8243d-150">Возвращает значение `value`, усеченное до ближайшего указанного знака `digits`.</span><span class="sxs-lookup"><span data-stu-id="8243d-150">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="8243d-151">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="8243d-151">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="8243d-152">`Double` или `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8243d-152">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="8243d-153">`Int16` или `Int32`.</span><span class="sxs-lookup"><span data-stu-id="8243d-153">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="8243d-154">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="8243d-154">**Return Value**</span></span>

<span data-ttu-id="8243d-155">Тип параметра `value`.</span><span class="sxs-lookup"><span data-stu-id="8243d-155">The type of `value`.</span></span>

<span data-ttu-id="8243d-156">**Пример**</span><span class="sxs-lookup"><span data-stu-id="8243d-156">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="8243d-157">Эти функции возвращают `null` при получении на входе `null`.</span><span class="sxs-lookup"><span data-stu-id="8243d-157">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="8243d-158">Эквивалентную функциональность предоставляет управляемый поставщик клиента Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="8243d-158">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="8243d-159">Дополнительные сведения см. в разделе [SqlClient для функций Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="8243d-159">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8243d-160">См. также</span><span class="sxs-lookup"><span data-stu-id="8243d-160">See also</span></span>

- [<span data-ttu-id="8243d-161">Канонические функции</span><span class="sxs-lookup"><span data-stu-id="8243d-161">Canonical Functions</span></span>](canonical-functions.md)
