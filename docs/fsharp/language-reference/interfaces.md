---
title: Интерфейсы
description: 'Узнайте, как интерфейсы F # определяют наборы связанных элементов, реализуемых другими классами.'
ms.date: 08/15/2020
ms.openlocfilehash: ca6ff206758cab12f1a240c4b79ea5143a2a0b7d
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369638"
---
# <a name="interfaces"></a>Интерфейсы

*Интерфейсы* указывают наборы связанных элементов, реализуемых другими классами.

## <a name="syntax"></a>Синтаксис

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Примечания

Объявления интерфейсов похожи на объявления классов, за исключением того, что ни один член не реализован. Вместо этого все члены являются абстрактными, как указано ключевым словом `abstract` . Не предоставляется тело метода для абстрактных методов. Однако можно предоставить реализацию по умолчанию, включив отдельное определение члена в качестве метода вместе с `default` ключевым словом. Это эквивалентно созданию виртуального метода в базовом классе на других языках .NET. Такой виртуальный метод можно переопределить в классах, реализующих интерфейс.

По умолчанию для интерфейсов используется уровень доступности `public` .

При необходимости можно присвоить каждому параметру метода имя с помощью обычного синтаксиса F #:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

В приведенном выше `ISprintable` примере `Print` метод имеет единственный параметр типа `string` с именем `format` .

Реализовать интерфейсы можно двумя способами: с помощью выражений объектов и типов классов. В любом случае тип класса или выражение объекта предоставляет тела методов для абстрактных методов интерфейса. Реализации относятся к каждому типу, реализующему интерфейс. Поэтому методы интерфейса для разных типов могут отличаться друг от друга.

Ключевые слова `interface` и `end` , которые отмечают начало и конец определения, являются необязательными при использовании упрощенного синтаксиса. Если эти ключевые слова не используются, компилятор пытается определить, является ли тип классом или интерфейсом, анализируя используемые конструкции. При определении члена или использовании другого синтаксиса класса тип интерпретируется как класс.

Стиль написания кода .NET — это начало всех интерфейсов с заглавной буквой `I` .

Можно указать несколько параметров двумя способами: F #-style и. Стиль NET. Оба метода будут компилироваться одинаково для потребителей .NET, но в стиле F # будут принудительно использовать в f # приложение с параметрами и. NET-Styles вынуждает вызывающие методы F # использовать приложение аргументов кортежа.

```fsharp
type INumericFSharp =
    abstract Add: x: int -> y: int -> int

type INumericDotNet =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>Реализация интерфейсов с помощью типов классов

Можно реализовать один или несколько интерфейсов в типе класса с помощью `interface` ключевого слова, имени интерфейса и `with` ключевого слова, а затем определений членов интерфейса, как показано в следующем коде.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Реализации интерфейса наследуются, поэтому все производные классы не нуждаются в их повторной реализации.

## <a name="calling-interface-methods"></a>Вызов методов интерфейса

Методы интерфейса могут вызываться только через интерфейс, а не через какой-либо объект типа, который реализует интерфейс. Поэтому для вызова этих методов может потребоваться выполнить приведение к типу интерфейса с помощью `:>` оператора или `upcast` оператора.

Чтобы вызвать метод интерфейса при наличии объекта типа `SomeClass` , необходимо выполнить операцию приведения объекта к типу интерфейса, как показано в следующем коде.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Альтернативой является объявление метода для объекта, который выполняет приведение и вызов метода интерфейса, как показано в следующем примере.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Реализация интерфейсов с помощью выражений объектов

Выражения объектов предоставляют короткий способ реализации интерфейса. Они полезны в тех случаях, когда не нужно создавать именованный тип и нужен только объект, поддерживающий методы интерфейса, без каких-либо дополнительных методов. В следующем коде показано выражение объекта.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Наследование интерфейса

Интерфейсы могут наследовать от одного или нескольких базовых интерфейсов.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a>Реализация интерфейсов с реализациями по умолчанию

C# поддерживает определение интерфейсов с реализациями по умолчанию следующим образом:

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

Они напрямую используются в F #:

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

Можно переопределить реализацию по умолчанию с помощью `override` , например переопределив любой виртуальный член.

Все члены интерфейса, у которых нет реализации по умолчанию, по-прежнему должны быть явно реализованы.

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a>Реализация того же интерфейса в различных универсальных экземплярах

F # поддерживает реализацию того же интерфейса в различных универсальных экземплярах, таких как:

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

## <a name="see-also"></a>См. также

- [Справочник по языку F#](index.md)
- [Выражения объекта](object-expressions.md)
- [Классы](classes.md)
