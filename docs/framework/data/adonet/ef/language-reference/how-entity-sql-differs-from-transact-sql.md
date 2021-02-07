---
description: Дополнительные сведения о том, как Entity SQL отличается от языка Transact-SQL.
title: Отличия Entity SQL от Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 349dd64cc0e548ab0dc8d0e66e8bb14b58912d09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696871"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="c19ae-103">Отличие Entity SQL от Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c19ae-103">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="c19ae-104">В этой статье описываются различия между Entity SQL и Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-104">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="c19ae-105">Поддержка наследования и связей</span><span class="sxs-lookup"><span data-stu-id="c19ae-105">Inheritance and Relationships Support</span></span>  

 <span data-ttu-id="c19ae-106">Entity SQL работает непосредственно с концептуальными схемами сущностей и поддерживает такие функции концептуальной модели, как наследование и связи.</span><span class="sxs-lookup"><span data-stu-id="c19ae-106">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="c19ae-107">При работе с наследованием часто полезно выбрать экземпляры подтипа из коллекции экземпляров супертипа.</span><span class="sxs-lookup"><span data-stu-id="c19ae-107">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="c19ae-108">Оператор [OFTYPE](oftype-entity-sql.md) в Entity SQL (аналогично `oftype` в последовательности C#) предоставляет эту возможность.</span><span class="sxs-lookup"><span data-stu-id="c19ae-108">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="c19ae-109">Поддержка коллекций</span><span class="sxs-lookup"><span data-stu-id="c19ae-109">Support for Collections</span></span>  

 <span data-ttu-id="c19ae-110">Entity SQL считает коллекции сущностями первого класса.</span><span class="sxs-lookup"><span data-stu-id="c19ae-110">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="c19ae-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="c19ae-111">For example:</span></span>  
  
- <span data-ttu-id="c19ae-112">Выражения коллекций допускаются в предложении `from`.</span><span class="sxs-lookup"><span data-stu-id="c19ae-112">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="c19ae-113">Вложенные запросы `in` и `exists` были обобщены, чтобы разрешить любые коллекции.</span><span class="sxs-lookup"><span data-stu-id="c19ae-113">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="c19ae-114">Вложенный запрос - один из видов коллекций.</span><span class="sxs-lookup"><span data-stu-id="c19ae-114">A subquery is one kind of collection.</span></span> <span data-ttu-id="c19ae-115">`e1 in e2` и `exists(e)` являются конструкциями Entity SQL для выполнения этих операций.</span><span class="sxs-lookup"><span data-stu-id="c19ae-115">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="c19ae-116">Операторы работы с наборами, такие как `union`, `intersect` и `except`, теперь работают с коллекциями.</span><span class="sxs-lookup"><span data-stu-id="c19ae-116">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="c19ae-117">Операции соединения с коллекциями.</span><span class="sxs-lookup"><span data-stu-id="c19ae-117">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="c19ae-118">Поддержка выражений</span><span class="sxs-lookup"><span data-stu-id="c19ae-118">Support for Expressions</span></span>  

 <span data-ttu-id="c19ae-119">Transact-SQL содержит вложенные запросы (таблицы) и выражения (строки и столбцы).</span><span class="sxs-lookup"><span data-stu-id="c19ae-119">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="c19ae-120">Для поддержки коллекций и вложенных коллекций Entity SQL делает все выражение.</span><span class="sxs-lookup"><span data-stu-id="c19ae-120">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="c19ae-121">Entity SQL является более композицией, чем Transact-SQL — каждое выражение можно использовать в любом месте.</span><span class="sxs-lookup"><span data-stu-id="c19ae-121">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="c19ae-122">Результатом выражения запроса всегда является коллекция проецируемых типов, которая может быть использована везде, где разрешено выражение коллекции.</span><span class="sxs-lookup"><span data-stu-id="c19ae-122">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="c19ae-123">Дополнительные сведения о выражениях Transact-SQL, которые не поддерживаются в Entity SQL, см. в разделе [Неподдерживаемые выражения](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c19ae-123">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c19ae-124">Ниже приведены все допустимые Entity SQL запросы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-124">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="c19ae-125">Единая обработка вложенных запросов</span><span class="sxs-lookup"><span data-stu-id="c19ae-125">Uniform Treatment of Subqueries</span></span>  

 <span data-ttu-id="c19ae-126">Учитывая его акцент на таблицах, Transact-SQL выполняет контекстную интерпретацию вложенных запросов.</span><span class="sxs-lookup"><span data-stu-id="c19ae-126">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="c19ae-127">Например, вложенный запрос в `from` предложении считается мультинабором (таблицей).</span><span class="sxs-lookup"><span data-stu-id="c19ae-127">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="c19ae-128">Тот же вложенный запрос в предложении `select` считается скалярным вложенным запросом.</span><span class="sxs-lookup"><span data-stu-id="c19ae-128">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="c19ae-129">Аналогичным образом вложенный запрос, используемый в левой части `in` оператора, считается скалярным вложенным запросом, тогда как правая часть должна быть вложенным запросом мультинабора.</span><span class="sxs-lookup"><span data-stu-id="c19ae-129">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="c19ae-130">Entity SQL устраняет эти различия.</span><span class="sxs-lookup"><span data-stu-id="c19ae-130">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="c19ae-131">Выражение имеет единую интерпретацию, которая не зависит от контекста, в котором оно использовано.</span><span class="sxs-lookup"><span data-stu-id="c19ae-131">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="c19ae-132">Entity SQL считает, что все вложенные запросы являются вложенными запросами мультинабора.</span><span class="sxs-lookup"><span data-stu-id="c19ae-132">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="c19ae-133">Если из вложенного запроса требуется скалярное значение, Entity SQL предоставляет `anyelement` оператор, который работает с коллекцией (в данном случае вложенный запрос), и извлекает одноэлементное значение из коллекции.</span><span class="sxs-lookup"><span data-stu-id="c19ae-133">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="c19ae-134">Устранение неявных приведений для вложенных запросов</span><span class="sxs-lookup"><span data-stu-id="c19ae-134">Avoiding Implicit Coercions for Subqueries</span></span>  

 <span data-ttu-id="c19ae-135">Побочный эффект единообразной обработки вложенных запросов - неявное преобразование вложенных запросов к скалярным значениям.</span><span class="sxs-lookup"><span data-stu-id="c19ae-135">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="c19ae-136">В частности, в языке Transact-SQL мультинабор строк (с одним полем) неявно преобразуется в скалярное значение, тип данных которого является значением поля.</span><span class="sxs-lookup"><span data-stu-id="c19ae-136">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="c19ae-137">Entity SQL не поддерживает это неявное приведение.</span><span class="sxs-lookup"><span data-stu-id="c19ae-137">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="c19ae-138">Entity SQL предоставляет `ANYELEMENT` оператор для извлечения одноэлементного значения из коллекции и `select value` предложение во избежание создания оболочки строк во время выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="c19ae-138">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="c19ae-139">Выбранное значение: устранение неявной оболочки строк</span><span class="sxs-lookup"><span data-stu-id="c19ae-139">Select Value: Avoiding the Implicit Row Wrapper</span></span>  

 <span data-ttu-id="c19ae-140">Предложение SELECT в вложенном запросе Transact-SQL неявно создает оболочку строк вокруг элементов в предложении.</span><span class="sxs-lookup"><span data-stu-id="c19ae-140">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="c19ae-141">Это означает, что нельзя создавать коллекции скалярных величин или объектов.</span><span class="sxs-lookup"><span data-stu-id="c19ae-141">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="c19ae-142">Transact-SQL позволяет неявное приведение между `rowtype` с одним полем и одноэлементным значением одного и того же типа данных.</span><span class="sxs-lookup"><span data-stu-id="c19ae-142">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="c19ae-143">Entity SQL предоставляет `select value` предложение для пропуска неявной конструкции строки.</span><span class="sxs-lookup"><span data-stu-id="c19ae-143">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="c19ae-144">В предложении `select value` можно указать только один элемент.</span><span class="sxs-lookup"><span data-stu-id="c19ae-144">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="c19ae-145">При использовании такого предложения оболочка строк не создается вокруг элементов в `select` предложении, а коллекция требуемой формы может быть создана, например `select value a` .</span><span class="sxs-lookup"><span data-stu-id="c19ae-145">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="c19ae-146">Entity SQL также предоставляет конструктор строк для создания произвольных строк.</span><span class="sxs-lookup"><span data-stu-id="c19ae-146">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="c19ae-147">`select` принимает один или несколько элементов в проекции и приводит к записи данных с полями:</span><span class="sxs-lookup"><span data-stu-id="c19ae-147">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="c19ae-148">Левая корреляция и задание псевдонимов</span><span class="sxs-lookup"><span data-stu-id="c19ae-148">Left Correlation and Aliasing</span></span>  

 <span data-ttu-id="c19ae-149">В языке Transact-SQL выражения в заданной области (одно предложение вроде `select` или `from` ) не могут ссылаться на выражения, определенные ранее в той же области.</span><span class="sxs-lookup"><span data-stu-id="c19ae-149">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="c19ae-150">Некоторые диалекты SQL (включая Transact-SQL) поддерживают ограниченные формы в `from` предложении.</span><span class="sxs-lookup"><span data-stu-id="c19ae-150">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="c19ae-151">Entity SQL обобщает левые корреляции в `from` предложении и обрабатывает их единообразно.</span><span class="sxs-lookup"><span data-stu-id="c19ae-151">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="c19ae-152">Выражения в предложении `from` могут содержать ссылки на более ранние определения (определения слева) в том же предложении без дополнительных синтаксических конструкций.</span><span class="sxs-lookup"><span data-stu-id="c19ae-152">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="c19ae-153">Entity SQL также накладывает дополнительные ограничения на запросы, включающие `group by` предложения.</span><span class="sxs-lookup"><span data-stu-id="c19ae-153">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="c19ae-154">Выражения в `select` предложении и `having` предложении таких запросов могут ссылаться только на `group by` ключи через их псевдонимы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-154">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="c19ae-155">Следующая конструкция допустима в Transact-SQL, но не в Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="c19ae-155">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="c19ae-156">Для этого в Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="c19ae-156">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="c19ae-157">Ссылочные столбцы (свойства) таблиц (коллекций)</span><span class="sxs-lookup"><span data-stu-id="c19ae-157">Referencing Columns (Properties) of Tables (Collections)</span></span>  

 <span data-ttu-id="c19ae-158">Все ссылки на столбцы в Entity SQL должны уточняться псевдонимом таблицы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-158">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="c19ae-159">Следующая конструкция (при условии, что `a` является допустимым столбцом таблицы `T` ) допустима в TRANSACT-SQL, но не в Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-159">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="c19ae-160">Форма Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c19ae-160">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="c19ae-161">Псевдонимы таблицы в предложении `from` необязательны.</span><span class="sxs-lookup"><span data-stu-id="c19ae-161">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="c19ae-162">Имя таблицы используется как неявный псевдоним.</span><span class="sxs-lookup"><span data-stu-id="c19ae-162">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="c19ae-163">Entity SQL также поддерживает следующие формы:</span><span class="sxs-lookup"><span data-stu-id="c19ae-163">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="c19ae-164">Перемещение по объектам</span><span class="sxs-lookup"><span data-stu-id="c19ae-164">Navigation Through Objects</span></span>  

 <span data-ttu-id="c19ae-165">В Transact-SQL используется нотация "." для ссылок на столбцы (строки) таблицы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-165">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="c19ae-166">Entity SQL расширяет эту нотацию (заимствованную из языков программирования) для поддержки навигации по свойствам объекта.</span><span class="sxs-lookup"><span data-stu-id="c19ae-166">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="c19ae-167">Например, если `p` является выражением типа Person, ниже приведен синтаксис Entity SQL для ссылки на город адреса этого человека.</span><span class="sxs-lookup"><span data-stu-id="c19ae-167">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="c19ae-168">Нет поддержки для \*</span><span class="sxs-lookup"><span data-stu-id="c19ae-168">No Support for \*</span></span>  

 <span data-ttu-id="c19ae-169">Transact-SQL поддерживает неполный \* синтаксис в качестве псевдонима для всей строки и полный \* синтаксис (t. \* ) в качестве ярлыка для полей этой таблицы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-169">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="c19ae-170">Кроме того, Transact-SQL позволяет выполнять специальные \* статистические функции Count (), которые включают значения NULL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-170">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="c19ae-171">Entity SQL не поддерживает конструкцию \*.</span><span class="sxs-lookup"><span data-stu-id="c19ae-171">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="c19ae-172">Запросы Transact-SQL к форме `select * from T` и `select T1.* from T1, T2...` могут быть выражены в Entity SQL как `select value t from T as t` и `select value t1 from T1 as t1, T2 as t2...` соответственно.</span><span class="sxs-lookup"><span data-stu-id="c19ae-172">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="c19ae-173">Эти конструкции также обеспечивают наследование (заменяемость значений), в то время как варианты `select *` ограничены свойствами верхнего уровня объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="c19ae-173">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="c19ae-174">Entity SQL не поддерживает `count(*)` статистическую обработку.</span><span class="sxs-lookup"><span data-stu-id="c19ae-174">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="c19ae-175">Взамен рекомендуется использовать `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="c19ae-175">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="c19ae-176">Изменения на предложение Group By</span><span class="sxs-lookup"><span data-stu-id="c19ae-176">Changes to Group By</span></span>  

 <span data-ttu-id="c19ae-177">Entity SQL поддерживает псевдонимы `group by` ключей.</span><span class="sxs-lookup"><span data-stu-id="c19ae-177">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="c19ae-178">Выражения в предложении `select` и предложении `having` таких запросов должны ссылаться на ключи `group by` через псевдонимы.</span><span class="sxs-lookup"><span data-stu-id="c19ae-178">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="c19ae-179">Например, следующий синтаксис Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="c19ae-179">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="c19ae-180">... эквивалентен следующему языку Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="c19ae-180">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="c19ae-181">Статистические функции на основе коллекций</span><span class="sxs-lookup"><span data-stu-id="c19ae-181">Collection-Based Aggregates</span></span>  

 <span data-ttu-id="c19ae-182">Entity SQL поддерживает два вида агрегатов.</span><span class="sxs-lookup"><span data-stu-id="c19ae-182">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="c19ae-183">Статистические функции на основе коллекций работают с коллекциями и возвращают результат статистической обработки.</span><span class="sxs-lookup"><span data-stu-id="c19ae-183">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="c19ae-184">Они могут применяться в любом месте в запросе и не требуют предложения `group by`.</span><span class="sxs-lookup"><span data-stu-id="c19ae-184">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="c19ae-185">Пример:</span><span class="sxs-lookup"><span data-stu-id="c19ae-185">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="c19ae-186">Entity SQL также поддерживает статистические выражения в стиле SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-186">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="c19ae-187">Пример:</span><span class="sxs-lookup"><span data-stu-id="c19ae-187">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="c19ae-188">Использование предложения ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c19ae-188">ORDER BY Clause Usage</span></span>  

<span data-ttu-id="c19ae-189">Transact-SQL позволяет `ORDER BY` указывать предложения только в самом верхнем `SELECT .. FROM .. WHERE` блоке.</span><span class="sxs-lookup"><span data-stu-id="c19ae-189">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="c19ae-190">В Entity SQL можно использовать вложенное `ORDER BY` выражение, которое можно поместить в любом месте запроса, но упорядочение во вложенном запросе не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="c19ae-190">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="c19ae-191">Идентификаторы</span><span class="sxs-lookup"><span data-stu-id="c19ae-191">Identifiers</span></span>  

 <span data-ttu-id="c19ae-192">В Transact-SQL сравнение идентификаторов основано на параметрах сортировки текущей базы данных.</span><span class="sxs-lookup"><span data-stu-id="c19ae-192">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="c19ae-193">В Entity SQL идентификаторы всегда не учитывают регистр и диакритические знаки (т. е. Entity SQL различаются символы с диакритическими знаками и без них, например, "a" не равно "ấ").</span><span class="sxs-lookup"><span data-stu-id="c19ae-193">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="c19ae-194">Entity SQL воспринимает версии букв, которые выглядят одинаково, но находятся в разных кодовых страницах с разными символами.</span><span class="sxs-lookup"><span data-stu-id="c19ae-194">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="c19ae-195">Дополнительные сведения см. в разделе [input character set](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c19ae-195">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="c19ae-196">Функциональность Transact-SQL, недоступная в Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c19ae-196">Transact-SQL Functionality Not Available in Entity SQL</span></span>  

 <span data-ttu-id="c19ae-197">Следующие функциональные возможности Transact-SQL недоступны в Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-197">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="c19ae-198">DML</span><span class="sxs-lookup"><span data-stu-id="c19ae-198">DML</span></span>  
 <span data-ttu-id="c19ae-199">В настоящее время Entity SQL не поддерживает инструкции DML (INSERT, Update, DELETE).</span><span class="sxs-lookup"><span data-stu-id="c19ae-199">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="c19ae-200">DDL</span><span class="sxs-lookup"><span data-stu-id="c19ae-200">DDL</span></span>  
 <span data-ttu-id="c19ae-201">Entity SQL не обеспечивает поддержку DDL в текущей версии.</span><span class="sxs-lookup"><span data-stu-id="c19ae-201">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="c19ae-202">Командное программирование</span><span class="sxs-lookup"><span data-stu-id="c19ae-202">Imperative Programming</span></span>  
 <span data-ttu-id="c19ae-203">Entity SQL не обеспечивает поддержку императивного программирования, в отличие от Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-203">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="c19ae-204">Используйте вместо этого языки программирования.</span><span class="sxs-lookup"><span data-stu-id="c19ae-204">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="c19ae-205">Функции группирования</span><span class="sxs-lookup"><span data-stu-id="c19ae-205">Grouping Functions</span></span>  
 <span data-ttu-id="c19ae-206">Entity SQL еще не предоставляет поддержку группирования функций (например, CUBE, ROLLUP и GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="c19ae-206">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="c19ae-207">Аналитические функции</span><span class="sxs-lookup"><span data-stu-id="c19ae-207">Analytic Functions</span></span>  
 <span data-ttu-id="c19ae-208">Entity SQL не предоставляет поддержку аналитических функций.</span><span class="sxs-lookup"><span data-stu-id="c19ae-208">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="c19ae-209">Встроенные функции, операторы</span><span class="sxs-lookup"><span data-stu-id="c19ae-209">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="c19ae-210">Entity SQL поддерживает подмножество встроенных функций и операторов Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-210">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="c19ae-211">Вероятно, эти операторы и функции будут реализованы ведущими поставщиками хранилищ.</span><span class="sxs-lookup"><span data-stu-id="c19ae-211">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="c19ae-212">Entity SQL использует зависящие от хранилища функции, объявленные в манифесте поставщика.</span><span class="sxs-lookup"><span data-stu-id="c19ae-212">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="c19ae-213">Кроме того, Entity Framework позволяет объявлять встроенные и определяемые пользователем существующие функции хранилища для использования Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="c19ae-213">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="c19ae-214">Указания</span><span class="sxs-lookup"><span data-stu-id="c19ae-214">Hints</span></span>  
 <span data-ttu-id="c19ae-215">Entity SQL не предоставляет механизмов для указания запросов.</span><span class="sxs-lookup"><span data-stu-id="c19ae-215">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="c19ae-216">Пакетирование результатов запроса</span><span class="sxs-lookup"><span data-stu-id="c19ae-216">Batching Query Results</span></span>  
 <span data-ttu-id="c19ae-217">Entity SQL не поддерживает пакетную обработку результатов запросов.</span><span class="sxs-lookup"><span data-stu-id="c19ae-217">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="c19ae-218">Например, ниже приведен допустимый Transact-SQL (отправка в виде пакета):</span><span class="sxs-lookup"><span data-stu-id="c19ae-218">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="c19ae-219">Однако эквивалентные Entity SQL не поддерживаются:</span><span class="sxs-lookup"><span data-stu-id="c19ae-219">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="c19ae-220">Entity SQL поддерживает только одну инструкцию запроса с результатами для каждой команды.</span><span class="sxs-lookup"><span data-stu-id="c19ae-220">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19ae-221">См. также</span><span class="sxs-lookup"><span data-stu-id="c19ae-221">See also</span></span>

- [<span data-ttu-id="c19ae-222">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c19ae-222">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="c19ae-223">Неподдерживаемые выражения</span><span class="sxs-lookup"><span data-stu-id="c19ae-223">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
