---
title: 'Критическое изменение. CA2247: аргумент для конструктора TaskCompletionSource должен соответствовать значению TaskCreationOptions'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2247.
ms.date: 09/03/2020
ms.openlocfilehash: 6c7accaad312352a1448406f2bbf4189f3df1ee5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257704"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="3342c-103">Предупреждение CA2247: аргумент для конструктора TaskCompletionSource должен соответствовать значению TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="3342c-103">Warning CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="3342c-104">Правило [CA2247](/visualstudio/code-quality/ca2247) анализатора кода .NET включено по умолчанию, начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="3342c-104">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="3342c-105">Оно создает предупреждение сборки для вызовов конструктора <xref:System.Threading.Tasks.TaskCompletionSource%601>, которые передают аргумент типа <xref:System.Threading.Tasks.TaskContinuationOptions>.</span><span class="sxs-lookup"><span data-stu-id="3342c-105">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

## <a name="change-description"></a><span data-ttu-id="3342c-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="3342c-106">Change description</span></span>

<span data-ttu-id="3342c-107">Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="3342c-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="3342c-108">Некоторые из этих правил включены по умолчанию, в том числе [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="3342c-108">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="3342c-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="3342c-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="3342c-110">Правило CA2247 находит вызовы конструктора <xref:System.Threading.Tasks.TaskCompletionSource%601>, которые передают аргумент типа <xref:System.Threading.Tasks.TaskContinuationOptions>.</span><span class="sxs-lookup"><span data-stu-id="3342c-110">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="3342c-111">Тип <xref:System.Threading.Tasks.TaskCompletionSource%601> имеет конструктор, принимающий значение <xref:System.Threading.Tasks.TaskCreationOptions>, и другой конструктор, принимающий <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="3342c-111">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="3342c-112">Если вы случайно передадите значение <xref:System.Threading.Tasks.TaskContinuationOptions> вместо значения <xref:System.Threading.Tasks.TaskCreationOptions>, конструктор с параметром <xref:System.Object> будет вызван во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3342c-112">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="3342c-113">Код будет компилироваться и выполняться, но поведение будет отличаться от ожидаемого.</span><span class="sxs-lookup"><span data-stu-id="3342c-113">Your code will compile and run but won't have the intended behavior.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3342c-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3342c-114">Version introduced</span></span>

<span data-ttu-id="3342c-115">5.0</span><span class="sxs-lookup"><span data-stu-id="3342c-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3342c-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="3342c-116">Recommended action</span></span>

- <span data-ttu-id="3342c-117">Замените аргумент <xref:System.Threading.Tasks.TaskContinuationOptions> соответствующим значением <xref:System.Threading.Tasks.TaskCreationOptions>.</span><span class="sxs-lookup"><span data-stu-id="3342c-117">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="3342c-118">Не отключайте это предупреждение, так как оно почти всегда выделяет ошибку в коде.</span><span class="sxs-lookup"><span data-stu-id="3342c-118">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="3342c-119">См. раздел [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="3342c-119">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="3342c-120">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="3342c-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="3342c-121">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="3342c-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3342c-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3342c-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
