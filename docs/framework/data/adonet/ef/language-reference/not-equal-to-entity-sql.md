---
description: Дополнительные сведения:! = (не равно) (Entity SQL)
title: '!= (не равно) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: a7a96606fb1834b757253948c3a0d2cde11893dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696403"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="3d3da-103">!= (не равно) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3d3da-103">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="3d3da-104">Сравнивает два выражения, чтобы определить, является ли значение левого выражения не равным значению правого выражения.</span><span class="sxs-lookup"><span data-stu-id="3d3da-104">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="3d3da-105">Действие оператора != (не равно) эквивалентно действию оператора <>.</span><span class="sxs-lookup"><span data-stu-id="3d3da-105">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d3da-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d3da-106">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d3da-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3d3da-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3d3da-108">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="3d3da-108">Any valid expression.</span></span> <span data-ttu-id="3d3da-109">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="3d3da-109">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3d3da-110">Типы результата</span><span class="sxs-lookup"><span data-stu-id="3d3da-110">Result Types</span></span>  

 <span data-ttu-id="3d3da-111">`true` , если значение левого выражения не равно значению правого; в противном случае - `false`.</span><span class="sxs-lookup"><span data-stu-id="3d3da-111">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d3da-112">Пример</span><span class="sxs-lookup"><span data-stu-id="3d3da-112">Example</span></span>  

 <span data-ttu-id="3d3da-113">В следующем запросе Entity SQL оператор != используется для сравнения двух выражений, чтобы определить, отличается ли значение левого выражения от значения правого.</span><span class="sxs-lookup"><span data-stu-id="3d3da-113">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="3d3da-114">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="3d3da-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d3da-115">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="3d3da-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3d3da-116">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d3da-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3d3da-117">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="3d3da-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="3d3da-118">См. также</span><span class="sxs-lookup"><span data-stu-id="3d3da-118">See also</span></span>

- [<span data-ttu-id="3d3da-119">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3d3da-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
