---
title: Сопоставление шаблонов
description: 'Узнайте, как шаблоны используются в F # для сравнения данных с логическими структурами, разложения данных на составляющие части или извлечения информации из данных.'
ms.date: 11/12/2020
ms.openlocfilehash: 932f50b7947f6df728149437dd3ceb19c42e5c6a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740280"
---
# <a name="pattern-matching"></a><span data-ttu-id="1a802-103">Сопоставление шаблонов</span><span class="sxs-lookup"><span data-stu-id="1a802-103">Pattern Matching</span></span>

<span data-ttu-id="1a802-104">Шаблоны — это правила для преобразования входных данных.</span><span class="sxs-lookup"><span data-stu-id="1a802-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="1a802-105">Они используются на любом языке F # для сравнения данных с логической структурой или структурами, разложения данных на составляющие части или извлечения информации из данных различными способами.</span><span class="sxs-lookup"><span data-stu-id="1a802-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a802-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a802-106">Remarks</span></span>

<span data-ttu-id="1a802-107">Шаблоны используются во многих языковых конструкциях, таких как `match` выражение.</span><span class="sxs-lookup"><span data-stu-id="1a802-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="1a802-108">Они используются при обработке аргументов для функций в `let` привязках, лямбда-выражениях и в обработчиках исключений, связанных с `try...with` выражением.</span><span class="sxs-lookup"><span data-stu-id="1a802-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="1a802-109">Дополнительные сведения см. в разделе [выражения Match](match-expressions.md), [Привязка let](./functions/let-bindings.md), [лямбда-выражения: `fun` ключевое слово](./functions/lambda-expressions-the-fun-keyword.md)и [исключения: `try...with` выражение](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1a802-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="1a802-110">Например, в `match` выражении *шаблон* соответствует символу вертикальной черты.</span><span class="sxs-lookup"><span data-stu-id="1a802-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="1a802-111">Каждый шаблон выступает в качестве правила для преобразования входных данных каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="1a802-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="1a802-112">В `match` выражении каждый шаблон рассматривается в, в свою очередь, для того, чтобы проверить, совместимы ли входные данные с шаблоном.</span><span class="sxs-lookup"><span data-stu-id="1a802-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="1a802-113">При обнаружении совпадения выполняется результирующее выражение.</span><span class="sxs-lookup"><span data-stu-id="1a802-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="1a802-114">Если совпадение не найдено, проверяется следующее правило шаблона.</span><span class="sxs-lookup"><span data-stu-id="1a802-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="1a802-115">Необязательная часть *условия* when объясняется в [выражениях Match](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1a802-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="1a802-116">Поддерживаемые шаблоны показаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="1a802-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="1a802-117">Во время выполнения входные данные тестируются по каждому из следующих шаблонов в порядке, указанном в таблице, а шаблоны применяются рекурсивно, от первого до последнего, как они отображаются в коде, и слева направо для шаблонов в каждой строке.</span><span class="sxs-lookup"><span data-stu-id="1a802-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="1a802-118">Имя</span><span class="sxs-lookup"><span data-stu-id="1a802-118">Name</span></span>|<span data-ttu-id="1a802-119">Описание</span><span class="sxs-lookup"><span data-stu-id="1a802-119">Description</span></span>|<span data-ttu-id="1a802-120">Пример</span><span class="sxs-lookup"><span data-stu-id="1a802-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="1a802-121">Шаблон константы</span><span class="sxs-lookup"><span data-stu-id="1a802-121">Constant pattern</span></span>|<span data-ttu-id="1a802-122">Любой числовой, символьный или строковый литерал, константа перечисления или определенный литеральный идентификатор</span><span class="sxs-lookup"><span data-stu-id="1a802-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="1a802-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="1a802-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="1a802-124">Шаблон идентификатора</span><span class="sxs-lookup"><span data-stu-id="1a802-124">Identifier pattern</span></span>|<span data-ttu-id="1a802-125">Значение варианта для размеченного объединения, метки исключения или активного варианта шаблона</span><span class="sxs-lookup"><span data-stu-id="1a802-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="1a802-126">Шаблон переменной</span><span class="sxs-lookup"><span data-stu-id="1a802-126">Variable pattern</span></span>|<span data-ttu-id="1a802-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="1a802-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="1a802-128">`as` пакет</span><span class="sxs-lookup"><span data-stu-id="1a802-128">`as` pattern</span></span>|<span data-ttu-id="1a802-129">*шаблон* в качестве *идентификатора*</span><span class="sxs-lookup"><span data-stu-id="1a802-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="1a802-130">ИЛИ шаблон</span><span class="sxs-lookup"><span data-stu-id="1a802-130">OR pattern</span></span>|<span data-ttu-id="1a802-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="1a802-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="1a802-132">И шаблон</span><span class="sxs-lookup"><span data-stu-id="1a802-132">AND pattern</span></span>|<span data-ttu-id="1a802-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="1a802-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="1a802-134">Шаблон «против»</span><span class="sxs-lookup"><span data-stu-id="1a802-134">Cons pattern</span></span>|<span data-ttu-id="1a802-135">*идентификатор* :: *List-identifier*</span><span class="sxs-lookup"><span data-stu-id="1a802-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="1a802-136">Шаблон списка</span><span class="sxs-lookup"><span data-stu-id="1a802-136">List pattern</span></span>|<span data-ttu-id="1a802-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="1a802-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="1a802-138">Шаблон массива</span><span class="sxs-lookup"><span data-stu-id="1a802-138">Array pattern</span></span>|<span data-ttu-id="1a802-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="1a802-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="1a802-140">Шаблон в круглых скобках</span><span class="sxs-lookup"><span data-stu-id="1a802-140">Parenthesized pattern</span></span>|<span data-ttu-id="1a802-141">( *шаблон* )</span><span class="sxs-lookup"><span data-stu-id="1a802-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="1a802-142">Шаблон кортежа</span><span class="sxs-lookup"><span data-stu-id="1a802-142">Tuple pattern</span></span>|<span data-ttu-id="1a802-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="1a802-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="1a802-144">Шаблон записи</span><span class="sxs-lookup"><span data-stu-id="1a802-144">Record pattern</span></span>|<span data-ttu-id="1a802-145">{ *идентификатор1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="1a802-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="1a802-146">Шаблон подстановочного знака</span><span class="sxs-lookup"><span data-stu-id="1a802-146">Wildcard pattern</span></span>|<span data-ttu-id="1a802-147">_</span><span class="sxs-lookup"><span data-stu-id="1a802-147">_</span></span>|`_`|
|<span data-ttu-id="1a802-148">Шаблон вместе с аннотацией типа</span><span class="sxs-lookup"><span data-stu-id="1a802-148">Pattern together with type annotation</span></span>|<span data-ttu-id="1a802-149">*шаблон* : *тип*</span><span class="sxs-lookup"><span data-stu-id="1a802-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="1a802-150">Шаблон проверки типа</span><span class="sxs-lookup"><span data-stu-id="1a802-150">Type test pattern</span></span>|<span data-ttu-id="1a802-151">:?</span><span class="sxs-lookup"><span data-stu-id="1a802-151">:?</span></span> <span data-ttu-id="1a802-152">*введите* [как *идентификатор* ]</span><span class="sxs-lookup"><span data-stu-id="1a802-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="1a802-153">Шаблон NULL</span><span class="sxs-lookup"><span data-stu-id="1a802-153">Null pattern</span></span>|<span data-ttu-id="1a802-154">null</span><span class="sxs-lookup"><span data-stu-id="1a802-154">null</span></span>|`null`|
|<span data-ttu-id="1a802-155">Шаблон NameOf</span><span class="sxs-lookup"><span data-stu-id="1a802-155">Nameof pattern</span></span>|<span data-ttu-id="1a802-156">*NameOf expr*</span><span class="sxs-lookup"><span data-stu-id="1a802-156">*nameof expr*</span></span>|`nameof str`|

## <a name="constant-patterns"></a><span data-ttu-id="1a802-157">Шаблоны констант</span><span class="sxs-lookup"><span data-stu-id="1a802-157">Constant Patterns</span></span>

<span data-ttu-id="1a802-158">Шаблоны констант — это числовые, символьные и строковые литералы, константы перечисления (с включаемым именем типа перечисления).</span><span class="sxs-lookup"><span data-stu-id="1a802-158">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="1a802-159">`match`Выражение, имеющее только постоянные шаблоны, можно сравнивать с оператором case на других языках.</span><span class="sxs-lookup"><span data-stu-id="1a802-159">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="1a802-160">Входные данные сравниваются с литеральным значением, а шаблон соответствует, если значения равны.</span><span class="sxs-lookup"><span data-stu-id="1a802-160">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="1a802-161">Тип литерала должен быть совместим с типом входных данных.</span><span class="sxs-lookup"><span data-stu-id="1a802-161">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="1a802-162">В следующем примере демонстрируется использование литеральных шаблонов, а также используется шаблон переменной и шаблон или.</span><span class="sxs-lookup"><span data-stu-id="1a802-162">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="1a802-163">Еще один пример литерального шаблона — это шаблон, основанный на константах перечисления.</span><span class="sxs-lookup"><span data-stu-id="1a802-163">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="1a802-164">При использовании констант перечисления необходимо указать имя типа перечисления.</span><span class="sxs-lookup"><span data-stu-id="1a802-164">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="1a802-165">Шаблоны идентификаторов</span><span class="sxs-lookup"><span data-stu-id="1a802-165">Identifier Patterns</span></span>

<span data-ttu-id="1a802-166">Если шаблон представляет собой строку символов, образующих допустимый идентификатор, форма идентификатора определяет способ сопоставления шаблона.</span><span class="sxs-lookup"><span data-stu-id="1a802-166">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="1a802-167">Если идентификатор длиннее одного символа и начинается с символа верхнего регистра, компилятор пытается выполнить сопоставление с шаблоном идентификатора.</span><span class="sxs-lookup"><span data-stu-id="1a802-167">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="1a802-168">Идентификатором для этого шаблона может быть значение, помеченное атрибутом Literal, вариантом размеченного объединения, идентификатором исключения или активным шаблоном.</span><span class="sxs-lookup"><span data-stu-id="1a802-168">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="1a802-169">Если соответствующий идентификатор не найден, сопоставление завершается ошибкой, а следующее правило шаблона, шаблон переменной, сравнивается с входными данными.</span><span class="sxs-lookup"><span data-stu-id="1a802-169">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="1a802-170">Шаблоны размеченного объединения могут быть простыми именованными вариантами или иметь значение или кортеж, содержащий несколько значений.</span><span class="sxs-lookup"><span data-stu-id="1a802-170">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="1a802-171">Если имеется значение, необходимо указать идентификатор для этого значения.</span><span class="sxs-lookup"><span data-stu-id="1a802-171">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="1a802-172">В случае кортежа необходимо предоставить шаблон кортежа с идентификатором для каждого элемента кортежа или идентификатором с именем поля для одного или нескольких именованных полей объединения.</span><span class="sxs-lookup"><span data-stu-id="1a802-172">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="1a802-173">Примеры см. в примерах кода в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="1a802-173">See the code examples in this section for examples.</span></span>

<span data-ttu-id="1a802-174">`option`Тип — это размеченное объединение, которое имеет два варианта: `Some` и `None` .</span><span class="sxs-lookup"><span data-stu-id="1a802-174">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="1a802-175">В одном варианте ( `Some` ) есть значение, а другое ( `None` ) — это просто именованное обращение.</span><span class="sxs-lookup"><span data-stu-id="1a802-175">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="1a802-176">Следовательно, необходимо `Some` иметь переменную для значения, связанного с `Some` вариантом, но `None` должно быть само по себе.</span><span class="sxs-lookup"><span data-stu-id="1a802-176">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="1a802-177">В следующем коде переменной `var1` присваивается значение, полученное путем сопоставления с `Some` вариантом.</span><span class="sxs-lookup"><span data-stu-id="1a802-177">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="1a802-178">В следующем примере `PersonName` размеченное объединение содержит сочетание строк и символов, представляющих возможные формы имен.</span><span class="sxs-lookup"><span data-stu-id="1a802-178">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="1a802-179">Размеченные объединения: `FirstOnly` , `LastOnly` и `FirstLast` .</span><span class="sxs-lookup"><span data-stu-id="1a802-179">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="1a802-180">Для размеченных объединений с именованными полями используется знак равенства (=) для извлечения значения именованного поля.</span><span class="sxs-lookup"><span data-stu-id="1a802-180">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="1a802-181">Например, рассмотрим размеченное объединение с объявлением, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="1a802-181">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="1a802-182">Именованные поля можно использовать в выражении сопоставления шаблонов следующим образом.</span><span class="sxs-lookup"><span data-stu-id="1a802-182">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn $"Rectangle with length %f{h}"
    | Circle(r) -> printfn $"Circle with radius %f{r}"
```

<span data-ttu-id="1a802-183">Использование именованного поля является необязательным, поэтому в предыдущем примере оба `Circle(r)` и `Circle(radius = r)` имеют одинаковый результат.</span><span class="sxs-lookup"><span data-stu-id="1a802-183">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="1a802-184">При указании нескольких полей используйте точку с запятой (;) в качестве разделителя.</span><span class="sxs-lookup"><span data-stu-id="1a802-184">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn $"Rectangle with height %f{h} and width %f{w}"
| _ -> ()
```

<span data-ttu-id="1a802-185">Активные шаблоны позволяют определить более сложное сопоставление пользовательских шаблонов.</span><span class="sxs-lookup"><span data-stu-id="1a802-185">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="1a802-186">Дополнительные сведения об активных шаблонах см. в разделе [Активные закономерности](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="1a802-186">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="1a802-187">Случай, когда идентификатор является исключением, используется в сопоставлении шаблонов в контексте обработчиков исключений.</span><span class="sxs-lookup"><span data-stu-id="1a802-187">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="1a802-188">Сведения о сопоставлении шаблонов в обработке исключений см. [в разделе исключения: `try...with` выражение](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1a802-188">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="1a802-189">Шаблоны переменных</span><span class="sxs-lookup"><span data-stu-id="1a802-189">Variable Patterns</span></span>

<span data-ttu-id="1a802-190">Шаблон переменной присваивает значение, совпадающее с именем переменной, которое затем можно использовать в выражении выполнения справа от `->` символа.</span><span class="sxs-lookup"><span data-stu-id="1a802-190">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="1a802-191">Только шаблон переменной соответствует любым входным данным, но шаблоны переменных часто появляются в других шаблонах, поэтому для реализации более сложных структур, таких как кортежи и массивы, следует разложить их на переменные.</span><span class="sxs-lookup"><span data-stu-id="1a802-191">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="1a802-192">В следующем примере демонстрируется шаблон переменной в шаблоне кортежа.</span><span class="sxs-lookup"><span data-stu-id="1a802-192">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="1a802-193">Шаблон as</span><span class="sxs-lookup"><span data-stu-id="1a802-193">as Pattern</span></span>

<span data-ttu-id="1a802-194">`as`Шаблон — это шаблон, `as` к которому добавляется предложение.</span><span class="sxs-lookup"><span data-stu-id="1a802-194">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="1a802-195">`as`Предложение привязывает совпадающее значение к имени, которое может использоваться в выражении выполнения `match` выражения, или, если этот шаблон используется в `let` привязке, имя добавляется в качестве привязки в локальную область.</span><span class="sxs-lookup"><span data-stu-id="1a802-195">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="1a802-196">В следующем примере используется `as` шаблон.</span><span class="sxs-lookup"><span data-stu-id="1a802-196">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="1a802-197">ИЛИ шаблон</span><span class="sxs-lookup"><span data-stu-id="1a802-197">OR Pattern</span></span>

<span data-ttu-id="1a802-198">Шаблон или используется, если входные данные могут соответствовать нескольким шаблонам и вы хотите выполнить тот же код в результате.</span><span class="sxs-lookup"><span data-stu-id="1a802-198">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="1a802-199">Типы обеих сторон шаблона или должны быть совместимы.</span><span class="sxs-lookup"><span data-stu-id="1a802-199">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="1a802-200">В следующем примере демонстрируется шаблон или.</span><span class="sxs-lookup"><span data-stu-id="1a802-200">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="1a802-201">И шаблон</span><span class="sxs-lookup"><span data-stu-id="1a802-201">AND Pattern</span></span>

<span data-ttu-id="1a802-202">Шаблон и требует, чтобы входные данные соответствовали двум шаблонам.</span><span class="sxs-lookup"><span data-stu-id="1a802-202">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="1a802-203">Типы обеих сторон шаблона и должны быть совместимы.</span><span class="sxs-lookup"><span data-stu-id="1a802-203">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="1a802-204">Следующий пример аналогичен `detectZeroTuple` показанному в разделе Шаблон кортежа далее в этом разделе, но здесь `var1` и и `var2` получаются в виде значений с помощью шаблона и.</span><span class="sxs-lookup"><span data-stu-id="1a802-204">The following example is like `detectZeroTuple` shown in the Tuple Pattern section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="1a802-205">Шаблон «против»</span><span class="sxs-lookup"><span data-stu-id="1a802-205">Cons Pattern</span></span>

<span data-ttu-id="1a802-206">Шаблон недостатков используется для разбиения списка на первый элемент, *заголовок* и список, содержащий остальные элементы, *хвост*.</span><span class="sxs-lookup"><span data-stu-id="1a802-206">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="1a802-207">Шаблон списка</span><span class="sxs-lookup"><span data-stu-id="1a802-207">List Pattern</span></span>

<span data-ttu-id="1a802-208">Шаблон списка позволяет разложить списки на несколько элементов.</span><span class="sxs-lookup"><span data-stu-id="1a802-208">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="1a802-209">Сам шаблон списка может сопоставлять только списки определенного числа элементов.</span><span class="sxs-lookup"><span data-stu-id="1a802-209">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="1a802-210">Шаблон массива</span><span class="sxs-lookup"><span data-stu-id="1a802-210">Array Pattern</span></span>

<span data-ttu-id="1a802-211">Шаблон массива напоминает шаблон списка и может использоваться для разложения массивов определенной длины.</span><span class="sxs-lookup"><span data-stu-id="1a802-211">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="1a802-212">Шаблон в круглых скобках</span><span class="sxs-lookup"><span data-stu-id="1a802-212">Parenthesized Pattern</span></span>

<span data-ttu-id="1a802-213">Круглые скобки могут быть сгруппированы вокруг шаблонов для достижения требуемой ассоциативности.</span><span class="sxs-lookup"><span data-stu-id="1a802-213">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="1a802-214">В следующем примере круглые скобки используются для управления ассоциативностью между шаблоном и и шаблоном недостатка.</span><span class="sxs-lookup"><span data-stu-id="1a802-214">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="1a802-215">Шаблон кортежа</span><span class="sxs-lookup"><span data-stu-id="1a802-215">Tuple Pattern</span></span>

<span data-ttu-id="1a802-216">Шаблон кортежа соответствует входным данным в форме кортежа и позволяет разложить кортеж в составные элементы с помощью переменных сопоставления шаблонов для каждой из позиций в кортеже.</span><span class="sxs-lookup"><span data-stu-id="1a802-216">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="1a802-217">В следующем примере демонстрируется шаблон кортежа, а также используются литеральные шаблоны, шаблоны переменных и шаблон с подстановочными знаками.</span><span class="sxs-lookup"><span data-stu-id="1a802-217">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="1a802-218">Шаблон записи</span><span class="sxs-lookup"><span data-stu-id="1a802-218">Record Pattern</span></span>

<span data-ttu-id="1a802-219">Шаблон записи используется для разложения записей, чтобы извлечь значения полей.</span><span class="sxs-lookup"><span data-stu-id="1a802-219">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="1a802-220">Шаблон не должен ссылаться на все поля записи; все пропущенные поля просто не участвуют в сопоставлении и не извлекаются.</span><span class="sxs-lookup"><span data-stu-id="1a802-220">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="1a802-221">Шаблон подстановочного знака</span><span class="sxs-lookup"><span data-stu-id="1a802-221">Wildcard Pattern</span></span>

<span data-ttu-id="1a802-222">Шаблон подстановочного знака представлен символом подчеркивания ( `_` ) и соответствует любым входным данным, как и шаблону переменной, за исключением того, что входные данные удаляются, а не присваиваются переменной.</span><span class="sxs-lookup"><span data-stu-id="1a802-222">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="1a802-223">Шаблон шаблона часто используется в других шаблонах в качестве заполнителя для значений, которые не требуются в выражении справа от `->` символа.</span><span class="sxs-lookup"><span data-stu-id="1a802-223">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="1a802-224">Шаблон с подстановочным знаком также часто используется в конце списка шаблонов для сопоставления с любыми несоответствующими входными данными.</span><span class="sxs-lookup"><span data-stu-id="1a802-224">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="1a802-225">Шаблон с подстановочными знаками демонстрируется во многих примерах кода в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="1a802-225">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="1a802-226">См. Приведенный выше код для одного примера.</span><span class="sxs-lookup"><span data-stu-id="1a802-226">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="1a802-227">Шаблоны с аннотациями типов</span><span class="sxs-lookup"><span data-stu-id="1a802-227">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="1a802-228">Шаблоны могут иметь аннотации типов.</span><span class="sxs-lookup"><span data-stu-id="1a802-228">Patterns can have type annotations.</span></span> <span data-ttu-id="1a802-229">Они ведут себя так же, как и другие аннотации типа и пошаговое определение, как и другие заметки типа.</span><span class="sxs-lookup"><span data-stu-id="1a802-229">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="1a802-230">Для заметок типа в шаблонах требуются круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="1a802-230">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="1a802-231">В следующем коде показан шаблон с аннотацией типа.</span><span class="sxs-lookup"><span data-stu-id="1a802-231">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="1a802-232">Шаблон проверки типа</span><span class="sxs-lookup"><span data-stu-id="1a802-232">Type Test Pattern</span></span>

<span data-ttu-id="1a802-233">Шаблон проверки типа используется для сопоставления входных данных с типом.</span><span class="sxs-lookup"><span data-stu-id="1a802-233">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="1a802-234">Если тип входных данных соответствует типу (или производному типу) типа, указанного в шаблоне, сопоставление выполняется с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="1a802-234">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="1a802-235">В следующем примере показан шаблон проверки типа.</span><span class="sxs-lookup"><span data-stu-id="1a802-235">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="1a802-236">Если проверяется только идентификатор определенного производного типа, то `as identifier` часть шаблона не требуется, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="1a802-236">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a><span data-ttu-id="1a802-237">Шаблон NULL</span><span class="sxs-lookup"><span data-stu-id="1a802-237">Null Pattern</span></span>

<span data-ttu-id="1a802-238">Шаблон NULL соответствует значению NULL, которое может появиться при работе с типами, допускающими значение null.</span><span class="sxs-lookup"><span data-stu-id="1a802-238">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="1a802-239">Шаблоны NULL часто используются при взаимодействии с .NET Frameworkным кодом.</span><span class="sxs-lookup"><span data-stu-id="1a802-239">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="1a802-240">Например, возвращаемое значение API-интерфейса .NET может быть входным для `match` выражения.</span><span class="sxs-lookup"><span data-stu-id="1a802-240">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="1a802-241">Можно управлять выполнением программы в зависимости от того, имеет ли возвращаемое значение значение null, а также другие характеристики возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="1a802-241">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="1a802-242">Можно использовать шаблон NULL, чтобы предотвратить распространение значений NULL на остальную часть программы.</span><span class="sxs-lookup"><span data-stu-id="1a802-242">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="1a802-243">В следующем примере используется шаблон NULL и шаблон переменной.</span><span class="sxs-lookup"><span data-stu-id="1a802-243">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="nameof-pattern"></a><span data-ttu-id="1a802-244">Шаблон NameOf</span><span class="sxs-lookup"><span data-stu-id="1a802-244">Nameof pattern</span></span>

<span data-ttu-id="1a802-245">`nameof`Шаблон соответствует строке, если его значение равно выражению, которое следует за `nameof` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="1a802-245">The `nameof` pattern matches against a string when its value is equal to the expression that follows the `nameof` keyword.</span></span> <span data-ttu-id="1a802-246">Например:</span><span class="sxs-lookup"><span data-stu-id="1a802-246">for example:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```

<span data-ttu-id="1a802-247">Сведения о [`nameof`](nameof.md) том, что можно сделать, см. в операторе.</span><span class="sxs-lookup"><span data-stu-id="1a802-247">See the [`nameof`](nameof.md) operator for information on what you can take a name of.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a802-248">См. также</span><span class="sxs-lookup"><span data-stu-id="1a802-248">See also</span></span>

- [<span data-ttu-id="1a802-249">Выражения match</span><span class="sxs-lookup"><span data-stu-id="1a802-249">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="1a802-250">Активные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1a802-250">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="1a802-251">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="1a802-251">F# Language Reference</span></span>](index.md)
