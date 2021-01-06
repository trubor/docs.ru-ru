---
title: Записи
description: 'Узнайте, как записи F # представляют простые статистические выражения именованных значений, при необходимости с элементами.'
ms.date: 08/15/2020
ms.openlocfilehash: 2da31da0ec830d458a370e64ca105048181f5d74
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899643"
---
# <a name="records"></a><span data-ttu-id="4cc08-103">Записи</span><span class="sxs-lookup"><span data-stu-id="4cc08-103">Records</span></span>

<span data-ttu-id="4cc08-104">Записи представляют собой простые агрегаты именованных значений, которые могут иметь элементы.</span><span class="sxs-lookup"><span data-stu-id="4cc08-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="4cc08-105">Они могут быть либо структурами, либо ссылочными типами.</span><span class="sxs-lookup"><span data-stu-id="4cc08-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="4cc08-106">По умолчанию они являются ссылочными типами.</span><span class="sxs-lookup"><span data-stu-id="4cc08-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cc08-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4cc08-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="4cc08-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="4cc08-108">Remarks</span></span>

<span data-ttu-id="4cc08-109">В предыдущем синтаксисе *TypeName* — это имя типа записи, *Label1* и *ярлык2* — имена значений, называемые *метками*, а *Type1* и *тип2* — типы этих значений.</span><span class="sxs-lookup"><span data-stu-id="4cc08-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="4cc08-110">*member-list* — это необязательный список элементов для типа.</span><span class="sxs-lookup"><span data-stu-id="4cc08-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="4cc08-111">Атрибут можно использовать `[<Struct>]` для создания записи структуры, а не для записи, которая является ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="4cc08-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="4cc08-112">Ниже приводятся некоторые примеры.</span><span class="sxs-lookup"><span data-stu-id="4cc08-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="4cc08-113">Если каждая метка находится в отдельной строке, точка с запятой является необязательной.</span><span class="sxs-lookup"><span data-stu-id="4cc08-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="4cc08-114">Значения можно задавать в выражениях, называемых *выражениями записи*.</span><span class="sxs-lookup"><span data-stu-id="4cc08-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="4cc08-115">Компилятор выводит тип из используемых меток (если метки достаточно отличаются от других типов записей).</span><span class="sxs-lookup"><span data-stu-id="4cc08-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="4cc08-116">Фигурные скобки ({}) заключают выражение записи.</span><span class="sxs-lookup"><span data-stu-id="4cc08-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="4cc08-117">В следующем коде показано выражение записи, которое инициализирует запись с тремя элементами с плавающей запятой с метками `x` `y` и `z` .</span><span class="sxs-lookup"><span data-stu-id="4cc08-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="4cc08-118">Не используйте сокращенную форму, если возможно наличие другого типа, который также имеет одинаковые метки.</span><span class="sxs-lookup"><span data-stu-id="4cc08-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="4cc08-119">Метки последнего объявленного типа имеют приоритет над элементами ранее объявленного типа, поэтому в предыдущем примере `mypoint3D` выводится как `Point3D` .</span><span class="sxs-lookup"><span data-stu-id="4cc08-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="4cc08-120">Можно явно указать тип записи, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4cc08-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="4cc08-121">Методы могут быть определены для типов записей так же, как для типов классов.</span><span class="sxs-lookup"><span data-stu-id="4cc08-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="4cc08-122">Создание записей с помощью выражений записи</span><span class="sxs-lookup"><span data-stu-id="4cc08-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="4cc08-123">Можно инициализировать записи с помощью меток, определенных в записи.</span><span class="sxs-lookup"><span data-stu-id="4cc08-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="4cc08-124">Выражение, которое делает это, называется *выражением записи*.</span><span class="sxs-lookup"><span data-stu-id="4cc08-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="4cc08-125">Используйте фигурные скобки, чтобы заключить выражение записи и использовать точку с запятой в качестве разделителя.</span><span class="sxs-lookup"><span data-stu-id="4cc08-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="4cc08-126">В следующем примере показано, как создать запись.</span><span class="sxs-lookup"><span data-stu-id="4cc08-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="4cc08-127">Точки с запятой после последнего поля в выражении записи и в определении типа являются необязательными независимо от того, все ли поля находятся в одной строке.</span><span class="sxs-lookup"><span data-stu-id="4cc08-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="4cc08-128">При создании записи необходимо указать значения для каждого поля.</span><span class="sxs-lookup"><span data-stu-id="4cc08-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="4cc08-129">Нельзя ссылаться на значения других полей в выражении инициализации для любого поля.</span><span class="sxs-lookup"><span data-stu-id="4cc08-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="4cc08-130">В следующем коде тип `myRecord2` выводится из имен полей.</span><span class="sxs-lookup"><span data-stu-id="4cc08-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="4cc08-131">При необходимости можно явно указать имя типа.</span><span class="sxs-lookup"><span data-stu-id="4cc08-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="4cc08-132">Другая форма создания записи может быть полезной, если необходимо скопировать существующую запись и, возможно, изменить некоторые значения полей.</span><span class="sxs-lookup"><span data-stu-id="4cc08-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="4cc08-133">Это показано в следующей строке кода.</span><span class="sxs-lookup"><span data-stu-id="4cc08-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="4cc08-134">Эта форма выражения записи называется *выражением копирования и обновления записи*.</span><span class="sxs-lookup"><span data-stu-id="4cc08-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="4cc08-135">По умолчанию записи являются неизменяемыми; Однако вы можете легко создавать измененные записи с помощью выражения копирования и обновления.</span><span class="sxs-lookup"><span data-stu-id="4cc08-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="4cc08-136">Можно также явно указать изменяемое поле.</span><span class="sxs-lookup"><span data-stu-id="4cc08-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="4cc08-137">Не используйте атрибут DefaultValue с полями записей.</span><span class="sxs-lookup"><span data-stu-id="4cc08-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="4cc08-138">Лучшим подходом является определение экземпляров по умолчанию для записей с полями, которые инициализируются значениями по умолчанию, а затем использование выражения копирования и обновления записей для установки любых полей, которые отличаются от значений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4cc08-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="4cc08-139">Создание взаимно рекурсивных записей</span><span class="sxs-lookup"><span data-stu-id="4cc08-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="4cc08-140">Иногда при создании записи может потребоваться, чтобы она зависела от другого типа, который вы хотите определить позже.</span><span class="sxs-lookup"><span data-stu-id="4cc08-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="4cc08-141">Это ошибка компиляции, если не определить типы записей для взаимной рекурсивной рекурсии.</span><span class="sxs-lookup"><span data-stu-id="4cc08-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="4cc08-142">Определение взаимно рекурсивных записей выполняется с помощью `and` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="4cc08-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="4cc08-143">Это позволяет связать 2 или более типов записей вместе.</span><span class="sxs-lookup"><span data-stu-id="4cc08-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="4cc08-144">Например, следующий код определяет `Person` `Address` тип и как взаимно рекурсивный:</span><span class="sxs-lookup"><span data-stu-id="4cc08-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

<span data-ttu-id="4cc08-145">Если бы вы определили предыдущий пример без `and` ключевого слова, он не будет компилироваться.</span><span class="sxs-lookup"><span data-stu-id="4cc08-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="4cc08-146">`and`Для взаимно рекурсивных определений требуется ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="4cc08-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="4cc08-147">Сопоставление шаблонов с записями</span><span class="sxs-lookup"><span data-stu-id="4cc08-147">Pattern Matching with Records</span></span>

<span data-ttu-id="4cc08-148">Записи можно использовать с сопоставлением шаблонов.</span><span class="sxs-lookup"><span data-stu-id="4cc08-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="4cc08-149">Можно явно указать некоторые поля и предоставить переменные для других полей, которые будут назначаться при совпадении.</span><span class="sxs-lookup"><span data-stu-id="4cc08-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="4cc08-150">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="4cc08-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="4cc08-151">Выходные данные этого кода выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="4cc08-151">The output of this code is as follows.</span></span>

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a><span data-ttu-id="4cc08-152">Записи и члены</span><span class="sxs-lookup"><span data-stu-id="4cc08-152">Records and members</span></span>

<span data-ttu-id="4cc08-153">Вы можете указать элементы в записях так же, как и с классами.</span><span class="sxs-lookup"><span data-stu-id="4cc08-153">You can specify members on records much like you can with classes.</span></span> <span data-ttu-id="4cc08-154">Поля не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4cc08-154">There is no support for fields.</span></span> <span data-ttu-id="4cc08-155">Распространенный подход заключается в определении `Default` статического члена для простоты создания записей:</span><span class="sxs-lookup"><span data-stu-id="4cc08-155">A common approach is to define a `Default` static member for easy record construction:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

<span data-ttu-id="4cc08-156">При использовании собственного идентификатора этот идентификатор ссылается на экземпляр записи, членом которой является:</span><span class="sxs-lookup"><span data-stu-id="4cc08-156">If you use a self identifier, that identifier refers to the instance of the record whose member is called:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123" }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="4cc08-157">Различия между записями и классами</span><span class="sxs-lookup"><span data-stu-id="4cc08-157">Differences Between Records and Classes</span></span>

<span data-ttu-id="4cc08-158">Поля записей отличаются от полей классов тем, что они автоматически предоставляются как свойства и используются при создании и копировании записей.</span><span class="sxs-lookup"><span data-stu-id="4cc08-158">Record fields differ from class fields in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="4cc08-159">Построение записей также отличается от создания класса.</span><span class="sxs-lookup"><span data-stu-id="4cc08-159">Record construction also differs from class construction.</span></span> <span data-ttu-id="4cc08-160">В типе записи нельзя определить конструктор.</span><span class="sxs-lookup"><span data-stu-id="4cc08-160">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="4cc08-161">Вместо этого применяется синтаксис создания, описанный в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="4cc08-161">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="4cc08-162">Классы не имеют прямой связи между параметрами конструктора, полями и свойствами.</span><span class="sxs-lookup"><span data-stu-id="4cc08-162">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="4cc08-163">Как и типы Union и Structure, записи имеют семантику структурного равенства.</span><span class="sxs-lookup"><span data-stu-id="4cc08-163">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="4cc08-164">Классы имеют семантику равенства ссылок.</span><span class="sxs-lookup"><span data-stu-id="4cc08-164">Classes have reference equality semantics.</span></span> <span data-ttu-id="4cc08-165">Это действие представлено в следующем примере кода:</span><span class="sxs-lookup"><span data-stu-id="4cc08-165">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="4cc08-166">Результат выполнения этого кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4cc08-166">The output of this code is as follows:</span></span>

```console
The records are equal.
```

<span data-ttu-id="4cc08-167">Если написать тот же код с классами, то два объекта класса будут неравными, так как два значения будут представлять два объекта в куче и будут сравниваться только адреса (если только тип класса не переопределит `System.Object.Equals` метод).</span><span class="sxs-lookup"><span data-stu-id="4cc08-167">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="4cc08-168">Если для записей требуется равенство ссылок, добавьте атрибут `[<ReferenceEquality>]` над записью.</span><span class="sxs-lookup"><span data-stu-id="4cc08-168">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cc08-169">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4cc08-169">See also</span></span>

- [<span data-ttu-id="4cc08-170">Типы языка F#</span><span class="sxs-lookup"><span data-stu-id="4cc08-170">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="4cc08-171">Классы</span><span class="sxs-lookup"><span data-stu-id="4cc08-171">Classes</span></span>](classes.md)
- [<span data-ttu-id="4cc08-172">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="4cc08-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4cc08-173">Равенство ссылок</span><span class="sxs-lookup"><span data-stu-id="4cc08-173">Reference-Equality</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [<span data-ttu-id="4cc08-174">Соответствие шаблону</span><span class="sxs-lookup"><span data-stu-id="4cc08-174">Pattern Matching</span></span>](pattern-matching.md)
