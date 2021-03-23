---
title: 'Новые возможности в F # 5,0-F # Guide'
description: 'Ознакомьтесь с обзором новых функций, доступных в F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: c686bcf5df18d24ac35bbafb2b2d90f768ef7947
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876712"
---
# <a name="whats-new-in-f-50"></a>Новые возможности F# 5.0

В f # 5,0 добавлено несколько улучшений языка F # и F# Interactive. Он выпущен с **.NET 5**.

Вы можете скачать последний пакет SDK для .NET на странице [скачиваемых файлов .NET](https://dotnet.microsoft.com/download).

## <a name="get-started"></a>Начало работы

F # 5,0 доступен во всех дистрибутивах .NET Core и средствах Visual Studio. Дополнительные сведения см. в статье [Приступая к работе с F #](../get-started/index.md) .

## <a name="package-references-in-f-scripts"></a>Ссылки на пакеты в скриптах F #

F # 5 предоставляет поддержку ссылок на пакеты в скриптах F # с `#r "nuget:..."` синтаксисом. Например, рассмотрим следующую ссылку на пакет:

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn $"{JsonConvert.SerializeObject o}"
```

Можно также указать явную версию после имени пакета следующим образом:

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

Ссылки на пакет поддерживают пакеты с собственными зависимостями, например ML.NET.

Ссылки на пакет также поддерживают пакеты с особыми требованиями к ссылкам, зависимым от `.dll` s. Например, пакет [фпарсек](https://www.nuget.org/packages/FParsec/) , используемый, чтобы пользователи вручную гарантированно ссылались на зависимый объект, `FParsecCS.dll` прежде чем `FParsec.dll` был указан в F# Interactive. Это больше не требуется, и вы можете ссылаться на пакет следующим образом:

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn $"Success: {result}"
    | Failure(errorMsg, _, _) -> printfn $"Failure: {errorMsg}"

test pfloat "1.234"
```

Эта функция реализует [F # Tools RFC ФСТ-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md). Дополнительные сведения о ссылках на пакеты см. в руководстве по [F# Interactive](../tools/fsharp-interactive/index.md) .

## <a name="string-interpolation"></a>Интерполяция строк

Строки с интерполяцией F # очень похожи на строки с интерполяцией C# или JavaScript, в том, что они позволяют писать код в "отверстиях" внутри строкового литерала. Простой пример:

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

Однако строки с интерполяцией F # также позволяют использовать типизированные интерполяции, как и `sprintf` функцию, чтобы обеспечить соответствие выражения в контексте с интерполяцией конкретному типу. В нем используются те же описатели формата.

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

В приведенном выше примере интерполяции объект `%s` требует, чтобы интерполяция была типа `string` , тогда как для параметра `%d` требуется интерполяция `integer` .

Кроме того, любое произвольное выражение F # (или выражения) может быть помещено в сторону контекста интерполяции. Даже можно написать более сложное выражение, например так:

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

Хотя мы не рекомендуем делать это слишком много на практике.

Эта функция реализует [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).

## <a name="support-for-nameof"></a>Поддержка NameOf

F # 5 поддерживает `nameof` оператор, который разрешает символ, который он использует, и создает его имя в источнике f #. Это полезно в различных сценариях, таких как ведение журнала, и защита ведения журнала от изменений в исходном коде.

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

printfn $"{lookupMonth 12}"
printfn $"{lookupMonth 1}"
printfn $"{lookupMonth 13}"
```

В последней строке будет выдано исключение, а в сообщении об ошибке появится сообщение "month" (месяц).

Вы можете задействовать почти каждую конструкцию F #:

```fsharp
module M =
    let f x = nameof x

printfn $"{M.f 12}"
printfn $"{nameof M}"
printfn $"{nameof M.f}"
```

Три последних дополнения — это изменения в работе операторов: Добавление `nameof<'type-parameter>` формы для параметров универсального типа и возможность использования в `nameof` качестве шаблона в выражении соответствия шаблону.

Если присвоить имя оператору, он получает его исходную строку. Если требуется скомпилированная форма, используйте скомпилированное имя оператора:

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

Для получения имени параметра типа требуется немного другой синтаксис:

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

Это похоже на `typeof<'T>` `typedefof<'T>` операторы и.

В F # 5 также добавлена поддержка `nameof` шаблона, который можно использовать в `match` выражениях:

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

Приведенный выше код использует "NameOf" вместо строкового литерала в выражении match.

Эта функция реализует [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).

## <a name="open-type-declarations"></a>Открытые объявления типов

В F # 5 также добавлена поддержка объявлений открытых типов. Объявление открытого типа аналогично открытию статического класса в C#, за исключением некоторого другого синтаксиса и немного другого поведения в соответствии с семантикой F #.

С помощью объявлений открытых типов можно использовать `open` любой тип для предоставления статического содержимого внутри него. Кроме того, вы можете `open` определить объединения и записи F #, чтобы предоставить их содержимое. Например, это может быть полезно, если имеется объединение, определенное в модуле и требующее доступа к его случаям, но не нужно открывать весь модуль.

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn $"{A}"
```

В отличие от C#, при использовании `open type` двух типов, предоставляющих член с тем же именем, элемент из последнего типа `open` ED скрывает другое имя. Это согласуется с семантикой языка F # вокруг уже существующей теневой копии.

Эта функция реализует [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>Единообразное поведение при выполнении срезов для встроенных типов данных

Поведение для создания среза встроенных `FSharp.Core` типов данных (массив, список, строка, 2D-массив, трехмерный массив, массив 4d), которые использовались для несоответствия до F # 5. В некоторых случаях происходит исключение, но некоторые из них не были бы. В F # 5 все встроенные типы теперь возвращают пустые срезы для срезов, которые невозможно создать:

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

Эта функция реализует [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>Срезы фиксированного индекса для трехмерных и 4D-массивов в FSharp. Core

F # 5,0 предоставляет поддержку среза с фиксированным индексом во встроенных типах массивов 3D и 4D.

Чтобы проиллюстрировать это, рассмотрим следующий трехмерный массив:

*z = 0*

| кс\и   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*

| кс\и   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Что делать, если вы хотите извлечь срез `[| 4; 5 |]` из массива? Теперь это очень просто!

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

Эта функция реализует [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).

## <a name="f-quotations-improvements"></a>Усовершенствования в кавычках F #

[Цитаты кода](../language-reference/code-quotations.md) F # теперь имеют возможность хранить сведения об ограничениях типов. Рассмотрим следующий пример.

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

Ограничение, созданное `inline` функцией, сохраняется в цитате кода. `negate`Теперь можно вычислить форму куотатед функции.

Эта функция реализует [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).

## <a name="applicative-computation-expressions"></a>Выражения вычисления аппликативе

[Выражения вычислений (CEs)](../language-reference/computation-expressions.md) используются сегодня для моделирования "контекстных вычислений" или более функциональной терминологии, понятной программированию, готовых вычислений.

В F # 5 появился аппликативе CEs, предлагающий другую вычислительную модель. Аппликативе CEs обеспечивает более эффективные вычисления при условии, что каждое вычисление является независимым, и результаты накоплены в конце. Если вычисления не зависят друг от друга, они также просты в параллелизуемые, что позволяет авторам CE создавать более эффективные библиотеки. Это преимущество обусловлено ограничением. Однако вычисления, зависящие от ранее вычисленных значений, не допускаются.

В следующем примере показана базовая аппликативе CE для `Result` типа.

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
    | Ok x -> printfn $"{nameof res1} is: %d{x}"
    | Error e -> printfn $"{nameof res1} is: {e}"

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

Если вы являетесь автором библиотеки, который в настоящее время предоставляет CEs в своей библиотеке, необходимо учитывать некоторые дополнительные соображения.

Эта функция реализует [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a>Интерфейсы могут быть реализованы в разных универсальных экземплярах

Теперь можно реализовать тот же интерфейс в различных универсальных экземплярах:

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

Эта функция реализует [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).

## <a name="default-interface-member-consumption"></a>Использование элементов интерфейса по умолчанию

F # 5 позволяет использовать [интерфейсы с реализациями по умолчанию](../../csharp/whats-new/tutorials/default-interface-methods-versions.md).

Рассмотрим интерфейс, определенный в C# следующим образом:

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

Его можно использовать в F # с помощью любого из стандартных средств реализации интерфейса:

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

Это позволяет безопасно использовать преимущества кода C# и компонентов .NET, написанных на современном языке C#, когда они хотят, чтобы пользователи могли использовать реализацию по умолчанию.

Эта функция реализует [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).

## <a name="simplified-interop-with-nullable-value-types"></a>Упрощенное взаимодействие с типами значений, допускающими значение null

В F # поддерживаются [типы, допускающие значения NULL](/dotnet/api/system.nullable-1) (которые также называются типами, допускающими значения NULL), но их взаимодействие с ними традиционно было довольно сложно, поскольку вам пришлось бы `Nullable` создавать `Nullable<SomeType>` обертку или каждый раз, когда нужно передать значение. Теперь компилятор будет неявно преобразовывать тип значения в, `Nullable<ThatValueType>` Если целевой тип соответствует. Теперь возможны следующие фрагменты кода:

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

Эта функция реализует [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).

## <a name="preview-reverse-indexes"></a>Предварительный просмотр: обратные индексы

В F # 5 также появился предварительный просмотр для разрешения обратных индексов. Синтаксис: `^idx`. Вот как можно получить значение элемента 1 из конца списка:

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

Кроме того, можно определить обратные индексы для собственных типов. Для этого необходимо реализовать следующий метод:

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

Ниже приведен пример для `Span<'T>` типа:

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
    printfn $"{arr}"

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

Эта функция реализует [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>Предварительный просмотр: перегрузки пользовательских ключевых слов в вычислительных выражениях

Вычислительные выражения — это мощная функция для авторов библиотек и платформ. Они позволяют значительно повысить выразительность компонентов, позволяя определять хорошо известные члены и формировать DSL для домена, в котором вы работаете.

В F # 5 добавлена поддержка предварительной версии для перегрузки пользовательских операций в вычислительных выражениях. Это позволяет написать и использовать следующий код:

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

До этого изменения можно было бы написать `InputBuilder` тип так, как он есть, но вы не смогли использовать его так, как он используется в примере. Так как перегрузки, необязательные параметры и `System.ParamArray` типы Now разрешены, все работает так, как если бы оно было бы ожидаемым.

Эта функция реализует [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).
