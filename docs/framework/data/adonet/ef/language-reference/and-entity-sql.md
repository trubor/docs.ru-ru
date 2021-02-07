---
description: 'Дополнительные сведения: &amp; &amp; (и) (Entity SQL)'
title: '&amp;&amp; ПЕРЕТАСКИВАНИ (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 14fc6bc3f58ac78cb9806a7f421db87bbad048ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697183"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="5626f-103">&amp;&amp; ПЕРЕТАСКИВАНИ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5626f-103">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="5626f-104">Возвращает значение `true` если оба выражения `true`; в противном случае возвращает значение `false` или `NULL`.</span><span class="sxs-lookup"><span data-stu-id="5626f-104">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5626f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5626f-105">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="5626f-106">or</span><span class="sxs-lookup"><span data-stu-id="5626f-106">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5626f-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5626f-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="5626f-108">Любое допустимое выражение, возвращающее значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="5626f-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5626f-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="5626f-109">Remarks</span></span>  

 <span data-ttu-id="5626f-110">Два амперсанда (&&) действуют так же, как оператор AND.</span><span class="sxs-lookup"><span data-stu-id="5626f-110">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="5626f-111">В следующей таблице указаны возможные входные значения и возвращаемые типы.</span><span class="sxs-lookup"><span data-stu-id="5626f-111">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="5626f-112">TRUE</span><span class="sxs-lookup"><span data-stu-id="5626f-112">TRUE</span></span>|<span data-ttu-id="5626f-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="5626f-113">FALSE</span></span>|<span data-ttu-id="5626f-114">NULL</span><span class="sxs-lookup"><span data-stu-id="5626f-114">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="5626f-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="5626f-115">FALSE</span></span>|<span data-ttu-id="5626f-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="5626f-116">FALSE</span></span>|<span data-ttu-id="5626f-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="5626f-117">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="5626f-118">NULL</span><span class="sxs-lookup"><span data-stu-id="5626f-118">NULL</span></span>|<span data-ttu-id="5626f-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="5626f-119">FALSE</span></span>|<span data-ttu-id="5626f-120">NULL</span><span class="sxs-lookup"><span data-stu-id="5626f-120">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5626f-121">Пример</span><span class="sxs-lookup"><span data-stu-id="5626f-121">Example</span></span>  

 <span data-ttu-id="5626f-122">Следующий запрос Entity SQL демонстрирует, как использовать оператор AND.</span><span class="sxs-lookup"><span data-stu-id="5626f-122">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="5626f-123">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="5626f-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5626f-124">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="5626f-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5626f-125">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5626f-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5626f-126">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="5626f-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="5626f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="5626f-127">See also</span></span>

- [<span data-ttu-id="5626f-128">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5626f-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
