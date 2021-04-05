---
description: Сведения о различных директивах препроцессора C#, которые управляют условной компиляцией, предупреждениями, анализом объектов, допускающих значение NULL, и многим другим.
title: Директивы препроцессора C#
ms.date: 03/17/2021
f1_keywords:
- cs.preprocessor
- '#nullable'
- '#if'
- '#else'
- '#elif'
- '#endif'
- '#define'
- '#undef'
- '#warning'
- '#error'
- '#line'
- '#region'
- '#endregion'
- '#pragma'
- '#pragma warning'
- '#pragma checksum'
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
- '#nullable directive [C#]'
- '#if directive [C#]'
- '#else directive [C#]'
- '#elif directive [C#]'
- '#endif directive [C#]'
- '#define directive [C#]'
- '#undef directive [C#]'
- '#warning directive [C#]'
- '#error directive [C#]'
- '#line directive [C#]'
- '#region directive [C#]'
- '#endregion directive [C#]'
- '#pragma directive [C#]'
- '#pragma warning [C#]'
- '#pragma checksum [C#]'
ms.openlocfilehash: 373952282a684da25414af9853e18b7bc4874108
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637662"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="a64da-103">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="a64da-103">C# preprocessor directives</span></span>

<span data-ttu-id="a64da-104">Хотя у компилятора нет отдельного препроцессора, директивы, описанные в этом разделе, обрабатываются так, как если бы он был.</span><span class="sxs-lookup"><span data-stu-id="a64da-104">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="a64da-105">Они используются в условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="a64da-105">You use them to help in conditional compilation.</span></span> <span data-ttu-id="a64da-106">В отличие от директив C и C++ вы не можете использовать их для создания макросов.</span><span class="sxs-lookup"><span data-stu-id="a64da-106">Unlike C and C++ directives, you can't use these directives to create macros.</span></span> <span data-ttu-id="a64da-107">Директива препроцессора должна быть единственной инструкцией в строке.</span><span class="sxs-lookup"><span data-stu-id="a64da-107">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="nullable-context"></a><span data-ttu-id="a64da-108">Контекст, допускающий значение NULL</span><span class="sxs-lookup"><span data-stu-id="a64da-108">Nullable context</span></span>

<span data-ttu-id="a64da-109">Директива препроцессора `#nullable` устанавливает контекст с *заметками о допустимости значений NULL* и *контекст с предупреждениями о допустимости значений NULL*.</span><span class="sxs-lookup"><span data-stu-id="a64da-109">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="a64da-110">Эта директива определяет, действуют ли заметки, допускающие значение NULL, и могут ли быть заданы предупреждения о допустимости значений NULL.</span><span class="sxs-lookup"><span data-stu-id="a64da-110">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="a64da-111">Каждый контекст либо *отключен*, либо *включен*.</span><span class="sxs-lookup"><span data-stu-id="a64da-111">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="a64da-112">Оба контекста можно указать на уровне проекта (за пределами исходного кода C#).</span><span class="sxs-lookup"><span data-stu-id="a64da-112">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="a64da-113">Директива `#nullable` управляет контекстами заметок и предупреждений и имеет приоритет над параметрами уровня проекта.</span><span class="sxs-lookup"><span data-stu-id="a64da-113">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="a64da-114">Директива задает контексты, которыми управляет, пока другая директива не переопределит ее, или до конца исходного файла.</span><span class="sxs-lookup"><span data-stu-id="a64da-114">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="a64da-115">Ниже приведены результаты использования директив:</span><span class="sxs-lookup"><span data-stu-id="a64da-115">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="a64da-116">`#nullable disable`: задает контексты с заметками и предупреждениями о допустимости значения NULL в значение *отключено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-116">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="a64da-117">`#nullable enable`: задает контексты с заметками и предупреждениями о допустимости значения NULL в значение *включено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-117">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="a64da-118">`#nullable restore`: восстанавливает контексты с заметками и предупреждениями о допустимости значения NULL до параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="a64da-118">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="a64da-119">`#nullable disable annotations`: устанавливает контекст с заметками о допустимости значения NULL в режим *отключено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-119">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="a64da-120">`#nullable enable annotations`: устанавливает контекст с заметками о допустимости значения NULL в режим *включено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-120">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="a64da-121">`#nullable restore annotations`: восстанавливает контексты с заметками о допустимости значения NULL до параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="a64da-121">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="a64da-122">`#nullable disable warnings`: устанавливает контекст с предупреждениями о допустимости значения NULL в режим *отключено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-122">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="a64da-123">`#nullable enable warnings`: устанавливает контекст с предупреждениями о допустимости значения NULL в режим *включено*.</span><span class="sxs-lookup"><span data-stu-id="a64da-123">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="a64da-124">`#nullable restore warnings`: восстанавливает контексты с предупреждениями о допустимости значения NULL до параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="a64da-124">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="conditional-compilation"></a><span data-ttu-id="a64da-125">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="a64da-125">Conditional compilation</span></span>

<span data-ttu-id="a64da-126">Для управления условной компиляцией используются четыре директивы препроцессора.</span><span class="sxs-lookup"><span data-stu-id="a64da-126">You use four preprocessor directives to control conditional compilation:</span></span>

- <span data-ttu-id="a64da-127">`#if`: открывает условную компиляцию, где код компилируется, только если определен указанный символ.</span><span class="sxs-lookup"><span data-stu-id="a64da-127">`#if`: Opens a conditional compilation, where code is compiled only if the specified symbol is defined.</span></span>
- <span data-ttu-id="a64da-128">`#elif`: закрывает предыдущую условную компиляцию и открывает новую на основе того, определен ли указанный символ.</span><span class="sxs-lookup"><span data-stu-id="a64da-128">`#elif`: Closes the preceding conditional compilation and opens a new conditional compilation based on if the specified symbol is defined.</span></span>
- <span data-ttu-id="a64da-129">`#else`: закрывает предыдущую условную компиляцию и открывает новую, если указанный символ не определен.</span><span class="sxs-lookup"><span data-stu-id="a64da-129">`#else`: Closes the preceding conditional compilation and opens a new conditional compilation if the previous specified symbol isn't defined.</span></span>
- <span data-ttu-id="a64da-130">`#endif`: закрывает предыдущую условную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="a64da-130">`#endif`: Closes the preceding conditional compilation.</span></span>

<span data-ttu-id="a64da-131">Когда компилятор C# встречает директиву `#if`, за которой следует директива `#endif`, код между этими директивами он компилирует, только когда определен указанный символ.</span><span class="sxs-lookup"><span data-stu-id="a64da-131">When the C# compiler finds an `#if` directive, followed eventually by an `#endif` directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="a64da-132">В отличие от С и С++ здесь невозможно назначить символу числовое значение.</span><span class="sxs-lookup"><span data-stu-id="a64da-132">Unlike C and C++, you can't assign a numeric value to a symbol.</span></span> <span data-ttu-id="a64da-133">Оператор `#if` в C# является логическим. Он проверяет только одно условие — определен ли указанный символ.</span><span class="sxs-lookup"><span data-stu-id="a64da-133">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="a64da-134">Пример:</span><span class="sxs-lookup"><span data-stu-id="a64da-134">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="a64da-135">Вы можете использовать операторы [`==` (равенство)](operators/equality-operators.md#equality-operator-) и [`!=` (неравенство)](operators/equality-operators.md#inequality-operator-) для проверки значений [`bool`](builtin-types/bool.md) `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="a64da-135">You can use the operators [`==` (equality)](operators/equality-operators.md#equality-operator-) and [`!=` (inequality)](operators/equality-operators.md#inequality-operator-) to test for the [`bool`](builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="a64da-136">Значение `true` означает, что символ определен.</span><span class="sxs-lookup"><span data-stu-id="a64da-136">`true` means the symbol is defined.</span></span> <span data-ttu-id="a64da-137">Инструкция `#if DEBUG` имеет то же значение, что и `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="a64da-137">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="a64da-138">Вы можете использовать операторы [`&&` (и)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [`||` (или)](operators/boolean-logical-operators.md#conditional-logical-or-operator-) и [`!` (не)](operators/boolean-logical-operators.md#logical-negation-operator-), чтобы узнать, определено ли несколько символов.</span><span class="sxs-lookup"><span data-stu-id="a64da-138">You can use the [`&&` (and)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [`||` (or)](operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [`!` (not)](operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="a64da-139">Можно также группировать символы и операторы при помощи скобок.</span><span class="sxs-lookup"><span data-stu-id="a64da-139">You can also group symbols and operators with parentheses.</span></span>

<span data-ttu-id="a64da-140">`#if`, как и директивы `#else`, `#elif`, `#endif`, `#define` и `#undef`, позволяет включить или исключить код в зависимости от существования одного или нескольких символов.</span><span class="sxs-lookup"><span data-stu-id="a64da-140">`#if`, along with the `#else`, `#elif`, `#endif`, `#define`, and `#undef` directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="a64da-141">Условная компиляция может быть полезной при компиляции кода для отладочной сборки или для определенной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a64da-141">Conditional compilation can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="a64da-142">Условные директивы, начинающиеся с директивы `#if`, должны явным образом завершаться директивой `#endif`.</span><span class="sxs-lookup"><span data-stu-id="a64da-142">A conditional directive beginning with an `#if` directive must explicitly be terminated with an `#endif` directive.</span></span> <span data-ttu-id="a64da-143">`#define` позволяет определить символ,</span><span class="sxs-lookup"><span data-stu-id="a64da-143">`#define` lets you define a symbol.</span></span> <span data-ttu-id="a64da-144">чтобы выражение, в качестве которого этот символ передается в директиву `#if`, при вычислении давало значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a64da-144">By using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span> <span data-ttu-id="a64da-145">Символ также можно определить с помощью параметра компилятора [**DefineConstants**](compiler-options/language.md#defineconstants).</span><span class="sxs-lookup"><span data-stu-id="a64da-145">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="a64da-146">Для отмены определения символа служит директива `#undef`.</span><span class="sxs-lookup"><span data-stu-id="a64da-146">You can undefine a symbol with `#undef`.</span></span> <span data-ttu-id="a64da-147">Символ, создаваемый с помощью `#define`, будет определен в пределах того файл, в котором он определен.</span><span class="sxs-lookup"><span data-stu-id="a64da-147">The scope of a symbol created with `#define` is the file in which it was defined.</span></span> <span data-ttu-id="a64da-148">Символ, определенный с помощью **DefineConstants** или `#define`, не конфликтует с одноименной переменной.</span><span class="sxs-lookup"><span data-stu-id="a64da-148">A symbol that you define with **DefineConstants** or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="a64da-149">Соответственно, имя переменной не должно передаваться директиве препроцессора, а символ может использоваться только в директиве препроцессора.</span><span class="sxs-lookup"><span data-stu-id="a64da-149">That is, a variable name shouldn't be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="a64da-150">Директива `#elif` позволяет создать составную условную директиву.</span><span class="sxs-lookup"><span data-stu-id="a64da-150">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="a64da-151">Выражение `#elif` будет вычисляться в том случае, если ни одна из предшествующих директив `#if` или необязательных директив `#elif` после вычисления выражения не возвращает значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a64da-151">The `#elif` expression will be evaluated if neither the preceding `#if` nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="a64da-152">Если после вычисления выражения `#elif` возвращается значение `true`, компилятор вычисляет весь код между директивой `#elif` и следующей условной директивой.</span><span class="sxs-lookup"><span data-stu-id="a64da-152">If an `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="a64da-153">Пример:</span><span class="sxs-lookup"><span data-stu-id="a64da-153">For example:</span></span>

```csharp
#define VC7
//...
#if debug
    Console.WriteLine("Debug build");
#elif VC7
    Console.WriteLine("Visual Studio 7");
#endif
```

<span data-ttu-id="a64da-154">С помощью директивы `#else` можно создать составную условную директиву со следующим поведением: если ни одно из выражений в предшествующих директивах `#if` или (необязательно) `#elif` не принимает значение `true`, компилятор вычисляет код между директивой `#else` и последующей директивой `#endif`.</span><span class="sxs-lookup"><span data-stu-id="a64da-154">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding `#if` or (optional) `#elif` directives evaluate to `true`, the compiler will evaluate all code between `#else` and the next `#endif`.</span></span> <span data-ttu-id="a64da-155">Директива `#endif` обязательно указывается в качестве следующей директивы препроцессора после `#else`.</span><span class="sxs-lookup"><span data-stu-id="a64da-155">`#endif`(#endif) must be the next preprocessor directive after `#else`.</span></span>

<span data-ttu-id="a64da-156">`#endif` указывает на конец условной директивы, начало которой было задано с помощью директивы `#if`.</span><span class="sxs-lookup"><span data-stu-id="a64da-156">`#endif` specifies the end of a conditional directive, which began with the `#if` directive.</span></span>

<span data-ttu-id="a64da-157">Система сборки также учитывает символы препроцессора, представляющие [целевые платформы](../../standard/frameworks.md) в проектах в стиле SDK.</span><span class="sxs-lookup"><span data-stu-id="a64da-157">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="a64da-158">Они полезны при создании приложений, предназначенных для нескольких версий .NET.</span><span class="sxs-lookup"><span data-stu-id="a64da-158">They're useful when creating applications that can target more than one .NET version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="a64da-159">Для традиционных проектов, в которых не используется пакет SDK, необходимо вручную настроить символы условной компиляции для различных целевых платформ в Visual Studio с помощью страниц свойств проекта.</span><span class="sxs-lookup"><span data-stu-id="a64da-159">For traditional, non-SDK-style projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="a64da-160">Другие предопределенные символы включают константы `DEBUG` и `TRACE`.</span><span class="sxs-lookup"><span data-stu-id="a64da-160">Other predefined symbols include the `DEBUG` and `TRACE` constants.</span></span> <span data-ttu-id="a64da-161">Вы можете переопределить значения для проектов с помощью `#define`.</span><span class="sxs-lookup"><span data-stu-id="a64da-161">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="a64da-162">Например, символ DEBUG автоматически устанавливается в зависимости от свойств конфигурации сборки (в режиме отладки или выпуска).</span><span class="sxs-lookup"><span data-stu-id="a64da-162">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

<span data-ttu-id="a64da-163">В следующем примере показано, как определить символ `MYTEST` в файле и затем протестировать значения символов `MYTEST` и `DEBUG`.</span><span class="sxs-lookup"><span data-stu-id="a64da-163">The following example shows you how to define a `MYTEST` symbol on a file and then test the values of the `MYTEST` and `DEBUG` symbols.</span></span> <span data-ttu-id="a64da-164">Выходные данные этого примера зависят от режима конфигурации, в котором создан проект (**Отладка** или **Выпуск**).</span><span class="sxs-lookup"><span data-stu-id="a64da-164">The output of this example depends on whether you built the project on **Debug** or **Release** configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="a64da-165">В следующем примере показано, как тестировать разные целевые платформы для использования более новых интерфейсов API, когда это возможно:</span><span class="sxs-lookup"><span data-stu-id="a64da-165">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="defining-symbols"></a><span data-ttu-id="a64da-166">Определение символов</span><span class="sxs-lookup"><span data-stu-id="a64da-166">Defining symbols</span></span>

<span data-ttu-id="a64da-167">Используйте следующие две директивы препроцессора, чтобы определить или отменить определение символов для условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="a64da-167">You use the following two preprocessor directives to define or undefine symbols for conditional compilation:</span></span>

- <span data-ttu-id="a64da-168">`#define`: определение символа.</span><span class="sxs-lookup"><span data-stu-id="a64da-168">`#define`: Define a symbol.</span></span>
- <span data-ttu-id="a64da-169">`#undef`: отмена определения символа.</span><span class="sxs-lookup"><span data-stu-id="a64da-169">`#undef`: undefine a symbol.</span></span>

<span data-ttu-id="a64da-170">`#define` позволяет определить символ.</span><span class="sxs-lookup"><span data-stu-id="a64da-170">You use `#define` to define a symbol.</span></span> <span data-ttu-id="a64da-171">При использовании символа в качестве выражения, которое передается директиве `#if`, выражение будет иметь значение `true`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="a64da-171">When you use the symbol as the expression that's passed to the `#if` directive, the expression will evaluate to `true`, as the following example shows:</span></span>

 ```csharp
 #define VERBOSE

#if VERBOSE
    Console.WriteLine("Verbose output version");
#endif

 ```

> [!NOTE]
> <span data-ttu-id="a64da-172">Директиву `#define` нельзя использовать для объявления значений констант, как это обычно делается в C и C++.</span><span class="sxs-lookup"><span data-stu-id="a64da-172">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="a64da-173">Для определения констант в C# следует использовать статические элементы класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a64da-173">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="a64da-174">При наличии нескольких констант имеет смысл создать для них отдельный класс "Constants".</span><span class="sxs-lookup"><span data-stu-id="a64da-174">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>

<span data-ttu-id="a64da-175">Символы можно использовать для указания условий компиляции.</span><span class="sxs-lookup"><span data-stu-id="a64da-175">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="a64da-176">Для проверки символов можно использовать директивы `#if` или `#elif`.</span><span class="sxs-lookup"><span data-stu-id="a64da-176">You can test for the symbol with either `#if` or `#elif`.</span></span> <span data-ttu-id="a64da-177">Для условной компиляции также можно использовать <xref:System.Diagnostics.ConditionalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a64da-177">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span> <span data-ttu-id="a64da-178">Вы можете определить символ, но не можете присвоить символу значение.</span><span class="sxs-lookup"><span data-stu-id="a64da-178">You can define a symbol, but you can't assign a value to a symbol.</span></span> <span data-ttu-id="a64da-179">Директива `#define` должна находиться в файле перед использованием любых инструкций, которые также не являются директивами препроцессора.</span><span class="sxs-lookup"><span data-stu-id="a64da-179">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span> <span data-ttu-id="a64da-180">Символ также можно определить с помощью параметра компилятора [**DefineConstants**](compiler-options/language.md#defineconstants).</span><span class="sxs-lookup"><span data-stu-id="a64da-180">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="a64da-181">Для отмены определения символа служит директива `#undef`.</span><span class="sxs-lookup"><span data-stu-id="a64da-181">You can undefine a symbol with `#undef`.</span></span>

## <a name="defining-regions"></a><span data-ttu-id="a64da-182">Определение областей</span><span class="sxs-lookup"><span data-stu-id="a64da-182">Defining regions</span></span>

<span data-ttu-id="a64da-183">Вы можете определить области кода, которые можно свернуть в структуру, используя следующие две директивы препроцессора.</span><span class="sxs-lookup"><span data-stu-id="a64da-183">You can define regions of code that can be collapsed in an outline using the following two preprocessor directives:</span></span>

- <span data-ttu-id="a64da-184">`#region`: начало области.</span><span class="sxs-lookup"><span data-stu-id="a64da-184">`#region`: Start a region.</span></span>
- <span data-ttu-id="a64da-185">`#endregion`: конец области.</span><span class="sxs-lookup"><span data-stu-id="a64da-185">`#endregion`: End a region</span></span>

<span data-ttu-id="a64da-186">Директива `#region` позволяет указать блок кода, который можно разворачивать и сворачивать с помощью функции [структурирования](/visualstudio/ide/outlining) в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="a64da-186">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="a64da-187">В больших файлах кода удобно сворачивать или скрывать одну область или несколько, чтобы не отвлекаться от той части файла, над которой в настоящее время идет работа.</span><span class="sxs-lookup"><span data-stu-id="a64da-187">In longer code files, it's convenient to collapse or hide one or more regions so that you can focus on the part of the file that you're currently working on.</span></span> <span data-ttu-id="a64da-188">В следующем примере показано, как определить область:</span><span class="sxs-lookup"><span data-stu-id="a64da-188">The following example shows how to define a region:</span></span>

```csharp
#region MyClass definition
public class MyClass
{
    static void Main()
    {
    }
}
#endregion
```

<span data-ttu-id="a64da-189">В конце блока `#region` должна присутствовать директива `#endregion`.</span><span class="sxs-lookup"><span data-stu-id="a64da-189">A `#region` block must be terminated with an `#endregion` directive.</span></span> <span data-ttu-id="a64da-190">Блок `#region` не может накладываться на блок `#if`.</span><span class="sxs-lookup"><span data-stu-id="a64da-190">A `#region` block can't overlap with an `#if` block.</span></span> <span data-ttu-id="a64da-191">Однако блок `#region` можно вложить в блок `#if`, а блок `#if` — в блок `#region`.</span><span class="sxs-lookup"><span data-stu-id="a64da-191">However, a `#region` block can be nested in an `#if` block, and an `#if` block can be nested in a `#region` block.</span></span>

## <a name="error-and-warning-information"></a><span data-ttu-id="a64da-192">Сведения об ошибках и предупреждениях</span><span class="sxs-lookup"><span data-stu-id="a64da-192">Error and warning information</span></span>

<span data-ttu-id="a64da-193">Вы указываете компилятору создавать определенные пользователем ошибки и предупреждения компилятора, а также управлять сведениями о строках с помощью следующих директив.</span><span class="sxs-lookup"><span data-stu-id="a64da-193">You instruct the compiler to generate user-defined compiler errors and warnings, and control line information using the following directives:</span></span>

- <span data-ttu-id="a64da-194">`#error`: создание ошибки компилятора с указанным сообщением.</span><span class="sxs-lookup"><span data-stu-id="a64da-194">`#error`: Generate a compiler error with a specified message.</span></span>
- <span data-ttu-id="a64da-195">`#warning`: создание предупреждения компилятора с конкретным сообщением.</span><span class="sxs-lookup"><span data-stu-id="a64da-195">`#warning`: Generate a compiler warning, with a specific message.</span></span>
- <span data-ttu-id="a64da-196">`#line`: изменение номера строки, выводимого с сообщениями компилятора.</span><span class="sxs-lookup"><span data-stu-id="a64da-196">`#line`: Change the line number printed with compiler messages.</span></span>

<span data-ttu-id="a64da-197">`#error` позволяет создать определяемую пользователем ошибку [CS1029](compiler-messages/cs1029.md) из определенного места в коде.</span><span class="sxs-lookup"><span data-stu-id="a64da-197">`#error` lets you generate a [CS1029](compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="a64da-198">Пример:</span><span class="sxs-lookup"><span data-stu-id="a64da-198">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="a64da-199">Компилятор обрабатывает `#error version` особым образом и сообщает об ошибке компилятора CS8304 с сообщением, содержащим используемые версии компилятора и языка.</span><span class="sxs-lookup"><span data-stu-id="a64da-199">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

<span data-ttu-id="a64da-200">`#warning` позволяет создать предупреждение компилятора [CS1030](../misc/cs1030.md) первого уровня из определенного места в коде.</span><span class="sxs-lookup"><span data-stu-id="a64da-200">`#warning` lets you generate a [CS1030](../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="a64da-201">Пример:</span><span class="sxs-lookup"><span data-stu-id="a64da-201">For example:</span></span>

```csharp
#warning Deprecated code in this method.
```

<span data-ttu-id="a64da-202">Директива `#line` позволяет изменять номер строки компилятора и при необходимости имя файла, в который будут выводиться ошибки и предупреждения.</span><span class="sxs-lookup"><span data-stu-id="a64da-202">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="a64da-203">В следующем примере показано, как включить в отчет два предупреждения, связанные с номерами строк.</span><span class="sxs-lookup"><span data-stu-id="a64da-203">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="a64da-204">Директива `#line 200` принудительно устанавливает номер следующей строки 200 (по умолчанию используется номер 6). До выполнения следующей директивы `#line` в отчете будет указываться имя файла Special.</span><span class="sxs-lookup"><span data-stu-id="a64da-204">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="a64da-205">Директива `#line default` по умолчанию восстанавливает нумерацию строк в исходное состояние с учетом строк, номера которых были изменены с помощью предшествующей директивы.</span><span class="sxs-lookup"><span data-stu-id="a64da-205">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="a64da-206">В результате компиляции формируются следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="a64da-206">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

<span data-ttu-id="a64da-207">Директива `#line` может использоваться на автоматизированном промежуточном этапе процесса построения.</span><span class="sxs-lookup"><span data-stu-id="a64da-207">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="a64da-208">Например, если строки были удалены из первоначального файла с исходным кодом, но вам по-прежнему требуется создавать выходные файлы компилятора на основе изначальной нумерации строк в файле, можно удалить строки и затем смоделировать их первичную нумерацию с помощью директивы `#line`.</span><span class="sxs-lookup"><span data-stu-id="a64da-208">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="a64da-209">Директива `#line hidden` скрывает последующие строки для отладчика. В этом случае при пошаговой проверке кода разработчиком все строки между `#line hidden` и следующей директивой `#line` (кроме случаев, когда это также директива `#line hidden`) будут пропущены.</span><span class="sxs-lookup"><span data-stu-id="a64da-209">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it isn't another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="a64da-210">Этот параметр также можно использовать для того, чтобы дать ASP.NET возможность различать определяемый пользователем и создаваемый компьютером код.</span><span class="sxs-lookup"><span data-stu-id="a64da-210">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="a64da-211">В основном эта функция используется в ASP.NET, но также может быть полезна и в других генераторах исходного кода.</span><span class="sxs-lookup"><span data-stu-id="a64da-211">Although ASP.NET is the primary consumer of this feature, it's likely that more source generators will make use of it.</span></span>

<span data-ttu-id="a64da-212">Директива `#line hidden` не влияет на имена файлов и номера строк в отчетах об ошибках.</span><span class="sxs-lookup"><span data-stu-id="a64da-212">A `#line hidden` directive doesn't affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="a64da-213">Это значит, что при обнаружении ошибки в скрытом блоке компилятор укажет в отчете текущие имя файла и номер строки, где найдена ошибка.</span><span class="sxs-lookup"><span data-stu-id="a64da-213">That is, if the compiler finds an error in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="a64da-214">Директива `#line filename` задает имя файла, которое будет отображаться в выходных данных компилятора.</span><span class="sxs-lookup"><span data-stu-id="a64da-214">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="a64da-215">По умолчанию используется фактическое имя файла с исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="a64da-215">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="a64da-216">Имя файла должно заключаться в двойные кавычки (" "). Перед ним должен указываться номер строки.</span><span class="sxs-lookup"><span data-stu-id="a64da-216">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="a64da-217">В следующем примере демонстрируется, как отладчик игнорирует скрытые строки кода.</span><span class="sxs-lookup"><span data-stu-id="a64da-217">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="a64da-218">При выполнении этого примера будут показаны три строки текста.</span><span class="sxs-lookup"><span data-stu-id="a64da-218">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="a64da-219">Тем не менее, если задать точку останова, как показано в этом примере, и нажать клавишу F10 для пошаговой отладки кода, отладчик игнорирует скрытую строку.</span><span class="sxs-lookup"><span data-stu-id="a64da-219">However, when you set a break point, as shown in the example, and hit F10 to step through the code, the debugger ignores the hidden line.</span></span> <span data-ttu-id="a64da-220">Даже если точка останова установлена на скрытой строке, отладчик по-прежнему будет игнорировать ее.</span><span class="sxs-lookup"><span data-stu-id="a64da-220">Even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="pragmas"></a><span data-ttu-id="a64da-221">Директивы pragma</span><span class="sxs-lookup"><span data-stu-id="a64da-221">Pragmas</span></span>

<span data-ttu-id="a64da-222">Директива `#pragma` предоставляет компилятору специальные инструкции для компиляции файла, в котором она появляется.</span><span class="sxs-lookup"><span data-stu-id="a64da-222">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="a64da-223">Компилятор должен поддерживать эти инструкции.</span><span class="sxs-lookup"><span data-stu-id="a64da-223">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="a64da-224">Другими словами, директиву `#pragma` невозможно использовать для создания настраиваемых инструкций предварительной обработки.</span><span class="sxs-lookup"><span data-stu-id="a64da-224">In other words, you can't use `#pragma` to create custom preprocessing instructions.</span></span>
  
- <span data-ttu-id="a64da-225">[`#pragma warning`](#pragma-warning): включение или отключение предупреждений.</span><span class="sxs-lookup"><span data-stu-id="a64da-225">[`#pragma warning`](#pragma-warning): Enable or disable warnings.</span></span>
- <span data-ttu-id="a64da-226">[`#pragma checksum`](#pragma-checksum): создание контрольной суммы.</span><span class="sxs-lookup"><span data-stu-id="a64da-226">[`#pragma checksum`](#pragma-checksum): Generate a checksum.</span></span>

```csharp
#pragma pragma-name pragma-arguments
```

<span data-ttu-id="a64da-227">`pragma-name` — имя распознанной прагмы, а `pragma-arguments` — аргументы, относящиеся к прагме.</span><span class="sxs-lookup"><span data-stu-id="a64da-227">Where `pragma-name` is the name of a recognized pragma and `pragma-arguments` is the pragma-specific arguments.</span></span>

### <a name="pragma-warning"></a><span data-ttu-id="a64da-228">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="a64da-228">#pragma warning</span></span>

<span data-ttu-id="a64da-229">`#pragma warning` может включать или отключать определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="a64da-229">`#pragma warning` can enable or disable certain warnings.</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

<span data-ttu-id="a64da-230">`warning-list` — список номеров предупреждений с разделителем-запятой.</span><span class="sxs-lookup"><span data-stu-id="a64da-230">Where `warning-list` is a comma-separated list of warning numbers.</span></span> <span data-ttu-id="a64da-231">Префикс CS является необязательным.</span><span class="sxs-lookup"><span data-stu-id="a64da-231">The "CS" prefix is optional.</span></span> <span data-ttu-id="a64da-232">Если номера предупреждений не указаны, `disable` отключает все предупреждения, а `restore` включает все предупреждения.</span><span class="sxs-lookup"><span data-stu-id="a64da-232">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="a64da-233">Чтобы найти номера предупреждений в Visual Studio, выполните сборку проекта, а затем поиск номеров предупреждений в окне **Вывод**.</span><span class="sxs-lookup"><span data-stu-id="a64da-233">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

<span data-ttu-id="a64da-234">Параметр `disable` вступает в силу, начиная со следующей строки исходного файла.</span><span class="sxs-lookup"><span data-stu-id="a64da-234">The `disable` takes effect beginning on the next line of the source file.</span></span> <span data-ttu-id="a64da-235">Предупреждение восстанавливается в строке после `restore`.</span><span class="sxs-lookup"><span data-stu-id="a64da-235">The warning is restored on the line following the `restore`.</span></span> <span data-ttu-id="a64da-236">Если в файле нет `restore`, предупреждения восстанавливаются до их состояния по умолчанию в первой строке всех последующих файлов в той же компиляции.</span><span class="sxs-lookup"><span data-stu-id="a64da-236">If there's no `restore` in the file, the warnings are restored to their default state at the first line of any later files in the same compilation.</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

### <a name="pragma-checksum"></a><span data-ttu-id="a64da-237">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="a64da-237">#pragma checksum</span></span>

<span data-ttu-id="a64da-238">Создает контрольные суммы для исходных файлов, чтобы помочь с отладкой страниц ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a64da-238">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>

```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"
```

<span data-ttu-id="a64da-239">`"filename"` — это имя файла, для которого требуется наблюдение за изменениями или обновлениями, `"{guid}"` — глобальный уникальный идентификатор (GUID) для хэш-алгоритма, а `"checksum_bytes"` — строка шестнадцатеричных цифр, представляющих байты контрольной суммы.</span><span class="sxs-lookup"><span data-stu-id="a64da-239">Where `"filename"` is the name of the file that requires monitoring for changes or updates, `"{guid}"` is the Globally Unique Identifier (GUID) for the hash algorithm, and `"checksum_bytes"` is the string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="a64da-240">Должно быть четным числом шестнадцатеричных цифр.</span><span class="sxs-lookup"><span data-stu-id="a64da-240">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="a64da-241">Нечетное число цифр приведет к выводу предупреждения во время компиляции, и директива будет пропущена.</span><span class="sxs-lookup"><span data-stu-id="a64da-241">An odd number of digits results in a compile-time warning, and the directive is ignored.</span></span>

<span data-ttu-id="a64da-242">Отладчик Visual Studio использует контрольную сумму, чтобы подтвердить нахождение правильного источника.</span><span class="sxs-lookup"><span data-stu-id="a64da-242">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="a64da-243">Компилятор вычисляет контрольную сумму для исходного файла, а затем передает результат в файл базы данных (PDB) программы.</span><span class="sxs-lookup"><span data-stu-id="a64da-243">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="a64da-244">Отладчик затем использует PDB-файл для сравнения с контрольной суммой, вычисленной им для исходного файла.</span><span class="sxs-lookup"><span data-stu-id="a64da-244">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>

<span data-ttu-id="a64da-245">Это решение не работает для проектов ASP.NET, так как рассчитанная контрольная сумма относится к созданному исходному файлу, а не файлу ASPX.</span><span class="sxs-lookup"><span data-stu-id="a64da-245">This solution doesn't work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="a64da-246">Чтобы решить эту проблему, `#pragma checksum` предоставляет поддержку контрольных сумм для страниц ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a64da-246">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>

<span data-ttu-id="a64da-247">При создании проекта ASP.NET в Visual C# созданный исходный файл содержит контрольную сумму для ASPX-файла, из которого создается источник.</span><span class="sxs-lookup"><span data-stu-id="a64da-247">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="a64da-248">Затем компилятор записывает эти данные в PDB-файл.</span><span class="sxs-lookup"><span data-stu-id="a64da-248">The compiler then writes this information into the PDB file.</span></span>

<span data-ttu-id="a64da-249">Если компилятор не обнаруживает директиву `#pragma checksum` в файле, он вычисляет контрольную сумму и записывает значение в PDB-файл.</span><span class="sxs-lookup"><span data-stu-id="a64da-249">If the compiler doesn't find a `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>

```csharp
class TestClass
{
    static int Main()
    {
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum
    }
}
```
