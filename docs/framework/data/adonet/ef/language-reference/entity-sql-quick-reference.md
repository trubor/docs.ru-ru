---
description: 'Дополнительные сведения: Entity SQL краткий справочник'
title: Краткий справочник по Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: ddac48bece1f0e9df737db295d4d028529ea290f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724561"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="50bda-103">Краткий справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="50bda-103">Entity SQL Quick Reference</span></span>

<span data-ttu-id="50bda-104">В этом разделе содержится краткий справочник по запросам [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50bda-104">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="50bda-105">Запросы, описанные в этом разделе, основаны на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="50bda-105">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="50bda-106">Литералы</span><span class="sxs-lookup"><span data-stu-id="50bda-106">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="50bda-107">Строка</span><span class="sxs-lookup"><span data-stu-id="50bda-107">String</span></span>  

 <span data-ttu-id="50bda-108">Существуют строковые литералы в Юникоде и не в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="50bda-108">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="50bda-109">Строки в Юникоде добавляются в начало с префиксом N. Например, `N'hello'` .</span><span class="sxs-lookup"><span data-stu-id="50bda-109">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="50bda-110">Ниже приведен пример строкового литерала не в Юникоде:</span><span class="sxs-lookup"><span data-stu-id="50bda-110">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="50bda-111">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-111">Output:</span></span>  
  
|<span data-ttu-id="50bda-112">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-112">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-113">hello</span><span class="sxs-lookup"><span data-stu-id="50bda-113">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="50bda-114">Дата и время</span><span class="sxs-lookup"><span data-stu-id="50bda-114">DateTime</span></span>  

 <span data-ttu-id="50bda-115">В литералах DateTime обязательными являются и часть даты, и часть времени.</span><span class="sxs-lookup"><span data-stu-id="50bda-115">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="50bda-116">Значения по умолчанию отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="50bda-116">There are no default values.</span></span>  
  
 <span data-ttu-id="50bda-117">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-117">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="50bda-118">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-118">Output:</span></span>  
  
|<span data-ttu-id="50bda-119">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-119">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-120">Понедельник, 25.12.06, 01:01:00</span><span class="sxs-lookup"><span data-stu-id="50bda-120">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="50bda-121">Целое число</span><span class="sxs-lookup"><span data-stu-id="50bda-121">Integer</span></span>  

 <span data-ttu-id="50bda-122">Целочисленные литералы могут иметь тип Int32 (123), UInt32 (123U), Int64 (123L) и UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="50bda-122">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="50bda-123">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-123">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="50bda-124">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-124">Output:</span></span>  
  
|<span data-ttu-id="50bda-125">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-125">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-126">1</span><span class="sxs-lookup"><span data-stu-id="50bda-126">1</span></span>|  
|<span data-ttu-id="50bda-127">2</span><span class="sxs-lookup"><span data-stu-id="50bda-127">2</span></span>|  
|<span data-ttu-id="50bda-128">3</span><span class="sxs-lookup"><span data-stu-id="50bda-128">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="50bda-129">Другое</span><span class="sxs-lookup"><span data-stu-id="50bda-129">Other</span></span>  

 <span data-ttu-id="50bda-130">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает и другие типы литералов - Guid, Binary, Float/Double, Decimal и `null`.</span><span class="sxs-lookup"><span data-stu-id="50bda-130">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="50bda-131">Литералы NULL в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] считаются совместимыми с любым из других типов в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="50bda-131">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="50bda-132">Конструкторы типов</span><span class="sxs-lookup"><span data-stu-id="50bda-132">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="50bda-133">ROW</span><span class="sxs-lookup"><span data-stu-id="50bda-133">ROW</span></span>  

 <span data-ttu-id="50bda-134">[Строка](row-entity-sql.md) конструирует анонимное, структурно типизированное значение (запись), как в: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="50bda-134">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="50bda-135">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-135">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="50bda-136">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-136">Output:</span></span>  
  
|<span data-ttu-id="50bda-137">ProductID</span><span class="sxs-lookup"><span data-stu-id="50bda-137">ProductID</span></span>|<span data-ttu-id="50bda-138">Имя</span><span class="sxs-lookup"><span data-stu-id="50bda-138">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="50bda-139">1</span><span class="sxs-lookup"><span data-stu-id="50bda-139">1</span></span>|<span data-ttu-id="50bda-140">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="50bda-140">Adjustable Race</span></span>|  
|<span data-ttu-id="50bda-141">879</span><span class="sxs-lookup"><span data-stu-id="50bda-141">879</span></span>|<span data-ttu-id="50bda-142">Универсальная подставка для велосипеда</span><span class="sxs-lookup"><span data-stu-id="50bda-142">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="50bda-143">712</span><span class="sxs-lookup"><span data-stu-id="50bda-143">712</span></span>|<span data-ttu-id="50bda-144">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="50bda-144">AWC Logo Cap</span></span>|  
|<span data-ttu-id="50bda-145">...</span><span class="sxs-lookup"><span data-stu-id="50bda-145">...</span></span>|<span data-ttu-id="50bda-146">...</span><span class="sxs-lookup"><span data-stu-id="50bda-146">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="50bda-147">MULTISET</span><span class="sxs-lookup"><span data-stu-id="50bda-147">MULTISET</span></span>  

 <span data-ttu-id="50bda-148">Коллекции [мультинаборов](multiset-entity-sql.md) , например:</span><span class="sxs-lookup"><span data-stu-id="50bda-148">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="50bda-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="50bda-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="50bda-150">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-150">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="50bda-151">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-151">Output:</span></span>  
  
|<span data-ttu-id="50bda-152">ProductID</span><span class="sxs-lookup"><span data-stu-id="50bda-152">ProductID</span></span>|<span data-ttu-id="50bda-153">Имя</span><span class="sxs-lookup"><span data-stu-id="50bda-153">Name</span></span>|<span data-ttu-id="50bda-154">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="50bda-154">ProductNumber</span></span>|<span data-ttu-id="50bda-155">…</span><span class="sxs-lookup"><span data-stu-id="50bda-155">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="50bda-156">842</span><span class="sxs-lookup"><span data-stu-id="50bda-156">842</span></span>|<span data-ttu-id="50bda-157">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="50bda-157">Touring-Panniers, Large</span></span>|<span data-ttu-id="50bda-158">PA-T100</span><span class="sxs-lookup"><span data-stu-id="50bda-158">PA-T100</span></span>|<span data-ttu-id="50bda-159">…</span><span class="sxs-lookup"><span data-stu-id="50bda-159">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="50bda-160">Объект</span><span class="sxs-lookup"><span data-stu-id="50bda-160">Object</span></span>  

 <span data-ttu-id="50bda-161">[Конструктор именованного типа](named-type-constructor-entity-sql.md) конструирует (именованные) определяемые пользователем объекты, такие как `person("abc", 12)` .</span><span class="sxs-lookup"><span data-stu-id="50bda-161">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="50bda-162">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-162">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="50bda-163">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-163">Output:</span></span>  
  
|<span data-ttu-id="50bda-164">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="50bda-164">SalesOrderDetailID</span></span>|<span data-ttu-id="50bda-165">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="50bda-165">CarrierTrackingNumber</span></span>|<span data-ttu-id="50bda-166">OrderQty</span><span class="sxs-lookup"><span data-stu-id="50bda-166">OrderQty</span></span>|<span data-ttu-id="50bda-167">ProductID</span><span class="sxs-lookup"><span data-stu-id="50bda-167">ProductID</span></span>|<span data-ttu-id="50bda-168">...</span><span class="sxs-lookup"><span data-stu-id="50bda-168">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="50bda-169">1</span><span class="sxs-lookup"><span data-stu-id="50bda-169">1</span></span>|<span data-ttu-id="50bda-170">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="50bda-170">4911-403C-98</span></span>|<span data-ttu-id="50bda-171">1</span><span class="sxs-lookup"><span data-stu-id="50bda-171">1</span></span>|<span data-ttu-id="50bda-172">776</span><span class="sxs-lookup"><span data-stu-id="50bda-172">776</span></span>|<span data-ttu-id="50bda-173">...</span><span class="sxs-lookup"><span data-stu-id="50bda-173">...</span></span>|  
|<span data-ttu-id="50bda-174">2</span><span class="sxs-lookup"><span data-stu-id="50bda-174">2</span></span>|<span data-ttu-id="50bda-175">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="50bda-175">4911-403C-98</span></span>|<span data-ttu-id="50bda-176">3</span><span class="sxs-lookup"><span data-stu-id="50bda-176">3</span></span>|<span data-ttu-id="50bda-177">777</span><span class="sxs-lookup"><span data-stu-id="50bda-177">777</span></span>|<span data-ttu-id="50bda-178">...</span><span class="sxs-lookup"><span data-stu-id="50bda-178">...</span></span>|  
|<span data-ttu-id="50bda-179">...</span><span class="sxs-lookup"><span data-stu-id="50bda-179">...</span></span>|<span data-ttu-id="50bda-180">...</span><span class="sxs-lookup"><span data-stu-id="50bda-180">...</span></span>|<span data-ttu-id="50bda-181">...</span><span class="sxs-lookup"><span data-stu-id="50bda-181">...</span></span>|<span data-ttu-id="50bda-182">...</span><span class="sxs-lookup"><span data-stu-id="50bda-182">...</span></span>|<span data-ttu-id="50bda-183">...</span><span class="sxs-lookup"><span data-stu-id="50bda-183">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="50bda-184">Ссылки</span><span class="sxs-lookup"><span data-stu-id="50bda-184">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="50bda-185">REF</span><span class="sxs-lookup"><span data-stu-id="50bda-185">REF</span></span>  

 <span data-ttu-id="50bda-186">[Ref](ref-entity-sql.md) создает ссылку на экземпляр типа сущности.</span><span class="sxs-lookup"><span data-stu-id="50bda-186">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="50bda-187">Например, следующий запрос возвращает ссылки на каждую сущность Order в наборе сущностей Orders:</span><span class="sxs-lookup"><span data-stu-id="50bda-187">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="50bda-188">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-188">Output:</span></span>  
  
|<span data-ttu-id="50bda-189">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-189">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-190">1</span><span class="sxs-lookup"><span data-stu-id="50bda-190">1</span></span>|  
|<span data-ttu-id="50bda-191">2</span><span class="sxs-lookup"><span data-stu-id="50bda-191">2</span></span>|  
|<span data-ttu-id="50bda-192">3</span><span class="sxs-lookup"><span data-stu-id="50bda-192">3</span></span>|  
|<span data-ttu-id="50bda-193">...</span><span class="sxs-lookup"><span data-stu-id="50bda-193">...</span></span>|  
  
 <span data-ttu-id="50bda-194">В следующем примере оператор извлечения свойства (.) используется для доступа к свойству сущности.</span><span class="sxs-lookup"><span data-stu-id="50bda-194">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="50bda-195">При использовании этого оператора автоматически выполняется разыменование ссылки.</span><span class="sxs-lookup"><span data-stu-id="50bda-195">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="50bda-196">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-196">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="50bda-197">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-197">Output:</span></span>  
  
|<span data-ttu-id="50bda-198">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-198">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-199">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="50bda-199">Adjustable Race</span></span>|  
|<span data-ttu-id="50bda-200">Универсальная подставка для велосипеда</span><span class="sxs-lookup"><span data-stu-id="50bda-200">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="50bda-201">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="50bda-201">AWC Logo Cap</span></span>|  
|<span data-ttu-id="50bda-202">...</span><span class="sxs-lookup"><span data-stu-id="50bda-202">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="50bda-203">DEREF</span><span class="sxs-lookup"><span data-stu-id="50bda-203">DEREF</span></span>  

 <span data-ttu-id="50bda-204">[DEREF](deref-entity-sql.md) разыменование ссылочного значения и выдает результат разыменования.</span><span class="sxs-lookup"><span data-stu-id="50bda-204">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="50bda-205">Например, следующий запрос возвращает сущности Order для каждой из записей Order в наборе сущностей Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="50bda-205">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="50bda-206">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-206">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="50bda-207">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-207">Output:</span></span>  
  
|<span data-ttu-id="50bda-208">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-208">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-209">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="50bda-209">Adjustable Race</span></span>|  
|<span data-ttu-id="50bda-210">Универсальная подставка для велосипеда</span><span class="sxs-lookup"><span data-stu-id="50bda-210">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="50bda-211">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="50bda-211">AWC Logo Cap</span></span>|  
|<span data-ttu-id="50bda-212">...</span><span class="sxs-lookup"><span data-stu-id="50bda-212">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="50bda-213">CREATEREF и KEY</span><span class="sxs-lookup"><span data-stu-id="50bda-213">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="50bda-214">[CREATEREF](createref-entity-sql.md) создает ссылку, передавая ключ.</span><span class="sxs-lookup"><span data-stu-id="50bda-214">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="50bda-215">[Key](key-entity-sql.md) извлекает ключевую часть выражения со ссылкой на тип.</span><span class="sxs-lookup"><span data-stu-id="50bda-215">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="50bda-216">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-216">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="50bda-217">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-217">Output:</span></span>  
  
|<span data-ttu-id="50bda-218">ProductID</span><span class="sxs-lookup"><span data-stu-id="50bda-218">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="50bda-219">980</span><span class="sxs-lookup"><span data-stu-id="50bda-219">980</span></span>|  
|<span data-ttu-id="50bda-220">365</span><span class="sxs-lookup"><span data-stu-id="50bda-220">365</span></span>|  
|<span data-ttu-id="50bda-221">771</span><span class="sxs-lookup"><span data-stu-id="50bda-221">771</span></span>|  
|<span data-ttu-id="50bda-222">...</span><span class="sxs-lookup"><span data-stu-id="50bda-222">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="50bda-223">Функции</span><span class="sxs-lookup"><span data-stu-id="50bda-223">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="50bda-224">Canonical</span><span class="sxs-lookup"><span data-stu-id="50bda-224">Canonical</span></span>  

 <span data-ttu-id="50bda-225">Пространство имен для [канонических функций](canonical-functions.md) — EDM, как в `Edm.Length("string")` .</span><span class="sxs-lookup"><span data-stu-id="50bda-225">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="50bda-226">Если не импортировано другое пространство имен, содержащее функцию, имя которой совпадает с именем канонической функции, то указывать пространство имен не обязательно.</span><span class="sxs-lookup"><span data-stu-id="50bda-226">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="50bda-227">Если в двух пространствах имен имеется функция с тем же именем, то пользователь должен указать полное имя функции.</span><span class="sxs-lookup"><span data-stu-id="50bda-227">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="50bda-228">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-228">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="50bda-229">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-229">Output:</span></span>  
  
|<span data-ttu-id="50bda-230">NameLen</span><span class="sxs-lookup"><span data-stu-id="50bda-230">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="50bda-231">6</span><span class="sxs-lookup"><span data-stu-id="50bda-231">6</span></span>|  
|<span data-ttu-id="50bda-232">6</span><span class="sxs-lookup"><span data-stu-id="50bda-232">6</span></span>|  
|<span data-ttu-id="50bda-233">5</span><span class="sxs-lookup"><span data-stu-id="50bda-233">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="50bda-234">Функции поставщиков данных (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="50bda-234">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="50bda-235">[Функции, относящиеся к поставщику (Майкрософт)](../sqlclient-for-ef-functions.md) , находятся в `SqlServer` пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="50bda-235">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="50bda-236">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-236">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="50bda-237">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-237">Output:</span></span>  
  
|<span data-ttu-id="50bda-238">EmailLen</span><span class="sxs-lookup"><span data-stu-id="50bda-238">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="50bda-239">27</span><span class="sxs-lookup"><span data-stu-id="50bda-239">27</span></span>|  
|<span data-ttu-id="50bda-240">27</span><span class="sxs-lookup"><span data-stu-id="50bda-240">27</span></span>|  
|<span data-ttu-id="50bda-241">26</span><span class="sxs-lookup"><span data-stu-id="50bda-241">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="50bda-242">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="50bda-242">Namespaces</span></span>  

 <span data-ttu-id="50bda-243">[Использование](using-entity-sql.md) задает пространства имен, используемые в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="50bda-243">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="50bda-244">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-244">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="50bda-245">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-245">Output:</span></span>  
  
|<span data-ttu-id="50bda-246">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-246">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-247">aa</span><span class="sxs-lookup"><span data-stu-id="50bda-247">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="50bda-248">Разбивка на страницы</span><span class="sxs-lookup"><span data-stu-id="50bda-248">Paging</span></span>  

 <span data-ttu-id="50bda-249">Разбиение на страницы может быть выражено путем объявления вложенных предложений [Skip](skip-entity-sql.md) и [Limit](limit-entity-sql.md) в предложении [ORDER BY](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="50bda-249">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="50bda-250">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-250">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="50bda-251">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-251">Output:</span></span>  
  
|<span data-ttu-id="50bda-252">ID</span><span class="sxs-lookup"><span data-stu-id="50bda-252">ID</span></span>|<span data-ttu-id="50bda-253">Имя</span><span class="sxs-lookup"><span data-stu-id="50bda-253">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="50bda-254">10</span><span class="sxs-lookup"><span data-stu-id="50bda-254">10</span></span>|<span data-ttu-id="50bda-255">Adina</span><span class="sxs-lookup"><span data-stu-id="50bda-255">Adina</span></span>|  
|<span data-ttu-id="50bda-256">11</span><span class="sxs-lookup"><span data-stu-id="50bda-256">11</span></span>|<span data-ttu-id="50bda-257">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="50bda-257">Agcaoili</span></span>|  
|<span data-ttu-id="50bda-258">12</span><span class="sxs-lookup"><span data-stu-id="50bda-258">12</span></span>|<span data-ttu-id="50bda-259">Aguilar</span><span class="sxs-lookup"><span data-stu-id="50bda-259">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="50bda-260">Группирование</span><span class="sxs-lookup"><span data-stu-id="50bda-260">Grouping</span></span>  

 <span data-ttu-id="50bda-261">[Группирование по](group-by-entity-sql.md) задает группы, в которые должны быть помещены объекты, возвращаемые выражением запроса ([SELECT](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="50bda-261">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="50bda-262">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-262">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="50bda-263">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-263">Output:</span></span>  
  
|<span data-ttu-id="50bda-264">name</span><span class="sxs-lookup"><span data-stu-id="50bda-264">name</span></span>|  
|----------|  
|<span data-ttu-id="50bda-265">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="50bda-265">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="50bda-266">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="50bda-266">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="50bda-267">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="50bda-267">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="50bda-268">...</span><span class="sxs-lookup"><span data-stu-id="50bda-268">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="50bda-269">Навигация</span><span class="sxs-lookup"><span data-stu-id="50bda-269">Navigation</span></span>  

 <span data-ttu-id="50bda-270">Оператор навигации по связям позволяет переходить по связям от одной сущности (исходный элемент) к другой (конечный элемент).</span><span class="sxs-lookup"><span data-stu-id="50bda-270">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="50bda-271">[Навигация](navigate-entity-sql.md) принимает тип связи в виде \<namespace> . \<relationship type name> .</span><span class="sxs-lookup"><span data-stu-id="50bda-271">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="50bda-272">Функция Navigate возвращает ref, \<T> Если количество элементов с начала до конца равно 1.</span><span class="sxs-lookup"><span data-stu-id="50bda-272">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="50bda-273">Если число элементов в конец равно n, \<T> будет возвращена коллекция<ссылка>.</span><span class="sxs-lookup"><span data-stu-id="50bda-273">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="50bda-274">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-274">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="50bda-275">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-275">Output:</span></span>  
  
|<span data-ttu-id="50bda-276">AddressID</span><span class="sxs-lookup"><span data-stu-id="50bda-276">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="50bda-277">1</span><span class="sxs-lookup"><span data-stu-id="50bda-277">1</span></span>|  
|<span data-ttu-id="50bda-278">2</span><span class="sxs-lookup"><span data-stu-id="50bda-278">2</span></span>|  
|<span data-ttu-id="50bda-279">3</span><span class="sxs-lookup"><span data-stu-id="50bda-279">3</span></span>|  
|<span data-ttu-id="50bda-280">...</span><span class="sxs-lookup"><span data-stu-id="50bda-280">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="50bda-281">SELECT VALUE и SELECT</span><span class="sxs-lookup"><span data-stu-id="50bda-281">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="50bda-282">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="50bda-282">SELECT VALUE</span></span>  

 <span data-ttu-id="50bda-283">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает предложение SELECT VALUE, позволяющее пропустить неявное построение строки.</span><span class="sxs-lookup"><span data-stu-id="50bda-283">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="50bda-284">В предложении SELECT VALUE может быть указан только один элемент.</span><span class="sxs-lookup"><span data-stu-id="50bda-284">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="50bda-285">При использовании такого предложения оболочка строк не создается вокруг элементов в предложении SELECT, а коллекция требуемой формы может быть создана, например: `SELECT VALUE a` .</span><span class="sxs-lookup"><span data-stu-id="50bda-285">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="50bda-286">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-286">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="50bda-287">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-287">Output:</span></span>  
  
|<span data-ttu-id="50bda-288">Имя</span><span class="sxs-lookup"><span data-stu-id="50bda-288">Name</span></span>|  
|----------|  
|<span data-ttu-id="50bda-289">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="50bda-289">Adjustable Race</span></span>|  
|<span data-ttu-id="50bda-290">Универсальная подставка для велосипеда</span><span class="sxs-lookup"><span data-stu-id="50bda-290">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="50bda-291">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="50bda-291">AWC Logo Cap</span></span>|  
|<span data-ttu-id="50bda-292">...</span><span class="sxs-lookup"><span data-stu-id="50bda-292">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="50bda-293">SELECT</span><span class="sxs-lookup"><span data-stu-id="50bda-293">SELECT</span></span>  

 <span data-ttu-id="50bda-294">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает также конструктор строк, позволяющий создавать произвольные строки.</span><span class="sxs-lookup"><span data-stu-id="50bda-294">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="50bda-295">Предложение SELECT принимает один или несколько элементов в проекции и возвращает запись данных с полями, например: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="50bda-295">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="50bda-296">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-296">Example:</span></span>  
  
 <span data-ttu-id="50bda-297">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="50bda-297">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="50bda-298">Имя</span><span class="sxs-lookup"><span data-stu-id="50bda-298">Name</span></span>|<span data-ttu-id="50bda-299">ProductID</span><span class="sxs-lookup"><span data-stu-id="50bda-299">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="50bda-300">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="50bda-300">Adjustable Race</span></span>|<span data-ttu-id="50bda-301">1</span><span class="sxs-lookup"><span data-stu-id="50bda-301">1</span></span>|  
|<span data-ttu-id="50bda-302">Универсальная подставка для велосипеда</span><span class="sxs-lookup"><span data-stu-id="50bda-302">All-Purpose Bike Stand</span></span>|<span data-ttu-id="50bda-303">879</span><span class="sxs-lookup"><span data-stu-id="50bda-303">879</span></span>|  
|<span data-ttu-id="50bda-304">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="50bda-304">AWC Logo Cap</span></span>|<span data-ttu-id="50bda-305">712</span><span class="sxs-lookup"><span data-stu-id="50bda-305">712</span></span>|  
|<span data-ttu-id="50bda-306">...</span><span class="sxs-lookup"><span data-stu-id="50bda-306">...</span></span>|<span data-ttu-id="50bda-307">...</span><span class="sxs-lookup"><span data-stu-id="50bda-307">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="50bda-308">Выражение варианта выбора</span><span class="sxs-lookup"><span data-stu-id="50bda-308">CASE EXPRESSION</span></span>  

 <span data-ttu-id="50bda-309">[Выражение CASE](case-entity-sql.md) вычисляет набор логических выражений для определения результата.</span><span class="sxs-lookup"><span data-stu-id="50bda-309">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="50bda-310">Пример.</span><span class="sxs-lookup"><span data-stu-id="50bda-310">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="50bda-311">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="50bda-311">Output:</span></span>  
  
|<span data-ttu-id="50bda-312">Значение</span><span class="sxs-lookup"><span data-stu-id="50bda-312">Value</span></span>|  
|-----------|  
|<span data-ttu-id="50bda-313">true</span><span class="sxs-lookup"><span data-stu-id="50bda-313">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50bda-314">См. также</span><span class="sxs-lookup"><span data-stu-id="50bda-314">See also</span></span>

- [<span data-ttu-id="50bda-315">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="50bda-315">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="50bda-316">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="50bda-316">Entity SQL Overview</span></span>](entity-sql-overview.md)
