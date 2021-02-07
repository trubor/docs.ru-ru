---
description: 'Дополнительные сведения: < (меньше) (Entity SQL)'
title: < (меньше) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 523defa6c19ca43a5827258277bbe3f489b9b8c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748288"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="d7fb7-103">\< (меньше) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7fb7-103">\< (Less Than) (Entity SQL)</span></span>

<span data-ttu-id="d7fb7-104">Сравнивает два выражения, чтобы определить, является ли значение левого выражения меньшим, чем значение правого выражения.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-104">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fb7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7fb7-105">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7fb7-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d7fb7-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="d7fb7-107">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-107">Any valid expression.</span></span> <span data-ttu-id="d7fb7-108">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d7fb7-109">Типы результата</span><span class="sxs-lookup"><span data-stu-id="d7fb7-109">Result Types</span></span>  

 <span data-ttu-id="d7fb7-110">`true` , если значение левого выражения меньше, чем правого; в противном случае - `false`.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-110">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7fb7-111">Пример</span><span class="sxs-lookup"><span data-stu-id="d7fb7-111">Example</span></span>  

 <span data-ttu-id="d7fb7-112">В следующем запросе Entity SQL оператор < используется для сравнения двух выражений, чтобы определить, является ли значение левого выражения меньшим, чем правого.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-112">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="d7fb7-113">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7fb7-114">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d7fb7-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7fb7-115">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7fb7-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d7fb7-116">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="d7fb7-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="d7fb7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d7fb7-117">See also</span></span>

- [<span data-ttu-id="d7fb7-118">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d7fb7-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
