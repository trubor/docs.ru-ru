---
description: Дополнительные сведения см. в статье как изменить деревья выражений (Visual Basic)
title: Практическое руководство. Изменение деревьев выражений
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 13098f5588fe44be8e57c9be52a9cfe5f7cd661f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455903"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="638cf-103">Практическое руководство. Изменение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="638cf-103">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="638cf-104">В этом разделе показано, как изменить дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="638cf-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="638cf-105">Деревья выражений являются неизменяемыми, что означает невозможность их изменения напрямую.</span><span class="sxs-lookup"><span data-stu-id="638cf-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="638cf-106">Чтобы изменить дерево выражения, необходимо создать копию существующего дерева выражения, а затем внести необходимые изменения.</span><span class="sxs-lookup"><span data-stu-id="638cf-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="638cf-107">Для прохода по существующему дереву выражения и копирования каждого пройденного узла можно использовать класс <xref:System.Linq.Expressions.ExpressionVisitor>.</span><span class="sxs-lookup"><span data-stu-id="638cf-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="638cf-108">Изменение дерева выражения</span><span class="sxs-lookup"><span data-stu-id="638cf-108">To modify an expression tree</span></span>

1. <span data-ttu-id="638cf-109">Создайте новый проект **консольного приложения**.</span><span class="sxs-lookup"><span data-stu-id="638cf-109">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="638cf-110">Добавьте `Imports` в файл инструкцию для `System.Linq.Expressions` пространства имен.</span><span class="sxs-lookup"><span data-stu-id="638cf-110">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="638cf-111">Добавьте в проект класс `AndAlsoModifier`.</span><span class="sxs-lookup"><span data-stu-id="638cf-111">Add the `AndAlsoModifier` class to your project.</span></span>

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    <span data-ttu-id="638cf-112">Этот класс наследует класс <xref:System.Linq.Expressions.ExpressionVisitor> и специально предназначен для изменения выражений, которые представляют условные операции `AND`.</span><span class="sxs-lookup"><span data-stu-id="638cf-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="638cf-113">Он изменяет эти операции с условного `AND` на условное `OR`.</span><span class="sxs-lookup"><span data-stu-id="638cf-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="638cf-114">Для этого класс переопределяет метод <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> базового типа, потому что условные выражения `AND` представлены как двоичные выражения.</span><span class="sxs-lookup"><span data-stu-id="638cf-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="638cf-115">Если выражение, переданное в метод `VisitBinary`, представляет условную операцию `AND`, код создает новое выражение, которое содержит условный оператор `OR` вместо условного оператора `AND`.</span><span class="sxs-lookup"><span data-stu-id="638cf-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="638cf-116">Если выражение, передаваемое в `VisitBinary`, не представляет условную операцию `AND`, метод передает выполнение реализации базового класса.</span><span class="sxs-lookup"><span data-stu-id="638cf-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="638cf-117">Методы базового класса создают узлы, которые похожи на переданные деревья выражений, однако поддеревья этих деревьев заменены на деревья выражений, которые были рекурсивно созданы при обходе.</span><span class="sxs-lookup"><span data-stu-id="638cf-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="638cf-118">Добавьте `Imports` в файл инструкцию для `System.Linq.Expressions` пространства имен.</span><span class="sxs-lookup"><span data-stu-id="638cf-118">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="638cf-119">Добавьте код в `Main` метод в файле Module1. vb, чтобы создать дерево выражения и передать его в метод, который будет изменять его.</span><span class="sxs-lookup"><span data-stu-id="638cf-119">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    <span data-ttu-id="638cf-120">В приведенном ниже коде создается выражение, которое содержит условную операцию `AND`.</span><span class="sxs-lookup"><span data-stu-id="638cf-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="638cf-121">Затем в нем создается экземпляр класса `AndAlsoModifier`, и в метод `Modify` этого класса передается выражение.</span><span class="sxs-lookup"><span data-stu-id="638cf-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="638cf-122">Как исходные, так и измененные деревья выражений выводятся для отображения изменения.</span><span class="sxs-lookup"><span data-stu-id="638cf-122">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="638cf-123">Скомпилируйте и запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="638cf-123">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="638cf-124">См. также</span><span class="sxs-lookup"><span data-stu-id="638cf-124">See also</span></span>

- [<span data-ttu-id="638cf-125">Практическое руководство. Выполнение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="638cf-125">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- <span data-ttu-id="638cf-126">[Expression Trees (Visual Basic)](index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="638cf-126">[Expression Trees (Visual Basic)](index.md)</span></span>
