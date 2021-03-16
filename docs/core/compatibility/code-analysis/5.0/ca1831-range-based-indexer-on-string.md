---
title: 'Критическое изменение. CA1831: используйте AsSpan вместо индексаторов на основе диапазона для строки'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA1831.
ms.date: 08/21/2020
ms.openlocfilehash: 1ed4e2bdde9c3d525f95963f316551909ac3de7c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257795"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="c80a0-103">Предупреждение CA1831: используйте AsSpan вместо индексаторов на основе диапазона для строки</span><span class="sxs-lookup"><span data-stu-id="c80a0-103">Warning CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="c80a0-104">Правило анализатора кода .NET [CA1831](/visualstudio/code-quality/ca1831) включено по умолчанию, начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="c80a0-104">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="c80a0-105">Оно создает предупреждение сборки для любого кода, в котором для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось.</span><span class="sxs-lookup"><span data-stu-id="c80a0-105">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

## <a name="change-description"></a><span data-ttu-id="c80a0-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c80a0-106">Change description</span></span>

<span data-ttu-id="c80a0-107">Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="c80a0-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="c80a0-108">Некоторые из этих правил включены по умолчанию, включая [CA1831](/visualstudio/code-quality/ca1831).</span><span class="sxs-lookup"><span data-stu-id="c80a0-108">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="c80a0-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="c80a0-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="c80a0-110">Правило CA1831 находит экземпляры, в которых для строки используется индексатор на основе <xref:System.Range>, но копирование не планировалось.</span><span class="sxs-lookup"><span data-stu-id="c80a0-110">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="c80a0-111">Если индексатор на основе <xref:System.Range> используется непосредственно в строке для создания неявного приведения, то создается ненужная копия запрошенной части строки.</span><span class="sxs-lookup"><span data-stu-id="c80a0-111">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="c80a0-112">Пример:</span><span class="sxs-lookup"><span data-stu-id="c80a0-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="c80a0-113">CA1831 предлагает использовать индексатор на основе <xref:System.Range> в *span* строки.</span><span class="sxs-lookup"><span data-stu-id="c80a0-113">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="c80a0-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="c80a0-114">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a><span data-ttu-id="c80a0-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c80a0-115">Version introduced</span></span>

<span data-ttu-id="c80a0-116">5.0</span><span class="sxs-lookup"><span data-stu-id="c80a0-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c80a0-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c80a0-117">Recommended action</span></span>

- <span data-ttu-id="c80a0-118">Чтобы исправить код и избежать ненужных выделений, вызовите <xref:System.MemoryExtensions.AsSpan(System.String)> или <xref:System.MemoryExtensions.AsMemory(System.String)> перед использованием индексатора на основе <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="c80a0-118">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="c80a0-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="c80a0-119">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="c80a0-120">Если вы не хотите изменять код, можно отключить правило, задав серьезность `suggestion` или `none`.</span><span class="sxs-lookup"><span data-stu-id="c80a0-120">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="c80a0-121">Дополнительные сведения см. в разделе [Настройка правил анализа кода](../../../../fundamentals/code-analysis/configuration-options.md).</span><span class="sxs-lookup"><span data-stu-id="c80a0-121">For more information, see [Configure code analysis rules](../../../../fundamentals/code-analysis/configuration-options.md).</span></span>

- <span data-ttu-id="c80a0-122">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="c80a0-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="c80a0-123">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="c80a0-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c80a0-124">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c80a0-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
