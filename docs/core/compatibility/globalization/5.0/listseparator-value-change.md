---
title: Критическое изменение. Изменение значения TextInfo.ListSeparator
description: Узнайте о критическом изменении .NET 5.0, которое связано с тем, что значение по умолчанию TextInfo.ListSeparator изменилось между версиями 5.0 и 5.0.1.
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596423"
---
# <a name="textinfolistseparator-values-changed"></a><span data-ttu-id="a8613-103">Изменение значения TextInfo.ListSeparator</span><span class="sxs-lookup"><span data-stu-id="a8613-103">TextInfo.ListSeparator values changed</span></span>

<span data-ttu-id="a8613-104">Значения по умолчанию <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> для разных языков и региональных параметров изменились во всех операционных системах.</span><span class="sxs-lookup"><span data-stu-id="a8613-104">The default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures have changed on all operating systems.</span></span>

## <a name="change-description"></a><span data-ttu-id="a8613-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="a8613-105">Change description</span></span>

<span data-ttu-id="a8613-106">В .NET 5.0.0 в рамках [переключения с NLS на библиотеки ICU](icu-globalization-api.md) значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> по умолчанию для различных языков и региональных параметров в Windows изменились.</span><span class="sxs-lookup"><span data-stu-id="a8613-106">In .NET 5.0.0, as part of the [switch from NLS to ICU libraries](icu-globalization-api.md), the default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures changed on Windows.</span></span> <span data-ttu-id="a8613-107">В качестве значений <xref:System.Globalization.TextInfo.ListSeparator> были использованы значения десятичных разделителей, полученные из международных компонентов для Юникода (ICU).</span><span class="sxs-lookup"><span data-stu-id="a8613-107">Decimal separator values, obtained from International Components for Unicode (ICU), were used as the <xref:System.Globalization.TextInfo.ListSeparator> values.</span></span> <span data-ttu-id="a8613-108">В Linux и macOS значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> не изменились, то есть по-прежнему используются значения десятичного разделителя.</span><span class="sxs-lookup"><span data-stu-id="a8613-108">On Linux and macOS, there was no change in <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values; that is, they continued to use decimal separator values.</span></span>

<span data-ttu-id="a8613-109">Для всех операционных систем в .NET 5.0.1 и более поздних версий значения для <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> эквивалентны значениям, полученным из NLS.</span><span class="sxs-lookup"><span data-stu-id="a8613-109">For all operating systems in .NET 5.0.1 and later versions, the values for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> are equivalent to the values that would be obtained from NLS.</span></span> <span data-ttu-id="a8613-110">Для Windows это означает, что значения эквивалентны тем, что были в .NET Framework и .NET Core 1.0–3.1.</span><span class="sxs-lookup"><span data-stu-id="a8613-110">For Windows, this means the values are equivalent to what they were in .NET Framework and .NET Core 1.0 - 3.1.</span></span> <span data-ttu-id="a8613-111">Для Linux и macOS значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> теперь соответствуют значениям <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> для Windows.</span><span class="sxs-lookup"><span data-stu-id="a8613-111">For Linux and macOS, the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values now match the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for Windows.</span></span>

<span data-ttu-id="a8613-112">В следующей таблице приведены изменения для значений <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8613-112">The following table summarizes the changes for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

| | <span data-ttu-id="a8613-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8613-113">.NET Framework</span></span><br/><span data-ttu-id="a8613-114">.NET Core 1.0–3.1</span><span class="sxs-lookup"><span data-stu-id="a8613-114">.NET Core 1.0 - 3.1</span></span> | <span data-ttu-id="a8613-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a8613-115">.NET 5.0</span></span> | <span data-ttu-id="a8613-116">.NET 5.0.1</span><span class="sxs-lookup"><span data-stu-id="a8613-116">.NET 5.0.1</span></span> |
-|-|-|-
| <span data-ttu-id="a8613-117">**Windows**</span><span class="sxs-lookup"><span data-stu-id="a8613-117">**Windows**</span></span> | <span data-ttu-id="a8613-118">Получение из NLS</span><span class="sxs-lookup"><span data-stu-id="a8613-118">Obtain from NLS</span></span> | <span data-ttu-id="a8613-119">Десятичный разделитель из ICU.</span><span class="sxs-lookup"><span data-stu-id="a8613-119">Decimal separator from ICU.</span></span><br/><span data-ttu-id="a8613-120">Можно переключиться обратно на NLS.</span><span class="sxs-lookup"><span data-stu-id="a8613-120">Can switch back to NLS.</span></span> | <span data-ttu-id="a8613-121">Эквивалентно NLS</span><span class="sxs-lookup"><span data-stu-id="a8613-121">Equivalent to NLS</span></span> |
| <span data-ttu-id="a8613-122">**Linux и macOS**</span><span class="sxs-lookup"><span data-stu-id="a8613-122">**Linux and macOS**</span></span> | <span data-ttu-id="a8613-123">Десятичный разделитель из ICU</span><span class="sxs-lookup"><span data-stu-id="a8613-123">Decimal separator from ICU</span></span> | <span data-ttu-id="a8613-124">Десятичный разделитель из ICU</span><span class="sxs-lookup"><span data-stu-id="a8613-124">Decimal separator from ICU</span></span> | <span data-ttu-id="a8613-125">Эквивалентно NLS</span><span class="sxs-lookup"><span data-stu-id="a8613-125">Equivalent to NLS</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="a8613-126">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a8613-126">Version introduced</span></span>

<span data-ttu-id="a8613-127">5.0.1</span><span class="sxs-lookup"><span data-stu-id="a8613-127">5.0.1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a8613-128">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a8613-128">Reason for change</span></span>

<span data-ttu-id="a8613-129">Разработчики сообщили, что они используют свойство <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> при анализе файлов с разделителями-запятыми (CSV), а новые значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> нарушают этот синтаксический анализ.</span><span class="sxs-lookup"><span data-stu-id="a8613-129">Developers reported that they use the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> property when parsing comma-separated value (CSV) files, and the new <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values broke that parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a8613-130">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a8613-130">Recommended action</span></span>

<span data-ttu-id="a8613-131">Если код зависит от предыдущих значений десятичного разделителя, можно жестко закодировать требуемые значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8613-131">If your code relies on the previous decimal separator values, you can hardcode the desired <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a8613-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a8613-132">Affected APIs</span></span>

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
