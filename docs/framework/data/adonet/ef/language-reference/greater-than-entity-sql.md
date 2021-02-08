---
description: 'Дополнительные сведения: > (больше) (Entity SQL)'
title: '>  (больше) (язык Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e14470d477336fd719bb419657af3fdadcd54d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786294"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="f6817-103">> (больше) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f6817-103">> (Greater Than) (Entity SQL)</span></span>

<span data-ttu-id="f6817-104">Сравнивает два выражения и определяет, имеет ли левое выражение значение больше значения правого выражения.</span><span class="sxs-lookup"><span data-stu-id="f6817-104">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6817-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6817-105">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6817-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f6817-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f6817-107">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="f6817-107">Any valid expression.</span></span> <span data-ttu-id="f6817-108">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="f6817-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f6817-109">Типы результата</span><span class="sxs-lookup"><span data-stu-id="f6817-109">Result Types</span></span>  

 <span data-ttu-id="f6817-110">Значение`true` , если левое выражение больше правого. В противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="f6817-110">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6817-111">Пример</span><span class="sxs-lookup"><span data-stu-id="f6817-111">Example</span></span>  

 <span data-ttu-id="f6817-112">Следующий запрос Entity SQL использует оператор сравнения > для сравнения двух выражений и определяет, имеет ли левое выражение значение, большее значения правого выражения.</span><span class="sxs-lookup"><span data-stu-id="f6817-112">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="f6817-113">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="f6817-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f6817-114">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="f6817-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f6817-115">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f6817-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f6817-116">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="f6817-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="f6817-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f6817-117">See also</span></span>

- [<span data-ttu-id="f6817-118">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f6817-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
