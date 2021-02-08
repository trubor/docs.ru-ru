---
description: Дополнительные сведения см. в статье семантика сравнения (Entity SQL)
title: Семантика сравнения (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: b1c832cb6f2903073b1c6be806c73823b1f4a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786437"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="28a19-103">Семантика сравнения (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="28a19-103">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="28a19-104">Выполнение любого следующего оператора [!INCLUDE[esql](../../../../../../includes/esql-md.md)] подразумевает сравнение типов экземпляров.</span><span class="sxs-lookup"><span data-stu-id="28a19-104">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="28a19-105">Явное сравнение</span><span class="sxs-lookup"><span data-stu-id="28a19-105">Explicit comparison</span></span>  

 <span data-ttu-id="28a19-106">Операции сравнения:</span><span class="sxs-lookup"><span data-stu-id="28a19-106">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="28a19-107">!=</span><span class="sxs-lookup"><span data-stu-id="28a19-107">!=</span></span>  
  
 <span data-ttu-id="28a19-108">Операции упорядочивания:</span><span class="sxs-lookup"><span data-stu-id="28a19-108">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="28a19-109">Операции допустимости значений NULL:</span><span class="sxs-lookup"><span data-stu-id="28a19-109">Nullability operations:</span></span>  
  
- <span data-ttu-id="28a19-110">IS NULL</span><span class="sxs-lookup"><span data-stu-id="28a19-110">IS NULL</span></span>  
  
- <span data-ttu-id="28a19-111">IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="28a19-111">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="28a19-112">Явное отличие</span><span class="sxs-lookup"><span data-stu-id="28a19-112">Explicit distinction</span></span>  

 <span data-ttu-id="28a19-113">Отличие равенства:</span><span class="sxs-lookup"><span data-stu-id="28a19-113">Equality distinction:</span></span>  
  
- <span data-ttu-id="28a19-114">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="28a19-114">DISTINCT</span></span>  
  
- <span data-ttu-id="28a19-115">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="28a19-115">GROUP BY</span></span>  
  
 <span data-ttu-id="28a19-116">Отличие упорядочивания:</span><span class="sxs-lookup"><span data-stu-id="28a19-116">Ordering distinction:</span></span>  
  
- <span data-ttu-id="28a19-117">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="28a19-117">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="28a19-118">Неявное отличие</span><span class="sxs-lookup"><span data-stu-id="28a19-118">Implicit distinction</span></span>  

 <span data-ttu-id="28a19-119">Операция и предикаты для работы с наборами (равенство):</span><span class="sxs-lookup"><span data-stu-id="28a19-119">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="28a19-120">UNION</span><span class="sxs-lookup"><span data-stu-id="28a19-120">UNION</span></span>  
  
- <span data-ttu-id="28a19-121">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="28a19-121">INTERSECT</span></span>  
  
- <span data-ttu-id="28a19-122">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="28a19-122">EXCEPT</span></span>  
  
- <span data-ttu-id="28a19-123">SET</span><span class="sxs-lookup"><span data-stu-id="28a19-123">SET</span></span>  
  
- <span data-ttu-id="28a19-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="28a19-124">OVERLAPS</span></span>  
  
 <span data-ttu-id="28a19-125">Предикаты элементов (равенство):</span><span class="sxs-lookup"><span data-stu-id="28a19-125">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="28a19-126">IN</span><span class="sxs-lookup"><span data-stu-id="28a19-126">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="28a19-127">Поддерживаемые сочетания</span><span class="sxs-lookup"><span data-stu-id="28a19-127">Supported Combinations</span></span>  

 <span data-ttu-id="28a19-128">В следующей таблице приводятся все поддерживаемые сочетания операторов сравнения для каждого типа.</span><span class="sxs-lookup"><span data-stu-id="28a19-128">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="28a19-129">**Тип**</span><span class="sxs-lookup"><span data-stu-id="28a19-129">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="28a19-130">**!=**</span><span class="sxs-lookup"><span data-stu-id="28a19-130">**!=**</span></span>|<span data-ttu-id="28a19-131">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="28a19-131">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="28a19-132">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="28a19-132">**DISTINCT**</span></span>|<span data-ttu-id="28a19-133">**UNION**</span><span class="sxs-lookup"><span data-stu-id="28a19-133">**UNION**</span></span><br /><br /> <span data-ttu-id="28a19-134">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="28a19-134">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="28a19-135">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="28a19-135">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="28a19-136">**SET**</span><span class="sxs-lookup"><span data-stu-id="28a19-136">**SET**</span></span><br /><br /> <span data-ttu-id="28a19-137">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="28a19-137">**OVERLAPS**</span></span>|<span data-ttu-id="28a19-138">**IN**</span><span class="sxs-lookup"><span data-stu-id="28a19-138">**IN**</span></span>|<span data-ttu-id="28a19-139">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="28a19-139">**<   <=**</span></span><br /><br /> <span data-ttu-id="28a19-140">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="28a19-140">**>   >=**</span></span>|<span data-ttu-id="28a19-141">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="28a19-141">**ORDER BY**</span></span>|<span data-ttu-id="28a19-142">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="28a19-142">**IS NULL**</span></span><br /><br /> <span data-ttu-id="28a19-143">**НЕ РАВНО NULL**</span><span class="sxs-lookup"><span data-stu-id="28a19-143">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="28a19-144">Тип сущности</span><span class="sxs-lookup"><span data-stu-id="28a19-144">Entity type</span></span>|<span data-ttu-id="28a19-145">Ссылка<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-145">Ref<sup>1</sup></span></span>|<span data-ttu-id="28a19-146">Все свойства<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="28a19-147">Все свойства<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="28a19-148">Все свойства<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-148">All properties<sup>2</sup></span></span>|<span data-ttu-id="28a19-149">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-150">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-150">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-151">Ссылка<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-151">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="28a19-152">Сложный тип</span><span class="sxs-lookup"><span data-stu-id="28a19-152">Complex type</span></span>|<span data-ttu-id="28a19-153">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-154">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-155">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-156">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-157">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-158">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-158">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-159">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-159">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="28a19-160">Строка</span><span class="sxs-lookup"><span data-stu-id="28a19-160">Row</span></span>|<span data-ttu-id="28a19-161">Все свойства<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="28a19-162">Все свойства<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="28a19-163">Все свойства<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-163">All properties<sup>4</sup></span></span>|<span data-ttu-id="28a19-164">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-165">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-165">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-166">Все свойства<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-166">All properties<sup>4</sup></span></span>|<span data-ttu-id="28a19-167">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-167">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="28a19-168">Тип-примитив</span><span class="sxs-lookup"><span data-stu-id="28a19-168">Primitive type</span></span>|<span data-ttu-id="28a19-169">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-169">Provider-specific</span></span>|<span data-ttu-id="28a19-170">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-170">Provider-specific</span></span>|<span data-ttu-id="28a19-171">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-171">Provider-specific</span></span>|<span data-ttu-id="28a19-172">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-172">Provider-specific</span></span>|<span data-ttu-id="28a19-173">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-173">Provider-specific</span></span>|<span data-ttu-id="28a19-174">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-174">Provider-specific</span></span>|<span data-ttu-id="28a19-175">Зависит от поставщика</span><span class="sxs-lookup"><span data-stu-id="28a19-175">Provider-specific</span></span>|  
|<span data-ttu-id="28a19-176">Мультинабор</span><span class="sxs-lookup"><span data-stu-id="28a19-176">Multiset</span></span>|<span data-ttu-id="28a19-177">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-178">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-179">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-180">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-181">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-182">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-182">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-183">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-183">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="28a19-184">Ссылочный</span><span class="sxs-lookup"><span data-stu-id="28a19-184">Ref</span></span>|<span data-ttu-id="28a19-185">Да<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="28a19-186">Да<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="28a19-187">Да<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="28a19-188">Да<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-188">Yes<sup>5</sup></span></span>|<span data-ttu-id="28a19-189">Ключевое слово throw</span><span class="sxs-lookup"><span data-stu-id="28a19-189">Throw</span></span>|<span data-ttu-id="28a19-190">Ключевое слово throw</span><span class="sxs-lookup"><span data-stu-id="28a19-190">Throw</span></span>|<span data-ttu-id="28a19-191">Да<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-191">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="28a19-192">Взаимосвязь</span><span class="sxs-lookup"><span data-stu-id="28a19-192">Association</span></span><br /><br /> <span data-ttu-id="28a19-193">тип</span><span class="sxs-lookup"><span data-stu-id="28a19-193">type</span></span>|<span data-ttu-id="28a19-194">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-194">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-195">Ключевое слово throw</span><span class="sxs-lookup"><span data-stu-id="28a19-195">Throw</span></span>|<span data-ttu-id="28a19-196">Ключевое слово throw</span><span class="sxs-lookup"><span data-stu-id="28a19-196">Throw</span></span>|<span data-ttu-id="28a19-197">Ключевое слово throw</span><span class="sxs-lookup"><span data-stu-id="28a19-197">Throw</span></span>|<span data-ttu-id="28a19-198">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-199">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-199">Throw<sup>3</sup></span></span>|<span data-ttu-id="28a19-200">Исключение<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-200">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="28a19-201"><sup>1</sup> Ссылки на заданные экземпляры типа сущности неявно сравниваются, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="28a19-201"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="28a19-202">Экземпляр сущности нельзя сравнивать с явной ссылкой.</span><span class="sxs-lookup"><span data-stu-id="28a19-202">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="28a19-203">При попытке такого сравнения возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="28a19-203">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="28a19-204">Например, следующий запрос вызовет исключение:</span><span class="sxs-lookup"><span data-stu-id="28a19-204">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="28a19-205"><sup>2</sup> Свойства сложных типов выравниваются перед отправкой в хранилище, поэтому они становятся сравнимыми (при условии, что все их свойства сравнимы).</span><span class="sxs-lookup"><span data-stu-id="28a19-205"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="28a19-206">См <sup>. также 4.</sup></span><span class="sxs-lookup"><span data-stu-id="28a19-206">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="28a19-207"><sup>3</sup> Среда выполнения Entity Framework обнаруживает неподдерживаемый вариант и создает осмысленное исключение без привлечения поставщика или хранилища.</span><span class="sxs-lookup"><span data-stu-id="28a19-207"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="28a19-208"><sup>4</sup> Выполняется попытка сравнить все свойства.</span><span class="sxs-lookup"><span data-stu-id="28a19-208"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="28a19-209">Если имеется свойство несравнимого типа, например text, ntext или image, может возникнуть серверное исключение.</span><span class="sxs-lookup"><span data-stu-id="28a19-209">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="28a19-210"><sup>5</sup> Сравниваются все отдельные элементы ссылок (в том числе имя набора сущностей и все ключевые свойства типа сущности).</span><span class="sxs-lookup"><span data-stu-id="28a19-210"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a19-211">См. также</span><span class="sxs-lookup"><span data-stu-id="28a19-211">See also</span></span>

- [<span data-ttu-id="28a19-212">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="28a19-212">Entity SQL Overview</span></span>](entity-sql-overview.md)
