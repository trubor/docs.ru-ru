---
description: Дополнительные сведения см. в статье как выполнять деревья выражений (Visual Basic)
title: Практическое руководство. Выполнение деревьев выражений
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: debd850f35d8239c20d9b848a43dafd76ac19bbc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430707"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="12cf2-103">Практическое руководство. Выполнение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12cf2-103">How to: Execute Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="12cf2-104">В этом разделе показано, как выполнить дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="12cf2-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="12cf2-105">В результате выполнения дерева выражения может возвращаться значение или просто выполняться действие, такое как вызов метода.</span><span class="sxs-lookup"><span data-stu-id="12cf2-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="12cf2-106">Можно выполнять только деревья выражений, представляющие лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="12cf2-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="12cf2-107">Деревья выражений, представляющие лямбда-выражения, имеют тип <xref:System.Linq.Expressions.LambdaExpression> или <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="12cf2-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="12cf2-108">Для выполнения таких деревьев выражений вызовите метод <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>, чтобы создать исполняемый делегат, а затем вызовите делегат.</span><span class="sxs-lookup"><span data-stu-id="12cf2-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12cf2-109">Если тип делегата неизвестен, то есть лямбда-выражение имеет тип <xref:System.Linq.Expressions.LambdaExpression>, а не тип <xref:System.Linq.Expressions.Expression%601>, необходимо вызвать метод <xref:System.Delegate.DynamicInvoke%2A> для делегата, а не напрямую.</span><span class="sxs-lookup"><span data-stu-id="12cf2-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="12cf2-110">Если дерево выражения не представляет лямбда-выражение, можно создать новое лямбда-выражение, в качестве тела которого будет использоваться исходное дерево выражения. Для этого следует вызвать метод <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="12cf2-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="12cf2-111">Затем можно выполнить лямбда-выражение, как описано ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="12cf2-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12cf2-112">Пример</span><span class="sxs-lookup"><span data-stu-id="12cf2-112">Example</span></span>  

 <span data-ttu-id="12cf2-113">В приведенном ниже примере кода показано, как путем создания и выполнения лямбда-выражения выполнить дерево выражения, которое представляет возведение числа в степень.</span><span class="sxs-lookup"><span data-stu-id="12cf2-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="12cf2-114">Выводится результат, представляющий число, возведенное в степень.</span><span class="sxs-lookup"><span data-stu-id="12cf2-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="12cf2-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="12cf2-115">Compile the code</span></span>  
  
- <span data-ttu-id="12cf2-116">Включите пространство имен System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="12cf2-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12cf2-117">См. также</span><span class="sxs-lookup"><span data-stu-id="12cf2-117">See also</span></span>

- <span data-ttu-id="12cf2-118">[Expression Trees (Visual Basic)](index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="12cf2-118">[Expression Trees (Visual Basic)](index.md)</span></span>
- [<span data-ttu-id="12cf2-119">Практическое руководство. Изменение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12cf2-119">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
