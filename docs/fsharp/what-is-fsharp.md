---
title: Что такое F#
description: 'Сведения о языке программирования F # и программировании F #. Узнайте о типах данных, функциях и способах их совместного размещения.'
ms.date: 08/03/2018
ms.openlocfilehash: a6bad3e1db63c3fe948b5916925d5eb24a18a41c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739481"
---
# <a name="what-is-f"></a><span data-ttu-id="edc1d-104">Что такое F\#</span><span class="sxs-lookup"><span data-stu-id="edc1d-104">What is F\#</span></span>

<span data-ttu-id="edc1d-105">F # — это функциональный язык программирования, упрощающий написание правильного и сопровождаемого кода.</span><span class="sxs-lookup"><span data-stu-id="edc1d-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="edc1d-106">Программирование F # в основном включает определение типов и функций, которые выводятся и обобщены автоматически.</span><span class="sxs-lookup"><span data-stu-id="edc1d-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="edc1d-107">Это позволяет сосредоточиться на проблемном домене и манипулировать его данными, а не на деталях программирования.</span><span class="sxs-lookup"><span data-stu-id="edc1d-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn $"{greeting}")

    0
```

<span data-ttu-id="edc1d-108">F # содержит множество функций, включая:</span><span class="sxs-lookup"><span data-stu-id="edc1d-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="edc1d-109">Упрощенный синтаксис</span><span class="sxs-lookup"><span data-stu-id="edc1d-109">Lightweight syntax</span></span>
* <span data-ttu-id="edc1d-110">Неизменяемое по умолчанию</span><span class="sxs-lookup"><span data-stu-id="edc1d-110">Immutable by default</span></span>
* <span data-ttu-id="edc1d-111">Определение типа и автоматическое обобщение</span><span class="sxs-lookup"><span data-stu-id="edc1d-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="edc1d-112">Функции первого класса</span><span class="sxs-lookup"><span data-stu-id="edc1d-112">First-class functions</span></span>
* <span data-ttu-id="edc1d-113">Мощные типы данных</span><span class="sxs-lookup"><span data-stu-id="edc1d-113">Powerful data types</span></span>
* <span data-ttu-id="edc1d-114">Регулярные выражения</span><span class="sxs-lookup"><span data-stu-id="edc1d-114">Pattern matching</span></span>
* <span data-ttu-id="edc1d-115">Асинхронное программирование</span><span class="sxs-lookup"><span data-stu-id="edc1d-115">Async programming</span></span>

<span data-ttu-id="edc1d-116">Полный набор функций приведен в [справочнике по языку F #](./language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="edc1d-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="edc1d-117">Типы данных с богатыми возможностями</span><span class="sxs-lookup"><span data-stu-id="edc1d-117">Rich data types</span></span>

<span data-ttu-id="edc1d-118">Типы данных, такие как [записи](./language-reference/records.md) и [Размеченные объединения](./language-reference/discriminated-unions.md) , позволяют представлять сложные данные и домены.</span><span class="sxs-lookup"><span data-stu-id="edc1d-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

```fsharp
// Group data with Records
type SuccessfulWithdrawal =
    { Amount: decimal
      Balance: decimal }

type FailedWithdrawal =
    { Amount: decimal
      Balance: decimal
      IsOverdraft: bool }

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

<span data-ttu-id="edc1d-119">Записи F # и размеченные объединения не равны NULL, неизменяемы и сравнимы по умолчанию, что делает их очень простыми в использовании.</span><span class="sxs-lookup"><span data-stu-id="edc1d-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="edc1d-120">Принудительная правильность с помощью функций и сопоставления шаблонов</span><span class="sxs-lookup"><span data-stu-id="edc1d-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="edc1d-121">Функции F # легко объявляются и являются мощными на практике.</span><span class="sxs-lookup"><span data-stu-id="edc1d-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="edc1d-122">В сочетании с [сопоставлением шаблонов](./language-reference/pattern-matching.md)они позволяют определить поведение, корректность которого обеспечивается компилятором.</span><span class="sxs-lookup"><span data-stu-id="edc1d-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f{s.Amount}"
    | InsufficientFunds f -> printfn "Failed: balance is %f{f.Balance}"
    | CardExpired d -> printfn "Failed: card expired on {d}"
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

<span data-ttu-id="edc1d-123">Функции F # также являются первыми классами, то есть они могут передаваться в качестве параметров и возвращаться из других функций.</span><span class="sxs-lookup"><span data-stu-id="edc1d-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="edc1d-124">Функции для определения операций с объектами</span><span class="sxs-lookup"><span data-stu-id="edc1d-124">Functions to define operations on objects</span></span>

<span data-ttu-id="edc1d-125">F # обеспечивает полную поддержку объектов, которые являются полезными типами данных, когда требуется смешивать данные и функциональность.</span><span class="sxs-lookup"><span data-stu-id="edc1d-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="edc1d-126">Функции F # используются для работы с объектами.</span><span class="sxs-lookup"><span data-stu-id="edc1d-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="edc1d-127">Вместо написания кода, который является объектно-ориентированным, в F # часто создается код, который обрабатывает объекты как другой тип данных для функций, которыми необходимо управлять.</span><span class="sxs-lookup"><span data-stu-id="edc1d-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="edc1d-128">Такие функции, как [универсальные интерфейсы](./language-reference/interfaces.md), [выражения объектов](./language-reference/object-expressions.md)и разумное использование [элементов](./language-reference/members/index.md) , являются общими в более крупных программах F #.</span><span class="sxs-lookup"><span data-stu-id="edc1d-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="edc1d-129">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="edc1d-129">Next steps</span></span>

<span data-ttu-id="edc1d-130">Дополнительные сведения о большем наборе функций F # см. в [обзоре f #](tour.md).</span><span class="sxs-lookup"><span data-stu-id="edc1d-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
