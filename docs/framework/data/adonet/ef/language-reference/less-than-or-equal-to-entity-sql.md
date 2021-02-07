---
description: 'Дополнительные сведения: <= (меньше или равно) (Entity SQL)'
title: <= (меньше или равно) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: f720c4ef87cdd0cceea175b1ea70caf5ac6e1deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748262"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="89e4d-103">\<= (меньше или равно) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="89e4d-103">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="89e4d-104">Сравнивает два выражения и определяет, имеет ли левое выражение значение, меньшее или равное значению правого выражения.</span><span class="sxs-lookup"><span data-stu-id="89e4d-104">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e4d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89e4d-105">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="89e4d-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="89e4d-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="89e4d-107">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="89e4d-107">Any valid expression.</span></span> <span data-ttu-id="89e4d-108">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="89e4d-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="89e4d-109">Типы результата</span><span class="sxs-lookup"><span data-stu-id="89e4d-109">Result Types</span></span>  

 <span data-ttu-id="89e4d-110">Значение`true` , если левое выражение меньше или равно правому выражению. В противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="89e4d-110">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89e4d-111">Пример</span><span class="sxs-lookup"><span data-stu-id="89e4d-111">Example</span></span>  

 <span data-ttu-id="89e4d-112">Следующий запрос Entity SQL использует оператор сравнения <= для сравнения двух выражений и определяет, имеет ли левое выражение значение, меньшее или равное значению правого выражения.</span><span class="sxs-lookup"><span data-stu-id="89e4d-112">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="89e4d-113">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="89e4d-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="89e4d-114">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="89e4d-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="89e4d-115">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="89e4d-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="89e4d-116">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="89e4d-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="89e4d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="89e4d-117">See also</span></span>

- [<span data-ttu-id="89e4d-118">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="89e4d-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
