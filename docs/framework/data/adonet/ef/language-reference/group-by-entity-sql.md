---
description: 'Дополнительные сведения: GROUP BY (Entity SQL)'
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 16328b46a59a2a07622cda43dce30d8b4f1d3dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696936"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="e05aa-103">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e05aa-103">GROUP BY (Entity SQL)</span></span>

<span data-ttu-id="e05aa-104">Определяет группы, в которые должны быть помещены объекты, возвращаемые выражением запроса ([SELECT](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="e05aa-104">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05aa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e05aa-105">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e05aa-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e05aa-106">Arguments</span></span>  

 `aliasedExpression`  
 <span data-ttu-id="e05aa-107">Любое допустимое выражение запроса, в котором выполняется группирование.</span><span class="sxs-lookup"><span data-stu-id="e05aa-107">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="e05aa-108">Аргумент`expression` может быть свойством или нестатистическим выражением, ссылающимся на свойство, которое возвращается предложением FROM.</span><span class="sxs-lookup"><span data-stu-id="e05aa-108">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="e05aa-109">Каждое выражение в предложении GROUP BY должно иметь тип, который может быть проверен на равенство.</span><span class="sxs-lookup"><span data-stu-id="e05aa-109">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="e05aa-110">Такими типами обычно являются скалярные примитивы - числа, строки и даты.</span><span class="sxs-lookup"><span data-stu-id="e05aa-110">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="e05aa-111">Операция GROUP BY не может быть выполнена по коллекциям.</span><span class="sxs-lookup"><span data-stu-id="e05aa-111">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e05aa-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e05aa-112">Remarks</span></span>  

 <span data-ttu-id="e05aa-113">Если в предложение SELECT включены агрегатные функции \<select list> , GROUP BY вычисляет сводное значение для каждой группы.</span><span class="sxs-lookup"><span data-stu-id="e05aa-113">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="e05aa-114">Если задано предложение GROUP BY, то каждое имя свойства во всех нестатистических выражениях в списке выбора должно быть включено в список GROUP BY либо выражение GROUP BY должно точно соответствовать выражению списка выбора.</span><span class="sxs-lookup"><span data-stu-id="e05aa-114">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e05aa-115">Если предложение ORDER BY не задано, то группы, возвращаемые предложением GROUP BY, не упорядочиваются.</span><span class="sxs-lookup"><span data-stu-id="e05aa-115">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="e05aa-116">Рекомендуется всегда пользоваться предложением ORDER BY, чтобы данные были представлены в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="e05aa-116">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="e05aa-117">Если предложение GROUP BY задано явным или неявным образом (например, в силу присутствия в запросе предложения HAVING), то текущая область является скрытой и появляется новая область.</span><span class="sxs-lookup"><span data-stu-id="e05aa-117">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="e05aa-118">Предложения SELECT, HAVING и ORDER BY больше не смогут ссылаться на имена элементов в предложении FROM.</span><span class="sxs-lookup"><span data-stu-id="e05aa-118">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="e05aa-119">Ссылка будет возможна только на сами выражения группирования.</span><span class="sxs-lookup"><span data-stu-id="e05aa-119">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="e05aa-120">Для этого каждому выражению группирования можно присвоить новые имена (псевдонимы).</span><span class="sxs-lookup"><span data-stu-id="e05aa-120">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="e05aa-121">Если для выражения группирования не задан псевдоним, то [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается создать псевдоним согласно правилам создания псевдонимов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e05aa-121">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="e05aa-122">Выражения в предложении GROUP BY не могут ссылаться на имена, определенные ранее в том же предложении GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="e05aa-122">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="e05aa-123">Помимо имен группирований, в предложениях SELECT, HAVING и ORDER BY могут быть указаны статистические функции.</span><span class="sxs-lookup"><span data-stu-id="e05aa-123">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="e05aa-124">Статистическая функция содержит выражение, которое вычисляется для каждого элемента в группе.</span><span class="sxs-lookup"><span data-stu-id="e05aa-124">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="e05aa-125">Статистический оператор объединяет значения этих выражений (обычно, но не всегда) в единственное значение.</span><span class="sxs-lookup"><span data-stu-id="e05aa-125">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="e05aa-126">Статистическое выражение может ссылаться на исходные имена элементов, которые видны в родительской области, или на любые новые имена, указанные в самом предложении GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="e05aa-126">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="e05aa-127">Хотя статистические выражения указываются в предложениях SELECT, HAVING и ORDER BY, они фактически вычисляются в той же области, что и выражения группирования, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e05aa-127">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="e05aa-128">В этом запросе предложение GROUP BY применяется для создания отчета о стоимости всех заказов с разбивкой по товарам.</span><span class="sxs-lookup"><span data-stu-id="e05aa-128">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="e05aa-129">Товару в выражении группирования присваивается имя `name` , которое затем указывается в списке выбора.</span><span class="sxs-lookup"><span data-stu-id="e05aa-129">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="e05aa-130">Запрос также содержит в списке выбора статистическую функцию `sum` , которая внутренним образом ссылается на цену и количество в строке заказа.</span><span class="sxs-lookup"><span data-stu-id="e05aa-130">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="e05aa-131">Каждое ключевое выражение GROUP BY должно содержать как минимум одну ссылку на область ввода.</span><span class="sxs-lookup"><span data-stu-id="e05aa-131">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="e05aa-132">Пример использования GROUP BY см. в статье [HAVING](having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e05aa-132">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e05aa-133">Пример</span><span class="sxs-lookup"><span data-stu-id="e05aa-133">Example</span></span>  

 <span data-ttu-id="e05aa-134">В следующем запросе Entity SQL оператор GROUP BY задает группы, в которые помещаются объекты, возвращаемые запросом.</span><span class="sxs-lookup"><span data-stu-id="e05aa-134">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="e05aa-135">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="e05aa-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e05aa-136">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="e05aa-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e05aa-137">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e05aa-137">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e05aa-138">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e05aa-138">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="e05aa-139">См. также</span><span class="sxs-lookup"><span data-stu-id="e05aa-139">See also</span></span>

- [<span data-ttu-id="e05aa-140">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e05aa-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e05aa-141">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="e05aa-141">Query Expressions</span></span>](query-expressions-entity-sql.md)
