---
description: 'Дополнительные сведения о: INTERSECT (Entity SQL)'
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 45c0434f6fc0ed6c110162d7e34d76c336635b0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748518"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="726b1-103">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="726b1-103">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="726b1-104">Возвращает коллекцию различных значений, возвращаемых выражениями запроса, указанных как слева, так и справа от операнда INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="726b1-104">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="726b1-105">Все выражения должны иметь тот же тип, что и аргумент `expression`, или принадлежать к базовому или производному типу для типа этого аргумента.</span><span class="sxs-lookup"><span data-stu-id="726b1-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726b1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="726b1-106">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="726b1-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="726b1-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="726b1-108">Любое допустимое выражение запроса, которое возвращает коллекцию для сравнения с коллекцией, возвращенной другим выражением запроса.</span><span class="sxs-lookup"><span data-stu-id="726b1-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="726b1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="726b1-109">Return Value</span></span>  

 <span data-ttu-id="726b1-110">Коллекция того же типа, что и параметр `expression`, или же базового или производного типа для типа этого параметра.</span><span class="sxs-lookup"><span data-stu-id="726b1-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="726b1-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="726b1-111">Remarks</span></span>  

 <span data-ttu-id="726b1-112">INTERSECT - один из операторов для работы с наборами в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="726b1-112">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="726b1-113">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="726b1-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="726b1-114">Сведения о приоритетах для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора см. в разделе [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="726b1-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="726b1-115">Пример</span><span class="sxs-lookup"><span data-stu-id="726b1-115">Example</span></span>  

 <span data-ttu-id="726b1-116">Следующий запрос Entity SQL использует оператор INTERSECT, чтобы вернуть коллекцию различных значений, возвращаемых выражениями запроса, указанных как слева, так и справа от операнда INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="726b1-116">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="726b1-117">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="726b1-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="726b1-118">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="726b1-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="726b1-119">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="726b1-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="726b1-120">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="726b1-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="726b1-121">См. также</span><span class="sxs-lookup"><span data-stu-id="726b1-121">See also</span></span>

- [<span data-ttu-id="726b1-122">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="726b1-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
