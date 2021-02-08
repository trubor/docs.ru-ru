---
description: 'Дополнительные сведения: СВЕДЕНИЕ (Entity SQL)'
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 3701fbdf481024c799b4cdc6f109bae9fc226609
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786359"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="a73cd-103">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a73cd-103">FLATTEN (Entity SQL)</span></span>

<span data-ttu-id="a73cd-104">Преобразовывает коллекцию коллекций в плоскую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="a73cd-104">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="a73cd-105">Новая коллекция содержит все те же элементы, что и старая коллекция, но без структуры вложения.</span><span class="sxs-lookup"><span data-stu-id="a73cd-105">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73cd-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a73cd-106">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="a73cd-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="a73cd-107">Arguments</span></span>  

 `collection`  
 <span data-ttu-id="a73cd-108">Любое допустимое выражение, которое возвращает коллекцию коллекций значений, предназначенных для сведения в плоскую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="a73cd-108">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a73cd-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a73cd-109">Remarks</span></span>  

 <span data-ttu-id="a73cd-110">Оператор`FLATTEN` - это один из операторов работы с наборами в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a73cd-110">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a73cd-111">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="a73cd-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a73cd-112">Дополнительные сведения см. в разделе, [за исключением](except-entity-sql.md) сведений о приоритете для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора.</span><span class="sxs-lookup"><span data-stu-id="a73cd-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73cd-113">Пример</span><span class="sxs-lookup"><span data-stu-id="a73cd-113">Example</span></span>  

 <span data-ttu-id="a73cd-114">В следующем запросе Entity SQL используется оператор `FLATTEN` для преобразования коллекции коллекций в плоскую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="a73cd-114">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="a73cd-115">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="a73cd-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a73cd-116">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a73cd-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a73cd-117">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="a73cd-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="a73cd-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a73cd-118">See also</span></span>

- [<span data-ttu-id="a73cd-119">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a73cd-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
