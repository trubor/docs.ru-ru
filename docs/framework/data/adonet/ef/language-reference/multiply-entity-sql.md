---
description: 'Дополнительные сведения: * (умножение) (Entity SQL)'
title: '* Перемножаемых (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696624"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="586b6-103">\* (умножение) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="586b6-103">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="586b6-104">умножает два выражения.</span><span class="sxs-lookup"><span data-stu-id="586b6-104">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="586b6-105">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="586b6-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="586b6-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="586b6-107">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="586b6-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="586b6-108">Типы результата</span><span class="sxs-lookup"><span data-stu-id="586b6-108">Result Types</span></span>  

 <span data-ttu-id="586b6-109">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="586b6-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="586b6-110">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="586b6-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="586b6-111">Пример</span><span class="sxs-lookup"><span data-stu-id="586b6-111">Example</span></span>  

 <span data-ttu-id="586b6-112">В следующем запросе Entity SQL арифметический оператор умножения (\*) используется для умножения двух чисел.</span><span class="sxs-lookup"><span data-stu-id="586b6-112">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="586b6-113">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="586b6-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="586b6-114">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="586b6-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="586b6-115">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="586b6-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="586b6-116">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="586b6-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="586b6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="586b6-117">See also</span></span>

- [<span data-ttu-id="586b6-118">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="586b6-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
