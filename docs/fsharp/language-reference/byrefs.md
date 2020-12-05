---
title: Byref
description: 'Сведения о типах, схожих с ByRef и ByRef, в F #, которые используются для низкоуровневого программирования.'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740319"
---
# <a name="byrefs"></a><span data-ttu-id="55e40-103">Byref</span><span class="sxs-lookup"><span data-stu-id="55e40-103">Byrefs</span></span>

<span data-ttu-id="55e40-104">F # имеет две основные функциональные области, которые имеют место в пространстве низкоуровневого программирования:</span><span class="sxs-lookup"><span data-stu-id="55e40-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="55e40-105">`byref` / `inref` / `outref` Типы, являющиеся управляемыми указателями.</span><span class="sxs-lookup"><span data-stu-id="55e40-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="55e40-106">Они имеют ограничения на использование, поэтому нельзя компилировать программу, недопустимую во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="55e40-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="55e40-107">Структура, похожая на `byref` [структуру](structures.md) , которая имеет подобную семантику и те же ограничения времени компиляции, что и `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="55e40-108">Один из примеров: <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="55e40-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="55e40-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55e40-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="55e40-110">ByRef, инреф и аутреф</span><span class="sxs-lookup"><span data-stu-id="55e40-110">Byref, inref, and outref</span></span>

<span data-ttu-id="55e40-111">Существует три вида `byref` :</span><span class="sxs-lookup"><span data-stu-id="55e40-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="55e40-112">`inref<'T>`управляемый указатель для чтения базового значения.</span><span class="sxs-lookup"><span data-stu-id="55e40-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="55e40-113">`outref<'T>`управляемый указатель для записи в базовое значение.</span><span class="sxs-lookup"><span data-stu-id="55e40-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="55e40-114">`byref<'T>`управляемый указатель для чтения и записи базового значения.</span><span class="sxs-lookup"><span data-stu-id="55e40-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="55e40-115">`byref<'T>`Может быть передан, где `inref<'T>` ожидается.</span><span class="sxs-lookup"><span data-stu-id="55e40-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="55e40-116">Аналогичным образом `byref<'T>` можно передать значение, где `outref<'T>` ожидается.</span><span class="sxs-lookup"><span data-stu-id="55e40-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="55e40-117">Использование ByRef</span><span class="sxs-lookup"><span data-stu-id="55e40-117">Using byrefs</span></span>

<span data-ttu-id="55e40-118">Чтобы использовать `inref<'T>` , необходимо получить значение указателя с помощью `&` :</span><span class="sxs-lookup"><span data-stu-id="55e40-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="55e40-119">Для записи в указатель с помощью `outref<'T>` или `byref<'T>` необходимо также сделать значение, которое вы захватите на указатель `mutable` .</span><span class="sxs-lookup"><span data-stu-id="55e40-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="55e40-120">Если вы пишете только указатель, а не читаете его, рассмотрите возможность использования `outref<'T>` вместо `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="55e40-121">Семантика инреф</span><span class="sxs-lookup"><span data-stu-id="55e40-121">Inref semantics</span></span>

<span data-ttu-id="55e40-122">Рассмотрим следующий код:</span><span class="sxs-lookup"><span data-stu-id="55e40-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="55e40-123">В семантическом виде это означает следующее:</span><span class="sxs-lookup"><span data-stu-id="55e40-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="55e40-124">Владелец `x` указателя может использовать его только для чтения значения.</span><span class="sxs-lookup"><span data-stu-id="55e40-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="55e40-125">Любой указатель, полученный к `struct` полям, вложенным в `SomeStruct` , задается типом `inref<_>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="55e40-126">Также верно следующее:</span><span class="sxs-lookup"><span data-stu-id="55e40-126">The following is also true:</span></span>

* <span data-ttu-id="55e40-127">Нет никаких последствие того, что другие потоки или псевдонимы не имеют доступа на запись `x` .</span><span class="sxs-lookup"><span data-stu-id="55e40-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="55e40-128">Неизменность не является `SomeStruct` неизменяемой, так как является `x` `inref` .</span><span class="sxs-lookup"><span data-stu-id="55e40-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="55e40-129">Однако для типов значений F #, которые **являются** неизменяемыми, `this` указатель выводится как `inref` .</span><span class="sxs-lookup"><span data-stu-id="55e40-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="55e40-130">Все эти правила вместе означают, что владелец `inref` указателя не может изменить немедленное содержимое памяти, на которое указывает.</span><span class="sxs-lookup"><span data-stu-id="55e40-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="55e40-131">Семантика аутреф</span><span class="sxs-lookup"><span data-stu-id="55e40-131">Outref semantics</span></span>

<span data-ttu-id="55e40-132">Целью `outref<'T>` является указание на то, что указатель должен быть записан только в.</span><span class="sxs-lookup"><span data-stu-id="55e40-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="55e40-133">Неожиданно, `outref<'T>` позволяет считывать базовое значение, несмотря на его имя.</span><span class="sxs-lookup"><span data-stu-id="55e40-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="55e40-134">Это происходит в целях совместимости.</span><span class="sxs-lookup"><span data-stu-id="55e40-134">This is for compatibility purposes.</span></span> <span data-ttu-id="55e40-135">Семантически, не `outref<'T>` отличается от `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="55e40-136">Взаимодействие с C\#</span><span class="sxs-lookup"><span data-stu-id="55e40-136">Interop with C\#</span></span>

<span data-ttu-id="55e40-137">C# поддерживает `in ref` `out ref` Ключевые слова и, а также `ref` возвращает.</span><span class="sxs-lookup"><span data-stu-id="55e40-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="55e40-138">В следующей таблице показано, как F # интерпретирует вырожденные выпуски C#:</span><span class="sxs-lookup"><span data-stu-id="55e40-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="55e40-139">Конструкция C#</span><span class="sxs-lookup"><span data-stu-id="55e40-139">C# construct</span></span>|<span data-ttu-id="55e40-140">Выводит F #</span><span class="sxs-lookup"><span data-stu-id="55e40-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="55e40-141">`ref` Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="55e40-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="55e40-142">`ref readonly` Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="55e40-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="55e40-143">Параметр `in ref`</span><span class="sxs-lookup"><span data-stu-id="55e40-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="55e40-144">Параметр `out ref`</span><span class="sxs-lookup"><span data-stu-id="55e40-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="55e40-145">В следующей таблице показано, какие выпуски F #:</span><span class="sxs-lookup"><span data-stu-id="55e40-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="55e40-146">Конструкция F #</span><span class="sxs-lookup"><span data-stu-id="55e40-146">F# construct</span></span>|<span data-ttu-id="55e40-147">Выпущенная конструкция</span><span class="sxs-lookup"><span data-stu-id="55e40-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="55e40-148">Аргумент `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="55e40-148">`inref<'T>` argument</span></span>|<span data-ttu-id="55e40-149">`[In]` атрибут в аргументе</span><span class="sxs-lookup"><span data-stu-id="55e40-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="55e40-150">`inref<'T>` вернул</span><span class="sxs-lookup"><span data-stu-id="55e40-150">`inref<'T>` return</span></span>|<span data-ttu-id="55e40-151">`modreq` атрибут для значения</span><span class="sxs-lookup"><span data-stu-id="55e40-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="55e40-152">`inref<'T>` в абстрактном слоте или реализации</span><span class="sxs-lookup"><span data-stu-id="55e40-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="55e40-153">`modreq` аргумент ON или Return</span><span class="sxs-lookup"><span data-stu-id="55e40-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="55e40-154">Аргумент `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="55e40-154">`outref<'T>` argument</span></span>|<span data-ttu-id="55e40-155">`[Out]` атрибут в аргументе</span><span class="sxs-lookup"><span data-stu-id="55e40-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="55e40-156">Определение типа и перегрузка правил</span><span class="sxs-lookup"><span data-stu-id="55e40-156">Type inference and overloading rules</span></span>

<span data-ttu-id="55e40-157">`inref<'T>`Тип выводится компилятором F # в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="55e40-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="55e40-158">Параметр или возвращаемый тип .NET, имеющий `IsReadOnly` атрибут.</span><span class="sxs-lookup"><span data-stu-id="55e40-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="55e40-159">`this`Указатель на тип структуры, не имеющий изменяемых полей.</span><span class="sxs-lookup"><span data-stu-id="55e40-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="55e40-160">Адрес области памяти, полученной из другого `inref<_>` указателя.</span><span class="sxs-lookup"><span data-stu-id="55e40-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="55e40-161">Когда выполняется неявный адрес `inref` , перегрузка с аргументом типа `SomeType` является предпочтительной для перегрузки с аргументом типа `inref<SomeType>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="55e40-162">Пример:</span><span class="sxs-lookup"><span data-stu-id="55e40-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="55e40-163">В обоих случаях перегрузки `System.DateTime` разрешаются, а не перегрузками `inref<System.DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="55e40-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="55e40-164">Структуры, аналогичные ByRef</span><span class="sxs-lookup"><span data-stu-id="55e40-164">Byref-like structs</span></span>

<span data-ttu-id="55e40-165">В дополнение к `byref` / `inref` / `outref` три можно определить собственные структуры, которые могут соответствовать `byref` семантике, схожей с.</span><span class="sxs-lookup"><span data-stu-id="55e40-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="55e40-166">Это делается с помощью <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> атрибута:</span><span class="sxs-lookup"><span data-stu-id="55e40-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="55e40-167">`IsByRefLike` не подразумевается `Struct` .</span><span class="sxs-lookup"><span data-stu-id="55e40-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="55e40-168">Оба должны присутствовать в типе.</span><span class="sxs-lookup"><span data-stu-id="55e40-168">Both must be present on the type.</span></span>

<span data-ttu-id="55e40-169">Структура " `byref` -Like" в F # является типом значения, привязанного к стеку.</span><span class="sxs-lookup"><span data-stu-id="55e40-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="55e40-170">Он никогда не выделяется в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="55e40-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="55e40-171">`byref`Структура, похожая на структуру, полезна для высокопроизводительного программирования, так как она применяется с набором строгих проверок на время существования и без записи.</span><span class="sxs-lookup"><span data-stu-id="55e40-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="55e40-172">Правила:</span><span class="sxs-lookup"><span data-stu-id="55e40-172">The rules are:</span></span>

* <span data-ttu-id="55e40-173">Их можно использовать в качестве параметров функций, параметров методов, локальных переменных, возвращаемых методом.</span><span class="sxs-lookup"><span data-stu-id="55e40-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="55e40-174">Они не могут быть статическими или членами экземпляров класса или обычной структуры.</span><span class="sxs-lookup"><span data-stu-id="55e40-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="55e40-175">Они не могут быть захвачены ни одной конструкцией замыкания ( `async` методами или лямбда-выражениями).</span><span class="sxs-lookup"><span data-stu-id="55e40-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="55e40-176">Их нельзя использовать в качестве универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="55e40-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="55e40-177">Последний момент является ключевым для программирования в стиле конвейера F #, как и `|>` универсальная функция, которая выполняет параметризацию входных типов.</span><span class="sxs-lookup"><span data-stu-id="55e40-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="55e40-178">Это ограничение может быть ослаблено `|>` в будущем, так как оно встроено и не выполняет вызовы невстроенных универсальных функций в тексте.</span><span class="sxs-lookup"><span data-stu-id="55e40-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="55e40-179">Хотя эти правила строго ограничивают использование, они делают это для обеспечения безопасности высокопроизводительных вычислительных систем.</span><span class="sxs-lookup"><span data-stu-id="55e40-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="55e40-180">Возвраты по ссылке</span><span class="sxs-lookup"><span data-stu-id="55e40-180">Byref returns</span></span>

<span data-ttu-id="55e40-181">Функция ByRef возвращает из функций или членов F #, которые могут быть созданы и использованы.</span><span class="sxs-lookup"><span data-stu-id="55e40-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="55e40-182">При использовании `byref` метода, возвращающего возврат, значение неявно разыменовано.</span><span class="sxs-lookup"><span data-stu-id="55e40-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="55e40-183">Пример:</span><span class="sxs-lookup"><span data-stu-id="55e40-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

<span data-ttu-id="55e40-184">Чтобы получить значение ByRef, переменная, содержащая значение, должна находиться дольше текущей области.</span><span class="sxs-lookup"><span data-stu-id="55e40-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="55e40-185">Кроме того, чтобы вернуть ByRef, используйте `&value` (где value — переменная, которая находится дольше текущей области).</span><span class="sxs-lookup"><span data-stu-id="55e40-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="55e40-186">Чтобы избежать неявного разыменования, например передачи ссылки через несколько цепочек вызовов, используйте `&x` (где `x` — это значение).</span><span class="sxs-lookup"><span data-stu-id="55e40-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="55e40-187">Вы также можете напрямую присвоить значение `byref` .</span><span class="sxs-lookup"><span data-stu-id="55e40-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="55e40-188">Рассмотрим следующую (очень императивную) программу:</span><span class="sxs-lookup"><span data-stu-id="55e40-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

<span data-ttu-id="55e40-189">Результат.</span><span class="sxs-lookup"><span data-stu-id="55e40-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="55e40-190">Определение области для ByRef</span><span class="sxs-lookup"><span data-stu-id="55e40-190">Scoping for byrefs</span></span>

<span data-ttu-id="55e40-191">`let`Значение привязки не может быть больше, чем область, в которой он был определен.</span><span class="sxs-lookup"><span data-stu-id="55e40-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="55e40-192">Например, запрещены следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="55e40-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="55e40-193">Это не позволит получить разные результаты в зависимости от того, выполняется ли компиляция с оптимизацией или нет.</span><span class="sxs-lookup"><span data-stu-id="55e40-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
