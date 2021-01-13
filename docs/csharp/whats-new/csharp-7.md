---
title: Новые возможности C# 7.0. Руководство по языку C#
description: Общие сведения о новых возможностях версии 7.0 языка C#.
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: c238439b0f435e579d932b3b1eb13e9b0061fa5f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678223"
---
# <a name="whats-new-in-c-70-through-c-73"></a><span data-ttu-id="f5338-103">Новые возможности в C# версий 7.0–7.3</span><span class="sxs-lookup"><span data-stu-id="f5338-103">What's new in C# 7.0 through C# 7.3</span></span>

<span data-ttu-id="f5338-104">В C# версий 7.0–7.3 был реализован ряд функций и улучшены возможности разработки на C#.</span><span class="sxs-lookup"><span data-stu-id="f5338-104">C# 7.0 through C# 7.3 brought a number of features and incremental improvements to your development experience with C#.</span></span> <span data-ttu-id="f5338-105">В этой статье приводятся общие сведения о новых функциях языка и параметрах компилятора.</span><span class="sxs-lookup"><span data-stu-id="f5338-105">This article provides an overview of the new language features and compiler options.</span></span> <span data-ttu-id="f5338-106">Приводится описание поведения C# 7.3, то есть самой последней версии, поддерживаемой для приложений на основе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5338-106">The descriptions describe the behavior for C# 7.3, which is the most recent version supported for .NET Framework-based applications.</span></span>

<span data-ttu-id="f5338-107">В C# 7.1 добавлен элемент конфигурации [выбор версии языка](../language-reference/configure-language-version.md), что позволяет указать версию языка компилятора в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="f5338-107">The [language version selection](../language-reference/configure-language-version.md) configuration element was added with C# 7.1, which enables you to specify the compiler language version in your project file.</span></span>

<span data-ttu-id="f5338-108">В C# версий 7.0–7.3 добавлены следующие функции и темы в язык C#:</span><span class="sxs-lookup"><span data-stu-id="f5338-108">C# 7.0-7.3 adds these features and themes to the C# language:</span></span>

- [<span data-ttu-id="f5338-109">Кортежи и пустые переменные</span><span class="sxs-lookup"><span data-stu-id="f5338-109">Tuples and discards</span></span>](#tuples-and-discards)
  - <span data-ttu-id="f5338-110">Вы можете создать простые, неименованные типы, содержащие несколько открытых полей.</span><span class="sxs-lookup"><span data-stu-id="f5338-110">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="f5338-111">Компиляторы и инструменты IDE понимают семантику этих типов.</span><span class="sxs-lookup"><span data-stu-id="f5338-111">Compilers and IDE tools understand the semantics of these types.</span></span>
  - <span data-ttu-id="f5338-112">Пустые переменные представляют собой временные переменные, доступные только для записи, которые используются при присвоении в тех случаях, когда присваиваемое значение не важно.</span><span class="sxs-lookup"><span data-stu-id="f5338-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="f5338-113">Они особенно полезны при деконструкции кортежей и пользовательских типов, а также при вызове методов с параметрами `out`.</span><span class="sxs-lookup"><span data-stu-id="f5338-113">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
- [<span data-ttu-id="f5338-114">Соответствие шаблону</span><span class="sxs-lookup"><span data-stu-id="f5338-114">Pattern Matching</span></span>](#pattern-matching)
  - <span data-ttu-id="f5338-115">На основе произвольных типов и значений их членов можно создать логику ветвления.</span><span class="sxs-lookup"><span data-stu-id="f5338-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
- [<span data-ttu-id="f5338-116">Метод `async` `Main`</span><span class="sxs-lookup"><span data-stu-id="f5338-116">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f5338-117">Точка входа для приложения может иметь модификатор `async`.</span><span class="sxs-lookup"><span data-stu-id="f5338-117">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="f5338-118">Локальные функции</span><span class="sxs-lookup"><span data-stu-id="f5338-118">Local Functions</span></span>](#local-functions)
  - <span data-ttu-id="f5338-119">Функции можно вкладывать в другие функции, чтобы ограничить область их действия и видимость.</span><span class="sxs-lookup"><span data-stu-id="f5338-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
- [<span data-ttu-id="f5338-120">Другие элементы, воплощающие выражение</span><span class="sxs-lookup"><span data-stu-id="f5338-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
  - <span data-ttu-id="f5338-121">Список элементов, которые можно создавать с помощью выражений, увеличился.</span><span class="sxs-lookup"><span data-stu-id="f5338-121">The list of members that can be authored using expressions has grown.</span></span>
- [<span data-ttu-id="f5338-122">Выражения `throw`</span><span class="sxs-lookup"><span data-stu-id="f5338-122">`throw` Expressions</span></span>](#throw-expressions)
  - <span data-ttu-id="f5338-123">Исключения могут возникать в конструкциях кода, которые ранее не допускались, поскольку `throw` был оператором.</span><span class="sxs-lookup"><span data-stu-id="f5338-123">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span>
- [<span data-ttu-id="f5338-124">Литеральные выражения `default`</span><span class="sxs-lookup"><span data-stu-id="f5338-124">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f5338-125">Литеральные выражения по умолчанию можно использовать в выражениях значения по умолчанию, если можно вывести тип целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="f5338-125">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="f5338-126">Усовершенствования в синтаксисе числовых литералов</span><span class="sxs-lookup"><span data-stu-id="f5338-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
  - <span data-ttu-id="f5338-127">Новые маркеры делают числовые константы более удобочитаемыми.</span><span class="sxs-lookup"><span data-stu-id="f5338-127">New tokens improve readability for numeric constants.</span></span>
- [<span data-ttu-id="f5338-128">Переменные `out`</span><span class="sxs-lookup"><span data-stu-id="f5338-128">`out` variables</span></span>](#out-variables)
  - <span data-ttu-id="f5338-129">Значения `out` можно объявлять встроенными как аргументы для метода, в котором они используются.</span><span class="sxs-lookup"><span data-stu-id="f5338-129">You can declare `out` values inline as arguments to the method where they're used.</span></span>
- [<span data-ttu-id="f5338-130">Неконечные именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="f5338-130">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="f5338-131">После именованных аргументов могут следовать позиционные аргументы.</span><span class="sxs-lookup"><span data-stu-id="f5338-131">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="f5338-132">Модификатор доступа `private protected`</span><span class="sxs-lookup"><span data-stu-id="f5338-132">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="f5338-133">Модификатор доступа `private protected` разрешает доступ для производных классов в одной сборке.</span><span class="sxs-lookup"><span data-stu-id="f5338-133">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="f5338-134">Улучшенное разрешение перегрузки</span><span class="sxs-lookup"><span data-stu-id="f5338-134">Improved overload resolution</span></span>](#improved-overload-candidates)
  - <span data-ttu-id="f5338-135">Новые правила для устранения неоднозначности разрешения перегрузки.</span><span class="sxs-lookup"><span data-stu-id="f5338-135">New rules to resolve overload resolution ambiguity.</span></span>
- [<span data-ttu-id="f5338-136">Методы написания безопасного и эффективного кода</span><span class="sxs-lookup"><span data-stu-id="f5338-136">Techniques for writing safe efficient code</span></span>](#enabling-more-efficient-safe-code)
  - <span data-ttu-id="f5338-137">Ряд улучшений синтаксиса, обеспечивающих работу с типами значений с использованием семантики ссылок.</span><span class="sxs-lookup"><span data-stu-id="f5338-137">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>

<span data-ttu-id="f5338-138">Наконец, компилятор получил новые параметры:</span><span class="sxs-lookup"><span data-stu-id="f5338-138">Finally, the compiler has new options:</span></span>

- <span data-ttu-id="f5338-139">`-refout` и `-refonly`, которые управляют [созданием базовой сборки](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="f5338-139">`-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>
- <span data-ttu-id="f5338-140">`-publicsign` позволяет включить подписывание сборок как программного обеспечения с открытым кодом;</span><span class="sxs-lookup"><span data-stu-id="f5338-140">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="f5338-141">`-pathmap` позволяет предоставить сопоставление для исходных каталогов.</span><span class="sxs-lookup"><span data-stu-id="f5338-141">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="f5338-142">В оставшейся части этой статьи представлены общие сведения об этих функциях.</span><span class="sxs-lookup"><span data-stu-id="f5338-142">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="f5338-143">Каждая функция сопровождается обоснованием и описанием синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="f5338-143">For each feature, you'll learn the reasoning behind it and the syntax.</span></span> <span data-ttu-id="f5338-144">Эти функции можно изучить в своей среде с помощью глобального средства `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="f5338-144">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="f5338-145">Установите глобальное средство [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="f5338-145">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="f5338-146">Клонируйте репозиторий [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="f5338-146">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="f5338-147">Для репозитория *try-samples* установите в качестве текущего каталога подкаталог *csharp7*.</span><span class="sxs-lookup"><span data-stu-id="f5338-147">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="f5338-148">Запустите `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="f5338-148">Run `dotnet try`.</span></span>

## <a name="tuples-and-discards"></a><span data-ttu-id="f5338-149">Кортежи и пустые переменные</span><span class="sxs-lookup"><span data-stu-id="f5338-149">Tuples and discards</span></span>

<span data-ttu-id="f5338-150">C# предоставляет расширенный синтаксис для классов и структур, который используется для объяснения цели проекта.</span><span class="sxs-lookup"><span data-stu-id="f5338-150">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="f5338-151">Однако в некоторых случаях расширенный синтаксис требует дополнительной работы с минимальной результативностью.</span><span class="sxs-lookup"><span data-stu-id="f5338-151">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="f5338-152">Зачастую требуется написание методов, которым нужна простая структура, состоящая из более чем одного элемента данных.</span><span class="sxs-lookup"><span data-stu-id="f5338-152">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="f5338-153">Для поддержки этих сценариев в C# были добавлены *кортежи*.</span><span class="sxs-lookup"><span data-stu-id="f5338-153">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="f5338-154">Кортежи — это упрощенные структуры данных, содержащие несколько полей для представления элементов данных.</span><span class="sxs-lookup"><span data-stu-id="f5338-154">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span> <span data-ttu-id="f5338-155">Поля не проверяются, и собственные методы определять нельзя.</span><span class="sxs-lookup"><span data-stu-id="f5338-155">The fields aren't validated, and you can't define your own methods.</span></span> <span data-ttu-id="f5338-156">Типы кортежей в C# поддерживают `==` и `!=`.</span><span class="sxs-lookup"><span data-stu-id="f5338-156">C# tuple types support `==` and `!=`.</span></span> <span data-ttu-id="f5338-157">Дополнительные сведения см. в записи блога</span><span class="sxs-lookup"><span data-stu-id="f5338-157">For more information.</span></span>

> [!NOTE]
> <span data-ttu-id="f5338-158">Кортежи существовали и в версиях C#, предшествовавших версии 7.0, но были неэффективны и не имели языковой поддержки.</span><span class="sxs-lookup"><span data-stu-id="f5338-158">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span> <span data-ttu-id="f5338-159">Это означает, что ссылки на элементы кортежа можно было задавать только в виде `Item1`, `Item2` и т. д.</span><span class="sxs-lookup"><span data-stu-id="f5338-159">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="f5338-160">В C# 7.0 реализуется языковая поддержка кортежей, что позволяет работать с семантическими именами полей кортежа с использованием новых, более эффективных типов кортежей.</span><span class="sxs-lookup"><span data-stu-id="f5338-160">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="f5338-161">Можно создать кортеж путем присваивания значения каждого элемента, а также (необязательно) задать семантические имена для каждого из элементов кортежа:</span><span class="sxs-lookup"><span data-stu-id="f5338-161">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="f5338-162">Кортеж `namedLetters` содержит поля, которые называются `Alpha` и `Beta`.</span><span class="sxs-lookup"><span data-stu-id="f5338-162">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="f5338-163">Эти имена существуют только во время компиляции и не сохраняются, например при проверке кортежа посредством отражения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="f5338-163">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at run time.</span></span>

<span data-ttu-id="f5338-164">В назначении кортежа можно также указать имена полей в правой части назначения:</span><span class="sxs-lookup"><span data-stu-id="f5338-164">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="f5338-165">В некоторых случаях элементы возвращаемого методом кортежа необходимо распаковать.</span><span class="sxs-lookup"><span data-stu-id="f5338-165">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="f5338-166">С этой целью для каждого значения в этом кортеже объявляется отдельная переменная.</span><span class="sxs-lookup"><span data-stu-id="f5338-166">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="f5338-167">Такая распаковка называется *деконструкцией* кортежа:</span><span class="sxs-lookup"><span data-stu-id="f5338-167">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="f5338-168">Аналогичную деконструкцию можно обеспечить для любого типа в .NET.</span><span class="sxs-lookup"><span data-stu-id="f5338-168">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="f5338-169">Можно написать метод `Deconstruct` в качестве члена класса.</span><span class="sxs-lookup"><span data-stu-id="f5338-169">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="f5338-170">Метод `Deconstruct` предоставляет набор аргументов `out` для каждого из свойств, которые нужно извлечь.</span><span class="sxs-lookup"><span data-stu-id="f5338-170">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="f5338-171">Рассмотрим этот класс `Point`, предоставляющий метод deconstructor, который извлекает координаты `X` и `Y`:</span><span class="sxs-lookup"><span data-stu-id="f5338-171">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

<span data-ttu-id="f5338-172">Отдельные поля можно извлекать, назначая кортежу метод `Point`:</span><span class="sxs-lookup"><span data-stu-id="f5338-172">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="f5338-173">Очень часто при инициализации кортежа переменные в правой части задания совпадают с именами для элементов кортежа: Имена элементов кортежа можно вывести из переменных, используемых для инициализации кортежа:</span><span class="sxs-lookup"><span data-stu-id="f5338-173">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements: The names of tuple elements can be inferred from the variables used to initialize the tuple:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f5338-174">Дополнительные сведения об этой функции см. в статье [Типы кортежей](../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-174">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

<span data-ttu-id="f5338-175">При деконструкции кортежа или вызове метода с параметрами `out` часто требуется определить переменную, которую вы не планируете использовать и значение которой не важно.</span><span class="sxs-lookup"><span data-stu-id="f5338-175">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="f5338-176">Для работы в таких сценариях в C# реализована поддержка *пустых переменных*.</span><span class="sxs-lookup"><span data-stu-id="f5338-176">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="f5338-177">Пустая переменная представляет собой доступную только для записи переменную с именем `_` (знак подчеркивания). Вы можете назначить одной переменной все значения, которые не потребуются в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="f5338-177">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="f5338-178">Пустая переменная является аналогом неприсвоенной переменной и не может использоваться в коде где-либо, за исключением оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="f5338-178">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="f5338-179">Пустые переменные поддерживается в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="f5338-179">Discards are supported in the following scenarios:</span></span>

- <span data-ttu-id="f5338-180">При деконструкции кортежей или пользовательских типов.</span><span class="sxs-lookup"><span data-stu-id="f5338-180">When deconstructing tuples or user-defined types.</span></span>
- <span data-ttu-id="f5338-181">При вызове методов с параметрами [out](../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-181">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="f5338-182">В операции сопоставления шаблонов с выражениями [is](../language-reference/keywords/is.md) и [switch](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-182">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
- <span data-ttu-id="f5338-183">В качестве автономного идентификатора в тех случаях, когда требуется явно идентифицировать значение присваивания как пустую переменную.</span><span class="sxs-lookup"><span data-stu-id="f5338-183">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="f5338-184">В приведенном ниже примере определяется метод `QueryCityDataForYears`, который возвращает кортеж из 6 элементов, содержащий данные по городу за два разных года.</span><span class="sxs-lookup"><span data-stu-id="f5338-184">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains data for a city for two different years.</span></span> <span data-ttu-id="f5338-185">В вызове метода в этом примере учитываются только два возвращаемых методом значения population, поэтому при деконструкции кортежа оставшиеся значения обрабатываются как пустые переменные.</span><span class="sxs-lookup"><span data-stu-id="f5338-185">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="f5338-186">Дополнительные сведения см. в разделе [Пустые переменные](../discards.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-186">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="f5338-187">Регулярные выражения</span><span class="sxs-lookup"><span data-stu-id="f5338-187">Pattern matching</span></span>

<span data-ttu-id="f5338-188">*Сопоставление шаблонов* — это набор функций, которые позволяют использовать новые способы выражения потока управления в коде.</span><span class="sxs-lookup"><span data-stu-id="f5338-188">*Pattern matching* is a set of features that enable new ways to express control flow in your code.</span></span> <span data-ttu-id="f5338-189">Можно проверить переменные на их тип, значение или значения их свойств.</span><span class="sxs-lookup"><span data-stu-id="f5338-189">You can test variables for their type, values or the values of their properties.</span></span> <span data-ttu-id="f5338-190">Эти методы создают более удобочитаемый поток кода.</span><span class="sxs-lookup"><span data-stu-id="f5338-190">These techniques create more readable code flow.</span></span>

<span data-ttu-id="f5338-191">Сопоставление шаблонов поддерживает выражения `is` и `switch`.</span><span class="sxs-lookup"><span data-stu-id="f5338-191">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="f5338-192">Каждое из них позволяет проверять объект и его свойства и определять, соответствует ли этот объект искомому шаблону.</span><span class="sxs-lookup"><span data-stu-id="f5338-192">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="f5338-193">Для добавления правил в шаблон используется ключевое слово `when`.</span><span class="sxs-lookup"><span data-stu-id="f5338-193">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="f5338-194">Выражение шаблона `is` позволяет использовать знакомый [оператор `is`](../language-reference/keywords/is.md#pattern-matching-with-is) для запроса объекта о типе и присваивания результата в одной инструкции.</span><span class="sxs-lookup"><span data-stu-id="f5338-194">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="f5338-195">Следующий код проверяет, является ли переменная `int`; если да, добавляет ее к текущей сумме:</span><span class="sxs-lookup"><span data-stu-id="f5338-195">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="f5338-196">Предыдущий небольшой пример показывает улучшенное выражение `is`.</span><span class="sxs-lookup"><span data-stu-id="f5338-196">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="f5338-197">Можно проверять типы значений, а также ссылочные типы; успешный результат можно назначить переменной соответствующего типа.</span><span class="sxs-lookup"><span data-stu-id="f5338-197">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="f5338-198">Выражение сопоставления со switch имеет знакомый синтаксис, основанный на операторе `switch`, который уже является частью языка C#.</span><span class="sxs-lookup"><span data-stu-id="f5338-198">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="f5338-199">Обновленный оператор switch имеет несколько новых конструкций:</span><span class="sxs-lookup"><span data-stu-id="f5338-199">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="f5338-200">Определяющий тип выражения `switch` больше не ограничен интегральными типами, типами `Enum`, `string` или типами, принимающими значения NULL, соответствующими одному из таких типов.</span><span class="sxs-lookup"><span data-stu-id="f5338-200">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="f5338-201">Может использоваться любой тип.</span><span class="sxs-lookup"><span data-stu-id="f5338-201">Any type may be used.</span></span>
- <span data-ttu-id="f5338-202">Можно проверить тип выражения `switch` в каждой метке `case`.</span><span class="sxs-lookup"><span data-stu-id="f5338-202">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="f5338-203">Как и в выражении `is`, можно назначить новую переменную этого типа.</span><span class="sxs-lookup"><span data-stu-id="f5338-203">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="f5338-204">Можно добавить предложение `when` для дальнейшей проверки условий по этой переменной.</span><span class="sxs-lookup"><span data-stu-id="f5338-204">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="f5338-205">Порядок меток `case` становится важным.</span><span class="sxs-lookup"><span data-stu-id="f5338-205">The order of `case` labels is now important.</span></span> <span data-ttu-id="f5338-206">Будет выполнена первая совпавшая ветвь; другие пропускаются.</span><span class="sxs-lookup"><span data-stu-id="f5338-206">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="f5338-207">Это демонстрируется в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="f5338-207">The following code demonstrates these new features:</span></span>

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- <span data-ttu-id="f5338-208">`case 0:` — знакомый шаблон константы.</span><span class="sxs-lookup"><span data-stu-id="f5338-208">`case 0:` is the familiar constant pattern.</span></span>
- <span data-ttu-id="f5338-209">`case IEnumerable<int> childSequence:` — шаблон типа.</span><span class="sxs-lookup"><span data-stu-id="f5338-209">`case IEnumerable<int> childSequence:` is a type pattern.</span></span>
- <span data-ttu-id="f5338-210">`case int n when n > 0:` — шаблон типа с дополнительным условием `when`.</span><span class="sxs-lookup"><span data-stu-id="f5338-210">`case int n when n > 0:` is a type pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="f5338-211">`case null:` — шаблон NULL.</span><span class="sxs-lookup"><span data-stu-id="f5338-211">`case null:` is the null pattern.</span></span>
- <span data-ttu-id="f5338-212">`default:` — знакомый вариант по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5338-212">`default:` is the familiar default case.</span></span>

<span data-ttu-id="f5338-213">Начиная с версии C# 7.1, выражение шаблона для шаблона типа `is` и `switch` может быть типом параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f5338-213">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="f5338-214">Эта возможность особенно полезна при проверке типов, которые могут представлять типы `struct` или `class`, когда вы хотите избежать упаковки-преобразования.</span><span class="sxs-lookup"><span data-stu-id="f5338-214">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

<span data-ttu-id="f5338-215">Дополнительные сведения о сопоставлении шаблонов см. в разделе [Сопоставление шаблонов в C#](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-215">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="async-main"></a><span data-ttu-id="f5338-216">Async main</span><span class="sxs-lookup"><span data-stu-id="f5338-216">Async main</span></span>

<span data-ttu-id="f5338-217">Метод *async main* позволяет использовать `await` в методе `Main`.</span><span class="sxs-lookup"><span data-stu-id="f5338-217">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="f5338-218">Раньше пришлось бы написать:</span><span class="sxs-lookup"><span data-stu-id="f5338-218">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f5338-219">Теперь можно написать:</span><span class="sxs-lookup"><span data-stu-id="f5338-219">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f5338-220">Если программа не возвращает код выхода, объявите метод `Main`, возвращающий <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f5338-220">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f5338-221">См. подробнее в описании [async main](../programming-guide/main-and-command-args/index.md) в руководстве по программированию.</span><span class="sxs-lookup"><span data-stu-id="f5338-221">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="local-functions"></a><span data-ttu-id="f5338-222">Локальные функции</span><span class="sxs-lookup"><span data-stu-id="f5338-222">Local functions</span></span>

<span data-ttu-id="f5338-223">Модели многих классов включают методы, вызываемые только из одного места.</span><span class="sxs-lookup"><span data-stu-id="f5338-223">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="f5338-224">Эти дополнительные закрытые методы делают каждый метод небольшим и направленным.</span><span class="sxs-lookup"><span data-stu-id="f5338-224">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="f5338-225">*Локальные функции* позволяют объявлять методы в контексте другого метода.</span><span class="sxs-lookup"><span data-stu-id="f5338-225">*Local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="f5338-226">Локальные функции позволяют читателям класса легче увидеть, что локальный метод вызывается только из контекста, в котором он объявлен.</span><span class="sxs-lookup"><span data-stu-id="f5338-226">Local functions make it easier for readers of the class to see that the local method is only called from the context in which it is declared.</span></span>

<span data-ttu-id="f5338-227">Существуют два общих варианта использования локальных функций: открытые методы итератора и открытые асинхронные методы.</span><span class="sxs-lookup"><span data-stu-id="f5338-227">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="f5338-228">Оба эти типа методов создают код, который сообщает об ошибках позднее, чем могли ожидать программисты.</span><span class="sxs-lookup"><span data-stu-id="f5338-228">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="f5338-229">В случае методов итератора исключения наблюдаются только при вызове кода, перечисляющего возвращенную последовательность.</span><span class="sxs-lookup"><span data-stu-id="f5338-229">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="f5338-230">В случае асинхронных методов исключения наблюдаются только при ожидании возвращаемого объекта `Task`.</span><span class="sxs-lookup"><span data-stu-id="f5338-230">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="f5338-231">В следующем примере показано отделение проверки параметров от реализации итератора с использованием локальной функции:</span><span class="sxs-lookup"><span data-stu-id="f5338-231">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="f5338-232">Та же технология может применяться с методами `async` для того, чтобы исключения, возникающие при проверке параметров, выдавались до начала асинхронной работы:</span><span class="sxs-lookup"><span data-stu-id="f5338-232">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="f5338-233">Теперь поддерживается такой синтаксис:</span><span class="sxs-lookup"><span data-stu-id="f5338-233">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="f5338-234">Атрибут `SomeThingAboutFieldAttribute` применяется к резервному полю, созданному компилятором для `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="f5338-234">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="f5338-235">Дополнительные сведения см. в статье об [атрибутах](../programming-guide/concepts/attributes/index.md) в руководстве по программированию на C#.</span><span class="sxs-lookup"><span data-stu-id="f5338-235">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

> [!NOTE]
> <span data-ttu-id="f5338-236">Некоторые конструкции, поддерживаемые локальными функциями, могут также выполняться с помощью *лямбда-выражений*.</span><span class="sxs-lookup"><span data-stu-id="f5338-236">Some of the designs that are supported by local functions can also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="f5338-237">Дополнительные сведения см. в статье [Сравнение локальных функций и лямбда-выражений](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span><span class="sxs-lookup"><span data-stu-id="f5338-237">For more information, see [Local functions vs. lambda expressions](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="f5338-238">Другие элементы, воплощающие выражение</span><span class="sxs-lookup"><span data-stu-id="f5338-238">More expression-bodied members</span></span>

<span data-ttu-id="f5338-239">В C# версии 6 появились элементы, воплощающие выражение, для функций-членов и свойств, доступных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="f5338-239">C# 6 introduced expression-bodied members for member functions and read-only properties.</span></span> <span data-ttu-id="f5338-240">В C# 7.0 расширен список допустимых членов, которые могут быть реализованы как выражения.</span><span class="sxs-lookup"><span data-stu-id="f5338-240">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="f5338-241">В C# 7.0 можно реализовать *конструкторы*, *методы завершения*, а также методы доступа `get` и `set` для *свойств* и *индексаторов*.</span><span class="sxs-lookup"><span data-stu-id="f5338-241">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="f5338-242">В следующем коде показаны примеры каждого из них:</span><span class="sxs-lookup"><span data-stu-id="f5338-242">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="f5338-243">В этом примере метод завершения не требуется, он приводится для демонстрации синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="f5338-243">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="f5338-244">Метод завершения следует реализовывать в классе только в том случае, если это необходимо для высвобождения неуправляемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f5338-244">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="f5338-245">Кроме того, вместо управления неуправляемыми ресурсами напрямую можно воспользоваться классом <xref:System.Runtime.InteropServices.SafeHandle>.</span><span class="sxs-lookup"><span data-stu-id="f5338-245">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="f5338-246">Новые расположения для элементов, составляющих выражение, представляют важный этап развития языка C#. Эти функции были реализованы членами сообщества, работающими над проектом [Roslyn](https://github.com/dotnet/Roslyn) с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="f5338-246">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="f5338-247">Изменение метода на элемент, воплощающий выражение, является [совместимым на уровне двоичного кода](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-247">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="f5338-248">Выражения throw</span><span class="sxs-lookup"><span data-stu-id="f5338-248">Throw expressions</span></span>

<span data-ttu-id="f5338-249">В C# `throw` всегда был оператором.</span><span class="sxs-lookup"><span data-stu-id="f5338-249">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="f5338-250">Поскольку `throw` — оператор, а не выражение, конструкции C# находились там, где использовать их было невозможно.</span><span class="sxs-lookup"><span data-stu-id="f5338-250">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="f5338-251">Они включали условные выражения, выражения объединения со значением NULL и некоторые лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="f5338-251">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="f5338-252">Добавление элементов, воплощающих выражение, расширяет список мест, в которых могут пригодиться выражения `throw`.</span><span class="sxs-lookup"><span data-stu-id="f5338-252">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="f5338-253">Для записи этих конструкций в C# 7.0 представлены [*выражения throw*](../language-reference/keywords/throw.md#the-throw-expression).</span><span class="sxs-lookup"><span data-stu-id="f5338-253">So that you can write any of these constructs, C# 7.0 introduces [*throw expressions*](../language-reference/keywords/throw.md#the-throw-expression).</span></span>

<span data-ttu-id="f5338-254">Это добавление упрощает написание кода на основе выражений.</span><span class="sxs-lookup"><span data-stu-id="f5338-254">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="f5338-255">Дополнительные инструкции для проверки на наличие ошибок не требуются.</span><span class="sxs-lookup"><span data-stu-id="f5338-255">You don't need additional statements for error checking.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f5338-256">Литеральные выражения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="f5338-256">Default literal expressions</span></span>

<span data-ttu-id="f5338-257">Литеральные выражения по умолчанию — это усовершенствование выражения значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5338-257">Default literal expressions are an enhancement to default value expressions.</span></span> <span data-ttu-id="f5338-258">Эти выражения инициализируют переменную до значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5338-258">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f5338-259">Раньше пришлось бы написать:</span><span class="sxs-lookup"><span data-stu-id="f5338-259">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f5338-260">Теперь можно опустить тип с правой стороны инициализации:</span><span class="sxs-lookup"><span data-stu-id="f5338-260">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f5338-261">Дополнительные сведения см. в разделе [о литерале default](../language-reference/operators/default.md#default-literal) в статье об [операторе default](../language-reference/operators/default.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-261">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="f5338-262">Усовершенствования в синтаксисе числовых литералов</span><span class="sxs-lookup"><span data-stu-id="f5338-262">Numeric literal syntax improvements</span></span>

<span data-ttu-id="f5338-263">Неправильное толкование числовых констант затрудняет понимание кода при первом прочтении.</span><span class="sxs-lookup"><span data-stu-id="f5338-263">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="f5338-264">Битовые маски или другие символьные значения могут вызывать затруднения.</span><span class="sxs-lookup"><span data-stu-id="f5338-264">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="f5338-265">C# 7.0 содержит две новые возможности для записи чисел в удобочитаемом виде: *двоичные литералы* и *разделители цифр*.</span><span class="sxs-lookup"><span data-stu-id="f5338-265">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="f5338-266">Если вы создаете битовые маски или двоичное представление числа дает наиболее удобочитаемый код, используйте запись в двоичном формате:</span><span class="sxs-lookup"><span data-stu-id="f5338-266">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="f5338-267">`0b` в начале константы означает, что число записано в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="f5338-267">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="f5338-268">Двоичные числа могут быть длинными, поэтому для удобства работы с битовыми шаблонами можно разделять разряды с помощью символа `_`, как показано в двоичной константе в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="f5338-268">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown in the binary constant in the preceding example.</span></span> <span data-ttu-id="f5338-269">Разделитель разрядов может находиться в любом месте константы.</span><span class="sxs-lookup"><span data-stu-id="f5338-269">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="f5338-270">В десятичных числах он обычно используется для разделения тысяч.</span><span class="sxs-lookup"><span data-stu-id="f5338-270">For base 10 numbers, it is common to use it as a thousands separator.</span></span> <span data-ttu-id="f5338-271">Шестнадцатеричные и двоичные числовые литералы могут начинаться со знака `_`:</span><span class="sxs-lookup"><span data-stu-id="f5338-271">Hex and binary numeric literals may begin with an `_`:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="f5338-272">Разделитель разрядов можно также использовать с типами `decimal`, `float` и `double`:</span><span class="sxs-lookup"><span data-stu-id="f5338-272">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="f5338-273">Суммируя вышеизложенное, числовые константы можно объявлять в гораздо более удобочитаемом виде.</span><span class="sxs-lookup"><span data-stu-id="f5338-273">Taken together, you can declare numeric constants with much more readability.</span></span>

## <a name="out-variables"></a><span data-ttu-id="f5338-274">Переменные `out`</span><span class="sxs-lookup"><span data-stu-id="f5338-274">`out` variables</span></span>

<span data-ttu-id="f5338-275">Существующий синтаксис, поддерживающий параметры `out`, был улучшен в C# 7.</span><span class="sxs-lookup"><span data-stu-id="f5338-275">The existing syntax that supports `out` parameters has been improved in C# 7.</span></span> <span data-ttu-id="f5338-276">Переменные `out` можно объявлять в списке аргументов в вызове метода, не записывая отдельный оператор объявления:</span><span class="sxs-lookup"><span data-stu-id="f5338-276">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="f5338-277">Для ясности можно указать тип переменной `out`, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="f5338-277">You may want to specify the type of the `out` variable for clarity, as shown in the preceding example.</span></span> <span data-ttu-id="f5338-278">В то же время язык поддерживает использование неявно типизированной локальной переменной:</span><span class="sxs-lookup"><span data-stu-id="f5338-278">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- <span data-ttu-id="f5338-279">Код проще читать.</span><span class="sxs-lookup"><span data-stu-id="f5338-279">The code is easier to read.</span></span>
  - <span data-ttu-id="f5338-280">Переменная out объявляется при использовании, а не в предыдущей строке кода.</span><span class="sxs-lookup"><span data-stu-id="f5338-280">You declare the out variable where you use it, not on a preceding line of code.</span></span>
- <span data-ttu-id="f5338-281">Назначать начальное значение не нужно.</span><span class="sxs-lookup"><span data-stu-id="f5338-281">No need to assign an initial value.</span></span>
  - <span data-ttu-id="f5338-282">Объявляя переменную `out`, когда она используется при вызове метода, ее нельзя случайно использовать прежде, чем она будет назначена.</span><span class="sxs-lookup"><span data-stu-id="f5338-282">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="f5338-283">Синтаксис, который с версии C# 7.0 позволяет объявлять переменные `out`, теперь также поддерживает инициализаторы полей, инициализаторы свойств, инициализаторы конструктора и предложения запроса.</span><span class="sxs-lookup"><span data-stu-id="f5338-283">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="f5338-284">Он позволяет создать такой код, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="f5338-284">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="f5338-285">Неконечные именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="f5338-285">Non-trailing named arguments</span></span>

<span data-ttu-id="f5338-286">В вызовах методов после находящихся в правильной позиции именованных аргументов теперь можно использовать позиционные аргументы.</span><span class="sxs-lookup"><span data-stu-id="f5338-286">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="f5338-287">Дополнительные сведения см. в разделе [Именованные и необязательные аргументы](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-287">For more information, see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="private-protected-access-modifier"></a><span data-ttu-id="f5338-288">*private protected* — модификатор доступа</span><span class="sxs-lookup"><span data-stu-id="f5338-288">*private protected* access modifier</span></span>

<span data-ttu-id="f5338-289">Новый составной модификатор доступа `private protected` указывает, что доступ к члену может осуществляться содержащим классом или производными классами, которые объявлены в рамках одной сборки.</span><span class="sxs-lookup"><span data-stu-id="f5338-289">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="f5338-290">В отличие от модификатора `protected internal`, который разрешает доступ производным классам или классам из той же сборки, `private protected` ограничивает доступ только для производных классов, объявленных в рамках одной сборки.</span><span class="sxs-lookup"><span data-stu-id="f5338-290">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="f5338-291">Дополнительные сведения см. в разделе [Модификаторы доступа](../language-reference/keywords/access-modifiers.md) в справочнике по языку.</span><span class="sxs-lookup"><span data-stu-id="f5338-291">For more information, see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="improved-overload-candidates"></a><span data-ttu-id="f5338-292">Улучшенный отбор потенциальных перегрузок</span><span class="sxs-lookup"><span data-stu-id="f5338-292">Improved overload candidates</span></span>

<span data-ttu-id="f5338-293">В каждом выпуске обновляются правила разрешения перегрузок для устранения ситуаций, где неоднозначный вызов методов можно решить "очевидным" способом.</span><span class="sxs-lookup"><span data-stu-id="f5338-293">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="f5338-294">В этот выпуск добавлены три новых правила, которые помогают компилятору выбрать очевидный вариант.</span><span class="sxs-lookup"><span data-stu-id="f5338-294">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="f5338-295">Если группа методов содержит элементы экземпляра и статические элементы, компилятор отклоняет все элементы экземпляра при вызове метода без экземпляра-получателя и вне контекста экземпляра.</span><span class="sxs-lookup"><span data-stu-id="f5338-295">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="f5338-296">Компилятор отклоняет статические элементы, если метод был вызван с экземпляром-получателем.</span><span class="sxs-lookup"><span data-stu-id="f5338-296">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="f5338-297">Если получатель не указан, компилятор включает в статический контекст только статические элементы, а в противном случае — статические элементы и элементы экземпляра.</span><span class="sxs-lookup"><span data-stu-id="f5338-297">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="f5338-298">Если получатель невозможно однозначно определить как экземпляр или тип, компилятор включает и те, и другие элементы.</span><span class="sxs-lookup"><span data-stu-id="f5338-298">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="f5338-299">В статический контекст, в котором невозможно использовать неявный экземпляр-получатель `this`, включается текст тех элементов, для которых не определено `this`, например статические элементы, а также все места, где не может использоваться `this`, такие как инициализаторы полей и конструкторы-инициализаторы.</span><span class="sxs-lookup"><span data-stu-id="f5338-299">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="f5338-300">Если группа методов содержит некоторые универсальные методы, у которых аргументы типа не удовлетворяют ограничениям, такие элементы удаляются из набора кандидатов.</span><span class="sxs-lookup"><span data-stu-id="f5338-300">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="f5338-301">При преобразовании группы методов из набора удаляются методы-кандидаты, у которых возвращаемый тип не соответствует возвращаемому типу делегата.</span><span class="sxs-lookup"><span data-stu-id="f5338-301">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="f5338-302">Это изменение проявится только тем, что вы реже будете встречать ошибки компилятора о неоднозначной перегрузке методов в тех ситуациях, когда вы точно уверены в выборе лучшего метода.</span><span class="sxs-lookup"><span data-stu-id="f5338-302">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="f5338-303">Повышение эффективности безопасного кода</span><span class="sxs-lookup"><span data-stu-id="f5338-303">Enabling more efficient safe code</span></span>

<span data-ttu-id="f5338-304">Теперь вы сможете создавать безопасный код C#, который выполняется не хуже небезопасного кода.</span><span class="sxs-lookup"><span data-stu-id="f5338-304">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="f5338-305">Безопасный код позволяет избежать ошибок некоторых типов, таких как переполнение буфера, свободные указатели и другие ошибки доступа к памяти.</span><span class="sxs-lookup"><span data-stu-id="f5338-305">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="f5338-306">Новые функции расширяют возможности гарантированно безопасного кода.</span><span class="sxs-lookup"><span data-stu-id="f5338-306">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="f5338-307">Старайтесь как можно большую часть кода создавать из безопасных конструкций.</span><span class="sxs-lookup"><span data-stu-id="f5338-307">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="f5338-308">Благодаря новым возможностям это станет проще.</span><span class="sxs-lookup"><span data-stu-id="f5338-308">These features make that easier.</span></span>

<span data-ttu-id="f5338-309">В ту группу, которая отвечает за повышение производительности безопасного кода, входят следующие новые возможности:</span><span class="sxs-lookup"><span data-stu-id="f5338-309">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="f5338-310">доступ к полям фиксированной ширины без закрепления;</span><span class="sxs-lookup"><span data-stu-id="f5338-310">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="f5338-311">возможность переназначать локальные переменные `ref`;</span><span class="sxs-lookup"><span data-stu-id="f5338-311">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="f5338-312">возможность использовать инициализаторы для массивов `stackalloc`;</span><span class="sxs-lookup"><span data-stu-id="f5338-312">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="f5338-313">возможность использовать инструкции `fixed` с любым типом, который поддерживает шаблон;</span><span class="sxs-lookup"><span data-stu-id="f5338-313">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="f5338-314">возможность использовать дополнительные универсальные ограничения.</span><span class="sxs-lookup"><span data-stu-id="f5338-314">You can use additional generic constraints.</span></span>
- <span data-ttu-id="f5338-315">модификатор `in` для параметров, указывающий, что аргумент передается по ссылке, но не изменяется вызываемым методом;</span><span class="sxs-lookup"><span data-stu-id="f5338-315">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="f5338-316">Добавление модификатора `in` к аргументу является [изменением, совместимым на уровне исходного кода](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-316">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="f5338-317">модификатор `ref readonly` для возвращаемого значения метода, указывающий, что метод возвращает значение по ссылке, но не допускает операции записи в соответствующий объект;</span><span class="sxs-lookup"><span data-stu-id="f5338-317">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="f5338-318">Добавление модификатора `ref readonly` к аргументу является [изменением, совместимым на уровне исходного кода](version-update-considerations.md#source-compatible-changes), если оператору return присваивается значение.</span><span class="sxs-lookup"><span data-stu-id="f5338-318">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="f5338-319">Добавление модификатора `readonly` к существующему оператору return `ref` является [несовместимым изменением](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-319">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="f5338-320">Требуется указать вызывающие объекты, чтобы добавить модификатор `readonly` в объявление локальных переменных `ref`.</span><span class="sxs-lookup"><span data-stu-id="f5338-320">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="f5338-321">объявление `readonly struct`, указывающее, что структура является неизменяемой и должна передаваться в методы члена как параметр `in`;</span><span class="sxs-lookup"><span data-stu-id="f5338-321">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="f5338-322">Добавление модификатора `readonly` к существующему объявлению структуры является [двоично совместимым изменением](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-322">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="f5338-323">объявление `ref struct`, указывающее, что тип структуры обращается напрямую к управляемой памяти и всегда должен обрабатываться с выделением стека.</span><span class="sxs-lookup"><span data-stu-id="f5338-323">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="f5338-324">Добавление модификатора `ref` к существующему объявлению `struct` является [двоично совместимым изменением](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-324">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="f5338-325">Объект `ref struct` не может быть членом класса или использоваться в других местах, где он может выделяться в куче.</span><span class="sxs-lookup"><span data-stu-id="f5338-325">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="f5338-326">Дополнительные сведения обо всех эти изменениях см. в статье о том, как [писать безопасный и эффективный код](../write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-326">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

### <a name="ref-locals-and-returns"></a><span data-ttu-id="f5338-327">Локальные переменные и возвращаемые значения Ref</span><span class="sxs-lookup"><span data-stu-id="f5338-327">Ref locals and returns</span></span>

<span data-ttu-id="f5338-328">Эта функция активирует алгоритмы, которые используют и возвращают ссылки на переменные, определенные в другом месте.</span><span class="sxs-lookup"><span data-stu-id="f5338-328">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="f5338-329">В качестве примера можно привести работу с большими матрицами и поиск одного местоположения с определенными характеристиками.</span><span class="sxs-lookup"><span data-stu-id="f5338-329">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="f5338-330">Следующий метод возвращает **ссылку** на это хранилище в матрице:</span><span class="sxs-lookup"><span data-stu-id="f5338-330">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="f5338-331">Можно объявить возвращаемое значение как `ref` и изменять это значение в матрице, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="f5338-331">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="f5338-332">Язык C# включает правила, которые защищают вас от неправильного использования локальных переменных и возвращаемых значений `ref`:</span><span class="sxs-lookup"><span data-stu-id="f5338-332">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

- <span data-ttu-id="f5338-333">Необходимо добавить ключевое слово `ref` в сигнатуру метода и все инструкции `return` в методе.</span><span class="sxs-lookup"><span data-stu-id="f5338-333">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
  - <span data-ttu-id="f5338-334">Это позволяет уточнить, что метод возвращает значение по ссылке, во всех местах.</span><span class="sxs-lookup"><span data-stu-id="f5338-334">That makes it clear the method returns by reference throughout the method.</span></span>
- <span data-ttu-id="f5338-335">Объект `ref return` может быть назначен переменной-значению или переменной `ref`.</span><span class="sxs-lookup"><span data-stu-id="f5338-335">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
  - <span data-ttu-id="f5338-336">Вызывающий объект определяет, копируется ли возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="f5338-336">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="f5338-337">Пропуск модификатора `ref` при присваивании возвращаемого значения указывает, что вызывающий объект хочет получить копию значения, а не ссылку на хранилище.</span><span class="sxs-lookup"><span data-stu-id="f5338-337">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
- <span data-ttu-id="f5338-338">Присвоить локальной переменной `ref` стандартное возвращаемое значение метода невозможно.</span><span class="sxs-lookup"><span data-stu-id="f5338-338">You can't assign a standard method return value to a `ref` local variable.</span></span>
  - <span data-ttu-id="f5338-339">Это запрещает использовать операторы вида `ref int i = sequence.Count();`</span><span class="sxs-lookup"><span data-stu-id="f5338-339">That disallows statements like `ref int i = sequence.Count();`</span></span>
- <span data-ttu-id="f5338-340">Переменную `ref` невозможно возвращать переменной, которая продолжает существовать даже после того, как метод будет выполнен.</span><span class="sxs-lookup"><span data-stu-id="f5338-340">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
  - <span data-ttu-id="f5338-341">Это означает невозможность возвращения ссылки на локальную переменную или переменную с аналогичной областью.</span><span class="sxs-lookup"><span data-stu-id="f5338-341">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
- <span data-ttu-id="f5338-342">Возвращаемые значения и локальные переменные `ref` не могут использоваться с асинхронными методами.</span><span class="sxs-lookup"><span data-stu-id="f5338-342">`ref` locals and returns can't be used with async methods.</span></span>
  - <span data-ttu-id="f5338-343">На момент, когда асинхронный метод возвращает значение, компилятору неизвестно, присвоено ли переменной, на которую указывает ссылка, окончательное значение.</span><span class="sxs-lookup"><span data-stu-id="f5338-343">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="f5338-344">Добавление локальных переменных и возвращаемых значений ref дает возможность использовать более эффективные алгоритмы, поскольку избавляет от необходимости многократно копировать значения или выполнять операции разыменования.</span><span class="sxs-lookup"><span data-stu-id="f5338-344">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="f5338-345">Добавление `ref` для возврата значения является [изменением, совместимым на уровне исходного кода](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-345">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="f5338-346">Существующий код компилируется, но возвращаемое значение ссылочного типа копируется при назначении.</span><span class="sxs-lookup"><span data-stu-id="f5338-346">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="f5338-347">Вызывающие объекты должны изменить переменную хранилища для возвращаемого значения на локальную переменную `ref`, чтобы это значение хранилось в качестве ссылки.</span><span class="sxs-lookup"><span data-stu-id="f5338-347">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="f5338-348">Теперь локальные переменные `ref` можно переназначить другим экземплярам после инициализации.</span><span class="sxs-lookup"><span data-stu-id="f5338-348">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="f5338-349">Следующая команда теперь успешно компилируется:</span><span class="sxs-lookup"><span data-stu-id="f5338-349">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="f5338-350">Дополнительные сведения см. в статье о возвращаемых значениях [`ref` и локальных переменных `ref`](../programming-guide/classes-and-structs/ref-returns.md), а также в статье [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-350">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

<span data-ttu-id="f5338-351">Дополнительные сведения см. в статье [ref (Справочник по C#)](../language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-351">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

### <a name="conditional-ref-expressions"></a><span data-ttu-id="f5338-352">Условные выражения `ref`</span><span class="sxs-lookup"><span data-stu-id="f5338-352">Conditional `ref` expressions</span></span>

<span data-ttu-id="f5338-353">Результат условного выражения может быть ссылкой, а не значением.</span><span class="sxs-lookup"><span data-stu-id="f5338-353">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="f5338-354">Например, можно написать следующий код, чтобы получить ссылку на первый элемент в одном из двух массивов:</span><span class="sxs-lookup"><span data-stu-id="f5338-354">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="f5338-355">Переменная `r` — это ссылка на первое значение в `arr` или `otherArr`.</span><span class="sxs-lookup"><span data-stu-id="f5338-355">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="f5338-356">Дополнительные сведения см. в описании [условного оператора (?:)](../language-reference/operators/conditional-operator.md) в справочнике по языку.</span><span class="sxs-lookup"><span data-stu-id="f5338-356">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>

### <a name="in-parameter-modifier"></a><span data-ttu-id="f5338-357">Модификатор параметра `in`</span><span class="sxs-lookup"><span data-stu-id="f5338-357">`in` parameter modifier</span></span>

<span data-ttu-id="f5338-358">При передаче аргументов по ссылке можно использовать ключевое слово `in` как дополнение к существующим ключевым словам ref и out.</span><span class="sxs-lookup"><span data-stu-id="f5338-358">The `in` keyword complements the existing ref and out keywords to pass arguments by reference.</span></span> <span data-ttu-id="f5338-359">Ключевое слово `in` указывает, что аргумент передается по ссылке, но вызванный метод не изменяет это значение.</span><span class="sxs-lookup"><span data-stu-id="f5338-359">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="f5338-360">Перегрузки, передаваемые по значению или ссылке "только для чтения", можно объявлять, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="f5338-360">You may declare overloads that pass by value or by readonly reference, as shown in the following code:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="f5338-361">Перегрузка по значению (первая в предыдущем примере) считается лучше, чем перегрузка по атрибуту "только для чтения".</span><span class="sxs-lookup"><span data-stu-id="f5338-361">The by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="f5338-362">Чтобы вызвать версию со ссылочным аргументом "только для чтения", необходимо при вызове метода указать модификатор `in`.</span><span class="sxs-lookup"><span data-stu-id="f5338-362">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

<span data-ttu-id="f5338-363">Дополнительные сведения см. в статье, посвященной [модификатору параметра `in`](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-363">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="f5338-364">Больше типов поддерживают инструкцию `fixed`</span><span class="sxs-lookup"><span data-stu-id="f5338-364">More types support the `fixed` statement</span></span>

<span data-ttu-id="f5338-365">Инструкция `fixed` ранее поддерживала лишь ограниченный набор типов.</span><span class="sxs-lookup"><span data-stu-id="f5338-365">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="f5338-366">Начиная с C# 7.3 любой тип, содержащий метод `GetPinnableReference()`, который возвращает `ref T` или `ref readonly T`, может иметь инструкцию `fixed`.</span><span class="sxs-lookup"><span data-stu-id="f5338-366">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="f5338-367">Добавление этой возможности означает, что `fixed` можно применять для <xref:System.Span%601?displayProperty=nameWithType> и связанных типов.</span><span class="sxs-lookup"><span data-stu-id="f5338-367">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="f5338-368">Дополнительные сведения см. в статье [об инструкции `fixed`](../language-reference/keywords/fixed-statement.md) в справочнике по языку.</span><span class="sxs-lookup"><span data-stu-id="f5338-368">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="f5338-369">Индексирование полей `fixed` не требует закрепления</span><span class="sxs-lookup"><span data-stu-id="f5338-369">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="f5338-370">Давайте рассмотрим такую структуру:</span><span class="sxs-lookup"><span data-stu-id="f5338-370">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="f5338-371">В более ранних версиях C# переменную необходимо закрепить, чтобы получить доступ к целым числам, входящим в `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="f5338-371">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="f5338-372">Теперь приведенный ниже код компилируется без закрепления переменной `p` внутри отдельного оператора `fixed`:</span><span class="sxs-lookup"><span data-stu-id="f5338-372">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="f5338-373">Переменная `p` обращается к одному элементу в `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="f5338-373">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="f5338-374">Для этого не нужно объявлять отдельную переменную `int*`.</span><span class="sxs-lookup"><span data-stu-id="f5338-374">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="f5338-375">Контекст `unsafe` по-прежнему является обязательным.</span><span class="sxs-lookup"><span data-stu-id="f5338-375">You still need an `unsafe` context.</span></span> <span data-ttu-id="f5338-376">В более ранних версиях C# необходимо объявить второй фиксированный указатель:</span><span class="sxs-lookup"><span data-stu-id="f5338-376">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="f5338-377">Дополнительные сведения см. в статье, посвященной [инструкции `fixed`](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-377">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="f5338-378">Массивы `stackalloc` поддерживают инициализаторы</span><span class="sxs-lookup"><span data-stu-id="f5338-378">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="f5338-379">Раньше вы могли задавать значения для элементов массива при его инициализации:</span><span class="sxs-lookup"><span data-stu-id="f5338-379">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="f5338-380">Теперь такой же синтаксис можно применять к массивам, в объявлении которых есть `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="f5338-380">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="f5338-381">Дополнительные сведения см. в статье [Оператор `stackalloc`](../language-reference/operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-381">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="f5338-382">Расширенные универсальные ограничения</span><span class="sxs-lookup"><span data-stu-id="f5338-382">Enhanced generic constraints</span></span>

<span data-ttu-id="f5338-383">Теперь вы можете указать тип <xref:System.Enum?displayProperty=nameWithType> или <xref:System.Delegate?displayProperty=nameWithType> в качестве ограничения базового класса для параметра типа.</span><span class="sxs-lookup"><span data-stu-id="f5338-383">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="f5338-384">Вы также можете использовать новое ограничение `unmanaged`, чтобы указать, что параметр типа должен быть [неуправляемым типом](../language-reference/builtin-types/unmanaged-types.md), не допускающим значения NULL.</span><span class="sxs-lookup"><span data-stu-id="f5338-384">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="f5338-385">Дополнительные сведения см. в статьях [об универсальных ограничениях `where`](../language-reference/keywords/where-generic-type-constraint.md) и [ограничениях параметров типа](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-385">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="f5338-386">Добавление этих ограничений в существующие типы — это [несовместимое изменение](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="f5338-386">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="f5338-387">Закрытые универсальные типы не будут соответствовать подобным ограничениям.</span><span class="sxs-lookup"><span data-stu-id="f5338-387">Closed generic types may no longer meet these new constraints.</span></span>

### <a name="generalized-async-return-types"></a><span data-ttu-id="f5338-388">Обобщенные асинхронные типы возвращаемых значений</span><span class="sxs-lookup"><span data-stu-id="f5338-388">Generalized async return types</span></span>

<span data-ttu-id="f5338-389">В некоторых случаях возврат объекта `Task` из асинхронных методов может вызывать сложности.</span><span class="sxs-lookup"><span data-stu-id="f5338-389">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="f5338-390">`Task` — это тип ссылки, поэтому его применение означает распределение объекта.</span><span class="sxs-lookup"><span data-stu-id="f5338-390">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="f5338-391">В случаях, когда метод, объявленный с модификатором `async`, возвращает кэшированный результат или завершается синхронно, лишние распределения могут вызывать серьезные потери времени при выполнении фрагментов кода, зависящих от производительности.</span><span class="sxs-lookup"><span data-stu-id="f5338-391">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="f5338-392">Эта проблема встает серьезно, если распределения происходят в коротких циклах.</span><span class="sxs-lookup"><span data-stu-id="f5338-392">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="f5338-393">Новая возможность языка означает, что этот асинхронный метод возвращает типы, не ограниченные `Task`, `Task<T>` и `void`.</span><span class="sxs-lookup"><span data-stu-id="f5338-393">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="f5338-394">Возвращаемый тип должен по-прежнему соответствовать асинхронному шаблону, а значит, метод `GetAwaiter` должен быть доступен.</span><span class="sxs-lookup"><span data-stu-id="f5338-394">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="f5338-395">Конкретный пример. В .NET добавлен новый тип `ValueTask`, позволяющий применять эту новую возможность языка:</span><span class="sxs-lookup"><span data-stu-id="f5338-395">As one concrete example, the `ValueTask` type has been added to .NET to make use of this new language feature:</span></span>

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="f5338-396">Чтобы использовать тип <xref:System.Threading.Tasks.ValueTask%601>, необходимо добавить пакет NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) >.</span><span class="sxs-lookup"><span data-stu-id="f5338-396">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="f5338-397">Это улучшение особенно полезно для авторов библиотек, которые хотят избежать выделения `Task` в критическом по производительности коде.</span><span class="sxs-lookup"><span data-stu-id="f5338-397">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="f5338-398">Новые параметры компилятора</span><span class="sxs-lookup"><span data-stu-id="f5338-398">New compiler options</span></span>

<span data-ttu-id="f5338-399">Новые параметры компилятора поддерживают сценарии сборки и DevOps для программ на C#.</span><span class="sxs-lookup"><span data-stu-id="f5338-399">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="reference-assembly-generation"></a><span data-ttu-id="f5338-400">Создание базовой сборки</span><span class="sxs-lookup"><span data-stu-id="f5338-400">Reference assembly generation</span></span>

<span data-ttu-id="f5338-401">Существует два новых параметра компилятора, которые создают *только базовые сборки*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) и [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-401">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f5338-402">В соответствующих статьях подробно рассматриваются эти параметры и базовые сборки.</span><span class="sxs-lookup"><span data-stu-id="f5338-402">The linked articles explain these options and reference assemblies in more detail.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="f5338-403">Подписывание открытым ключом или с открытым исходным кодом</span><span class="sxs-lookup"><span data-stu-id="f5338-403">Public or Open Source signing</span></span>

<span data-ttu-id="f5338-404">Параметр компилятора `-publicsign` указывает, что сборку нужно подписать открытым ключом.</span><span class="sxs-lookup"><span data-stu-id="f5338-404">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="f5338-405">Такая сборка будет помечена как подписанная, но подпись для нее берется из открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="f5338-405">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="f5338-406">Этот параметр позволяет создавать подписанные сборки из проектов с открытым кодом с помощью открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="f5338-406">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="f5338-407">Дополнительные сведения см. в статье [о параметре компилятора -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-407">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="f5338-408">pathmap</span><span class="sxs-lookup"><span data-stu-id="f5338-408">pathmap</span></span>

<span data-ttu-id="f5338-409">Параметр компилятора `-pathmap` указывает, что исходные пути в среде создания следует заменить сопоставленными исходными путями.</span><span class="sxs-lookup"><span data-stu-id="f5338-409">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="f5338-410">Параметр `-pathmap` управляет исходными путями, которые компилятор записывает в PDB-файлы или для <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f5338-410">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="f5338-411">Дополнительные сведения см. в статье [о параметре компилятора -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-411">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
