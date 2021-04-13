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
# <a name="interfaces"></a><span data-ttu-id="464ed-103">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="464ed-103">Interfaces</span></span>

<span data-ttu-id="464ed-104">*Интерфейсы* указывают наборы связанных элементов, реализуемых другими классами.</span><span class="sxs-lookup"><span data-stu-id="464ed-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="464ed-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="464ed-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="464ed-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="464ed-106">Remarks</span></span>

<span data-ttu-id="464ed-107">Объявления интерфейсов похожи на объявления классов, за исключением того, что ни один член не реализован.</span><span class="sxs-lookup"><span data-stu-id="464ed-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="464ed-108">Вместо этого все члены являются абстрактными, как указано ключевым словом `abstract` .</span><span class="sxs-lookup"><span data-stu-id="464ed-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="464ed-109">Не предоставляется тело метода для абстрактных методов.</span><span class="sxs-lookup"><span data-stu-id="464ed-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="464ed-110">Однако можно предоставить реализацию по умолчанию, включив отдельное определение члена в качестве метода вместе с `default` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="464ed-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="464ed-111">Это эквивалентно созданию виртуального метода в базовом классе на других языках .NET.</span><span class="sxs-lookup"><span data-stu-id="464ed-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="464ed-112">Такой виртуальный метод можно переопределить в классах, реализующих интерфейс.</span><span class="sxs-lookup"><span data-stu-id="464ed-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="464ed-113">По умолчанию для интерфейсов используется уровень доступности `public` .</span><span class="sxs-lookup"><span data-stu-id="464ed-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="464ed-114">При необходимости можно присвоить каждому параметру метода имя с помощью обычного синтаксиса F #:</span><span class="sxs-lookup"><span data-stu-id="464ed-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="464ed-115">В приведенном выше `ISprintable` примере `Print` метод имеет единственный параметр типа `string` с именем `format` .</span><span class="sxs-lookup"><span data-stu-id="464ed-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="464ed-116">Реализовать интерфейсы можно двумя способами: с помощью выражений объектов и типов классов.</span><span class="sxs-lookup"><span data-stu-id="464ed-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="464ed-117">В любом случае тип класса или выражение объекта предоставляет тела методов для абстрактных методов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="464ed-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="464ed-118">Реализации относятся к каждому типу, реализующему интерфейс.</span><span class="sxs-lookup"><span data-stu-id="464ed-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="464ed-119">Поэтому методы интерфейса для разных типов могут отличаться друг от друга.</span><span class="sxs-lookup"><span data-stu-id="464ed-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="464ed-120">Ключевые слова `interface` и `end` , которые отмечают начало и конец определения, являются необязательными при использовании упрощенного синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="464ed-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="464ed-121">Если эти ключевые слова не используются, компилятор пытается определить, является ли тип классом или интерфейсом, анализируя используемые конструкции.</span><span class="sxs-lookup"><span data-stu-id="464ed-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="464ed-122">При определении члена или использовании другого синтаксиса класса тип интерпретируется как класс.</span><span class="sxs-lookup"><span data-stu-id="464ed-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="464ed-123">Стиль написания кода .NET — это начало всех интерфейсов с заглавной буквой `I` .</span><span class="sxs-lookup"><span data-stu-id="464ed-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="464ed-124">Можно указать несколько параметров двумя способами: F #-style и. Стиль NET.</span><span class="sxs-lookup"><span data-stu-id="464ed-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="464ed-125">Оба метода будут компилироваться одинаково для потребителей .NET, но в стиле F # будут принудительно использовать в f # приложение с параметрами и. NET-Styles вынуждает вызывающие методы F # использовать приложение аргументов кортежа.</span><span class="sxs-lookup"><span data-stu-id="464ed-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumericFSharp =
    abstract Add: x: int -> y: int -> int

type INumericDotNet =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="464ed-126">Реализация интерфейсов с помощью типов классов</span><span class="sxs-lookup"><span data-stu-id="464ed-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="464ed-127">Можно реализовать один или несколько интерфейсов в типе класса с помощью `interface` ключевого слова, имени интерфейса и `with` ключевого слова, а затем определений членов интерфейса, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="464ed-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="464ed-128">Реализации интерфейса наследуются, поэтому все производные классы не нуждаются в их повторной реализации.</span><span class="sxs-lookup"><span data-stu-id="464ed-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="464ed-129">Вызов методов интерфейса</span><span class="sxs-lookup"><span data-stu-id="464ed-129">Calling Interface Methods</span></span>

<span data-ttu-id="464ed-130">Методы интерфейса могут вызываться только через интерфейс, а не через какой-либо объект типа, который реализует интерфейс.</span><span class="sxs-lookup"><span data-stu-id="464ed-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="464ed-131">Поэтому для вызова этих методов может потребоваться выполнить приведение к типу интерфейса с помощью `:>` оператора или `upcast` оператора.</span><span class="sxs-lookup"><span data-stu-id="464ed-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="464ed-132">Чтобы вызвать метод интерфейса при наличии объекта типа `SomeClass` , необходимо выполнить операцию приведения объекта к типу интерфейса, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="464ed-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="464ed-133">Альтернативой является объявление метода для объекта, который выполняет приведение и вызов метода интерфейса, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="464ed-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="464ed-134">Реализация интерфейсов с помощью выражений объектов</span><span class="sxs-lookup"><span data-stu-id="464ed-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="464ed-135">Выражения объектов предоставляют короткий способ реализации интерфейса.</span><span class="sxs-lookup"><span data-stu-id="464ed-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="464ed-136">Они полезны в тех случаях, когда не нужно создавать именованный тип и нужен только объект, поддерживающий методы интерфейса, без каких-либо дополнительных методов.</span><span class="sxs-lookup"><span data-stu-id="464ed-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="464ed-137">В следующем коде показано выражение объекта.</span><span class="sxs-lookup"><span data-stu-id="464ed-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="464ed-138">Наследование интерфейса</span><span class="sxs-lookup"><span data-stu-id="464ed-138">Interface Inheritance</span></span>

<span data-ttu-id="464ed-139">Интерфейсы могут наследовать от одного или нескольких базовых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="464ed-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a><span data-ttu-id="464ed-140">Реализация интерфейсов с реализациями по умолчанию</span><span class="sxs-lookup"><span data-stu-id="464ed-140">Implementing interfaces with default implementations</span></span>

<span data-ttu-id="464ed-141">C# поддерживает определение интерфейсов с реализациями по умолчанию следующим образом:</span><span class="sxs-lookup"><span data-stu-id="464ed-141">C# supports defining interfaces with default implementations, like so:</span></span>

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

<span data-ttu-id="464ed-142">Они напрямую используются в F #:</span><span class="sxs-lookup"><span data-stu-id="464ed-142">These are directly consumable from F#:</span></span>

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

<span data-ttu-id="464ed-143">Можно переопределить реализацию по умолчанию с помощью `override` , например переопределив любой виртуальный член.</span><span class="sxs-lookup"><span data-stu-id="464ed-143">You can override a default implementation with `override`, like overriding any virtual member.</span></span>

<span data-ttu-id="464ed-144">Все члены интерфейса, у которых нет реализации по умолчанию, по-прежнему должны быть явно реализованы.</span><span class="sxs-lookup"><span data-stu-id="464ed-144">Any members in an interface that do not have a default implementation must still be explicitly implemented.</span></span>

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a><span data-ttu-id="464ed-145">Реализация того же интерфейса в различных универсальных экземплярах</span><span class="sxs-lookup"><span data-stu-id="464ed-145">Implementing the same interface at different generic instantiations</span></span>

<span data-ttu-id="464ed-146">F # поддерживает реализацию того же интерфейса в различных универсальных экземплярах, таких как:</span><span class="sxs-lookup"><span data-stu-id="464ed-146">F# supports implementing the same interface at different generic instantiations like so:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="464ed-147">См. также</span><span class="sxs-lookup"><span data-stu-id="464ed-147">See also</span></span>

- [<span data-ttu-id="464ed-148">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="464ed-148">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="464ed-149">Выражения объекта</span><span class="sxs-lookup"><span data-stu-id="464ed-149">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="464ed-150">Классы</span><span class="sxs-lookup"><span data-stu-id="464ed-150">Classes</span></span>](classes.md)
