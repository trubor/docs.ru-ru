---
description: 'Дополнительные сведения о: в (Entity SQL)'
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 234ed15430e44d12d4ca7c98fcb4a7bc03d117f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748600"
---
# <a name="in-entity-sql"></a><span data-ttu-id="7eaab-103">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7eaab-103">IN (Entity SQL)</span></span>

<span data-ttu-id="7eaab-104">Определяет, совпадает ли значение с каким-либо значением в коллекции.</span><span class="sxs-lookup"><span data-stu-id="7eaab-104">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7eaab-105">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7eaab-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="7eaab-106">Arguments</span></span>  

 `value`  
 <span data-ttu-id="7eaab-107">Любое допустимое выражение, возвращающее значение для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="7eaab-107">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="7eaab-108">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="7eaab-108">[ NOT ]</span></span>  
 <span data-ttu-id="7eaab-109">Указывает, что значение `Boolean` оператора IN следует инвертировать.</span><span class="sxs-lookup"><span data-stu-id="7eaab-109">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="7eaab-110">Любое допустимое выражение, возвращающее коллекцию для проверки соответствия.</span><span class="sxs-lookup"><span data-stu-id="7eaab-110">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="7eaab-111">Все выражения должны иметь тот же тип, что и аргумент `value`, или принадлежать к базовому или производному типу для типа этого аргумента.</span><span class="sxs-lookup"><span data-stu-id="7eaab-111">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eaab-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7eaab-112">Return Value</span></span>  

 <span data-ttu-id="7eaab-113">Значение `true`, если значение найдено в коллекции. Значение NULL, если параметр value имеет значение NULL или коллекция пуста. В противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="7eaab-113">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="7eaab-114">Использование NOT IN логически инвертирует результат IN.</span><span class="sxs-lookup"><span data-stu-id="7eaab-114">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eaab-115">Пример</span><span class="sxs-lookup"><span data-stu-id="7eaab-115">Example</span></span>  

 <span data-ttu-id="7eaab-116">В следующем запросе на языке Entity SQL оператор IN используется для определения, совпадает ли значение с каким-либо значением в коллекции.</span><span class="sxs-lookup"><span data-stu-id="7eaab-116">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="7eaab-117">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="7eaab-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7eaab-118">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="7eaab-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7eaab-119">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7eaab-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7eaab-120">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="7eaab-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="7eaab-121">См. также</span><span class="sxs-lookup"><span data-stu-id="7eaab-121">See also</span></span>

- [<span data-ttu-id="7eaab-122">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7eaab-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
