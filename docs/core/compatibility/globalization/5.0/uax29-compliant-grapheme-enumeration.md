---
title: Критическое изменение. Теперь StringInfo и TextElementEnumerator совместимы с UAX29
description: Сведения о критическом изменении глобализации в .NET 5.0, где кластеры графем процесса StringInfo и TextElementEnumerator совместимы с последней версией стандарта Unicode.
ms.date: 04/07/2020
ms.openlocfilehash: cd5ae5a3eb9f2dd9c02bc179a40d454d24101199
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759625"
---
# <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="a53b5-103">Теперь StringInfo и TextElementEnumerator совместимы с UAX29</span><span class="sxs-lookup"><span data-stu-id="a53b5-103">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="a53b5-104">До этого изменения <xref:System.Globalization.StringInfo?displayProperty=fullName> и <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> обрабатывали все кластеры графем неправильно.</span><span class="sxs-lookup"><span data-stu-id="a53b5-104">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="a53b5-105">Некоторые графемы были разбиты на составные компоненты, а не объединялись.</span><span class="sxs-lookup"><span data-stu-id="a53b5-105">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="a53b5-106">Теперь <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> обрабатывают кластеры графем в соответствии с последней версией стандарта Юникода.</span><span class="sxs-lookup"><span data-stu-id="a53b5-106">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="a53b5-107">Кроме того, метод <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>, который меняет порядок символов строки в Visual Basic на обратный, теперь также соответствует стандарту Юникода для кластеров графем.</span><span class="sxs-lookup"><span data-stu-id="a53b5-107">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

## <a name="change-description"></a><span data-ttu-id="a53b5-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="a53b5-108">Change description</span></span>

<span data-ttu-id="a53b5-109">[Графема](https://www.unicode.org/glossary/#grapheme) или [расширенный кластер графем](https://www.unicode.org/glossary/#extended_grapheme_cluster) — это отдельный воспринимаемый пользователем символ, который может состоять из нескольких кодовых точек Юникода.</span><span class="sxs-lookup"><span data-stu-id="a53b5-109">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="a53b5-110">Например, строка, содержащая тайский символ "кам" (:::no-loc text="กำ":::), состоит из двух следующих символов:</span><span class="sxs-lookup"><span data-stu-id="a53b5-110">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="a53b5-111">:::no-loc text="ก"::: (= '\u0e01') — тайский символ "ко кай"</span><span class="sxs-lookup"><span data-stu-id="a53b5-111">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="a53b5-112">:::no-loc text=" ำ"::: (= '\u0e33') — тайский символ "сара ам"</span><span class="sxs-lookup"><span data-stu-id="a53b5-112">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="a53b5-113">При отображении пользователю операционная система объединяет эти два символа для формирования одного отображаемого символа (или графемы) "кам" или :::no-loc text="กำ":::.</span><span class="sxs-lookup"><span data-stu-id="a53b5-113">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="a53b5-114">Эмодзи также могут состоять из нескольких символов, объединенных для единообразного отображения.</span><span class="sxs-lookup"><span data-stu-id="a53b5-114">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="a53b5-115">В документации по .NET при ссылке на графему иногда применяется термин "текстовый элемент".</span><span class="sxs-lookup"><span data-stu-id="a53b5-115">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="a53b5-116">Классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> проверяют строки и возвращают сведения о содержащихся в них графемах.</span><span class="sxs-lookup"><span data-stu-id="a53b5-116">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="a53b5-117">В .NET Framework (все версии) и .NET Core 3.x и более ранних версий эти два класса используют пользовательскую логику, которая обрабатывает некоторые комбинирующие классы, но не полностью соответствует [стандарту Юникода](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="a53b5-117">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="a53b5-118">Например, классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> ошибочно разделяют один тайский символ "кам" на составляющие компоненты вместо того, чтобы объединить их.</span><span class="sxs-lookup"><span data-stu-id="a53b5-118">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="a53b5-119">Эти классы также ошибочно разбивают символ эмодзи "🤷🏽‍♀️" на четыре кластера (пожимание плечами, модификатор тона кожи, модификатор пола и невидимый объединяющий блок) вместо того, чтобы объединить их в один кластер графем.</span><span class="sxs-lookup"><span data-stu-id="a53b5-119">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="a53b5-120">Начиная с .NET 5 классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> удовлетворяют требованиям стандарта Юникода, как указано в [приложении к стандарту Юникод \#29, редакция 35, раздел 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="a53b5-120">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="a53b5-121">В частности, теперь они возвращают [расширенные кластеры графем](https://www.unicode.org/glossary/#extended_grapheme_cluster) для всех комбинирующих классов.</span><span class="sxs-lookup"><span data-stu-id="a53b5-121">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="a53b5-122">Рассмотрим следующий код C#:</span><span class="sxs-lookup"><span data-stu-id="a53b5-122">Consider the following C# code:</span></span>

```csharp
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

<span data-ttu-id="a53b5-123">В .NET Framework и .NET Core 3.x и более ранних версий графемы разделяются, а выходные данные в консоли выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a53b5-123">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

<span data-ttu-id="a53b5-124">В .NET 5 и более поздних версий графемы объединяются, а выходные данные в консоли выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a53b5-124">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="a53b5-125">Кроме того, начиная с .NET 5 метод <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>, который меняет порядок символов строки в Visual Basic на обратный, также соответствует стандарту Юникода для кластеров графем.</span><span class="sxs-lookup"><span data-stu-id="a53b5-125">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="a53b5-126">Эти изменения являются частью более обширного набора улучшений для Юникода и UTF-8 в .NET, включая API перечисления расширенных кластеров графем, который дополняет интерфейсы API перечисления скалярных значений Юникода, появившиеся с типом <xref:System.Text.Rune?displayProperty=fullName> в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a53b5-126">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a53b5-127">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a53b5-127">Version introduced</span></span>

<span data-ttu-id="a53b5-128">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a53b5-128">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a53b5-129">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a53b5-129">Recommended action</span></span>

<span data-ttu-id="a53b5-130">Никаких дополнительных действий от вас не требуется.</span><span class="sxs-lookup"><span data-stu-id="a53b5-130">You don't need to take any action.</span></span> <span data-ttu-id="a53b5-131">Ваши приложения будут автоматически обеспечивать более полное соответствие стандартам в различных сценариях, связанных с глобализацией.</span><span class="sxs-lookup"><span data-stu-id="a53b5-131">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a53b5-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a53b5-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

### Category

Globalization

-->
