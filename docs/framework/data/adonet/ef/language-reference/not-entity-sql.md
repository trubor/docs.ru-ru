---
description: Дополнительные сведения:! (NOT) (язык Entity SQL)
title: '! (NOT) (язык Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 648cc4ff73769ae280570b2d42934b2001fa5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696455"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="3214d-105">!</span><span class="sxs-lookup"><span data-stu-id="3214d-105">!</span></span> <span data-ttu-id="3214d-106">(NOT) (язык Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3214d-106">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="3214d-107">Изменяет значение выражения типа `Boolean` на обратное.</span><span class="sxs-lookup"><span data-stu-id="3214d-107">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3214d-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3214d-108">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="3214d-109">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3214d-109">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="3214d-110">Любое допустимое выражение, возвращающее значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="3214d-110">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3214d-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3214d-111">Remarks</span></span>  

 <span data-ttu-id="3214d-112">Восклицательный знак (!) имеет ту же функциональность, что и оператор NOT.</span><span class="sxs-lookup"><span data-stu-id="3214d-112">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3214d-113">Пример</span><span class="sxs-lookup"><span data-stu-id="3214d-113">Example</span></span>  

 <span data-ttu-id="3214d-114">Следующий запрос Entity SQL использует оператор NOT, чтобы изменить на обратное выражение типа `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3214d-114">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="3214d-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="3214d-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3214d-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="3214d-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3214d-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3214d-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3214d-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="3214d-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="3214d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3214d-119">See also</span></span>

- [<span data-ttu-id="3214d-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3214d-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
