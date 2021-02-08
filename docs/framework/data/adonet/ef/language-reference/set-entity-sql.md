---
description: 'Дополнительные сведения: SET (Entity SQL)'
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 80be5b76e654c39776d97413c4ece5a8f3df8d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768029"
---
# <a name="set-entity-sql"></a><span data-ttu-id="505c2-103">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="505c2-103">SET (Entity SQL)</span></span>

<span data-ttu-id="505c2-104">Выражение SET используется для преобразования коллекции объектов в набор путем получения новой коллекции, из которой удалены все повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="505c2-104">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="505c2-105">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="505c2-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="505c2-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="505c2-107">Любое допустимое выражение запроса, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="505c2-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="505c2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="505c2-108">Remarks</span></span>  

 <span data-ttu-id="505c2-109">Выражение набора `SET(c)` логически эквивалентно следующей инструкции SELECT:</span><span class="sxs-lookup"><span data-stu-id="505c2-109">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="505c2-110">Оператор`SET` - это один из операторов работы с наборами в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="505c2-110">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="505c2-111">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="505c2-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="505c2-112">Дополнительные сведения см. в разделе, [за исключением](except-entity-sql.md) сведений о приоритете для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора.</span><span class="sxs-lookup"><span data-stu-id="505c2-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="505c2-113">Пример</span><span class="sxs-lookup"><span data-stu-id="505c2-113">Example</span></span>  

 <span data-ttu-id="505c2-114">В следующем запросе Entity SQL используется выражение SET для преобразования коллекции объектов в набор.</span><span class="sxs-lookup"><span data-stu-id="505c2-114">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="505c2-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="505c2-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="505c2-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="505c2-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="505c2-117">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="505c2-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="505c2-118">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="505c2-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="505c2-119">См. также</span><span class="sxs-lookup"><span data-stu-id="505c2-119">See also</span></span>

- [<span data-ttu-id="505c2-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="505c2-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
