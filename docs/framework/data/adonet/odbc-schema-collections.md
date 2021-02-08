---
description: 'Дополнительные сведения: коллекции схем ODBC'
title: Коллекции схемы ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ceac67e49914db7010e315a2dfcdb630bea1e29f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786203"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="2a1ca-103">Коллекции схемы ODBC</span><span class="sxs-lookup"><span data-stu-id="2a1ca-103">ODBC Schema Collections</span></span>

<span data-ttu-id="2a1ca-104">В данном разделе рассматривается поддержка коллекций схем для драйверов ODBC для Microsoft SQL Server, Oracle и Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="2a1ca-104">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="2a1ca-105">Драйвер ODBC для Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="2a1ca-105">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="2a1ca-106">Драйвер ODBC для Microsoft SQL Server поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="2a1ca-106">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="2a1ca-107">Таблицы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-107">Tables</span></span>

- <span data-ttu-id="2a1ca-108">Индексы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-108">Indexes</span></span>

- <span data-ttu-id="2a1ca-109">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-109">Columns</span></span>

- <span data-ttu-id="2a1ca-110">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-110">Procedures</span></span>

- <span data-ttu-id="2a1ca-111">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-111">ProcedureColumns</span></span>

- <span data-ttu-id="2a1ca-112">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2a1ca-112">ProcedureParameters</span></span>

- <span data-ttu-id="2a1ca-113">Представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-113">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="2a1ca-114">Таблицы и представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-114">Tables and Views</span></span>

|<span data-ttu-id="2a1ca-115">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-115">ColumnName</span></span>|<span data-ttu-id="2a1ca-116">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-116">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-117">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-117">TABLE_CAT</span></span>|<span data-ttu-id="2a1ca-118">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-118">String</span></span>|
|<span data-ttu-id="2a1ca-119">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-119">TABLE_SCHEM</span></span>|<span data-ttu-id="2a1ca-120">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-120">String</span></span>|
|<span data-ttu-id="2a1ca-121">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-121">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-122">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-122">String</span></span>|
|<span data-ttu-id="2a1ca-123">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-123">TABLE_TYPE</span></span>|<span data-ttu-id="2a1ca-124">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-124">String</span></span>|
|<span data-ttu-id="2a1ca-125">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-125">REMARKS</span></span>|<span data-ttu-id="2a1ca-126">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-126">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="2a1ca-127">Индексы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-127">Indexes</span></span>

|<span data-ttu-id="2a1ca-128">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-128">ColumnName</span></span>|<span data-ttu-id="2a1ca-129">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-129">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-130">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-130">TABLE_CAT</span></span>|<span data-ttu-id="2a1ca-131">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-131">String</span></span>|
|<span data-ttu-id="2a1ca-132">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-132">TABLE_SCHEM</span></span>|<span data-ttu-id="2a1ca-133">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-133">String</span></span>|
|<span data-ttu-id="2a1ca-134">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-134">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-135">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-135">String</span></span>|
|<span data-ttu-id="2a1ca-136">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-136">NON_UNIQUE</span></span>|<span data-ttu-id="2a1ca-137">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-137">Int16</span></span>|
|<span data-ttu-id="2a1ca-138">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-138">INDEX_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-139">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-139">String</span></span>|
|<span data-ttu-id="2a1ca-140">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-140">INDEX_NAME</span></span>|<span data-ttu-id="2a1ca-141">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-141">String</span></span>|
|<span data-ttu-id="2a1ca-142">TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-142">TYPE</span></span>|<span data-ttu-id="2a1ca-143">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-143">Int16</span></span>|
|<span data-ttu-id="2a1ca-144">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-144">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-145">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-145">Int16</span></span>|
|<span data-ttu-id="2a1ca-146">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-146">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-147">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-147">String</span></span>|
|<span data-ttu-id="2a1ca-148">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="2a1ca-148">ASC_OR_DESC</span></span>|<span data-ttu-id="2a1ca-149">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-149">String</span></span>|
|<span data-ttu-id="2a1ca-150">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="2a1ca-150">CARDINALITY</span></span>|<span data-ttu-id="2a1ca-151">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-151">Int32</span></span>|
|<span data-ttu-id="2a1ca-152">PAGES</span><span class="sxs-lookup"><span data-stu-id="2a1ca-152">PAGES</span></span>|<span data-ttu-id="2a1ca-153">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-153">Int32</span></span>|
|<span data-ttu-id="2a1ca-154">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-154">FILTER_CONDITION</span></span>|<span data-ttu-id="2a1ca-155">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-155">String</span></span>|
|<span data-ttu-id="2a1ca-156">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2a1ca-156">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2a1ca-157">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-157">String</span></span>|
|<span data-ttu-id="2a1ca-158">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-158">SS_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-159">Byte</span><span class="sxs-lookup"><span data-stu-id="2a1ca-159">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="2a1ca-160">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-160">Columns</span></span>

|<span data-ttu-id="2a1ca-161">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-161">ColumnName</span></span>|<span data-ttu-id="2a1ca-162">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-162">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-163">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-163">TABLE_CAT</span></span>|<span data-ttu-id="2a1ca-164">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-164">String</span></span>|
|<span data-ttu-id="2a1ca-165">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-165">TABLE_SCHEM</span></span>|<span data-ttu-id="2a1ca-166">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-166">String</span></span>|
|<span data-ttu-id="2a1ca-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-167">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-168">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-168">String</span></span>|
|<span data-ttu-id="2a1ca-169">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-169">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-170">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-170">String</span></span>|
|<span data-ttu-id="2a1ca-171">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-171">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-172">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-172">Int16</span></span>|
|<span data-ttu-id="2a1ca-173">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-173">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-174">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-174">String</span></span>|
|<span data-ttu-id="2a1ca-175">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-175">COLUMN_SIZE</span></span>|<span data-ttu-id="2a1ca-176">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-176">Int32</span></span>|
|<span data-ttu-id="2a1ca-177">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-177">BUFFER_LENGTH</span></span>|<span data-ttu-id="2a1ca-178">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-178">Int32</span></span>|
|<span data-ttu-id="2a1ca-179">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-179">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2a1ca-180">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-180">Int16</span></span>|
|<span data-ttu-id="2a1ca-181">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-181">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2a1ca-182">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-182">Int16</span></span>|
|<span data-ttu-id="2a1ca-183">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-183">NULLABLE</span></span>|<span data-ttu-id="2a1ca-184">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-184">Int16</span></span>|
|<span data-ttu-id="2a1ca-185">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-185">REMARKS</span></span>|<span data-ttu-id="2a1ca-186">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-186">String</span></span>|
|<span data-ttu-id="2a1ca-187">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2a1ca-187">COLUMN_DEF</span></span>|<span data-ttu-id="2a1ca-188">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-188">String</span></span>|
|<span data-ttu-id="2a1ca-189">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-189">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-190">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-190">Int16</span></span>|
|<span data-ttu-id="2a1ca-191">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2a1ca-191">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2a1ca-192">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-192">Int16</span></span>|
|<span data-ttu-id="2a1ca-193">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-193">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2a1ca-194">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-194">Int32</span></span>|
|<span data-ttu-id="2a1ca-195">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-195">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-196">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-196">Int32</span></span>|
|<span data-ttu-id="2a1ca-197">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-197">IS_NULLABLE</span></span>|<span data-ttu-id="2a1ca-198">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-198">String</span></span>|
|<span data-ttu-id="2a1ca-199">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2a1ca-199">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2a1ca-200">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-200">String</span></span>|
|<span data-ttu-id="2a1ca-201">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2a1ca-201">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2a1ca-202">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-202">String</span></span>|
|<span data-ttu-id="2a1ca-203">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-203">SS_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-204">Byte</span><span class="sxs-lookup"><span data-stu-id="2a1ca-204">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="2a1ca-205">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-205">Procedures</span></span>

|<span data-ttu-id="2a1ca-206">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-206">ColumnName</span></span>|<span data-ttu-id="2a1ca-207">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-207">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-208">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-208">PROCEDURE_CAT</span></span>|<span data-ttu-id="2a1ca-209">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-209">String</span></span>|
|<span data-ttu-id="2a1ca-210">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-210">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2a1ca-211">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-211">String</span></span>|
|<span data-ttu-id="2a1ca-212">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-212">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-213">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-213">String</span></span>|
|<span data-ttu-id="2a1ca-214">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-214">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-215">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-215">Int32</span></span>|
|<span data-ttu-id="2a1ca-216">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-216">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-217">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-217">Int32</span></span>|
|<span data-ttu-id="2a1ca-218">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-218">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2a1ca-219">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-219">Int32</span></span>|
|<span data-ttu-id="2a1ca-220">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-220">REMARKS</span></span>|<span data-ttu-id="2a1ca-221">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-221">String</span></span>|
|<span data-ttu-id="2a1ca-222">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-222">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2a1ca-223">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-223">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="2a1ca-224">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-224">ProcedureColumns</span></span>

|<span data-ttu-id="2a1ca-225">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-225">ColumnName</span></span>|<span data-ttu-id="2a1ca-226">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-226">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-227">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-227">PROCEDURE_CAT</span></span>|<span data-ttu-id="2a1ca-228">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-228">String</span></span>|
|<span data-ttu-id="2a1ca-229">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-229">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2a1ca-230">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-230">String</span></span>|
|<span data-ttu-id="2a1ca-231">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-231">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-232">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-232">String</span></span>|
|<span data-ttu-id="2a1ca-233">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-233">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-234">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-234">String</span></span>|
|<span data-ttu-id="2a1ca-235">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-235">COLUMN_TYPE</span></span>|<span data-ttu-id="2a1ca-236">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-236">Int16</span></span>|
|<span data-ttu-id="2a1ca-237">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-237">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-238">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-238">Int16</span></span>|
|<span data-ttu-id="2a1ca-239">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-239">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-240">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-240">String</span></span>|
|<span data-ttu-id="2a1ca-241">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-241">COLUMN_SIZE</span></span>|<span data-ttu-id="2a1ca-242">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-242">Int32</span></span>|
|<span data-ttu-id="2a1ca-243">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-243">BUFFER_LENGTH</span></span>|<span data-ttu-id="2a1ca-244">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-244">Int32</span></span>|
|<span data-ttu-id="2a1ca-245">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-245">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2a1ca-246">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-246">Int16</span></span>|
|<span data-ttu-id="2a1ca-247">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-247">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2a1ca-248">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-248">Int16</span></span>|
|<span data-ttu-id="2a1ca-249">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-249">NULLABLE</span></span>|<span data-ttu-id="2a1ca-250">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-250">Int16</span></span>|
|<span data-ttu-id="2a1ca-251">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-251">REMARKS</span></span>|<span data-ttu-id="2a1ca-252">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-252">String</span></span>|
|<span data-ttu-id="2a1ca-253">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2a1ca-253">COLUMN_DEF</span></span>|<span data-ttu-id="2a1ca-254">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-254">String</span></span>|
|<span data-ttu-id="2a1ca-255">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-255">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-256">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-256">Int16</span></span>|
|<span data-ttu-id="2a1ca-257">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2a1ca-257">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2a1ca-258">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-258">Int16</span></span>|
|<span data-ttu-id="2a1ca-259">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-259">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2a1ca-260">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-260">Int32</span></span>|
|<span data-ttu-id="2a1ca-261">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-261">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-262">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-262">Int32</span></span>|
|<span data-ttu-id="2a1ca-263">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-263">IS_NULLABLE</span></span>|<span data-ttu-id="2a1ca-264">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-264">String</span></span>|
|<span data-ttu-id="2a1ca-265">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2a1ca-265">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2a1ca-266">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-266">String</span></span>|
|<span data-ttu-id="2a1ca-267">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2a1ca-267">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2a1ca-268">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-268">String</span></span>|
|<span data-ttu-id="2a1ca-269">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-269">SS_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-270">Byte</span><span class="sxs-lookup"><span data-stu-id="2a1ca-270">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="2a1ca-271">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2a1ca-271">ProcedureParameters</span></span>

|<span data-ttu-id="2a1ca-272">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-272">ColumnName</span></span>|<span data-ttu-id="2a1ca-273">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-273">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-274">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-274">PROCEDURE_CAT</span></span>|<span data-ttu-id="2a1ca-275">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-275">String</span></span>|
|<span data-ttu-id="2a1ca-276">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-276">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2a1ca-277">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-277">String</span></span>|
|<span data-ttu-id="2a1ca-278">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-278">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-279">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-279">String</span></span>|
|<span data-ttu-id="2a1ca-280">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-280">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-281">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-281">String</span></span>|
|<span data-ttu-id="2a1ca-282">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-282">COLUMN_TYPE</span></span>|<span data-ttu-id="2a1ca-283">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-283">Int16</span></span>|
|<span data-ttu-id="2a1ca-284">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-284">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-285">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-285">Int16</span></span>|
|<span data-ttu-id="2a1ca-286">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-286">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-287">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-287">String</span></span>|
|<span data-ttu-id="2a1ca-288">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-288">COLUMN_SIZE</span></span>|<span data-ttu-id="2a1ca-289">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-289">Int32</span></span>|
|<span data-ttu-id="2a1ca-290">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-290">BUFFER_LENGTH</span></span>|<span data-ttu-id="2a1ca-291">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-291">Int32</span></span>|
|<span data-ttu-id="2a1ca-292">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-292">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2a1ca-293">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-293">Int16</span></span>|
|<span data-ttu-id="2a1ca-294">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-294">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2a1ca-295">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-295">Int16</span></span>|
|<span data-ttu-id="2a1ca-296">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-296">NULLABLE</span></span>|<span data-ttu-id="2a1ca-297">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-297">Int16</span></span>|
|<span data-ttu-id="2a1ca-298">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-298">REMARKS</span></span>|<span data-ttu-id="2a1ca-299">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-299">String</span></span>|
|<span data-ttu-id="2a1ca-300">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2a1ca-300">COLUMN_DEF</span></span>|<span data-ttu-id="2a1ca-301">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-301">String</span></span>|
|<span data-ttu-id="2a1ca-302">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-302">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-303">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-303">Int16</span></span>|
|<span data-ttu-id="2a1ca-304">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2a1ca-304">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2a1ca-305">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-305">Int16</span></span>|
|<span data-ttu-id="2a1ca-306">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-306">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2a1ca-307">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-307">Int32</span></span>|
|<span data-ttu-id="2a1ca-308">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-308">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-309">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-309">Int32</span></span>|
|<span data-ttu-id="2a1ca-310">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-310">IS_NULLABLE</span></span>|<span data-ttu-id="2a1ca-311">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-311">String</span></span>|
|<span data-ttu-id="2a1ca-312">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2a1ca-312">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2a1ca-313">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-313">String</span></span>|
|<span data-ttu-id="2a1ca-314">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2a1ca-314">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2a1ca-315">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-315">String</span></span>|
|<span data-ttu-id="2a1ca-316">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-316">SS_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-317">Byte</span><span class="sxs-lookup"><span data-stu-id="2a1ca-317">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="2a1ca-318">Драйвер ODBC для Oracle (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="2a1ca-318">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="2a1ca-319">Драйвер Microsoft SQL Server ODBC для Oracle поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="2a1ca-319">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="2a1ca-320">Таблицы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-320">Tables</span></span>

- <span data-ttu-id="2a1ca-321">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-321">Columns</span></span>

- <span data-ttu-id="2a1ca-322">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-322">Procedures</span></span>

- <span data-ttu-id="2a1ca-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-323">ProcedureColumns</span></span>

- <span data-ttu-id="2a1ca-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2a1ca-324">ProcedureParameters</span></span>

- <span data-ttu-id="2a1ca-325">Представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-325">Views</span></span>

- <span data-ttu-id="2a1ca-326">Индексы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-326">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="2a1ca-327">Таблицы и представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-327">Tables and Views</span></span>

|<span data-ttu-id="2a1ca-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-328">ColumnName</span></span>|<span data-ttu-id="2a1ca-329">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-329">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-330">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-330">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-331">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-331">String</span></span>|
|<span data-ttu-id="2a1ca-332">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-332">TABLE_OWNER</span></span>|<span data-ttu-id="2a1ca-333">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-333">String</span></span>|
|<span data-ttu-id="2a1ca-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-334">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-335">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-335">String</span></span>|
|<span data-ttu-id="2a1ca-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-336">TABLE_TYPE</span></span>|<span data-ttu-id="2a1ca-337">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-337">String</span></span>|
|<span data-ttu-id="2a1ca-338">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-338">REMARKS</span></span>|<span data-ttu-id="2a1ca-339">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-339">String</span></span>|

### <a name="columns"></a><span data-ttu-id="2a1ca-340">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-340">Columns</span></span>

|<span data-ttu-id="2a1ca-341">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-341">ColumnName</span></span>|<span data-ttu-id="2a1ca-342">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-342">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-343">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-343">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-344">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-344">String</span></span>|
|<span data-ttu-id="2a1ca-345">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-345">TABLE_OWNER</span></span>|<span data-ttu-id="2a1ca-346">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-346">String</span></span>|
|<span data-ttu-id="2a1ca-347">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-347">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-348">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-348">String</span></span>|
|<span data-ttu-id="2a1ca-349">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-349">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-350">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-350">String</span></span>|
|<span data-ttu-id="2a1ca-351">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-351">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-352">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-352">Int16</span></span>|
|<span data-ttu-id="2a1ca-353">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-353">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-354">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-354">String</span></span>|
|<span data-ttu-id="2a1ca-355">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-355">PRECISION</span></span>|<span data-ttu-id="2a1ca-356">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-356">Int32</span></span>|
|<span data-ttu-id="2a1ca-357">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-357">LENGTH</span></span>|<span data-ttu-id="2a1ca-358">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-358">Int32</span></span>|
|<span data-ttu-id="2a1ca-359">SCALE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-359">SCALE</span></span>|<span data-ttu-id="2a1ca-360">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-360">Int16</span></span>|
|<span data-ttu-id="2a1ca-361">RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-361">RADIX</span></span>|<span data-ttu-id="2a1ca-362">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-362">Int16</span></span>|
|<span data-ttu-id="2a1ca-363">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-363">NULLABLE</span></span>|<span data-ttu-id="2a1ca-364">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-364">Int16</span></span>|
|<span data-ttu-id="2a1ca-365">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-365">REMARKS</span></span>|<span data-ttu-id="2a1ca-366">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-366">String</span></span>|
|<span data-ttu-id="2a1ca-367">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-367">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-368">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-368">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="2a1ca-369">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-369">Procedures</span></span>

|<span data-ttu-id="2a1ca-370">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-370">ColumnName</span></span>|<span data-ttu-id="2a1ca-371">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-371">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-372">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-372">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-373">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-373">String</span></span>|
|<span data-ttu-id="2a1ca-374">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-374">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2a1ca-375">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-375">String</span></span>|
|<span data-ttu-id="2a1ca-376">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-376">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-377">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-377">String</span></span>|
|<span data-ttu-id="2a1ca-378">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-378">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-379">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-379">Int16</span></span>|
|<span data-ttu-id="2a1ca-380">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-380">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-381">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-381">Int16</span></span>|
|<span data-ttu-id="2a1ca-382">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-382">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2a1ca-383">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-383">Int16</span></span>|
|<span data-ttu-id="2a1ca-384">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-384">REMARKS</span></span>|<span data-ttu-id="2a1ca-385">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-385">String</span></span>|
|<span data-ttu-id="2a1ca-386">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-386">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2a1ca-387">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-387">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="2a1ca-388">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-388">ProcedureColumns</span></span>

|<span data-ttu-id="2a1ca-389">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-389">ColumnName</span></span>|<span data-ttu-id="2a1ca-390">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-390">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-391">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-391">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-392">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-392">String</span></span>|
|<span data-ttu-id="2a1ca-393">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-393">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2a1ca-394">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-394">String</span></span>|
|<span data-ttu-id="2a1ca-395">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-395">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-396">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-396">String</span></span>|
|<span data-ttu-id="2a1ca-397">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-397">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-398">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-398">String</span></span>|
|<span data-ttu-id="2a1ca-399">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-399">COLUMN_TYPE</span></span>|<span data-ttu-id="2a1ca-400">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-400">Int16</span></span>|
|<span data-ttu-id="2a1ca-401">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-401">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-402">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-402">Int16</span></span>|
|<span data-ttu-id="2a1ca-403">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-403">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-404">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-404">String</span></span>|
|<span data-ttu-id="2a1ca-405">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-405">PRECISION</span></span>|<span data-ttu-id="2a1ca-406">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-406">Int32</span></span>|
|<span data-ttu-id="2a1ca-407">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-407">LENGTH</span></span>|<span data-ttu-id="2a1ca-408">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-408">Int32</span></span>|
|<span data-ttu-id="2a1ca-409">SCALE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-409">SCALE</span></span>|<span data-ttu-id="2a1ca-410">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-410">Int16</span></span>|
|<span data-ttu-id="2a1ca-411">RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-411">RADIX</span></span>|<span data-ttu-id="2a1ca-412">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-412">Int16</span></span>|
|<span data-ttu-id="2a1ca-413">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-413">NULLABLE</span></span>|<span data-ttu-id="2a1ca-414">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-414">Int16</span></span>|
|<span data-ttu-id="2a1ca-415">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-415">REMARKS</span></span>|<span data-ttu-id="2a1ca-416">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-416">String</span></span>|
|<span data-ttu-id="2a1ca-417">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="2a1ca-417">OVERLOAD</span></span>|<span data-ttu-id="2a1ca-418">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-418">Int32</span></span>|
|<span data-ttu-id="2a1ca-419">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-419">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-420">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-420">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="2a1ca-421">Драйвер ODBC для Jet (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="2a1ca-421">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="2a1ca-422">Драйвер ODBC для Jet (Майкрософт) поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="2a1ca-422">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="2a1ca-423">Таблицы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-423">Tables</span></span>

- <span data-ttu-id="2a1ca-424">Индексы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-424">Indexes</span></span>

- <span data-ttu-id="2a1ca-425">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-425">Columns</span></span>

- <span data-ttu-id="2a1ca-426">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-426">Procedures</span></span>

- <span data-ttu-id="2a1ca-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-427">ProcedureColumns</span></span>

- <span data-ttu-id="2a1ca-428">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2a1ca-428">ProcedureParameters</span></span>

- <span data-ttu-id="2a1ca-429">Представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-429">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="2a1ca-430">Таблицы и представления</span><span class="sxs-lookup"><span data-stu-id="2a1ca-430">Tables and Views</span></span>

|<span data-ttu-id="2a1ca-431">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-431">ColumnName</span></span>|<span data-ttu-id="2a1ca-432">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-432">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-433">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-433">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-434">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-434">String</span></span>|
|<span data-ttu-id="2a1ca-435">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-435">TABLE_OWNER</span></span>|<span data-ttu-id="2a1ca-436">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-436">String</span></span>|
|<span data-ttu-id="2a1ca-437">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-437">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-438">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-438">String</span></span>|
|<span data-ttu-id="2a1ca-439">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-439">TABLE_TYPE</span></span>|<span data-ttu-id="2a1ca-440">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-440">String</span></span>|
|<span data-ttu-id="2a1ca-441">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-441">REMARKS</span></span>|<span data-ttu-id="2a1ca-442">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-442">String</span></span>|

### <a name="columns"></a><span data-ttu-id="2a1ca-443">Столбцы</span><span class="sxs-lookup"><span data-stu-id="2a1ca-443">Columns</span></span>

|<span data-ttu-id="2a1ca-444">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-444">ColumnName</span></span>|<span data-ttu-id="2a1ca-445">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-445">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-446">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-446">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-447">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-447">String</span></span>|
|<span data-ttu-id="2a1ca-448">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-448">TABLE_OWNER</span></span>|<span data-ttu-id="2a1ca-449">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-449">String</span></span>|
|<span data-ttu-id="2a1ca-450">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-450">TABLE_NAME</span></span>|<span data-ttu-id="2a1ca-451">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-451">String</span></span>|
|<span data-ttu-id="2a1ca-452">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-452">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-453">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-453">String</span></span>|
|<span data-ttu-id="2a1ca-454">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-454">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-455">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-455">Int16</span></span>|
|<span data-ttu-id="2a1ca-456">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-456">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-457">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-457">String</span></span>|
|<span data-ttu-id="2a1ca-458">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-458">PRECISION</span></span>|<span data-ttu-id="2a1ca-459">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-459">Int32</span></span>|
|<span data-ttu-id="2a1ca-460">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-460">LENGTH</span></span>|<span data-ttu-id="2a1ca-461">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-461">Int32</span></span>|
|<span data-ttu-id="2a1ca-462">SCALE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-462">SCALE</span></span>|<span data-ttu-id="2a1ca-463">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-463">Int16</span></span>|
|<span data-ttu-id="2a1ca-464">RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-464">RADIX</span></span>|<span data-ttu-id="2a1ca-465">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-465">Int16</span></span>|
|<span data-ttu-id="2a1ca-466">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-466">NULLABLE</span></span>|<span data-ttu-id="2a1ca-467">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-467">Int16</span></span>|
|<span data-ttu-id="2a1ca-468">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-468">REMARKS</span></span>|<span data-ttu-id="2a1ca-469">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-469">String</span></span>|
|<span data-ttu-id="2a1ca-470">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-470">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-471">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-471">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="2a1ca-472">Процедуры</span><span class="sxs-lookup"><span data-stu-id="2a1ca-472">Procedures</span></span>

|<span data-ttu-id="2a1ca-473">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-473">ColumnName</span></span>|<span data-ttu-id="2a1ca-474">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-474">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-475">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-475">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-476">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-476">String</span></span>|
|<span data-ttu-id="2a1ca-477">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-477">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2a1ca-478">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-478">String</span></span>|
|<span data-ttu-id="2a1ca-479">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-479">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-480">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-480">String</span></span>|
|<span data-ttu-id="2a1ca-481">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-481">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-482">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-482">Int16</span></span>|
|<span data-ttu-id="2a1ca-483">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-483">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2a1ca-484">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-484">Int16</span></span>|
|<span data-ttu-id="2a1ca-485">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-485">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2a1ca-486">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-486">Int16</span></span>|
|<span data-ttu-id="2a1ca-487">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-487">REMARKS</span></span>|<span data-ttu-id="2a1ca-488">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-488">String</span></span>|
|<span data-ttu-id="2a1ca-489">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-489">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2a1ca-490">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-490">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="2a1ca-491">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2a1ca-491">ProcedureColumns</span></span>

|<span data-ttu-id="2a1ca-492">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-492">ColumnName</span></span>|<span data-ttu-id="2a1ca-493">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-493">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-494">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-494">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2a1ca-495">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-495">String</span></span>|
|<span data-ttu-id="2a1ca-496">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1ca-496">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2a1ca-497">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-497">String</span></span>|
|<span data-ttu-id="2a1ca-498">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-498">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-499">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-499">String</span></span>|
|<span data-ttu-id="2a1ca-500">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-500">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-501">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-501">String</span></span>|
|<span data-ttu-id="2a1ca-502">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-502">COLUMN_TYPE</span></span>|<span data-ttu-id="2a1ca-503">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-503">Int16</span></span>|
|<span data-ttu-id="2a1ca-504">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-504">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-505">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-505">Int16</span></span>|
|<span data-ttu-id="2a1ca-506">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-506">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-507">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-507">String</span></span>|
|<span data-ttu-id="2a1ca-508">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-508">PRECISION</span></span>|<span data-ttu-id="2a1ca-509">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-509">Int32</span></span>|
|<span data-ttu-id="2a1ca-510">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-510">LENGTH</span></span>|<span data-ttu-id="2a1ca-511">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-511">Int32</span></span>|
|<span data-ttu-id="2a1ca-512">SCALE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-512">SCALE</span></span>|<span data-ttu-id="2a1ca-513">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-513">Int16</span></span>|
|<span data-ttu-id="2a1ca-514">RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-514">RADIX</span></span>|<span data-ttu-id="2a1ca-515">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-515">Int16</span></span>|
|<span data-ttu-id="2a1ca-516">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-516">NULLABLE</span></span>|<span data-ttu-id="2a1ca-517">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-517">Int16</span></span>|
|<span data-ttu-id="2a1ca-518">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-518">REMARKS</span></span>|<span data-ttu-id="2a1ca-519">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-519">String</span></span>|
|<span data-ttu-id="2a1ca-520">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="2a1ca-520">OVERLOAD</span></span>|<span data-ttu-id="2a1ca-521">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-521">Int32</span></span>|
|<span data-ttu-id="2a1ca-522">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-522">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-523">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-523">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="2a1ca-524">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2a1ca-524">ProcedureParameters</span></span>

|<span data-ttu-id="2a1ca-525">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2a1ca-525">ColumnName</span></span>|<span data-ttu-id="2a1ca-526">DataType</span><span class="sxs-lookup"><span data-stu-id="2a1ca-526">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="2a1ca-527">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2a1ca-527">PROCEDURE_CAT</span></span>|<span data-ttu-id="2a1ca-528">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-528">String</span></span>|
|<span data-ttu-id="2a1ca-529">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2a1ca-529">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2a1ca-530">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-530">String</span></span>|
|<span data-ttu-id="2a1ca-531">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-531">PROCEDURE_NAME</span></span>|<span data-ttu-id="2a1ca-532">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-532">String</span></span>|
|<span data-ttu-id="2a1ca-533">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-533">COLUMN_NAME</span></span>|<span data-ttu-id="2a1ca-534">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-534">String</span></span>|
|<span data-ttu-id="2a1ca-535">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-535">COLUMN_TYPE</span></span>|<span data-ttu-id="2a1ca-536">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-536">Int16</span></span>|
|<span data-ttu-id="2a1ca-537">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-537">DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-538">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-538">Int16</span></span>|
|<span data-ttu-id="2a1ca-539">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2a1ca-539">TYPE_NAME</span></span>|<span data-ttu-id="2a1ca-540">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-540">String</span></span>|
|<span data-ttu-id="2a1ca-541">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-541">COLUMN_SIZE</span></span>|<span data-ttu-id="2a1ca-542">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-542">Int32</span></span>|
|<span data-ttu-id="2a1ca-543">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-543">BUFFER_LENGTH</span></span>|<span data-ttu-id="2a1ca-544">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-544">Int32</span></span>|
|<span data-ttu-id="2a1ca-545">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2a1ca-545">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2a1ca-546">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-546">Int16</span></span>|
|<span data-ttu-id="2a1ca-547">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2a1ca-547">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2a1ca-548">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-548">Int16</span></span>|
|<span data-ttu-id="2a1ca-549">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-549">NULLABLE</span></span>|<span data-ttu-id="2a1ca-550">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-550">Int16</span></span>|
|<span data-ttu-id="2a1ca-551">ПРИМЕЧАНИЯ</span><span class="sxs-lookup"><span data-stu-id="2a1ca-551">REMARKS</span></span>|<span data-ttu-id="2a1ca-552">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-552">String</span></span>|
|<span data-ttu-id="2a1ca-553">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2a1ca-553">COLUMN_DEF</span></span>|<span data-ttu-id="2a1ca-554">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-554">String</span></span>|
|<span data-ttu-id="2a1ca-555">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-555">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2a1ca-556">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-556">Int16</span></span>|
|<span data-ttu-id="2a1ca-557">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2a1ca-557">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2a1ca-558">Int16</span><span class="sxs-lookup"><span data-stu-id="2a1ca-558">Int16</span></span>|
|<span data-ttu-id="2a1ca-559">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2a1ca-559">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2a1ca-560">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-560">Int32</span></span>|
|<span data-ttu-id="2a1ca-561">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2a1ca-561">ORDINAL_POSITION</span></span>|<span data-ttu-id="2a1ca-562">Int32</span><span class="sxs-lookup"><span data-stu-id="2a1ca-562">Int32</span></span>|
|<span data-ttu-id="2a1ca-563">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2a1ca-563">IS_NULLABLE</span></span>|<span data-ttu-id="2a1ca-564">Строка</span><span class="sxs-lookup"><span data-stu-id="2a1ca-564">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="2a1ca-565">См. также</span><span class="sxs-lookup"><span data-stu-id="2a1ca-565">See also</span></span>

- [<span data-ttu-id="2a1ca-566">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a1ca-566">ADO.NET Overview</span></span>](ado-net-overview.md)
