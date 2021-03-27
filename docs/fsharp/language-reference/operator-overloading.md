---
title: Перегрузка операторов
description: 'Узнайте, как перегружать арифметические операторы в классе или типе записи и на глобальном уровне в F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 64ff87a8706e6a05754b5328a7d95cd6a2b360c1
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610854"
---
# <a name="operator-overloading"></a><span data-ttu-id="8574c-103">Перегрузка операторов</span><span class="sxs-lookup"><span data-stu-id="8574c-103">Operator Overloading</span></span>

<span data-ttu-id="8574c-104">В этом разделе описывается перегрузка арифметических операторов в классе или типе записи, а также на глобальном уровне.</span><span class="sxs-lookup"><span data-stu-id="8574c-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="8574c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8574c-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="8574c-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="8574c-106">Remarks</span></span>

<span data-ttu-id="8574c-107">В предыдущем синтаксисе *оператор-Symbol* является одним из `+` ,,, `-` `*` `/` , `=` и т. д.</span><span class="sxs-lookup"><span data-stu-id="8574c-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="8574c-108">*Параметр-List* задает операнды в том порядке, в котором они отображаются в обычном синтаксисе для этого оператора.</span><span class="sxs-lookup"><span data-stu-id="8574c-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="8574c-109">*Метод-Body* конструирует результирующее значение.</span><span class="sxs-lookup"><span data-stu-id="8574c-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="8574c-110">Перегрузки операторов для операторов должны быть статическими.</span><span class="sxs-lookup"><span data-stu-id="8574c-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="8574c-111">Перегрузки операторов для унарных операторов, таких как `+` и `-` , должны использовать символ тильды ( `~` ) в *операторе-Symbol* , чтобы указать, что оператор является унарным оператором, а не бинарным оператором, как показано в следующем объявлении.</span><span class="sxs-lookup"><span data-stu-id="8574c-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="8574c-112">В следующем коде показан класс Vector, имеющий только два оператора: один для унарного минуса и один для умножения скаляром.</span><span class="sxs-lookup"><span data-stu-id="8574c-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="8574c-113">В этом примере требуется две перегрузки для скалярного умножения, так как оператор должен работать независимо от порядка, в котором отображаются Vector и scalar.</span><span class="sxs-lookup"><span data-stu-id="8574c-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="8574c-114">Создание новых операторов</span><span class="sxs-lookup"><span data-stu-id="8574c-114">Creating New Operators</span></span>

<span data-ttu-id="8574c-115">Можно перегружать все стандартные операторы, но можно также создавать новые операторы из последовательностей определенных символов.</span><span class="sxs-lookup"><span data-stu-id="8574c-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="8574c-116">Допустимые символы оператора: `!` , `$` ,,, `%` `&` `*` , `+` , `-` , `.` , `/` , `<` , `=` , `>` , `?` , `@` , `^` , `|` и `~` .</span><span class="sxs-lookup"><span data-stu-id="8574c-116">Allowed operator characters are `!`, `$`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="8574c-117">`~`Символ имеет особое значение, что делает оператор унарным и не является частью последовательности символов оператора.</span><span class="sxs-lookup"><span data-stu-id="8574c-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="8574c-118">Не все операторы можно сделать унарными.</span><span class="sxs-lookup"><span data-stu-id="8574c-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="8574c-119">В зависимости от того, какая последовательность символов используется, оператор будет иметь определенный приоритет и ассоциативность.</span><span class="sxs-lookup"><span data-stu-id="8574c-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="8574c-120">Ассоциативность может быть либо слева направо, либо справа налево, и используется всякий раз, когда операторы одного и того же уровня приоритета отображаются в последовательности без скобок.</span><span class="sxs-lookup"><span data-stu-id="8574c-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="8574c-121">Символ оператора не `.` влияет на приоритет, поэтому, например, если требуется определить собственную версию умножения, имеющую тот же приоритет и ассоциативность, что и обычное умножение, можно создать такие операторы, как `.*` .</span><span class="sxs-lookup"><span data-stu-id="8574c-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="8574c-122">Только операторы `?` и `?<-` могут начинаться с `?` .</span><span class="sxs-lookup"><span data-stu-id="8574c-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="8574c-123">`$`Оператор должен быть изолированным и без дополнительных символов.</span><span class="sxs-lookup"><span data-stu-id="8574c-123">The `$` operator must stand alone and without additional symbols.</span></span>

<span data-ttu-id="8574c-124">Таблица, в которой показан приоритет всех операторов в F #, можно найти в [справочнике по символам и операторам](./symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="8574c-124">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="8574c-125">Имена перегруженных операторов</span><span class="sxs-lookup"><span data-stu-id="8574c-125">Overloaded Operator Names</span></span>

<span data-ttu-id="8574c-126">Когда компилятор F # компилирует выражение оператора, он создает метод с именем, созданным компилятором для этого оператора.</span><span class="sxs-lookup"><span data-stu-id="8574c-126">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="8574c-127">Это имя, которое отображается на языке MSIL для метода, а также в отражении и IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8574c-127">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="8574c-128">Обычно вам не нужно использовать эти имена в коде F #.</span><span class="sxs-lookup"><span data-stu-id="8574c-128">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="8574c-129">В следующей таблице показаны стандартные операторы и соответствующие им созданные имена.</span><span class="sxs-lookup"><span data-stu-id="8574c-129">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="8574c-130">Оператор</span><span class="sxs-lookup"><span data-stu-id="8574c-130">Operator</span></span>|<span data-ttu-id="8574c-131">Созданное имя</span><span class="sxs-lookup"><span data-stu-id="8574c-131">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

<span data-ttu-id="8574c-132">Обратите внимание, что `not` оператор в F # не выдается, `op_Inequality` так как он не является символом-оператором.</span><span class="sxs-lookup"><span data-stu-id="8574c-132">Note that the `not` operator in F# does not emit `op_Inequality` because it is not a symbolic operator.</span></span> <span data-ttu-id="8574c-133">Это функция, которая создает IL, который Инвертирует логическое выражение.</span><span class="sxs-lookup"><span data-stu-id="8574c-133">It is a function that emits IL that negates a boolean expression.</span></span>

<span data-ttu-id="8574c-134">Другие сочетания символов операторов, которые не перечислены здесь, могут использоваться в качестве операторов и иметь имена, которые объединяются путем объединения имен для отдельных символов из следующей таблицы.</span><span class="sxs-lookup"><span data-stu-id="8574c-134">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="8574c-135">Например, +!</span><span class="sxs-lookup"><span data-stu-id="8574c-135">For example, +!</span></span> <span data-ttu-id="8574c-136"> превращается в `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="8574c-136">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="8574c-137">Символ оператора</span><span class="sxs-lookup"><span data-stu-id="8574c-137">Operator character</span></span>|<span data-ttu-id="8574c-138">Имя</span><span class="sxs-lookup"><span data-stu-id="8574c-138">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`$`|`Dollar`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="8574c-139">Операторы prefix и инфиксные</span><span class="sxs-lookup"><span data-stu-id="8574c-139">Prefix and Infix Operators</span></span>

<span data-ttu-id="8574c-140">Операторы *префикса* должны размещаться перед операндом или операндами, во многом подобно функции.</span><span class="sxs-lookup"><span data-stu-id="8574c-140">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="8574c-141">Операторы *инфиксные* должны располагаться между двумя операндами.</span><span class="sxs-lookup"><span data-stu-id="8574c-141">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="8574c-142">В качестве префиксных операторов можно использовать только определенные операторы.</span><span class="sxs-lookup"><span data-stu-id="8574c-142">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="8574c-143">Некоторые операторы всегда являются префиксными операторами, другие могут быть инфиксные или префиксом, а остальные всегда инфиксные операторами.</span><span class="sxs-lookup"><span data-stu-id="8574c-143">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="8574c-144">Операторы, которые начинаются с `!` оператора, за исключением `!=` and, `~` или повторяющихся последовательностей `~` , всегда являются префиксными операторами.</span><span class="sxs-lookup"><span data-stu-id="8574c-144">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="8574c-145">Операторы,,,,,, `+` `-` `+.` `-.` `&` `&&` `%` и `%%` могут быть префиксными операторами или операторами инфиксные.</span><span class="sxs-lookup"><span data-stu-id="8574c-145">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="8574c-146">Префиксную версию этих операторов можно отличить от версии инфиксные, добавляя в `~` начале префиксного оператора, когда он определен.</span><span class="sxs-lookup"><span data-stu-id="8574c-146">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="8574c-147">`~`Не используется при использовании оператора, только если он определен.</span><span class="sxs-lookup"><span data-stu-id="8574c-147">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="8574c-148">Пример</span><span class="sxs-lookup"><span data-stu-id="8574c-148">Example</span></span>

<span data-ttu-id="8574c-149">В следующем коде показано использование перегрузки операторов для реализации типа дробной части.</span><span class="sxs-lookup"><span data-stu-id="8574c-149">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="8574c-150">Дробная часть представляется числителем и знаменателем.</span><span class="sxs-lookup"><span data-stu-id="8574c-150">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="8574c-151">Функция `hcf` используется для определения самого высокого общего фактора, который используется для сокращения дробей.</span><span class="sxs-lookup"><span data-stu-id="8574c-151">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="8574c-152">**Выходные данные:**</span><span class="sxs-lookup"><span data-stu-id="8574c-152">**Output:**</span></span>

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="8574c-153">Операторы на глобальном уровне</span><span class="sxs-lookup"><span data-stu-id="8574c-153">Operators at the Global Level</span></span>

<span data-ttu-id="8574c-154">Операторы также можно определять на глобальном уровне.</span><span class="sxs-lookup"><span data-stu-id="8574c-154">You can also define operators at the global level.</span></span> <span data-ttu-id="8574c-155">В следующем коде определяется оператор `+?` .</span><span class="sxs-lookup"><span data-stu-id="8574c-155">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="8574c-156">Выходные данные приведенного выше кода имеют значение `12` .</span><span class="sxs-lookup"><span data-stu-id="8574c-156">The output of the above code is `12`.</span></span>

<span data-ttu-id="8574c-157">Таким образом, можно переопределить регулярные арифметические операторы, так как правила области для F # определяют, что новые определенные операторы имеют приоритет над встроенными операторами.</span><span class="sxs-lookup"><span data-stu-id="8574c-157">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="8574c-158">Ключевое слово `inline` часто используется с глобальными операторами, которые часто являются маленькими функциями, которые лучше всего интегрируются в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="8574c-158">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="8574c-159">Использование встроенных функций операторов также позволяет им работать с статически разрешаемыми параметрами типов для формирования статически разрешаемого универсального кода.</span><span class="sxs-lookup"><span data-stu-id="8574c-159">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="8574c-160">Дополнительные сведения см. в разделе [встроенные функции](./functions/inline-functions.md) и [статически разрешаемые параметры типа](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8574c-160">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8574c-161">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8574c-161">See also</span></span>

- [<span data-ttu-id="8574c-162">Члены</span><span class="sxs-lookup"><span data-stu-id="8574c-162">Members</span></span>](./members/index.md)
