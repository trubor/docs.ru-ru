---
description: 'Дополнительные сведения: ORDER BY (Entity SQL)'
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 092850e864ae95d50b615839265041a7e32b39a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696325"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="b4cf2-103">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b4cf2-103">ORDER BY (Entity SQL)</span></span>

<span data-ttu-id="b4cf2-104">Указывает порядок сортировки для объектов, возвращаемых инструкцией SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-104">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4cf2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4cf2-105">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4cf2-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="b4cf2-106">Arguments</span></span>  

 `order_by_expression`  
 <span data-ttu-id="b4cf2-107">Любое допустимое выражение запроса, задающее свойство, по которому выполняется сортировка.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-107">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="b4cf2-108">Может быть указано несколько выражений сортировки.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-108">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="b4cf2-109">Последовательность выражений сортировки в предложении ORDER BY определяет порядок сортировки результирующего набора.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-109">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="b4cf2-110">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="b4cf2-110">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="b4cf2-111">Указывает, что операция ORDER BY должна выполняться в соответствии с параметрами сортировки, заданными в аргументе `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-111">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="b4cf2-112">COLLATE применяется только для строковых выражений.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-112">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="b4cf2-113">ASC</span><span class="sxs-lookup"><span data-stu-id="b4cf2-113">ASC</span></span>  
 <span data-ttu-id="b4cf2-114">Указывает, что значения в указанном свойстве должны быть отсортированы в порядке возрастания, от меньшего к большему.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-114">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="b4cf2-115">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-115">This is the default.</span></span>  
  
 <span data-ttu-id="b4cf2-116">DESC</span><span class="sxs-lookup"><span data-stu-id="b4cf2-116">DESC</span></span>  
 <span data-ttu-id="b4cf2-117">Указывает, что значения в указанном свойстве должны быть отсортированы в порядке убывания, от большего к меньшему.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-117">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="b4cf2-118">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="b4cf2-118">LIMIT `n`</span></span>  
 <span data-ttu-id="b4cf2-119">Будут выбраны только первые `n` элементов.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-119">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="b4cf2-120">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="b4cf2-120">SKIP `n`</span></span>  
 <span data-ttu-id="b4cf2-121">Пропускает первые `n` элементов.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-121">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4cf2-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4cf2-122">Remarks</span></span>  

 <span data-ttu-id="b4cf2-123">Предложение ORDER BY логически применяется к результату предложения SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-123">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="b4cf2-124">Предложение ORDER BY может ссылаться на элементы списка выбора по их псевдонимам.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-124">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="b4cf2-125">Предложение ORDER BY может также ссылаться на другие переменные, находящиеся в области видимости.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-125">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="b4cf2-126">Однако если предложение SELECT указано с модификатором DISTINCT, то предложение ORDER BY может ссылаться только на псевдонимы из предложения SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-126">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="b4cf2-127">Выражения в предложении ORDER BY должны иметь сравнимый тип, поскольку для упорядочивания производится сравнение элементов (меньше, больше и т. д.).</span><span class="sxs-lookup"><span data-stu-id="b4cf2-127">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="b4cf2-128">Такими типами обычно являются скалярные примитивы - числа, строки и даты.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-128">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="b4cf2-129">Типы RowType для сравнимых типов также являются сравнимыми для упорядочивания.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-129">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="b4cf2-130">Если код проходит по упорядоченному набору, отличному от проекции верхнего уровня, то сохранение порядка в выходных данных не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-130">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="b4cf2-131">В следующем примере гарантируется сохранение порядка:</span><span class="sxs-lookup"><span data-stu-id="b4cf2-131">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="b4cf2-132">В следующем запросе не учитывается порядок вложенных запросов:</span><span class="sxs-lookup"><span data-stu-id="b4cf2-132">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="b4cf2-133">Получить упорядоченный результат выполнения операции UNION, UNION ALL, EXCEPT или INTERSECT можно следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-133">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="b4cf2-134">Служебные ключевые слова</span><span class="sxs-lookup"><span data-stu-id="b4cf2-134">Restricted keywords</span></span>  

 <span data-ttu-id="b4cf2-135">Следующие ключевые слова при использовании в предложении `ORDER BY` необходимо заключать в кавычки.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-135">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="b4cf2-136">CROSS</span><span class="sxs-lookup"><span data-stu-id="b4cf2-136">CROSS</span></span>  
  
- <span data-ttu-id="b4cf2-137">FULL</span><span class="sxs-lookup"><span data-stu-id="b4cf2-137">FULL</span></span>  
  
- <span data-ttu-id="b4cf2-138">KEY</span><span class="sxs-lookup"><span data-stu-id="b4cf2-138">KEY</span></span>  
  
- <span data-ttu-id="b4cf2-139">LEFT</span><span class="sxs-lookup"><span data-stu-id="b4cf2-139">LEFT</span></span>  
  
- <span data-ttu-id="b4cf2-140">ORDER</span><span class="sxs-lookup"><span data-stu-id="b4cf2-140">ORDER</span></span>  
  
- <span data-ttu-id="b4cf2-141">OUTER</span><span class="sxs-lookup"><span data-stu-id="b4cf2-141">OUTER</span></span>  
  
- <span data-ttu-id="b4cf2-142">RIGHT</span><span class="sxs-lookup"><span data-stu-id="b4cf2-142">RIGHT</span></span>  
  
- <span data-ttu-id="b4cf2-143">ROW</span><span class="sxs-lookup"><span data-stu-id="b4cf2-143">ROW</span></span>  
  
- <span data-ttu-id="b4cf2-144">Значение</span><span class="sxs-lookup"><span data-stu-id="b4cf2-144">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="b4cf2-145">Упорядочение вложенных запросов</span><span class="sxs-lookup"><span data-stu-id="b4cf2-145">Ordering Nested Queries</span></span>  

 <span data-ttu-id="b4cf2-146">Платформа Entity Framework позволяет разместить вложенное выражение в любом месте запроса. Порядок вложенного запроса не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-146">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="b4cf2-147">Следующий запрос упорядочивает результаты по фамилии:</span><span class="sxs-lookup"><span data-stu-id="b4cf2-147">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="b4cf2-148">В следующем запросе не учитывается порядок вложенных запросов:</span><span class="sxs-lookup"><span data-stu-id="b4cf2-148">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="b4cf2-149">Пример</span><span class="sxs-lookup"><span data-stu-id="b4cf2-149">Example</span></span>  

 <span data-ttu-id="b4cf2-150">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор ORDER BY задает порядок сортировки для объектов, возвращаемых инструкцией SELECT.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-150">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="b4cf2-151">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-151">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b4cf2-152">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="b4cf2-152">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b4cf2-153">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf2-153">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b4cf2-154">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="b4cf2-154">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="b4cf2-155">См. также</span><span class="sxs-lookup"><span data-stu-id="b4cf2-155">See also</span></span>

- [<span data-ttu-id="b4cf2-156">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="b4cf2-156">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="b4cf2-157">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b4cf2-157">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b4cf2-158">СРАЗУ</span><span class="sxs-lookup"><span data-stu-id="b4cf2-158">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="b4cf2-159">Размер</span><span class="sxs-lookup"><span data-stu-id="b4cf2-159">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="b4cf2-160">В начало</span><span class="sxs-lookup"><span data-stu-id="b4cf2-160">TOP</span></span>](top-entity-sql.md)
