---
title: Выполнение запросов на основе состояния среды выполнения (C#)
description: Описание различных методов, которые код может использовать для динамического запроса в зависимости от состояния среды выполнения, путем изменения либо вызовов методов LINQ, либо деревьев выражений, переданных в эти методы.
ms.date: 02/11/2021
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 1a3bbe8c9ba6752c541d69502b7c4ac020fd9708
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876725"
---
# <a name="querying-based-on-runtime-state-c"></a>Выполнение запросов на основе состояния среды выполнения (C#)

Рассмотрим код, определяющий <xref:System.Linq.IQueryable> или [IQueryable\<T>](<xref:System.Linq.IQueryable%601>) для источника данных:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Initialize":::

Каждый раз при выполнении этого кода выполняется один и тот же запрос. Зачастую это неэффективно, поскольку может потребоваться, чтобы код выполнял различные запросы в зависимости от условий во время выполнения. В этой статье описывается, как можно выполнить другой запрос на основе состояния среды выполнения.

## <a name="iqueryable--iqueryablet-and-expression-trees"></a>IQueryable/IQueryable\<T> и деревья выражений

В своей основе <xref:System.Linq.IQueryable> имеет два компонента:

* <xref:System.Linq.IQueryable.Expression>&mdash;представление компонентов текущего запроса с учетом языка и источника данных в виде дерева выражения.
* <xref:System.Linq.IQueryable.Provider>&mdash;экземпляр поставщика LINQ, которому известно, как материализовать текущий запрос в значение или набор значений.

В контексте динамических запросов поставщик обычно остается неизменным; дерево выражения запроса будет отличаться от запроса к запросу.

Деревья выражений являются неизменяемыми; если вы хотите использовать другое дерево выражения &mdash;и, таким образом, другой запрос&mdash;, вам потребуется перевести существующее дерево выражения в новое, а значит в новое <xref:System.Linq.IQueryable>.

В следующих разделах описываются конкретные методы запроса в зависимости от состояния среды выполнения.

- Использование состояния среды выполнения из дерева выражений
- Вызов дополнительных методов LINQ
- Изменение дерева выражения, переданного в методы LINQ
- Создайте выражение дерево выражения [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) с помощью фабричных методов в <xref:System.Linq.Expressions.Expression>
- Добавление узлов вызова метода в дерево выражения <xref:System.Linq.IQueryable>.
- Создание строк и использование [динамической библиотеки LINQ](https://dynamic-linq.net/)

## <a name="use-runtime-state-from-within-the-expression-tree"></a>Использование состояния среды выполнения из дерева выражений

Предположив, что поставщик LINQ поддерживает его, самый простой способ динамического запроса будет заключаться в ссылке на состояние среды выполнения непосредственно в запросе с помощью закрытой переменной, такой как `length` в следующем примере кода:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Runtime_state_from_within_expression_tree":::

Внутреннее дерево выражения, &mdash;а соответственно и запрос&mdash;, не были изменены; запрос возвращает разные значения только из-за изменения значения `length`.

## <a name="call-additional-linq-methods"></a>Вызов дополнительных методов LINQ

Как правило, [встроенные методы LINQ](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) в <xref:System.Linq.Queryable> выполняют два действия:

* Заключение текущего дерево выражения в оболочку в <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода.
* Передача инкапсулированного дерева выражения в поставщик, чтобы вернуть значение через метод <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> поставщика, либо чтобы вернуть объект переведенного запроса с помощью метода <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType>.

Чтобы получить новый запрос, можно заменить исходный запрос на результат метода, возвращающего [IQueryable\<T>](xref:System.Linq.IQueryable%601). Это можно сделать по условию на основе состояния среды выполнения, как показано в следующем примере:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a>Изменение дерева выражения, переданного в методы LINQ

В методы LINQ можно передать разные выражения в зависимости от состояния среды выполнения:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Varying_expressions":::

Также может потребоваться составить различные подвыражения, используя сторонние библиотеки, такие как [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx) от [LinqKit](http://www.albahari.com/nutshell/linqkit.aspx):

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compose_expressions":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a>Создание деревьев выражений и запросов с помощью фабричных методов

Во всех примерах нам известен тип элемента во время компиляции,&mdash;`string`&mdash;а соответственно и тип запроса&mdash;`IQueryable<string>`. Может потребоваться добавить компоненты в запрос любого типа элемента или добавить различные компоненты в зависимости от типа элемента. Можно создавать деревья выражений с нуля, используя фабричные методы в <xref:System.Linq.Expressions.Expression?displayProperty=fullName> и таким образом адаптировать выражение в среде выполнения к определенному типу элемента.

### <a name="constructing-an-expressiontdelegate"></a>Создание [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601)

При создании выражения для его передачи в один из методов LINQ фактически создается экземпляр [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601), где `TDelegate` — это некоторый тип делегата, например `Func<string, bool>`, `Action` или настраиваемый тип делегата.

[Выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) наследуется от <xref:System.Linq.Expressions.LambdaExpression>, которое представляет собой полное лямбда-выражение следующего вида:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compiler_generated_expression_tree":::

<xref:System.Linq.Expressions.LambdaExpression> имеет два компонента:

* список параметров,&mdash;`(string x)`&mdash;представленных свойством <xref:System.Linq.Expressions.LambdaExpression.Parameters>;
* тело,&mdash;`x.StartsWith("a")`&mdash;представленное свойством <xref:System.Linq.Expressions.LambdaExpression.Body>.

Ниже указаны основные шаги по созданию [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601).

* Определите объекты <xref:System.Linq.Expressions.ParameterExpression> для каждого из параметров (если таковые имеются) в лямбда-выражении с помощью фабричного метода <xref:System.Linq.Expressions.Expression.Parameter%2A>.

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_parameter":::

* Создайте текст <xref:System.Linq.Expressions.LambdaExpression>, используя заданные вами выражения <xref:System.Linq.Expressions.ParameterExpression> и фабричные методы в <xref:System.Linq.Expressions.Expression>. Например, выражение, представляющее `x.StartsWith("a")`, может быть построено следующим образом:

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_body":::

* Заключите параметры и текст в [выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) с типов времени компиляции, используя соответствующую перегрузку фабричного метода <xref:System.Linq.Expressions.Expression.Lambda%2A>:

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_lambda":::

В следующих разделах описывается сценарий, в котором может потребоваться создать [выражение\<TDelegate>](xref:System.Linq.Expressions.Expression%601) для передачи в метод LINQ, а также представлен полный пример того, как это сделать с помощью фабричных методов.

### <a name="scenario"></a>Сценарий

Допустим, у вас есть несколько типов сущностей:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Entities":::

Для любого из этих типов сущностей необходимо отфильтровать и возвратить только те сущности, которые имеют заданный текст в одном из полей `string`. Для `Person` необходимо найти свойства `FirstName` и `LastName`:

```csharp
string term = /* ... */;
var personsQry = new List<Person>()
    .AsQueryable()
    .Where(x => x.FirstName.Contains(term) || x.LastName.Contains(term));
```

но для `Car` требуется найти только свойство `Model`:

```csharp
string term = /* ... */;
var carsQry = new List<Car>()
    .AsQueryable()
    .Where(x => x.Model.Contains(term));
```

Несмотря на то что можно написать одну настраиваемую функцию для `IQueryable<Person>` и другую для `IQueryable<Car>`, следующая функция добавляет эту фильтрацию в любой существующий запрос независимо от конкретного типа элемента.

### <a name="example"></a>Пример

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate":::

Поскольку функция `TextFilter` принимает и возвращает [IQueryable\<T>](xref:System.Linq.IQueryable%601) (а не только <xref:System.Linq.IQueryable>), после текстового фильтра можно добавить дополнительные элементы запроса с типом времени компиляции.

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a>Добавление узлов вызова метода в дерево выражения <xref:System.Linq.IQueryable>

При наличии <xref:System.Linq.IQueryable> вместо [IQueryable\<T>](xref:System.Linq.IQueryable%601) нельзя напрямую вызывать универсальные методы LINQ. В качестве альтернативы можно создать внутреннее дерево выражения, как показано выше, и использовать отражение для вызова соответствующего метода LINQ при передаче в дерево выражения.

Можно также дублировать функциональность метода LINQ, заключив все дерево в <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода LINQ:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_lambdaexpression":::

Обратите внимание, что в этом случае у вас нет общего заполнителя `T` времени компиляции, поэтому вы будете использовать перегрузку <xref:System.Linq.Expressions.Expression.Lambda%2A>, для которой не требуются сведения о типе времени компиляции, в результате чего вместо [выражения\<TDelegate>](xref:System.Linq.Expressions.Expression%601) создается <xref:System.Linq.Expressions.LambdaExpression>.

## <a name="the-dynamic-linq-library"></a>Динамическая библиотека LINQ

Построение деревьев выражений с помощью фабричных методов достаточно сложное занятие; проще создавать строки. [Динамическая библиотека LINQ](https://dynamic-linq.net/) предоставляет набор методов расширения для <xref:System.Linq.IQueryable>, соответствующих стандартным методам LINQ в <xref:System.Linq.Queryable>, и который принимает строки в [специальном синтаксисе](https://dynamic-linq.net/expression-language) вместо деревьев выражений. Библиотека создает соответствующее дерево выражения из строки и может возвращать результирующий преобразованный <xref:System.Linq.IQueryable>.

Например, предыдущий пример можно переписать следующим образом:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Dynamic_linq":::

## <a name="see-also"></a>См. также

- [Деревья выражений (C#)](./index.md)
- [Выполнение деревьев выражений (C#)](./how-to-execute-expression-trees.md)
- [Динамическое определение фильтров предикатов во время выполнения](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
