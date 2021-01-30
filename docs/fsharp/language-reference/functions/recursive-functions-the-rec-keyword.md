---
title: Рекурсивные функции. Ключевое слово rec
description: 'Узнайте, как ключевое слово F # REC используется с ключевым словом let для определения рекурсивной функции.'
ms.date: 08/12/2020
ms.openlocfilehash: 27f215f7b6f09646e847898c2618cfac10175e6e
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215716"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="cbe3e-103">Рекурсивные функции. Ключевое слово rec</span><span class="sxs-lookup"><span data-stu-id="cbe3e-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="cbe3e-104">`rec`Ключевое слово используется вместе с `let` ключевым словом для определения рекурсивной функции.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbe3e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbe3e-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="cbe3e-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="cbe3e-106">Remarks</span></span>

<span data-ttu-id="cbe3e-107">Рекурсивные функции — функции, которые вызывают сами себя, явным образом определяются на языке F # с помощью `rec` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="cbe3e-108">`rec`Ключевое слово делает имя `let` привязки доступным в ее тексте.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="cbe3e-109">В следующем примере показана рекурсивная функция, которая выполняет вычисление *n*-<sup>го</sup> числа Фибоначчи с помощью математического определения.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> n
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="cbe3e-110">На практике код, подобный предыдущему примеру, не является идеальным, поскольку он унецессарили повторно выполняет вычисление значений, которые уже были вычислены.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="cbe3e-111">Это обусловлено тем, что не является рекурсивным, что объясняется далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="cbe3e-112">Методы неявно являются рекурсивными в пределах типа, в котором они определены, то есть нет необходимости добавлять `rec` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="cbe3e-113">Например:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> n
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="cbe3e-114">Однако привязки let в классах не являются неявно рекурсивными.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="cbe3e-115">`let`Для функций с привязкой требуется `rec` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="cbe3e-116">Заключительная рекурсия</span><span class="sxs-lookup"><span data-stu-id="cbe3e-116">Tail recursion</span></span>

<span data-ttu-id="cbe3e-117">Для некоторых рекурсивных функций необходимо выполнить рефакторинг более "чистого" определения до первого [рекурсивного](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="cbe3e-118">Это предотвращает ненужные вычисления.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="cbe3e-119">Например, предыдущий генератор чисел Фибоначчи можно перезаписывать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="cbe3e-120">Это более сложная реализация.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-120">This is a more complicated implementation.</span></span> <span data-ttu-id="cbe3e-121">Создание числа Фибоначчи — отличный пример алгоритма "упрощенного", который математически является чистым, но неэффективным на практике.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="cbe3e-122">Некоторые аспекты делают его эффективным в F #, хотя и по-прежнему рекурсивно определяются:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="cbe3e-123">Рекурсивная внутренняя функция с именем `loop` , которая является шаблоном идиоматическим F #.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="cbe3e-124">Два агрегатных параметра, которые передают значения накопления рекурсивным вызовам.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="cbe3e-125">Проверка значения, `n` возвращающего определенную совокупность.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="cbe3e-126">Если этот пример был написан итеративно с помощью цикла, код будет выглядеть аналогично двум различным значениям, которые суммируют числа до тех пор, пока не будет выполнено определенное условие.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="cbe3e-127">Причина этого состоит в том, что рекурсивный вызов не требует сохранения каких-либо значений в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="cbe3e-128">Все вычисляемые промежуточные значения накапливаются с помощью входных данных внутренней функции.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="cbe3e-129">Это также позволяет компилятору F # оптимизировать код так же быстро, как если бы вы написали нечто вроде `while` цикла.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="cbe3e-130">Часто написание кода на F # позволяет рекурсивно обрабатывать что-то с внутренней и внешней функцией, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="cbe3e-131">Внутренняя функция использует хвостовую рекурсию, а внешняя функция — лучший интерфейс для вызывающих объектов.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="cbe3e-132">Взаимные рекурсивные функции</span><span class="sxs-lookup"><span data-stu-id="cbe3e-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="cbe3e-133">Иногда функции являются *взаимно рекурсивными*, то есть вызывают форму круга, где одна функция вызывает другую, которая, в свою очередь, вызывает первую, с любым числом вызовов между.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="cbe3e-134">Необходимо определить такие функции вместе в одной `let` привязке, используя `and` ключевое слово, чтобы связать их вместе.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="cbe3e-135">В следующем примере показаны две взаимно рекурсивные функции.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="cbe3e-136">Рекурсивные значения</span><span class="sxs-lookup"><span data-stu-id="cbe3e-136">Recursive values</span></span>

<span data-ttu-id="cbe3e-137">Можно также определить значение с `let` привязкой, которое будет рекурсивно.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="cbe3e-138">Это иногда делается для ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-138">This is sometimes done for logging.</span></span> <span data-ttu-id="cbe3e-139">С помощью F # 5 и `nameof` функции можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="cbe3e-140">См. также</span><span class="sxs-lookup"><span data-stu-id="cbe3e-140">See also</span></span>

- [<span data-ttu-id="cbe3e-141">Функции</span><span class="sxs-lookup"><span data-stu-id="cbe3e-141">Functions</span></span>](index.md)
