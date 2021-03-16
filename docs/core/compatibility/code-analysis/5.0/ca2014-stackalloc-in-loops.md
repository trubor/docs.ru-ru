---
title: 'Критическое изменение. CA2014: не используйте stackalloc в циклах'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2014.
ms.date: 09/03/2020
ms.openlocfilehash: ac17c8ee588576947e21618a55c0eea883aa37ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257782"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="f55cf-103">Предупреждение CA2014: не используйте stackalloc в циклах</span><span class="sxs-lookup"><span data-stu-id="f55cf-103">Warning CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="f55cf-104">Правило [CA2014](/visualstudio/code-quality/ca2014) анализатора кода .NET включено по умолчанию, начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="f55cf-104">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="f55cf-105">Оно создает предупреждение сборки для любого кода C#, в котором используется выражение [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) внутри цикла.</span><span class="sxs-lookup"><span data-stu-id="f55cf-105">It produces a build warning for any C# code where a [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

## <a name="change-description"></a><span data-ttu-id="f55cf-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f55cf-106">Change description</span></span>

<span data-ttu-id="f55cf-107">Начиная с .NET 5, пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="f55cf-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="f55cf-108">Некоторые из этих правил включены по умолчанию, в том числе [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="f55cf-108">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="f55cf-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="f55cf-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="f55cf-110">Правило CA2014 ищет код C#, в котором выражение [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) используется внутри цикла.</span><span class="sxs-lookup"><span data-stu-id="f55cf-110">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="f55cf-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) выделяет память из текущего кадра стека.</span><span class="sxs-lookup"><span data-stu-id="f55cf-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="f55cf-112">Память не освобождается до тех пор, пока не будет возвращен текущий вызов метода, что может привести к переполнению стека.</span><span class="sxs-lookup"><span data-stu-id="f55cf-112">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="f55cf-113">Так как вы не можете перехватывать исключения переполнения стека, в таком случае работа приложения будет завершена.</span><span class="sxs-lookup"><span data-stu-id="f55cf-113">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f55cf-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f55cf-114">Version introduced</span></span>

<span data-ttu-id="f55cf-115">5.0</span><span class="sxs-lookup"><span data-stu-id="f55cf-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f55cf-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f55cf-116">Recommended action</span></span>

- <span data-ttu-id="f55cf-117">Старайтесь не использовать [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) в циклах.</span><span class="sxs-lookup"><span data-stu-id="f55cf-117">Avoid using [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="f55cf-118">Выделяйте блок памяти за пределами цикла и используйте его повторно внутри цикла.</span><span class="sxs-lookup"><span data-stu-id="f55cf-118">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="f55cf-119">См. раздел [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="f55cf-119">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="f55cf-120">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="f55cf-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="f55cf-121">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="f55cf-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f55cf-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f55cf-122">Affected APIs</span></span>

<span data-ttu-id="f55cf-123">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="f55cf-123">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
