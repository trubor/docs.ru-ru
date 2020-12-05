---
title: Параметры и аргументы
description: 'Сведения о поддержке языка F # для определения параметров и передачи аргументов в функции, методы и свойства.'
ms.date: 08/15/2020
ms.openlocfilehash: 3c391ca37a1cf3bd150316943e5b06efa532b317
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740293"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="c1835-103">Параметры и аргументы</span><span class="sxs-lookup"><span data-stu-id="c1835-103">Parameters and Arguments</span></span>

<span data-ttu-id="c1835-104">В этом разделе описывается языковая поддержка для определения параметров и передачи аргументов в функции, методы и свойства.</span><span class="sxs-lookup"><span data-stu-id="c1835-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="c1835-105">Он содержит сведения о том, как передавать данные по ссылке, а также определять и использовать методы, которые могут принимать переменное число аргументов.</span><span class="sxs-lookup"><span data-stu-id="c1835-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="c1835-106">Параметры и аргументы</span><span class="sxs-lookup"><span data-stu-id="c1835-106">Parameters and Arguments</span></span>

<span data-ttu-id="c1835-107">*Параметр* term используется для описания имен для значений, которые должны быть указаны.</span><span class="sxs-lookup"><span data-stu-id="c1835-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="c1835-108">*Аргумент* term используется для значений, предоставленных для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="c1835-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="c1835-109">Параметры могут быть указаны в кортеже или в каррированных форме или в некоторой комбинации этих двух значений.</span><span class="sxs-lookup"><span data-stu-id="c1835-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="c1835-110">Аргументы можно передать с помощью явного имени параметра.</span><span class="sxs-lookup"><span data-stu-id="c1835-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="c1835-111">Параметры методов можно указать как необязательные и задавая значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c1835-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="c1835-112">Шаблоны параметров</span><span class="sxs-lookup"><span data-stu-id="c1835-112">Parameter Patterns</span></span>

<span data-ttu-id="c1835-113">Параметры, предоставляемые функциям и методам, обычно являются шаблонами, разделенными пробелами.</span><span class="sxs-lookup"><span data-stu-id="c1835-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="c1835-114">Это означает, что в принципе любой из шаблонов, описанных в [выражениях Match](match-expressions.md) , можно использовать в списке параметров для функции или элемента.</span><span class="sxs-lookup"><span data-stu-id="c1835-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="c1835-115">Обычно методы используют форму кортежа передаваемых аргументов.</span><span class="sxs-lookup"><span data-stu-id="c1835-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="c1835-116">Это дает более четкий результат с точки зрения других языков .NET, поскольку форма кортежа соответствует способу передачи аргументов в методах .NET.</span><span class="sxs-lookup"><span data-stu-id="c1835-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="c1835-117">Каррированных формы чаще всего используются с функциями, созданными с помощью `let` привязок.</span><span class="sxs-lookup"><span data-stu-id="c1835-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="c1835-118">В следующем псевдокоде показаны примеры кортежа и каррированных аргумента.</span><span class="sxs-lookup"><span data-stu-id="c1835-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="c1835-119">Объединенные формы возможны, когда некоторые аргументы находятся в кортежах, а некоторые — нет.</span><span class="sxs-lookup"><span data-stu-id="c1835-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="c1835-120">Другие шаблоны также можно использовать в списках параметров, но если шаблон параметра не соответствует всем возможным входным данным, то во время выполнения может быть неполным совпадением.</span><span class="sxs-lookup"><span data-stu-id="c1835-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="c1835-121">Исключение `MatchFailureException` создается, когда значение аргумента не совпадает с шаблонами, указанными в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="c1835-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="c1835-122">Компилятор выдает предупреждение, если шаблон параметра допускает неполные соответствия.</span><span class="sxs-lookup"><span data-stu-id="c1835-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="c1835-123">По крайней мере один другой шаблон обычно полезен для списков параметров, и это шаблон с подстановочными знаками.</span><span class="sxs-lookup"><span data-stu-id="c1835-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="c1835-124">Шаблон подстановочного знака используется в списке параметров, если нужно просто игнорировать любые аргументы.</span><span class="sxs-lookup"><span data-stu-id="c1835-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="c1835-125">Следующий код иллюстрирует использование шаблона с подстановочными знаками в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="c1835-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="c1835-126">Шаблон подстановочного знака может быть полезен, если не нужны передаваемые аргументы, например, в главной точке входа в программу, если вы не заинтересованы в аргументах командной строки, которые обычно предоставляются в виде массива строк, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="c1835-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="c1835-127">Другие шаблоны, которые иногда используются в аргументах, являются `as` шаблоном и шаблонами идентификаторов, связанными с размеченные объединениями и активными шаблонами.</span><span class="sxs-lookup"><span data-stu-id="c1835-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="c1835-128">Шаблон размеченного объединения с одним вариантом можно использовать следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c1835-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="c1835-129">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c1835-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="c1835-130">Активные шаблоны могут быть полезны в качестве параметров, например при преобразовании аргумента в нужный формат, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c1835-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="c1835-131">Шаблон можно использовать `as` для сохранения совпадающего значения в качестве локального значения, как показано в следующей строке кода.</span><span class="sxs-lookup"><span data-stu-id="c1835-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="c1835-132">Другой шаблон, который используется иногда, — это функция, которая оставляет последний аргумент без имени, предоставляя в качестве тела функции лямбда-выражение, которое сразу же выполняет сопоставление шаблона с неявным аргументом.</span><span class="sxs-lookup"><span data-stu-id="c1835-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="c1835-133">Ниже приведен пример кода.</span><span class="sxs-lookup"><span data-stu-id="c1835-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="c1835-134">Этот код определяет функцию, которая принимает универсальный список и возвращает `true` значение, если список пуст, и `false` в противном случае.</span><span class="sxs-lookup"><span data-stu-id="c1835-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="c1835-135">Использование таких методов может сделать код более трудным для чтения.</span><span class="sxs-lookup"><span data-stu-id="c1835-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="c1835-136">Иногда шаблоны, использующие Неполные совпадения, полезны, например, если известно, что списки в программе содержат только три элемента, в списке параметров можно использовать такой шаблон, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="c1835-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="c1835-137">Использование шаблонов с неполными соответствиями лучше всего зарезервировано для быстрого создания прототипов и других временных применений.</span><span class="sxs-lookup"><span data-stu-id="c1835-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="c1835-138">Компилятор выдаст предупреждение для такого кода.</span><span class="sxs-lookup"><span data-stu-id="c1835-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="c1835-139">Такие шаблоны не могут охватывать все возможные входные данные и поэтому не подходят для API-интерфейсов компонентов.</span><span class="sxs-lookup"><span data-stu-id="c1835-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="c1835-140">Именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="c1835-140">Named Arguments</span></span>

<span data-ttu-id="c1835-141">Аргументы для методов могут быть заданы по положению в списке аргументов с разделителями-запятыми или могут быть переданы в метод явным образом путем указания имени, за которым следует знак равенства и значение, которое необходимо передать.</span><span class="sxs-lookup"><span data-stu-id="c1835-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="c1835-142">Если указано имя, оно может находиться в другом порядке, отличном от того, который используется в объявлении.</span><span class="sxs-lookup"><span data-stu-id="c1835-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="c1835-143">Именованные аргументы могут сделать код более удобочитаемым и более адаптируемым к определенным типам изменений в API, например изменить порядок параметров метода.</span><span class="sxs-lookup"><span data-stu-id="c1835-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="c1835-144">Именованные аргументы допускаются только для методов, а не для `let` функций, значений функций или лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="c1835-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="c1835-145">В следующем примере кода показано использование именованных аргументов.</span><span class="sxs-lookup"><span data-stu-id="c1835-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="c1835-146">При вызове конструктора класса можно задать значения свойств класса, используя синтаксис, аналогичный именованным аргументам.</span><span class="sxs-lookup"><span data-stu-id="c1835-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="c1835-147">Этот синтаксис показан в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c1835-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="c1835-148">Дополнительные сведения см. в разделе [конструкторы (F #)](members/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="c1835-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="c1835-149">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="c1835-149">Optional Parameters</span></span>

<span data-ttu-id="c1835-150">Для метода можно указать необязательный параметр, используя вопросительный знак перед именем параметра.</span><span class="sxs-lookup"><span data-stu-id="c1835-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="c1835-151">Необязательные параметры интерпретируется как тип параметра F #, поэтому их можно запросить обычным способом запроса типов параметров с помощью `match` выражения с `Some` и `None` .</span><span class="sxs-lookup"><span data-stu-id="c1835-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="c1835-152">Необязательные параметры разрешены только для членов, но не для функций, созданных с помощью `let` привязок.</span><span class="sxs-lookup"><span data-stu-id="c1835-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="c1835-153">Можно передать существующие необязательные значения методу по имени параметра, например `?arg=None` или `?arg=Some(3)` `?arg=arg` .</span><span class="sxs-lookup"><span data-stu-id="c1835-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="c1835-154">Это может быть полезно при создании метода, который передает необязательные аргументы другому методу.</span><span class="sxs-lookup"><span data-stu-id="c1835-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="c1835-155">Можно также использовать функцию `defaultArg` , которая задает значение по умолчанию для необязательного аргумента.</span><span class="sxs-lookup"><span data-stu-id="c1835-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="c1835-156">`defaultArg`Функция принимает необязательный параметр в качестве первого аргумента и значение по умолчанию в качестве второго.</span><span class="sxs-lookup"><span data-stu-id="c1835-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="c1835-157">В следующем примере показано использование необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="c1835-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="c1835-158">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c1835-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="c1835-159">В C# и Visual Basic Interop можно использовать атрибуты `[<Optional; DefaultParameterValue<(...)>]` в F #, чтобы вызывающие объекты могли видеть аргумент как необязательный.</span><span class="sxs-lookup"><span data-stu-id="c1835-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="c1835-160">Это эквивалентно определению аргумента в C# как необязательное, как в `MyMethod(int i = 3)` .</span><span class="sxs-lookup"><span data-stu-id="c1835-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn $"{message}"
```

<span data-ttu-id="c1835-161">Можно также указать новый объект в качестве значения параметра по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c1835-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="c1835-162">Например, `Foo` элемент может иметь необязательный `CancellationToken` Вход в качестве входа:</span><span class="sxs-lookup"><span data-stu-id="c1835-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn $"{ct}"
```

<span data-ttu-id="c1835-163">Значение, заданное в качестве аргумента, `DefaultParameterValue` должно соответствовать типу параметра.</span><span class="sxs-lookup"><span data-stu-id="c1835-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="c1835-164">Например, следующее не разрешено:</span><span class="sxs-lookup"><span data-stu-id="c1835-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="c1835-165">В этом случае компилятор выдает предупреждение и будет полностью игнорировать оба атрибута.</span><span class="sxs-lookup"><span data-stu-id="c1835-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="c1835-166">Обратите внимание, что значение по умолчанию `null` должно быть снабжено заметками типа, так как в противном случае компилятор выводит неверный тип, т. е. `[<Optional; DefaultParameterValue(null:obj)>] o:obj` .</span><span class="sxs-lookup"><span data-stu-id="c1835-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="c1835-167">Передача по ссылке</span><span class="sxs-lookup"><span data-stu-id="c1835-167">Passing by Reference</span></span>

<span data-ttu-id="c1835-168">Передача значения F # по ссылке включает в себя [ByRef](byrefs.md), которые являются типами управляемых указателей.</span><span class="sxs-lookup"><span data-stu-id="c1835-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="c1835-169">Ниже приведены рекомендации по использованию типа.</span><span class="sxs-lookup"><span data-stu-id="c1835-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="c1835-170">Используйте `inref<'T>` , если требуется только чтение указателя.</span><span class="sxs-lookup"><span data-stu-id="c1835-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="c1835-171">Используйте `outref<'T>` , если требуется только запись в указатель.</span><span class="sxs-lookup"><span data-stu-id="c1835-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="c1835-172">Используйте, `byref<'T>` Если требуется как чтение, так и запись в указатель.</span><span class="sxs-lookup"><span data-stu-id="c1835-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn $"It's %d{x}"

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn $"It's %d{x}"
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="c1835-173">Поскольку параметр является указателем и значение является изменяемым, любые изменения значения сохраняются после выполнения функции.</span><span class="sxs-lookup"><span data-stu-id="c1835-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="c1835-174">Можно использовать кортеж в качестве возвращаемого значения для хранения любых `out` параметров в методах библиотеки .NET.</span><span class="sxs-lookup"><span data-stu-id="c1835-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="c1835-175">Кроме того, параметр можно рассматривать `out` как `byref` параметр.</span><span class="sxs-lookup"><span data-stu-id="c1835-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="c1835-176">В следующем примере кода показаны оба способа.</span><span class="sxs-lookup"><span data-stu-id="c1835-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="c1835-177">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="c1835-177">Parameter Arrays</span></span>

<span data-ttu-id="c1835-178">Иногда необходимо определить функцию, которая принимает произвольное число параметров разнородного типа.</span><span class="sxs-lookup"><span data-stu-id="c1835-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="c1835-179">Было бы нецелесообразным создавать все возможные перегруженные методы для учета всех типов, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="c1835-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="c1835-180">Реализации .NET обеспечивают поддержку таких методов с помощью функции массива параметров.</span><span class="sxs-lookup"><span data-stu-id="c1835-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="c1835-181">Метод, принимающий в сигнатуру массив параметров, может предоставляться с произвольным числом параметров.</span><span class="sxs-lookup"><span data-stu-id="c1835-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="c1835-182">Параметры помещаются в массив.</span><span class="sxs-lookup"><span data-stu-id="c1835-182">The parameters are put into an array.</span></span> <span data-ttu-id="c1835-183">Тип элементов массива определяет типы параметров, которые могут быть переданы в функцию.</span><span class="sxs-lookup"><span data-stu-id="c1835-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="c1835-184">Если определить массив параметров с `System.Object` типом элемента, клиентский код может передавать значения любого типа.</span><span class="sxs-lookup"><span data-stu-id="c1835-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="c1835-185">В F # массивы параметров могут быть определены только в методах.</span><span class="sxs-lookup"><span data-stu-id="c1835-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="c1835-186">Их нельзя использовать в отдельных функциях или функциях, определенных в модулях.</span><span class="sxs-lookup"><span data-stu-id="c1835-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="c1835-187">Массив параметров определяется с помощью `ParamArray` атрибута.</span><span class="sxs-lookup"><span data-stu-id="c1835-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="c1835-188">`ParamArray`Атрибут может применяться только к последнему параметру.</span><span class="sxs-lookup"><span data-stu-id="c1835-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="c1835-189">В следующем коде показано, как вызвать метод .NET, который принимает массив параметров, и определение типа в F #, имеющее метод, принимающий массив параметров.</span><span class="sxs-lookup"><span data-stu-id="c1835-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="c1835-190">При запуске в проекте выходные данные предыдущего кода выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c1835-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="c1835-191">См. также</span><span class="sxs-lookup"><span data-stu-id="c1835-191">See also</span></span>

- [<span data-ttu-id="c1835-192">Члены</span><span class="sxs-lookup"><span data-stu-id="c1835-192">Members</span></span>](./members/index.md)
