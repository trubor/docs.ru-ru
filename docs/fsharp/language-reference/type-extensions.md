---
title: Расширения типов
description: 'Узнайте, как расширения типа F # позволяют добавлять новые члены к ранее определенному типу объекта.'
ms.date: 02/05/2020
ms.openlocfilehash: c9adddb3133a4af57a12be0b09c22954a8bff6a7
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737272"
---
# <a name="type-extensions"></a><span data-ttu-id="f7025-103">Расширения типов</span><span class="sxs-lookup"><span data-stu-id="f7025-103">Type extensions</span></span>

<span data-ttu-id="f7025-104">Расширения типов (также называемые _приращениями_) — это семейство функций, которые позволяют добавлять новые члены к ранее определенным типам объектов.</span><span class="sxs-lookup"><span data-stu-id="f7025-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="f7025-105">Доступны следующие три функции.</span><span class="sxs-lookup"><span data-stu-id="f7025-105">The three features are:</span></span>

- <span data-ttu-id="f7025-106">Встроенные расширения типов</span><span class="sxs-lookup"><span data-stu-id="f7025-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="f7025-107">Необязательные расширения типов</span><span class="sxs-lookup"><span data-stu-id="f7025-107">Optional type extensions</span></span>
- <span data-ttu-id="f7025-108">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="f7025-108">Extension methods</span></span>

<span data-ttu-id="f7025-109">Каждый из них можно использовать в различных сценариях и имеет различные компромиссы.</span><span class="sxs-lookup"><span data-stu-id="f7025-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7025-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7025-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [<Extension>]
    static member extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="f7025-111">Встроенные расширения типов</span><span class="sxs-lookup"><span data-stu-id="f7025-111">Intrinsic type extensions</span></span>

<span data-ttu-id="f7025-112">Внутреннее расширение типа — это расширение типа, расширяющее определяемый пользователем тип.</span><span class="sxs-lookup"><span data-stu-id="f7025-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="f7025-113">Встроенные расширения типов должны быть определены в том же файле **и** в том же пространстве имен или модуле, что и расширяемый тип.</span><span class="sxs-lookup"><span data-stu-id="f7025-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="f7025-114">Любое другое определение приведет к тому, что они станут [дополнительными расширениями типа](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="f7025-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="f7025-115">Встроенные расширения типов иногда являются четким способом разделения функциональных возможностей из объявления типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="f7025-116">В следующем примере показано, как определить внутреннее расширение типа:</span><span class="sxs-lookup"><span data-stu-id="f7025-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="f7025-117">Использование расширения типа позволяет разделить каждый из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="f7025-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="f7025-118">Объявление `Variant` типа</span><span class="sxs-lookup"><span data-stu-id="f7025-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="f7025-119">Функции для печати `Variant` класса в зависимости от его "формы"</span><span class="sxs-lookup"><span data-stu-id="f7025-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="f7025-120">Способ доступа к функции печати с помощью `.` нотации объекта</span><span class="sxs-lookup"><span data-stu-id="f7025-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="f7025-121">Это альтернатива определению всех элементов в качестве члена `Variant` .</span><span class="sxs-lookup"><span data-stu-id="f7025-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="f7025-122">Хотя это и не является оптимальным подходом, в некоторых ситуациях это может быть понятным представлением функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="f7025-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="f7025-123">Встроенные расширения типов компилируются как члены типа, которые они расширяют, и отображаются в типе при проверке типа с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="f7025-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="f7025-124">Необязательные расширения типов</span><span class="sxs-lookup"><span data-stu-id="f7025-124">Optional type extensions</span></span>

<span data-ttu-id="f7025-125">Необязательное расширение типа — это расширение, которое отображается вне исходного модуля, пространства имен или сборки расширяемого типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="f7025-126">Необязательные расширения типов полезны для расширения типа, который вы не определили самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="f7025-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="f7025-127">Пример:</span><span class="sxs-lookup"><span data-stu-id="f7025-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="f7025-128">Теперь можно получить доступ `RepeatElements` , как если бы он был членом, пока <xref:System.Collections.Generic.IEnumerable%601> `Extensions` модуль открыт в области, в которой вы работаете.</span><span class="sxs-lookup"><span data-stu-id="f7025-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="f7025-129">Дополнительные расширения не отображаются в расширенном типе при проверке с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="f7025-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="f7025-130">Необязательные расширения должны находиться в модулях, и они находятся только в области, если модуль, содержащий расширение, открыт или в другой области.</span><span class="sxs-lookup"><span data-stu-id="f7025-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="f7025-131">Необязательные элементы расширения компилируются в статические члены, для которых экземпляр объекта передается неявно в качестве первого параметра.</span><span class="sxs-lookup"><span data-stu-id="f7025-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="f7025-132">Однако они действуют так, как если бы они были членами экземпляров или статическими членами в соответствии с их объявлением.</span><span class="sxs-lookup"><span data-stu-id="f7025-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="f7025-133">Необязательные члены расширения также невидимы для потребителей C# или Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7025-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="f7025-134">Их можно использовать только в другом коде F #.</span><span class="sxs-lookup"><span data-stu-id="f7025-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="f7025-135">Универсальное ограничение встроенных и необязательных расширений типов</span><span class="sxs-lookup"><span data-stu-id="f7025-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="f7025-136">Можно объявить расширение типа для универсального типа, в котором переменная типа ограничена.</span><span class="sxs-lookup"><span data-stu-id="f7025-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="f7025-137">Требование заключается в том, что ограничение объявления расширения соответствует ограничению объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="f7025-138">Однако даже при совпадении ограничений между объявленным типом и расширением типа можно вывести ограничение в тексте расширенного члена, который накладывает иное требование для параметра типа, чем объявленный тип.</span><span class="sxs-lookup"><span data-stu-id="f7025-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="f7025-139">Пример:</span><span class="sxs-lookup"><span data-stu-id="f7025-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="f7025-140">Невозможно получить этот код для работы с дополнительным расширением типа:</span><span class="sxs-lookup"><span data-stu-id="f7025-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="f7025-141">Как есть, у `Sum` члена есть другое ограничение `'T` ( `static member get_Zero` и), `static member (+)` чем определено расширением типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="f7025-142">Изменение расширения типа с тем же ограничением, которое `Sum` больше не будет соответствовать определенному ограничению в `IEnumerable<'T>` .</span><span class="sxs-lookup"><span data-stu-id="f7025-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="f7025-143">Если изменить `member this.Sum` на, `member inline this.Sum` будет выдаваться ошибка, при которой ограничения типов не совпадают.</span><span class="sxs-lookup"><span data-stu-id="f7025-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="f7025-144">Нужны такие статические методы, как "плавающее место", и их можно представить так, как если бы они расширялись типом.</span><span class="sxs-lookup"><span data-stu-id="f7025-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="f7025-145">Именно здесь методы расширения становятся необходимыми.</span><span class="sxs-lookup"><span data-stu-id="f7025-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="f7025-146">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="f7025-146">Extension methods</span></span>

<span data-ttu-id="f7025-147">Наконец, методы расширения (иногда называемые «членами расширения стиля C#») могут быть объявлены в F # как статический метод-член для класса.</span><span class="sxs-lookup"><span data-stu-id="f7025-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="f7025-148">Методы расширения полезны при определении расширений для универсального типа, которые ограничивают бы переменную типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="f7025-149">Пример:</span><span class="sxs-lookup"><span data-stu-id="f7025-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="f7025-150">Если используется этот код, он будет выглядеть так, как если бы он был `Sum` определен в <xref:System.Collections.Generic.IEnumerable%601> , пока он `Extensions` открыт или находится в области.</span><span class="sxs-lookup"><span data-stu-id="f7025-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="f7025-151">Чтобы расширение было доступно для кода VB.NET, `ExtensionAttribute` на уровне сборки требуется дополнительный объект:</span><span class="sxs-lookup"><span data-stu-id="f7025-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="f7025-152">Другие замечания</span><span class="sxs-lookup"><span data-stu-id="f7025-152">Other remarks</span></span>

<span data-ttu-id="f7025-153">Расширения типов также имеют следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="f7025-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="f7025-154">Любой тип, к которому можно получить доступ, можно расширить.</span><span class="sxs-lookup"><span data-stu-id="f7025-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="f7025-155">Встроенные и необязательные расширения типов могут определять _любые_ типы членов, а не только методы.</span><span class="sxs-lookup"><span data-stu-id="f7025-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="f7025-156">Итак, свойства расширения также возможны, например.</span><span class="sxs-lookup"><span data-stu-id="f7025-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="f7025-157">`self-identifier`Токен в [синтаксисе](type-extensions.md#syntax) представляет экземпляр вызываемого типа, как и обычные члены.</span><span class="sxs-lookup"><span data-stu-id="f7025-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="f7025-158">Расширенные элементы могут быть статическими или членами экземпляра.</span><span class="sxs-lookup"><span data-stu-id="f7025-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="f7025-159">Переменные типа в расширении типа должны соответствовать ограничениям объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="f7025-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="f7025-160">Для расширений типов также существуют следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="f7025-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="f7025-161">Расширения типов не поддерживают виртуальные или абстрактные методы.</span><span class="sxs-lookup"><span data-stu-id="f7025-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="f7025-162">Расширения типов не поддерживают методы переопределения в качестве дополнений.</span><span class="sxs-lookup"><span data-stu-id="f7025-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="f7025-163">Расширения типов не поддерживают [статически разрешаемые параметры типа](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f7025-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="f7025-164">Необязательные расширения типов не поддерживают конструкторы как дополнения.</span><span class="sxs-lookup"><span data-stu-id="f7025-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="f7025-165">Расширения типов не могут быть определены для [сокращений типов](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="f7025-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="f7025-166">Расширения типов недопустимы для `byref<'T>` (хотя они могут быть объявлены).</span><span class="sxs-lookup"><span data-stu-id="f7025-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="f7025-167">Расширения типов недопустимы для атрибутов (хотя они могут быть объявлены).</span><span class="sxs-lookup"><span data-stu-id="f7025-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="f7025-168">Можно определить расширения, которые перегружают другие методы с тем же именем, но компилятор F # дает предпочтение методам, не являющимся расширениями, если имеется неоднозначный вызов.</span><span class="sxs-lookup"><span data-stu-id="f7025-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="f7025-169">Наконец, если существует несколько встроенных расширений типов для одного типа, все элементы должны быть уникальными.</span><span class="sxs-lookup"><span data-stu-id="f7025-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="f7025-170">Для необязательных расширений типов члены в разных расширениях типов могут иметь одинаковые имена.</span><span class="sxs-lookup"><span data-stu-id="f7025-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="f7025-171">Ошибки неоднозначности возникают, только если клиентский код открывает две различные области, определяющие одинаковые имена членов.</span><span class="sxs-lookup"><span data-stu-id="f7025-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7025-172">См. также</span><span class="sxs-lookup"><span data-stu-id="f7025-172">See also</span></span>

- [<span data-ttu-id="f7025-173">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="f7025-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f7025-174">Члены</span><span class="sxs-lookup"><span data-stu-id="f7025-174">Members</span></span>](./members/index.md)
