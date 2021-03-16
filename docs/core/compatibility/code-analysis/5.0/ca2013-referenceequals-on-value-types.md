---
title: 'Критическое изменение. CA2013: не используйте ReferenceEquals с типами значений'
description: Сведения о критическом изменении в .NET 5, вызванном включением правила анализа кода CA2013.
ms.date: 09/03/2020
ms.openlocfilehash: fc68d9a3af0d629dc39aba0091d32b1982d6f2c5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257769"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="23303-103">Предупреждение CA2013: не используйте ReferenceEquals с типами значений</span><span class="sxs-lookup"><span data-stu-id="23303-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="23303-104">Правило [CA2013](/visualstudio/code-quality/ca2013) анализатора кода .NET включено по умолчанию начиная с .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="23303-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="23303-105">Оно создает предупреждение сборки для любого кода, где для сравнения одного или нескольких типов значений на предмет равенства используется <xref:System.Object.ReferenceEquals(System.Object,System.Object)>.</span><span class="sxs-lookup"><span data-stu-id="23303-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="23303-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="23303-106">Change description</span></span>

<span data-ttu-id="23303-107">Начиная с .NET 5 пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="23303-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="23303-108">Некоторые из этих правил включены по умолчанию, в том числе [CA2013](/visualstudio/code-quality/ca2013).</span><span class="sxs-lookup"><span data-stu-id="23303-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="23303-109">Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.</span><span class="sxs-lookup"><span data-stu-id="23303-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="23303-110">Правило CA2013 находит экземпляры, где для сравнения одного или нескольких типов значений на предмет равенства используется <xref:System.Object.ReferenceEquals(System.Object,System.Object)>.</span><span class="sxs-lookup"><span data-stu-id="23303-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="23303-111">Сравнение типов значений на предмет равенства таким образом может привести к неверным результатам, так как значения упаковываются до их сравнения.</span><span class="sxs-lookup"><span data-stu-id="23303-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="23303-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> будет возвращать `false` даже в том случае, если сравниваемые значения представляют один и тот же экземпляр типа значения.</span><span class="sxs-lookup"><span data-stu-id="23303-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="23303-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="23303-113">Version introduced</span></span>

<span data-ttu-id="23303-114">5.0</span><span class="sxs-lookup"><span data-stu-id="23303-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="23303-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="23303-115">Recommended action</span></span>

- <span data-ttu-id="23303-116">Измените код, чтобы использовать соответствующий оператор равенства, например `==`.</span><span class="sxs-lookup"><span data-stu-id="23303-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="23303-117">Не следует отключать это предупреждение.</span><span class="sxs-lookup"><span data-stu-id="23303-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="23303-118">Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="23303-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="23303-119">Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="23303-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="23303-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="23303-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
