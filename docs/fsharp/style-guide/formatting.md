---
title: Рекомендации по форматированию кода F#
description: 'Ознакомьтесь с рекомендациями по форматированию кода F #.'
ms.date: 08/31/2020
ms.openlocfilehash: 7e20c76f4cfafa50a15b6501a498b228b526057e
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513072"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="129ed-103">Рекомендации по форматированию кода F#</span><span class="sxs-lookup"><span data-stu-id="129ed-103">F# code formatting guidelines</span></span>

<span data-ttu-id="129ed-104">В этой статье содержатся рекомендации по форматированию кода, чтобы код F # был следующим:</span><span class="sxs-lookup"><span data-stu-id="129ed-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="129ed-105">Более разборчиво</span><span class="sxs-lookup"><span data-stu-id="129ed-105">More legible</span></span>
* <span data-ttu-id="129ed-106">В соответствии с соглашениями, применяемыми средствами форматирования в Visual Studio и другими редакторами</span><span class="sxs-lookup"><span data-stu-id="129ed-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="129ed-107">Аналогично другому коду в Интернете</span><span class="sxs-lookup"><span data-stu-id="129ed-107">Similar to other code online</span></span>

<span data-ttu-id="129ed-108">Эти рекомендации основаны на [подробном руководстве по форматированию F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) с помощью [АНХ-dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="129ed-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="129ed-109">Общие правила для отступов</span><span class="sxs-lookup"><span data-stu-id="129ed-109">General rules for indentation</span></span>

<span data-ttu-id="129ed-110">По умолчанию F # использует значащие пробелы.</span><span class="sxs-lookup"><span data-stu-id="129ed-110">F# uses significant white space by default.</span></span> <span data-ttu-id="129ed-111">Следующие рекомендации предназначены для указания того, как решать некоторые проблемы, которые могут накладываться.</span><span class="sxs-lookup"><span data-stu-id="129ed-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="129ed-112">Использование пробелов</span><span class="sxs-lookup"><span data-stu-id="129ed-112">Using spaces</span></span>

<span data-ttu-id="129ed-113">Если требуется отступ, необходимо использовать пробелы, а не символы табуляции.</span><span class="sxs-lookup"><span data-stu-id="129ed-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="129ed-114">Требуется по крайней мере один пробел.</span><span class="sxs-lookup"><span data-stu-id="129ed-114">At least one space is required.</span></span> <span data-ttu-id="129ed-115">Ваша организация может создавать стандарты кодирования для указания количества пробелов, используемых для отступов; два, три или четыре пространства отступов на каждом уровне, где происходит отступ, является типичным.</span><span class="sxs-lookup"><span data-stu-id="129ed-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="129ed-116">**Мы рекомендуем использовать четыре пробела для отступа.**</span><span class="sxs-lookup"><span data-stu-id="129ed-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="129ed-117">С другой стороны, отступы программ являются субъективным вопросом.</span><span class="sxs-lookup"><span data-stu-id="129ed-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="129ed-118">Варианты — ОК, но первым правилом, которое следует следовать, является *согласованность отступов*.</span><span class="sxs-lookup"><span data-stu-id="129ed-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="129ed-119">Выберите общепринятый стиль отступов и используйте его систематически во всей базе кода.</span><span class="sxs-lookup"><span data-stu-id="129ed-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="129ed-120">Форматирование пробелов</span><span class="sxs-lookup"><span data-stu-id="129ed-120">Formatting white space</span></span>

<span data-ttu-id="129ed-121">В F # учитывается пробел.</span><span class="sxs-lookup"><span data-stu-id="129ed-121">F# is white space sensitive.</span></span> <span data-ttu-id="129ed-122">Хотя большая семантика из пустого пространства охватывается правильным отступом, необходимо учитывать некоторые другие моменты.</span><span class="sxs-lookup"><span data-stu-id="129ed-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="129ed-123">Операторы форматирования в арифметических выражениях</span><span class="sxs-lookup"><span data-stu-id="129ed-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="129ed-124">Всегда используйте пробелы вокруг двоичных арифметических выражений:</span><span class="sxs-lookup"><span data-stu-id="129ed-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="129ed-125">За унарными `-` операторами всегда должно следовать значение, которое они инвертирует:</span><span class="sxs-lookup"><span data-stu-id="129ed-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="129ed-126">Добавление символа пробела после `-` оператора может привести к путанице для других.</span><span class="sxs-lookup"><span data-stu-id="129ed-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="129ed-127">В целом, важно всегда:</span><span class="sxs-lookup"><span data-stu-id="129ed-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="129ed-128">Заключить бинарные операторы в пробелы</span><span class="sxs-lookup"><span data-stu-id="129ed-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="129ed-129">Никогда не иметь конечных пробелов после унарного оператора</span><span class="sxs-lookup"><span data-stu-id="129ed-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="129ed-130">Особенно важна рекомендация бинарных арифметических операторов.</span><span class="sxs-lookup"><span data-stu-id="129ed-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="129ed-131">Если не заключить бинарный `-` оператор в сочетание с определенными вариантами форматирования, может привести к интерпретации его как унарного `-` .</span><span class="sxs-lookup"><span data-stu-id="129ed-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="129ed-132">Заключить определение пользовательского оператора с помощью пробела</span><span class="sxs-lookup"><span data-stu-id="129ed-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="129ed-133">Всегда используйте пробелы, чтобы заключить определение оператора:</span><span class="sxs-lookup"><span data-stu-id="129ed-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="129ed-134">Для любого пользовательского оператора, начинающегося с `*` и имеющего более одного символа, необходимо добавить пробел в начало определения, чтобы избежать неоднозначности компилятора.</span><span class="sxs-lookup"><span data-stu-id="129ed-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="129ed-135">Поэтому рекомендуется просто заключить определения всех операторов в один символ пробела.</span><span class="sxs-lookup"><span data-stu-id="129ed-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="129ed-136">Стрелки параметров вокруг функции с пробелами</span><span class="sxs-lookup"><span data-stu-id="129ed-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="129ed-137">При определении сигнатуры функции используйте пробел вокруг `->` символа:</span><span class="sxs-lookup"><span data-stu-id="129ed-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="129ed-138">Аргументы функции вокруг пробелов</span><span class="sxs-lookup"><span data-stu-id="129ed-138">Surround function arguments with white space</span></span>

<span data-ttu-id="129ed-139">При определении функции следует использовать пробел вокруг каждого аргумента.</span><span class="sxs-lookup"><span data-stu-id="129ed-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="avoid-name-sensitive-alignments"></a><span data-ttu-id="129ed-140">Избегайте выравнивания с учетом имени</span><span class="sxs-lookup"><span data-stu-id="129ed-140">Avoid name-sensitive alignments</span></span>

<span data-ttu-id="129ed-141">Как правило, следует искать, чтобы избежать отступов и выравнивания, которые чувствительны к именованию:</span><span class="sxs-lookup"><span data-stu-id="129ed-141">In general, seek to avoid indentation and alignment that is sensitive to naming:</span></span>

```fsharp
// OK
let myLongValueName =
    someExpression
    |> anotherExpression


// Bad
let myLongValueName = someExpression
                      |> anotherExpression
```

<span data-ttu-id="129ed-142">Иногда это называется «выравниванием именного» или «именного отступами».</span><span class="sxs-lookup"><span data-stu-id="129ed-142">This is sometimes called “vanity alignment” or “vanity indentation”.</span></span> <span data-ttu-id="129ed-143">Основные причины, по которым следует избегать этого:</span><span class="sxs-lookup"><span data-stu-id="129ed-143">The primary reasons for avoiding this are:</span></span>

* <span data-ttu-id="129ed-144">Важный код перемещается на дальнее право</span><span class="sxs-lookup"><span data-stu-id="129ed-144">Important code is moved far to the right</span></span>
* <span data-ttu-id="129ed-145">Для фактического кода осталось меньше ширины.</span><span class="sxs-lookup"><span data-stu-id="129ed-145">There is less width left for the actual code</span></span>
* <span data-ttu-id="129ed-146">Переименование может привести к нарушению выравнивания</span><span class="sxs-lookup"><span data-stu-id="129ed-146">Renaming can break the alignment</span></span>

<span data-ttu-id="129ed-147">Сделайте то же самое для, `do` / `do!` чтобы обеспечить соответствие отступов `let` / `let!` .</span><span class="sxs-lookup"><span data-stu-id="129ed-147">Do the same for `do`/`do!` in order to keep the indentation consistent with `let`/`let!`.</span></span> <span data-ttu-id="129ed-148">Ниже приведен пример использования `do` в классе:</span><span class="sxs-lookup"><span data-stu-id="129ed-148">Here is an example using `do` in a class:</span></span>

```fsharp
// OK
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog

// Bad - notice the "do" expression is indented one space less than the `let` expression
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do fooBarBaz
       |> loremIpsumDolorSitAmet
       |> theQuickBrownFoxJumpedOverTheLazyDog
```

<span data-ttu-id="129ed-149">Ниже приведен пример `do!` использования двух пробелов (из-за отсутствия `do!` различий между подходами при использовании 4 пробелов):</span><span class="sxs-lookup"><span data-stu-id="129ed-149">Here is an example with `do!` using 2 spaces of indentation (because with `do!` there is coincidentally no difference between the approaches when using 4 spaces of indentation):</span></span>

```fsharp
// OK
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do!
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
}

// Bad - notice the "do!" expression is indented two spaces more than the `let!` expression
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do! fooBarBaz
      |> loremIpsumDolorSitAmet
      |> theQuickBrownFoxJumpedOverTheLazyDog
}
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a><span data-ttu-id="129ed-150">Размещение параметров в новой строке для длинных определений</span><span class="sxs-lookup"><span data-stu-id="129ed-150">Place parameters on a new line for long definitions</span></span>

<span data-ttu-id="129ed-151">При наличии длинного определения функции разместите параметры на новых строках и установите отступы в соответствии с уровнем отступа последующего параметра.</span><span class="sxs-lookup"><span data-stu-id="129ed-151">If you have a long function definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
module M =
    let LongFunctionWithLotsOfParameters
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method follows
```

<span data-ttu-id="129ed-152">Это также относится к элементам, конструкторам и параметрам с помощью кортежей:</span><span class="sxs-lookup"><span data-stu-id="129ed-152">This also applies to members, constructors, and parameters using tuples:</span></span>

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method

type TC
    (
        aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse
    ) =
    // ... the body of the class follows
```

<span data-ttu-id="129ed-153">Если параметры куррифиед или есть явная аннотация типа возвращаемого значения, предпочтительнее поместить `=` символ в новую строку:</span><span class="sxs-lookup"><span data-stu-id="129ed-153">If the parameters are currified or there's an explicit return type annotation, it is preferable to place the `=` character on a new line:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) : AReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method
```

<span data-ttu-id="129ed-154">Это способ избежать слишком длинных строк (в случае, если тип возвращаемого значения может иметь длинное имя) и при добавлении параметров будет меньше повреждений строк.</span><span class="sxs-lookup"><span data-stu-id="129ed-154">This is a way to avoid too long lines (in case return type might have long name) and have less line-damage when adding parameters.</span></span>

### <a name="type-annotations"></a><span data-ttu-id="129ed-155">Аннотации типов</span><span class="sxs-lookup"><span data-stu-id="129ed-155">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="129ed-156">Заметки о типе аргумента функции в правой панели</span><span class="sxs-lookup"><span data-stu-id="129ed-156">Right-pad function argument type annotations</span></span>

<span data-ttu-id="129ed-157">При определении аргументов с заметками типа используйте пробел после `:` символа:</span><span class="sxs-lookup"><span data-stu-id="129ed-157">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="129ed-158">Заметка возвращаемого типа вокруг пробелов</span><span class="sxs-lookup"><span data-stu-id="129ed-158">Surround return type annotations with white space</span></span>

<span data-ttu-id="129ed-159">В заметке функции, привязанной к let, или типе значения (возвращаемый тип в случае функции) используйте пробелы до и после `:` символа:</span><span class="sxs-lookup"><span data-stu-id="129ed-159">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="129ed-160">Форматирование пустых строк</span><span class="sxs-lookup"><span data-stu-id="129ed-160">Formatting blank lines</span></span>

* <span data-ttu-id="129ed-161">Отдельные определения функций и классов верхнего уровня с двумя пустыми строками.</span><span class="sxs-lookup"><span data-stu-id="129ed-161">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="129ed-162">Определения методов внутри класса разделяются одной пустой строкой.</span><span class="sxs-lookup"><span data-stu-id="129ed-162">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="129ed-163">Для разделения групп связанных функций можно использовать дополнительные пустые строки (с осторожностью).</span><span class="sxs-lookup"><span data-stu-id="129ed-163">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="129ed-164">Пустые строки могут быть опущены между несколькими строками с одной строкой (например, набором фиктивных реализаций).</span><span class="sxs-lookup"><span data-stu-id="129ed-164">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="129ed-165">Для обозначения логических разделов используйте в функциях пустые строки.</span><span class="sxs-lookup"><span data-stu-id="129ed-165">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="129ed-166">Форматирование комментариев</span><span class="sxs-lookup"><span data-stu-id="129ed-166">Formatting comments</span></span>

<span data-ttu-id="129ed-167">Обычно в качестве комментариев блока в стиле ML предпочтительно несколько комментариев с двойной косой чертой.</span><span class="sxs-lookup"><span data-stu-id="129ed-167">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="129ed-168">Встроенные комментарии должны заменять первую букву прописной.</span><span class="sxs-lookup"><span data-stu-id="129ed-168">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="129ed-169">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="129ed-169">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="129ed-170">Использование camelCase для привязанных к классам значений и функций</span><span class="sxs-lookup"><span data-stu-id="129ed-170">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="129ed-171">Общий и принятый в стиле F # подход к использованию camelCase для всех имен, привязанных как локальные переменные или в соответствии с шаблонами и определениями функций.</span><span class="sxs-lookup"><span data-stu-id="129ed-171">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="129ed-172">Локально привязанные функции в классах также должны использовать camelCase.</span><span class="sxs-lookup"><span data-stu-id="129ed-172">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="129ed-173">Использование camelCase для открытых функций, привязанных к модулю</span><span class="sxs-lookup"><span data-stu-id="129ed-173">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="129ed-174">Если функция, привязанная к модулю, является частью общедоступного API, она должна использовать camelCase:</span><span class="sxs-lookup"><span data-stu-id="129ed-174">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="129ed-175">Использовать camelCase для внутренних и частных привязанных к модулю значений и функций</span><span class="sxs-lookup"><span data-stu-id="129ed-175">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="129ed-176">Используйте camelCase для частных значений, привязанных к модулю, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="129ed-176">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="129ed-177">Специальные функции в скриптах</span><span class="sxs-lookup"><span data-stu-id="129ed-177">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="129ed-178">Значения, составляющие внутреннюю реализацию модуля или типа</span><span class="sxs-lookup"><span data-stu-id="129ed-178">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="129ed-179">Использование camelCase для параметров</span><span class="sxs-lookup"><span data-stu-id="129ed-179">Use camelCase for parameters</span></span>

<span data-ttu-id="129ed-180">Все параметры должны использовать camelCase в соответствии с соглашениями об именовании .NET.</span><span class="sxs-lookup"><span data-stu-id="129ed-180">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="129ed-181">Использование PascalCase для модулей</span><span class="sxs-lookup"><span data-stu-id="129ed-181">Use PascalCase for modules</span></span>

<span data-ttu-id="129ed-182">Все модули (верхний, внутренний, частный, вложенный) должны использовать PascalCase.</span><span class="sxs-lookup"><span data-stu-id="129ed-182">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="129ed-183">Использование PascalCase для объявлений типов, элементов и меток</span><span class="sxs-lookup"><span data-stu-id="129ed-183">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="129ed-184">Классы, интерфейсы, структуры, перечисления, делегаты, записи и размеченные объединения должны иметь имена с PascalCase.</span><span class="sxs-lookup"><span data-stu-id="129ed-184">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="129ed-185">Элементы в типах и метках для записей и размеченных объединений должны также использовать PascalCase.</span><span class="sxs-lookup"><span data-stu-id="129ed-185">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="129ed-186">Использование PascalCase для конструкций, встроенных в .NET</span><span class="sxs-lookup"><span data-stu-id="129ed-186">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="129ed-187">Пространства имен, исключения, события и имена проектов и `.dll` имен также должны использовать PascalCase.</span><span class="sxs-lookup"><span data-stu-id="129ed-187">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="129ed-188">Это не только делает использование других языков .NET более естественным для потребителей, но также согласуется с соглашениями об именовании .NET, которые, скорее всего, встречаются.</span><span class="sxs-lookup"><span data-stu-id="129ed-188">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="129ed-189">Не используйте знаки подчеркивания в именах</span><span class="sxs-lookup"><span data-stu-id="129ed-189">Avoid underscores in names</span></span>

<span data-ttu-id="129ed-190">Исторически некоторые библиотеки F # использовали в именах символы подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="129ed-190">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="129ed-191">Однако он больше не принимается частично, поскольку он противоречит соглашениям об именовании .NET.</span><span class="sxs-lookup"><span data-stu-id="129ed-191">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="129ed-192">С другой стороны, некоторые программисты F # часто используют подчеркивания, частично по историческим причинам, а чувствительность и уважение важны.</span><span class="sxs-lookup"><span data-stu-id="129ed-192">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="129ed-193">Тем не менее, стиль часто отличается от других, которые имеют возможность выбрать, следует ли использовать его.</span><span class="sxs-lookup"><span data-stu-id="129ed-193">However, the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="129ed-194">Одно исключение включает взаимодействие с собственными компонентами, в которых подчеркивания являются общими.</span><span class="sxs-lookup"><span data-stu-id="129ed-194">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="129ed-195">Использовать стандартные операторы F #</span><span class="sxs-lookup"><span data-stu-id="129ed-195">Use standard F# operators</span></span>

<span data-ttu-id="129ed-196">Следующие операторы определены в стандартной библиотеке F # и должны использоваться вместо определения эквивалентов.</span><span class="sxs-lookup"><span data-stu-id="129ed-196">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="129ed-197">Рекомендуется использовать эти операторы, так как он, как правило, делает код более читаемым и идиоматическим.</span><span class="sxs-lookup"><span data-stu-id="129ed-197">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="129ed-198">Разработчики с фоном в OCaml или другом языке функционального программирования могут прилагаться к различным идиомам.</span><span class="sxs-lookup"><span data-stu-id="129ed-198">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="129ed-199">В следующем списке перечислены рекомендуемые операторы F #.</span><span class="sxs-lookup"><span data-stu-id="129ed-199">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="129ed-200">Использовать префиксный синтаксис для универсальных типов ( `Foo<T>` ) в качестве предпочтений для постфиксного синтаксиса ( `T Foo` )</span><span class="sxs-lookup"><span data-stu-id="129ed-200">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="129ed-201">F # наследует постфиксный стиль именования универсальных типов (например,), `int list` а также стиль префикса .NET (например, `list<int>` ).</span><span class="sxs-lookup"><span data-stu-id="129ed-201">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="129ed-202">Предпочитать стиль .NET, за исключением пяти конкретных типов:</span><span class="sxs-lookup"><span data-stu-id="129ed-202">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="129ed-203">Для списков F # используйте постфиксную форму: `int list` вместо `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="129ed-203">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="129ed-204">Для параметров F # используйте постфиксную форму: `int option` вместо `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="129ed-204">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="129ed-205">Для параметров значения F # используйте постфиксную форму: `int voption` , а не `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="129ed-205">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="129ed-206">Для массивов F # используйте синтаксические имена, `int[]` а не `int array` или `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="129ed-206">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="129ed-207">Для ссылочных ячеек используйте `int ref` вместо `ref<int>` или `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="129ed-207">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="129ed-208">Для всех остальных типов используйте форму префикса.</span><span class="sxs-lookup"><span data-stu-id="129ed-208">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="129ed-209">Форматирование кортежей</span><span class="sxs-lookup"><span data-stu-id="129ed-209">Formatting tuples</span></span>

<span data-ttu-id="129ed-210">Создание экземпляра кортежа должно быть заключено в круглые скобки, за которыми следует одиночный пробел, например: `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="129ed-210">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="129ed-211">Обычно можно опустить круглые скобки в шаблоне, сопоставленном с кортежами:</span><span class="sxs-lookup"><span data-stu-id="129ed-211">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="129ed-212">Также обычно можно опустить круглые скобки, если кортеж является возвращаемым значением функции:</span><span class="sxs-lookup"><span data-stu-id="129ed-212">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="129ed-213">В заключение следует предпочесть создание экземпляров кортежей в круглых скобках, но при использовании кортежей для сопоставления шаблонов или возвращаемого значения оно считается точным, чтобы избежать круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="129ed-213">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="129ed-214">Форматирование объявлений размеченного объединения</span><span class="sxs-lookup"><span data-stu-id="129ed-214">Formatting discriminated union declarations</span></span>

<span data-ttu-id="129ed-215">Отступ `|` в определении типа по четырем пробелам:</span><span class="sxs-lookup"><span data-stu-id="129ed-215">Indent `|` in type definition by four spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="129ed-216">Форматирование размеченных объединений</span><span class="sxs-lookup"><span data-stu-id="129ed-216">Formatting discriminated unions</span></span>

<span data-ttu-id="129ed-217">Экземпляры с различенными объединениями, разделенными по нескольким строкам, должны предоставлять новой области с отступами следующие данные.</span><span class="sxs-lookup"><span data-stu-id="129ed-217">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="129ed-218">Закрывающая круглая скобка также может находиться на новой строке:</span><span class="sxs-lookup"><span data-stu-id="129ed-218">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="129ed-219">Форматирование объявлений записей</span><span class="sxs-lookup"><span data-stu-id="129ed-219">Formatting record declarations</span></span>

<span data-ttu-id="129ed-220">`{`Создайте отступ в определении типа на четыре пробела и начните список полей в той же строке:</span><span class="sxs-lookup"><span data-stu-id="129ed-220">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="129ed-221">Помещение открывающего маркера в новую строку и закрывающий маркер в новой строке предпочтительнее, если объявить реализации интерфейса или элементы в записи:</span><span class="sxs-lookup"><span data-stu-id="129ed-221">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="129ed-222">Форматирование записей</span><span class="sxs-lookup"><span data-stu-id="129ed-222">Formatting records</span></span>

<span data-ttu-id="129ed-223">Короткие записи можно записать в одной строке:</span><span class="sxs-lookup"><span data-stu-id="129ed-223">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="129ed-224">Записи, которые больше не должны использовать новые строки для меток:</span><span class="sxs-lookup"><span data-stu-id="129ed-224">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="129ed-225">Размещение открывающего маркера на новой строке, содержимое, вкладка над одной областью, и закрывающий маркер в новой строке предпочтительнее, если вы:</span><span class="sxs-lookup"><span data-stu-id="129ed-225">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="129ed-226">Перемещение записей в коде с разными областями отступов</span><span class="sxs-lookup"><span data-stu-id="129ed-226">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="129ed-227">Передача их в функцию</span><span class="sxs-lookup"><span data-stu-id="129ed-227">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="129ed-228">Для списка и элементов массива применяются те же правила.</span><span class="sxs-lookup"><span data-stu-id="129ed-228">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="129ed-229">Форматирование выражений записи копирования и обновления</span><span class="sxs-lookup"><span data-stu-id="129ed-229">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="129ed-230">Выражение записи копирования и обновления по-прежнему является записью, поэтому применяются аналогичные рекомендации.</span><span class="sxs-lookup"><span data-stu-id="129ed-230">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="129ed-231">Короткие выражения могут помещаться в одну строку:</span><span class="sxs-lookup"><span data-stu-id="129ed-231">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="129ed-232">В более длинных выражениях должны использоваться новые строки:</span><span class="sxs-lookup"><span data-stu-id="129ed-232">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="129ed-233">Как и в руководстве по записям, может потребоваться выделить отдельные строки для фигурных скобок и задать отступ для одной области справа с помощью выражения.</span><span class="sxs-lookup"><span data-stu-id="129ed-233">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="129ed-234">В некоторых особых случаях, например при переносе значения с необязательными скобками, может потребоваться разместить фигурную скобку в одной строке:</span><span class="sxs-lookup"><span data-stu-id="129ed-234">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { Foo: S option }

let state = { Foo = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            Foo =
                Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="129ed-235">Форматирование списков и массивов</span><span class="sxs-lookup"><span data-stu-id="129ed-235">Formatting lists and arrays</span></span>

<span data-ttu-id="129ed-236">Напишите `x :: l` с пробелами вокруг `::` оператора ( `::` является оператором инфиксные, таким образом заключенным в пробелы).</span><span class="sxs-lookup"><span data-stu-id="129ed-236">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="129ed-237">Список и массивы, объявленные в одной строке, должны содержать пробел после открывающей скобки и перед закрывающей скобкой:</span><span class="sxs-lookup"><span data-stu-id="129ed-237">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="129ed-238">Всегда используйте хотя бы один пробел между двумя различными операторами, похожими на фигурные скобки.</span><span class="sxs-lookup"><span data-stu-id="129ed-238">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="129ed-239">Например, оставьте пробел между `[` и `{` .</span><span class="sxs-lookup"><span data-stu-id="129ed-239">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="129ed-240">Одно и то же правило применимо к спискам или массивам кортежей.</span><span class="sxs-lookup"><span data-stu-id="129ed-240">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="129ed-241">Списки и массивы, разделенные по нескольким строкам, следуют тому же правилу, что и записи:</span><span class="sxs-lookup"><span data-stu-id="129ed-241">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="129ed-242">И, как и в случае с записями, объявление открывающих и закрывающих квадратных скобок в собственной строке сделает код более простым и походит к функциям.</span><span class="sxs-lookup"><span data-stu-id="129ed-242">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="129ed-243">При создании массивов и списков программным способом предпочтительнее, `->` `do ... yield` когда всегда создается значение:</span><span class="sxs-lookup"><span data-stu-id="129ed-243">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="129ed-244">Более старые версии языка F # требовали указания `yield` в ситуациях, когда данные могут создаваться условно, или для вычисления последовательных выражений.</span><span class="sxs-lookup"><span data-stu-id="129ed-244">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="129ed-245">Рекомендуется опустить эти `yield` Ключевые слова, если не требуется компиляция с использованием более старой версии языка F #:</span><span class="sxs-lookup"><span data-stu-id="129ed-245">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="129ed-246">В некоторых случаях `do...yield` может помочь в удобочитаемости.</span><span class="sxs-lookup"><span data-stu-id="129ed-246">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="129ed-247">В этих случаях следует учитывать субъективные ситуации.</span><span class="sxs-lookup"><span data-stu-id="129ed-247">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="129ed-248">Форматирование выражений if</span><span class="sxs-lookup"><span data-stu-id="129ed-248">Formatting if expressions</span></span>

<span data-ttu-id="129ed-249">Отступы условий зависят от размера и сложности выражений, которые их составляют.</span><span class="sxs-lookup"><span data-stu-id="129ed-249">Indentation of conditionals depends on the size and complexity of the expressions that make them up.</span></span>
<span data-ttu-id="129ed-250">Запишите их на одной строке, когда:</span><span class="sxs-lookup"><span data-stu-id="129ed-250">Write them on one line when:</span></span>

- <span data-ttu-id="129ed-251">`cond`, `e1` и `e2` являются короткими</span><span class="sxs-lookup"><span data-stu-id="129ed-251">`cond`, `e1`, and `e2` are short</span></span>
- <span data-ttu-id="129ed-252">`e1` и `e2` не являются `if/then/else` самими выражениями.</span><span class="sxs-lookup"><span data-stu-id="129ed-252">`e1` and `e2` are not `if/then/else` expressions themselves.</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="129ed-253">Если любое из выражений является многострочным или `if/then/else` выражением.</span><span class="sxs-lookup"><span data-stu-id="129ed-253">If any of the expressions are multi-line or `if/then/else` expressions.</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="129ed-254">Несколько условий с `elif` и `else` располагаются с отступом в той же области, что и `if` при соблюдении правил из выражений одной строки `if/then/else` .</span><span class="sxs-lookup"><span data-stu-id="129ed-254">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if` when they follow the rules of the one line `if/then/else` expressions.</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

<span data-ttu-id="129ed-255">Если любое из условий или выражений является многострочным, все `if/then/else` выражение будет иметь несколько строк:</span><span class="sxs-lookup"><span data-stu-id="129ed-255">If any of the conditions or expressions is multi-line, the entire `if/then/else` expression is multi-line:</span></span>

```fsharp
if cond1 then
    e1
elif cond2 then
    e2
elif cond3 then
    e3
else
    e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="129ed-256">Конструкции сопоставления шаблонов</span><span class="sxs-lookup"><span data-stu-id="129ed-256">Pattern matching constructs</span></span>

<span data-ttu-id="129ed-257">Используйте `|` предложение for each совпадения без отступов.</span><span class="sxs-lookup"><span data-stu-id="129ed-257">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="129ed-258">Если выражение является коротким, можно использовать одну строку, если каждая часть выражения также является простой.</span><span class="sxs-lookup"><span data-stu-id="129ed-258">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="129ed-259">Если выражение справа от стрелки сопоставления шаблонов слишком велико, переместите его в следующую строку с отступом на один шаг из `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="129ed-259">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="129ed-260">Сопоставление шаблонов анонимных функций, начиная от `function` , не должно быть слишком большим.</span><span class="sxs-lookup"><span data-stu-id="129ed-260">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="129ed-261">Например, чтобы задать отступ для одной области, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="129ed-261">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="129ed-262">Сопоставление шаблонов в функциях `let` , определенных или `let rec` , должно начинаться с отступа в четыре пробела после начала `let` , даже если `function` используется ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="129ed-262">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="129ed-263">Не рекомендуется выровняйте стрелки.</span><span class="sxs-lookup"><span data-stu-id="129ed-263">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="129ed-264">Форматирование выражений try и with</span><span class="sxs-lookup"><span data-stu-id="129ed-264">Formatting try/with expressions</span></span>

<span data-ttu-id="129ed-265">Сопоставление шаблонов для типа исключения должно иметь отступ на том же уровне, что и `with` .</span><span class="sxs-lookup"><span data-stu-id="129ed-265">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="129ed-266">Приложение параметров функции форматирования</span><span class="sxs-lookup"><span data-stu-id="129ed-266">Formatting function parameter application</span></span>

<span data-ttu-id="129ed-267">Как правило, большинство параметров функции выполняются в одной строке.</span><span class="sxs-lookup"><span data-stu-id="129ed-267">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="129ed-268">Если вы хотите применить параметры к функции в новой строке, понизить их до одной области.</span><span class="sxs-lookup"><span data-stu-id="129ed-268">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="129ed-269">Те же рекомендации применяются для лямбда-выражений в качестве аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="129ed-269">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="129ed-270">Если тело лямбда-выражения, текст может иметь другую строку, с отступом на одну область</span><span class="sxs-lookup"><span data-stu-id="129ed-270">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn $"%d{a + elem}")
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn $"%d{a + elem}")
        list1
```

<span data-ttu-id="129ed-271">Однако если тело лямбда-выражения является более одной строкой, рекомендуется разбить его на отдельную функцию, а не использовать многострочную конструкцию, применяемую в качестве одного аргумента для функции.</span><span class="sxs-lookup"><span data-stu-id="129ed-271">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="129ed-272">Форматирование операторов инфиксные</span><span class="sxs-lookup"><span data-stu-id="129ed-272">Formatting infix operators</span></span>

<span data-ttu-id="129ed-273">Разделяйте операторы по пробелам.</span><span class="sxs-lookup"><span data-stu-id="129ed-273">Separate operators by spaces.</span></span> <span data-ttu-id="129ed-274">Очевидными исключениями из этого правила `!` являются `.` операторы и.</span><span class="sxs-lookup"><span data-stu-id="129ed-274">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="129ed-275">Выражения инфиксные являются допустимыми для сопоставления по одному и тому же столбцу:</span><span class="sxs-lookup"><span data-stu-id="129ed-275">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators-or-mutable-assignments"></a><span data-ttu-id="129ed-276">Форматирование операторов конвейера или изменяемых назначений</span><span class="sxs-lookup"><span data-stu-id="129ed-276">Formatting pipeline operators or mutable assignments</span></span>

<span data-ttu-id="129ed-277">Операторы конвейера `|>` должны идти под выражениями, над которыми они работают.</span><span class="sxs-lookup"><span data-stu-id="129ed-277">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat

// Not OK either
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat
```

<span data-ttu-id="129ed-278">Это также относится к изменяемым методам задания:</span><span class="sxs-lookup"><span data-stu-id="129ed-278">This also applies to mutable setters:</span></span>

```fsharp
// Preferred approach
ctx.Response.Headers.[HeaderNames.ContentType] <-
    Constants.jsonApiMediaType |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <-
    bytes.Length |> string |> StringValues

// Not OK
ctx.Response.Headers.[HeaderNames.ContentType] <- Constants.jsonApiMediaType
                                                  |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <- bytes.Length
                                                    |> string
                                                    |> StringValues
```

### <a name="formatting-modules"></a><span data-ttu-id="129ed-279">Модули форматирования</span><span class="sxs-lookup"><span data-stu-id="129ed-279">Formatting modules</span></span>

<span data-ttu-id="129ed-280">Код в локальном модуле должен иметь отступ относительно модуля, но код в модуле верхнего уровня не должен иметь отступы.</span><span class="sxs-lookup"><span data-stu-id="129ed-280">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="129ed-281">Элементы пространства имен не обязательно должны иметь отступы.</span><span class="sxs-lookup"><span data-stu-id="129ed-281">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="129ed-282">Форматирование выражений и интерфейсов объекта</span><span class="sxs-lookup"><span data-stu-id="129ed-282">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="129ed-283">Выражения объектов и интерфейсы должны быть выровнены так же, как и с `member` отступом после четырех пробелов.</span><span class="sxs-lookup"><span data-stu-id="129ed-283">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="129ed-284">Форматирование пробелов в выражениях</span><span class="sxs-lookup"><span data-stu-id="129ed-284">Formatting white space in expressions</span></span>

<span data-ttu-id="129ed-285">Избегайте излишнего пробела в выражениях F #.</span><span class="sxs-lookup"><span data-stu-id="129ed-285">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="129ed-286">Именованные аргументы также не должны содержать пробелы, окружающие `=` :</span><span class="sxs-lookup"><span data-stu-id="129ed-286">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a><span data-ttu-id="129ed-287">Конструкторы форматирования, статические члены и вызовы элементов</span><span class="sxs-lookup"><span data-stu-id="129ed-287">Formatting constructors, static members, and member invocations</span></span>

<span data-ttu-id="129ed-288">Если выражение является коротким, разделяйте аргументы пробелами и оставляйте их в одной строке.</span><span class="sxs-lookup"><span data-stu-id="129ed-288">If the expression is short, separate arguments with spaces and keep it in one line.</span></span>

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

<span data-ttu-id="129ed-289">Если выражение является длинным, используйте символы новой строки и отступа для одной области, а не отступа до квадратной скобки.</span><span class="sxs-lookup"><span data-stu-id="129ed-289">If the expression is long, use newlines and indent one scope, rather than indenting to the bracket.</span></span>

```fsharp
let person =
    new Person(
        argument1,
        argument2
    )

let myRegexMatch =
    Regex.Match(
        "my longer input string with some interesting content in it",
        "myRegexPattern"
    )

let untypedRes =
    checker.ParseFile(
        fileName,
        sourceText,
        parsingOptionsWithDefines
    )
```

## <a name="formatting-attributes"></a><span data-ttu-id="129ed-290">Атрибуты форматирования</span><span class="sxs-lookup"><span data-stu-id="129ed-290">Formatting attributes</span></span>

<span data-ttu-id="129ed-291">[Атрибуты](../language-reference/attributes.md) помещаются над конструкцией:</span><span class="sxs-lookup"><span data-stu-id="129ed-291">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="129ed-292">Они должны идти после любой XML-документации:</span><span class="sxs-lookup"><span data-stu-id="129ed-292">They should go after any XML documentation:</span></span>

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="129ed-293">Атрибуты форматирования для параметров</span><span class="sxs-lookup"><span data-stu-id="129ed-293">Formatting attributes on parameters</span></span>

<span data-ttu-id="129ed-294">Атрибуты также могут быть помещены в параметры.</span><span class="sxs-lookup"><span data-stu-id="129ed-294">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="129ed-295">В этом случае поместите его в ту же строку, что и параметр, и перед именем:</span><span class="sxs-lookup"><span data-stu-id="129ed-295">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="129ed-296">Форматирование нескольких атрибутов</span><span class="sxs-lookup"><span data-stu-id="129ed-296">Formatting multiple attributes</span></span>

<span data-ttu-id="129ed-297">Если к конструкции, которая не является параметром, применяется несколько атрибутов, их следует размещать таким образом, чтобы в каждой строке был один атрибут:</span><span class="sxs-lookup"><span data-stu-id="129ed-297">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="129ed-298">При применении к параметру они должны находиться в той же строке и разделяться `;` разделителем.</span><span class="sxs-lookup"><span data-stu-id="129ed-298">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="129ed-299">Литералы форматирования</span><span class="sxs-lookup"><span data-stu-id="129ed-299">Formatting literals</span></span>

<span data-ttu-id="129ed-300">[Литералы F #](../language-reference/literals.md) , использующие `Literal` атрибут, должны располагать атрибут в собственной строке и использовать PascalCase именование:</span><span class="sxs-lookup"><span data-stu-id="129ed-300">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="129ed-301">Старайтесь не размещать атрибут в той же строке, что и значение.</span><span class="sxs-lookup"><span data-stu-id="129ed-301">Avoid placing the attribute on the same line as the value.</span></span>

## <a name="formatting-computation-expression-operations"></a><span data-ttu-id="129ed-302">Форматирование операций вычисления выражения</span><span class="sxs-lookup"><span data-stu-id="129ed-302">Formatting computation expression operations</span></span>

<span data-ttu-id="129ed-303">При создании пользовательских операций для [вычислительных выражений](../language-reference/computation-expressions.md)рекомендуется использовать camelCase именование:</span><span class="sxs-lookup"><span data-stu-id="129ed-303">When creating custom operations for [computation expressions](../language-reference/computation-expressions.md), it is recommended to use camelCase naming:</span></span>

```fsharp
type MathBuilder () =
    member _.Yield _ = 0

    [<CustomOperation("addOne")>]
    member _.AddOne (state: int) =
        state + 1

    [<CustomOperation("subtractOne")>]
    member _.SubtractOne (state: int) =
        state - 1

    [<CustomOperation("divideBy")>]
    member _.DivideBy (state: int, divisor: int) =
        state / divisor

    [<CustomOperation("multiplyBy")>]
    member _.MultiplyBy (state: int, factor: int) =
        state * factor

let math = MathBuilder()

// 10
let myNumber =
    math {
        addOne
        addOne
        addOne

        subtractOne

        divideBy 2

        multiplyBy 10
    }
```

<span data-ttu-id="129ed-304">Домен, для которого моделируется моделирование, должен в конечном итоге обменяться соглашением об именовании.</span><span class="sxs-lookup"><span data-stu-id="129ed-304">The domain that's being modeled should ultimately drive the naming convention.</span></span>
<span data-ttu-id="129ed-305">Если идиоматическим использовать другое соглашение, вместо него следует использовать это соглашение.</span><span class="sxs-lookup"><span data-stu-id="129ed-305">If it is idiomatic to use a different convention, that convention should be used instead.</span></span>
