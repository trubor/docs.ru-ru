---
description: Дополнительные сведения о предложении FROM (Visual Basic)
title: Предложение From
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: e35188412deb7fd9f2d8306c85057d050a60d030
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700563"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="419f1-103">Предложение From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419f1-103">From Clause (Visual Basic)</span></span>

<span data-ttu-id="419f1-104">Указывает одну или несколько переменных диапазона и коллекцию для запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-104">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="419f1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="419f1-105">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="419f1-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="419f1-106">Parts</span></span>  
  
|<span data-ttu-id="419f1-107">Термин</span><span class="sxs-lookup"><span data-stu-id="419f1-107">Term</span></span>|<span data-ttu-id="419f1-108">Определение</span><span class="sxs-lookup"><span data-stu-id="419f1-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="419f1-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="419f1-109">Required.</span></span> <span data-ttu-id="419f1-110">*Переменная диапазона* , используемая для прохода по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="419f1-110">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="419f1-111">Переменная диапазона используется для ссылки на каждый элемент в, `collection` когда запрос выполняет итерацию по `collection` .</span><span class="sxs-lookup"><span data-stu-id="419f1-111">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="419f1-112">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="419f1-112">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="419f1-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="419f1-113">Optional.</span></span> <span data-ttu-id="419f1-114">Тип параметра `element`.</span><span class="sxs-lookup"><span data-stu-id="419f1-114">The type of `element`.</span></span> <span data-ttu-id="419f1-115">Если не `type` указано, тип `element` выводится из `collection` .</span><span class="sxs-lookup"><span data-stu-id="419f1-115">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="419f1-116">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="419f1-116">Required.</span></span> <span data-ttu-id="419f1-117">Ссылается на коллекцию, к которой выполняется запрос.</span><span class="sxs-lookup"><span data-stu-id="419f1-117">Refers to the collection to be queried.</span></span> <span data-ttu-id="419f1-118">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="419f1-118">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="419f1-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="419f1-119">Remarks</span></span>  

 <span data-ttu-id="419f1-120">`From`Предложение используется для указания исходных данных для запроса и переменных, которые используются для ссылки на элемент из исходной коллекции.</span><span class="sxs-lookup"><span data-stu-id="419f1-120">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="419f1-121">Эти переменные называются *переменными диапазона*.</span><span class="sxs-lookup"><span data-stu-id="419f1-121">These variables are called *range variables*.</span></span> <span data-ttu-id="419f1-122">`From`Предложение является обязательным для запроса, за исключением случаев, когда `Aggregate` предложение используется для задания запроса, возвращающего только агрегированные результаты.</span><span class="sxs-lookup"><span data-stu-id="419f1-122">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="419f1-123">Дополнительные сведения см. в разделе [предложение Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="419f1-123">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="419f1-124">В запросе можно указать несколько `From` предложений, чтобы определить несколько коллекций для объединения.</span><span class="sxs-lookup"><span data-stu-id="419f1-124">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="419f1-125">Если указано несколько коллекций, они проходят по отдельности или объединяются, если они связаны.</span><span class="sxs-lookup"><span data-stu-id="419f1-125">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="419f1-126">Коллекции можно объединять неявным образом с помощью `Select` предложения или явно с помощью `Join` предложений или `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="419f1-126">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="419f1-127">В качестве альтернативы можно указать несколько переменных диапазона и коллекций в одном `From` предложении, при этом каждая связанная переменная диапазона и коллекция, отделенные друг от друга запятыми.</span><span class="sxs-lookup"><span data-stu-id="419f1-127">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="419f1-128">В следующем примере кода показаны оба синтаксических параметра для `From` предложения.</span><span class="sxs-lookup"><span data-stu-id="419f1-128">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="419f1-129">`From`Предложение определяет область запроса, аналогичную области `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="419f1-129">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="419f1-130">Таким образом, каждая `element` переменная диапазона в области запроса должна иметь уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="419f1-130">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="419f1-131">Поскольку можно указать несколько `From` предложений для запроса, последующие `From` предложения могут ссылаться на переменные диапазона в `From` предложении или они могут ссылаться на переменные диапазона в предыдущем `From` предложении.</span><span class="sxs-lookup"><span data-stu-id="419f1-131">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="419f1-132">Например, в следующем примере показано вложенное `From` предложение, где коллекция во втором предложении основана на свойстве переменной диапазона в первом предложении.</span><span class="sxs-lookup"><span data-stu-id="419f1-132">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="419f1-133">`From`За каждым предложением может следовать любое сочетание дополнительных предложений запроса для уточнения запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-133">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="419f1-134">Запрос можно уточнить следующими способами.</span><span class="sxs-lookup"><span data-stu-id="419f1-134">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="419f1-135">Объедините несколько коллекций неявным образом с помощью `From` `Select` предложений и или явно с помощью `Join` предложений или `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="419f1-135">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="419f1-136">Используйте `Where` предложение для фильтрации результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-136">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="419f1-137">Отсортируйте результат с помощью `Order By` предложения.</span><span class="sxs-lookup"><span data-stu-id="419f1-137">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="419f1-138">Группировать аналогичные результаты вместе с помощью `Group By` предложения.</span><span class="sxs-lookup"><span data-stu-id="419f1-138">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="419f1-139">Используйте `Aggregate` предложение для определения агрегатных функций для вычисления результата всего запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-139">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="419f1-140">Используйте `Let` предложение, чтобы ввести переменную итерации, значение которой определяется выражением, а не коллекцией.</span><span class="sxs-lookup"><span data-stu-id="419f1-140">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="419f1-141">Используйте `Distinct` предложение для пропуска повторяющихся результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-141">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="419f1-142">Выявление частей результата, возвращаемых с помощью `Skip` предложений, `Take` , `Skip While` и `Take While` .</span><span class="sxs-lookup"><span data-stu-id="419f1-142">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="419f1-143">Пример</span><span class="sxs-lookup"><span data-stu-id="419f1-143">Example</span></span>  

 <span data-ttu-id="419f1-144">Следующее выражение запроса использует `From` предложение для объявления переменной диапазона `cust` для каждого `Customer` объекта в `customers` коллекции.</span><span class="sxs-lookup"><span data-stu-id="419f1-144">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="419f1-145">`Where`Предложение использует переменную диапазона для ограничения выходных данных для клиентов из указанной области.</span><span class="sxs-lookup"><span data-stu-id="419f1-145">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="419f1-146">`For Each`Цикл отображает название компании для каждого клиента в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="419f1-146">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="419f1-147">См. также</span><span class="sxs-lookup"><span data-stu-id="419f1-147">See also</span></span>

- [<span data-ttu-id="419f1-148">Запросы</span><span class="sxs-lookup"><span data-stu-id="419f1-148">Queries</span></span>](index.md)
- <span data-ttu-id="419f1-149">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419f1-149">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="419f1-150">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="419f1-150">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="419f1-151">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="419f1-151">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="419f1-152">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="419f1-152">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="419f1-153">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="419f1-153">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="419f1-154">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="419f1-154">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="419f1-155">Предложение Distinct</span><span class="sxs-lookup"><span data-stu-id="419f1-155">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="419f1-156">Предложение Join</span><span class="sxs-lookup"><span data-stu-id="419f1-156">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="419f1-157">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="419f1-157">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="419f1-158">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="419f1-158">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="419f1-159">Предложение Let</span><span class="sxs-lookup"><span data-stu-id="419f1-159">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="419f1-160">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="419f1-160">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="419f1-161">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="419f1-161">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="419f1-162">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="419f1-162">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="419f1-163">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="419f1-163">Take While Clause</span></span>](take-while-clause.md)
