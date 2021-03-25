---
description: Параметры компилятора C# для ошибок и предупреждений. Эти параметры отключают и включают предупреждения, а также управляют предупреждениями как ошибками.
title: Параметры компилятора C# — ошибки и предупреждения
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- WarningLevel compiler option [C#]
- TreatWarningsAsErrors compiler option [C#]
- WarningsAsErrors compiler option [C#]
- WarningsNotAsErrors compiler option [C#]
- DisabledWarnings compiler option [C#]
- CodeAnalysisRuleSet compiler option [C#]
- ErrorLog compiler option [C#]
- ReportAnalyzer compiler option [C#]
ms.openlocfilehash: 2bdda13d6b8b2b75d80c228da678a5b7fbcb8892
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482495"
---
# <a name="c-compiler-options-to-report-errors-and-warnings"></a><span data-ttu-id="598e1-104">Параметры компилятора C# для информирования об ошибках и предупреждениях</span><span class="sxs-lookup"><span data-stu-id="598e1-104">C# Compiler Options to report errors and warnings</span></span>

<span data-ttu-id="598e1-105">Следующие параметры управляют тем, как компилятор сообщает об ошибках и предупреждениях.</span><span class="sxs-lookup"><span data-stu-id="598e1-105">The following options control how the compiler reports errors and warnings.</span></span> <span data-ttu-id="598e1-106">Новый синтаксис MSBuild выделен **полужирным шрифтом**.</span><span class="sxs-lookup"><span data-stu-id="598e1-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="598e1-107">Для старого синтаксиса *csc.exe* используется формат `code style`.</span><span class="sxs-lookup"><span data-stu-id="598e1-107">The older *csc.exe* syntax is shown in `code style`.</span></span>

- <span data-ttu-id="598e1-108">**WarningLevel** / `-warn`: определение порога предупреждений.</span><span class="sxs-lookup"><span data-stu-id="598e1-108">**WarningLevel** / `-warn`: Set warning level.</span></span>
- <span data-ttu-id="598e1-109">**TreatWarningsAsErrors** / `-warnaserror`: обработка всех предупреждений как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-109">**TreatWarningsAsErrors** / `-warnaserror`: Treat all warnings as errors</span></span>
- <span data-ttu-id="598e1-110">**WarningsAsErrors** / `-warnaserror`: обработка одного или нескольких предупреждений как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-110">**WarningsAsErrors** / `-warnaserror`: Treat one or more warnings as errors</span></span>
- <span data-ttu-id="598e1-111">**WarningsNotAsErrors** / `-warnaserror`: обработка одного или нескольких предупреждений не как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-111">**WarningsNotAsErrors** / `-warnaserror`: Treat one or more warnings not as errors</span></span>
- <span data-ttu-id="598e1-112">**DisabledWarnings** / `-nowarn`: определение списка отключенных предупреждений.</span><span class="sxs-lookup"><span data-stu-id="598e1-112">**DisabledWarnings** / `-nowarn`: Set a list of disabled warnings.</span></span>
- <span data-ttu-id="598e1-113">**CodeAnalysisRuleSet** / `-ruleset`: определение файла набора правил, который отключает определенную диагностику.</span><span class="sxs-lookup"><span data-stu-id="598e1-113">**CodeAnalysisRuleSet** / `-ruleset`: Specify a ruleset file that disables specific diagnostics.</span></span>
- <span data-ttu-id="598e1-114">**ErrorLog** / `-errorlog`: определение файла для регистрации всей диагностики компилятора и анализатора.</span><span class="sxs-lookup"><span data-stu-id="598e1-114">**ErrorLog** / `-errorlog`: Specify a file to log all compiler and analyzer diagnostics.</span></span>
- <span data-ttu-id="598e1-115">**ReportAnalyzer** / `-reportanalyzer`: регистрация дополнительных сведений анализатора, включая сведения о времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="598e1-115">**ReportAnalyzer** / `-reportanalyzer`:  Report additional analyzer information, such as execution time.</span></span>

## <a name="warninglevel"></a><span data-ttu-id="598e1-116">WarningLevel</span><span class="sxs-lookup"><span data-stu-id="598e1-116">WarningLevel</span></span>

<span data-ttu-id="598e1-117">Параметр **WarningLevel** определяет порог предупреждений для отображения компилятором.</span><span class="sxs-lookup"><span data-stu-id="598e1-117">The **WarningLevel** option specifies the warning level for the compiler to display.</span></span>

```xml
<WarningLevel>3</WarningLevel>
```

<span data-ttu-id="598e1-118">Значение элемента — это порог предупреждений, который должен отображаться для компиляции: при меньших значениях отображаются только самые серьезные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-118">The element value is the warning level you want displayed for the compilation: Lower numbers show only high severity warnings.</span></span> <span data-ttu-id="598e1-119">Чем выше значение, тем больше предупреждений будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="598e1-119">Higher numbers show more warnings.</span></span> <span data-ttu-id="598e1-120">Значение должно быть больше нуля или равно ему.</span><span class="sxs-lookup"><span data-stu-id="598e1-120">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="598e1-121">Уровень предупреждений</span><span class="sxs-lookup"><span data-stu-id="598e1-121">Warning level</span></span>|<span data-ttu-id="598e1-122">Значение</span><span class="sxs-lookup"><span data-stu-id="598e1-122">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="598e1-123">0</span><span class="sxs-lookup"><span data-stu-id="598e1-123">0</span></span>|<span data-ttu-id="598e1-124">Отключает вывод всех предупреждающих сообщений.</span><span class="sxs-lookup"><span data-stu-id="598e1-124">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="598e1-125">1</span><span class="sxs-lookup"><span data-stu-id="598e1-125">1</span></span>|<span data-ttu-id="598e1-126">Отображает серьезные предупреждающие сообщения.</span><span class="sxs-lookup"><span data-stu-id="598e1-126">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="598e1-127">2</span><span class="sxs-lookup"><span data-stu-id="598e1-127">2</span></span>|<span data-ttu-id="598e1-128">Отображает предупреждения уровня 1, а также некоторые менее серьезные предупреждения, в том числе связанные со скрытием членов класса.</span><span class="sxs-lookup"><span data-stu-id="598e1-128">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|
|<span data-ttu-id="598e1-129">3</span><span class="sxs-lookup"><span data-stu-id="598e1-129">3</span></span>|<span data-ttu-id="598e1-130">Отображает предупреждения уровня 2, а также некоторые менее серьезные предупреждения, в том числе связанные с выражениями, которые всегда возвращают значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="598e1-130">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|
|<span data-ttu-id="598e1-131">4 (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="598e1-131">4 (the default)</span></span>|<span data-ttu-id="598e1-132">Отображает все предупреждения уровня 3, а также информационные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-132">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="598e1-133">5</span><span class="sxs-lookup"><span data-stu-id="598e1-133">5</span></span>|<span data-ttu-id="598e1-134">Отображает предупреждения уровня 4, а также [дополнительные предупреждения](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) от компилятора, поставляемого в составе C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="598e1-134">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="598e1-135">Больше 5</span><span class="sxs-lookup"><span data-stu-id="598e1-135">Greater than 5</span></span>|<span data-ttu-id="598e1-136">Любое значение больше 5 будет рассматриваться как 5.</span><span class="sxs-lookup"><span data-stu-id="598e1-136">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="598e1-137">Чтобы гарантировать постоянное отображение всех предупреждений, если в компиляторе указаны новые пороги предупреждений, задайте произвольное большое значение (например, `9999`).</span><span class="sxs-lookup"><span data-stu-id="598e1-137">To make sure you always have all warnings if the compiler is updated with new warning levels, put an arbitrary large value (for example, `9999`).</span></span>

<span data-ttu-id="598e1-138">Чтобы получить сведения об ошибке или предупреждении, выполните поиск по соответствующему коду в указателе справочной системы.</span><span class="sxs-lookup"><span data-stu-id="598e1-138">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="598e1-139">Дополнительные сведения о других способах получить информацию об ошибках и предупреждениях см. в разделе [Ошибки компилятора C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="598e1-139">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span> <span data-ttu-id="598e1-140">Используйте [**TreatWarningsAsErrors**](#treatwarningsaserrors), чтобы обрабатывать все предупреждения как ошибки.</span><span class="sxs-lookup"><span data-stu-id="598e1-140">Use [**TreatWarningsAsErrors**](#treatwarningsaserrors) to treat all warnings as errors.</span></span> <span data-ttu-id="598e1-141">Используйте [**DisabledWarnings**](#disabledwarnings), чтобы отключить определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-141">Use [**DisabledWarnings**](#disabledwarnings) to disable certain warnings.</span></span>  

## <a name="treatwarningsaserrors"></a><span data-ttu-id="598e1-142">TreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="598e1-142">TreatWarningsAsErrors</span></span>

<span data-ttu-id="598e1-143">Параметр **TreatWarningsAsErrors** включает обработку всех предупреждений как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-143">The **TreatWarningsAsErrors** option treats all warnings as errors.</span></span> <span data-ttu-id="598e1-144">Вы также можете использовать **TreatWarningsAsErrors**, чтобы обрабатывать как ошибки только некоторые предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-144">You can also use the **TreatWarningsAsErrors** to set only some warnings as errors.</span></span> <span data-ttu-id="598e1-145">Включив **TreatWarningsAsErrors**, вы можете использовать **TreatWarningsAsErrors**, чтобы перечислить предупреждения, которые не должны обрабатываться как ошибки.</span><span class="sxs-lookup"><span data-stu-id="598e1-145">If you turn on **TreatWarningsAsErrors**, you can use **TreatWarningsAsErrors** to list warnings that shouldn't be treated as errors.</span></span>

```xml
<TreatWarningsAsErrors></TreatWarningsAsErrors>
```

<span data-ttu-id="598e1-146">Все предупреждающие сообщения вместо этого будут выводиться как ошибки.</span><span class="sxs-lookup"><span data-stu-id="598e1-146">All warning messages are instead reported as errors.</span></span> <span data-ttu-id="598e1-147">Процесс сборки будет остановлен (выходные файлы не будут создаваться).</span><span class="sxs-lookup"><span data-stu-id="598e1-147">The build process halts (no output files are built).</span></span> <span data-ttu-id="598e1-148">По умолчанию **TreatWarningsAsErrors** не применяется, и это означает, что наличие предупреждений не препятствует созданию выходного файла.</span><span class="sxs-lookup"><span data-stu-id="598e1-148">By default, **TreatWarningsAsErrors** isn't in effect, which means warnings don't prevent the generation of an output file.</span></span> <span data-ttu-id="598e1-149">Если требуется обрабатывать как ошибки только конкретные предупреждения, укажите их номера через запятую.</span><span class="sxs-lookup"><span data-stu-id="598e1-149">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="598e1-150">Набор всех предупреждений о допустимости значений NULL можно указать с помощью сокращения [**Nullable**](language.md#nullable).</span><span class="sxs-lookup"><span data-stu-id="598e1-150">The set of all nullability warnings can be specified with the [**Nullable**](language.md#nullable) shorthand.</span></span> <span data-ttu-id="598e1-151">Используйте [**WarningLevel**](#warninglevel), чтобы определить порог предупреждений, которые будет отображать компилятор.</span><span class="sxs-lookup"><span data-stu-id="598e1-151">Use [**WarningLevel**](#warninglevel) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="598e1-152">Используйте [**DisabledWarnings**](#disabledwarnings), чтобы отключить определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-152">Use [**DisabledWarnings**](#disabledwarnings) to disable certain warnings.</span></span>

## <a name="warningsaserrors-and-warningsnotaserrors"></a><span data-ttu-id="598e1-153">WarningsAsErrors и WarningsNotAsErrors</span><span class="sxs-lookup"><span data-stu-id="598e1-153">WarningsAsErrors and WarningsNotAsErrors</span></span>

<span data-ttu-id="598e1-154">Параметры **WarningsAsErrors** и **WarningsNotAsErrors** переопределяют параметр **TreatWarningsAsErrors** для списка предупреждений.</span><span class="sxs-lookup"><span data-stu-id="598e1-154">The **WarningsAsErrors** and **WarningsNotAsErrors** options override the **TreatWarningsAsErrors** option for a list of warnings.</span></span>

<span data-ttu-id="598e1-155">Включение предупреждений 0219 и 0168 как ошибок:</span><span class="sxs-lookup"><span data-stu-id="598e1-155">Enable warnings 0219 and 0168 as errors:</span></span>

```xml
<WarningsAsErrors>0219,0168</WarningsAsErrors>
```

<span data-ttu-id="598e1-156">Отключение этих же предупреждений как ошибок:</span><span class="sxs-lookup"><span data-stu-id="598e1-156">Disable the same warnings as errors:</span></span>

```xml
<WarningsNotAsErrors>0219,0168</WarningsNotAsErrors>
```

<span data-ttu-id="598e1-157">Вы можете использовать **WarningsAsErrors**, чтобы настроить набор предупреждений как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-157">You use **WarningsAsErrors** to configure a set of warnings as errors.</span></span> <span data-ttu-id="598e1-158">Используйте **WarningsNotAsErrors**, чтобы настроить набор предупреждений, которые не должны обрабатываться как ошибки, если вы включили обработку всех предупреждений как ошибок.</span><span class="sxs-lookup"><span data-stu-id="598e1-158">Use **WarningsNotAsErrors** to configure a set of warnings that should not be errors when you've set all warnings as errors.</span></span>

## <a name="disabledwarnings"></a><span data-ttu-id="598e1-159">DisabledWarnings</span><span class="sxs-lookup"><span data-stu-id="598e1-159">DisabledWarnings</span></span>

<span data-ttu-id="598e1-160">Параметр **DisabledWarnings** позволяет отключить отображение одного или нескольких предупреждений компилятором.</span><span class="sxs-lookup"><span data-stu-id="598e1-160">The **DisabledWarnings** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="598e1-161">Разделяйте предупреждения запятыми.</span><span class="sxs-lookup"><span data-stu-id="598e1-161">Separate multiple warning numbers with a comma.</span></span>

```xml
<DisabledWarnings>number1, number2</DisabledWarnings>
```

<span data-ttu-id="598e1-162">`number1`, `number2` — номера предупреждений, которые требуется отключить в компиляторе.</span><span class="sxs-lookup"><span data-stu-id="598e1-162">`number1`, `number2` Warning number(s) that you want the compiler to suppress.</span></span> <span data-ttu-id="598e1-163">Вы можете указать только числовую часть идентификатора предупреждения.</span><span class="sxs-lookup"><span data-stu-id="598e1-163">You specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="598e1-164">Например, чтобы отключить *CS0028*, можно указать `<DisabledWarnings>28</DisabledWarnings>`.</span><span class="sxs-lookup"><span data-stu-id="598e1-164">For example, if you want to suppress *CS0028*, you could specify `<DisabledWarnings>28</DisabledWarnings>`.</span></span> <span data-ttu-id="598e1-165">Компилятор просто пропустит номера предупреждений, переданные в **DisabledWarnings**, которые были действительными в предыдущих выпусках, но были удалены.</span><span class="sxs-lookup"><span data-stu-id="598e1-165">The compiler silently ignores warning numbers passed to **DisabledWarnings** that were valid in previous releases, but that have been removed.</span></span> <span data-ttu-id="598e1-166">Например, предупреждение *CS0679* было действительным в компиляторе Visual Studio .NET 2002, но было удалено в последующих версиях.</span><span class="sxs-lookup"><span data-stu-id="598e1-166">For example, *CS0679* was valid in the compiler in Visual Studio .NET 2002 but was removed later.</span></span>

 <span data-ttu-id="598e1-167">Следующие предупреждения нельзя отключить с помощью параметра **DisabledWarnings**:</span><span class="sxs-lookup"><span data-stu-id="598e1-167">The following warnings cannot be suppressed by the **DisabledWarnings** option:</span></span>

- <span data-ttu-id="598e1-168">Предупреждение компилятора (уровень 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="598e1-168">Compiler Warning (level 1) CS2002</span></span>  
- <span data-ttu-id="598e1-169">Предупреждение компилятора (уровень 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="598e1-169">Compiler Warning (level 1) CS2023</span></span>
- <span data-ttu-id="598e1-170">Предупреждение компилятора (уровень 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="598e1-170">Compiler Warning (level 1) CS2029</span></span>

## <a name="codeanalysisruleset"></a><span data-ttu-id="598e1-171">CodeAnalysisRuleSet</span><span class="sxs-lookup"><span data-stu-id="598e1-171">CodeAnalysisRuleSet</span></span>

<span data-ttu-id="598e1-172">Укажите файл набора правил, который настраивает определенную диагностику.</span><span class="sxs-lookup"><span data-stu-id="598e1-172">Specify a ruleset file that configures specific diagnostics.</span></span>

```xml
<CodeAnalysisRuleSet>MyConfiguration.ruleset</CodeAnalysisRuleSet>
```

<span data-ttu-id="598e1-173">`MyConfiguration.ruleset` — это путь к файлу набора правил.</span><span class="sxs-lookup"><span data-stu-id="598e1-173">Where `MyConfiguration.ruleset` is the path to the ruleset file.</span></span> <span data-ttu-id="598e1-174">Дополнительные сведения об использовании наборов правил см. в статье [Использование набора правил для группирования правил анализа кода](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).</span><span class="sxs-lookup"><span data-stu-id="598e1-174">For more information on using rule sets, see the article in the [Visual Studio documentation on Rule sets](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).</span></span>

## <a name="errorlog"></a><span data-ttu-id="598e1-175">ErrorLog</span><span class="sxs-lookup"><span data-stu-id="598e1-175">ErrorLog</span></span>

<span data-ttu-id="598e1-176">Укажите файл для записи данных диагностики компилятора и анализатора в журнал.</span><span class="sxs-lookup"><span data-stu-id="598e1-176">Specify a file to log all compiler and analyzer diagnostics.</span></span>

```xml
<ErrorLog>MyConfiguration.ruleset</ErrorLog>
```

<span data-ttu-id="598e1-177">Параметр **ErrorLog** указывает компилятору вывести [журнал в формате обмена результатами статического анализа (SARIF)](https://github.com/microsoft/sarif-tutorials/blob/main/docs/1-Introduction.md#:~:text=What%20is%20SARIF%3F,for%20use%20by%20simpler%20tools).</span><span class="sxs-lookup"><span data-stu-id="598e1-177">The **ErrorLog** option causes the compiler to output a [Static Analysis Results Interchange Format (SARIF) log](https://github.com/microsoft/sarif-tutorials/blob/main/docs/1-Introduction.md#:~:text=What%20is%20SARIF%3F,for%20use%20by%20simpler%20tools).</span></span> <span data-ttu-id="598e1-178">Журналы SARIF обычно считываются средствами, которые анализируют результаты диагностики компилятора и анализатора.</span><span class="sxs-lookup"><span data-stu-id="598e1-178">SARIF logs are typically read by tools that analyze the results from compiler and analyzer diagnostics.</span></span>

## <a name="reportanalyzer"></a><span data-ttu-id="598e1-179">ReportAnalyzer</span><span class="sxs-lookup"><span data-stu-id="598e1-179">ReportAnalyzer</span></span>

<span data-ttu-id="598e1-180">Включение в отчет дополнительных сведений об анализаторе, включая время выполнения.</span><span class="sxs-lookup"><span data-stu-id="598e1-180">Report additional analyzer information, such as execution time.</span></span>

```xml
<ReportAnalyzer>true</ReportAnalyzer>
```

<span data-ttu-id="598e1-181">Параметр **ReportAnalyzer** указывает компилятору создавать дополнительные сведения журнала MSBuild, в которых подробно описываются характеристики производительности анализаторов в сборке.</span><span class="sxs-lookup"><span data-stu-id="598e1-181">The **ReportAnalyzer** option causes the compiler to emit extra MSBuild log information that details the performance characteristics of analyzers in the build.</span></span> <span data-ttu-id="598e1-182">Обычно он используется создателями анализаторов в ходе проверки анализатора.</span><span class="sxs-lookup"><span data-stu-id="598e1-182">It's typically used by analyzer authors as part of validating the analyzer.</span></span>
