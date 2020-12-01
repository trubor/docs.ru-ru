---
title: 'Новые возможности в F # 5,0-F # Guide'
description: 'Ознакомьтесь с обзором новых функций, доступных в F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: dd954fac31b008beab37cd6c1f06b1d41c5d5004
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438004"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="2f72b-103">Новые возможности F# 5.0</span><span class="sxs-lookup"><span data-stu-id="2f72b-103">What's new in F# 5.0</span></span>

<span data-ttu-id="2f72b-104">В f # 5,0 добавлено несколько улучшений языка F # и F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="2f72b-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="2f72b-105">Он выпущен с **.NET 5**.</span><span class="sxs-lookup"><span data-stu-id="2f72b-105">It is released with **.NET 5**.</span></span>

<span data-ttu-id="2f72b-106">Вы можете скачать последний пакет SDK для .NET на странице [скачиваемых файлов .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="2f72b-106">You can download the latest .NET SDK from the [.NET downloads page](https://dotnet.microsoft.com/download).</span></span>

## <a name="get-started"></a><span data-ttu-id="2f72b-107">Начало работы</span><span class="sxs-lookup"><span data-stu-id="2f72b-107">Get started</span></span>

<span data-ttu-id="2f72b-108">F # 5,0 доступен во всех дистрибутивах .NET Core и средствах Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f72b-108">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="2f72b-109">Дополнительные сведения см. в статье [Приступая к работе с F #](../get-started/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2f72b-109">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="2f72b-110">Ссылки на пакеты в скриптах F #</span><span class="sxs-lookup"><span data-stu-id="2f72b-110">Package references in F# scripts</span></span>

<span data-ttu-id="2f72b-111">F # 5 предоставляет поддержку ссылок на пакеты в скриптах F # с `#r "nuget:..."` синтаксисом.</span><span class="sxs-lookup"><span data-stu-id="2f72b-111">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="2f72b-112">Например, рассмотрим следующую ссылку на пакет:</span><span class="sxs-lookup"><span data-stu-id="2f72b-112">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

<span data-ttu-id="2f72b-113">Можно также указать явную версию после имени пакета следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2f72b-113">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="2f72b-114">Ссылки на пакет поддерживают пакеты с собственными зависимостями, например ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2f72b-114">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="2f72b-115">Ссылки на пакет также поддерживают пакеты с особыми требованиями к ссылкам, зависимым от `.dll` s.</span><span class="sxs-lookup"><span data-stu-id="2f72b-115">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="2f72b-116">Например, пакет [фпарсек](https://www.nuget.org/packages/FParsec/) , используемый, чтобы пользователи вручную гарантированно ссылались на зависимый объект, `FParsecCS.dll` прежде чем `FParsec.dll` был указан в F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="2f72b-116">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="2f72b-117">Это больше не требуется, и вы можете ссылаться на пакет следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2f72b-117">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

<span data-ttu-id="2f72b-118">Эта функция реализует [F # Tools RFC ФСТ-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-118">This feature implements [F# Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span></span> <span data-ttu-id="2f72b-119">Дополнительные сведения о ссылках на пакеты см. в руководстве по [F# Interactive](../tools/fsharp-interactive/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2f72b-119">For more information on package references, see the [F# Interactive](../tools/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="2f72b-120">Интерполяция строк</span><span class="sxs-lookup"><span data-stu-id="2f72b-120">String interpolation</span></span>

<span data-ttu-id="2f72b-121">Строки с интерполяцией F # очень похожи на строки с интерполяцией C# или JavaScript, в том, что они позволяют писать код в "отверстиях" внутри строкового литерала.</span><span class="sxs-lookup"><span data-stu-id="2f72b-121">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="2f72b-122">Простой пример:</span><span class="sxs-lookup"><span data-stu-id="2f72b-122">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="2f72b-123">Однако строки с интерполяцией F # также позволяют использовать типизированные интерполяции, как и `sprintf` функцию, чтобы обеспечить соответствие выражения в контексте с интерполяцией конкретному типу.</span><span class="sxs-lookup"><span data-stu-id="2f72b-123">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="2f72b-124">В нем используются те же описатели формата.</span><span class="sxs-lookup"><span data-stu-id="2f72b-124">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="2f72b-125">В приведенном выше примере интерполяции объект `%s` требует, чтобы интерполяция была типа `string` , тогда как для параметра `%d` требуется интерполяция `integer` .</span><span class="sxs-lookup"><span data-stu-id="2f72b-125">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="2f72b-126">Кроме того, любое произвольное выражение F # (или выражения) может быть помещено в сторону контекста интерполяции.</span><span class="sxs-lookup"><span data-stu-id="2f72b-126">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="2f72b-127">Даже можно написать более сложное выражение, например так:</span><span class="sxs-lookup"><span data-stu-id="2f72b-127">It is even possible to write a more complicated expression, like so:</span></span>

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

<span data-ttu-id="2f72b-128">Хотя мы не рекомендуем делать это слишком много на практике.</span><span class="sxs-lookup"><span data-stu-id="2f72b-128">Although we don't recommend doing this too much in practice.</span></span>

<span data-ttu-id="2f72b-129">Эта функция реализует [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-129">This feature implements [F# RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="2f72b-130">Поддержка NameOf</span><span class="sxs-lookup"><span data-stu-id="2f72b-130">Support for nameof</span></span>

<span data-ttu-id="2f72b-131">F # 5 поддерживает `nameof` оператор, который разрешает символ, который он использует, и создает его имя в источнике f #.</span><span class="sxs-lookup"><span data-stu-id="2f72b-131">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="2f72b-132">Это полезно в различных сценариях, таких как ведение журнала, и защита ведения журнала от изменений в исходном коде.</span><span class="sxs-lookup"><span data-stu-id="2f72b-132">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="2f72b-133">В последней строке будет выдано исключение, а в сообщении об ошибке появится сообщение "month" (месяц).</span><span class="sxs-lookup"><span data-stu-id="2f72b-133">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="2f72b-134">Вы можете задействовать почти каждую конструкцию F #:</span><span class="sxs-lookup"><span data-stu-id="2f72b-134">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

<span data-ttu-id="2f72b-135">Три последних дополнения — это изменения в работе операторов: Добавление `nameof<'type-parameter>` формы для параметров универсального типа и возможность использования в `nameof` качестве шаблона в выражении соответствия шаблону.</span><span class="sxs-lookup"><span data-stu-id="2f72b-135">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="2f72b-136">Если присвоить имя оператору, он получает его исходную строку.</span><span class="sxs-lookup"><span data-stu-id="2f72b-136">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="2f72b-137">Если требуется скомпилированная форма, используйте скомпилированное имя оператора:</span><span class="sxs-lookup"><span data-stu-id="2f72b-137">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="2f72b-138">Для получения имени параметра типа требуется немного другой синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2f72b-138">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="2f72b-139">Это похоже на `typeof<'T>` `typedefof<'T>` операторы и.</span><span class="sxs-lookup"><span data-stu-id="2f72b-139">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="2f72b-140">В F # 5 также добавлена поддержка `nameof` шаблона, который можно использовать в `match` выражениях:</span><span class="sxs-lookup"><span data-stu-id="2f72b-140">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

<span data-ttu-id="2f72b-141">Приведенный выше код использует "NameOf" вместо строкового литерала в выражении match.</span><span class="sxs-lookup"><span data-stu-id="2f72b-141">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

<span data-ttu-id="2f72b-142">Эта функция реализует [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-142">This feature implements [F# RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="2f72b-143">Открытые объявления типов</span><span class="sxs-lookup"><span data-stu-id="2f72b-143">Open type declarations</span></span>

<span data-ttu-id="2f72b-144">В F # 5 также добавлена поддержка объявлений открытых типов.</span><span class="sxs-lookup"><span data-stu-id="2f72b-144">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="2f72b-145">Объявление открытого типа аналогично открытию статического класса в C#, за исключением некоторого другого синтаксиса и немного другого поведения в соответствии с семантикой F #.</span><span class="sxs-lookup"><span data-stu-id="2f72b-145">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="2f72b-146">С помощью объявлений открытых типов можно использовать `open` любой тип для предоставления статического содержимого внутри него.</span><span class="sxs-lookup"><span data-stu-id="2f72b-146">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="2f72b-147">Кроме того, вы можете `open` определить объединения и записи F #, чтобы предоставить их содержимое.</span><span class="sxs-lookup"><span data-stu-id="2f72b-147">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="2f72b-148">Например, это может быть полезно, если имеется объединение, определенное в модуле и требующее доступа к его случаям, но не нужно открывать весь модуль.</span><span class="sxs-lookup"><span data-stu-id="2f72b-148">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

<span data-ttu-id="2f72b-149">В отличие от C#, при использовании `open type` двух типов, предоставляющих член с тем же именем, элемент из последнего типа `open` ED скрывает другое имя.</span><span class="sxs-lookup"><span data-stu-id="2f72b-149">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="2f72b-150">Это согласуется с семантикой языка F # вокруг уже существующей теневой копии.</span><span class="sxs-lookup"><span data-stu-id="2f72b-150">This is consistent with F# semantics around shadowing that exist already.</span></span>

<span data-ttu-id="2f72b-151">Эта функция реализует [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-151">This feature implements [F# RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="2f72b-152">Единообразное поведение при выполнении срезов для встроенных типов данных</span><span class="sxs-lookup"><span data-stu-id="2f72b-152">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="2f72b-153">Поведение для создания среза встроенных `FSharp.Core` типов данных (массив, список, строка, 2D-массив, трехмерный массив, массив 4d), которые использовались для несоответствия до F # 5.</span><span class="sxs-lookup"><span data-stu-id="2f72b-153">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="2f72b-154">В некоторых случаях происходит исключение, но некоторые из них не были бы.</span><span class="sxs-lookup"><span data-stu-id="2f72b-154">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="2f72b-155">В F # 5 все встроенные типы теперь возвращают пустые срезы для срезов, которые невозможно создать:</span><span class="sxs-lookup"><span data-stu-id="2f72b-155">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="2f72b-156">Эта функция реализует [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-156">This feature implements [F# RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="2f72b-157">Срезы фиксированного индекса для трехмерных и 4D-массивов в FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="2f72b-157">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="2f72b-158">F # 5,0 предоставляет поддержку среза с фиксированным индексом во встроенных типах массивов 3D и 4D.</span><span class="sxs-lookup"><span data-stu-id="2f72b-158">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="2f72b-159">Чтобы проиллюстрировать это, рассмотрим следующий трехмерный массив:</span><span class="sxs-lookup"><span data-stu-id="2f72b-159">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="2f72b-160">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="2f72b-160">*z = 0*</span></span>
| <span data-ttu-id="2f72b-161">кс\и</span><span class="sxs-lookup"><span data-stu-id="2f72b-161">x\y</span></span>   | <span data-ttu-id="2f72b-162">0</span><span class="sxs-lookup"><span data-stu-id="2f72b-162">0</span></span> | <span data-ttu-id="2f72b-163">1</span><span class="sxs-lookup"><span data-stu-id="2f72b-163">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2f72b-164">**0**</span><span class="sxs-lookup"><span data-stu-id="2f72b-164">**0**</span></span> | <span data-ttu-id="2f72b-165">0</span><span class="sxs-lookup"><span data-stu-id="2f72b-165">0</span></span> | <span data-ttu-id="2f72b-166">1</span><span class="sxs-lookup"><span data-stu-id="2f72b-166">1</span></span> |
| <span data-ttu-id="2f72b-167">**1**</span><span class="sxs-lookup"><span data-stu-id="2f72b-167">**1**</span></span> | <span data-ttu-id="2f72b-168">2</span><span class="sxs-lookup"><span data-stu-id="2f72b-168">2</span></span> | <span data-ttu-id="2f72b-169">3</span><span class="sxs-lookup"><span data-stu-id="2f72b-169">3</span></span> |

<span data-ttu-id="2f72b-170">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="2f72b-170">*z = 1*</span></span>
| <span data-ttu-id="2f72b-171">кс\и</span><span class="sxs-lookup"><span data-stu-id="2f72b-171">x\y</span></span>   | <span data-ttu-id="2f72b-172">0</span><span class="sxs-lookup"><span data-stu-id="2f72b-172">0</span></span> | <span data-ttu-id="2f72b-173">1</span><span class="sxs-lookup"><span data-stu-id="2f72b-173">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2f72b-174">**0**</span><span class="sxs-lookup"><span data-stu-id="2f72b-174">**0**</span></span> | <span data-ttu-id="2f72b-175">4</span><span class="sxs-lookup"><span data-stu-id="2f72b-175">4</span></span> | <span data-ttu-id="2f72b-176">5</span><span class="sxs-lookup"><span data-stu-id="2f72b-176">5</span></span> |
| <span data-ttu-id="2f72b-177">**1**</span><span class="sxs-lookup"><span data-stu-id="2f72b-177">**1**</span></span> | <span data-ttu-id="2f72b-178">6</span><span class="sxs-lookup"><span data-stu-id="2f72b-178">6</span></span> | <span data-ttu-id="2f72b-179">7</span><span class="sxs-lookup"><span data-stu-id="2f72b-179">7</span></span> |

<span data-ttu-id="2f72b-180">Что делать, если вы хотите извлечь срез `[| 4; 5 |]` из массива?</span><span class="sxs-lookup"><span data-stu-id="2f72b-180">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="2f72b-181">Теперь это очень просто!</span><span class="sxs-lookup"><span data-stu-id="2f72b-181">This is now very simple!</span></span>

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

<span data-ttu-id="2f72b-182">Эта функция реализует [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-182">This feature implements [F# RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span></span>

## <a name="f-quotations-improvements"></a><span data-ttu-id="2f72b-183">Усовершенствования в кавычках F #</span><span class="sxs-lookup"><span data-stu-id="2f72b-183">F# quotations improvements</span></span>

<span data-ttu-id="2f72b-184">[Цитаты кода](../language-reference/code-quotations.md) F # теперь имеют возможность хранить сведения об ограничениях типов.</span><span class="sxs-lookup"><span data-stu-id="2f72b-184">F# [code quotations](../language-reference/code-quotations.md) now have the ability to retain type constraint information.</span></span> <span data-ttu-id="2f72b-185">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="2f72b-185">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="2f72b-186">Ограничение, созданное `inline` функцией, сохраняется в цитате кода.</span><span class="sxs-lookup"><span data-stu-id="2f72b-186">The constraint generated by the `inline` function is retained in the code quotation.</span></span> <span data-ttu-id="2f72b-187">`negate`Теперь можно вычислить форму с кавычками для функции.</span><span class="sxs-lookup"><span data-stu-id="2f72b-187">The `negate` function's quoted form can now be evaluated.</span></span>

<span data-ttu-id="2f72b-188">Эта функция реализует [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-188">This feature implements [F# RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span></span>

## <a name="applicative-computation-expressions"></a><span data-ttu-id="2f72b-189">Выражения вычисления аппликативе</span><span class="sxs-lookup"><span data-stu-id="2f72b-189">Applicative Computation Expressions</span></span>

<span data-ttu-id="2f72b-190">[Выражения вычислений (CEs)](../language-reference/computation-expressions.md) используются сегодня для моделирования "контекстных вычислений" или более функциональной терминологии, понятной программированию, готовых вычислений.</span><span class="sxs-lookup"><span data-stu-id="2f72b-190">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming-friendly terminology, monadic computations.</span></span>

<span data-ttu-id="2f72b-191">В F # 5 появился аппликативе CEs, предлагающий другую вычислительную модель.</span><span class="sxs-lookup"><span data-stu-id="2f72b-191">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="2f72b-192">Аппликативе CEs обеспечивает более эффективные вычисления при условии, что каждое вычисление является независимым, и результаты накоплены в конце.</span><span class="sxs-lookup"><span data-stu-id="2f72b-192">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="2f72b-193">Если вычисления не зависят друг от друга, они также просты в параллелизуемые, что позволяет авторам CE создавать более эффективные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="2f72b-193">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="2f72b-194">Это преимущество обусловлено ограничением. Однако вычисления, зависящие от ранее вычисленных значений, не допускаются.</span><span class="sxs-lookup"><span data-stu-id="2f72b-194">This benefit comes at a restriction, though: computations that depend on previously computed values are not allowed.</span></span>

<span data-ttu-id="2f72b-195">В следующем примере показана базовая аппликативе CE для `Result` типа.</span><span class="sxs-lookup"><span data-stu-id="2f72b-195">The follow example shows a basic applicative CE for the `Result` type.</span></span>

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="2f72b-196">Если вы являетесь автором библиотеки, который в настоящее время предоставляет CEs в своей библиотеке, необходимо учитывать некоторые дополнительные соображения.</span><span class="sxs-lookup"><span data-stu-id="2f72b-196">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

<span data-ttu-id="2f72b-197">Эта функция реализует [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-197">This feature implements [F# RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span></span>

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a><span data-ttu-id="2f72b-198">Интерфейсы могут быть реализованы в разных универсальных экземплярах</span><span class="sxs-lookup"><span data-stu-id="2f72b-198">Interfaces can be implemented at different generic instantiations</span></span>

<span data-ttu-id="2f72b-199">Теперь можно реализовать тот же интерфейс в различных универсальных экземплярах:</span><span class="sxs-lookup"><span data-stu-id="2f72b-199">You can now implement the same interface at different generic instantiations:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

<span data-ttu-id="2f72b-200">Эта функция реализует [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-200">This feature implements [F# RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span></span>

## <a name="default-interface-member-consumption"></a><span data-ttu-id="2f72b-201">Использование элементов интерфейса по умолчанию</span><span class="sxs-lookup"><span data-stu-id="2f72b-201">Default interface member consumption</span></span>

<span data-ttu-id="2f72b-202">F # 5 позволяет использовать [интерфейсы с реализациями по умолчанию](../../csharp/tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-202">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="2f72b-203">Рассмотрим интерфейс, определенный в C# следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2f72b-203">Consider an interface defined in C# like this:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="2f72b-204">Его можно использовать в F # с помощью любого из стандартных средств реализации интерфейса:</span><span class="sxs-lookup"><span data-stu-id="2f72b-204">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

<span data-ttu-id="2f72b-205">Это позволяет безопасно использовать преимущества кода C# и компонентов .NET, написанных на современном языке C#, когда они хотят, чтобы пользователи могли использовать реализацию по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2f72b-205">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

<span data-ttu-id="2f72b-206">Эта функция реализует [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-206">This feature implements [F# RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="2f72b-207">Упрощенное взаимодействие с типами значений, допускающими значение null</span><span class="sxs-lookup"><span data-stu-id="2f72b-207">Simplified interop with nullable value types</span></span>

<span data-ttu-id="2f72b-208">В F # поддерживаются [типы, допускающие значения NULL](https://docs.microsoft.com/dotnet/api/system.nullable-1) (которые также называются типами, допускающими значения NULL), но их взаимодействие с ними традиционно было довольно сложно, поскольку вам пришлось бы `Nullable` создавать `Nullable<SomeType>` обертку или каждый раз, когда нужно передать значение.</span><span class="sxs-lookup"><span data-stu-id="2f72b-208">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="2f72b-209">Теперь компилятор будет неявно преобразовывать тип значения в, `Nullable<ThatValueType>` Если целевой тип соответствует.</span><span class="sxs-lookup"><span data-stu-id="2f72b-209">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="2f72b-210">Теперь возможны следующие фрагменты кода:</span><span class="sxs-lookup"><span data-stu-id="2f72b-210">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

<span data-ttu-id="2f72b-211">Эта функция реализует [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-211">This feature implements [F# RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span></span>

## <a name="preview-reverse-indexes"></a><span data-ttu-id="2f72b-212">Предварительный просмотр: обратные индексы</span><span class="sxs-lookup"><span data-stu-id="2f72b-212">Preview: reverse indexes</span></span>

<span data-ttu-id="2f72b-213">В F # 5 также появился предварительный просмотр для разрешения обратных индексов.</span><span class="sxs-lookup"><span data-stu-id="2f72b-213">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="2f72b-214">Синтаксис: `^idx`.</span><span class="sxs-lookup"><span data-stu-id="2f72b-214">The syntax is `^idx`.</span></span> <span data-ttu-id="2f72b-215">Вот как можно получить значение элемента 1 из конца списка:</span><span class="sxs-lookup"><span data-stu-id="2f72b-215">Here's how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="2f72b-216">Кроме того, можно определить обратные индексы для собственных типов.</span><span class="sxs-lookup"><span data-stu-id="2f72b-216">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="2f72b-217">Для этого необходимо реализовать следующий метод:</span><span class="sxs-lookup"><span data-stu-id="2f72b-217">To do so, you'll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="2f72b-218">Ниже приведен пример для `Span<'T>` типа:</span><span class="sxs-lookup"><span data-stu-id="2f72b-218">Here's an example for the `Span<'T>` type:</span></span>

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

<span data-ttu-id="2f72b-219">Эта функция реализует [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-219">This feature implements [F# RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span></span>

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="2f72b-220">Предварительный просмотр: перегрузки пользовательских ключевых слов в вычислительных выражениях</span><span class="sxs-lookup"><span data-stu-id="2f72b-220">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="2f72b-221">Вычислительные выражения — это мощная функция для авторов библиотек и платформ.</span><span class="sxs-lookup"><span data-stu-id="2f72b-221">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="2f72b-222">Они позволяют значительно повысить выразительность компонентов, позволяя определять хорошо известные члены и формировать DSL для домена, в котором вы работаете.</span><span class="sxs-lookup"><span data-stu-id="2f72b-222">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="2f72b-223">В F # 5 добавлена поддержка предварительной версии для перегрузки пользовательских операций в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="2f72b-223">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="2f72b-224">Это позволяет написать и использовать следующий код:</span><span class="sxs-lookup"><span data-stu-id="2f72b-224">It allows the following code to be written and consumed:</span></span>

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

<span data-ttu-id="2f72b-225">До этого изменения можно было бы написать `InputBuilder` тип так, как он есть, но вы не смогли использовать его так, как он используется в примере.</span><span class="sxs-lookup"><span data-stu-id="2f72b-225">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="2f72b-226">Так как перегрузки, необязательные параметры и `System.ParamArray` типы Now разрешены, все работает так, как если бы оно было бы ожидаемым.</span><span class="sxs-lookup"><span data-stu-id="2f72b-226">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>

<span data-ttu-id="2f72b-227">Эта функция реализует [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span><span class="sxs-lookup"><span data-stu-id="2f72b-227">This feature implements [F# RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span></span>
