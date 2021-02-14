---
description: Дополнительные сведения см. в статье деревья выражений (Visual Basic)
title: Деревья выражений
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 7fa4f36334a5a951cbe86c6db80af77db40e245a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462260"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="71907-103">Деревья выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71907-103">Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="71907-104">Деревья выражений представляют код в виде древовидной структуры, где каждый узел является выражением, например, вызовом метода или двоичной операцией, такой как `x < y`.</span><span class="sxs-lookup"><span data-stu-id="71907-104">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="71907-105">Вы можете компилировать и выполнять код, представленный деревьями выражений.</span><span class="sxs-lookup"><span data-stu-id="71907-105">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="71907-106">Это позволяет динамически изменять выполняемый код, выполнять запросы LINQ в различных базах данных и создавать динамические запросы.</span><span class="sxs-lookup"><span data-stu-id="71907-106">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="71907-107">Дополнительные сведения о деревьях выражений в LINQ см. в разделе [Практическое руководство. Использование деревьев выражений для создания динамических запросов (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="71907-107">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="71907-108">Кроме того, деревья выражений используются в среде выполнения динамического языка (DLR) для обеспечения взаимодействия между динамическими языками и платформой .NET Framework, а также и предоставления разработчикам компиляторов возможности выдавать деревья выражений вместо промежуточного языка Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="71907-108">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="71907-109">Дополнительные сведения о DLR см. в разделе [Общие сведения о среде DLR](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71907-109">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="71907-110">Вы можете использовать компилятор C# или Visual Basic для создания дерева выражений на основе анонимного лямбда-выражения или создания деревьев выражений вручную с помощью пространства имен <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="71907-110">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="71907-111">Создание деревьев выражений на основе лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="71907-111">Creating Expression Trees from Lambda Expressions</span></span>  

 <span data-ttu-id="71907-112">Когда лямбда-выражение назначается переменной с типом <xref:System.Linq.Expressions.Expression%601>, компилятор выдает код для создания дерева выражений, представляющего лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="71907-112">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="71907-113">Компилятор Visual Basic может создавать деревья выражений только на основе лямбда-выражений (или однострочных лямбда-функций).</span><span class="sxs-lookup"><span data-stu-id="71907-113">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="71907-114">Они не могут анализировать лямбды операторов (или многострочные лямбды).</span><span class="sxs-lookup"><span data-stu-id="71907-114">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="71907-115">Дополнительные сведения о лямбда-выражениях в Visual Basic см. в разделе [Лямбда-выражения](../../language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="71907-115">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="71907-116">В следующем примере кода демонстрируется способ применения компилятора Visual Basic для создания дерева выражений, представляющего лямбда-выражение `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="71907-116">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="71907-117">Создание деревьев выражений с помощью API-интерфейса</span><span class="sxs-lookup"><span data-stu-id="71907-117">Creating Expression Trees by Using the API</span></span>  

 <span data-ttu-id="71907-118">Для создания деревьев выражений с помощью API-интерфейса используйте класс <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="71907-118">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="71907-119">Этот класс содержит статические методы фабрики, позволяющие создать узлы дерева выражения конкретного типа, например, <xref:System.Linq.Expressions.ParameterExpression>, который представляет переменную или параметр, или <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода.</span><span class="sxs-lookup"><span data-stu-id="71907-119">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="71907-120"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> и другие зависящие от выражения типы также определяются в пространстве имен <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="71907-120"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="71907-121">Эти типы являются производными от абстрактного типа <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="71907-121">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="71907-122">В следующем примере кода демонстрируется способ создания дерева выражений, представляющего лямбда-выражение `Function(num) num < 5`, с помощью API.</span><span class="sxs-lookup"><span data-stu-id="71907-122">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="71907-123">На платформе .NET Framework 4 или более поздней версии API деревьев выражений также поддерживает присваивание и выражения потока управления, такие как циклы, условные блоки и блоки `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="71907-123">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="71907-124">С помощью API можно создавать деревья выражений более сложные, чем деревья, создаваемые компилятором Visual Basic из лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="71907-124">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="71907-125">В следующем примере показан способ создания дерева выражений, которое вычисляет факториал числа.</span><span class="sxs-lookup"><span data-stu-id="71907-125">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="71907-126">Дополнительные сведения см. в записи блога [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (Создание динамических методов с использованием деревьев выражений в Visual Studio 2010), которая также применима к более поздним версиям Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71907-126">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="71907-127">Синтаксический анализ деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="71907-127">Parsing Expression Trees</span></span>  

 <span data-ttu-id="71907-128">В следующем примере кода показано, как дерево выражений, представляющее лямбда-выражение `Function(num) num < 5`, может быть разложено на части.</span><span class="sxs-lookup"><span data-stu-id="71907-128">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="71907-129">Неизменность деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="71907-129">Immutability of Expression Trees</span></span>  

 <span data-ttu-id="71907-130">Деревья выражений должны быть неизменными.</span><span class="sxs-lookup"><span data-stu-id="71907-130">Expression trees should be immutable.</span></span> <span data-ttu-id="71907-131">Это означает, что если требуется изменить дерево выражений, следует создать новое дерево выражений путем копирования существующего и заменить узлы в нем.</span><span class="sxs-lookup"><span data-stu-id="71907-131">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="71907-132">Для прохода по существующему дереву выражений можно использовать другое дерево выражений (посетитель).</span><span class="sxs-lookup"><span data-stu-id="71907-132">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="71907-133">Дополнительные сведения см. в разделе [Практическое руководство. Изменение деревьев выражений (Visual Basic)](how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="71907-133">For more information, see [How to: Modify Expression Trees (Visual Basic)](how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="71907-134">Компиляция деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="71907-134">Compiling Expression Trees</span></span>  

 <span data-ttu-id="71907-135">Тип <xref:System.Linq.Expressions.Expression%601> предоставляет метод  <xref:System.Linq.Expressions.Expression%601.Compile%2A>, который компилирует код, представляемый деревом выражений, в исполняемый делегат.</span><span class="sxs-lookup"><span data-stu-id="71907-135">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="71907-136">В следующем примере кода показан способ компиляции дерева выражений и выполнения результирующего кода.</span><span class="sxs-lookup"><span data-stu-id="71907-136">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="71907-137">Дополнительные сведения см. в разделе [Практическое руководство. Выполнение деревьев выражений (Visual Basic)](how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="71907-137">For more information, see [How to: Execute Expression Trees (Visual Basic)](how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71907-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="71907-138">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="71907-139">Практическое руководство. Выполнение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71907-139">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="71907-140">Практическое руководство. Изменение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71907-140">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
- [<span data-ttu-id="71907-141">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="71907-141">Lambda Expressions</span></span>](../../language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="71907-142">Общие сведения о среде DLR</span><span class="sxs-lookup"><span data-stu-id="71907-142">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="71907-143">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71907-143">Programming Concepts (Visual Basic)</span></span>](../index.md)
