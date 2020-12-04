---
title: Предопределенные файлы конфигурации (анализ кода)
description: Узнайте, как использовать предопределенные файлы editorconfig и наборов правил для назначения конкретных типов анализа кода.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "96593137"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="2a69d-103">Предопределенные файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="2a69d-103">Predefined configuration files</span></span>

<span data-ttu-id="2a69d-104">Доступны предопределенные файлы EditorConfig и [наборов правил](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) , которые позволяют быстро и легко включить категорию правил качества кода, например правила безопасности или разработки.</span><span class="sxs-lookup"><span data-stu-id="2a69d-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="2a69d-105">Включив определенную категорию правил, можно вычислить целевые проблемы и конкретные условия.</span><span class="sxs-lookup"><span data-stu-id="2a69d-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="2a69d-106">Чтобы получить доступ к этим предопределенным файлам, установите пакет анализатора NuGet [Microsoft. CodeAnalysis. нетанализерс](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) .</span><span class="sxs-lookup"><span data-stu-id="2a69d-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="2a69d-107">[Microsoft. CodeAnalysis. нетанализерс](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) включает предопределенные файлы EditorConfig и наборы правил для следующих категорий правил:</span><span class="sxs-lookup"><span data-stu-id="2a69d-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="2a69d-108">Все правила</span><span class="sxs-lookup"><span data-stu-id="2a69d-108">All rules</span></span>
- <span data-ttu-id="2a69d-109">Поток данных</span><span class="sxs-lookup"><span data-stu-id="2a69d-109">Dataflow</span></span>
- <span data-ttu-id="2a69d-110">Конструирование</span><span class="sxs-lookup"><span data-stu-id="2a69d-110">Design</span></span>
- <span data-ttu-id="2a69d-111">Документация</span><span class="sxs-lookup"><span data-stu-id="2a69d-111">Documentation</span></span>
- <span data-ttu-id="2a69d-112">Глобализация</span><span class="sxs-lookup"><span data-stu-id="2a69d-112">Globalization</span></span>
- <span data-ttu-id="2a69d-113">Совместимость</span><span class="sxs-lookup"><span data-stu-id="2a69d-113">Interoperability</span></span>
- <span data-ttu-id="2a69d-114">Удобство обслуживания</span><span class="sxs-lookup"><span data-stu-id="2a69d-114">Maintainability</span></span>
- <span data-ttu-id="2a69d-115">Именование</span><span class="sxs-lookup"><span data-stu-id="2a69d-115">Naming</span></span>
- <span data-ttu-id="2a69d-116">Производительность</span><span class="sxs-lookup"><span data-stu-id="2a69d-116">Performance</span></span>
- <span data-ttu-id="2a69d-117">Перенесено из FxCop</span><span class="sxs-lookup"><span data-stu-id="2a69d-117">Ported from FxCop</span></span>
- <span data-ttu-id="2a69d-118">надежность;</span><span class="sxs-lookup"><span data-stu-id="2a69d-118">Reliability</span></span>
- <span data-ttu-id="2a69d-119">Безопасность</span><span class="sxs-lookup"><span data-stu-id="2a69d-119">Security</span></span>
- <span data-ttu-id="2a69d-120">Использование</span><span class="sxs-lookup"><span data-stu-id="2a69d-120">Usage</span></span>

<span data-ttu-id="2a69d-121">Каждая из этих категорий правил имеет файл EditorConfig или набора правил:</span><span class="sxs-lookup"><span data-stu-id="2a69d-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="2a69d-122">Включить все правила в категории (и отключить все остальные правила)</span><span class="sxs-lookup"><span data-stu-id="2a69d-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="2a69d-123">Используйте уровень серьезности по умолчанию для каждого правила и параметр включен по умолчанию (и отключите все остальные правила).</span><span class="sxs-lookup"><span data-stu-id="2a69d-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="2a69d-124">Категория "все правила" имеет дополнительный файл EditorConfig или набора правил для отключения всех правил.</span><span class="sxs-lookup"><span data-stu-id="2a69d-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="2a69d-125">Используйте этот файл, чтобы быстро избавиться от любых предупреждений или ошибок анализатора в проекте.</span><span class="sxs-lookup"><span data-stu-id="2a69d-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="2a69d-126">Предопределенные файлы EditorConfig</span><span class="sxs-lookup"><span data-stu-id="2a69d-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="2a69d-127">Предопределенные файлы EditorConfig для пакета анализатора Microsoft. CodeAnalysis. Нетанализерс находятся в подкаталоге *EditorConfig* , где установлен пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="2a69d-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="2a69d-128">Например, файл EditorConfig для включения всех правил безопасности находится в папке *EditorConfig/секуритирулесенаблед/. EditorConfig*.</span><span class="sxs-lookup"><span data-stu-id="2a69d-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="2a69d-129">Скопируйте выбранный файл *. editorconfig* в корневой каталог проекта.</span><span class="sxs-lookup"><span data-stu-id="2a69d-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="2a69d-130">Предопределенные наборы правил</span><span class="sxs-lookup"><span data-stu-id="2a69d-130">Predefined rule sets</span></span>

<span data-ttu-id="2a69d-131">Стандартные файлы набора правил для пакета анализатора Microsoft. CodeAnalysis. Нетанализерс находятся в подкаталоге *набора правил* , в котором установлен пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="2a69d-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="2a69d-132">Например, файл набора правил для включения всех правил безопасности находится в папке *RuleSets/секуритирулесенаблед. RuleSet*.</span><span class="sxs-lookup"><span data-stu-id="2a69d-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="2a69d-133">Скопируйте один или несколько наборов правил и вставьте их в каталог, содержащий проект.</span><span class="sxs-lookup"><span data-stu-id="2a69d-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a69d-134">См. также</span><span class="sxs-lookup"><span data-stu-id="2a69d-134">See also</span></span>

- [<span data-ttu-id="2a69d-135">Конфигурация анализатора</span><span class="sxs-lookup"><span data-stu-id="2a69d-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="2a69d-136">Параметры правила стиля кода .NET для EditorConfig</span><span class="sxs-lookup"><span data-stu-id="2a69d-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
