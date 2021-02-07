---
description: 'Дополнительные сведения: UNION (Entity SQL)'
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: f02b3d76d8c21848b7a1b7ef5e7bbf749aea5c0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673314"
---
# <a name="union-entity-sql"></a><span data-ttu-id="1e754-103">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e754-103">UNION (Entity SQL)</span></span>

<span data-ttu-id="1e754-104">Сводит результаты двух или более запросов в одну коллекцию.</span><span class="sxs-lookup"><span data-stu-id="1e754-104">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e754-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e754-105">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e754-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="1e754-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="1e754-107">Любое допустимое выражение запроса, возвращающее коллекцию для объединения с данной коллекцией. Все выражения должны быть одного типа с параметром `expression`либо базового или производного типа для типа этого параметра.</span><span class="sxs-lookup"><span data-stu-id="1e754-107">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="1e754-108">UNION</span><span class="sxs-lookup"><span data-stu-id="1e754-108">UNION</span></span>  
 <span data-ttu-id="1e754-109">Указывает на то, что несколько коллекций следует объединить и возвратить в виде единой коллекции.</span><span class="sxs-lookup"><span data-stu-id="1e754-109">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="1e754-110">ALL</span><span class="sxs-lookup"><span data-stu-id="1e754-110">ALL</span></span>  
 <span data-ttu-id="1e754-111">Указывает на то, что несколько коллекций следует объединить и возвратить в виде единой коллекции, включая повторения.</span><span class="sxs-lookup"><span data-stu-id="1e754-111">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="1e754-112">Если этот аргумент не указан, то повторения удаляются из итоговой коллекции.</span><span class="sxs-lookup"><span data-stu-id="1e754-112">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e754-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1e754-113">Return Value</span></span>  

 <span data-ttu-id="1e754-114">Коллекция того же типа, что и параметр `expression`, или же базового или производного типа для типа этого параметра.</span><span class="sxs-lookup"><span data-stu-id="1e754-114">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e754-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e754-115">Remarks</span></span>  

 <span data-ttu-id="1e754-116">UNION - это один из операторов работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1e754-116">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1e754-117">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="1e754-117">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1e754-118">Сведения о приоритетах для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора см. в разделе [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1e754-118">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e754-119">Пример</span><span class="sxs-lookup"><span data-stu-id="1e754-119">Example</span></span>  

 <span data-ttu-id="1e754-120">В следующем запросе Entity SQL оператор UNION ALL используется, чтобы объединить результаты двух запросов в единую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="1e754-120">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="1e754-121">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="1e754-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1e754-122">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="1e754-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1e754-123">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1e754-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1e754-124">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1e754-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="1e754-125">См. также</span><span class="sxs-lookup"><span data-stu-id="1e754-125">See also</span></span>

- [<span data-ttu-id="1e754-126">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1e754-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
