---
description: 'Дополнительные сведения о: + (Add)'
title: + (сложение)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b8ec9f50b349fe971513f399b7e9984e9044cf58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697313"
---
# <a name="-add"></a><span data-ttu-id="5cc86-103">+ (сложение)</span><span class="sxs-lookup"><span data-stu-id="5cc86-103">+ (Add)</span></span>

<span data-ttu-id="5cc86-104">складывает два числа.</span><span class="sxs-lookup"><span data-stu-id="5cc86-104">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cc86-105">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5cc86-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5cc86-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="5cc86-107">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="5cc86-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5cc86-108">Типы результата</span><span class="sxs-lookup"><span data-stu-id="5cc86-108">Result Types</span></span>  

 <span data-ttu-id="5cc86-109">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="5cc86-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="5cc86-110">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5cc86-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc86-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="5cc86-111">Remarks</span></span>  

 <span data-ttu-id="5cc86-112">Для типов EDM.String сложение является объединением строк.</span><span class="sxs-lookup"><span data-stu-id="5cc86-112">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc86-113">Пример</span><span class="sxs-lookup"><span data-stu-id="5cc86-113">Example</span></span>  

 <span data-ttu-id="5cc86-114">В следующем запросе Entity SQL арифметический оператор сложения (+) используется для сложения двух чисел.</span><span class="sxs-lookup"><span data-stu-id="5cc86-114">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="5cc86-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="5cc86-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5cc86-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="5cc86-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5cc86-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5cc86-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5cc86-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="5cc86-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="5cc86-119">См. также</span><span class="sxs-lookup"><span data-stu-id="5cc86-119">See also</span></span>

- [<span data-ttu-id="5cc86-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5cc86-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5cc86-121">Типы концептуальной модели (CSDL)</span><span class="sxs-lookup"><span data-stu-id="5cc86-121">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
