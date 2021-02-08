---
description: 'Дополнительные сведения о: EXISTs (Entity SQL)'
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: c6c5b86616d63b9cc3389365a96c382101463732
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786385"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="a6171-103">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a6171-103">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="a6171-104">Определяет, является ли коллекция пустой.</span><span class="sxs-lookup"><span data-stu-id="a6171-104">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6171-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6171-105">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6171-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="a6171-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="a6171-107">Любое допустимое выражение, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="a6171-107">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="a6171-108">NOT</span><span class="sxs-lookup"><span data-stu-id="a6171-108">NOT</span></span>  
 <span data-ttu-id="a6171-109">Указывает, что результат оператора EXISTS должен быть инвертирован.</span><span class="sxs-lookup"><span data-stu-id="a6171-109">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6171-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a6171-110">Return Value</span></span>  

 <span data-ttu-id="a6171-111">Значение `true`, если коллекция не пуста; в противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a6171-111">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6171-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6171-112">Remarks</span></span>  

 <span data-ttu-id="a6171-113">EXISTS - это один из операторов работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6171-113">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a6171-114">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="a6171-114">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a6171-115">Сведения о приоритетах для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора см. в разделе [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a6171-115">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6171-116">Пример</span><span class="sxs-lookup"><span data-stu-id="a6171-116">Example</span></span>  

 <span data-ttu-id="a6171-117">В следующем запросе Entity SQL оператор EXISTS используется, чтобы определить, пуста ли коллекция.</span><span class="sxs-lookup"><span data-stu-id="a6171-117">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="a6171-118">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="a6171-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a6171-119">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="a6171-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a6171-120">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a6171-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a6171-121">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="a6171-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="a6171-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a6171-122">See also</span></span>

- [<span data-ttu-id="a6171-123">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a6171-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
