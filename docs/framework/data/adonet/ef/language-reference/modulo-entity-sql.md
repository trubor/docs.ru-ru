---
description: 'Дополнительные сведения о: (остаток от деления) (Entity SQL)'
title: (Остаток от деления) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 8ac9bf2fa9dbee843215dcfeed13fefc7bd54796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696637"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="78586-103">(Остаток от деления) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="78586-103">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="78586-104">Возвращает остаток от деления значения одного выражения на другое.</span><span class="sxs-lookup"><span data-stu-id="78586-104">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78586-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78586-105">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="78586-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="78586-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="78586-107">Делимое числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="78586-107">The numeric expression to divide.</span></span> <span data-ttu-id="78586-108">`dividend` - любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="78586-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="78586-109">Числовое выражение, на которое делится делимое.</span><span class="sxs-lookup"><span data-stu-id="78586-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="78586-110">`divisor` - любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="78586-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="78586-111">Типы результата</span><span class="sxs-lookup"><span data-stu-id="78586-111">Result Types</span></span>  

 <span data-ttu-id="78586-112">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="78586-112">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="78586-113">Пример</span><span class="sxs-lookup"><span data-stu-id="78586-113">Example</span></span>  

 <span data-ttu-id="78586-114">В следующем запросе Entity SQL используется арифметический оператор % для получения остатка от деления одного выражения на другое.</span><span class="sxs-lookup"><span data-stu-id="78586-114">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="78586-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="78586-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="78586-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="78586-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="78586-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="78586-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="78586-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="78586-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="78586-119">См. также</span><span class="sxs-lookup"><span data-stu-id="78586-119">See also</span></span>

- [<span data-ttu-id="78586-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="78586-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
