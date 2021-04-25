---
title: Выражение switch в справочнике по C#
description: Сведения о выражении switch в C#, которое реализует аналогичную switch семантику на основе сопоставления шаблонов.
ms.date: 04/16/2021
f1_keywords:
- switch_CSharpKeyword
helpviewer_keywords:
- switch expression [C#]
- pattern matching [C#]
ms.openlocfilehash: ce892598f364e4934613a797d9290fa385abd4c8
ms.sourcegitcommit: 23e2bc267872ce6ea22db4bf6478fe57bcba4bc8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2021
ms.locfileid: "107592270"
---
# <a name="switch-expression-c-reference"></a><span data-ttu-id="e6c4e-103">Выражение switch (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="e6c4e-103">switch expression (C# reference)</span></span>

<span data-ttu-id="e6c4e-104">Начиная с версии C# 8.0, вы можете использовать `switch`, чтобы вычислить какое-то одно выражение из списка кандидатов, основываясь на сопоставлении шаблонов по входному выражению.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-104">Beginning with C# 8.0, you use the `switch` expression to evaluate a single expression from a list of candidate expressions based on a pattern match with an input expression.</span></span> <span data-ttu-id="e6c4e-105">Дополнительные сведения об операторе `switch`, который поддерживает семантику, аналогичную `switch`, в контексте оператора, см. в статье об [операторе `switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-105">For information about the `switch` statement that supports `switch`-like semantics in a statement context, see the [`switch` statement](../keywords/switch.md) article.</span></span>

<span data-ttu-id="e6c4e-106">В следующем примере демонстрируется выражение `switch`, которое преобразует значения [`enum`](../builtin-types/enum.md), представляющие визуальные направления на интерактивной карте, в соответствующие стороны света.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-106">The following example demonstrates a `switch` expression, which converts values of an [`enum`](../builtin-types/enum.md) representing visual directions in an online map to the corresponding cardinal directions:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

<span data-ttu-id="e6c4e-107">В предыдущем примере показаны основные элементы выражения `switch`.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-107">The preceding example shows the basic elements of a `switch` expression:</span></span>

- <span data-ttu-id="e6c4e-108">Выражение, за которым следует ключевое слово `switch`.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-108">An expression followed by the `switch` keyword.</span></span> <span data-ttu-id="e6c4e-109">В предыдущем примере это параметр метода `direction`.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-109">In the preceding example, it's the `direction` method parameter.</span></span>
- <span data-ttu-id="e6c4e-110">*Ветви выражения `switch`* , разделенные запятыми.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-110">The *`switch` expression arms*, separated by commas.</span></span> <span data-ttu-id="e6c4e-111">Каждая ветвь выражения `switch` содержит *шаблон*, необязательное [*охранное условие*](#case-guards), маркер `=>` и *выражение*.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-111">Each `switch` expression arm contains a *pattern*, an optional [*case guard*](#case-guards), the `=>` token, and an *expression*.</span></span>

<span data-ttu-id="e6c4e-112">В предыдущем примере выражение `switch` использует следующие шаблоны.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-112">At the preceding example, a `switch` expression uses the following patterns:</span></span>

- <span data-ttu-id="e6c4e-113">[Шаблон константы](patterns.md#constant-pattern), используемый для обработки определенных значений перечисления `Direction`.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-113">A [constant pattern](patterns.md#constant-pattern) that is used to handle the defined values of the `Direction` enumeration.</span></span>
- <span data-ttu-id="e6c4e-114">[Шаблон пустой переменной](patterns.md#discard-pattern), используемый для обработки любых целочисленных значений, которые не имеют соответствующих элементов в перечислении `Direction` (например, `(Direction)10`).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-114">A [discard pattern](patterns.md#discard-pattern) that is used to handle any integer value that doesn't have the corresponding member of the `Direction` enumeration (for example, `(Direction)10`).</span></span> <span data-ttu-id="e6c4e-115">Это делает выражение `switch` [исчерпывающим](#non-exhaustive-switch-expressions).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-115">That makes the `switch` expression [exhaustive](#non-exhaustive-switch-expressions).</span></span>

<span data-ttu-id="e6c4e-116">Сведения о шаблонах, поддерживаемых выражением `switch`, см. в статье [Шаблоны](patterns.md).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-116">For information about the patterns supported by a `switch` expression, see [Patterns](patterns.md).</span></span>

<span data-ttu-id="e6c4e-117">Результатом выражения `switch` является значение выражения первой ветви `switch`, чей шаблон соответствует входному выражению, а охранное условие, если таковое есть, принимает значение `true`.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-117">The result of a `switch` expression is the value of the expression of the first `switch` expression arm whose pattern matches the input expression and whose case guard, if present, evaluates to `true`.</span></span> <span data-ttu-id="e6c4e-118">Ветви выражения `switch` вычисляются в том порядке, в котором они приведены в тексте.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-118">The `switch` expression arms are evaluated in text order.</span></span>

<span data-ttu-id="e6c4e-119">Когда выбрать идущую ниже ветвь выражения `switch` невозможно, так как идущая выше ветвь `switch` соответствует всем значениям этого выражения, компилятор выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-119">The compiler generates an error when a lower `switch` expression arm can't be chosen because a higher `switch` expression arm matches all its values.</span></span>

## <a name="case-guards"></a><span data-ttu-id="e6c4e-120">Охранные условия</span><span class="sxs-lookup"><span data-stu-id="e6c4e-120">Case guards</span></span>

<span data-ttu-id="e6c4e-121">Шаблон может недостаточно полно выражать условие вычисления выражения ветви.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-121">A pattern may be not expressive enough to specify the condition for the evaluation of an arm's expression.</span></span> <span data-ttu-id="e6c4e-122">В этом случае можно использовать охранное условие.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-122">In such a case, you can use a case guard.</span></span> <span data-ttu-id="e6c4e-123">Это дополнительное условие, которое должно выполняться помимо соответствия шаблону.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-123">That is an additional condition that must be satisfied together with a matched pattern.</span></span> <span data-ttu-id="e6c4e-124">Охранное условие указывается после ключевого слова `when`, идущего за шаблоном, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-124">You specify a case guard after the `when` keyword that follows a pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="CaseGuardExample":::

<span data-ttu-id="e6c4e-125">В предыдущем примере используются [шаблоны свойств](patterns.md#property-pattern) с вложенными [шаблонами var](patterns.md#var-pattern).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-125">The preceding example uses [property patterns](patterns.md#property-pattern) with nested [var patterns](patterns.md#var-pattern).</span></span>

## <a name="non-exhaustive-switch-expressions"></a><span data-ttu-id="e6c4e-126">Неисчерпывающие выражения switch</span><span class="sxs-lookup"><span data-stu-id="e6c4e-126">Non-exhaustive switch expressions</span></span>

<span data-ttu-id="e6c4e-127">Если ни один из шаблонов выражения `switch` не соответствует входному значению, среда выполнения выдает исключение.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-127">If none of a `switch` expression's patterns matches an input value, the runtime throws an exception.</span></span> <span data-ttu-id="e6c4e-128">В .NET Core 3.0 и более поздних версиях исключением является <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-128">In .NET Core 3.0 and later versions, the exception is a <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6c4e-129">В .NET Framework исключением является <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-129">In .NET Framework, the exception is an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="e6c4e-130">Если выражение `switch` не обрабатывает все возможные входные значения, компилятор генерирует предупреждение.</span><span class="sxs-lookup"><span data-stu-id="e6c4e-130">The compiler generates a warning if a `switch` expression doesn't handle all possible input values.</span></span>

> [!TIP]
> <span data-ttu-id="e6c4e-131">Чтобы гарантировать, что выражение `switch` обработает все возможные входные значения, укажите ветвь выражения `switch` с [шаблоном пустой переменной](patterns.md#discard-pattern).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-131">To guarantee that a `switch` expression handles all possible input values, provide a `switch` expression arm with a [discard pattern](patterns.md#discard-pattern).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e6c4e-132">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="e6c4e-132">C# language specification</span></span>

<span data-ttu-id="e6c4e-133">Дополнительные сведения см. в разделе о [выражении `switch`](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression) в этой [заметке о предлагаемых функциях](~/_csharplang/proposals/csharp-8.0/patterns.md).</span><span class="sxs-lookup"><span data-stu-id="e6c4e-133">For more information, see the [`switch` expression](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression) section of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/patterns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6c4e-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e6c4e-134">See also</span></span>

- [<span data-ttu-id="e6c4e-135">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="e6c4e-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e6c4e-136">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="e6c4e-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="e6c4e-137">Шаблоны</span><span class="sxs-lookup"><span data-stu-id="e6c4e-137">Patterns</span></span>](patterns.md)
- [<span data-ttu-id="e6c4e-138">Учебник. Использование сопоставления шаблонов для создания управляемых типами и управляемых данными алгоритмов</span><span class="sxs-lookup"><span data-stu-id="e6c4e-138">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>](../../tutorials/pattern-matching.md)
- [<span data-ttu-id="e6c4e-139">Инструкция `switch`</span><span class="sxs-lookup"><span data-stu-id="e6c4e-139">`switch` statement</span></span>](../keywords/switch.md)
