---
title: Введение в функциональное программирование на F#
description: Сведения об основах функционального программирования на F#.
ms.date: 10/29/2018
ms.openlocfilehash: fc2aebe80de16b92942c3557c0e03c198883dde1
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740332"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="ad91d-103">Введение в функциональное программирование на F\#</span><span class="sxs-lookup"><span data-stu-id="ad91d-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="ad91d-104">Функциональное программирование — это стиль программирования, в котором особое значение придается использованию функций и неизменяемых данных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="ad91d-105">Типизированное функциональное программирование — это сочетание функционального программирования со статическими типами, как это характерно для F#.</span><span class="sxs-lookup"><span data-stu-id="ad91d-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="ad91d-106">В целом в функциональном программировании применяются такие основные подходы:</span><span class="sxs-lookup"><span data-stu-id="ad91d-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="ad91d-107">функции как основные используемые конструкции;</span><span class="sxs-lookup"><span data-stu-id="ad91d-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="ad91d-108">выражения вместо инструкций;</span><span class="sxs-lookup"><span data-stu-id="ad91d-108">Expressions instead of statements</span></span>
* <span data-ttu-id="ad91d-109">неизменяемые значения имеют приоритет перед переменными;</span><span class="sxs-lookup"><span data-stu-id="ad91d-109">Immutable values over variables</span></span>
* <span data-ttu-id="ad91d-110">декларативное программирование имеет приоритет перед императивным программированием.</span><span class="sxs-lookup"><span data-stu-id="ad91d-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="ad91d-111">В этой серии вы ознакомитесь с основными понятиями и особенностями функционального программирования на F#.</span><span class="sxs-lookup"><span data-stu-id="ad91d-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="ad91d-112">Кроме того, в процессе вы немного научитесь писать код на F#.</span><span class="sxs-lookup"><span data-stu-id="ad91d-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="ad91d-113">Терминология</span><span class="sxs-lookup"><span data-stu-id="ad91d-113">Terminology</span></span>

<span data-ttu-id="ad91d-114">Функциональное программирование, как и другие подходы программирования, имеет свой словарь, который вам придется изучить.</span><span class="sxs-lookup"><span data-stu-id="ad91d-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="ad91d-115">Ниже приведены некоторые распространенные термины:</span><span class="sxs-lookup"><span data-stu-id="ad91d-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="ad91d-116">**Функция** — это конструкция, которая возвращает выходные данные при наличии входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="ad91d-117">Фактически она _сопоставляет_ элемент из одного набора с другим набором.</span><span class="sxs-lookup"><span data-stu-id="ad91d-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="ad91d-118">На практике такой подход может реализоваться разными способами, особенно при использовании функций, которые работают с коллекциями данных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="ad91d-119">Это самое простое (и важное) понятие в функциональном программировании.</span><span class="sxs-lookup"><span data-stu-id="ad91d-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="ad91d-120">**Выражение** — это конструкция в коде, которая возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="ad91d-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="ad91d-121">В F# это значение должно быть привязано или явно игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="ad91d-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="ad91d-122">Выражение можно легко заменить вызовом функции.</span><span class="sxs-lookup"><span data-stu-id="ad91d-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="ad91d-123">**Чистота** — это свойство функции, которое означает, что возвращаемое значение всегда будет одним и тем же при использовании одних и тех же аргументов, а ее выполнение не имеет побочных эффектов.</span><span class="sxs-lookup"><span data-stu-id="ad91d-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="ad91d-124">Чистая функция полностью зависит от своих аргументов.</span><span class="sxs-lookup"><span data-stu-id="ad91d-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="ad91d-125">**Ссылочная прозрачность** — это свойство выражений, которое означает, что их можно заменить выходными данными без изменения поведения программы.</span><span class="sxs-lookup"><span data-stu-id="ad91d-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="ad91d-126">**Неизменяемость** — означает, что значение нельзя изменить на месте.</span><span class="sxs-lookup"><span data-stu-id="ad91d-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="ad91d-127">Но переменные можно изменить на месте.</span><span class="sxs-lookup"><span data-stu-id="ad91d-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="ad91d-128">Примеры</span><span class="sxs-lookup"><span data-stu-id="ad91d-128">Examples</span></span>

<span data-ttu-id="ad91d-129">Все эти основные понятия демонстрируются в приведенных ниже примерах.</span><span class="sxs-lookup"><span data-stu-id="ad91d-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="ad91d-130">Функции</span><span class="sxs-lookup"><span data-stu-id="ad91d-130">Functions</span></span>

<span data-ttu-id="ad91d-131">Самая распространенная и основная конструкция функционального программирования — это функция.</span><span class="sxs-lookup"><span data-stu-id="ad91d-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="ad91d-132">Ниже приведена простая функция, которая добавляет 1 к целому числу:</span><span class="sxs-lookup"><span data-stu-id="ad91d-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="ad91d-133">Ее сигнатура типа имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="ad91d-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="ad91d-134">Сигнатуру можно прочитать как "`addOne` принимает значение типа `int` с именем `x` и возвращает значение типа `int`".</span><span class="sxs-lookup"><span data-stu-id="ad91d-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="ad91d-135">Фактически `addOne` — это _сопоставление_ значения из набора целых чисел с набором целых чисел.</span><span class="sxs-lookup"><span data-stu-id="ad91d-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="ad91d-136">Такое сопоставление обозначено маркером `->`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="ad91d-137">В F# вы можете просмотреть сигнатуру функции, чтобы узнать ее назначение.</span><span class="sxs-lookup"><span data-stu-id="ad91d-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="ad91d-138">Так в чем важность сигнатуры?</span><span class="sxs-lookup"><span data-stu-id="ad91d-138">So, why is the signature important?</span></span> <span data-ttu-id="ad91d-139">В типизированном функциональном программировании реализация функции часто менее важна, чем фактическая сигнатура типа.</span><span class="sxs-lookup"><span data-stu-id="ad91d-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="ad91d-140">Тот факт, что `addOne` добавляет значение 1 к целому числу, представляет интерес во время выполнения. Но при создании программы именно тот факт, что функция принимает и возвращает значение типа `int`, определяет, как вы будете использовать ее.</span><span class="sxs-lookup"><span data-stu-id="ad91d-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="ad91d-141">Кроме того, если эта функция используется правильно (с учетом сигнатуры типа), диагностику проблем можно выполнить только в теле функции `addOne`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="ad91d-142">Это и обуславливает особенности типизированного функционального программирования.</span><span class="sxs-lookup"><span data-stu-id="ad91d-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="ad91d-143">Выражения</span><span class="sxs-lookup"><span data-stu-id="ad91d-143">Expressions</span></span>

<span data-ttu-id="ad91d-144">Выражения — это конструкции, возвращающие значения.</span><span class="sxs-lookup"><span data-stu-id="ad91d-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="ad91d-145">В отличие от инструкций, выполняющих действия, выражения можно рассматривать как действия с возвратом значения.</span><span class="sxs-lookup"><span data-stu-id="ad91d-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="ad91d-146">В функциональном программировании приоритет практически всегда отдается выражениям, а не инструкциям.</span><span class="sxs-lookup"><span data-stu-id="ad91d-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="ad91d-147">Давайте рассмотрим предыдущую функцию, `addOne`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="ad91d-148">Тело функции `addOne` — это выражение:</span><span class="sxs-lookup"><span data-stu-id="ad91d-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="ad91d-149">Это результат выражения, определяющий тип результата функции `addOne`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="ad91d-150">Например, выражение, образующее эту функцию, можно изменить на другой тип, такой как `string`:</span><span class="sxs-lookup"><span data-stu-id="ad91d-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="ad91d-151">Сигнатура функции теперь выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ad91d-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="ad91d-152">Так как для любого типа в F# можно вызвать `ToString()`, тип `x` изменен на универсальный (с помощью [автоматического обобщения](../language-reference/generics/automatic-generalization.md)), а результирующий тип — это `string`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="ad91d-153">Выражения — это не просто тела функций.</span><span class="sxs-lookup"><span data-stu-id="ad91d-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="ad91d-154">Вы можете использовать выражения, возвращающие значение, которое затем используется в другой области.</span><span class="sxs-lookup"><span data-stu-id="ad91d-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="ad91d-155">Одно из распространенных выражений — это `if`:</span><span class="sxs-lookup"><span data-stu-id="ad91d-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="ad91d-156">Выражение `if` возвращает значение с именем `result`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="ad91d-157">Обратите внимание, что `result` можно полностью опустить, сделав выражение `if` телом функции `addOneIfOdd`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="ad91d-158">Главное, о чем нужно помнить при использовании выражений, это то, что они возвращают значение.</span><span class="sxs-lookup"><span data-stu-id="ad91d-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="ad91d-159">Существует специальный тип выражений, `unit`, который используется, если результат возвращать не нужно.</span><span class="sxs-lookup"><span data-stu-id="ad91d-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="ad91d-160">Рассмотрим, например, следующую простую функцию:</span><span class="sxs-lookup"><span data-stu-id="ad91d-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

<span data-ttu-id="ad91d-161">Сигнатура выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ad91d-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="ad91d-162">Тип `unit` указывает, что значение не возвращается.</span><span class="sxs-lookup"><span data-stu-id="ad91d-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="ad91d-163">Это полезно, если у вас есть подпрограммы, которые должны выполнять действия, но при этом без возврата результата.</span><span class="sxs-lookup"><span data-stu-id="ad91d-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="ad91d-164">Такой подход сильно отличается от подхода императивного программирования, где эквивалентная конструкция `if` является инструкцией, а возврат значений часто осуществляется с помощью изменения переменных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="ad91d-165">Например, в C# код можно написать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ad91d-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="ad91d-166">Стоит отметить, что C# и другие языки в стиле C поддерживают [тернарное выражение](../../csharp/language-reference/operators/conditional-operator.md), что позволяет применять условное программирование на основе выражений.</span><span class="sxs-lookup"><span data-stu-id="ad91d-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="ad91d-167">В функциональном программировании инструкции редко используются для изменения значений.</span><span class="sxs-lookup"><span data-stu-id="ad91d-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="ad91d-168">Хотя некоторые функциональные языки поддерживают инструкции и изменения, в функциональном программировании редко используется такой подход.</span><span class="sxs-lookup"><span data-stu-id="ad91d-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="ad91d-169">Чистые функции</span><span class="sxs-lookup"><span data-stu-id="ad91d-169">Pure functions</span></span>

<span data-ttu-id="ad91d-170">Как было сказано ранее, чистые функции — это функции, которые:</span><span class="sxs-lookup"><span data-stu-id="ad91d-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="ad91d-171">всегда возвращают одно и то же значение для одних и тех же входных данных;</span><span class="sxs-lookup"><span data-stu-id="ad91d-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="ad91d-172">не имеют побочных эффектов.</span><span class="sxs-lookup"><span data-stu-id="ad91d-172">Have no side effects.</span></span>

<span data-ttu-id="ad91d-173">В этом контексте чистые функции удобно сравнить с математическими функциями.</span><span class="sxs-lookup"><span data-stu-id="ad91d-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="ad91d-174">В математике функции зависят только от своих аргументов и не имеют побочных эффектов.</span><span class="sxs-lookup"><span data-stu-id="ad91d-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="ad91d-175">В математической функции `f(x) = x + 1` значение `f(x)` зависит только от значения `x`.</span><span class="sxs-lookup"><span data-stu-id="ad91d-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="ad91d-176">Чистые функции в функциональном программировании ведут себя так же.</span><span class="sxs-lookup"><span data-stu-id="ad91d-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="ad91d-177">При написании чистой функции она должна зависеть только от своих аргументов и не выполнять какие-либо действия, которые приводят к побочному результату.</span><span class="sxs-lookup"><span data-stu-id="ad91d-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="ad91d-178">Ниже приведен пример функции, не являющейся чистой, так как она зависит от глобального изменяемого состояния:</span><span class="sxs-lookup"><span data-stu-id="ad91d-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="ad91d-179">Очевидно, что функция `addOneToValue` не является чистой, так как `value` можно изменить в любое время на другое значение, отличное от 1.</span><span class="sxs-lookup"><span data-stu-id="ad91d-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="ad91d-180">В функциональном программировании следует избегать такого подхода с зависимостью от глобального значения.</span><span class="sxs-lookup"><span data-stu-id="ad91d-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="ad91d-181">Ниже приведен еще один пример функции, не являющейся чистой, так как она имеет побочный эффект:</span><span class="sxs-lookup"><span data-stu-id="ad91d-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

<span data-ttu-id="ad91d-182">Эта функция не зависит от глобального значения, но она записывает значение `x` в выходные данные программы.</span><span class="sxs-lookup"><span data-stu-id="ad91d-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="ad91d-183">Хотя в этом нет ничего плохого, это означает, что функция не является чистой.</span><span class="sxs-lookup"><span data-stu-id="ad91d-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="ad91d-184">Если другая часть программы зависит от внешнего для программы объекта, например выходного буфера, вызов этой функции может повлиять на другую часть программы.</span><span class="sxs-lookup"><span data-stu-id="ad91d-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="ad91d-185">Если удалить инструкцию `printfn`, функция станет чистой:</span><span class="sxs-lookup"><span data-stu-id="ad91d-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="ad91d-186">Хотя эта функция сама по себе не является _лучшим_ вариантом, чем предыдущая версия с инструкцией `printfn`, она гарантирует только возврат значения. Другие действия не выполняются.</span><span class="sxs-lookup"><span data-stu-id="ad91d-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="ad91d-187">При вызове этой функции любое количество раз вы получите одинаковый результат.</span><span class="sxs-lookup"><span data-stu-id="ad91d-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="ad91d-188">Многие разработчики, использующие функциональное программирование, ценят такую предсказуемость, обеспечиваемую чистотой.</span><span class="sxs-lookup"><span data-stu-id="ad91d-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="ad91d-189">Неизменяемость</span><span class="sxs-lookup"><span data-stu-id="ad91d-189">Immutability</span></span>

<span data-ttu-id="ad91d-190">Наконец, одно из самых основных понятий типизированного функционального программирования — это неизменяемость.</span><span class="sxs-lookup"><span data-stu-id="ad91d-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="ad91d-191">В F# все значения являются неизменяемыми по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ad91d-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="ad91d-192">Это означает, что их нельзя изменить без обработки, если только вы не пометите их как изменяемые.</span><span class="sxs-lookup"><span data-stu-id="ad91d-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="ad91d-193">На практике работа с неизменяемыми значениями приводит к тому, что вам придется менять подход к программированию с "мне нужно изменить что-нибудь" на "мне нужно получить новое значение".</span><span class="sxs-lookup"><span data-stu-id="ad91d-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="ad91d-194">Например, если добавить 1 к значению, будет создано новое значение, а не изменено существующее:</span><span class="sxs-lookup"><span data-stu-id="ad91d-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="ad91d-195">В F# следующий код **не** изменяет функцию `value`, а выполняет проверку равенства:</span><span class="sxs-lookup"><span data-stu-id="ad91d-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="ad91d-196">Некоторые языки функционального программирования совершенно не поддерживают изменяемость.</span><span class="sxs-lookup"><span data-stu-id="ad91d-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="ad91d-197">В F# она поддерживается, но не является поведением по умолчанию для значений.</span><span class="sxs-lookup"><span data-stu-id="ad91d-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="ad91d-198">Этот подход применяется и к структурам данных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="ad91d-199">В функциональном программировании неизменяемые структуры данных, такие как наборы (и многие другие), имеют реализацию, отличную от той, которую вы можете ожидать.</span><span class="sxs-lookup"><span data-stu-id="ad91d-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="ad91d-200">Фактически такие действия, как добавление элемента в набор, приводят не к изменению набора, а к созданию _нового_ набора с добавленным значением.</span><span class="sxs-lookup"><span data-stu-id="ad91d-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="ad91d-201">На внутреннем уровне при этом часто используется другая структура данных, которая позволяет эффективно отслеживать значение, чтобы в результате можно было получить соответствующее представление данных.</span><span class="sxs-lookup"><span data-stu-id="ad91d-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="ad91d-202">Такой стиль работы со значениями и структурами данных критически важен, так как он вынуждает рассматривать любые операции, которые вносят изменения, как операции, создающие новые версии целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="ad91d-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="ad91d-203">Это позволяет обеспечить согласованность равенства и сравнения в программах.</span><span class="sxs-lookup"><span data-stu-id="ad91d-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad91d-204">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ad91d-204">Next steps</span></span>

<span data-ttu-id="ad91d-205">В следующем разделе будут подробно рассмотрены функции, а также различные способы их использования в функциональном программировании.</span><span class="sxs-lookup"><span data-stu-id="ad91d-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="ad91d-206">В статье [Функции первого класса](first-class-functions.md) подробно рассматриваются функции и то, как их можно использовать в различных контекстах.</span><span class="sxs-lookup"><span data-stu-id="ad91d-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="ad91d-207">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="ad91d-207">Further reading</span></span>

<span data-ttu-id="ad91d-208">Серия [Функциональное мышление](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) — это еще один отличный ресурс для изучения функционального программирования на F#.</span><span class="sxs-lookup"><span data-stu-id="ad91d-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="ad91d-209">В ней доступно описаны основы функционального программирования с практическими примерами использования функций F# для иллюстрации понятий.</span><span class="sxs-lookup"><span data-stu-id="ad91d-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
