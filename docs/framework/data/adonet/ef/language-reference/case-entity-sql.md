---
description: 'Дополнительные сведения: CASE (Entity SQL)'
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58f51aa46f41c3b502bcd6d364e893a12624f4cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739499"
---
# <a name="case-entity-sql"></a><span data-ttu-id="f4f98-103">CASE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f4f98-103">CASE (Entity SQL)</span></span>

<span data-ttu-id="f4f98-104">Вычисляет набор выражений типа `Boolean` для определения результата.</span><span class="sxs-lookup"><span data-stu-id="f4f98-104">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f98-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4f98-105">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4f98-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f4f98-106">Arguments</span></span>  

 `n`  
 <span data-ttu-id="f4f98-107">Заполнитель, который показывает, что можно использовать несколько предложений WHEN `Boolean_expression` THEN `result_expression` .</span><span class="sxs-lookup"><span data-stu-id="f4f98-107">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="f4f98-108">THEN `result_expression`</span><span class="sxs-lookup"><span data-stu-id="f4f98-108">THEN `result_expression`</span></span>  
 <span data-ttu-id="f4f98-109">Выражение, возвращаемое, если результатом выражения `Boolean_expression` является значение `true`.</span><span class="sxs-lookup"><span data-stu-id="f4f98-109">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="f4f98-110">`result expression` - любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="f4f98-110">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="f4f98-111">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="f4f98-111">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="f4f98-112">Это выражение, возвращаемое, если ни одна из операций сравнения не дает в результате `true`.</span><span class="sxs-lookup"><span data-stu-id="f4f98-112">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="f4f98-113">Если этот аргумент опущен и ни одна из операций сравнения не дает в результате `true`, функция CASE возвращает NULL.</span><span class="sxs-lookup"><span data-stu-id="f4f98-113">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="f4f98-114">`else_result_expression` - любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="f4f98-114">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="f4f98-115">Типы данных аргумента `else_result_expression` и любого из аргументов `result_expression` должны быть одинаковыми или неявно приводимыми друг к другу.</span><span class="sxs-lookup"><span data-stu-id="f4f98-115">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="f4f98-116">WHEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="f4f98-116">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="f4f98-117">Выражение типа `Boolean` , вычисляемое при использовании поискового формата оператора CASE.</span><span class="sxs-lookup"><span data-stu-id="f4f98-117">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="f4f98-118">`Boolean_expression` - любое допустимое выражение типа `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f4f98-118">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4f98-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f4f98-119">Return Value</span></span>  

 <span data-ttu-id="f4f98-120">Возвращает тип с наивысшим приоритетом из набора типов в выражении `result_expression` и необязательном выражении `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="f4f98-120">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4f98-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4f98-121">Remarks</span></span>  

 <span data-ttu-id="f4f98-122">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Выражение CASE напоминает выражение CASE языка Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="f4f98-122">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="f4f98-123">Выражение CASE применяется для выполнения ряда проверок условий в целях определения того, вычисление какого выражения приведет к получению приемлемого результата.</span><span class="sxs-lookup"><span data-stu-id="f4f98-123">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="f4f98-124">В этой форме выражение CASE применяется к ряду, состоящему из одного или нескольких выражений типа `Boolean` , для определения правильного результирующего выражения.</span><span class="sxs-lookup"><span data-stu-id="f4f98-124">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="f4f98-125">Функция CASE находит значение `Boolean_expression` для каждого предложения WHEN в указанном порядке и возвращает значение `result_expression` первого выражения `Boolean_expression` , которое определяется как `true`.</span><span class="sxs-lookup"><span data-stu-id="f4f98-125">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="f4f98-126">Остальные выражения оцениваться не будут.</span><span class="sxs-lookup"><span data-stu-id="f4f98-126">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="f4f98-127">Если ни одно выражение `Boolean_expression` не вычисляется в `true`, компонент Database Engine возвращает выражение `else_result_expression` , если указано предложение ELSE, или значение NULL, если предложение ELSE не указано.</span><span class="sxs-lookup"><span data-stu-id="f4f98-127">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="f4f98-128">Инструкция CASE не может возвращать мультинабор.</span><span class="sxs-lookup"><span data-stu-id="f4f98-128">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4f98-129">Пример</span><span class="sxs-lookup"><span data-stu-id="f4f98-129">Example</span></span>  

 <span data-ttu-id="f4f98-130">Следующий запрос Entity SQL с помощью выражения CASE оценивает набор выражений типа `Boolean` , чтобы определить результат.</span><span class="sxs-lookup"><span data-stu-id="f4f98-130">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="f4f98-131">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="f4f98-131">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f4f98-132">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="f4f98-132">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f4f98-133">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f4f98-133">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f4f98-134">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="f4f98-134">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="f4f98-135">См. также</span><span class="sxs-lookup"><span data-stu-id="f4f98-135">See also</span></span>

- [<span data-ttu-id="f4f98-136">THEN</span><span class="sxs-lookup"><span data-stu-id="f4f98-136">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="f4f98-137">SELECT</span><span class="sxs-lookup"><span data-stu-id="f4f98-137">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="f4f98-138">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4f98-138">Entity SQL Reference</span></span>](entity-sql-reference.md)
