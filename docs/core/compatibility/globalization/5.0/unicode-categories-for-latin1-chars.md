---
title: Критическое изменение. Для некоторых символов латиницы-1 изменилась категория Юникода
description: Сведения о критическом изменении глобализации в .NET 5, где методы char теперь возвращают правильную категорию Юникода для символов в диапазоне латиницы-1.
ms.date: 04/07/2020
ms.openlocfilehash: 03355c488d2bdae78f989e647c9b5b7913d73649
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256677"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="45a61-103">Для некоторых символов латиницы-1 изменилась категория Юникода</span><span class="sxs-lookup"><span data-stu-id="45a61-103">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="45a61-104">Методы <xref:System.Char> теперь возвращают правильную категорию Юникода для символов в диапазоне латиницы-1.</span><span class="sxs-lookup"><span data-stu-id="45a61-104"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="45a61-105">Категория соответствует стандарту Юникода.</span><span class="sxs-lookup"><span data-stu-id="45a61-105">The category matches that of the Unicode standard.</span></span>

## <a name="change-description"></a><span data-ttu-id="45a61-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="45a61-106">Change description</span></span>

<span data-ttu-id="45a61-107">В предыдущих версиях .NET методы <xref:System.Char> использовали фиксированный список категорий Юникода для символов в диапазоне латиницы-1.</span><span class="sxs-lookup"><span data-stu-id="45a61-107">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="45a61-108">Однако в стандарте Юникода категории некоторых из этих символов были изменены, так как эти API были реализованы, что создает расхождение.</span><span class="sxs-lookup"><span data-stu-id="45a61-108">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="45a61-109">Кроме того, существует несоответствие между API <xref:System.Char> и <xref:System.Globalization.CharUnicodeInfo>, которые следуют стандарту Юникода.</span><span class="sxs-lookup"><span data-stu-id="45a61-109">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="45a61-110">В .NET 5 и более поздних версиях методы <xref:System.Char> используют и возвращают категорию Юникода, которая соответствует стандарту Юникода для всех символов.</span><span class="sxs-lookup"><span data-stu-id="45a61-110">In .NET 5 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="45a61-111">В следующей таблице показаны символы, чьи категории Юникода изменились в .NET 5.0:</span><span class="sxs-lookup"><span data-stu-id="45a61-111">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="45a61-112">Символ</span><span class="sxs-lookup"><span data-stu-id="45a61-112">Character</span></span>    | <span data-ttu-id="45a61-113">Категория Юникода</span><span class="sxs-lookup"><span data-stu-id="45a61-113">Unicode category</span></span><br><span data-ttu-id="45a61-114">в предыдущих версиях .NET</span><span class="sxs-lookup"><span data-stu-id="45a61-114">in previous .NET versions</span></span> | <span data-ttu-id="45a61-115">Категория Юникода</span><span class="sxs-lookup"><span data-stu-id="45a61-115">Unicode category</span></span><br><span data-ttu-id="45a61-116">в .NET 5 и более поздних версиях</span><span class="sxs-lookup"><span data-stu-id="45a61-116">in .NET 5 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="45a61-117">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="45a61-117">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="45a61-118">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="45a61-118">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="45a61-119">SHY (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="45a61-119">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="45a61-120">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="45a61-120">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="45a61-121">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="45a61-121">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a><span data-ttu-id="45a61-122">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="45a61-122">Version introduced</span></span>

<span data-ttu-id="45a61-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="45a61-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="45a61-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="45a61-124">Recommended action</span></span>

<span data-ttu-id="45a61-125">Если у вас есть код, который получает категорию символов Юникода с помощью класса <xref:System.Char> и предполагает, что категория никогда не изменится, может потребоваться обновить его.</span><span class="sxs-lookup"><span data-stu-id="45a61-125">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="45a61-126">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="45a61-126">Reason for change</span></span>

<span data-ttu-id="45a61-127">Это изменение было сделано таким образом, чтобы категории, возвращаемые типом <xref:System.Char>, соответствовали стандарту Unicode и типу <xref:System.Globalization.CharUnicodeInfo>.</span><span class="sxs-lookup"><span data-stu-id="45a61-127">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="45a61-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="45a61-128">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="45a61-129">Кроме того, это изменение затрагивает любой класс, зависящий от <xref:System.Char> для получения категории символов Юникода, например <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="45a61-129">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
