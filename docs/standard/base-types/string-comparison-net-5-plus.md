---
title: Изменения в поведении при сравнении строк в .NET 5+
description: Узнайте больше об изменениях в поведении при сравнении строк в .NET 5 и более поздних версий в Windows.
ms.date: 11/04/2020
ms.openlocfilehash: fa1a1d12f45e5b41877a674d7b8747bb2b2f9658
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734235"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="81107-103">Изменения в поведении при сравнении строк в .NET 5+</span><span class="sxs-lookup"><span data-stu-id="81107-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="81107-104">В .NET 5.0 введено изменение поведения среды, и теперь API глобализации используют на всех поддерживаемых платформах [ICU по умолчанию](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="81107-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="81107-105">Это отход от более ранних версий .NET Core и от .NET Framework, которые используют функциональные возможности многоязыковой поддержки (NLS) операционной системы при работе в Windows.</span><span class="sxs-lookup"><span data-stu-id="81107-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="81107-106">Дополнительные сведения об этих изменениях, включая параметры совместимости, которые могут отменять изменение поведения, см. в статье [Глобализация .NET и ICU](../globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="81107-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="81107-107">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="81107-107">Reason for change</span></span>

<span data-ttu-id="81107-108">Это изменение введено для унификации поведения глобализации .NET во всех поддерживаемых операционных системах.</span><span class="sxs-lookup"><span data-stu-id="81107-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="81107-109">Благодаря ему приложения смогут объединять собственные библиотеки глобализации и не зависеть от встроенных библиотек операционных систем.</span><span class="sxs-lookup"><span data-stu-id="81107-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="81107-110">Дополнительные сведения см. в статье [Уведомления о критических изменениях](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="81107-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="81107-111">Различия в поведении</span><span class="sxs-lookup"><span data-stu-id="81107-111">Behavioral differences</span></span>

<span data-ttu-id="81107-112">Если вы используете такие функции, как `string.IndexOf(string)`, не вызывая перегрузку, которая принимает аргумент <xref:System.StringComparison>, вместо *порядкового* поиска вы можете непреднамеренно принять зависимость от поведения, на которое влияют язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="81107-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="81107-113">Поскольку NLS и ICU реализуют в лингвистических функциях сравнения другую логику, то результаты таких методов, как `string.IndexOf(string)`, могут возвращать непредвиденные значения.</span><span class="sxs-lookup"><span data-stu-id="81107-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="81107-114">Такое проявление возможно даже в процессах, для которых активность средств глобализации не всегда ожидаема.</span><span class="sxs-lookup"><span data-stu-id="81107-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="81107-115">Например, следующий код может предоставить не тот ответ в зависимости от текущей среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="81107-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="81107-116">Предотвращение непредвиденного поведения</span><span class="sxs-lookup"><span data-stu-id="81107-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="81107-117">В этом разделе приводятся два варианта решения вопросов касательно непредвиденных изменений поведения в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="81107-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="81107-118">Включение анализаторов кода</span><span class="sxs-lookup"><span data-stu-id="81107-118">Enable code analyzers</span></span>

<span data-ttu-id="81107-119">[Анализаторы кода](../../fundamentals/code-analysis/overview.md) могут обнаруживать места вызовов с ошибками.</span><span class="sxs-lookup"><span data-stu-id="81107-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="81107-120">Для защиты от непредвиденного поведения мы рекомендуем установить [для вашего проекта пакет NuGet __Microsoft.CodeAnalysis.FxCopAnalyzers__](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).</span><span class="sxs-lookup"><span data-stu-id="81107-120">To help guard against any surprising behaviors, we recommend installing [the __Microsoft.CodeAnalysis.FxCopAnalyzers__ NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) into your project.</span></span> <span data-ttu-id="81107-121">Пакет включает правила анализа кода [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) и [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), благодаря которым вы сможете отмечать код, в котором вместо порядкового сравнения непреднамеренно использовалась лингвистическая функция сравнения.</span><span class="sxs-lookup"><span data-stu-id="81107-121">This package includes the code analysis rules [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), which help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span>

<span data-ttu-id="81107-122">Пример:</span><span class="sxs-lookup"><span data-stu-id="81107-122">For example:</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1307.
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="81107-123">Аналогичным образом укажите явный компаратор при создании отсортированной коллекции строк или при сортировке существующей коллекции строк.</span><span class="sxs-lookup"><span data-stu-id="81107-123">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

<span data-ttu-id="81107-124">Дополнительные сведения об этих правилах анализатора кода, в том числе о том, когда необходимо добавлять эти правила в собственную базу кода, см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="81107-124">For more information about these code analyzer rules, including when it might be appropriate to suppress these rules in your own code base, see the following articles:</span></span>

* [<span data-ttu-id="81107-125">CA1307. Используйте StringComparison, чтобы ясно указать намерение.</span><span class="sxs-lookup"><span data-stu-id="81107-125">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
* [<span data-ttu-id="81107-126">CA1309. Используйте порядковый параметр StringComparison</span><span class="sxs-lookup"><span data-stu-id="81107-126">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="81107-127">Возврат к поведению NLS</span><span class="sxs-lookup"><span data-stu-id="81107-127">Revert back to NLS behaviors</span></span>

<span data-ttu-id="81107-128">Чтобы восстановить для приложения .NET 5 прежнее поведение NLS при работе в Windows, выполните действия, описанные в статье [Глобализация .NET и ICU](../globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="81107-128">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="81107-129">Этот переключатель совместимости следует установить на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="81107-129">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="81107-130">Индивидуальные библиотеки не могут перенимать это поведение или отказываться от него.</span><span class="sxs-lookup"><span data-stu-id="81107-130">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="81107-131">Мы настоятельно рекомендуем включить правила анализа кода [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) и [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) для очистки кода и обнаружения скрытых ошибок.</span><span class="sxs-lookup"><span data-stu-id="81107-131">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="81107-132">Дополнительные сведения см. в разделе [Включение анализаторов кода](#enable-code-analyzers).</span><span class="sxs-lookup"><span data-stu-id="81107-132">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="81107-133">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="81107-133">Affected APIs</span></span>

<span data-ttu-id="81107-134">Благодаря изменениям в .NET 5.0 вы не будете сталкиваться с проблемой с непредвиденным поведением в большинстве приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="81107-134">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="81107-135">Однако, учитывая количество затронутых API, а также их важность для широкой экосистемы .NET, следует обращать внимание на возможное непредвиденное поведение в .NET 5.0 или выявлять имеющиеся скрытые ошибки в приложении.</span><span class="sxs-lookup"><span data-stu-id="81107-135">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="81107-136">В число затронутых API входят:</span><span class="sxs-lookup"><span data-stu-id="81107-136">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="81107-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (большинство элементов)</span><span class="sxs-lookup"><span data-stu-id="81107-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="81107-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (большинство элементов)</span><span class="sxs-lookup"><span data-stu-id="81107-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="81107-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (при сортировке массивов строк)</span><span class="sxs-lookup"><span data-stu-id="81107-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="81107-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (если элементы списка являются строками)</span><span class="sxs-lookup"><span data-stu-id="81107-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="81107-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (если ключи являются строками)</span><span class="sxs-lookup"><span data-stu-id="81107-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="81107-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (если ключи являются строками)</span><span class="sxs-lookup"><span data-stu-id="81107-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="81107-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (если набор содержит строки)</span><span class="sxs-lookup"><span data-stu-id="81107-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="81107-144">Это неполный список затронутых API.</span><span class="sxs-lookup"><span data-stu-id="81107-144">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="81107-145">Вышеперечисленные API применяют *лингвистический* поиск и сравнение строк, используя по умолчанию текущие [язык и региональные параметры](xref:System.Threading.Thread.CurrentCulture) потока.</span><span class="sxs-lookup"><span data-stu-id="81107-145">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="81107-146">Различия между *лингвистическим* и *порядковым* поиском и сравнением описаны в разделе [Противопоставление методов порядкового и лингвистического поиска и сравнения](#ordinal-vs-linguistic-search-and-comparison).</span><span class="sxs-lookup"><span data-stu-id="81107-146">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="81107-147">Поскольку ICU реализует лингвистические сравнения строк иначе, чем NLS, приложения Windows, обновленные с более ранней версии .NET Core или .NET Framework до .NET 5.0, вызывающие один из затронутых API, могут работать с различным поведением.</span><span class="sxs-lookup"><span data-stu-id="81107-147">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="81107-148">Исключения</span><span class="sxs-lookup"><span data-stu-id="81107-148">Exceptions</span></span>

* <span data-ttu-id="81107-149">Если API принимает явный параметр `StringComparison` или `CultureInfo`, этот параметр переопределяет поведение API по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81107-149">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="81107-150">Элементы `System.String`, в которых параметром является тип `char` (например, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>), используют порядковый поиск, если вызывающий объект не передает явный аргумент `StringComparison`, указывающий на `CurrentCulture[IgnoreCase]` или `InvariantCulture[IgnoreCase]`.</span><span class="sxs-lookup"><span data-stu-id="81107-150">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="81107-151">Более подробный анализ стандартного поведения для каждого API <xref:System.String> см. в разделе [Стандартные типы поиска и сравнения](#default-search-and-comparison-types).</span><span class="sxs-lookup"><span data-stu-id="81107-151">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="81107-152">Противопоставление методов порядкового и лингвистического поиска и сравнения</span><span class="sxs-lookup"><span data-stu-id="81107-152">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="81107-153">*Порядковый* (или *не лингвистический*) поиск и сравнение разбивает строку на отдельные элементы `char` и выполняет поиск или сравнение по каждому типу char.</span><span class="sxs-lookup"><span data-stu-id="81107-153">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="81107-154">Например, строки `"dog"` и `"dog"` в функции сравнения `Ordinal` определяются как *равные*, поскольку обе состоят из одной и той же последовательности символов char.</span><span class="sxs-lookup"><span data-stu-id="81107-154">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="81107-155">Однако сравнение строк `"dog"` и `"Dog"` приводит к значению *не равно* в функции сравнения `Ordinal`, поскольку последовательности символов char в этих строках отличаются.</span><span class="sxs-lookup"><span data-stu-id="81107-155">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="81107-156">Это значит, что кодовая точка `U+0044` прописной `'D'` появляется до кодовой точки `U+0064` нижнего регистра `'d'`, что приводит к сортировке `"dog"` перед `"Dog"`.</span><span class="sxs-lookup"><span data-stu-id="81107-156">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="81107-157">Функция сравнения `OrdinalIgnoreCase` по-прежнему работает с каждым символом char, однако устраняет различия в регистрах при выполнении операции.</span><span class="sxs-lookup"><span data-stu-id="81107-157">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="81107-158">В функции сравнения `OrdinalIgnoreCase` пары символов char `'d'` и `'D'` будут определены как *равные*, как и пары символов char `'á'` и `'Á'`.</span><span class="sxs-lookup"><span data-stu-id="81107-158">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="81107-159">Однако символ char без диакритического знака `'a'` и символ char с диакритическим знаком `'á'` при сравнении определяются как *не равно*.</span><span class="sxs-lookup"><span data-stu-id="81107-159">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="81107-160">Некоторые примеры приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="81107-160">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="81107-161">Строка 1</span><span class="sxs-lookup"><span data-stu-id="81107-161">String 1</span></span> | <span data-ttu-id="81107-162">Строка 2</span><span class="sxs-lookup"><span data-stu-id="81107-162">String 2</span></span> | <span data-ttu-id="81107-163">Сравнение `Ordinal`</span><span class="sxs-lookup"><span data-stu-id="81107-163">`Ordinal` comparison</span></span> | <span data-ttu-id="81107-164">Сравнение `OrdinalIgnoreCase`</span><span class="sxs-lookup"><span data-stu-id="81107-164">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="81107-165">equal</span><span class="sxs-lookup"><span data-stu-id="81107-165">equal</span></span> | <span data-ttu-id="81107-166">equal</span><span class="sxs-lookup"><span data-stu-id="81107-166">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="81107-167">не равно</span><span class="sxs-lookup"><span data-stu-id="81107-167">not equal</span></span> | <span data-ttu-id="81107-168">equal</span><span class="sxs-lookup"><span data-stu-id="81107-168">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="81107-169">не равно</span><span class="sxs-lookup"><span data-stu-id="81107-169">not equal</span></span> | <span data-ttu-id="81107-170">equal</span><span class="sxs-lookup"><span data-stu-id="81107-170">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="81107-171">не равно</span><span class="sxs-lookup"><span data-stu-id="81107-171">not equal</span></span> | <span data-ttu-id="81107-172">не равно</span><span class="sxs-lookup"><span data-stu-id="81107-172">not equal</span></span> |

<span data-ttu-id="81107-173">В Юникоде строки также могут иметь несколько различных представлений в памяти.</span><span class="sxs-lookup"><span data-stu-id="81107-173">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="81107-174">Например, e с акутом (é) можно представить двумя способами:</span><span class="sxs-lookup"><span data-stu-id="81107-174">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="81107-175">Одиночный литерал `'é'` (также пишется как `'\u00E9'`).</span><span class="sxs-lookup"><span data-stu-id="81107-175">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="81107-176">Литерал без диакритических знаков `'e'`, за которым следует символ объединения диакритических знаков `'\u0301'`.</span><span class="sxs-lookup"><span data-stu-id="81107-176">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="81107-177">Это означает, что при отображении следующие _четыре_ строки будут представлены как `"résumé"`, даже если их составные части отличаются.</span><span class="sxs-lookup"><span data-stu-id="81107-177">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="81107-178">В строках используется сочетание литералов `'é'` или литералов без диакритических знаков `'e'` с модификатором объединения диакритических знаков `'\u0301'`.</span><span class="sxs-lookup"><span data-stu-id="81107-178">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="81107-179">При использовании порядковой функции сравнения ни одна из этих строк не будет представлена как равная другой.</span><span class="sxs-lookup"><span data-stu-id="81107-179">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="81107-180">Это связано с тем, что все они содержат разные базовые последовательности символов char, даже если при отображении на экране выглядят одинаково.</span><span class="sxs-lookup"><span data-stu-id="81107-180">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="81107-181">При выполнении операции `string.IndexOf(..., StringComparison.Ordinal)` среда выполнения ищет точную совпадающую подстроку.</span><span class="sxs-lookup"><span data-stu-id="81107-181">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="81107-182">Результаты выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81107-182">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="81107-183">На поисковые и сравнительные подпрограммы язык и региональные параметры текущего потока не влияют.</span><span class="sxs-lookup"><span data-stu-id="81107-183">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="81107-184">Подпрограммы для *лингвистического* поиска и сравнения разбивают строку на *элементы параметров сортировки* и выполняют поиск или сравнение этих элементов.</span><span class="sxs-lookup"><span data-stu-id="81107-184">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="81107-185">Не обязательно сопоставлять символы строк с составными элементами параметров сортировки 1:1.</span><span class="sxs-lookup"><span data-stu-id="81107-185">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="81107-186">Например, строка длиной 2 символа может состоять только из одного элемента параметров сортировки.</span><span class="sxs-lookup"><span data-stu-id="81107-186">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="81107-187">При сравнении двух строк с учетом лингвистического сравнения функция сравнения проверяет, имеют ли два элемента параметров сортировки одинаковое семантическое значение, даже если литеральные символы строки различны.</span><span class="sxs-lookup"><span data-stu-id="81107-187">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="81107-188">Рассмотрим строку `"résumé"` и ее четыре различные интерпретации еще раз.</span><span class="sxs-lookup"><span data-stu-id="81107-188">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="81107-189">В следующей таблице показаны все интерпретации, разделенные на элементы параметров сортировки.</span><span class="sxs-lookup"><span data-stu-id="81107-189">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="81107-190">Строка</span><span class="sxs-lookup"><span data-stu-id="81107-190">String</span></span> | <span data-ttu-id="81107-191">Как элементы параметров сортировки</span><span class="sxs-lookup"><span data-stu-id="81107-191">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="81107-192">Элемент параметров сортировки частично соответствует тому, что читатели представляют, думая об одном символе или кластере символов.</span><span class="sxs-lookup"><span data-stu-id="81107-192">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="81107-193">Он концептуально похож на [кластер графем](character-encoding-introduction.md#grapheme-clusters), однако охватывает более крупные группировки.</span><span class="sxs-lookup"><span data-stu-id="81107-193">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="81107-194">В лингвистической функции сравнения точные совпадения не требуются.</span><span class="sxs-lookup"><span data-stu-id="81107-194">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="81107-195">Элементы параметров сортировки сравниваются на основе их семантического значения.</span><span class="sxs-lookup"><span data-stu-id="81107-195">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="81107-196">Например, лингвистическая функция сравнения анализирует подстроки `"\u00E9"` и `"e\u0301"` как равные, поскольку они обе семантически означают "строчная буква e с модификатором знака акута".</span><span class="sxs-lookup"><span data-stu-id="81107-196">For example, a linguistic comparer tsreat the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="81107-197">Это позволяет методу `IndexOf` сопоставлять подстроку `"e\u0301"` в более длинной строке, содержащей семантически эквивалентную подстроку `"\u00E9"`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="81107-197">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="81107-198">Как следствие, при лингвистическом сравнении две строки разной длины могут быть представлены как равные.</span><span class="sxs-lookup"><span data-stu-id="81107-198">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="81107-199">Вызывающие объекты не должны следовать логике особых случаев, которая в таких сценариях учитывает длину строки.</span><span class="sxs-lookup"><span data-stu-id="81107-199">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="81107-200">Подпрограммы поиска и сравнения с учетом *языка и региональных параметров* представляют собой специальную форму подпрограмм лингвистического поиска и сравнения.</span><span class="sxs-lookup"><span data-stu-id="81107-200">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="81107-201">В функции сравнения, учитывающей язык и региональные параметры, понятие элемента параметров сортировки расширено до включения сведений, относящихся к заданному языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="81107-201">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="81107-202">Например, [в венгерском алфавите](https://en.wikipedia.org/wiki/Hungarian_alphabet), когда два символа \<dz\> следуют один за другим, они считаются собственными уникальными буквами, отличающимися от \<d\> или \<z\>.</span><span class="sxs-lookup"><span data-stu-id="81107-202">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="81107-203">Это означает, что если в строке отображается \<dz\>, функция сравнения с поддержкой венгерского языка и региональных параметров рассматривает этот символ как отдельный элемент параметров сортировки.</span><span class="sxs-lookup"><span data-stu-id="81107-203">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="81107-204">Строка</span><span class="sxs-lookup"><span data-stu-id="81107-204">String</span></span> | <span data-ttu-id="81107-205">Как элементы параметров сортировки</span><span class="sxs-lookup"><span data-stu-id="81107-205">As collation elements</span></span> | <span data-ttu-id="81107-206">Комментарии</span><span class="sxs-lookup"><span data-stu-id="81107-206">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="81107-207">(использование стандартной лингвистической функции сравнения)</span><span class="sxs-lookup"><span data-stu-id="81107-207">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="81107-208">(использование функции сравнения с поддержкой венгерского языка)</span><span class="sxs-lookup"><span data-stu-id="81107-208">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="81107-209">Это значит, что при использовании функции сравнения с поддержкой венгерского языка и региональных параметров строка `"endz"` *не* заканчивается подстрокой `"z"`, поскольку <\dz\> и <\z\> считаются элементами сортировки с другим семантическим значением.</span><span class="sxs-lookup"><span data-stu-id="81107-209">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="81107-210">Поведение. Лингвистические функции сравнения и функции сравнения с учетом языка и региональных параметров могут иногда корректировать поведение.</span><span class="sxs-lookup"><span data-stu-id="81107-210">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="81107-211">ICU и более старые функции Windows NLS обновляются с учетом изменений в мировых языках.</span><span class="sxs-lookup"><span data-stu-id="81107-211">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="81107-212">Дополнительные сведения см. в записи блога [Смешивание локальных данных (язык и региональные параметры)](/archive/blogs/shawnste/locale-culture-data-churn).</span><span class="sxs-lookup"><span data-stu-id="81107-212">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="81107-213">Поведение *порядковой* функции сравнения не изменится, поскольку она выполняет точную операцию поиска и сравнения по битам.</span><span class="sxs-lookup"><span data-stu-id="81107-213">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="81107-214">Однако поведение функции сравнения *OrdinalIgnoreCase* может изменяться по мере увеличения Юникода для охвата большего количества наборов символов и исправления пропусков в существующих данных регистра.</span><span class="sxs-lookup"><span data-stu-id="81107-214">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="81107-215">Использование. Функции сравнения `StringComparison.InvariantCulture` и `StringComparison.InvariantCultureIgnoreCase` являются лингвистическими функциями сравнения, которые не поддерживают языки и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="81107-215">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="81107-216">Это значит, что эти функции сравнения настроены так, что диакритический знак é может иметь несколько возможных базовых интерпретаций и все эти интерпретации должны обрабатываться одинаково.</span><span class="sxs-lookup"><span data-stu-id="81107-216">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="81107-217">Однако лингвистические функции сравнения без поддержки языков и региональных параметров не будут использовать специальную обработку для символа \<dz\> как отличного от \<d\> или \<z\>, как показано выше.</span><span class="sxs-lookup"><span data-stu-id="81107-217">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="81107-218">Они также не поддерживают специальные символы, такие как немецкий Eszett (ß).</span><span class="sxs-lookup"><span data-stu-id="81107-218">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="81107-219">.NET также предлагает *инвариантный режим глобализации*.</span><span class="sxs-lookup"><span data-stu-id="81107-219">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="81107-220">Этот режим отключает пути кода, которые работают с лингвистическими подпрограммами поиска и сравнения.</span><span class="sxs-lookup"><span data-stu-id="81107-220">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="81107-221">В этом режиме все операции используют поведение *Ordinal* или *OrdinalIgnoreCase*, независимо от того, какой из аргументов, `CultureInfo` или `StringComparison`, предоставляется вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="81107-221">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="81107-222">Дополнительные сведения см. в статьях [Параметры конфигурации времени выполнения для глобализации](../../core/run-time-config/globalization.md) и [Инвариантный режим глобализации в .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="81107-222">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="81107-223">Дополнительные сведения см. в статье [Рекомендации по сравнению строк в .NET](best-practices-strings.md).</span><span class="sxs-lookup"><span data-stu-id="81107-223">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="81107-224">Последствия для безопасности</span><span class="sxs-lookup"><span data-stu-id="81107-224">Security implications</span></span>

<span data-ttu-id="81107-225">Если ваше приложение использует для фильтрации затронутый API, рекомендуется включить правила для анализа кода CA1307 и CA1309, чтобы находить места непреднамеренного использования лингвистического поиска вместо порядкового.</span><span class="sxs-lookup"><span data-stu-id="81107-225">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="81107-226">Приведенные ниже шаблоны кода могут быть подвержены взломам системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="81107-226">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="81107-227">Поскольку метод `string.IndexOf(string)` использует лингвистический поиск по умолчанию, строка может содержать литерал `'<'` или `'&'`, а подпрограммы `string.IndexOf(string)` возвращать `-1`, указывая на то, что подстроку поиска не найдено.</span><span class="sxs-lookup"><span data-stu-id="81107-227">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="81107-228">Правила анализа кода CA1307 и CA1309 помечают такие точки вызова и предупреждают разработчика о потенциальных проблемах.</span><span class="sxs-lookup"><span data-stu-id="81107-228">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="81107-229">Стандартные типы поиска и сравнения</span><span class="sxs-lookup"><span data-stu-id="81107-229">Default search and comparison types</span></span>

<span data-ttu-id="81107-230">В следующей таблице перечислены стандартные типы поиска и сравнения для различных API string и string-like.</span><span class="sxs-lookup"><span data-stu-id="81107-230">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="81107-231">Если вызывающий объект предоставляет явный параметр `CultureInfo` или `StringComparison`, этот параметр будет учитываться как приоритетный по отношению к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81107-231">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="81107-232">API</span><span class="sxs-lookup"><span data-stu-id="81107-232">API</span></span> | <span data-ttu-id="81107-233">Поведение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="81107-233">Default behavior</span></span> | <span data-ttu-id="81107-234">Комментарии</span><span class="sxs-lookup"><span data-stu-id="81107-234">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="81107-235">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-235">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="81107-236">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-236">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="81107-237">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-237">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="81107-238">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-238">Ordinal</span></span> | <span data-ttu-id="81107-239">(когда первый параметр — `char`)</span><span class="sxs-lookup"><span data-stu-id="81107-239">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="81107-240">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-240">CurrentCulture</span></span> | <span data-ttu-id="81107-241">(когда первый параметр — `string`)</span><span class="sxs-lookup"><span data-stu-id="81107-241">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="81107-242">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-242">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="81107-243">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-243">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="81107-244">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-244">Ordinal</span></span> | <span data-ttu-id="81107-245">(когда первый параметр — `char`)</span><span class="sxs-lookup"><span data-stu-id="81107-245">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="81107-246">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-246">CurrentCulture</span></span> | <span data-ttu-id="81107-247">(когда первый параметр — `string`)</span><span class="sxs-lookup"><span data-stu-id="81107-247">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="81107-248">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-248">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="81107-249">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-249">Ordinal</span></span> | <span data-ttu-id="81107-250">(когда первый параметр — `char`)</span><span class="sxs-lookup"><span data-stu-id="81107-250">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="81107-251">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-251">CurrentCulture</span></span> | <span data-ttu-id="81107-252">(когда первый параметр — `string`)</span><span class="sxs-lookup"><span data-stu-id="81107-252">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="81107-253">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-253">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="81107-254">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-254">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="81107-255">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-255">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="81107-256">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-256">Ordinal</span></span> | <span data-ttu-id="81107-257">(когда первый параметр — `char`)</span><span class="sxs-lookup"><span data-stu-id="81107-257">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="81107-258">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-258">CurrentCulture</span></span> | <span data-ttu-id="81107-259">(когда первый параметр — `string`)</span><span class="sxs-lookup"><span data-stu-id="81107-259">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="81107-260">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-260">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="81107-261">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="81107-261">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="81107-262">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-262">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="81107-263">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="81107-263">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="81107-264">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-264">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="81107-265">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-265">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="81107-266">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-266">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="81107-267">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-267">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="81107-268">Порядковый номер</span><span class="sxs-lookup"><span data-stu-id="81107-268">Ordinal</span></span> | |

<span data-ttu-id="81107-269">В отличие от API `string`, все API `MemoryExtensions` по умолчанию выполняют *порядковый* поиск и сравнение со следующими исключениями.</span><span class="sxs-lookup"><span data-stu-id="81107-269">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="81107-270">API</span><span class="sxs-lookup"><span data-stu-id="81107-270">API</span></span> | <span data-ttu-id="81107-271">Поведение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="81107-271">Default behavior</span></span> | <span data-ttu-id="81107-272">Комментарии</span><span class="sxs-lookup"><span data-stu-id="81107-272">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="81107-273">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-273">CurrentCulture</span></span> | <span data-ttu-id="81107-274">(при передаче нулевого аргумента `CultureInfo`)</span><span class="sxs-lookup"><span data-stu-id="81107-274">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="81107-275">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="81107-275">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="81107-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="81107-276">CurrentCulture</span></span> | <span data-ttu-id="81107-277">(при передаче нулевого аргумента `CultureInfo`)</span><span class="sxs-lookup"><span data-stu-id="81107-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="81107-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="81107-278">InvariantCulture</span></span> | |

<span data-ttu-id="81107-279">Следствием является то, что при преобразовании кода от использования `string` к использованию `ReadOnlySpan<char>` изменения в поведении могут быть сделаны непреднамеренно.</span><span class="sxs-lookup"><span data-stu-id="81107-279">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="81107-280">Далее приведен пример.</span><span class="sxs-lookup"><span data-stu-id="81107-280">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="81107-281">Чтобы устранить это явление, рекомендуется передавать явный параметр `StringComparison` в эти API.</span><span class="sxs-lookup"><span data-stu-id="81107-281">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="81107-282">Для этого можно использовать правила анализа кода CA1307 и CA1309.</span><span class="sxs-lookup"><span data-stu-id="81107-282">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="81107-283">См. также</span><span class="sxs-lookup"><span data-stu-id="81107-283">See also</span></span>

- [<span data-ttu-id="81107-284">Критические изменения в области глобализации</span><span class="sxs-lookup"><span data-stu-id="81107-284">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="81107-285">Рекомендации по сравнению строк в .NET</span><span class="sxs-lookup"><span data-stu-id="81107-285">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="81107-286">Сравнение строк в C#</span><span class="sxs-lookup"><span data-stu-id="81107-286">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="81107-287">Глобализация .NET и ICU</span><span class="sxs-lookup"><span data-stu-id="81107-287">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="81107-288">Сравнение порядковых операций со строками и операций, учитывающих язык и региональные параметры</span><span class="sxs-lookup"><span data-stu-id="81107-288">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="81107-289">Обзор анализа исходного кода .NET</span><span class="sxs-lookup"><span data-stu-id="81107-289">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
