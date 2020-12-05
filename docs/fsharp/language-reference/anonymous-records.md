---
title: Анонимные записи
description: Узнайте, как использовать конструкцию и анонимные записи — функции языка, которые помогают управлять данными.
ms.date: 06/12/2019
ms.openlocfilehash: 13950048f02ab74362f8174725f5f8615d9d7654
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739819"
---
# <a name="anonymous-records"></a><span data-ttu-id="d8a14-103">Анонимные записи</span><span class="sxs-lookup"><span data-stu-id="d8a14-103">Anonymous Records</span></span>

<span data-ttu-id="d8a14-104">Анонимные записи — это простые статистические выражения именованных значений, которые не нужно объявлять перед использованием.</span><span class="sxs-lookup"><span data-stu-id="d8a14-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="d8a14-105">Их можно объявить как структуры или ссылочные типы.</span><span class="sxs-lookup"><span data-stu-id="d8a14-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="d8a14-106">По умолчанию они являются ссылочными типами.</span><span class="sxs-lookup"><span data-stu-id="d8a14-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8a14-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8a14-107">Syntax</span></span>

<span data-ttu-id="d8a14-108">В следующих примерах демонстрируется синтаксис анонимных записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="d8a14-109">Элементы разделяются как `[item]` необязательные.</span><span class="sxs-lookup"><span data-stu-id="d8a14-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="d8a14-110">Базовое использование</span><span class="sxs-lookup"><span data-stu-id="d8a14-110">Basic usage</span></span>

<span data-ttu-id="d8a14-111">Анонимные записи лучше рассматривать как типы записей F #, которые не нужно объявлять перед созданием экземпляра.</span><span class="sxs-lookup"><span data-stu-id="d8a14-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="d8a14-112">Например, вот как можно взаимодействовать с функцией, которая создает анонимную запись:</span><span class="sxs-lookup"><span data-stu-id="d8a14-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

<span data-ttu-id="d8a14-113">В следующем примере предыдущий объект разворачивается с помощью `printCircleStats` функции, которая принимает анонимную запись в качестве входных данных:</span><span class="sxs-lookup"><span data-stu-id="d8a14-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

<span data-ttu-id="d8a14-114">Вызов `printCircleStats` с любым типом анонимных записей, который не имеет такой же "формы", как и тип входных данных, не будет компилироваться:</span><span class="sxs-lookup"><span data-stu-id="d8a14-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="d8a14-115">Анонимные записи структуры</span><span class="sxs-lookup"><span data-stu-id="d8a14-115">Struct anonymous records</span></span>

<span data-ttu-id="d8a14-116">Анонимные записи также можно определить как структуру с `struct` ключевым словом Optional.</span><span class="sxs-lookup"><span data-stu-id="d8a14-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="d8a14-117">В следующем примере предыдущий объект расширяется путем создания и использования анонимной записи структуры:</span><span class="sxs-lookup"><span data-stu-id="d8a14-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a><span data-ttu-id="d8a14-118">Определение структуры</span><span class="sxs-lookup"><span data-stu-id="d8a14-118">Structness inference</span></span>

<span data-ttu-id="d8a14-119">Анонимные записи структуры также позволяют «выведение структуры», где не нужно указывать `struct` ключевое слово в месте вызова.</span><span class="sxs-lookup"><span data-stu-id="d8a14-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="d8a14-120">В этом примере вы елиде `struct` ключевое слово при вызове `printCircleStats` :</span><span class="sxs-lookup"><span data-stu-id="d8a14-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="d8a14-121">Обратный шаблон — указывает, `struct` когда входной тип не является анонимной записью структуры, не сможет компилироваться.</span><span class="sxs-lookup"><span data-stu-id="d8a14-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="d8a14-122">Внедрение анонимных записей в другие типы</span><span class="sxs-lookup"><span data-stu-id="d8a14-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="d8a14-123">Полезно объявлять [Размеченные объединения](discriminated-unions.md) , варианты которых являются записями.</span><span class="sxs-lookup"><span data-stu-id="d8a14-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="d8a14-124">Но если данные в записях имеют тот же тип, что и размеченное объединение, необходимо определить все типы как взаимные рекурсивные.</span><span class="sxs-lookup"><span data-stu-id="d8a14-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="d8a14-125">Использование анонимных записей позволяет избежать этого ограничения.</span><span class="sxs-lookup"><span data-stu-id="d8a14-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="d8a14-126">Ниже приведен пример типа и функции, которые соответствуют шаблону:</span><span class="sxs-lookup"><span data-stu-id="d8a14-126">What follows is an example type and function that pattern matches over it:</span></span>

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named record for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a><span data-ttu-id="d8a14-127">Копирование и обновление выражений</span><span class="sxs-lookup"><span data-stu-id="d8a14-127">Copy and update expressions</span></span>

<span data-ttu-id="d8a14-128">Анонимные записи поддерживают конструкцию с [выражениями копирования и обновления](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d8a14-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="d8a14-129">Например, вот как можно создать новый экземпляр анонимной записи, который копирует существующие данные.</span><span class="sxs-lookup"><span data-stu-id="d8a14-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="d8a14-130">Однако в отличие от именованных записей анонимные записи позволяют создавать совершенно разные формы с выражениями копирования и обновления.</span><span class="sxs-lookup"><span data-stu-id="d8a14-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="d8a14-131">Следующий пример принимает ту же анонимную запись из предыдущего примера и разворачивает ее в новую анонимную запись:</span><span class="sxs-lookup"><span data-stu-id="d8a14-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="d8a14-132">Кроме того, можно создавать анонимные записи из экземпляров именованных записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="d8a14-133">Также можно скопировать данные в анонимные записи ссылок и структуры и обратно:</span><span class="sxs-lookup"><span data-stu-id="d8a14-133">You can also copy data to and from reference and struct anonymous records:</span></span>

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="d8a14-134">Свойства анонимных записей</span><span class="sxs-lookup"><span data-stu-id="d8a14-134">Properties of anonymous records</span></span>

<span data-ttu-id="d8a14-135">Анонимные записи имеют ряд характеристик, необходимых для полного понимания того, как их можно использовать.</span><span class="sxs-lookup"><span data-stu-id="d8a14-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="d8a14-136">Анонимные записи являются номинальными</span><span class="sxs-lookup"><span data-stu-id="d8a14-136">Anonymous records are nominal</span></span>

<span data-ttu-id="d8a14-137">Анонимные записи — это [Номинальные типы](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="d8a14-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="d8a14-138">Они лучше рассматривать как именованные типы [записей](records.md) (которые также являются номинальными), для которых не требуется объявление переднего плана.</span><span class="sxs-lookup"><span data-stu-id="d8a14-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="d8a14-139">Рассмотрим следующий пример с двумя анонимными объявлениями записей:</span><span class="sxs-lookup"><span data-stu-id="d8a14-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="d8a14-140">`x`Значения и `y` имеют разные типы и несовместимы друг с другом.</span><span class="sxs-lookup"><span data-stu-id="d8a14-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="d8a14-141">Они не являются сопоставимыми и не являются сравнимыми.</span><span class="sxs-lookup"><span data-stu-id="d8a14-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="d8a14-142">Чтобы проиллюстрировать это, рассмотрим эквивалент именованной записи:</span><span class="sxs-lookup"><span data-stu-id="d8a14-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="d8a14-143">При сравнении с их эквивалентами типов анонимные записи по-разному не различаются.</span><span class="sxs-lookup"><span data-stu-id="d8a14-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="d8a14-144">Анонимные записи используют структурное равенство и сравнение</span><span class="sxs-lookup"><span data-stu-id="d8a14-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="d8a14-145">Как и типы записей, анонимные записи имеют структурную равенство и сравнимы.</span><span class="sxs-lookup"><span data-stu-id="d8a14-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="d8a14-146">Это справедливо только в том случае, если все составные типы поддерживают равенство и сравнение, как и типы записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="d8a14-147">Для поддержки равенства или сравнения две анонимные записи должны иметь одинаковую форму.</span><span class="sxs-lookup"><span data-stu-id="d8a14-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="d8a14-148">Анонимные записи являются сериализуемыми</span><span class="sxs-lookup"><span data-stu-id="d8a14-148">Anonymous records are serializable</span></span>

<span data-ttu-id="d8a14-149">Можно выполнять сериализацию анонимных записей так же, как и с именованными записями.</span><span class="sxs-lookup"><span data-stu-id="d8a14-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="d8a14-150">Ниже приведен пример использования [Newtonsoft.Jsв](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="d8a14-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn $"Name: {phillip.name} Age: %d{phillip.age}"
```

<span data-ttu-id="d8a14-151">Анонимные записи полезны для отправки облегченных данных по сети без необходимости определения домена для сериализованных и десериализованных типов.</span><span class="sxs-lookup"><span data-stu-id="d8a14-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="d8a14-152">Анонимные записи взаимодействуют с анонимными типами C#</span><span class="sxs-lookup"><span data-stu-id="d8a14-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="d8a14-153">Можно использовать API-интерфейс .NET, который требует использования [анонимных типов C#](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d8a14-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="d8a14-154">Анонимные типы C# являются тривиальными для взаимодействия с с помощью анонимных записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="d8a14-155">В следующем примере показано, как использовать анонимные записи для вызова перегрузки [LINQ](../../csharp/programming-guide/concepts/linq/index.md) , для которой требуется анонимный тип:</span><span class="sxs-lookup"><span data-stu-id="d8a14-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn $"{ng.Name} has first letter {ng.FirstLetter}"
```

<span data-ttu-id="d8a14-156">Существует множество других API-интерфейсов, используемых в .NET, требующих передачи анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="d8a14-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="d8a14-157">Анонимные записи — это средство для работы с ними.</span><span class="sxs-lookup"><span data-stu-id="d8a14-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="d8a14-158">Ограничения</span><span class="sxs-lookup"><span data-stu-id="d8a14-158">Limitations</span></span>

<span data-ttu-id="d8a14-159">Анонимные записи имеют некоторые ограничения в их использовании.</span><span class="sxs-lookup"><span data-stu-id="d8a14-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="d8a14-160">Некоторые из них относятся к их проектированию, но другие податлива.</span><span class="sxs-lookup"><span data-stu-id="d8a14-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="d8a14-161">Ограничения, связанные с сопоставлением шаблонов</span><span class="sxs-lookup"><span data-stu-id="d8a14-161">Limitations with pattern matching</span></span>

<span data-ttu-id="d8a14-162">Анонимные записи не поддерживают сопоставление шаблонов, в отличие от именованных записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="d8a14-163">Существует три причины.</span><span class="sxs-lookup"><span data-stu-id="d8a14-163">There are three reasons:</span></span>

1. <span data-ttu-id="d8a14-164">Шаблон должен учитывать каждое поле анонимной записи, в отличие от именованных типов записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="d8a14-165">Это обусловлено тем, что анонимные записи не поддерживают структурную подтипизацию — они являются номинальными типами.</span><span class="sxs-lookup"><span data-stu-id="d8a14-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="d8a14-166">Из-за (1) нет возможности иметь дополнительные шаблоны в выражении соответствия шаблону, так как каждый отдельный шаблон подразумевает другой анонимный тип записи.</span><span class="sxs-lookup"><span data-stu-id="d8a14-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="d8a14-167">Из-за (3) любой анонимный шаблон записи будет более подробным, чем использование нотации "точка".</span><span class="sxs-lookup"><span data-stu-id="d8a14-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="d8a14-168">Существует предложение Open Language, позволяющее [сопоставлять шаблоны в ограниченных контекстах](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="d8a14-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="d8a14-169">Ограничения с изменяемостью</span><span class="sxs-lookup"><span data-stu-id="d8a14-169">Limitations with mutability</span></span>

<span data-ttu-id="d8a14-170">В настоящее время невозможно определить анонимную запись с `mutable` данными.</span><span class="sxs-lookup"><span data-stu-id="d8a14-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="d8a14-171">Существует [предложение Open Language](https://github.com/fsharp/fslang-suggestions/issues/732) , разрешающее изменяющиеся данные.</span><span class="sxs-lookup"><span data-stu-id="d8a14-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="d8a14-172">Ограничения для анонимных записей структуры</span><span class="sxs-lookup"><span data-stu-id="d8a14-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="d8a14-173">Нельзя объявлять анонимные записи структуры как `IsByRefLike` или `IsReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="d8a14-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="d8a14-174">Существует [предложение Open Language](https://github.com/fsharp/fslang-suggestions/issues/712) для `IsByRefLike` `IsReadOnly` анонимных записей.</span><span class="sxs-lookup"><span data-stu-id="d8a14-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
