---
description: 'Дополнительные сведения: = (Equals) (Entity SQL)'
title: = (равно) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 500c3fdde2377b3b5160436f23d051c2bcd0ee62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786411"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="a98c6-103">= (равно) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a98c6-103">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="a98c6-104">Проверяет равенство двух выражений.</span><span class="sxs-lookup"><span data-stu-id="a98c6-104">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98c6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a98c6-105">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a98c6-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="a98c6-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="a98c6-107">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="a98c6-107">Any valid expression.</span></span> <span data-ttu-id="a98c6-108">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="a98c6-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a98c6-109">Типы результата</span><span class="sxs-lookup"><span data-stu-id="a98c6-109">Result Types</span></span>  

 <span data-ttu-id="a98c6-110">Имеет значение`true` , если левое выражение равно правому выражению. В противном случае имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a98c6-110">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98c6-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a98c6-111">Remarks</span></span>  

 <span data-ttu-id="a98c6-112">Оператор == эквивалентен оператору =.</span><span class="sxs-lookup"><span data-stu-id="a98c6-112">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a98c6-113">Пример</span><span class="sxs-lookup"><span data-stu-id="a98c6-113">Example</span></span>  

 <span data-ttu-id="a98c6-114">В следующем запросе Entity SQL оператор сравнения = используется для сравнения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="a98c6-114">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="a98c6-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="a98c6-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a98c6-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="a98c6-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a98c6-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a98c6-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a98c6-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="a98c6-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a98c6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a98c6-119">See also</span></span>

- [<span data-ttu-id="a98c6-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a98c6-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
