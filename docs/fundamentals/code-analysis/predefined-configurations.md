---
title: Предопределенные файлы конфигурации (анализ кода)
description: Сведения о том, как использовать предопределенные файлы EditorConfig и наборов правил для применения конкретных типов анализа кода.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 748ab8a9ddfcfcadeb33da877769cedac901655a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876595"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="32e77-103">Предопределенные файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="32e77-103">Predefined configuration files</span></span>

<span data-ttu-id="32e77-104">Предопределенные файлы EditorConfig и [наборов правил](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) позволяют быстро и легко включить конкретную категорию правил качества кода, например правил безопасности или разработки.</span><span class="sxs-lookup"><span data-stu-id="32e77-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="32e77-105">Включая определенную категорию правил, вы сможете выявлять соответствующие проблемы и проверять условия.</span><span class="sxs-lookup"><span data-stu-id="32e77-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="32e77-106">Чтобы использовать предопределенные файлы, установите пакет NuGet [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) для анализатора.</span><span class="sxs-lookup"><span data-stu-id="32e77-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="32e77-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) содержит предопределенные файлы EditorConfig и наборы правил для следующих категорий правил:</span><span class="sxs-lookup"><span data-stu-id="32e77-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="32e77-108">Все правила</span><span class="sxs-lookup"><span data-stu-id="32e77-108">All rules</span></span>
- <span data-ttu-id="32e77-109">Поток данных</span><span class="sxs-lookup"><span data-stu-id="32e77-109">Dataflow</span></span>
- <span data-ttu-id="32e77-110">Конструирование</span><span class="sxs-lookup"><span data-stu-id="32e77-110">Design</span></span>
- <span data-ttu-id="32e77-111">Документация</span><span class="sxs-lookup"><span data-stu-id="32e77-111">Documentation</span></span>
- <span data-ttu-id="32e77-112">Глобализация</span><span class="sxs-lookup"><span data-stu-id="32e77-112">Globalization</span></span>
- <span data-ttu-id="32e77-113">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="32e77-113">Interoperability</span></span>
- <span data-ttu-id="32e77-114">Удобство обслуживания</span><span class="sxs-lookup"><span data-stu-id="32e77-114">Maintainability</span></span>
- <span data-ttu-id="32e77-115">Именование</span><span class="sxs-lookup"><span data-stu-id="32e77-115">Naming</span></span>
- <span data-ttu-id="32e77-116">Производительность</span><span class="sxs-lookup"><span data-stu-id="32e77-116">Performance</span></span>
- <span data-ttu-id="32e77-117">Перенесенные из FxCop</span><span class="sxs-lookup"><span data-stu-id="32e77-117">Ported from FxCop</span></span>
- <span data-ttu-id="32e77-118">надежность;</span><span class="sxs-lookup"><span data-stu-id="32e77-118">Reliability</span></span>
- <span data-ttu-id="32e77-119">Безопасность</span><span class="sxs-lookup"><span data-stu-id="32e77-119">Security</span></span>
- <span data-ttu-id="32e77-120">Использование</span><span class="sxs-lookup"><span data-stu-id="32e77-120">Usage</span></span>

<span data-ttu-id="32e77-121">Для каждой из этих категорий правил предоставляется файл EditorConfig или набора правил, который позволяет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="32e77-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="32e77-122">включить все правила в категории (и отключить все остальные правила);</span><span class="sxs-lookup"><span data-stu-id="32e77-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="32e77-123">указать для каждого правила уровень серьезности по умолчанию и состояние включения по умолчанию (и отключите все остальные правила).</span><span class="sxs-lookup"><span data-stu-id="32e77-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="32e77-124">Для категории "Все правила" есть дополнительный файл EditorConfig или набора правил, который отключает все правила.</span><span class="sxs-lookup"><span data-stu-id="32e77-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="32e77-125">Этот файл поможет вам быстро избавиться от всех предупреждений и ошибок анализатора в проекте.</span><span class="sxs-lookup"><span data-stu-id="32e77-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="32e77-126">Предопределенные файлы EditorConfig</span><span class="sxs-lookup"><span data-stu-id="32e77-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="32e77-127">Предопределенные файлы EditorConfig для пакета анализатора Microsoft.CodeAnalysis.NetAnalyzers размещены в подкаталоге *editorconfig* того каталога, где установлен пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="32e77-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="32e77-128">Например, файл EditorConfig для включения всех правил безопасности находится в папке *editorconfig/SecurityRulesEnabled/.editorconfig*.</span><span class="sxs-lookup"><span data-stu-id="32e77-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="32e77-129">Скопируйте нужный файл с расширением *.editorconfig* в корневой каталог проекта.</span><span class="sxs-lookup"><span data-stu-id="32e77-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="32e77-130">Предопределенные наборы правил</span><span class="sxs-lookup"><span data-stu-id="32e77-130">Predefined rule sets</span></span>

<span data-ttu-id="32e77-131">Предопределенные файлы наборов правил для пакета анализатора Microsoft.CodeAnalysis.NetAnalyzers размещены в подкаталоге *rulesets* того каталога, где установлен пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="32e77-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="32e77-132">Например, файл набора правил для включения всех правил безопасности находится в папке *rulesets/SecurityRulesEnabled.ruleset*.</span><span class="sxs-lookup"><span data-stu-id="32e77-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="32e77-133">Скопируйте один или несколько наборов правил и вставьте их в каталог со своим проектом.</span><span class="sxs-lookup"><span data-stu-id="32e77-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="32e77-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="32e77-134">See also</span></span>

- [<span data-ttu-id="32e77-135">Конфигурация анализатора</span><span class="sxs-lookup"><span data-stu-id="32e77-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/main/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="32e77-136">Параметры правила стиля кода для .NET в EditorConfig</span><span class="sxs-lookup"><span data-stu-id="32e77-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
