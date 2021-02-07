---
description: 'Дополнительные сведения о: HAVING (Entity SQL)'
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 70ace20d67e93aa051873d2b32a49f560902e63d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696884"
---
# <a name="having-entity-sql"></a><span data-ttu-id="5ed34-103">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5ed34-103">HAVING (Entity SQL)</span></span>

<span data-ttu-id="5ed34-104">Определяет условие поиска для группы или статистического выражения.</span><span class="sxs-lookup"><span data-stu-id="5ed34-104">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed34-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ed34-105">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ed34-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5ed34-106">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="5ed34-107">Определяет условие поиска, которому должна соответствовать группа или статистическое выражение.</span><span class="sxs-lookup"><span data-stu-id="5ed34-107">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="5ed34-108">Если предложение HAVING используется в сочетании с GROUP BY ALL, то оно переопределяет ALL.</span><span class="sxs-lookup"><span data-stu-id="5ed34-108">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed34-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="5ed34-109">Remarks</span></span>  

 <span data-ttu-id="5ed34-110">Предложение HAVING позволяет указать дополнительное условие фильтрации для результатов группирования.</span><span class="sxs-lookup"><span data-stu-id="5ed34-110">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="5ed34-111">Если в выражении запроса не указано предложение GROUP BY, то предполагается неявным образом созданная группа, состоящая из одного набора.</span><span class="sxs-lookup"><span data-stu-id="5ed34-111">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ed34-112">HAVING можно использовать только с инструкцией [SELECT](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="5ed34-112">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="5ed34-113">Если [Group By](group-by-entity-sql.md) не используется, то ведет себя как предложение WHERE.</span><span class="sxs-lookup"><span data-stu-id="5ed34-113">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="5ed34-114">Предложение HAVING работает точно так же, как и предложение WHERE, за исключением того, что применяется после операции GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="5ed34-114">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="5ed34-115">Это означает, что предложение HAVING может создавать ссылки только на псевдонимы и агрегаты группирования, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="5ed34-115">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="5ed34-116">Предыдущий пример производится ограничение до тех групп, которые содержат более одного товара.</span><span class="sxs-lookup"><span data-stu-id="5ed34-116">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ed34-117">Пример</span><span class="sxs-lookup"><span data-stu-id="5ed34-117">Example</span></span>  

 <span data-ttu-id="5ed34-118">В следующем запросе Entity SQL операторы HAVING и GROUP BY задают условие поиска для группы или статистического выражения.</span><span class="sxs-lookup"><span data-stu-id="5ed34-118">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="5ed34-119">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="5ed34-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5ed34-120">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="5ed34-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5ed34-121">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5ed34-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="5ed34-122">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="5ed34-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="5ed34-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5ed34-123">See also</span></span>

- [<span data-ttu-id="5ed34-124">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5ed34-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5ed34-125">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="5ed34-125">Query Expressions</span></span>](query-expressions-entity-sql.md)
