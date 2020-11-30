---
title: 'Пример регулярных выражений: Поиск ссылок HREF'
description: Вы можете изучить пример регулярных выражений в .NET. В этом примере показан поиск в строке входных данных и вывод всех значений атрибута href, а также их позиций.
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
ms.openlocfilehash: aceccc019542bb1afe3082881626cfc32740a338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733650"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="31b93-104">Пример регулярных выражений: Поиск ссылок HREF</span><span class="sxs-lookup"><span data-stu-id="31b93-104">Regular Expression Example: Scanning for HREFs</span></span>

<span data-ttu-id="31b93-105">В следующем примере показаны поиск и вывод всех значений href="...", а также их позиций в строке.</span><span class="sxs-lookup"><span data-stu-id="31b93-105">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="the-regex-object"></a><span data-ttu-id="31b93-106">Объект Regex</span><span class="sxs-lookup"><span data-stu-id="31b93-106">The Regex Object</span></span>

 <span data-ttu-id="31b93-107">Поскольку метод `DumpHRefs` может быть вызван из пользовательского кода несколько раз, он использует метод `static` (`Shared` в Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31b93-107">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31b93-108">Это позволяет обработчику регулярных выражений кэшировать регулярное выражение и избежать дополнительной нагрузки, связанной с созданием объекта <xref:System.Text.RegularExpressions.Regex> при каждом вызове метода.</span><span class="sxs-lookup"><span data-stu-id="31b93-108">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="31b93-109">Затем объект <xref:System.Text.RegularExpressions.Match> выполняет итерацию по всем совпадениям в строке.</span><span class="sxs-lookup"><span data-stu-id="31b93-109">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="31b93-110">В следующем примере показан вызов метода `DumpHRefs`.</span><span class="sxs-lookup"><span data-stu-id="31b93-110">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="31b93-111">Возможные интерпретации шаблона регулярного выражения `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` показаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="31b93-111">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="31b93-112">Шаблон</span><span class="sxs-lookup"><span data-stu-id="31b93-112">Pattern</span></span>|<span data-ttu-id="31b93-113">Описание</span><span class="sxs-lookup"><span data-stu-id="31b93-113">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="31b93-114">Совпадение с литеральной строкой "href".</span><span class="sxs-lookup"><span data-stu-id="31b93-114">Match the literal string "href".</span></span> <span data-ttu-id="31b93-115">Сопоставление не учитывает регистр.</span><span class="sxs-lookup"><span data-stu-id="31b93-115">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="31b93-116">Соответствует нулю или нескольким символам пробела.</span><span class="sxs-lookup"><span data-stu-id="31b93-116">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="31b93-117">Соответствует знаку равенства.</span><span class="sxs-lookup"><span data-stu-id="31b93-117">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="31b93-118">Соответствует нулю или нескольким символам пробела.</span><span class="sxs-lookup"><span data-stu-id="31b93-118">Match zero or more white-space characters.</span></span>|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|<span data-ttu-id="31b93-119">Соответствует одному из следующих символов, не назначая результат группе записи.</span><span class="sxs-lookup"><span data-stu-id="31b93-119">Match one of the following without assigning the result to a captured group:</span></span><br /> <ul><li><p><span data-ttu-id="31b93-120">Кавычки или апостроф, за которыми следует ноль или несколько любых символов, кроме кавычек или апострофа, за которыми следуют кавычки или апостроф.</span><span class="sxs-lookup"><span data-stu-id="31b93-120">A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="31b93-121">В этот шаблон включена группа с именем `1`.</span><span class="sxs-lookup"><span data-stu-id="31b93-121">The group named `1` is included in this pattern.</span></span></p></li><li><p><span data-ttu-id="31b93-122">Один или более символов, которые не являются пробелами.</span><span class="sxs-lookup"><span data-stu-id="31b93-122">One or more non-white-space characters.</span></span> <span data-ttu-id="31b93-123">В этот шаблон включена группа с именем `1`.</span><span class="sxs-lookup"><span data-stu-id="31b93-123">The group named `1` is included in this pattern.</span></span></p></li></ul>|  
|`(?<1>[^"']*)`|<span data-ttu-id="31b93-124">Присвоить ноль или несколько любых символов, кроме кавычки или апострофа, группе записи `1`.</span><span class="sxs-lookup"><span data-stu-id="31b93-124">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`(?<1>\S+)`|<span data-ttu-id="31b93-125">Присвоить один или несколько символов, отличных от пробела, захваченной группе с именем `1`.</span><span class="sxs-lookup"><span data-stu-id="31b93-125">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="31b93-126">Класс результата поиска</span><span class="sxs-lookup"><span data-stu-id="31b93-126">Match Result Class</span></span>  

 <span data-ttu-id="31b93-127">Результаты поиска сохраняются в классе <xref:System.Text.RegularExpressions.Match>, который предоставляет доступ ко всем подстрокам, извлеченным в ходе поиска.</span><span class="sxs-lookup"><span data-stu-id="31b93-127">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="31b93-128">Также он запоминает искомую строку и использованное регулярное выражение, что позволяет вызвать метод <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> для продолжения поиска с того места, где закончился предыдущий.</span><span class="sxs-lookup"><span data-stu-id="31b93-128">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="31b93-129">Явно именованные шаблоны</span><span class="sxs-lookup"><span data-stu-id="31b93-129">Explicitly Named Captures</span></span>  

 <span data-ttu-id="31b93-130">В обычных регулярных выражениях круглые скобки, обозначающие отдельные шаблоны, автоматически последовательно нумеруются.</span><span class="sxs-lookup"><span data-stu-id="31b93-130">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="31b93-131">В связи с этим возникают две проблемы.</span><span class="sxs-lookup"><span data-stu-id="31b93-131">This leads to two problems.</span></span> <span data-ttu-id="31b93-132">Во-первых, если регулярное выражение изменяется из-за вставки или удаления пары круглых скобок, все части кода, которые ссылаются на нумерованные шаблоны, необходимо переписать, чтобы отразить новую нумерацию.</span><span class="sxs-lookup"><span data-stu-id="31b93-132">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="31b93-133">Во-вторых, вследствие того, что различные пары круглых скобок часто используются для определения двух альтернативных выражений для поиска, трудно определить, какое из двух выражений в действительности вернуло результат.</span><span class="sxs-lookup"><span data-stu-id="31b93-133">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="31b93-134">Для решения этих проблем класс <xref:System.Text.RegularExpressions.Regex> поддерживает синтаксис `(?<name>…)`, с помощью которого найденное совпадение можно сохранить в указанной ячейке (которой можно присвоить строковое имя или целочисленное обозначение; числа при этом работают быстрее).</span><span class="sxs-lookup"><span data-stu-id="31b93-134">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="31b93-135">Таким образом, если совпадение будет найдено повторно, оно попадет в ту же ячейку.</span><span class="sxs-lookup"><span data-stu-id="31b93-135">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="31b93-136">В случае конфликта успешным является то совпадение, которое было помещено в ячейку последним.</span><span class="sxs-lookup"><span data-stu-id="31b93-136">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="31b93-137">(Однако доступен и полный список совпадений для одной ячейки.</span><span class="sxs-lookup"><span data-stu-id="31b93-137">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="31b93-138">Подробнее см. описание коллекции <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="31b93-138">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b93-139">См. также</span><span class="sxs-lookup"><span data-stu-id="31b93-139">See also</span></span>

- [<span data-ttu-id="31b93-140">Регулярные выражения .NET</span><span class="sxs-lookup"><span data-stu-id="31b93-140">.NET Regular Expressions</span></span>](regular-expressions.md)
