---
title: Новые возможности в C# 8.0. Руководство по языку C#
description: Обзор новых функций, доступных в C# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: 318b0a4db97160c88c9743616989c0530b10d05e
ms.sourcegitcommit: 02cc87f02c46e603ea5925de95af746b7ab46a35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2021
ms.locfileid: "107954553"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="ad39f-103">Новые возможности C# 8.0</span><span class="sxs-lookup"><span data-stu-id="ad39f-103">What's new in C# 8.0</span></span>

<span data-ttu-id="ad39f-104">В C# 8.0 добавлены следующие функции и улучшения языка C#:</span><span class="sxs-lookup"><span data-stu-id="ad39f-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="ad39f-105">Члены только для чтения</span><span class="sxs-lookup"><span data-stu-id="ad39f-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="ad39f-106">Методы интерфейса по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ad39f-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="ad39f-107">[Улучшения сопоставления шаблонов](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="ad39f-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - <span data-ttu-id="ad39f-108">[выражения switch](#switch-expressions);</span><span class="sxs-lookup"><span data-stu-id="ad39f-108">[Switch expressions](#switch-expressions)</span></span>
  - <span data-ttu-id="ad39f-109">[шаблоны свойств](#property-patterns);</span><span class="sxs-lookup"><span data-stu-id="ad39f-109">[Property patterns](#property-patterns)</span></span>
  - <span data-ttu-id="ad39f-110">[шаблоны кортежей](#tuple-patterns);</span><span class="sxs-lookup"><span data-stu-id="ad39f-110">[Tuple patterns](#tuple-patterns)</span></span>
  - <span data-ttu-id="ad39f-111">[позиционные шаблоны](#positional-patterns).</span><span class="sxs-lookup"><span data-stu-id="ad39f-111">[Positional patterns](#positional-patterns)</span></span>
- <span data-ttu-id="ad39f-112">[Объявления using](#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="ad39f-112">[Using declarations](#using-declarations)</span></span>
- <span data-ttu-id="ad39f-113">[Статические локальные функции](#static-local-functions).</span><span class="sxs-lookup"><span data-stu-id="ad39f-113">[Static local functions](#static-local-functions)</span></span>
- <span data-ttu-id="ad39f-114">[Удаляемые ссылочные структуры](#disposable-ref-structs).</span><span class="sxs-lookup"><span data-stu-id="ad39f-114">[Disposable ref structs](#disposable-ref-structs)</span></span>
- [<span data-ttu-id="ad39f-115">Ссылочные типы, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="ad39f-115">Nullable reference types</span></span>](#nullable-reference-types)
- <span data-ttu-id="ad39f-116">[Асинхронные потоки](#asynchronous-streams).</span><span class="sxs-lookup"><span data-stu-id="ad39f-116">[Asynchronous streams](#asynchronous-streams)</span></span>
- [<span data-ttu-id="ad39f-117">Асинхронные высвобождаемые типы</span><span class="sxs-lookup"><span data-stu-id="ad39f-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- <span data-ttu-id="ad39f-118">[Индексы и диапазоны](#indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="ad39f-118">[Indices and ranges](#indices-and-ranges)</span></span>
- [<span data-ttu-id="ad39f-119">Присваивание объединения со значением NULL</span><span class="sxs-lookup"><span data-stu-id="ad39f-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="ad39f-120">Неуправляемые сконструированные типы</span><span class="sxs-lookup"><span data-stu-id="ad39f-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="ad39f-121">Выражение stackalloc во вложенных выражениях</span><span class="sxs-lookup"><span data-stu-id="ad39f-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="ad39f-122">Улучшение интерполированных строк verbatim</span><span class="sxs-lookup"><span data-stu-id="ad39f-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="ad39f-123">C# 8.0 поддерживается в **.NET Core 3.x** и **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="ad39f-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="ad39f-124">Дополнительные сведения см. в статье [Управление версиями языка C#](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="ad39f-125">В остальных разделах этой статьи кратко описываются эти возможности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="ad39f-126">Здесь приведены ссылки на эти подробные руководства и обзоры (если они доступны).</span><span class="sxs-lookup"><span data-stu-id="ad39f-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="ad39f-127">Эти функции можно изучить в своей среде с помощью глобального средства `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ad39f-128">Установите глобальное средство [dotnet-try](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) global tool.</span></span>
1. <span data-ttu-id="ad39f-129">Клонируйте репозиторий [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="ad39f-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ad39f-130">Для репозитория *try-samples* установите в качестве текущего каталога подкаталог *csharp8*.</span><span class="sxs-lookup"><span data-stu-id="ad39f-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ad39f-131">Запустите `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="ad39f-132">Члены только для чтения</span><span class="sxs-lookup"><span data-stu-id="ad39f-132">Readonly members</span></span>

<span data-ttu-id="ad39f-133">Модификатор `readonly` можно применить к членам структуры.</span><span class="sxs-lookup"><span data-stu-id="ad39f-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="ad39f-134">Он означает, что член не изменяет состояние.</span><span class="sxs-lookup"><span data-stu-id="ad39f-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="ad39f-135">Это более детализированный способ, чем применение модификатора `readonly` в объявлении `struct`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="ad39f-136">Рассмотрим следующую изменяемую структуру:</span><span class="sxs-lookup"><span data-stu-id="ad39f-136">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="ad39f-137">Как и большинство структур, метод `ToString()` не изменяет состояние.</span><span class="sxs-lookup"><span data-stu-id="ad39f-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="ad39f-138">Это можно указать, добавив модификатор `readonly` в объявление `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="ad39f-139">Предыдущее изменение создает предупреждение компилятора, так как `ToString` обращается к свойству `Distance`, которое не помечено как `readonly`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="ad39f-140">Компилятор выдает предупреждение, когда ему требуется создать защитную копию.</span><span class="sxs-lookup"><span data-stu-id="ad39f-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="ad39f-141">Свойство `Distance` не изменяет состояние, поэтому вы можете устранить это предупреждение, добавив модификатор `readonly` в объявление:</span><span class="sxs-lookup"><span data-stu-id="ad39f-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="ad39f-142">Обратите внимание, что модификатор `readonly` необходим для свойства только для чтения.</span><span class="sxs-lookup"><span data-stu-id="ad39f-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="ad39f-143">Компилятор не предполагает, что методы доступа `get` не изменяют состояние; `readonly` необходимо объявить явно.</span><span class="sxs-lookup"><span data-stu-id="ad39f-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="ad39f-144">Автоматические реализуемые свойства являются исключением; компилятор будет рассматривать все автоматические реализуемые методы получения как `readonly`, поэтому не нужно добавлять модификатор `readonly` к свойствам `X` и `Y`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as `readonly`, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="ad39f-145">Компилятор принудительно применяет правило, в соответствии с которым члены `readonly` не изменяют состояние.</span><span class="sxs-lookup"><span data-stu-id="ad39f-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="ad39f-146">Следующий метод не будет компилироваться, если не удалить модификатор `readonly`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="ad39f-147">Эта функция позволяет указать намерение вашего проекта, чтобы компилятор мог применить его и выполнить оптимизацию на основе намерения.</span><span class="sxs-lookup"><span data-stu-id="ad39f-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

<span data-ttu-id="ad39f-148">Дополнительные сведения см. в разделе о [членах экземпляров `readonly`](../language-reference/builtin-types/struct.md#readonly-instance-members) в статье [Типы структур](../language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-148">For more information, see the [`readonly` instance members](../language-reference/builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../language-reference/builtin-types/struct.md) article.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="ad39f-149">Методы интерфейса по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ad39f-149">Default interface methods</span></span>

<span data-ttu-id="ad39f-150">Теперь вы можете добавлять члены в интерфейсы и предоставлять реализацию для этих членов.</span><span class="sxs-lookup"><span data-stu-id="ad39f-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="ad39f-151">Эта возможность языка позволяет разработчикам API добавлять методы в интерфейс в более поздних версиях, не нарушая исходный код или совместимость на уровне двоичного кода с существующими реализациями этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ad39f-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="ad39f-152">Существующие реализации *наследуют* реализацию по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ad39f-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="ad39f-153">Эта функция также позволяет C# взаимодействовать с API-интерфейсами, предназначенными для Android или Swift, которые поддерживают аналогичные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="ad39f-154">Методы интерфейса по умолчанию также поддерживают сценарии, аналогичные функции языка "признаки".</span><span class="sxs-lookup"><span data-stu-id="ad39f-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="ad39f-155">Методы интерфейса по умолчанию влияют на многие сценарии и элементы языка.</span><span class="sxs-lookup"><span data-stu-id="ad39f-155">Default interface methods affect many scenarios and language elements.</span></span> <span data-ttu-id="ad39f-156">В нашем первом учебнике рассматривается [изменение интерфейса с помощью реализаций по умолчанию](./tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-156">Our first tutorial covers [updating an interface with default implementations](./tutorials/default-interface-methods-versions.md).</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="ad39f-157">Дополнительные шаблоны в нескольких расположениях</span><span class="sxs-lookup"><span data-stu-id="ad39f-157">More patterns in more places</span></span>

<span data-ttu-id="ad39f-158">Возможность **сопоставления шаблонов** позволяет работать с шаблонами в зависимости от формата в связанных, но различных типах данных.</span><span class="sxs-lookup"><span data-stu-id="ad39f-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="ad39f-159">В C# 7.0 появился синтаксис для шаблонов типа и шаблонов константы, использующий выражение [`is`](../language-reference/operators/is.md) и инструкцию [`switch`](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/operators/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="ad39f-160">Эти функции представляют первые пробные шаги на пути к поддержке парадигм программирования, где данные и функции разделены.</span><span class="sxs-lookup"><span data-stu-id="ad39f-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="ad39f-161">По мере того как отрасль переходит на использование микрослужб и других облачных архитектур, необходимы также средства других языков.</span><span class="sxs-lookup"><span data-stu-id="ad39f-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="ad39f-162">В C# 8.0 расширены эти возможности, так что вы можете использовать дополнительные выражения шаблонов в нескольких расположениях в коде.</span><span class="sxs-lookup"><span data-stu-id="ad39f-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="ad39f-163">Учитывайте эти функции, когда данные и функциональные возможности представлены отдельно.</span><span class="sxs-lookup"><span data-stu-id="ad39f-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="ad39f-164">Рассмотрите возможность сопоставления шаблонов, когда алгоритмы зависят от фактов, отличных от типа среды выполнения объекта.</span><span class="sxs-lookup"><span data-stu-id="ad39f-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="ad39f-165">Эти методы предоставляют другой способ выражения проектов.</span><span class="sxs-lookup"><span data-stu-id="ad39f-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="ad39f-166">Помимо новых шаблонов в новых расположениях, в C# 8.0 добавлены **рекурсивные шаблоны**.</span><span class="sxs-lookup"><span data-stu-id="ad39f-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="ad39f-167">Рекурсивные шаблоны — это шаблоны, которые могут содержать другие шаблоны.</span><span class="sxs-lookup"><span data-stu-id="ad39f-167">Recursive patterns are patterns that can contain other patterns.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="ad39f-168">Выражения switch</span><span class="sxs-lookup"><span data-stu-id="ad39f-168">Switch expressions</span></span>

<span data-ttu-id="ad39f-169">Часто инструкция [`switch`](../language-reference/keywords/switch.md) возвращает значение в каждом из блоков `case`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-169">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="ad39f-170">**Выражения switch** позволяет использовать более краткий синтаксис выражения.</span><span class="sxs-lookup"><span data-stu-id="ad39f-170">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="ad39f-171">В нем меньше повторяющихся ключевых слов `case` и `break`, а также меньше фигурных скобок.</span><span class="sxs-lookup"><span data-stu-id="ad39f-171">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="ad39f-172">Например, рассмотрим следующее перечисление, которое выводит список цветов радуги:</span><span class="sxs-lookup"><span data-stu-id="ad39f-172">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="ad39f-173">Если для приложения определен тип `RGBColor`, который создается на основе компонентов `R`, `G` и `B`, вы можете преобразовать значение `Rainbow` в RGB-значение, используя следующий метод, содержащий выражение switch:</span><span class="sxs-lookup"><span data-stu-id="ad39f-173">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="ad39f-174">Здесь представлено несколько улучшений синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="ad39f-174">There are several syntax improvements here:</span></span>

- <span data-ttu-id="ad39f-175">Переменная расположена перед ключевым словом `switch`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-175">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="ad39f-176">Другой порядок позволяет визуально легко отличить выражение switch от инструкции switch.</span><span class="sxs-lookup"><span data-stu-id="ad39f-176">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="ad39f-177">Элементы `case` и `:` заменяются на `=>`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-177">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="ad39f-178">Это более лаконично и интуитивно понятно.</span><span class="sxs-lookup"><span data-stu-id="ad39f-178">It's more concise and intuitive.</span></span>
- <span data-ttu-id="ad39f-179">Случай `default` заменяется пустой переменной `_`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-179">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="ad39f-180">Тексты являются выражениями, а не инструкциями.</span><span class="sxs-lookup"><span data-stu-id="ad39f-180">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="ad39f-181">Сравните это с эквивалентным кодом, где используется классическая инструкция `switch`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-181">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

<span data-ttu-id="ad39f-182">Дополнительные сведения см. в разделе о [выражении](../language-reference/operators/switch-expression.md) `switch`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-182">For more information, see [`switch` expression](../language-reference/operators/switch-expression.md).</span></span>

### <a name="property-patterns"></a><span data-ttu-id="ad39f-183">Шаблоны свойств</span><span class="sxs-lookup"><span data-stu-id="ad39f-183">Property patterns</span></span>

<span data-ttu-id="ad39f-184">**Шаблон свойств** позволяет сопоставлять свойства исследуемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ad39f-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="ad39f-185">Рассмотрим сайт электронной коммерции, на котором должен вычисляться налог с продаж по адресу покупателя.</span><span class="sxs-lookup"><span data-stu-id="ad39f-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="ad39f-186">Это вычисление не является основной задачей класса `Address`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="ad39f-187">Оно меняется со временем и, скорее всего, чаще, чем изменения формата адреса.</span><span class="sxs-lookup"><span data-stu-id="ad39f-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="ad39f-188">Сумма налога с продаж зависит от свойства `State` адреса.</span><span class="sxs-lookup"><span data-stu-id="ad39f-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="ad39f-189">В следующем методе используется шаблон свойства для вычисления налога с продаж по адресу и цене:</span><span class="sxs-lookup"><span data-stu-id="ad39f-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="ad39f-190">При сопоставлении шаблонов создается сокращенный синтаксис для выражения этого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="ad39f-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

<span data-ttu-id="ad39f-191">Дополнительные сведения см. в разделе [Шаблон свойства ](../language-reference/operators/patterns.md#property-pattern) статьи [Шаблоны](../language-reference/operators/patterns.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-191">For more information, see the [Property pattern](../language-reference/operators/patterns.md#property-pattern) section of the [Patterns](../language-reference/operators/patterns.md) article.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="ad39f-192">Шаблоны кортежей</span><span class="sxs-lookup"><span data-stu-id="ad39f-192">Tuple patterns</span></span>

<span data-ttu-id="ad39f-193">Некоторые алгоритмы зависят от нескольких наборов входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad39f-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="ad39f-194">**Шаблоны кортежей** позволяют переключаться между несколькими значениями, выраженными как [кортежи](../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../language-reference/builtin-types/value-tuples.md).</span></span> <span data-ttu-id="ad39f-195">В следующем примере кода показано выражение switch для игры *камень, ножницы, бумага*:</span><span class="sxs-lookup"><span data-stu-id="ad39f-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="ad39f-196">В сообщении указан победитель.</span><span class="sxs-lookup"><span data-stu-id="ad39f-196">The messages indicate the winner.</span></span> <span data-ttu-id="ad39f-197">В случае отклонения представляются три комбинации, ведущие к ничьей, или другие текстовые входные данные.</span><span class="sxs-lookup"><span data-stu-id="ad39f-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="ad39f-198">Позиционные шаблоны</span><span class="sxs-lookup"><span data-stu-id="ad39f-198">Positional patterns</span></span>

<span data-ttu-id="ad39f-199">Некоторые типы включают метод `Deconstruct`, свойства которого деконструируются на дискретные переменные.</span><span class="sxs-lookup"><span data-stu-id="ad39f-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="ad39f-200">Если метод `Deconstruct` доступен, можно использовать **позиционные шаблоны** для проверки свойств объекта и использовать эти свойства для шаблона.</span><span class="sxs-lookup"><span data-stu-id="ad39f-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="ad39f-201">Рассмотрим следующий класс `Point`, который содержит метод `Deconstruct` для создания дискретных переменных для `X` и `Y`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="ad39f-202">Кроме того, нужно учитывать следующее перечисление, представляющее различные позиции квадранта:</span><span class="sxs-lookup"><span data-stu-id="ad39f-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="ad39f-203">В следующем методе используется **позиционный шаблон** для извлечения значений `x` и `y`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="ad39f-204">Затем используется предложение `when` для определения `Quadrant` точки:</span><span class="sxs-lookup"><span data-stu-id="ad39f-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="ad39f-205">Шаблон пустой переменной в предыдущем операторе switch совпадает с выражением, если `x` или `y`, но не оба, имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="ad39f-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="ad39f-206">Выражение switch должно создавать значение или исключение.</span><span class="sxs-lookup"><span data-stu-id="ad39f-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="ad39f-207">Если ни один из вариантов не совпадает, выражение switch создает исключение.</span><span class="sxs-lookup"><span data-stu-id="ad39f-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="ad39f-208">Компилятор создает предупреждение, если в выражении switch не охватываются все возможные случаи.</span><span class="sxs-lookup"><span data-stu-id="ad39f-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="ad39f-209">Ознакомиться с методами сопоставления шаблонов можно в [этом подробном учебнике](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span> <span data-ttu-id="ad39f-210">Дополнительные сведения о позиционном шаблоне см. в разделе [Позиционный шаблон](../language-reference/operators/patterns.md#positional-pattern) статьи [Шаблоны](../language-reference/operators/patterns.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-210">For more information about a positional pattern, see the [Positional pattern](../language-reference/operators/patterns.md#positional-pattern) section of the [Patterns](../language-reference/operators/patterns.md) article.</span></span>

## <a name="using-declarations"></a><span data-ttu-id="ad39f-211">Объявления using</span><span class="sxs-lookup"><span data-stu-id="ad39f-211">Using declarations</span></span>

<span data-ttu-id="ad39f-212">**Объявление using** — это объявление переменной, которому предшествует ключевое слово `using`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-212">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="ad39f-213">Оно сообщает компилятору, что объявляемая переменная должна быть удалена в конце области видимости.</span><span class="sxs-lookup"><span data-stu-id="ad39f-213">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="ad39f-214">Для примера рассмотрим следующий код, в котором записывается текстовый файл:</span><span class="sxs-lookup"><span data-stu-id="ad39f-214">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="ad39f-215">В приведенном выше примере файл удаляется при достижении закрывающей фигурной скобки метода.</span><span class="sxs-lookup"><span data-stu-id="ad39f-215">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="ad39f-216">Это конец области, в котором объявляется `file`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-216">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="ad39f-217">Приведенный выше код эквивалентен следующему коду, в котором используется классическая [инструкция using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="ad39f-217">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        int skippedLines = 0;
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
        return skippedLines;
    } // file is disposed here
}
```

<span data-ttu-id="ad39f-218">В приведенном выше примере файл удаляется при достижении закрывающей фигурной скобки, связанной с инструкцией `using`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-218">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="ad39f-219">В обоих случаях компилятор создает вызов метода `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-219">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="ad39f-220">Компилятор создает ошибку, если выражение в инструкции `using` нельзя удалить.</span><span class="sxs-lookup"><span data-stu-id="ad39f-220">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="ad39f-221">Статические локальные функции</span><span class="sxs-lookup"><span data-stu-id="ad39f-221">Static local functions</span></span>

<span data-ttu-id="ad39f-222">Теперь вы можете добавить модификатор `static` в [локальные функции](../programming-guide/classes-and-structs/local-functions.md), чтобы убедиться, что локальная функция не сохраняет (не ссылается на) какие-либо переменные из включающей области.</span><span class="sxs-lookup"><span data-stu-id="ad39f-222">You can now add the `static` modifier to [local functions](../programming-guide/classes-and-structs/local-functions.md) to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="ad39f-223">Это приводит к возникновению ошибки `CS8421`: "A static local function can't contain a reference to \<variable>" (Статическая локальная функция не может содержать ссылку на \<variable>).</span><span class="sxs-lookup"><span data-stu-id="ad39f-223">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="ad39f-224">Рассмотрим следующий код.</span><span class="sxs-lookup"><span data-stu-id="ad39f-224">Consider the following code.</span></span> <span data-ttu-id="ad39f-225">Локальная функция `LocalFunction` обращается к переменной `y`, объявленной в области видимости (метод `M`).</span><span class="sxs-lookup"><span data-stu-id="ad39f-225">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="ad39f-226">Таким образом `LocalFunction` не может объявляться с помощью модификатора `static`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-226">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="ad39f-227">Следующий код содержит статическую локальную функцию.</span><span class="sxs-lookup"><span data-stu-id="ad39f-227">The following code contains a static local function.</span></span> <span data-ttu-id="ad39f-228">Она может быть статической, так как она не обращается ко всем переменным в области видимости:</span><span class="sxs-lookup"><span data-stu-id="ad39f-228">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="ad39f-229">Удаляемые ссылочные структуры</span><span class="sxs-lookup"><span data-stu-id="ad39f-229">Disposable ref structs</span></span>

<span data-ttu-id="ad39f-230">Объект `struct`, объявленный с помощью модификатора `ref`, не может реализовывать интерфейсы и поэтому не может реализовать <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-230">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="ad39f-231">Таким образом, чтобы объект `ref struct` можно было удалить, у него должен быть доступный метод `void Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-231">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="ad39f-232">Эта функция также применима к объявлениям `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-232">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="ad39f-233">Ссылочные типы, допускающие значение null</span><span class="sxs-lookup"><span data-stu-id="ad39f-233">Nullable reference types</span></span>

<span data-ttu-id="ad39f-234">Внутри контекста заметок, допускающих значение null, любая переменная ссылочного типа считается переменной **ссылочного типа, не допускающего значения null**.</span><span class="sxs-lookup"><span data-stu-id="ad39f-234">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="ad39f-235">Если вы хотите указать, что переменная может принимать значение null, необходимо добавить к имени типа `?`, чтобы объявить переменную как переменную **ссылочного типа, допускающего значения null**.</span><span class="sxs-lookup"><span data-stu-id="ad39f-235">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="ad39f-236">Для ссылочных типов, не допускающих значение null, компилятор использует анализ потока, чтобы убедиться, что локальные переменные инициализируются в значение, отличное от null, при объявлении.</span><span class="sxs-lookup"><span data-stu-id="ad39f-236">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="ad39f-237">Поля должны быть инициализированы во время построения.</span><span class="sxs-lookup"><span data-stu-id="ad39f-237">Fields must be initialized during construction.</span></span> <span data-ttu-id="ad39f-238">Компилятор создает предупреждение, если переменная не задается вызовом ни к одному из доступных конструкторов или инициализатором.</span><span class="sxs-lookup"><span data-stu-id="ad39f-238">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="ad39f-239">Кроме того, ссылочным типам, не допускающим значение null, нельзя задать значение, которое может быть null.</span><span class="sxs-lookup"><span data-stu-id="ad39f-239">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="ad39f-240">Ссылочные типы, допускающие значение null, не проверяются на предмет того, назначено ли им значение null или получили ли они его после инициализации.</span><span class="sxs-lookup"><span data-stu-id="ad39f-240">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="ad39f-241">Тем не менее, компилятор использует анализ потока, чтобы убедиться, что любая переменная ссылочного типа, допускающего значение null, проверяется на наличие значения null, прежде чем обратиться к ней или назначить ей ссылочный тип, не допускающий значение null.</span><span class="sxs-lookup"><span data-stu-id="ad39f-241">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="ad39f-242">Дополнительные сведения о функции см. в обзоре [ссылочных типов, допускающих значение null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-242">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="ad39f-243">Попробуйте самостоятельно применить эту возможность в новом приложении в этом [руководстве по ссылочным типам, допускающим значение null](tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-243">Try it yourself in a new application in this [nullable reference types tutorial](tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="ad39f-244">Дополнительные сведения о шагах переноса существующей базы кода для использования ссылочных типов, допускающих значение null, см. в [этом руководстве](tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-244">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="ad39f-245">Асинхронные потоки</span><span class="sxs-lookup"><span data-stu-id="ad39f-245">Asynchronous streams</span></span>

<span data-ttu-id="ad39f-246">Начиная с C# версии 8.0 можно создавать и использовать потоки асинхронно.</span><span class="sxs-lookup"><span data-stu-id="ad39f-246">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="ad39f-247">В методе, который возвращает асинхронный поток, есть три свойства:</span><span class="sxs-lookup"><span data-stu-id="ad39f-247">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="ad39f-248">Он объявлен с помощью модификатора `async`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-248">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="ad39f-249">Он возвращает интерфейс <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-249">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="ad39f-250">Метод содержит инструкции `yield return` для возвращения последовательных элементов в асинхронном потоке.</span><span class="sxs-lookup"><span data-stu-id="ad39f-250">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="ad39f-251">Для использования асинхронного потока требуется добавить ключевое слово `await` перед ключевым словом `foreach` при перечислении элементов потока.</span><span class="sxs-lookup"><span data-stu-id="ad39f-251">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="ad39f-252">Для добавления ключевого слова `await` требуется, чтобы метод, который перечисляет асинхронный поток, был объявлен с помощью модификатора `async` и возвращал тип, допустимый для метода `async`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-252">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="ad39f-253">Обычно это означает возвращение структуры <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-253">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ad39f-254">Это также может быть структура <xref:System.Threading.Tasks.ValueTask> или <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-254">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="ad39f-255">Метод может использовать и создавать асинхронный поток. Это означает, что будет возвращен интерфейс <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-255">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="ad39f-256">Следующий код создает последовательность чисел от 0 до 19 с интервалом 100 мс между генерированием каждого числа:</span><span class="sxs-lookup"><span data-stu-id="ad39f-256">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="ad39f-257">Вы бы перечислили последовательность с использованием инструкции `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-257">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="ad39f-258">Вы можете попробовать асинхронные потоки самостоятельно в нашем руководстве по [созданию и использованию асинхронных потоков](tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-258">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="ad39f-259">Элементы потока по умолчанию обрабатываются в захваченном контексте.</span><span class="sxs-lookup"><span data-stu-id="ad39f-259">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="ad39f-260">Чтобы отключить захват контекста, используйте метод расширения <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-260">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="ad39f-261">Дополнительные сведения о контекстах синхронизации и захвате текущего контекста см. в [статье](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md), посвященной использованию асинхронной модели на основе задач.</span><span class="sxs-lookup"><span data-stu-id="ad39f-261">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="ad39f-262">Асинхронные высвобождаемые типы</span><span class="sxs-lookup"><span data-stu-id="ad39f-262">Asynchronous disposable</span></span>

<span data-ttu-id="ad39f-263">Начиная с C# 8.0 язык поддерживает асинхронные освобождаемые типы, реализующие интерфейс <xref:System.IAsyncDisposable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad39f-263">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="ad39f-264">Для работы с асинхронно освобождаемым объектами используется инструкция `await using`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-264">You use the `await using` statement to work with an asynchronously disposable object.</span></span> <span data-ttu-id="ad39f-265">Дополнительные сведения см. в статье [Реализация метода DisposeAsync](../../standard/garbage-collection/implementing-disposeasync.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-265">For more information, see the [Implement a DisposeAsync method](../../standard/garbage-collection/implementing-disposeasync.md) article.</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="ad39f-266">Индексы и диапазоны</span><span class="sxs-lookup"><span data-stu-id="ad39f-266">Indices and ranges</span></span>

<span data-ttu-id="ad39f-267">Диапазоны и индексы обеспечивают лаконичный синтаксис для доступа к отдельным элементам или диапазонам в последовательности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="ad39f-268">Поддержка языков опирается на два новых типа и два новых оператора:</span><span class="sxs-lookup"><span data-stu-id="ad39f-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="ad39f-269"><xref:System.Index?displayProperty=nameWithType> представляет индекс в последовательности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="ad39f-270">Оператор `^` (индекс с конца), который указывает, что индекс указан относительно конца последовательности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="ad39f-271"><xref:System.Range?displayProperty=nameWithType> представляет вложенный диапазон последовательности.</span><span class="sxs-lookup"><span data-stu-id="ad39f-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="ad39f-272">Оператор диапазона `..`, который задает начало и конец диапазона в качестве своих операндов.</span><span class="sxs-lookup"><span data-stu-id="ad39f-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="ad39f-273">Начнем с правил для использования в индексах.</span><span class="sxs-lookup"><span data-stu-id="ad39f-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="ad39f-274">Рассмотрим массив `sequence`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-274">Consider an array `sequence`.</span></span> <span data-ttu-id="ad39f-275">Индекс `0` совпадает с `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="ad39f-276">Индекс `^0` совпадает с `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="ad39f-277">Обратите внимание, что `sequence[^0]` создает исключение так же, как и `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="ad39f-278">Для любого числа `n` индекс `^n` совпадает с `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="ad39f-279">Диапазон указывает *начало* и *конец* диапазона.</span><span class="sxs-lookup"><span data-stu-id="ad39f-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="ad39f-280">Начало диапазона является включающим, но конец диапазона является исключающим, то есть *начало* включается в диапазон, а *конец* не включается.</span><span class="sxs-lookup"><span data-stu-id="ad39f-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="ad39f-281">Диапазон `[0..^0]` представляет весь диапазон так же, как `[0..sequence.Length]` представляет весь диапазон.</span><span class="sxs-lookup"><span data-stu-id="ad39f-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="ad39f-282">Рассмотрим несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="ad39f-282">Let's look at a few examples.</span></span> <span data-ttu-id="ad39f-283">Обратите внимание на следующий массив, который помечен индексом от начала и от конца:</span><span class="sxs-lookup"><span data-stu-id="ad39f-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="ad39f-284">Вы можете получить последнее слово с помощью индекса `^1`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="ad39f-285">Следующий код создает поддиапазон со словами "quick", "brown" и "fox".</span><span class="sxs-lookup"><span data-stu-id="ad39f-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="ad39f-286">Он включает в себя элементы от `words[1]` до `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="ad39f-287">Элемент `words[4]` в диапазон не входит.</span><span class="sxs-lookup"><span data-stu-id="ad39f-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="ad39f-288">Следующий код создает поддиапазон со словами "lazy" и "dog".</span><span class="sxs-lookup"><span data-stu-id="ad39f-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="ad39f-289">Он включает элементы `words[^2]` и `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="ad39f-290">Конечный индекс `words[^0]` не включен:</span><span class="sxs-lookup"><span data-stu-id="ad39f-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="ad39f-291">В следующих примерах создаются диапазоны, которые должны быть открыты для начала, конца или в обоих случаях:</span><span class="sxs-lookup"><span data-stu-id="ad39f-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="ad39f-292">Вы также можете объявить диапазоны как переменные:</span><span class="sxs-lookup"><span data-stu-id="ad39f-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="ad39f-293">Затем вы можете использовать диапазон внутри символов `[` и `]`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="ad39f-294">Индексы и диапазоны поддерживаются не только массивами.</span><span class="sxs-lookup"><span data-stu-id="ad39f-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="ad39f-295">Можно также использовать индексы и диапазоны со [строкой](../language-reference/builtin-types/reference-types.md#the-string-type) (<xref:System.Span%601> или <xref:System.ReadOnlySpan%601>).</span><span class="sxs-lookup"><span data-stu-id="ad39f-295">You can also use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="ad39f-296">Дополнительные сведения см. в разделе [Поддержка типа для индексов и диапазонов](tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="ad39f-296">For more information, see [Type support for indices and ranges](tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="ad39f-297">Вы можете изучить сведения об индексах и диапазонах адресов в руководстве [Индексы и диапазоны](tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="ad39f-298">Присваивание объединения со значением NULL</span><span class="sxs-lookup"><span data-stu-id="ad39f-298">Null-coalescing assignment</span></span>

<span data-ttu-id="ad39f-299">В C# 8.0 появился оператор присваивания объединения со значением NULL `??=`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="ad39f-300">Оператор `??=` можно использовать для присваивания значения правого операнда левому операнду только в том случае, если левый операнд принимает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="ad39f-301">Дополнительные сведения см. в статье [Операторы ?? и ??=](../language-reference/operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="ad39f-302">Неуправляемые сконструированные типы</span><span class="sxs-lookup"><span data-stu-id="ad39f-302">Unmanaged constructed types</span></span>

<span data-ttu-id="ad39f-303">В C# 7.3 и более ранних версиях сконструированный тип (тип, содержащий по крайней мере один аргумент типа) не может быть [неуправляемым типом](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="ad39f-304">Начиная с C# 8.0, сконструированный тип значения является неуправляемым, если он содержит поля исключительно неуправляемых типов.</span><span class="sxs-lookup"><span data-stu-id="ad39f-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="ad39f-305">Например, при наличии следующего определения универсального типа `Coords<T>`:</span><span class="sxs-lookup"><span data-stu-id="ad39f-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="ad39f-306">тип `Coords<int>` является неуправляемым в C# 8.0 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="ad39f-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="ad39f-307">Как и для любого неуправляемого типа, вы можете создать указатель на переменную этого типа или [выделить блок памяти в стеке](../language-reference/operators/stackalloc.md) для экземпляров этого типа:</span><span class="sxs-lookup"><span data-stu-id="ad39f-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="ad39f-308">Дополнительные сведения см. в разделе [Неуправляемые типы](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="ad39f-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="ad39f-309">Выражение stackalloc во вложенных выражениях</span><span class="sxs-lookup"><span data-stu-id="ad39f-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="ad39f-310">Начиная с C# 8.0, если результат выражения [stackalloc](../language-reference/operators/stackalloc.md) имеет тип <xref:System.Span%601?displayProperty=nameWithType> или <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, можно использовать выражение `stackalloc` в других выражениях:</span><span class="sxs-lookup"><span data-stu-id="ad39f-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="ad39f-311">Улучшение интерполированных строк verbatim</span><span class="sxs-lookup"><span data-stu-id="ad39f-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="ad39f-312">Порядок маркеров `$` и `@` в [интерполированных ](../language-reference/tokens/interpolated.md) строках verbatim может быть любым: и `$@"..."`, и `@$"..."` являются допустимыми интерполированными строками verbatim.</span><span class="sxs-lookup"><span data-stu-id="ad39f-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="ad39f-313">В более ранних версиях C# маркер`$` должен располагаться перед маркером `@`.</span><span class="sxs-lookup"><span data-stu-id="ad39f-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
