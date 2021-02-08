---
description: 'Дополнительные сведения: SELECT (Entity SQL)'
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 7feaf1d9a5101cb745e67afeba8d608104430e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791872"
---
# <a name="select-entity-sql"></a><span data-ttu-id="ef078-103">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ef078-103">SELECT (Entity SQL)</span></span>

<span data-ttu-id="ef078-104">Указывает элементы, возвращаемые запросом.</span><span class="sxs-lookup"><span data-stu-id="ef078-104">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef078-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef078-105">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef078-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="ef078-106">Arguments</span></span>  

 <span data-ttu-id="ef078-107">ALL</span><span class="sxs-lookup"><span data-stu-id="ef078-107">ALL</span></span>  
 <span data-ttu-id="ef078-108">Указывает на то, что в результирующем наборе могут появляться повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="ef078-108">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="ef078-109">ALL является параметром по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ef078-109">ALL is the default.</span></span>  
  
 <span data-ttu-id="ef078-110">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="ef078-110">DISTINCT</span></span>  
 <span data-ttu-id="ef078-111">Указывает, что в результирующем наборе возвращаются только уникальные результаты.</span><span class="sxs-lookup"><span data-stu-id="ef078-111">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="ef078-112">Значение</span><span class="sxs-lookup"><span data-stu-id="ef078-112">VALUE</span></span>  
 <span data-ttu-id="ef078-113">Позволяет указать только один элемент и не добавляет оболочку строк.</span><span class="sxs-lookup"><span data-stu-id="ef078-113">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="ef078-114">Любое допустимое выражение, указывающее число первых результатов, возвращаемых запросом, в формате `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="ef078-114">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="ef078-115">Параметр LIMIT оператора [ORDER BY](order-by-entity-sql.md) также позволяет выбрать первые n элементов в результирующем наборе.</span><span class="sxs-lookup"><span data-stu-id="ef078-115">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="ef078-116">Выражение в следующем формате.</span><span class="sxs-lookup"><span data-stu-id="ef078-116">An expression of the form:</span></span>  
  
 <span data-ttu-id="ef078-117">`expr` как `identifier` &#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="ef078-117">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="ef078-118">Литерал или выражение.</span><span class="sxs-lookup"><span data-stu-id="ef078-118">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef078-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="ef078-119">Remarks</span></span>  

 <span data-ttu-id="ef078-120">Предложение SELECT вычисляется после вычисления предложений [from](from-entity-sql.md), [Group By](group-by-entity-sql.md)и [HAVING](having-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="ef078-120">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="ef078-121">В предложении SELECT могут быть указаны только те элементы, которые в настоящий момент находящиеся в области (из предложения FROM, из внешних областей).</span><span class="sxs-lookup"><span data-stu-id="ef078-121">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="ef078-122">Если указано предложение GROUP BY, то предложение SELECT может ссылаться только на псевдонимы для ключей GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="ef078-122">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="ef078-123">Обращение к элементам предложения FROM допустимо только в агрегатных функциях.</span><span class="sxs-lookup"><span data-stu-id="ef078-123">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="ef078-124">Список, содержащий одно или более выражений запросов, следующих за ключевым словом SELECT, называется списком выбора, или более формально - проекцией.</span><span class="sxs-lookup"><span data-stu-id="ef078-124">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="ef078-125">Наиболее распространенная форма проекции - единственное выражение запроса.</span><span class="sxs-lookup"><span data-stu-id="ef078-125">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="ef078-126">Если выбрать элемент `member1` из коллекции `collection1`, то будет подготовлена новая коллекция всех значений `member1` для каждого объекта в `collection1`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ef078-126">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="ef078-127">Например, если `customers` является коллекцией типа `Customer` со свойством `Name` типа `string`, то выбор `Name` из `customers` даст коллекцию строк, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ef078-127">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="ef078-128">Можно также воспользоваться синтаксисом JOIN (FULL, INNER, LEFT, OUTER, ON и RIGHT).</span><span class="sxs-lookup"><span data-stu-id="ef078-128">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="ef078-129">ON требуется для внутренних соединений и недопустим для перекрестных соединений.</span><span class="sxs-lookup"><span data-stu-id="ef078-129">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="ef078-130">Предложения выбора строк и значений</span><span class="sxs-lookup"><span data-stu-id="ef078-130">Row and Value Select Clauses</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ef078-131">поддерживает два варианта предложения SELECT.</span><span class="sxs-lookup"><span data-stu-id="ef078-131">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="ef078-132">Первый вариант, строка Select, определяется с помощью ключевого слова SELECT и может использоваться для указания одного или нескольких значений, которые должны быть выбраны для проецирования. Поскольку оболочка строк неявно добавляется вокруг возвращаемых значений, результатом выражения запроса всегда является мультинабор строк.</span><span class="sxs-lookup"><span data-stu-id="ef078-132">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="ef078-133">Для каждого выражения запроса в выборе строки должен быть указан псевдоним.</span><span class="sxs-lookup"><span data-stu-id="ef078-133">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="ef078-134">Если псевдоним не указан, то[!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается создать его на основе правил создания псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="ef078-134">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="ef078-135">Другой тип предложения SELECT, выбор значения, идентифицируется ключевым словом SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="ef078-135">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="ef078-136">Он позволяет указать только одно значение и не добавляет оболочку строк.</span><span class="sxs-lookup"><span data-stu-id="ef078-136">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="ef078-137">Выбор строк всегда можно выразить в терминах VALUE SELECT, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ef078-137">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="ef078-138">Модификаторы All и Distinct</span><span class="sxs-lookup"><span data-stu-id="ef078-138">All and Distinct Modifiers</span></span>  

 <span data-ttu-id="ef078-139">В обоих вариантах предложения SELECT языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)] могут быть указаны модификаторы ALL и DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="ef078-139">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="ef078-140">Если задан модификатор DISTINCT, то повторяющиеся значения исключаются из коллекции, полученной в результате выполнения выражения запроса (до предложения SELECT включительно).</span><span class="sxs-lookup"><span data-stu-id="ef078-140">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="ef078-141">Если задан модификатор ALL, то исключение повторяющихся значений не выполняется. ALL является модификатором по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ef078-141">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="ef078-142">Отличия от языка Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef078-142">Differences from Transact-SQL</span></span>  

 <span data-ttu-id="ef078-143">В отличие от Transact-SQL, язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] не поддерживает использование аргумента «\*» в предложении SELECT.</span><span class="sxs-lookup"><span data-stu-id="ef078-143">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="ef078-144">Вместо этого в языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запросы могут проецировать целые записи, ссылаясь на псевдонимы коллекций из предложения FROM, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ef078-144">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="ef078-145">Предыдущее выражение запроса Transact-SQL выражается [!INCLUDE[esql](../../../../../../includes/esql-md.md)] следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ef078-145">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="ef078-146">Пример</span><span class="sxs-lookup"><span data-stu-id="ef078-146">Example</span></span>  

 <span data-ttu-id="ef078-147">В следующем запросе Entity SQL оператор SELECT используется для задания элементов, возвращаемых запросом.</span><span class="sxs-lookup"><span data-stu-id="ef078-147">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="ef078-148">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="ef078-148">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ef078-149">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="ef078-149">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ef078-150">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-150">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ef078-151">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ef078-151">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="ef078-152">См. также</span><span class="sxs-lookup"><span data-stu-id="ef078-152">See also</span></span>

- [<span data-ttu-id="ef078-153">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="ef078-153">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="ef078-154">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ef078-154">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ef078-155">В начало</span><span class="sxs-lookup"><span data-stu-id="ef078-155">TOP</span></span>](top-entity-sql.md)
