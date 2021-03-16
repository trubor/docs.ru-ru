---
title: 'Критическое изменение. CA2015: не определяйте методы завершения для типов, производных от MemoryManager<T>'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2015.
ms.date: 09/03/2020
ms.openlocfilehash: 4333cec7657657f7e9ba864bcb9979609ad379e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257743"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="8235b-103">Предупреждение CA2015: не определяйте методы завершения для типов, производных от MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="8235b-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="8235b-104">Правило [CA2015](/visualstudio/code-quality/ca2015) анализатора кода .NET включено по умолчанию, начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="8235b-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="8235b-105">Оно создает предупреждение сборки для всех типов, производных от <xref:System.Buffers.MemoryManager%601>, определяющих метод завершения.</span><span class="sxs-lookup"><span data-stu-id="8235b-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="8235b-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="8235b-106">Change description</span></span>

<span data-ttu-id="8235b-107">Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8235b-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="8235b-108">Некоторые из этих правил включены по умолчанию, в том числе [CA2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="8235b-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="8235b-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="8235b-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="8235b-110">Правило CA2015 помечает типы, производные от <xref:System.Buffers.MemoryManager%601>, которые определяют метод завершения.</span><span class="sxs-lookup"><span data-stu-id="8235b-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="8235b-111">Добавление метода завершения в тип, производный от <xref:System.Buffers.MemoryManager%601>, скорее всего, свидетельствует об ошибке.</span><span class="sxs-lookup"><span data-stu-id="8235b-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="8235b-112">Предполагается, что собственный ресурс, который мог быть получен в <xref:System.Span%601>, очищается, даже если он по-прежнему используется <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="8235b-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8235b-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8235b-113">Version introduced</span></span>

<span data-ttu-id="8235b-114">5.0</span><span class="sxs-lookup"><span data-stu-id="8235b-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8235b-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8235b-115">Recommended action</span></span>

- <span data-ttu-id="8235b-116">Удалите определение метода завершения.</span><span class="sxs-lookup"><span data-stu-id="8235b-116">Remove the finalizer definition.</span></span> <span data-ttu-id="8235b-117">См. раздел [CA2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="8235b-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="8235b-118">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="8235b-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="8235b-119">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="8235b-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8235b-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8235b-120">Affected APIs</span></span>

<span data-ttu-id="8235b-121">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="8235b-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
