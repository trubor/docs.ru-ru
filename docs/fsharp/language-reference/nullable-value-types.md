---
title: Типы значений, допускающие значение NULL
description: 'Узнайте, как использовать типы значений, допускающие значение null, способ представления типов значений, которые также могут иметь значение null, в F #.'
ms.date: 11/19/2020
ms.openlocfilehash: e28cbfc57c5631573f46ac36462517cf011e96d2
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009642"
---
# <a name="nullable-value-types"></a><span data-ttu-id="764e4-103">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="764e4-103">Nullable value types</span></span>

<span data-ttu-id="764e4-104">_Тип значения, допускающий значения NULL_ `Nullable<'T>` , представляет любой тип [структуры](structures.md) , который также может иметь значение `null` .</span><span class="sxs-lookup"><span data-stu-id="764e4-104">A _nullable value type_ `Nullable<'T>` represents any [struct](structures.md) type that could also be `null`.</span></span> <span data-ttu-id="764e4-105">Это полезно при взаимодействии с библиотеками и компонентами, которые могут представлять типы таких типов, например целые числа, со `null` значением для повышения эффективности.</span><span class="sxs-lookup"><span data-stu-id="764e4-105">This is helpful when interacting with libraries and components that may choose to represent these kinds of types, like integers, with a `null` value for efficiency reasons.</span></span> <span data-ttu-id="764e4-106">Базовый тип, поддерживающий эту конструкцию, — <xref:System.Nullable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="764e4-106">The underlying type that backs this construct is <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span>

## <a name="syntax"></a><span data-ttu-id="764e4-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="764e4-107">Syntax</span></span>

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a><span data-ttu-id="764e4-108">Объявление и присваивание со значениями</span><span class="sxs-lookup"><span data-stu-id="764e4-108">Declare and assign with values</span></span>

<span data-ttu-id="764e4-109">Объявление типа значения, допускающего значение null, аналогично объявлению любого типа, подобного оболочке, в F #:</span><span class="sxs-lookup"><span data-stu-id="764e4-109">Declaring a nullable value type is just like declaring any wrapper-like type in F#:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

<span data-ttu-id="764e4-110">Можно также елиде параметр универсального типа и разрешить вывод типа для его разрешения:</span><span class="sxs-lookup"><span data-stu-id="764e4-110">You can also elide the generic type parameter and allow type inference to resolve it:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

<span data-ttu-id="764e4-111">Чтобы присвоить тип значения, допускающего значение null, необходимо также быть явным.</span><span class="sxs-lookup"><span data-stu-id="764e4-111">To assign to a nullable value type, you'll need to also be explicit.</span></span> <span data-ttu-id="764e4-112">Не существует неявного преобразования для определенных в F # типов значений, допускающих значения NULL:</span><span class="sxs-lookup"><span data-stu-id="764e4-112">There is no implicit conversion for F#-defined nullable value types:</span></span>

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a><span data-ttu-id="764e4-113">Присвоить значение null</span><span class="sxs-lookup"><span data-stu-id="764e4-113">Assign null</span></span>

<span data-ttu-id="764e4-114">Нельзя напрямую присвоить `null` тип значения, допускающего значение null.</span><span class="sxs-lookup"><span data-stu-id="764e4-114">You cannot directly assign `null` to a nullable value type.</span></span> <span data-ttu-id="764e4-115">`Nullable()`Вместо этого используйте:</span><span class="sxs-lookup"><span data-stu-id="764e4-115">Use `Nullable()` instead:</span></span>

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

<span data-ttu-id="764e4-116">Это вызвано тем, что `Nullable<'T>` имеет `null` неправильное значение.</span><span class="sxs-lookup"><span data-stu-id="764e4-116">This is because `Nullable<'T>` does not have `null` as a proper value.</span></span>

## <a name="pass-and-assign-to-members"></a><span data-ttu-id="764e4-117">Передача и назначение членам</span><span class="sxs-lookup"><span data-stu-id="764e4-117">Pass and assign to members</span></span>

<span data-ttu-id="764e4-118">Основное различие между работой с членами и значениями F # заключается в том, что типы значений, допускающие значение null, могут быть неявно выведены при работе с членами.</span><span class="sxs-lookup"><span data-stu-id="764e4-118">A key difference between working with members and F# values is that nullable value types can be implicitly inferred when you're working with members.</span></span> <span data-ttu-id="764e4-119">Рассмотрим следующий метод, принимающий тип значения Nullable в качестве входных данных:</span><span class="sxs-lookup"><span data-stu-id="764e4-119">Consider the following method that takes a nullable value type as input:</span></span>

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

<span data-ttu-id="764e4-120">В предыдущем примере можно передать `12` методу `M` .</span><span class="sxs-lookup"><span data-stu-id="764e4-120">In the previous example, you can pass `12` to the method `M`.</span></span> <span data-ttu-id="764e4-121">Также можно присвоить значение `12` свойству Auto `NVT` .</span><span class="sxs-lookup"><span data-stu-id="764e4-121">You can also assign `12` to the auto property `NVT`.</span></span> <span data-ttu-id="764e4-122">Если входные данные могут быть сконструированы как тип значения, допускающего значение null, и соответствует целевому типу, компилятор F # будет неявно преобразовывать такие вызовы или назначения.</span><span class="sxs-lookup"><span data-stu-id="764e4-122">If the input can be constructed as a nullable value type and it matches the target type, the F# compiler will implicitly convert such calls or assignments.</span></span>

## <a name="examine-a-nullable-value-type-instance"></a><span data-ttu-id="764e4-123">Проверка экземпляра типа значения, допускающего значение null</span><span class="sxs-lookup"><span data-stu-id="764e4-123">Examine a nullable value type instance</span></span>

<span data-ttu-id="764e4-124">В отличие от [параметров](options.md), которые являются обобщенной конструкцией для представления возможного значения, типы значений, допускающие значение null, не используются при сопоставлении шаблонов.</span><span class="sxs-lookup"><span data-stu-id="764e4-124">Unlike [Options](options.md), which are a generalized construct for representing a possible value, nullable value types are not used with pattern matching.</span></span> <span data-ttu-id="764e4-125">Вместо этого необходимо использовать [`if`](conditional-expressions-if-then-else.md) выражение и проверить `HasValue` свойство.</span><span class="sxs-lookup"><span data-stu-id="764e4-125">Instead, you need to use an [`if`](conditional-expressions-if-then-else.md) expression and check the `HasValue` property.</span></span>

<span data-ttu-id="764e4-126">Чтобы получить базовое значение, используйте `Value` свойство после `HasValue` проверки, например так:</span><span class="sxs-lookup"><span data-stu-id="764e4-126">To get the underlying value, use the `Value` property after a `HasValue` check, like so:</span></span>

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a><span data-ttu-id="764e4-127">Операторы, допускающие значение null</span><span class="sxs-lookup"><span data-stu-id="764e4-127">Nullable operators</span></span>

<span data-ttu-id="764e4-128">Операции с типами значений, допускающими значения NULL, такие как арифметическое или сравнение, могут потребовать использования [операторов, допускающих значение NULL](symbol-and-operator-reference/nullable-operators.md).</span><span class="sxs-lookup"><span data-stu-id="764e4-128">Operations on nullable value types, such as arithmetic or comparison, can require the use of [nullable operators](symbol-and-operator-reference/nullable-operators.md).</span></span>

<span data-ttu-id="764e4-129">Можно преобразовать из одного типа значений, допускающего значение null, в другой с помощью операторов преобразования из `FSharp.Linq` пространства имен:</span><span class="sxs-lookup"><span data-stu-id="764e4-129">You can convert from one nullable value type to another using conversion operators from the `FSharp.Linq` namespace:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

<span data-ttu-id="764e4-130">Можно также использовать соответствующий оператор, не допускающий значения NULL, для преобразования в примитивный тип, если он не имеет значения:</span><span class="sxs-lookup"><span data-stu-id="764e4-130">You can also use an appropriate non-nullable operator to convert to a primitive type, risking an exception if it has no value:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

<span data-ttu-id="764e4-131">Можно также использовать операторы Nullable в качестве короткого оператора для проверки `HasValue` и `Value` :</span><span class="sxs-lookup"><span data-stu-id="764e4-131">You can also use nullable operators as a short-hand for checking `HasValue` and `Value`:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

<span data-ttu-id="764e4-132">`?>`Сравнение проверяет, является ли левая часть значения NULL, и только если она имеет значение.</span><span class="sxs-lookup"><span data-stu-id="764e4-132">The `?>` comparison checks if the left-hand side is nullable and only succeeds if it has a value.</span></span> <span data-ttu-id="764e4-133">Он эквивалентен строке, следующей за ней.</span><span class="sxs-lookup"><span data-stu-id="764e4-133">It is equivalent to the line that follows it.</span></span>

## <a name="see-also"></a><span data-ttu-id="764e4-134">См. также</span><span class="sxs-lookup"><span data-stu-id="764e4-134">See also</span></span>

- [<span data-ttu-id="764e4-135">Структуры</span><span class="sxs-lookup"><span data-stu-id="764e4-135">Structures</span></span>](structures.md)
- [<span data-ttu-id="764e4-136">Параметры F #</span><span class="sxs-lookup"><span data-stu-id="764e4-136">F# Options</span></span>](options.md)
