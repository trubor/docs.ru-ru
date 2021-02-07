---
description: Дополнительные сведения:/(деление) (Entity SQL)
title: '- Деление (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 4ac487c636c460401eeb147dc7ce1a8d8ba7f7ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724639"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="827c2-103">/ (деление) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="827c2-103">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="827c2-104">делит одно число на другое.</span><span class="sxs-lookup"><span data-stu-id="827c2-104">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="827c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="827c2-105">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="827c2-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="827c2-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="827c2-107">Делимое числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="827c2-107">The numeric expression to divide.</span></span> <span data-ttu-id="827c2-108">`dividend` - любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="827c2-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="827c2-109">Числовое выражение, на которое делится делимое.</span><span class="sxs-lookup"><span data-stu-id="827c2-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="827c2-110">`divisor` - любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="827c2-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="827c2-111">Типы результата</span><span class="sxs-lookup"><span data-stu-id="827c2-111">Result Types</span></span>  

 <span data-ttu-id="827c2-112">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="827c2-112">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="827c2-113">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="827c2-113">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="827c2-114">Пример</span><span class="sxs-lookup"><span data-stu-id="827c2-114">Example</span></span>  

 <span data-ttu-id="827c2-115">Следующий Entity SQL запрос использует арифметический оператор/для деления одного числа на другое.</span><span class="sxs-lookup"><span data-stu-id="827c2-115">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="827c2-116">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="827c2-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="827c2-117">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="827c2-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="827c2-118">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="827c2-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="827c2-119">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="827c2-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="827c2-120">См. также</span><span class="sxs-lookup"><span data-stu-id="827c2-120">See also</span></span>

- [<span data-ttu-id="827c2-121">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="827c2-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
