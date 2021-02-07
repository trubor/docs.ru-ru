---
description: 'Дополнительные сведения: OLE DB коллекции схем'
title: Коллекции схемы OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: d4d4bae5387575bdaeaf013ed690e95aa3259068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672625"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="19601-103">Коллекции схемы OLE DB</span><span class="sxs-lookup"><span data-stu-id="19601-103">OLE DB Schema Collections</span></span>

<span data-ttu-id="19601-104">В данном разделе рассматривается поддержка коллекций схем для поставщиков OLE DB для Microsoft SQL Server, Oracle и Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="19601-104">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="19601-105">Поставщик OLE DB для Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="19601-105">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="19601-106">Драйвер OLE DB для Microsoft SQL Server поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="19601-106">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="19601-107">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-107">Tables</span></span>  
  
- <span data-ttu-id="19601-108">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-108">Columns</span></span>  
  
- <span data-ttu-id="19601-109">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-109">Procedures</span></span>  
  
- <span data-ttu-id="19601-110">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="19601-110">ProcedureParameters</span></span>  
  
- <span data-ttu-id="19601-111">Каталог</span><span class="sxs-lookup"><span data-stu-id="19601-111">Catalog</span></span>  
  
- <span data-ttu-id="19601-112">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-112">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="19601-113">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-113">Tables</span></span>  
  
|<span data-ttu-id="19601-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-114">ColumnName</span></span>|<span data-ttu-id="19601-115">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-116">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-117">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-117">String</span></span>|  
|<span data-ttu-id="19601-118">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-118">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-119">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-119">String</span></span>|  
|<span data-ttu-id="19601-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-120">TABLE_NAME</span></span>|<span data-ttu-id="19601-121">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-121">String</span></span>|  
|<span data-ttu-id="19601-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-122">TABLE_TYPE</span></span>|<span data-ttu-id="19601-123">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-123">String</span></span>|  
|<span data-ttu-id="19601-124">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-124">TABLE_GUID</span></span>|<span data-ttu-id="19601-125">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-125">Guid</span></span>|  
|<span data-ttu-id="19601-126">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-126">DESCRIPTION</span></span>|<span data-ttu-id="19601-127">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-127">String</span></span>|  
|<span data-ttu-id="19601-128">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-128">TABLE_PROPID</span></span>|<span data-ttu-id="19601-129">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-129">Int64</span></span>|  
|<span data-ttu-id="19601-130">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-130">DATE_CREATED</span></span>|<span data-ttu-id="19601-131">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-131">DateTime</span></span>|  
|<span data-ttu-id="19601-132">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-132">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-133">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-133">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="19601-134">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-134">Columns</span></span>  
  
|<span data-ttu-id="19601-135">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-135">ColumnName</span></span>|<span data-ttu-id="19601-136">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-136">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-137">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-137">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-138">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-138">String</span></span>|  
|<span data-ttu-id="19601-139">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-139">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-140">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-140">String</span></span>|  
|<span data-ttu-id="19601-141">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-141">TABLE_NAME</span></span>|<span data-ttu-id="19601-142">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-142">String</span></span>|  
|<span data-ttu-id="19601-143">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-143">COLUMN_NAME</span></span>|<span data-ttu-id="19601-144">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-144">String</span></span>|  
|<span data-ttu-id="19601-145">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-145">COLUMN_GUID</span></span>|<span data-ttu-id="19601-146">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-146">Guid</span></span>|  
|<span data-ttu-id="19601-147">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-147">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-148">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-148">Int64</span></span>|  
|<span data-ttu-id="19601-149">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-149">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-150">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-150">Int64</span></span>|  
|<span data-ttu-id="19601-151">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-151">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="19601-152">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-152">Boolean</span></span>|  
|<span data-ttu-id="19601-153">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-153">COLUMN_DEFAULT</span></span>|<span data-ttu-id="19601-154">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-154">String</span></span>|  
|<span data-ttu-id="19601-155">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="19601-155">COLUMN_FLAGS</span></span>|<span data-ttu-id="19601-156">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-156">Int64</span></span>|  
|<span data-ttu-id="19601-157">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="19601-157">IS_NULLABLE</span></span>|<span data-ttu-id="19601-158">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-158">Boolean</span></span>|  
|<span data-ttu-id="19601-159">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-159">DATA_TYPE</span></span>|<span data-ttu-id="19601-160">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-160">Int32</span></span>|  
|<span data-ttu-id="19601-161">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-161">TYPE_GUID</span></span>|<span data-ttu-id="19601-162">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-162">Guid</span></span>|  
|<span data-ttu-id="19601-163">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-163">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="19601-164">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-164">Int64</span></span>|  
|<span data-ttu-id="19601-165">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-165">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="19601-166">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-166">Int64</span></span>|  
|<span data-ttu-id="19601-167">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-167">NUMERIC_PRECISION</span></span>|<span data-ttu-id="19601-168">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-168">Int32</span></span>|  
|<span data-ttu-id="19601-169">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="19601-169">NUMERIC_SCALE</span></span>|<span data-ttu-id="19601-170">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-170">Int16</span></span>|  
|<span data-ttu-id="19601-171">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-171">DATETIME_PRECISION</span></span>|<span data-ttu-id="19601-172">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-172">Int64</span></span>|  
|<span data-ttu-id="19601-173">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-173">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="19601-174">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-174">String</span></span>|  
|<span data-ttu-id="19601-175">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-175">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="19601-176">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-176">String</span></span>|  
|<span data-ttu-id="19601-177">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-177">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="19601-178">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-178">String</span></span>|  
|<span data-ttu-id="19601-179">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-179">COLLATION_CATALOG</span></span>|<span data-ttu-id="19601-180">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-180">String</span></span>|  
|<span data-ttu-id="19601-181">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-181">COLLATION_SCHEMA</span></span>|<span data-ttu-id="19601-182">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-182">String</span></span>|  
|<span data-ttu-id="19601-183">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-183">COLLATION_NAME</span></span>|<span data-ttu-id="19601-184">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-184">String</span></span>|  
|<span data-ttu-id="19601-185">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-185">DOMAIN_CATALOG</span></span>|<span data-ttu-id="19601-186">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-186">String</span></span>|  
|<span data-ttu-id="19601-187">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-187">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="19601-188">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-188">String</span></span>|  
|<span data-ttu-id="19601-189">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-189">DOMAIN_NAME</span></span>|<span data-ttu-id="19601-190">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-190">String</span></span>|  
|<span data-ttu-id="19601-191">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-191">DESCRIPTION</span></span>|<span data-ttu-id="19601-192">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-192">String</span></span>|  
|<span data-ttu-id="19601-193">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="19601-193">COLUMN_LCID</span></span>|<span data-ttu-id="19601-194">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-194">Int32</span></span>|  
|<span data-ttu-id="19601-195">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="19601-195">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="19601-196">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-196">Int32</span></span>|  
|<span data-ttu-id="19601-197">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="19601-197">COLUMN_SORTID</span></span>|<span data-ttu-id="19601-198">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-198">Int32</span></span>|  
|<span data-ttu-id="19601-199">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-199">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="19601-200">Byte[]</span><span class="sxs-lookup"><span data-stu-id="19601-200">Byte[]</span></span>|  
|<span data-ttu-id="19601-201">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="19601-201">IS_COMPUTED</span></span>|<span data-ttu-id="19601-202">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-202">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="19601-203">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-203">Procedures</span></span>  
  
|<span data-ttu-id="19601-204">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-204">ColumnName</span></span>|<span data-ttu-id="19601-205">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-205">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-206">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-206">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="19601-207">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-207">String</span></span>|  
|<span data-ttu-id="19601-208">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-208">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="19601-209">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-209">String</span></span>|  
|<span data-ttu-id="19601-210">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-210">PROCEDURE_NAME</span></span>|<span data-ttu-id="19601-211">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-211">String</span></span>|  
|<span data-ttu-id="19601-212">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-212">PROCEDURE_TYPE</span></span>|<span data-ttu-id="19601-213">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-213">Int16</span></span>|  
|<span data-ttu-id="19601-214">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="19601-214">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="19601-215">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-215">String</span></span>|  
|<span data-ttu-id="19601-216">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-216">DESCRIPTION</span></span>|<span data-ttu-id="19601-217">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-217">String</span></span>|  
|<span data-ttu-id="19601-218">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-218">DATE_CREATED</span></span>|<span data-ttu-id="19601-219">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-219">DateTime</span></span>|  
|<span data-ttu-id="19601-220">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-220">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-221">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-221">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="19601-222">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="19601-222">ProcedureParameters</span></span>  
  
|<span data-ttu-id="19601-223">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-223">ColumnName</span></span>|<span data-ttu-id="19601-224">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-224">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-225">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-225">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="19601-226">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-226">String</span></span>|  
|<span data-ttu-id="19601-227">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-227">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="19601-228">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-228">String</span></span>|  
|<span data-ttu-id="19601-229">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-229">PROCEDURE_NAME</span></span>|<span data-ttu-id="19601-230">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-230">String</span></span>|  
|<span data-ttu-id="19601-231">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-231">PARAMETER_NAME</span></span>|<span data-ttu-id="19601-232">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-232">String</span></span>|  
|<span data-ttu-id="19601-233">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-233">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-234">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-234">Int32</span></span>|  
|<span data-ttu-id="19601-235">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-235">PARAMETER_TYPE</span></span>|<span data-ttu-id="19601-236">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-236">Int32</span></span>|  
|<span data-ttu-id="19601-237">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-237">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="19601-238">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-238">Boolean</span></span>|  
|<span data-ttu-id="19601-239">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-239">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="19601-240">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-240">String</span></span>|  
|<span data-ttu-id="19601-241">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="19601-241">IS_NULLABLE</span></span>|<span data-ttu-id="19601-242">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-242">Boolean</span></span>|  
|<span data-ttu-id="19601-243">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-243">DATA_TYPE</span></span>|<span data-ttu-id="19601-244">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-244">Int32</span></span>|  
|<span data-ttu-id="19601-245">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-245">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="19601-246">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-246">Int64</span></span>|  
|<span data-ttu-id="19601-247">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-247">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="19601-248">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-248">Int64</span></span>|  
|<span data-ttu-id="19601-249">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-249">NUMERIC_PRECISION</span></span>|<span data-ttu-id="19601-250">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-250">Int32</span></span>|  
|<span data-ttu-id="19601-251">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="19601-251">NUMERIC_SCALE</span></span>|<span data-ttu-id="19601-252">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-252">Int16</span></span>|  
|<span data-ttu-id="19601-253">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-253">DESCRIPTION</span></span>|<span data-ttu-id="19601-254">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-254">String</span></span>|  
|<span data-ttu-id="19601-255">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-255">TYPE_NAME</span></span>|<span data-ttu-id="19601-256">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-256">String</span></span>|  
|<span data-ttu-id="19601-257">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-257">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="19601-258">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-258">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="19601-259">Каталог</span><span class="sxs-lookup"><span data-stu-id="19601-259">Catalog</span></span>  
  
|<span data-ttu-id="19601-260">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-260">ColumnName</span></span>|<span data-ttu-id="19601-261">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-261">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-262">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-262">CATALOG_NAME</span></span>|<span data-ttu-id="19601-263">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-263">String</span></span>|  
|<span data-ttu-id="19601-264">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-264">DESCRIPTION</span></span>|<span data-ttu-id="19601-265">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-265">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="19601-266">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-266">Indexes</span></span>  
  
|<span data-ttu-id="19601-267">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-267">ColumnName</span></span>|<span data-ttu-id="19601-268">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-268">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-269">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-269">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-270">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-270">String</span></span>|  
|<span data-ttu-id="19601-271">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-271">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-272">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-272">String</span></span>|  
|<span data-ttu-id="19601-273">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-273">TABLE_NAME</span></span>|<span data-ttu-id="19601-274">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-274">String</span></span>|  
|<span data-ttu-id="19601-275">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-275">INDEX_CATALOG</span></span>|<span data-ttu-id="19601-276">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-276">String</span></span>|  
|<span data-ttu-id="19601-277">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-277">INDEX_SCHEMA</span></span>|<span data-ttu-id="19601-278">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-278">String</span></span>|  
|<span data-ttu-id="19601-279">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-279">INDEX_NAME</span></span>|<span data-ttu-id="19601-280">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-280">String</span></span>|  
|<span data-ttu-id="19601-281">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="19601-281">PRIMARY_KEY</span></span>|<span data-ttu-id="19601-282">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-282">Boolean</span></span>|  
|<span data-ttu-id="19601-283">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="19601-283">UNIQUE</span></span>|<span data-ttu-id="19601-284">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-284">Boolean</span></span>|  
|<span data-ttu-id="19601-285">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="19601-285">CLUSTERED</span></span>|<span data-ttu-id="19601-286">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-286">Boolean</span></span>|  
|<span data-ttu-id="19601-287">TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-287">TYPE</span></span>|<span data-ttu-id="19601-288">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-288">Int32</span></span>|  
|<span data-ttu-id="19601-289">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="19601-289">FILL_FACTOR</span></span>|<span data-ttu-id="19601-290">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-290">Int32</span></span>|  
|<span data-ttu-id="19601-291">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="19601-291">INITIAL_SIZE</span></span>|<span data-ttu-id="19601-292">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-292">Int32</span></span>|  
|<span data-ttu-id="19601-293">NULLS</span><span class="sxs-lookup"><span data-stu-id="19601-293">NULLS</span></span>|<span data-ttu-id="19601-294">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-294">Int32</span></span>|  
|<span data-ttu-id="19601-295">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="19601-295">SORT_BOOKMARKS</span></span>|<span data-ttu-id="19601-296">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-296">Boolean</span></span>|  
|<span data-ttu-id="19601-297">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="19601-297">AUTO_UPDATE</span></span>|<span data-ttu-id="19601-298">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-298">Boolean</span></span>|  
|<span data-ttu-id="19601-299">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-299">NULL_COLLATION</span></span>|<span data-ttu-id="19601-300">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-300">Int32</span></span>|  
|<span data-ttu-id="19601-301">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-301">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-302">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-302">Int64</span></span>|  
|<span data-ttu-id="19601-303">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-303">COLUMN_NAME</span></span>|<span data-ttu-id="19601-304">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-304">String</span></span>|  
|<span data-ttu-id="19601-305">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-305">COLUMN_GUID</span></span>|<span data-ttu-id="19601-306">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-306">Guid</span></span>|  
|<span data-ttu-id="19601-307">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-307">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-308">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-308">Int64</span></span>|  
|<span data-ttu-id="19601-309">COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-309">COLLATION</span></span>|<span data-ttu-id="19601-310">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-310">Int16</span></span>|  
|<span data-ttu-id="19601-311">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="19601-311">CARDINALITY</span></span>|<span data-ttu-id="19601-312">Decimal</span><span class="sxs-lookup"><span data-stu-id="19601-312">Decimal</span></span>|  
|<span data-ttu-id="19601-313">PAGES</span><span class="sxs-lookup"><span data-stu-id="19601-313">PAGES</span></span>|<span data-ttu-id="19601-314">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-314">Int32</span></span>|  
|<span data-ttu-id="19601-315">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="19601-315">FILTER_CONDITION</span></span>|<span data-ttu-id="19601-316">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-316">String</span></span>|  
|<span data-ttu-id="19601-317">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="19601-317">INTEGRATED</span></span>|<span data-ttu-id="19601-318">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-318">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="19601-319">Поставщик Microsoft OLE DB для Oracle</span><span class="sxs-lookup"><span data-stu-id="19601-319">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="19601-320">Драйвер OLE DB для Oracle (Майкрософт) поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="19601-320">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="19601-321">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-321">Tables</span></span>  
  
- <span data-ttu-id="19601-322">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-322">Columns</span></span>  
  
- <span data-ttu-id="19601-323">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-323">Procedures</span></span>  
  
- <span data-ttu-id="19601-324">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="19601-324">ProcedureColumns</span></span>  
  
- <span data-ttu-id="19601-325">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="19601-325">ProcedureParameters</span></span>  
  
- <span data-ttu-id="19601-326">Представления</span><span class="sxs-lookup"><span data-stu-id="19601-326">Views</span></span>  
  
- <span data-ttu-id="19601-327">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-327">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="19601-328">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-328">Tables</span></span>  
  
|<span data-ttu-id="19601-329">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-329">ColumnName</span></span>|<span data-ttu-id="19601-330">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-330">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-331">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-331">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-332">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-332">String</span></span>|  
|<span data-ttu-id="19601-333">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-333">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-334">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-334">String</span></span>|  
|<span data-ttu-id="19601-335">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-335">TABLE_NAME</span></span>|<span data-ttu-id="19601-336">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-336">String</span></span>|  
|<span data-ttu-id="19601-337">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-337">TABLE_TYPE</span></span>|<span data-ttu-id="19601-338">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-338">String</span></span>|  
|<span data-ttu-id="19601-339">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-339">TABLE_GUID</span></span>|<span data-ttu-id="19601-340">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-340">Guid</span></span>|  
|<span data-ttu-id="19601-341">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-341">DESCRIPTION</span></span>|<span data-ttu-id="19601-342">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-342">String</span></span>|  
|<span data-ttu-id="19601-343">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-343">TABLE_PROPID</span></span>|<span data-ttu-id="19601-344">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-344">Int64</span></span>|  
|<span data-ttu-id="19601-345">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-345">DATE_CREATED</span></span>|<span data-ttu-id="19601-346">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-346">DateTime</span></span>|  
|<span data-ttu-id="19601-347">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-347">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-348">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-348">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="19601-349">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-349">Columns</span></span>  
  
|<span data-ttu-id="19601-350">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-350">ColumnName</span></span>|<span data-ttu-id="19601-351">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-351">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-352">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-352">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-353">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-353">String</span></span>|  
|<span data-ttu-id="19601-354">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-354">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-355">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-355">String</span></span>|  
|<span data-ttu-id="19601-356">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-356">TABLE_NAME</span></span>|<span data-ttu-id="19601-357">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-357">String</span></span>|  
|<span data-ttu-id="19601-358">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-358">COLUMN_NAME</span></span>|<span data-ttu-id="19601-359">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-359">String</span></span>|  
|<span data-ttu-id="19601-360">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-360">COLUMN_GUID</span></span>|<span data-ttu-id="19601-361">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-361">Guid</span></span>|  
|<span data-ttu-id="19601-362">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-362">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-363">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-363">Int64</span></span>|  
|<span data-ttu-id="19601-364">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-364">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-365">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-365">Int64</span></span>|  
|<span data-ttu-id="19601-366">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-366">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="19601-367">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-367">Boolean</span></span>|  
|<span data-ttu-id="19601-368">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-368">COLUMN_DEFAULT</span></span>|<span data-ttu-id="19601-369">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-369">String</span></span>|  
|<span data-ttu-id="19601-370">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="19601-370">COLUMN_FLAGS</span></span>|<span data-ttu-id="19601-371">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-371">Int64</span></span>|  
|<span data-ttu-id="19601-372">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="19601-372">IS_NULLABLE</span></span>|<span data-ttu-id="19601-373">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-373">Boolean</span></span>|  
|<span data-ttu-id="19601-374">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-374">DATA_TYPE</span></span>|<span data-ttu-id="19601-375">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-375">Int32</span></span>|  
|<span data-ttu-id="19601-376">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-376">TYPE_GUID</span></span>|<span data-ttu-id="19601-377">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-377">Guid</span></span>|  
|<span data-ttu-id="19601-378">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-378">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="19601-379">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-379">Int64</span></span>|  
|<span data-ttu-id="19601-380">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-380">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="19601-381">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-381">Int64</span></span>|  
|<span data-ttu-id="19601-382">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-382">NUMERIC_PRECISION</span></span>|<span data-ttu-id="19601-383">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-383">Int32</span></span>|  
|<span data-ttu-id="19601-384">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="19601-384">NUMERIC_SCALE</span></span>|<span data-ttu-id="19601-385">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-385">Int16</span></span>|  
|<span data-ttu-id="19601-386">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-386">DATETIME_PRECISION</span></span>|<span data-ttu-id="19601-387">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-387">Int64</span></span>|  
|<span data-ttu-id="19601-388">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-388">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="19601-389">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-389">String</span></span>|  
|<span data-ttu-id="19601-390">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-390">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="19601-391">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-391">String</span></span>|  
|<span data-ttu-id="19601-392">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-392">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="19601-393">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-393">String</span></span>|  
|<span data-ttu-id="19601-394">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-394">COLLATION_CATALOG</span></span>|<span data-ttu-id="19601-395">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-395">String</span></span>|  
|<span data-ttu-id="19601-396">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-396">COLLATION_SCHEMA</span></span>|<span data-ttu-id="19601-397">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-397">String</span></span>|  
|<span data-ttu-id="19601-398">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-398">COLLATION_NAME</span></span>|<span data-ttu-id="19601-399">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-399">String</span></span>|  
|<span data-ttu-id="19601-400">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-400">DOMAIN_CATALOG</span></span>|<span data-ttu-id="19601-401">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-401">String</span></span>|  
|<span data-ttu-id="19601-402">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-402">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="19601-403">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-403">String</span></span>|  
|<span data-ttu-id="19601-404">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-404">DOMAIN_NAME</span></span>|<span data-ttu-id="19601-405">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-405">String</span></span>|  
|<span data-ttu-id="19601-406">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-406">DESCRIPTION</span></span>|<span data-ttu-id="19601-407">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-407">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="19601-408">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-408">Procedures</span></span>  
  
|<span data-ttu-id="19601-409">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-409">ColumnName</span></span>|<span data-ttu-id="19601-410">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-410">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-411">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-411">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="19601-412">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-412">String</span></span>|  
|<span data-ttu-id="19601-413">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-413">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="19601-414">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-414">String</span></span>|  
|<span data-ttu-id="19601-415">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-415">PROCEDURE_NAME</span></span>|<span data-ttu-id="19601-416">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-416">String</span></span>|  
|<span data-ttu-id="19601-417">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-417">PROCEDURE_TYPE</span></span>|<span data-ttu-id="19601-418">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-418">Int16</span></span>|  
|<span data-ttu-id="19601-419">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="19601-419">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="19601-420">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-420">String</span></span>|  
|<span data-ttu-id="19601-421">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-421">DESCRIPTION</span></span>|<span data-ttu-id="19601-422">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-422">String</span></span>|  
|<span data-ttu-id="19601-423">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-423">DATE_CREATED</span></span>|<span data-ttu-id="19601-424">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-424">DateTime</span></span>|  
|<span data-ttu-id="19601-425">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-425">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-426">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-426">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="19601-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="19601-427">ProcedureColumns</span></span>  
  
|<span data-ttu-id="19601-428">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-428">ColumnName</span></span>|<span data-ttu-id="19601-429">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-429">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-430">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-430">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="19601-431">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-431">String</span></span>|  
|<span data-ttu-id="19601-432">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-432">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="19601-433">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-433">String</span></span>|  
|<span data-ttu-id="19601-434">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-434">PROCEDURE_NAME</span></span>|<span data-ttu-id="19601-435">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-435">String</span></span>|  
|<span data-ttu-id="19601-436">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-436">COLUMN_NAME</span></span>|<span data-ttu-id="19601-437">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-437">String</span></span>|  
|<span data-ttu-id="19601-438">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-438">COLUMN_GUID</span></span>|<span data-ttu-id="19601-439">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-439">Guid</span></span>|  
|<span data-ttu-id="19601-440">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-440">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-441">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-441">Int64</span></span>|  
|<span data-ttu-id="19601-442">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="19601-442">ROWSET_NUMBER</span></span>|<span data-ttu-id="19601-443">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-443">Int64</span></span>|  
|<span data-ttu-id="19601-444">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-444">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-445">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-445">Int64</span></span>|  
|<span data-ttu-id="19601-446">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="19601-446">IS_NULLABLE</span></span>|<span data-ttu-id="19601-447">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-447">Boolean</span></span>|  
|<span data-ttu-id="19601-448">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-448">DATA_TYPE</span></span>|<span data-ttu-id="19601-449">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-449">Int32</span></span>|  
|<span data-ttu-id="19601-450">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-450">TYPE_GUID</span></span>|<span data-ttu-id="19601-451">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-451">Guid</span></span>|  
|<span data-ttu-id="19601-452">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-452">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="19601-453">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-453">Int64</span></span>|  
|<span data-ttu-id="19601-454">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-454">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="19601-455">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-455">Int64</span></span>|  
|<span data-ttu-id="19601-456">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-456">NUMERIC_PRECISION</span></span>|<span data-ttu-id="19601-457">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-457">Int32</span></span>|  
|<span data-ttu-id="19601-458">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="19601-458">NUMERIC_SCALE</span></span>|<span data-ttu-id="19601-459">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-459">Int16</span></span>|  
|<span data-ttu-id="19601-460">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-460">DESCRIPTION</span></span>|<span data-ttu-id="19601-461">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-461">String</span></span>|  
|<span data-ttu-id="19601-462">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="19601-462">OVERLOAD</span></span>|<span data-ttu-id="19601-463">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-463">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="19601-464">Представления</span><span class="sxs-lookup"><span data-stu-id="19601-464">Views</span></span>  
  
|<span data-ttu-id="19601-465">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-465">ColumnName</span></span>|<span data-ttu-id="19601-466">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-466">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-467">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-467">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-468">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-468">String</span></span>|  
|<span data-ttu-id="19601-469">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-469">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-470">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-470">String</span></span>|  
|<span data-ttu-id="19601-471">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-471">TABLE_NAME</span></span>|<span data-ttu-id="19601-472">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-472">String</span></span>|  
|<span data-ttu-id="19601-473">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="19601-473">VIEW_DEFINITION</span></span>|<span data-ttu-id="19601-474">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-474">String</span></span>|  
|<span data-ttu-id="19601-475">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="19601-475">CHECK_OPTION</span></span>|<span data-ttu-id="19601-476">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-476">Boolean</span></span>|  
|<span data-ttu-id="19601-477">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="19601-477">IS_UPDATABLE</span></span>|<span data-ttu-id="19601-478">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-478">Boolean</span></span>|  
|<span data-ttu-id="19601-479">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-479">DESCRIPTION</span></span>|<span data-ttu-id="19601-480">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-480">String</span></span>|  
|<span data-ttu-id="19601-481">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-481">DATE_CREATED</span></span>|<span data-ttu-id="19601-482">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-482">DateTime</span></span>|  
|<span data-ttu-id="19601-483">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-483">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-484">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-484">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="19601-485">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-485">Indexes</span></span>  
  
|<span data-ttu-id="19601-486">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-486">ColumnName</span></span>|<span data-ttu-id="19601-487">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-487">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-488">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-488">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-489">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-489">String</span></span>|  
|<span data-ttu-id="19601-490">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-490">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-491">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-491">String</span></span>|  
|<span data-ttu-id="19601-492">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-492">TABLE_NAME</span></span>|<span data-ttu-id="19601-493">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-493">String</span></span>|  
|<span data-ttu-id="19601-494">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-494">INDEX_CATALOG</span></span>|<span data-ttu-id="19601-495">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-495">String</span></span>|  
|<span data-ttu-id="19601-496">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-496">INDEX_SCHEMA</span></span>|<span data-ttu-id="19601-497">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-497">String</span></span>|  
|<span data-ttu-id="19601-498">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-498">INDEX_NAME</span></span>|<span data-ttu-id="19601-499">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-499">String</span></span>|  
|<span data-ttu-id="19601-500">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="19601-500">PRIMARY_KEY</span></span>|<span data-ttu-id="19601-501">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-501">Boolean</span></span>|  
|<span data-ttu-id="19601-502">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="19601-502">UNIQUE</span></span>|<span data-ttu-id="19601-503">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-503">Boolean</span></span>|  
|<span data-ttu-id="19601-504">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="19601-504">CLUSTERED</span></span>|<span data-ttu-id="19601-505">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-505">Boolean</span></span>|  
|<span data-ttu-id="19601-506">TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-506">TYPE</span></span>|<span data-ttu-id="19601-507">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-507">Int32</span></span>|  
|<span data-ttu-id="19601-508">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="19601-508">FILL_FACTOR</span></span>|<span data-ttu-id="19601-509">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-509">Int32</span></span>|  
|<span data-ttu-id="19601-510">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="19601-510">INITIAL_SIZE</span></span>|<span data-ttu-id="19601-511">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-511">Int32</span></span>|  
|<span data-ttu-id="19601-512">NULLS</span><span class="sxs-lookup"><span data-stu-id="19601-512">NULLS</span></span>|<span data-ttu-id="19601-513">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-513">Int32</span></span>|  
|<span data-ttu-id="19601-514">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="19601-514">SORT_BOOKMARKS</span></span>|<span data-ttu-id="19601-515">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-515">Boolean</span></span>|  
|<span data-ttu-id="19601-516">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="19601-516">AUTO_UPDATE</span></span>|<span data-ttu-id="19601-517">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-517">Boolean</span></span>|  
|<span data-ttu-id="19601-518">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-518">NULL_COLLATION</span></span>|<span data-ttu-id="19601-519">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-519">Int32</span></span>|  
|<span data-ttu-id="19601-520">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-520">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-521">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-521">Int64</span></span>|  
|<span data-ttu-id="19601-522">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-522">COLUMN_NAME</span></span>|<span data-ttu-id="19601-523">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-523">String</span></span>|  
|<span data-ttu-id="19601-524">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-524">COLUMN_GUID</span></span>|<span data-ttu-id="19601-525">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-525">Guid</span></span>|  
|<span data-ttu-id="19601-526">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-526">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-527">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-527">Int64</span></span>|  
|<span data-ttu-id="19601-528">COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-528">COLLATION</span></span>|<span data-ttu-id="19601-529">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-529">Int16</span></span>|  
|<span data-ttu-id="19601-530">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="19601-530">CARDINALITY</span></span>|<span data-ttu-id="19601-531">Decimal</span><span class="sxs-lookup"><span data-stu-id="19601-531">Decimal</span></span>|  
|<span data-ttu-id="19601-532">PAGES</span><span class="sxs-lookup"><span data-stu-id="19601-532">PAGES</span></span>|<span data-ttu-id="19601-533">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-533">Int32</span></span>|  
|<span data-ttu-id="19601-534">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="19601-534">FILTER_CONDITION</span></span>|<span data-ttu-id="19601-535">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-535">String</span></span>|  
|<span data-ttu-id="19601-536">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="19601-536">INTEGRATED</span></span>|<span data-ttu-id="19601-537">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-537">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="19601-538">Поставщик OLE DB для Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="19601-538">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="19601-539">Драйвер OLE DB для Jet (Майкрософт) поддерживает следующие специальные коллекции схем в дополнение к общим коллекциям.</span><span class="sxs-lookup"><span data-stu-id="19601-539">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="19601-540">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-540">Tables</span></span>  
  
- <span data-ttu-id="19601-541">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-541">Columns</span></span>  
  
- <span data-ttu-id="19601-542">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-542">Procedures</span></span>  
  
- <span data-ttu-id="19601-543">Представления</span><span class="sxs-lookup"><span data-stu-id="19601-543">Views</span></span>  
  
- <span data-ttu-id="19601-544">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-544">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="19601-545">Таблицы</span><span class="sxs-lookup"><span data-stu-id="19601-545">Tables</span></span>  
  
|<span data-ttu-id="19601-546">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-546">ColumnName</span></span>|<span data-ttu-id="19601-547">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-547">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-548">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-548">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-549">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-549">String</span></span>|  
|<span data-ttu-id="19601-550">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-550">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-551">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-551">String</span></span>|  
|<span data-ttu-id="19601-552">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-552">TABLE_NAME</span></span>|<span data-ttu-id="19601-553">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-553">String</span></span>|  
|<span data-ttu-id="19601-554">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-554">TABLE_TYPE</span></span>|<span data-ttu-id="19601-555">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-555">String</span></span>|  
|<span data-ttu-id="19601-556">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-556">TABLE_GUID</span></span>|<span data-ttu-id="19601-557">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-557">Guid</span></span>|  
|<span data-ttu-id="19601-558">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-558">DESCRIPTION</span></span>|<span data-ttu-id="19601-559">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-559">String</span></span>|  
|<span data-ttu-id="19601-560">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-560">TABLE_PROPID</span></span>|<span data-ttu-id="19601-561">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-561">Int64</span></span>|  
|<span data-ttu-id="19601-562">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-562">DATE_CREATED</span></span>|<span data-ttu-id="19601-563">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-563">DateTime</span></span>|  
|<span data-ttu-id="19601-564">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-564">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-565">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-565">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="19601-566">Столбцы</span><span class="sxs-lookup"><span data-stu-id="19601-566">Columns</span></span>  
  
|<span data-ttu-id="19601-567">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-567">ColumnName</span></span>|<span data-ttu-id="19601-568">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-568">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-569">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-569">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-570">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-570">String</span></span>|  
|<span data-ttu-id="19601-571">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-571">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-572">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-572">String</span></span>|  
|<span data-ttu-id="19601-573">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-573">TABLE_NAME</span></span>|<span data-ttu-id="19601-574">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-574">String</span></span>|  
|<span data-ttu-id="19601-575">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-575">COLUMN_NAME</span></span>|<span data-ttu-id="19601-576">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-576">String</span></span>|  
|<span data-ttu-id="19601-577">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-577">COLUMN_GUID</span></span>|<span data-ttu-id="19601-578">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-578">Guid</span></span>|  
|<span data-ttu-id="19601-579">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-579">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-580">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-580">Int64</span></span>|  
|<span data-ttu-id="19601-581">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-581">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-582">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-582">Int64</span></span>|  
|<span data-ttu-id="19601-583">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-583">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="19601-584">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-584">Boolean</span></span>|  
|<span data-ttu-id="19601-585">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="19601-585">COLUMN_DEFAULT</span></span>|<span data-ttu-id="19601-586">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-586">String</span></span>|  
|<span data-ttu-id="19601-587">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="19601-587">COLUMN_FLAGS</span></span>|<span data-ttu-id="19601-588">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-588">Int64</span></span>|  
|<span data-ttu-id="19601-589">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="19601-589">IS_NULLABLE</span></span>|<span data-ttu-id="19601-590">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-590">Boolean</span></span>|  
|<span data-ttu-id="19601-591">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-591">DATA_TYPE</span></span>|<span data-ttu-id="19601-592">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-592">Int32</span></span>|  
|<span data-ttu-id="19601-593">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-593">TYPE_GUID</span></span>|<span data-ttu-id="19601-594">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-594">Guid</span></span>|  
|<span data-ttu-id="19601-595">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-595">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="19601-596">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-596">Int64</span></span>|  
|<span data-ttu-id="19601-597">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="19601-597">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="19601-598">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-598">Int64</span></span>|  
|<span data-ttu-id="19601-599">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-599">NUMERIC_PRECISION</span></span>|<span data-ttu-id="19601-600">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-600">Int32</span></span>|  
|<span data-ttu-id="19601-601">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="19601-601">NUMERIC_SCALE</span></span>|<span data-ttu-id="19601-602">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-602">Int16</span></span>|  
|<span data-ttu-id="19601-603">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="19601-603">DATETIME_PRECISION</span></span>|<span data-ttu-id="19601-604">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-604">Int64</span></span>|  
|<span data-ttu-id="19601-605">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-605">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="19601-606">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-606">String</span></span>|  
|<span data-ttu-id="19601-607">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-607">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="19601-608">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-608">String</span></span>|  
|<span data-ttu-id="19601-609">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-609">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="19601-610">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-610">String</span></span>|  
|<span data-ttu-id="19601-611">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-611">COLLATION_CATALOG</span></span>|<span data-ttu-id="19601-612">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-612">String</span></span>|  
|<span data-ttu-id="19601-613">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-613">COLLATION_SCHEMA</span></span>|<span data-ttu-id="19601-614">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-614">String</span></span>|  
|<span data-ttu-id="19601-615">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-615">COLLATION_NAME</span></span>|<span data-ttu-id="19601-616">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-616">String</span></span>|  
|<span data-ttu-id="19601-617">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-617">DOMAIN_CATALOG</span></span>|<span data-ttu-id="19601-618">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-618">String</span></span>|  
|<span data-ttu-id="19601-619">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-619">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="19601-620">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-620">String</span></span>|  
|<span data-ttu-id="19601-621">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-621">DOMAIN_NAME</span></span>|<span data-ttu-id="19601-622">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-622">String</span></span>|  
|<span data-ttu-id="19601-623">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-623">DESCRIPTION</span></span>|<span data-ttu-id="19601-624">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-624">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="19601-625">Процедуры</span><span class="sxs-lookup"><span data-stu-id="19601-625">Procedures</span></span>  
  
|<span data-ttu-id="19601-626">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-626">ColumnName</span></span>|<span data-ttu-id="19601-627">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-627">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-628">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-628">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="19601-629">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-629">String</span></span>|  
|<span data-ttu-id="19601-630">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-630">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="19601-631">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-631">String</span></span>|  
|<span data-ttu-id="19601-632">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-632">PROCEDURE_NAME</span></span>|<span data-ttu-id="19601-633">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-633">String</span></span>|  
|<span data-ttu-id="19601-634">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-634">PROCEDURE_TYPE</span></span>|<span data-ttu-id="19601-635">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-635">Int16</span></span>|  
|<span data-ttu-id="19601-636">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="19601-636">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="19601-637">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-637">String</span></span>|  
|<span data-ttu-id="19601-638">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-638">DESCRIPTION</span></span>|<span data-ttu-id="19601-639">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-639">String</span></span>|  
|<span data-ttu-id="19601-640">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-640">DATE_CREATED</span></span>|<span data-ttu-id="19601-641">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-641">DateTime</span></span>|  
|<span data-ttu-id="19601-642">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-642">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-643">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-643">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="19601-644">Представления</span><span class="sxs-lookup"><span data-stu-id="19601-644">Views</span></span>  
  
|<span data-ttu-id="19601-645">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-645">ColumnName</span></span>|<span data-ttu-id="19601-646">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-646">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-647">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-647">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-648">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-648">String</span></span>|  
|<span data-ttu-id="19601-649">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-649">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-650">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-650">String</span></span>|  
|<span data-ttu-id="19601-651">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-651">TABLE_NAME</span></span>|<span data-ttu-id="19601-652">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-652">String</span></span>|  
|<span data-ttu-id="19601-653">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="19601-653">VIEW_DEFINITION</span></span>|<span data-ttu-id="19601-654">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-654">String</span></span>|  
|<span data-ttu-id="19601-655">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="19601-655">CHECK_OPTION</span></span>|<span data-ttu-id="19601-656">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-656">Boolean</span></span>|  
|<span data-ttu-id="19601-657">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="19601-657">IS_UPDATABLE</span></span>|<span data-ttu-id="19601-658">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-658">Boolean</span></span>|  
|<span data-ttu-id="19601-659">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="19601-659">DESCRIPTION</span></span>|<span data-ttu-id="19601-660">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-660">String</span></span>|  
|<span data-ttu-id="19601-661">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="19601-661">DATE_CREATED</span></span>|<span data-ttu-id="19601-662">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-662">DateTime</span></span>|  
|<span data-ttu-id="19601-663">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="19601-663">DATE_MODIFIED</span></span>|<span data-ttu-id="19601-664">Дата и время</span><span class="sxs-lookup"><span data-stu-id="19601-664">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="19601-665">Индексы</span><span class="sxs-lookup"><span data-stu-id="19601-665">Indexes</span></span>  
  
|<span data-ttu-id="19601-666">ColumnName</span><span class="sxs-lookup"><span data-stu-id="19601-666">ColumnName</span></span>|<span data-ttu-id="19601-667">DataType</span><span class="sxs-lookup"><span data-stu-id="19601-667">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="19601-668">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-668">TABLE_CATALOG</span></span>|<span data-ttu-id="19601-669">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-669">String</span></span>|  
|<span data-ttu-id="19601-670">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-670">TABLE_SCHEMA</span></span>|<span data-ttu-id="19601-671">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-671">String</span></span>|  
|<span data-ttu-id="19601-672">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-672">TABLE_NAME</span></span>|<span data-ttu-id="19601-673">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-673">String</span></span>|  
|<span data-ttu-id="19601-674">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="19601-674">INDEX_CATALOG</span></span>|<span data-ttu-id="19601-675">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-675">String</span></span>|  
|<span data-ttu-id="19601-676">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="19601-676">INDEX_SCHEMA</span></span>|<span data-ttu-id="19601-677">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-677">String</span></span>|  
|<span data-ttu-id="19601-678">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-678">INDEX_NAME</span></span>|<span data-ttu-id="19601-679">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-679">String</span></span>|  
|<span data-ttu-id="19601-680">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="19601-680">PRIMARY_KEY</span></span>|<span data-ttu-id="19601-681">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-681">Boolean</span></span>|  
|<span data-ttu-id="19601-682">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="19601-682">UNIQUE</span></span>|<span data-ttu-id="19601-683">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-683">Boolean</span></span>|  
|<span data-ttu-id="19601-684">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="19601-684">CLUSTERED</span></span>|<span data-ttu-id="19601-685">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-685">Boolean</span></span>|  
|<span data-ttu-id="19601-686">TYPE</span><span class="sxs-lookup"><span data-stu-id="19601-686">TYPE</span></span>|<span data-ttu-id="19601-687">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-687">Int32</span></span>|  
|<span data-ttu-id="19601-688">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="19601-688">FILL_FACTOR</span></span>|<span data-ttu-id="19601-689">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-689">Int32</span></span>|  
|<span data-ttu-id="19601-690">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="19601-690">INITIAL_SIZE</span></span>|<span data-ttu-id="19601-691">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-691">Int32</span></span>|  
|<span data-ttu-id="19601-692">NULLS</span><span class="sxs-lookup"><span data-stu-id="19601-692">NULLS</span></span>|<span data-ttu-id="19601-693">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-693">Int32</span></span>|  
|<span data-ttu-id="19601-694">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="19601-694">SORT_BOOKMARKS</span></span>|<span data-ttu-id="19601-695">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-695">Boolean</span></span>|  
|<span data-ttu-id="19601-696">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="19601-696">AUTO_UPDATE</span></span>|<span data-ttu-id="19601-697">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-697">Boolean</span></span>|  
|<span data-ttu-id="19601-698">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-698">NULL_COLLATION</span></span>|<span data-ttu-id="19601-699">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-699">Int32</span></span>|  
|<span data-ttu-id="19601-700">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="19601-700">ORDINAL_POSITION</span></span>|<span data-ttu-id="19601-701">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-701">Int64</span></span>|  
|<span data-ttu-id="19601-702">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="19601-702">COLUMN_NAME</span></span>|<span data-ttu-id="19601-703">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-703">String</span></span>|  
|<span data-ttu-id="19601-704">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="19601-704">COLUMN_GUID</span></span>|<span data-ttu-id="19601-705">Guid</span><span class="sxs-lookup"><span data-stu-id="19601-705">Guid</span></span>|  
|<span data-ttu-id="19601-706">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="19601-706">COLUMN_PROPID</span></span>|<span data-ttu-id="19601-707">Int64</span><span class="sxs-lookup"><span data-stu-id="19601-707">Int64</span></span>|  
|<span data-ttu-id="19601-708">COLLATION</span><span class="sxs-lookup"><span data-stu-id="19601-708">COLLATION</span></span>|<span data-ttu-id="19601-709">Int16</span><span class="sxs-lookup"><span data-stu-id="19601-709">Int16</span></span>|  
|<span data-ttu-id="19601-710">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="19601-710">CARDINALITY</span></span>|<span data-ttu-id="19601-711">Decimal</span><span class="sxs-lookup"><span data-stu-id="19601-711">Decimal</span></span>|  
|<span data-ttu-id="19601-712">PAGES</span><span class="sxs-lookup"><span data-stu-id="19601-712">PAGES</span></span>|<span data-ttu-id="19601-713">Int32</span><span class="sxs-lookup"><span data-stu-id="19601-713">Int32</span></span>|  
|<span data-ttu-id="19601-714">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="19601-714">FILTER_CONDITION</span></span>|<span data-ttu-id="19601-715">Строка</span><span class="sxs-lookup"><span data-stu-id="19601-715">String</span></span>|  
|<span data-ttu-id="19601-716">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="19601-716">INTEGRATED</span></span>|<span data-ttu-id="19601-717">Логическое</span><span class="sxs-lookup"><span data-stu-id="19601-717">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19601-718">См. также</span><span class="sxs-lookup"><span data-stu-id="19601-718">See also</span></span>

- [<span data-ttu-id="19601-719">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19601-719">ADO.NET Overview</span></span>](ado-net-overview.md)
