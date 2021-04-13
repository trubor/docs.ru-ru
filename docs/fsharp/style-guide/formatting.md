---
title: Рекомендации по форматированию кода F#
description: 'Ознакомьтесь с рекомендациями по форматированию кода F #.'
ms.date: 08/31/2020
ms.openlocfilehash: b8997a3cd854bd89e292e1090b5ebba3f7e6ae99
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255484"
---
# <a name="f-code-formatting-guidelines"></a>Рекомендации по форматированию кода F#

В этой статье содержатся рекомендации по форматированию кода, чтобы код F # был следующим:

* Более разборчиво
* В соответствии с соглашениями, применяемыми средствами форматирования в Visual Studio и другими редакторами
* Аналогично другому коду в Интернете

Эти рекомендации основаны на [подробном руководстве по форматированию F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) с помощью [АНХ-dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Общие правила для отступов

По умолчанию F # использует значащие пробелы. Следующие рекомендации предназначены для указания того, как решать некоторые проблемы, которые могут накладываться.

### <a name="using-spaces"></a>Использование пробелов

Если требуется отступ, необходимо использовать пробелы, а не символы табуляции. Требуется по крайней мере один пробел. Ваша организация может создавать стандарты кодирования для указания количества пробелов, используемых для отступов; два, три или четыре пространства отступов на каждом уровне, где происходит отступ, является типичным.

**Мы рекомендуем использовать четыре пробела для отступа.**

С другой стороны, отступы программ являются субъективным вопросом. Варианты — ОК, но первым правилом, которое следует следовать, является *согласованность отступов*. Выберите общепринятый стиль отступов и используйте его систематически во всей базе кода.

## <a name="formatting-white-space"></a>Форматирование пробелов

В F # учитывается пробел. Хотя большая семантика из пустого пространства охватывается правильным отступом, необходимо учитывать некоторые другие моменты.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Операторы форматирования в арифметических выражениях

Всегда используйте пробелы вокруг двоичных арифметических выражений:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

За унарными `-` операторами всегда должно следовать значение, которое они инвертирует:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Добавление символа пробела после `-` оператора может привести к путанице для других.

В целом, важно всегда:

* Заключить бинарные операторы в пробелы
* Никогда не иметь конечных пробелов после унарного оператора

Особенно важна рекомендация бинарных арифметических операторов. Если не заключить бинарный `-` оператор в сочетание с определенными вариантами форматирования, может привести к интерпретации его как унарного `-` .

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Заключить определение пользовательского оператора с помощью пробела

Всегда используйте пробелы, чтобы заключить определение оператора:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Для любого пользовательского оператора, начинающегося с `*` и имеющего более одного символа, необходимо добавить пробел в начало определения, чтобы избежать неоднозначности компилятора. Поэтому рекомендуется просто заключить определения всех операторов в один символ пробела.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Стрелки параметров вокруг функции с пробелами

При определении сигнатуры функции используйте пробел вокруг `->` символа:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Аргументы функции вокруг пробелов

При определении функции следует использовать пробел вокруг каждого аргумента.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="avoid-name-sensitive-alignments"></a>Избегайте выравнивания с учетом имени

Как правило, следует искать, чтобы избежать отступов и выравнивания, которые чувствительны к именованию:

```fsharp
// OK
let myLongValueName =
    someExpression
    |> anotherExpression


// Bad
let myLongValueName = someExpression
                      |> anotherExpression
```

Иногда это называется «выравниванием именного» или «именного отступами». Основные причины, по которым следует избегать этого:

* Важный код перемещается на дальнее право
* Для фактического кода осталось меньше ширины.
* Переименование может привести к нарушению выравнивания

Сделайте то же самое для, `do` / `do!` чтобы обеспечить соответствие отступов `let` / `let!` . Ниже приведен пример использования `do` в классе:

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

Ниже приведен пример `do!` использования двух пробелов (из-за отсутствия `do!` различий между подходами при использовании 4 пробелов):

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

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a>Размещение параметров в новой строке для длинных определений

При наличии длинного определения функции разместите параметры на новых строках и установите отступы в соответствии с уровнем отступа последующего параметра.

```fsharp
module M =
    let longFunctionWithLotsOfParameters
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method follows

    let longFunctionWithLotsOfParametersAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameter
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameterAndReturnType
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) : ReturnType =
        // ... the body of the method follows
```

Это также относится к элементам, конструкторам и параметрам с помощью кортежей:

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

Если параметры являются куррифиед, поместите `=` символ вместе с любым типом возвращаемого значения в новой строке:

```fsharp
type C() =
    member _.LongMethodWithLotsOfCurrifiedParamsAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method
```

Это способ избежать слишком длинных строк (в случае, если тип возвращаемого значения может иметь длинное имя) и при добавлении параметров будет меньше повреждений строк.

### <a name="type-annotations"></a>Аннотации типов

#### <a name="right-pad-function-argument-type-annotations"></a>Заметки о типе аргумента функции в правой панели

При определении аргументов с заметками типа используйте пробел после `:` символа:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Заметка возвращаемого типа вокруг пробелов

В заметке функции, привязанной к let, или типе значения (возвращаемый тип в случае функции) используйте пробелы до и после `:` символа:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

### <a name="formatting-bindings"></a>Привязки форматирования

Во всех случаях правая часть привязки либо все находятся в одной строке, либо (если она слишком длинная) переходит на новую строку с отступом в одну область.

Например, следующие действия не соответствуют требованиям:

```fsharp
let a = """
foobar, long string
"""

type File =
    member this.SaveAsync(path: string) : Async<unit> = async {
        // IO operation
        return ()
    }

let c = {
    Name = "Bilbo"
    Age = 111
    Region = "The Shire"
}

let d = while f do
    printfn "%A" x
```

Следующие совместимые:

```fsharp
let a =
    """
foobar, long string
"""

type File =
    member this.SaveAsync(path: string) : Async<unit> =
        async {
            // IO operation
            return ()
        }

let c =
    { Name = "Bilbo"
      Age = 111
      Region = "The Shire" }

let d =
    while f do
        printfn "%A" x
```

## <a name="formatting-blank-lines"></a>Форматирование пустых строк

* Отдельные определения функций и классов верхнего уровня с двумя пустыми строками.
* Определения методов внутри класса разделяются одной пустой строкой.
* Для разделения групп связанных функций можно использовать дополнительные пустые строки (с осторожностью). Пустые строки могут быть опущены между несколькими строками с одной строкой (например, набором фиктивных реализаций).
* Для обозначения логических разделов используйте в функциях пустые строки.

## <a name="formatting-comments"></a>Форматирование комментариев

Обычно в качестве комментариев блока в стиле ML предпочтительно несколько комментариев с двойной косой чертой.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Встроенные комментарии должны заменять первую букву прописной.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="formatting-string-literals-and-interpolated-strings"></a>Форматирование строковых литералов и интерполяции строк

Строковые литералы и интерполяция строк можно оставить только в одной строке, независимо от того, насколько длинна строка.

```fsharp
let serviceStorageConnection =
    $"DefaultEndpointsProtocol=https;AccountName=%s{serviceStorageAccount.Name};AccountKey=%s{serviceStorageAccountKey.Value}"
```

Многострочные интерполяции выражений настоятельно не рекомендуются. Вместо этого привяжите результат выражения к значению и используйте его в строке с интерполяцией.

## <a name="naming-conventions"></a>Соглашения об именах

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Использование camelCase для привязанных к классам значений и функций

Общий и принятый в стиле F # подход к использованию camelCase для всех имен, привязанных как локальные переменные или в соответствии с шаблонами и определениями функций.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Локально привязанные функции в классах также должны использовать camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Использование camelCase для открытых функций, привязанных к модулю

Если функция, привязанная к модулю, является частью общедоступного API, она должна использовать camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Использовать camelCase для внутренних и частных привязанных к модулю значений и функций

Используйте camelCase для частных значений, привязанных к модулю, включая следующие:

* Специальные функции в скриптах

* Значения, составляющие внутреннюю реализацию модуля или типа

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Использование camelCase для параметров

Все параметры должны использовать camelCase в соответствии с соглашениями об именовании .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Использование PascalCase для модулей

Все модули (верхний, внутренний, частный, вложенный) должны использовать PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Использование PascalCase для объявлений типов, элементов и меток

Классы, интерфейсы, структуры, перечисления, делегаты, записи и размеченные объединения должны иметь имена с PascalCase. Элементы в типах и метках для записей и размеченных объединений должны также использовать PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Использование PascalCase для конструкций, встроенных в .NET

Пространства имен, исключения, события и имена проектов и `.dll` имен также должны использовать PascalCase. Это не только делает использование других языков .NET более естественным для потребителей, но также согласуется с соглашениями об именовании .NET, которые, скорее всего, встречаются.

### <a name="avoid-underscores-in-names"></a>Не используйте знаки подчеркивания в именах

Исторически некоторые библиотеки F # использовали в именах символы подчеркивания. Однако он больше не принимается частично, поскольку он противоречит соглашениям об именовании .NET. С другой стороны, некоторые программисты F # часто используют подчеркивания, частично по историческим причинам, а чувствительность и уважение важны. Тем не менее, стиль часто отличается от других, которые имеют возможность выбрать, следует ли использовать его.

Одно исключение включает взаимодействие с собственными компонентами, в которых подчеркивания являются общими.

### <a name="use-standard-f-operators"></a>Использовать стандартные операторы F #

Следующие операторы определены в стандартной библиотеке F # и должны использоваться вместо определения эквивалентов. Рекомендуется использовать эти операторы, так как он, как правило, делает код более читаемым и идиоматическим. Разработчики с фоном в OCaml или другом языке функционального программирования могут прилагаться к различным идиомам. В следующем списке перечислены рекомендуемые операторы F #.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Использовать префиксный синтаксис для универсальных типов ( `Foo<T>` ) в качестве предпочтений для постфиксного синтаксиса ( `T Foo` )

F # наследует постфиксный стиль именования универсальных типов (например,), `int list` а также стиль префикса .NET (например, `list<int>` ). Предпочитать стиль .NET, за исключением пяти конкретных типов:

1. Для списков F # используйте постфиксную форму: `int list` вместо `list<int>` .
2. Для параметров F # используйте постфиксную форму: `int option` вместо `option<int>` .
3. Для параметров значения F # используйте постфиксную форму: `int voption` , а не `voption<int>` .
4. Для массивов F # используйте синтаксические имена, `int[]` а не `int array` или `array<int>` .
5. Для ссылочных ячеек используйте `int ref` вместо `ref<int>` или `Ref<int>` .

Для всех остальных типов используйте форму префикса.

## <a name="formatting-tuples"></a>Форматирование кортежей

Создание экземпляра кортежа должно быть заключено в круглые скобки, за которыми следует одиночный пробел, например: `(1, 2)` , `(x, y, z)` .

Обычно можно опустить круглые скобки в шаблоне, сопоставленном с кортежами:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Также обычно можно опустить круглые скобки, если кортеж является возвращаемым значением функции:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

В заключение следует предпочесть создание экземпляров кортежей в круглых скобках, но при использовании кортежей для сопоставления шаблонов или возвращаемого значения оно считается точным, чтобы избежать круглых скобок.

## <a name="formatting-discriminated-union-declarations"></a>Форматирование объявлений размеченного объединения

Отступ `|` в определении типа по четырем пробелам:

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

При наличии одного короткого объединения можно опустить начальный оператор `|` .

```fsharp
type Address = Address of string
```

Для более длинного или многострочного объединения не задерживайте `|` .

```fsharp
[<NoEquality; NoComparison>]
type SynBinding =
    | SynBinding of
        accessibility: SynAccess option *
        kind: SynBindingKind *
        mustInline: bool *
        isMutable: bool *
        attributes: SynAttributes *
        xmlDoc: PreXmlDoc *
        valData: SynValData *
        headPat: SynPat *
        returnInfo: SynBindingReturnInfo option *
        expr: SynExpr *
        range: range *
        seqPoint: DebugPointAtBinding
```

Можно также использовать комментарии с тройной косой чертой `///` .

```fsharp
type Foobar =
    /// Code comment
    | Foobar of int
```

## <a name="formatting-discriminated-unions"></a>Форматирование размеченных объединений

Использование пробела перед параметрами, заключенными в круглые скобки/кортежи, в случаи размеченного объединения:

```fsharp
// OK
let opt = Some ("A", 1)

// Not OK
let opt = Some("A", 1)
```

Экземпляры с различенными объединениями, разделенными по нескольким строкам, должны предоставлять новой области с отступами следующие данные.

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode (BinaryValue 1, BinaryValue 2),
         BinaryNode (BinaryValue 3, BinaryValue 4))
```

Закрывающая круглая скобка также может находиться на новой строке:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode (BinaryValue 1, BinaryValue 2),
        BinaryNode (BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Форматирование объявлений записей

`{`Создайте отступ в определении типа на четыре пробела и начните список полей в той же строке:

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

Помещение открывающего маркера в новую строку и закрывающий маркер в новой строке предпочтительнее, если объявить реализации интерфейса или элементы в записи:

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

## <a name="formatting-records"></a>Форматирование записей

Короткие записи можно записать в одной строке:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Записи, которые больше не должны использовать новые строки для меток:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Размещение открывающего маркера на новой строке, содержимое, вкладка над одной областью, и закрывающий маркер в новой строке предпочтительнее, если вы:

* Перемещение записей в коде с разными областями отступов
* Передача их в функцию

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
    |> Option.map
           (fun x ->
                {
                    MyField = x
                })
```

Для списка и элементов массива применяются те же правила.

## <a name="formatting-copy-and-update-record-expressions"></a>Форматирование выражений записи копирования и обновления

Выражение записи копирования и обновления по-прежнему является записью, поэтому применяются аналогичные рекомендации.

Короткие выражения могут помещаться в одну строку:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

В более длинных выражениях должны использоваться новые строки:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

Как и в руководстве по записям, может потребоваться выделить отдельные строки для фигурных скобок и задать отступ для одной области справа с помощью выражения. В некоторых особых случаях, например при переносе значения с необязательными скобками, может потребоваться разместить фигурную скобку в одной строке:

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

## <a name="formatting-lists-and-arrays"></a>Форматирование списков и массивов

Напишите `x :: l` с пробелами вокруг `::` оператора ( `::` является оператором инфиксные, таким образом заключенным в пробелы).

Список и массивы, объявленные в одной строке, должны содержать пробел после открывающей скобки и перед закрывающей скобкой:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Всегда используйте хотя бы один пробел между двумя различными операторами, похожими на фигурные скобки. Например, оставьте пробел между `[` и `{` .

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

Одно и то же правило применимо к спискам или массивам кортежей.

Списки и массивы, разделенные по нескольким строкам, следуют тому же правилу, что и записи:

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

И, как и в случае с записями, объявление открывающих и закрывающих квадратных скобок в собственной строке сделает код более простым и походит к функциям.

При создании массивов и списков программным способом предпочтительнее, `->` `do ... yield` когда всегда создается значение:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

Более старые версии языка F # требовали указания `yield` в ситуациях, когда данные могут создаваться условно, или для вычисления последовательных выражений. Рекомендуется опустить эти `yield` Ключевые слова, если не требуется компиляция с использованием более старой версии языка F #:

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

В некоторых случаях `do...yield` может помочь в удобочитаемости. В этих случаях следует учитывать субъективные ситуации.

## <a name="formatting-if-expressions"></a>Форматирование выражений if

Отступы условий зависят от размера и сложности выражений, которые их составляют.
Запишите их на одной строке, когда:

- `cond`, `e1` и `e2` являются короткими
- `e1` и `e2` не являются `if/then/else` самими выражениями.

```fsharp
if cond then e1 else e2
```

Если любое из выражений является многострочным или `if/then/else` выражением.

```fsharp
if cond then
    e1
else
    e2
```

Несколько условий с `elif` и `else` располагаются с отступом в той же области, что и `if` при соблюдении правил из выражений одной строки `if/then/else` .

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

Если любое из условий или выражений является многострочным, все `if/then/else` выражение будет иметь несколько строк:

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

### <a name="pattern-matching-constructs"></a>Конструкции сопоставления шаблонов

Используйте `|` предложение for each совпадения без отступов. Если выражение является коротким, можно использовать одну строку, если каждая часть выражения также является простой.

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

Если выражение справа от стрелки сопоставления шаблонов слишком велико, переместите его в следующую строку с отступом на один шаг из `match` / `|` .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Сопоставление шаблонов анонимных функций, начиная от `function` , не должно быть слишком большим. Например, чтобы задать отступ для одной области, сделайте следующее:

```fsharp
lambdaList
|> List.map
       (function
            | Abs(x, body) -> 1 + sizeLambda 0 body
            | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
            | Var v -> 1)
```

Сопоставление шаблонов в функциях `let` , определенных или `let rec` , должно начинаться с отступа в четыре пробела после начала `let` , даже если `function` используется ключевое слово.

```fsharp
let rec sizeLambda acc =
    function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Не рекомендуется выровняйте стрелки.

## <a name="formatting-trywith-expressions"></a>Форматирование выражений try и with

Сопоставление шаблонов для типа исключения должно иметь отступ на том же уровне, что и `with` .

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

## <a name="formatting-function-parameter-application"></a>Приложение параметров функции форматирования

Как правило, большинство аргументов предоставляются в одной строке:

```fsharp
let x = sprintf "\t%s - %i\n\r" x.IngredientName x.Quantity

let printListWithOffset a list1 =
    List.iter (fun elem -> printfn $"%d{a + elem}") list1
```

Когда речь идет о конвейерах, то также обычно верно и то, где каррированных функции применяется в качестве аргумента в той же строке:

```
let printListWithOffsetPiped a list1 =
    list1
    |> List.iter (fun elem -> printfn $"%d{a + elem}")
```

Тем не менее может потребоваться передать аргументы в функцию в новой строке, чтобы иметь возможность чтения, или так как список аргументов или имен аргументов слишком длинный. В этом случае отступ с одной областью:

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

Для лямбда-выражений может также потребоваться поместить текст лямбда-выражения в новую строку с отступом на одну область, если она достаточно Длинна:

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
             printfn $"A very long line to format the value: %d{a + elem}")
        list1

let printListWithOffsetPiped a list1 =
    list1
    |> List.iter
           (fun elem ->
                printfn $"A very long line to format the value: %d{a + elem}")
```

Если текст лямбда-выражения имеет несколько строк, следует рассмотреть возможность его рефакторинга в функцию, которая находится на локальном уровне.

Параметры обычно должны иметь отступ относительно функции или `fun` / `function` ключевого слова, независимо от контекста, в котором отображается функция.

```fsharp
// With 4 spaces indentation
list1
|> List.fold
       someLongParam
       anotherLongParam

list1
|> List.iter
       (fun elem ->
            printfn $"A very long line to format the value: %d{elem}")

// With 2 spaces indentation
list1
|> List.fold
     someLongParam
     anotherLongParam

list1
|> List.iter
       (fun elem ->
          printfn $"A very long line to format the value: %d{elem}")
```

Если функция принимает один аргумент многострочного кортежа, применяются те же правила для [конструкторов форматирования, статических членов и вызовов элементов](#formatting-constructors-static-members-and-member-invocations) .

```fsharp
let myFunction (a: int, b: string, c: int, d: bool) =
    ()

myFunction(
    478815516,
    "A very long string making all of this multi-line",
    1515,
    false
)
```

### <a name="formatting-infix-operators"></a>Форматирование операторов инфиксные

Разделяйте операторы по пробелам. Очевидными исключениями из этого правила `!` являются `.` операторы и.

Выражения инфиксные являются допустимыми для сопоставления по одному и тому же столбцу:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators-or-mutable-assignments"></a>Форматирование операторов конвейера или изменяемых назначений

Операторы конвейера `|>` должны идти под выражениями, над которыми они работают.

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

Это также относится к изменяемым методам задания:

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

### <a name="formatting-modules"></a>Модули форматирования

Код в локальном модуле должен иметь отступ относительно модуля, но код в модуле верхнего уровня не должен иметь отступы. Элементы пространства имен не обязательно должны иметь отступы.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Форматирование выражений и интерфейсов объекта

Выражения объектов и интерфейсы должны быть выровнены так же, как и с `member` отступом после четырех пробелов.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Форматирование пробелов в выражениях

Избегайте излишнего пробела в выражениях F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Именованные аргументы также не должны содержать пробелы, окружающие `=` :

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a>Конструкторы форматирования, статические члены и вызовы элементов

Если выражение является коротким, разделяйте аргументы пробелами и оставляйте их в одной строке.

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

Если выражение является длинным, используйте символы новой строки и отступа для одной области, а не отступа до квадратной скобки.

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

Те же правила применяются, даже если имеется только один многострочный аргумент.

```fsharp
let poemBuilder = StringBuilder()
poemBuilder.AppendLine(
    """
The last train is nearly due
The Underground is closing soon
And in the dark, deserted station
Restless in anticipation
A man waits in the shadows
    """
)

Option.traverse(
    create
    >> Result.setError [ invalidHeader "Content-Checksum" ]
)
```

## <a name="formatting-generic-type-arguments-and-constraints"></a>Форматирование аргументов и ограничений универсального типа

Приведенные ниже рекомендации применимы как к функциям, членам, так и к определениям типов.

Используйте аргументы универсального типа и ограничения для одной строки, если она имеет слишком большую длину:

```fsharp
let f<'a, 'b when 'a : equality and 'b : comparison> param =
    // function body
```

Если аргументы универсального типа, ограничения и параметры функции не умещаются, но параметры типа и ограничения действуют отдельно, поместите параметры на новые строки:

```fsharp
let f<'a, 'b when 'a : equality and 'b : comparison>
    param
    =
    // function body
```

Если параметры или ограничения типа слишком длинные, прерывать и выровняйте их, как показано ниже. Не заключайте список параметров типа в той же строке, что и функция, независимо от ее длины. Для ограничений разместите `when` на первой строке и не замещайте каждое ограничение на одну строку, независимо от ее длины. Поместите `>` в конец последней строки. Установка отступа для ограничений на один уровень.

```fsharp
let inline f< ^a, ^b
    when ^a : (static member Foo1: unit -> ^b)
    and ^b : (member Foo2: unit -> int)
    and ^b : (member Foo3: string -> ^a option)>
    arg1
    arg2
    =
    // function body
```

Если параметры или ограничения типа разбиваются, но нет обычных параметров функции, размещайте их `=` на новой строке независимо от того, что:

```f#
let inline f<^a, ^b
    when ^a : (static member Foo1: unit -> ^b)
    and ^b : (member Foo2: unit -> int)
    and ^b : (member Foo3: string -> ^a option)>
    =
    // function body
```

## <a name="formatting-attributes"></a>Атрибуты форматирования

[Атрибуты](../language-reference/attributes.md) помещаются над конструкцией:

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

Они должны идти после любой XML-документации:

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a>Атрибуты форматирования для параметров

Атрибуты также могут быть помещены в параметры. В этом случае поместите его в ту же строку, что и параметр, и перед именем:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Форматирование нескольких атрибутов

Если к конструкции, которая не является параметром, применяется несколько атрибутов, их следует размещать таким образом, чтобы в каждой строке был один атрибут:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

При применении к параметру они должны находиться в той же строке и разделяться `;` разделителем.

## <a name="formatting-literals"></a>Литералы форматирования

[Литералы F #](../language-reference/literals.md) , использующие `Literal` атрибут, должны располагать атрибут в собственной строке и использовать PascalCase именование:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Старайтесь не размещать атрибут в той же строке, что и значение.

## <a name="formatting-computation-expression-operations"></a>Форматирование операций вычисления выражения

При создании пользовательских операций для [вычислительных выражений](../language-reference/computation-expressions.md)рекомендуется использовать camelCase именование:

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

Домен, для которого моделируется моделирование, должен в конечном итоге обменяться соглашением об именовании.
Если идиоматическим использовать другое соглашение, вместо него следует использовать это соглашение.
