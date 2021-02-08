---
description: 'Дополнительные сведения о: EXCEPT (Entity SQL)'
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fd66d8dc6e22a73afbfd27e6eb1fd6c8bb9d3475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786398"
---
# <a name="except-entity-sql"></a><span data-ttu-id="018e0-103">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="018e0-103">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="018e0-104">Возвращает коллекцию различных значений из выражения запроса, расположенного левее операнда EXCEPT, за исключением тех, которые были возвращены выражением запроса, расположенного правее операнда EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="018e0-104">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="018e0-105">Все выражения должны иметь тот же тип, что и аргумент `expression`, или принадлежать к базовому или производному типу для типа этого аргумента.</span><span class="sxs-lookup"><span data-stu-id="018e0-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018e0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="018e0-106">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="018e0-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="018e0-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="018e0-108">Любое допустимое выражение запроса, которое возвращает коллекцию для сравнения с коллекцией, возвращенной другим выражением запроса.</span><span class="sxs-lookup"><span data-stu-id="018e0-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="018e0-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="018e0-109">Return Value</span></span>  

 <span data-ttu-id="018e0-110">Коллекция того же типа, что и параметр `expression`, или же базового или производного типа для типа этого параметра.</span><span class="sxs-lookup"><span data-stu-id="018e0-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="018e0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="018e0-111">Remarks</span></span>  

 <span data-ttu-id="018e0-112">Оператор EXCEPT - это один из операторов работы с наборами в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="018e0-112">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="018e0-113">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="018e0-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="018e0-114">Следующая таблица демонстрирует очередность операторов работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="018e0-114">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="018e0-115">Приоритет</span><span class="sxs-lookup"><span data-stu-id="018e0-115">Precedence</span></span>|<span data-ttu-id="018e0-116">Операторы</span><span class="sxs-lookup"><span data-stu-id="018e0-116">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="018e0-117">Наивысшая</span><span class="sxs-lookup"><span data-stu-id="018e0-117">Highest</span></span>|<span data-ttu-id="018e0-118">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="018e0-118">INTERSECT</span></span>|  
||<span data-ttu-id="018e0-119">UNION</span><span class="sxs-lookup"><span data-stu-id="018e0-119">UNION</span></span><br /><br /> <span data-ttu-id="018e0-120">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="018e0-120">UNION ALL</span></span>|  
||<span data-ttu-id="018e0-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="018e0-121">EXCEPT</span></span>|  
|<span data-ttu-id="018e0-122">Наименьшая</span><span class="sxs-lookup"><span data-stu-id="018e0-122">Lowest</span></span>|<span data-ttu-id="018e0-123">EXISTS</span><span class="sxs-lookup"><span data-stu-id="018e0-123">EXISTS</span></span><br /><br /> <span data-ttu-id="018e0-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="018e0-124">OVERLAPS</span></span><br /><br /> <span data-ttu-id="018e0-125">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="018e0-125">FLATTEN</span></span><br /><br /> <span data-ttu-id="018e0-126">SET</span><span class="sxs-lookup"><span data-stu-id="018e0-126">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="018e0-127">Пример</span><span class="sxs-lookup"><span data-stu-id="018e0-127">Example</span></span>  

 <span data-ttu-id="018e0-128">В следующем запросе Entity SQL с помощью оператора EXCEPT возвращается коллекция отдельных значений из двух выражений запросов.</span><span class="sxs-lookup"><span data-stu-id="018e0-128">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="018e0-129">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="018e0-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="018e0-130">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="018e0-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="018e0-131">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="018e0-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="018e0-132">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="018e0-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="018e0-133">См. также</span><span class="sxs-lookup"><span data-stu-id="018e0-133">See also</span></span>

- [<span data-ttu-id="018e0-134">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="018e0-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
