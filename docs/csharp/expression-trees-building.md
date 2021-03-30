---
title: Построение деревьев выражений
description: Сведения о способах построения деревьев выражений.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: f6752879dc01080e056221b00ca5377a6abc20db
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875815"
---
# <a name="building-expression-trees"></a><span data-ttu-id="4049f-103">Построение деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="4049f-103">Building Expression Trees</span></span>

[<span data-ttu-id="4049f-104">Предыдущий раздел — "Интерпретация выражений"</span><span class="sxs-lookup"><span data-stu-id="4049f-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="4049f-105">Все деревья выражений, которые вы уже видели, были созданы с помощью компилятора C#.</span><span class="sxs-lookup"><span data-stu-id="4049f-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="4049f-106">Все, что нужно было сделать, — это создать лямбда-выражение, которое было присвоено переменной, типизированной как `Expression<Func<T>>`, или имеющий схожий тип.</span><span class="sxs-lookup"><span data-stu-id="4049f-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="4049f-107">Это не единственный способ создания дерева выражений.</span><span class="sxs-lookup"><span data-stu-id="4049f-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="4049f-108">Во многих случаях может понадобиться создать выражение в памяти во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4049f-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="4049f-109">Процесс построения деревьев выражений усложняется тем фактом, что эти деревья выражений являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="4049f-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="4049f-110">Неизменяемость означает, что дерево необходимо создать, начиная с листьев и заканчивая корнем.</span><span class="sxs-lookup"><span data-stu-id="4049f-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="4049f-111">API-интерфейсы, которые будут использоваться для создания деревьев выражений, отражают этот факт: методы, используемые для создания узла, будут принимать все его дочерние узлы в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="4049f-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="4049f-112">Рассмотрим несколько примеров, демонстрирующих способы создания.</span><span class="sxs-lookup"><span data-stu-id="4049f-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="4049f-113">Создание узлов</span><span class="sxs-lookup"><span data-stu-id="4049f-113">Creating Nodes</span></span>

<span data-ttu-id="4049f-114">Начнем с относительно простого варианта.</span><span class="sxs-lookup"><span data-stu-id="4049f-114">Let's start relatively simply again.</span></span> <span data-ttu-id="4049f-115">Мы будем использовать выражение сложения, которое применялось в этих разделах:</span><span class="sxs-lookup"><span data-stu-id="4049f-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="4049f-116">Чтобы построить дерево выражения, необходимо создать конечные узлы.</span><span class="sxs-lookup"><span data-stu-id="4049f-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="4049f-117">Конечные узлы являются константами, поэтому для их создания можно использовать метод `Expression.Constant`:</span><span class="sxs-lookup"><span data-stu-id="4049f-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="4049f-118">Затем вы создадите выражение сложения:</span><span class="sxs-lookup"><span data-stu-id="4049f-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="4049f-119">После этого можно создать лямбда-выражение:</span><span class="sxs-lookup"><span data-stu-id="4049f-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="4049f-120">Это очень простое лямбда-выражение, так как оно не содержит аргументов.</span><span class="sxs-lookup"><span data-stu-id="4049f-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="4049f-121">Далее в этом разделе вы узнаете, как сопоставлять аргументы с параметрами и создавать более сложные выражения.</span><span class="sxs-lookup"><span data-stu-id="4049f-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="4049f-122">Для выражений, которые так же просты, как и это, можно совместить все вызовы в одну инструкцию:</span><span class="sxs-lookup"><span data-stu-id="4049f-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="4049f-123">Построение дерева</span><span class="sxs-lookup"><span data-stu-id="4049f-123">Building a Tree</span></span>

<span data-ttu-id="4049f-124">Это основные принципы построения дерева выражения в памяти.</span><span class="sxs-lookup"><span data-stu-id="4049f-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="4049f-125">Более сложные деревья обычно характеризуются большим количеством типов узлов и количеством самих узлов.</span><span class="sxs-lookup"><span data-stu-id="4049f-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="4049f-126">Рассмотрим еще один пример и взглянем на два дополнительных типа узлов, которые обычно создаются при построении деревьев выражений: узлы аргументов и узлы вызовов методов.</span><span class="sxs-lookup"><span data-stu-id="4049f-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="4049f-127">Построим дерево выражения, чтобы создать это выражение:</span><span class="sxs-lookup"><span data-stu-id="4049f-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="4049f-128">Начнем с создания выражений параметров для `x` и `y`:</span><span class="sxs-lookup"><span data-stu-id="4049f-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="4049f-129">Создание выражений умножения и сложения выполняется по шаблону, который вы уже видели:</span><span class="sxs-lookup"><span data-stu-id="4049f-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="4049f-130">Затем необходимо создать выражение вызова метода для вызова `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="4049f-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="4049f-131">И, наконец, нужно поместить вызов метода в лямбда-выражение и определить аргументы для лямбда-выражения:</span><span class="sxs-lookup"><span data-stu-id="4049f-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="4049f-132">В этом более сложном примере используется несколько дополнительных приемов, зачастую необходимых при созданий деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="4049f-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="4049f-133">Во-первых, необходимо создать объекты, представляющие параметры или локальные переменные, перед их использованием.</span><span class="sxs-lookup"><span data-stu-id="4049f-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="4049f-134">Созданные объекты можно использовать в дереве выражения там, где это необходимо.</span><span class="sxs-lookup"><span data-stu-id="4049f-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="4049f-135">Во-вторых, необходимо использовать подмножество API-интерфейсов отражения для создания объекта `MethodInfo`, чтобы можно было построить дерево выражения для получения доступа к этому методу.</span><span class="sxs-lookup"><span data-stu-id="4049f-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="4049f-136">Необходимо ограничить подмножество API-интерфейсов отражения, доступных на платформе .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4049f-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="4049f-137">Эти способы можно будет использовать для других деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="4049f-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="4049f-138">Всестороннее создание кода</span><span class="sxs-lookup"><span data-stu-id="4049f-138">Building Code In Depth</span></span>

<span data-ttu-id="4049f-139">С помощью этих API вы можете создавать что угодно.</span><span class="sxs-lookup"><span data-stu-id="4049f-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="4049f-140">Однако чем более сложное дерево выражения вы хотите построить, тем более сложными являются задачи чтения кода и управления им.</span><span class="sxs-lookup"><span data-stu-id="4049f-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="4049f-141">Давайте создадим дерево выражения, которое эквивалентно этому коду:</span><span class="sxs-lookup"><span data-stu-id="4049f-141">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="4049f-142">Обратите внимание, что было построено не дерево выражения, а просто делегат.</span><span class="sxs-lookup"><span data-stu-id="4049f-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="4049f-143">С помощью класса `Expression` нельзя создать лямбды операторов.</span><span class="sxs-lookup"><span data-stu-id="4049f-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="4049f-144">Ниже приведен код, необходимый для формирования тех же функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="4049f-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="4049f-145">Он усложняется тем фактом, что API для создания цикла `while` не существует. Вместо этого необходимо создать цикл, который содержит проверку условий, и целевой объект метки для разрыва цикла.</span><span class="sxs-lookup"><span data-stu-id="4049f-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="4049f-146">Код для создания дерева выражения для функции факториала немного больше, более сложен и содержит операторы меток и прерываний и другие элементы, использования которых хотелось бы избежать при выполнении ежедневных задач по созданию кода.</span><span class="sxs-lookup"><span data-stu-id="4049f-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="4049f-147">Для работы в этом разделе также обновлен код посетителя для просмотра каждого узла в этом дереве выражения и записи сведений об узлах, созданных в этом примере.</span><span class="sxs-lookup"><span data-stu-id="4049f-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="4049f-148">[Просмотреть или скачать пример кода](https://github.com/dotnet/samples/tree/main/csharp/expression-trees) можно в репозитории dotnet/docs на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="4049f-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/main/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="4049f-149">Поэкспериментируйте со сборкой и использованием примеров кода.</span><span class="sxs-lookup"><span data-stu-id="4049f-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="4049f-150">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="4049f-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="4049f-151">Изучение API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="4049f-151">Examining the APIs</span></span>

<span data-ttu-id="4049f-152">Возможности навигации по API-интерфейсам дерева выражений усложнены в .NET Core, но это нормально.</span><span class="sxs-lookup"><span data-stu-id="4049f-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="4049f-153">Их назначение довольно сложное — написание кода, который создает код во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4049f-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="4049f-154">Они с трудом обеспечивают баланс между поддержкой всех структур управления, доступных на языке C#, и сохранением минимально возможного размера контактной зоны API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="4049f-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="4049f-155">Этот баланс означает, что многие структуры управления представлены не своими конструкциями C#, а конструкциями, которые представляют базовую логику, создаваемую компилятором из этих конструкций более высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="4049f-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="4049f-156">Кроме того, в настоящее время не существует выражений C#, которые создаются напрямую с помощью методов класса `Expression`.</span><span class="sxs-lookup"><span data-stu-id="4049f-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="4049f-157">Как правило, это будут новые операторы и выражения, добавленные в C# 5 и C# 6.</span><span class="sxs-lookup"><span data-stu-id="4049f-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="4049f-158">(Например, выражения `async` не могут быть созданы, и новый оператор `?.` нельзя создать напрямую.)</span><span class="sxs-lookup"><span data-stu-id="4049f-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="4049f-159">Следующий раздел — "Преобразование выражений"</span><span class="sxs-lookup"><span data-stu-id="4049f-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
