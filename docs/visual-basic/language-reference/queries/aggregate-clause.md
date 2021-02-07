---
description: 'Дополнительные сведения о предложении: Aggregate (Visual Basic)'
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 404cb4091bc11132450cf0d8d001ce426439ece7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700667"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="37374-103">Предложение Aggregate (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37374-103">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="37374-104">Применяет одну или несколько агрегатных функций к коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-104">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37374-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37374-105">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="37374-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="37374-106">Parts</span></span>  
  
|<span data-ttu-id="37374-107">Термин</span><span class="sxs-lookup"><span data-stu-id="37374-107">Term</span></span>|<span data-ttu-id="37374-108">Определение</span><span class="sxs-lookup"><span data-stu-id="37374-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="37374-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="37374-109">Required.</span></span> <span data-ttu-id="37374-110">Переменная, используемая для прохода по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-110">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="37374-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="37374-111">Optional.</span></span> <span data-ttu-id="37374-112">Тип параметра `element`.</span><span class="sxs-lookup"><span data-stu-id="37374-112">The type of `element`.</span></span> <span data-ttu-id="37374-113">Если тип не указан, тип `element` выводится из `collection` .</span><span class="sxs-lookup"><span data-stu-id="37374-113">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="37374-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="37374-114">Required.</span></span> <span data-ttu-id="37374-115">Ссылается на коллекцию для обработки.</span><span class="sxs-lookup"><span data-stu-id="37374-115">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="37374-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="37374-116">Optional.</span></span> <span data-ttu-id="37374-117">Одно или несколько предложений запроса, например `Where` предложение, для уточнения результата запроса с целью применения предложения Aggregate или предложений к.</span><span class="sxs-lookup"><span data-stu-id="37374-117">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="37374-118">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="37374-118">Required.</span></span> <span data-ttu-id="37374-119">Одно или несколько выражений с разделителями-запятыми, которые обозначают агрегатную функцию, применяемую к коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-119">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="37374-120">Можно применить псевдоним к агрегатной функции, чтобы указать имя элемента для результата запроса.</span><span class="sxs-lookup"><span data-stu-id="37374-120">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="37374-121">Если псевдоним не указан, используется имя агрегатной функции.</span><span class="sxs-lookup"><span data-stu-id="37374-121">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="37374-122">Примеры см. в разделе агрегатные функции далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="37374-122">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37374-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="37374-123">Remarks</span></span>  

 <span data-ttu-id="37374-124">`Aggregate`Предложение можно использовать для включения в запросы агрегатных функций.</span><span class="sxs-lookup"><span data-stu-id="37374-124">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="37374-125">Агрегатные функции выполняют проверки и вычисления для набора значений и возвращают одно значение.</span><span class="sxs-lookup"><span data-stu-id="37374-125">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="37374-126">Доступ к вычисленному значению можно получить с помощью члена типа результата запроса.</span><span class="sxs-lookup"><span data-stu-id="37374-126">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="37374-127">Стандартные агрегатные функции, которые можно использовать, — это функции,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` и `Sum` .</span><span class="sxs-lookup"><span data-stu-id="37374-127">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="37374-128">Эти функции знакомы разработчикам, знакомым со статистическими выражениями в SQL.</span><span class="sxs-lookup"><span data-stu-id="37374-128">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="37374-129">Они описаны в следующем разделе этой статьи.</span><span class="sxs-lookup"><span data-stu-id="37374-129">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="37374-130">Результат агрегатной функции включается в результат запроса в виде поля типа результата запроса.</span><span class="sxs-lookup"><span data-stu-id="37374-130">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="37374-131">Можно указать псевдоним для результата агрегатной функции, чтобы указать имя элемента типа результата запроса, который будет содержать статистическое значение.</span><span class="sxs-lookup"><span data-stu-id="37374-131">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="37374-132">Если псевдоним не указан, используется имя агрегатной функции.</span><span class="sxs-lookup"><span data-stu-id="37374-132">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="37374-133">`Aggregate`Предложение может начинать запрос или включать его в запрос в качестве дополнительного предложения.</span><span class="sxs-lookup"><span data-stu-id="37374-133">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="37374-134">Если `Aggregate` предложение начинает запрос, результатом является единственное значение, которое является результатом агрегатной функции, указанной в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="37374-134">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="37374-135">Если в предложении указано более одной агрегатной функции `Into` , запрос возвращает один тип с отдельным свойством для ссылки на результат каждой агрегатной функции в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="37374-135">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="37374-136">Если `Aggregate` предложение включено в запрос как дополнительное предложение, тип, возвращаемый в коллекции запросов, будет иметь отдельное свойство для ссылки на результат каждой агрегатной функции в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="37374-136">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="37374-137">Агрегатные функции</span><span class="sxs-lookup"><span data-stu-id="37374-137">Aggregate Functions</span></span>

<span data-ttu-id="37374-138">Ниже приведены стандартные агрегатные функции, которые можно использовать с `Aggregate` предложением.</span><span class="sxs-lookup"><span data-stu-id="37374-138">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="37374-139">Все</span><span class="sxs-lookup"><span data-stu-id="37374-139">All</span></span>

<span data-ttu-id="37374-140">Возвращает значение, `true` Если все элементы в коллекции соответствуют заданному условию. в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="37374-140">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="37374-141">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-141">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="37374-142">Любой</span><span class="sxs-lookup"><span data-stu-id="37374-142">Any</span></span>

<span data-ttu-id="37374-143">Возвращает значение, `true` Если любой элемент в коллекции удовлетворяет заданному условию; в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="37374-143">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="37374-144">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-144">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="37374-145">Среднее значение</span><span class="sxs-lookup"><span data-stu-id="37374-145">Average</span></span>

<span data-ttu-id="37374-146">Вычисляет среднее значение всех элементов в коллекции или вычисляет заданное выражение для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-146">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="37374-147">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-147">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="37374-148">Count</span><span class="sxs-lookup"><span data-stu-id="37374-148">Count</span></span>

<span data-ttu-id="37374-149">Подсчитывает количество элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-149">Counts the number of elements in the collection.</span></span> <span data-ttu-id="37374-150">Можно указать необязательное `Boolean` выражение, чтобы подсчитать только количество элементов в коллекции, удовлетворяющее условию.</span><span class="sxs-lookup"><span data-stu-id="37374-150">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="37374-151">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-151">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="37374-152">Group</span><span class="sxs-lookup"><span data-stu-id="37374-152">Group</span></span>

<span data-ttu-id="37374-153">Относится к результатам запроса, сгруппированным в результате `Group By` `Group Join` предложения OR.</span><span class="sxs-lookup"><span data-stu-id="37374-153">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="37374-154">`Group`Функция допустима только в `Into` предложении `Group By` `Group Join` предложения OR.</span><span class="sxs-lookup"><span data-stu-id="37374-154">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="37374-155">Дополнительные сведения и примеры см. в разделе предложение [Group By](group-by-clause.md) и [предложение Group Join](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37374-155">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="37374-156">LongCount</span><span class="sxs-lookup"><span data-stu-id="37374-156">LongCount</span></span>

<span data-ttu-id="37374-157">Подсчитывает количество элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-157">Counts the number of elements in the collection.</span></span> <span data-ttu-id="37374-158">Можно указать необязательное `Boolean` выражение, чтобы подсчитать только количество элементов в коллекции, удовлетворяющее условию.</span><span class="sxs-lookup"><span data-stu-id="37374-158">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="37374-159">Возвращает результат в виде `Long` .</span><span class="sxs-lookup"><span data-stu-id="37374-159">Returns the result as a `Long`.</span></span> <span data-ttu-id="37374-160">Пример см. в разделе `Count` агрегатная функция.</span><span class="sxs-lookup"><span data-stu-id="37374-160">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="37374-161">Max</span><span class="sxs-lookup"><span data-stu-id="37374-161">Max</span></span>

<span data-ttu-id="37374-162">Вычисление максимального значения из коллекции или вычисление заданного выражения для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-162">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="37374-163">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-163">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="37374-164">Min</span><span class="sxs-lookup"><span data-stu-id="37374-164">Min</span></span>

<span data-ttu-id="37374-165">Вычисление минимального значения из коллекции или вычисление заданного выражения для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-165">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="37374-166">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-166">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="37374-167">SUM</span><span class="sxs-lookup"><span data-stu-id="37374-167">Sum</span></span>

<span data-ttu-id="37374-168">Вычисляет сумму всех элементов в коллекции или вычисляет заданное выражение для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="37374-168">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="37374-169">Ниже представлен пример такого кода:</span><span class="sxs-lookup"><span data-stu-id="37374-169">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="37374-170">Пример</span><span class="sxs-lookup"><span data-stu-id="37374-170">Example</span></span>  

<span data-ttu-id="37374-171">В следующем примере показано, как использовать `Aggregate` предложение для применения агрегатных функций к результату запроса.</span><span class="sxs-lookup"><span data-stu-id="37374-171">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="37374-172">Создание User-Defined агрегатных функций</span><span class="sxs-lookup"><span data-stu-id="37374-172">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="37374-173">Можно включить собственные пользовательские агрегатные функции в выражение запроса, добавив методы расширения в <xref:System.Collections.Generic.IEnumerable%601> тип.</span><span class="sxs-lookup"><span data-stu-id="37374-173">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="37374-174">Пользовательский метод может затем выполнить вычисление или операцию над перечислимой коллекцией, на которую ссылается агрегатная функция.</span><span class="sxs-lookup"><span data-stu-id="37374-174">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="37374-175">Дополнительные сведения о методах расширения см. в разделе [Методы расширения](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="37374-175">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="37374-176">Например, в следующем примере показана пользовательская агрегатная функция, которая вычисляет медианное значение коллекции чисел.</span><span class="sxs-lookup"><span data-stu-id="37374-176">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="37374-177">Существует две перегрузки `Median` метода расширения.</span><span class="sxs-lookup"><span data-stu-id="37374-177">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="37374-178">Первая перегрузка принимает в качестве входных данных коллекцию типа `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="37374-178">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="37374-179">Если `Median` для поля запроса типа вызывается агрегатная функция `Double` , этот метод будет вызван.</span><span class="sxs-lookup"><span data-stu-id="37374-179">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="37374-180">Второй перегруженный `Median` метод может передаваться любым универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="37374-180">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="37374-181">Универсальная перегрузка `Median` метода принимает второй параметр, который ссылается на `Func(Of T, Double)` лямбда-выражение, чтобы проецировать значение для типа (из коллекции) в качестве соответствующего значения типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="37374-181">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="37374-182">Затем оно делегирует вычисление значения медианы другой перегрузке `Median` метода.</span><span class="sxs-lookup"><span data-stu-id="37374-182">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="37374-183">Дополнительные сведения о лямбда-выражениях см. в разделе [лямбда-выражения](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="37374-183">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="37374-184">В следующем примере показаны образцы запросов, которые вызывают `Median` агрегатную функцию для коллекции типа `Integer` , и коллекцию типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="37374-184">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="37374-185">Запрос, вызывающий `Median` агрегатную функцию в коллекции типа, `Double` вызывает перегрузку `Median` метода, принимающего в качестве входных данных коллекцию типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="37374-185">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="37374-186">Запрос, вызывающий `Median` агрегатную функцию для коллекции типа `Integer` , вызывает универсальную перегрузку `Median` метода.</span><span class="sxs-lookup"><span data-stu-id="37374-186">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="37374-187">См. также</span><span class="sxs-lookup"><span data-stu-id="37374-187">See also</span></span>

- <span data-ttu-id="37374-188">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37374-188">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="37374-189">Запросы</span><span class="sxs-lookup"><span data-stu-id="37374-189">Queries</span></span>](index.md)
- [<span data-ttu-id="37374-190">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="37374-190">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="37374-191">Предложение From</span><span class="sxs-lookup"><span data-stu-id="37374-191">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="37374-192">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="37374-192">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="37374-193">Предложение GROUP BY</span><span class="sxs-lookup"><span data-stu-id="37374-193">Group By Clause</span></span>](group-by-clause.md)
