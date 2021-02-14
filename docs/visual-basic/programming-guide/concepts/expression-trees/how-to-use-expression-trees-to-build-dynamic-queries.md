---
description: Дополнительные сведения см. в статье как использовать деревья выражений для построения динамических запросов (Visual Basic)
title: Практическое руководство. Использование деревьев выражений для построения динамических запросов
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bb8abb22749cbf7c15b72632f60a5bd08287378d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423099"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="ff093-103">Как использовать деревья выражений для построения динамических запросов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff093-103">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="ff093-104">В LINQ деревья выражений используются для представления структурированных запросов к источникам данных, которые реализуют интерфейс <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="ff093-104">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="ff093-105">Например, поставщик LINQ реализует интерфейс <xref:System.Linq.IQueryable%601> для выполнения запросов к реляционным хранилищам данных.</span><span class="sxs-lookup"><span data-stu-id="ff093-105">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="ff093-106">Компилятор Visual Basic компилирует запросы, предназначенные для таких источников данных, в код, который создает дерево выражений во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ff093-106">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="ff093-107">Поставщик запросов может переходить по структуре данных дерева выражения и преобразовать ее в язык запросов, соответствующий источнику данных.</span><span class="sxs-lookup"><span data-stu-id="ff093-107">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="ff093-108">Деревья выражений также используются в LINQ для представления лямбда-выражений, которые присваиваются переменным типа <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="ff093-108">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="ff093-109">В этом разделе описывается использование деревьев выражений для создания динамических запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="ff093-109">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="ff093-110">Динамические запросы удобны в тех случаях, когда характеристики запроса неизвестны во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="ff093-110">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="ff093-111">Например, приложение может предоставлять пользовательский интерфейс, который позволяет конечному пользователю указать один или несколько предикатов для фильтрации данных.</span><span class="sxs-lookup"><span data-stu-id="ff093-111">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="ff093-112">Для использования LINQ для создания запросов такой тип приложения должен использовать деревья выражений для создания запроса LINQ во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ff093-112">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="ff093-113">Пример</span><span class="sxs-lookup"><span data-stu-id="ff093-113">Example</span></span>

<span data-ttu-id="ff093-114">В следующем примере показано использование деревьев выражений для создания запроса к источнику данных `IQueryable` и его выполнения.</span><span class="sxs-lookup"><span data-stu-id="ff093-114">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="ff093-115">В коде создается дерево выражения для представления следующего запроса:</span><span class="sxs-lookup"><span data-stu-id="ff093-115">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="ff093-116">Фабричные методы в пространстве имен <xref:System.Linq.Expressions> используются для создания деревьев выражений, представляющих общий запрос.</span><span class="sxs-lookup"><span data-stu-id="ff093-116">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="ff093-117">Выражения, которые представляют вызовы методов стандартных операторов запросов, ссылаются на реализации <xref:System.Linq.Queryable> этих методов.</span><span class="sxs-lookup"><span data-stu-id="ff093-117">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="ff093-118">Итоговое дерево выражения передается в реализацию <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> поставщика источника данных `IQueryable` для создания исполняемого запроса типа `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="ff093-118">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="ff093-119">Результаты получаются путем перечисления переменной запроса.</span><span class="sxs-lookup"><span data-stu-id="ff093-119">The results are obtained by enumerating that query variable.</span></span>

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

<span data-ttu-id="ff093-120">Этот код использует фиксированное число выражений в предикате, передаваемом в метод `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="ff093-120">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="ff093-121">Тем не менее можно написать приложение, которое будет сочетать переменное число выражений предиката, зависящих от вводимых пользователем данных.</span><span class="sxs-lookup"><span data-stu-id="ff093-121">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="ff093-122">Также можно изменять стандартные операторы запросов, которые вызываются в запросе, в зависимости от входных данных от пользователя.</span><span class="sxs-lookup"><span data-stu-id="ff093-122">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="ff093-123">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ff093-123">Compile the code</span></span>

- <span data-ttu-id="ff093-124">Создайте новый проект **консольного приложения**.</span><span class="sxs-lookup"><span data-stu-id="ff093-124">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="ff093-125">Включите пространство имен System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="ff093-125">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="ff093-126">Скопируйте код из примера и вставьте его в `Main` `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="ff093-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff093-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ff093-127">See also</span></span>

- <span data-ttu-id="ff093-128">[Expression Trees (Visual Basic)](index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="ff093-128">[Expression Trees (Visual Basic)](index.md)</span></span>
- [<span data-ttu-id="ff093-129">Практическое руководство. Выполнение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff093-129">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
