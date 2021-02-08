---
description: Дополнительные сведения о:-(Subtract) (Entity SQL)
title: '- Вычесть (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: cba23d998ad6beaf545118c69d806de46a1f6db0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791833"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="d5c2e-103">- (вычитание) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d5c2e-103">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="d5c2e-104">Выполняет вычитание двух чисел.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-104">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5c2e-105">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5c2e-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d5c2e-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="d5c2e-107">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d5c2e-108">Типы результата</span><span class="sxs-lookup"><span data-stu-id="d5c2e-108">Result Types</span></span>  

 <span data-ttu-id="d5c2e-109">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d5c2e-110">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d5c2e-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5c2e-111">Пример</span><span class="sxs-lookup"><span data-stu-id="d5c2e-111">Example</span></span>  

 <span data-ttu-id="d5c2e-112">Следующий запрос Entity SQL использует арифметический оператор вычитания (-) для вычитания одного числа из другого.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-112">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="d5c2e-113">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d5c2e-114">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d5c2e-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d5c2e-115">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d5c2e-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d5c2e-116">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="d5c2e-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="d5c2e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d5c2e-117">See also</span></span>

- [<span data-ttu-id="d5c2e-118">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d5c2e-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
