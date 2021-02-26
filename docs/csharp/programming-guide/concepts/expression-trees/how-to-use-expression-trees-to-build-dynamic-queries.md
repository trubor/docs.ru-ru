---
title: Выполнение запросов на основе состояния среды выполнения (C#)
description: Описание различных методов, которые код может использовать для динамического запроса в зависимости от состояния среды выполнения, путем изменения либо вызовов методов LINQ, либо деревьев выражений, переданных в эти методы.
ms.date: 02/11/2021
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 5e015bbc69b61b783abd7eba9cfcf13c29d5c3be
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100581946"
---
# <a name="querying-based-on-runtime-state-c"></a><span data-ttu-id="cbf76-103">Выполнение запросов на основе состояния среды выполнения (C#)</span><span class="sxs-lookup"><span data-stu-id="cbf76-103">Querying based on runtime state (C#)</span></span>

<span data-ttu-id="cbf76-104">Рассмотрим код, определяющий <xref:System.Linq.IQueryable> или [IQueryable\<T>](<xref:System.Linq.IQueryable%601>) для источника данных:</span><span class="sxs-lookup"><span data-stu-id="cbf76-104">Consider code that defines an <xref:System.Linq.IQueryable> or an [IQueryable\<T>](<xref:System.Linq.IQueryable%601>) against a data source:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Initialize":::

<span data-ttu-id="cbf76-105">Каждый раз при выполнении этого кода выполняется один и тот же запрос.</span><span class="sxs-lookup"><span data-stu-id="cbf76-105">Every time you run this code, the same exact query will be executed.</span></span> <span data-ttu-id="cbf76-106">Зачастую это неэффективно, поскольку может потребоваться, чтобы код выполнял различные запросы в зависимости от условий во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cbf76-106">This is frequently not very useful, as you may want your code to execute different queries depending on conditions at runtime.</span></span> <span data-ttu-id="cbf76-107">В этой статье описывается, как можно выполнить другой запрос на основе состояния среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="cbf76-107">This article describes how you can execute a different query based on runtime state.</span></span>

## <a name="iqueryable--iqueryablet-and-expression-trees"></a><span data-ttu-id="cbf76-108">IQueryable/IQueryable\<T> и деревья выражений</span><span class="sxs-lookup"><span data-stu-id="cbf76-108">IQueryable / IQueryable\<T> and expression trees</span></span>

<span data-ttu-id="cbf76-109">В своей основе <xref:System.Linq.IQueryable> имеет два компонента:</span><span class="sxs-lookup"><span data-stu-id="cbf76-109">Fundamentally, an <xref:System.Linq.IQueryable> has two components:</span></span>

* <span data-ttu-id="cbf76-110"><xref:System.Linq.IQueryable.Expression>&mdash;представление компонентов текущего запроса с учетом языка и источника данных в виде дерева выражения.</span><span class="sxs-lookup"><span data-stu-id="cbf76-110"><xref:System.Linq.IQueryable.Expression>&mdash;a language- and datasource-agnostic representation of the current query's components, in the form of an expression tree.</span></span>
* <span data-ttu-id="cbf76-111"><xref:System.Linq.IQueryable.Provider>&mdash;экземпляр поставщика LINQ, которому известно, как материализовать текущий запрос в значение или набор значений.</span><span class="sxs-lookup"><span data-stu-id="cbf76-111"><xref:System.Linq.IQueryable.Provider>&mdash;an instance of a LINQ provider, which knows how to materialize the current query into a value or set of values.</span></span>

<span data-ttu-id="cbf76-112">В контексте динамических запросов поставщик обычно остается неизменным; дерево выражения запроса будет отличаться от запроса к запросу.</span><span class="sxs-lookup"><span data-stu-id="cbf76-112">In the context of dynamic querying, the provider will usually remain the same; the expression tree of the query will differ from query to query.</span></span>

<span data-ttu-id="cbf76-113">Деревья выражений являются неизменяемыми; если вы хотите использовать другое дерево выражения &mdash;и, таким образом, другой запрос&mdash;, вам потребуется перевести существующее дерево выражения в новое, а значит в новое <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-113">Expression trees are immutable; if you want a different expression tree&mdash;and thus a different query&mdash;you'll need to translate the existing expression tree to a new one, and thus to a new <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="cbf76-114">В следующих разделах описываются конкретные методы запроса в зависимости от состояния среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="cbf76-114">The following sections describe specific techniques for querying differently in response to runtime state:</span></span>

- <span data-ttu-id="cbf76-115">Использование состояния среды выполнения из дерева выражений</span><span class="sxs-lookup"><span data-stu-id="cbf76-115">Use runtime state from within the expression tree</span></span>
- <span data-ttu-id="cbf76-116">Вызов дополнительных методов LINQ</span><span class="sxs-lookup"><span data-stu-id="cbf76-116">Call additional LINQ methods</span></span>
- <span data-ttu-id="cbf76-117">Изменение дерева выражения, переданного в методы LINQ</span><span class="sxs-lookup"><span data-stu-id="cbf76-117">Vary the expression tree passed into the LINQ methods</span></span>
- <span data-ttu-id="cbf76-118">Создайте выражение дерево выражения [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) с помощью фабричных методов в <xref:System.Linq.Expressions.Expression></span><span class="sxs-lookup"><span data-stu-id="cbf76-118">Construct an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) expression tree using the factory methods at <xref:System.Linq.Expressions.Expression></span></span>
- <span data-ttu-id="cbf76-119">Добавление узлов вызова метода в дерево выражения <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-119">Add method call nodes to an <xref:System.Linq.IQueryable>'s expression tree</span></span>
- <span data-ttu-id="cbf76-120">Создание строк и использование [динамической библиотеки LINQ](https://dynamic-linq.net/)</span><span class="sxs-lookup"><span data-stu-id="cbf76-120">Construct strings, and use the [Dynamic LINQ library](https://dynamic-linq.net/)</span></span>

## <a name="use-runtime-state-from-within-the-expression-tree"></a><span data-ttu-id="cbf76-121">Использование состояния среды выполнения из дерева выражений</span><span class="sxs-lookup"><span data-stu-id="cbf76-121">Use runtime state from within the expression tree</span></span>

<span data-ttu-id="cbf76-122">Предположив, что поставщик LINQ поддерживает его, самый простой способ динамического запроса будет заключаться в ссылке на состояние среды выполнения непосредственно в запросе с помощью закрытой переменной, такой как `length` в следующем примере кода:</span><span class="sxs-lookup"><span data-stu-id="cbf76-122">Assuming the LINQ provider supports it, the simplest way to query dynamically is to reference the runtime state directly in the query via a closed-over variable, such as `length` in the following code example:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Runtime_state_from_within_expression_tree":::

<span data-ttu-id="cbf76-123">Внутреннее дерево выражения, &mdash;а соответственно и запрос&mdash;, не были изменены; запрос возвращает разные значения только из-за изменения значения `length`.</span><span class="sxs-lookup"><span data-stu-id="cbf76-123">The internal expression tree&mdash;and thus the query&mdash;haven't been modified; the query returns different values only because the value of `length` has been changed.</span></span>

## <a name="call-additional-linq-methods"></a><span data-ttu-id="cbf76-124">Вызов дополнительных методов LINQ</span><span class="sxs-lookup"><span data-stu-id="cbf76-124">Call additional LINQ methods</span></span>

<span data-ttu-id="cbf76-125">Как правило, [встроенные методы LINQ](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) в <xref:System.Linq.Queryable> выполняют два действия:</span><span class="sxs-lookup"><span data-stu-id="cbf76-125">Generally, the [built-in LINQ methods](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) at <xref:System.Linq.Queryable> perform two steps:</span></span>

* <span data-ttu-id="cbf76-126">Заключение текущего дерево выражения в оболочку в <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода.</span><span class="sxs-lookup"><span data-stu-id="cbf76-126">Wrap the current expression tree in a <xref:System.Linq.Expressions.MethodCallExpression> representing the method call.</span></span>
* <span data-ttu-id="cbf76-127">Передача инкапсулированного дерева выражения в поставщик, чтобы вернуть значение через метод <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> поставщика, либо чтобы вернуть объект переведенного запроса с помощью метода <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-127">Pass the wrapped expression tree back to the provider, either to return a value via the provider's <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> method; or to return a translated query object via the <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cbf76-128">Чтобы получить новый запрос, можно заменить исходный запрос на результат метода, возвращающего [IQueryable\<T>](xref:System.Linq.IQueryable%601).</span><span class="sxs-lookup"><span data-stu-id="cbf76-128">You can replace the original query with the result of an [IQueryable\<T>](xref:System.Linq.IQueryable%601)-returning method, to get a new query.</span></span> <span data-ttu-id="cbf76-129">Это можно сделать по условию на основе состояния среды выполнения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="cbf76-129">You can do this conditionally based on runtime state, as in the following example:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a><span data-ttu-id="cbf76-130">Изменение дерева выражения, переданного в методы LINQ</span><span class="sxs-lookup"><span data-stu-id="cbf76-130">Vary the expression tree passed into the LINQ methods</span></span>

<span data-ttu-id="cbf76-131">В методы LINQ можно передать разные выражения в зависимости от состояния среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="cbf76-131">You can pass in different expressions to the LINQ methods, depending on runtime state:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Varying_expressions":::

<span data-ttu-id="cbf76-132">Также может потребоваться составить различные подвыражения, используя сторонние библиотеки, такие как [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx) от [LinqKit](http://www.albahari.com/nutshell/linqkit.aspx):</span><span class="sxs-lookup"><span data-stu-id="cbf76-132">You might also want to compose the various sub-expressions using a third-party library such as [LinqKit](http://www.albahari.com/nutshell/linqkit.aspx)'s [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx):</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compose_expressions":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a><span data-ttu-id="cbf76-133">Создание деревьев выражений и запросов с помощью фабричных методов</span><span class="sxs-lookup"><span data-stu-id="cbf76-133">Construct expression trees and queries using factory methods</span></span>

<span data-ttu-id="cbf76-134">Во всех примерах нам известен тип элемента во время компиляции,&mdash;`string`&mdash;а соответственно и тип запроса&mdash;`IQueryable<string>`.</span><span class="sxs-lookup"><span data-stu-id="cbf76-134">In all the examples up to this point, we've known the element type at compile time&mdash;`string`&mdash;and thus the type of the query&mdash;`IQueryable<string>`.</span></span> <span data-ttu-id="cbf76-135">Может потребоваться добавить компоненты в запрос любого типа элемента или добавить различные компоненты в зависимости от типа элемента.</span><span class="sxs-lookup"><span data-stu-id="cbf76-135">You may need to add components to a query of any element type, or to add different components, depending on the element type.</span></span> <span data-ttu-id="cbf76-136">Можно создавать деревья выражений с нуля, используя фабричные методы в <xref:System.Linq.Expressions.Expression?displayProperty=fullName> и таким образом адаптировать выражение в среде выполнения к определенному типу элемента.</span><span class="sxs-lookup"><span data-stu-id="cbf76-136">You can create expression trees from the ground up, using the factory methods at <xref:System.Linq.Expressions.Expression?displayProperty=fullName>, and thus tailor the expression at runtime to a specific element type.</span></span>

### <a name="constructing-an-expressiontdelegate"></a><span data-ttu-id="cbf76-137">Создание [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601)</span><span class="sxs-lookup"><span data-stu-id="cbf76-137">Constructing an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601)</span></span>

<span data-ttu-id="cbf76-138">При создании выражения для его передачи в один из методов LINQ фактически создается экземпляр [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601), где `TDelegate` — это некоторый тип делегата, например `Func<string, bool>`, `Action` или настраиваемый тип делегата.</span><span class="sxs-lookup"><span data-stu-id="cbf76-138">When you construct an expression to pass into one of the LINQ methods, you're actually constructing an instance of [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601), where `TDelegate` is some delegate type such as `Func<string, bool>`, `Action`, or a custom delegate type.</span></span>

<span data-ttu-id="cbf76-139">[Выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) наследуется от <xref:System.Linq.Expressions.LambdaExpression>, которое представляет собой полное лямбда-выражение следующего вида:</span><span class="sxs-lookup"><span data-stu-id="cbf76-139">[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) inherits from <xref:System.Linq.Expressions.LambdaExpression>, which represents a complete lambda expression like the following:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compiler_generated_expression_tree":::

<span data-ttu-id="cbf76-140"><xref:System.Linq.Expressions.LambdaExpression> имеет два компонента:</span><span class="sxs-lookup"><span data-stu-id="cbf76-140">A <xref:System.Linq.Expressions.LambdaExpression> has two components:</span></span>

* <span data-ttu-id="cbf76-141">список параметров,&mdash;`(string x)`&mdash;представленных свойством <xref:System.Linq.Expressions.LambdaExpression.Parameters>;</span><span class="sxs-lookup"><span data-stu-id="cbf76-141">a parameter list&mdash;`(string x)`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Parameters> property</span></span>
* <span data-ttu-id="cbf76-142">тело,&mdash;`x.StartsWith("a")`&mdash;представленное свойством <xref:System.Linq.Expressions.LambdaExpression.Body>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-142">a body&mdash;`x.StartsWith("a")`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Body> property.</span></span>

<span data-ttu-id="cbf76-143">Ниже указаны основные шаги по созданию [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601).</span><span class="sxs-lookup"><span data-stu-id="cbf76-143">The basic steps in constructing an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) are as follows:</span></span>

* <span data-ttu-id="cbf76-144">Определите объекты <xref:System.Linq.Expressions.ParameterExpression> для каждого из параметров (если таковые имеются) в лямбда-выражении с помощью фабричного метода <xref:System.Linq.Expressions.Expression.Parameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-144">Define <xref:System.Linq.Expressions.ParameterExpression> objects for each of the parameters (if any) in the lambda expression, using the <xref:System.Linq.Expressions.Expression.Parameter%2A> factory method.</span></span>

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_parameter":::

* <span data-ttu-id="cbf76-145">Создайте текст <xref:System.Linq.Expressions.LambdaExpression>, используя заданные вами выражения <xref:System.Linq.Expressions.ParameterExpression> и фабричные методы в <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-145">Construct the body of your <xref:System.Linq.Expressions.LambdaExpression>, using the <xref:System.Linq.Expressions.ParameterExpression>(s) you've defined, and the factory methods at <xref:System.Linq.Expressions.Expression>.</span></span> <span data-ttu-id="cbf76-146">Например, выражение, представляющее `x.StartsWith("a")`, может быть построено следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cbf76-146">For instance, an expression representing `x.StartsWith("a")` could be constructed like this:</span></span>

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_body":::

* <span data-ttu-id="cbf76-147">Заключите параметры и текст в [выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) с типов времени компиляции, используя соответствующую перегрузку фабричного метода <xref:System.Linq.Expressions.Expression.Lambda%2A>:</span><span class="sxs-lookup"><span data-stu-id="cbf76-147">Wrap the parameters and body in a compile-time-typed [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601), using the appropriate <xref:System.Linq.Expressions.Expression.Lambda%2A> factory method overload:</span></span>

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_lambda":::

<span data-ttu-id="cbf76-148">В следующих разделах описывается сценарий, в котором может потребоваться создать [выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) для передачи в метод LINQ, а также представлен полный пример того, как это сделать с помощью фабричных методов.</span><span class="sxs-lookup"><span data-stu-id="cbf76-148">The following sections describe a scenario in which you might want to construct an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) to pass into a LINQ method, and provide a complete example of how to do so using the factory methods.</span></span>

### <a name="scenario"></a><span data-ttu-id="cbf76-149">Сценарий</span><span class="sxs-lookup"><span data-stu-id="cbf76-149">Scenario</span></span>

<span data-ttu-id="cbf76-150">Допустим, у вас есть несколько типов сущностей:</span><span class="sxs-lookup"><span data-stu-id="cbf76-150">Let's say you have multiple entity types:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Entities":::

<span data-ttu-id="cbf76-151">Для любого из этих типов сущностей необходимо отфильтровать и возвратить только те сущности, которые имеют заданный текст в одном из полей `string`.</span><span class="sxs-lookup"><span data-stu-id="cbf76-151">For any of these entity types, you want to filter and return only those entities that have a given text inside one of their `string` fields.</span></span> <span data-ttu-id="cbf76-152">Для `Person` необходимо найти свойства `FirstName` и `LastName`:</span><span class="sxs-lookup"><span data-stu-id="cbf76-152">For `Person`, you'd want to search the `FirstName` and `LastName` properties:</span></span>

```csharp
string term = /* ... */;
var personsQry = new List<Person>()
    .AsQueryable()
    .Where(x => x.FirstName.Contains(term) || x.LastName.Contains(term));
```

<span data-ttu-id="cbf76-153">но для `Car` требуется найти только свойство `Model`:</span><span class="sxs-lookup"><span data-stu-id="cbf76-153">but for `Car`, you'd want to search only the `Model` property:</span></span>

```csharp
string term = /* ... */;
var carsQry = new List<Car>()
    .AsQueryable()
    .Where(x => x.Model.Contains(term));
```

<span data-ttu-id="cbf76-154">Несмотря на то что можно написать одну настраиваемую функцию для `IQueryable<Person>` и другую для `IQueryable<Car>`, следующая функция добавляет эту фильтрацию в любой существующий запрос независимо от конкретного типа элемента.</span><span class="sxs-lookup"><span data-stu-id="cbf76-154">While you could write one custom function for `IQueryable<Person>` and another for `IQueryable<Car>`, the following function adds this filtering to any existing query, irrespective of the specific element type.</span></span>

### <a name="example"></a><span data-ttu-id="cbf76-155">Пример</span><span class="sxs-lookup"><span data-stu-id="cbf76-155">Example</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate":::

<span data-ttu-id="cbf76-156">Поскольку функция `TextFilter` принимает и возвращает [IQueryable\<T>](xref:System.Linq.IQueryable%601) (а не только <xref:System.Linq.IQueryable>), после текстового фильтра можно добавить дополнительные элементы запроса с типом времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="cbf76-156">Because the `TextFilter` function takes and returns an [IQueryable\<T>](xref:System.Linq.IQueryable%601) (and not just an <xref:System.Linq.IQueryable>), you can add further compile-time-typed query elements after the text filter.</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a><span data-ttu-id="cbf76-157">Добавление узлов вызова метода в дерево выражения <xref:System.Linq.IQueryable></span><span class="sxs-lookup"><span data-stu-id="cbf76-157">Add method call nodes to the <xref:System.Linq.IQueryable>'s expression tree</span></span>

<span data-ttu-id="cbf76-158">При наличии <xref:System.Linq.IQueryable> вместо [IQueryable\<T>](xref:System.Linq.IQueryable%601) нельзя напрямую вызывать универсальные методы LINQ.</span><span class="sxs-lookup"><span data-stu-id="cbf76-158">If you have an <xref:System.Linq.IQueryable> instead of an [IQueryable\<T>](xref:System.Linq.IQueryable%601), you can't directly call the generic LINQ methods.</span></span> <span data-ttu-id="cbf76-159">В качестве альтернативы можно создать внутреннее дерево выражения, как показано выше, и использовать отражение для вызова соответствующего метода LINQ при передаче в дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="cbf76-159">One alternative is to build the inner expression tree as above, and use reflection to invoke the appropriate LINQ method while passing in the expression tree.</span></span>

<span data-ttu-id="cbf76-160">Можно также дублировать функциональность метода LINQ, заключив все дерево в <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода LINQ:</span><span class="sxs-lookup"><span data-stu-id="cbf76-160">You could also duplicate the LINQ method's functionality, by wrapping the entire tree in a <xref:System.Linq.Expressions.MethodCallExpression> which represents a call to the LINQ method:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_lambdaexpression":::

<span data-ttu-id="cbf76-161">Обратите внимание, что в этом случае у вас нет общего заполнителя `T` времени компиляции, поэтому вы будете использовать перегрузку <xref:System.Linq.Expressions.Expression.Lambda%2A>, для которой не требуются сведения о типе времени компиляции, в результате чего вместо [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601) создается <xref:System.Linq.Expressions.LambdaExpression>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-161">Note that in this case you don't have a compile-time `T` generic placeholder, so you'll use the <xref:System.Linq.Expressions.Expression.Lambda%2A> overload which doesn't require compile-time type information, and which produces a <xref:System.Linq.Expressions.LambdaExpression> instead of an an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601).</span></span>

## <a name="the-dynamic-linq-library"></a><span data-ttu-id="cbf76-162">Динамическая библиотека LINQ</span><span class="sxs-lookup"><span data-stu-id="cbf76-162">The Dynamic LINQ library</span></span>

<span data-ttu-id="cbf76-163">Построение деревьев выражений с помощью фабричных методов достаточно сложное занятие; проще создавать строки.</span><span class="sxs-lookup"><span data-stu-id="cbf76-163">Constructing expression trees using factory methods is relatively complex; it is easier to compose strings.</span></span> <span data-ttu-id="cbf76-164">[Динамическая библиотека LINQ](https://dynamic-linq.net/) предоставляет набор методов расширения для <xref:System.Linq.IQueryable>, соответствующих стандартным методам LINQ в <xref:System.Linq.Queryable>, и который принимает строки в [специальном синтаксисе](https://dynamic-linq.net/expression-language) вместо деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="cbf76-164">The [Dynamic LINQ library](https://dynamic-linq.net/) exposes a set of extension methods on <xref:System.Linq.IQueryable> corresponding to the standard LINQ methods at <xref:System.Linq.Queryable>, and which accept strings in a [special syntax](https://dynamic-linq.net/expression-language) instead of expression trees.</span></span> <span data-ttu-id="cbf76-165">Библиотека создает соответствующее дерево выражения из строки и может возвращать результирующий преобразованный <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="cbf76-165">The library generates the appropriate expression tree from the string, and can return the resultant translated <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="cbf76-166">Например, предыдущий пример можно переписать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cbf76-166">For instance, the previous example could be rewritten as follows:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Dynamic_linq":::

## <a name="see-also"></a><span data-ttu-id="cbf76-167">См. также</span><span class="sxs-lookup"><span data-stu-id="cbf76-167">See also</span></span>

- [<span data-ttu-id="cbf76-168">Деревья выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="cbf76-168">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="cbf76-169">Выполнение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="cbf76-169">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="cbf76-170">Динамическое определение фильтров предикатов во время выполнения</span><span class="sxs-lookup"><span data-stu-id="cbf76-170">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
