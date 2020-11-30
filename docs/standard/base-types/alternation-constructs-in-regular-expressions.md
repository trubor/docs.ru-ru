---
title: Конструкции изменения в регулярных выражениях .NET
description: Узнайте, как использовать конструкции изменения для условного сопоставления в регулярных выражениях.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 0a1b46443d5cd9f8a19f4cfb9f9b07a5e33e719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714696"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="a2496-103">Конструкции изменения в регулярных выражениях</span><span class="sxs-lookup"><span data-stu-id="a2496-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="a2496-104">Конструкции изменения модифицируют регулярное выражение, включая сопоставление по принципу «либо/или» или условное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="a2496-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="a2496-105">Платформа .NET поддерживает три указанные далее конструкции изменения.</span><span class="sxs-lookup"><span data-stu-id="a2496-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="a2496-106">Сопоставление шаблонов с помощью |</span><span class="sxs-lookup"><span data-stu-id="a2496-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="a2496-107">Условное сопоставление (?(expression) yes|no)</span><span class="sxs-lookup"><span data-stu-id="a2496-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="a2496-108">Условное сопоставление на основе действительной захватываемой группы</span><span class="sxs-lookup"><span data-stu-id="a2496-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>

## <a name="pattern-matching-with-124"></a><span data-ttu-id="a2496-109">Сопоставление шаблонов с помощью |</span><span class="sxs-lookup"><span data-stu-id="a2496-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="a2496-110">Вертикальную черту (`|`) можно использовать для сопоставления с любым набором шаблонов, в котором шаблоны разделяются с помощью символа `|`.</span><span class="sxs-lookup"><span data-stu-id="a2496-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="a2496-111">Как и класс положительных символов, символ `|` можно использовать для сопоставления с любым количеством отдельных символов.</span><span class="sxs-lookup"><span data-stu-id="a2496-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="a2496-112">В следующем примере используется класс положительных символов и сопоставление с шаблоном либо/или с символом `|` для обнаружения в строке всех вхождений слов gray или grey.</span><span class="sxs-lookup"><span data-stu-id="a2496-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="a2496-113">В этом случае символ `|` создает регулярное выражение, которое является более подробным.</span><span class="sxs-lookup"><span data-stu-id="a2496-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="a2496-114">Возможные интерпретации регулярного выражения, использующего символ `|`, `\bgr(a|e)y\b`, показаны в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="a2496-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a2496-115">Шаблон</span><span class="sxs-lookup"><span data-stu-id="a2496-115">Pattern</span></span>|<span data-ttu-id="a2496-116">Описание</span><span class="sxs-lookup"><span data-stu-id="a2496-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a2496-117">Начало на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="a2496-118">Соответствует символам gr.</span><span class="sxs-lookup"><span data-stu-id="a2496-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="a2496-119">Соответствует букве "a" или "e".</span><span class="sxs-lookup"><span data-stu-id="a2496-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="a2496-120">Соответствует символу у на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="a2496-121">С помощью символа `|` также можно выполнить сопоставление "или/либо" с несколькими символами или частями выражения, которые могут включать любую комбинацию символьных литералов и элементов языка регулярных выражений.</span><span class="sxs-lookup"><span data-stu-id="a2496-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="a2496-122">(Класс символов не предоставляет эту функцию). В следующем примере символ `|` используется для извлечения номера социального страхования США (SSN), который состоит из 9 цифр в формате *ddd*-*dd*-*dddd*, или номера идентификации работодателя США (EIN), который состоит из 9 цифр в формате *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="a2496-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="a2496-123">Возможные интерпретации регулярного выражения `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` показаны в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="a2496-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="a2496-124">Шаблон</span><span class="sxs-lookup"><span data-stu-id="a2496-124">Pattern</span></span>|<span data-ttu-id="a2496-125">Описание</span><span class="sxs-lookup"><span data-stu-id="a2496-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a2496-126">Начало на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="a2496-127">Сопоставьте любые из следующих значений: два десятичных знака, за которыми следует дефис и еще семь десятичных знаков; или последовательность из трех десятичных знаков, дефиса, двух десятичных знаков, еще одного дефиса и четырех десятичных знаков.</span><span class="sxs-lookup"><span data-stu-id="a2496-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a2496-128">Совпадение должно заканчиваться на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>

## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="a2496-129">Условное сопоставление с выражением</span><span class="sxs-lookup"><span data-stu-id="a2496-129">Conditional matching with an expression</span></span>

<span data-ttu-id="a2496-130">Этот элемент языка пытается сопоставить один из двух шаблонов в зависимости от того, может ли он сопоставить первоначальный шаблон.</span><span class="sxs-lookup"><span data-stu-id="a2496-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="a2496-131">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a2496-131">Its syntax is:</span></span>  

<span data-ttu-id="a2496-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="a2496-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a2496-133">где *expression* — первый сопоставляемый шаблон, *yes* — шаблон, который необходимо сопоставить, если сопоставлен шаблон *expression* , а *no* — это дополнительный шаблон, который необходимо сопоставить, если *expression* не сопоставлен.</span><span class="sxs-lookup"><span data-stu-id="a2496-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="a2496-134">Обработчик регулярных выражений рассматривает *expression* как утверждение нулевой ширины, то есть обработчик регулярных выражений не перемещается в потоке входных значений после оценки *expression*.</span><span class="sxs-lookup"><span data-stu-id="a2496-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="a2496-135">Следовательно, эта конструкция эквивалентна следующему.</span><span class="sxs-lookup"><span data-stu-id="a2496-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="a2496-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="a2496-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a2496-137">Где `(?=`*expression*`)` — это проверочное утверждение нулевой ширины.</span><span class="sxs-lookup"><span data-stu-id="a2496-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="a2496-138">(Дополнительные сведения см. в разделе [Конструкции группировки](grouping-constructs-in-regular-expressions.md).) Поскольку обработчик регулярных выражений интерпретирует *expression* как привязку (утверждение нулевой ширины), *expression* должно представлять собой утверждение нулевой ширины (дополнительные сведения см. в статье [Привязки](anchors-in-regular-expressions.md)) или часть выражения, которая также содержится в *yes*.</span><span class="sxs-lookup"><span data-stu-id="a2496-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="a2496-139">В противном случае шаблон *yes* сопоставить невозможно.</span><span class="sxs-lookup"><span data-stu-id="a2496-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2496-140">Если *expression* является именованной или нумерованной захватываемой группой, конструкция изменения интерпретируется как тест захвата. Дополнительные сведения см. далее в подразделе [Условное сопоставление на основе действительной захватываемой группы](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="a2496-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="a2496-141">Другими словами, обработчик регулярных выражений не пытается сопоставить захваченную часть строки, а вместо этого выполняет проверку на наличие или отсутствие группы.</span><span class="sxs-lookup"><span data-stu-id="a2496-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="a2496-142">Следующий пример является вариантом примера, который описан в разделе [Сопоставление шаблонов «либо/или» с помощью |](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="a2496-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a2496-143">Условное сопоставление используется, чтобы определить, являются ли первые три символа после границы слова двумя цифрами и дефисом.</span><span class="sxs-lookup"><span data-stu-id="a2496-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="a2496-144">Если да, предпринимается попытка сопоставить Идентификационный номер работодателя США (EIN).</span><span class="sxs-lookup"><span data-stu-id="a2496-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a2496-145">Если нет, предпринимается попытка сопоставить Номер социального страхования США (SSN).</span><span class="sxs-lookup"><span data-stu-id="a2496-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="a2496-146">Возможные интерпретации шаблона регулярного выражения `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` показаны в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="a2496-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a2496-147">Шаблон</span><span class="sxs-lookup"><span data-stu-id="a2496-147">Pattern</span></span>|<span data-ttu-id="a2496-148">Описание</span><span class="sxs-lookup"><span data-stu-id="a2496-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a2496-149">Начало на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="a2496-150">Определите, состоят ли следующие три символа из двух цифр, за которыми следуют дефис.</span><span class="sxs-lookup"><span data-stu-id="a2496-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="a2496-151">Если предыдущий шаблон сопоставлен, сопоставьте две цифры с дефисом, за которыми следуют еще семь цифр.</span><span class="sxs-lookup"><span data-stu-id="a2496-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="a2496-152">Если предыдущий шаблон не сопоставлен, сопоставьте три цифры, дефис, две цифры, еще один дефис и еще четыре цифры.</span><span class="sxs-lookup"><span data-stu-id="a2496-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a2496-153">Соответствует границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>

## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="a2496-154">Условное сопоставление на основе действительной захватываемой группы.</span><span class="sxs-lookup"><span data-stu-id="a2496-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="a2496-155">Этот элемент языка пытается сопоставить один из двух шаблонов, в зависимости от того, соответствует ли он указанной группе записи.</span><span class="sxs-lookup"><span data-stu-id="a2496-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="a2496-156">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a2496-156">Its syntax is:</span></span>

<span data-ttu-id="a2496-157">`(?(` *name* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="a2496-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a2496-158">or</span><span class="sxs-lookup"><span data-stu-id="a2496-158">or</span></span>

<span data-ttu-id="a2496-159">`(?(` *number* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="a2496-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a2496-160">где *name* — имя, а *number* — номер захватываемой группы, *yes* — сопоставляемое выражение, если для *name* или *number* имеется соответствие, а *no* — это дополнительное выражение для сопоставления при отсутствии соответствия.</span><span class="sxs-lookup"><span data-stu-id="a2496-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="a2496-161">Если *name* не соответствует имени захватываемой группы, которая используется в шаблоне регулярного выражения, конструкция изменения интерпретируется как проверка выражения, как было описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="a2496-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="a2496-162">Как правило, это означает, что *expression* имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a2496-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="a2496-163">Если *number* не соответствует нумерованной группе захвата, используемой в шаблоне регулярного выражения, обработчик регулярных выражений создает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="a2496-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="a2496-164">Следующий пример является вариантом примера, который описан в разделе [Сопоставление шаблонов «либо/или» с помощью |](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="a2496-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a2496-165">В нем используется захватываемая группа с именем `n2` , которая состоит из двух цифр и дефиса.</span><span class="sxs-lookup"><span data-stu-id="a2496-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="a2496-166">Конструкция изменения проверяет, сопоставлена ли эта группа захвата в строке ввода.</span><span class="sxs-lookup"><span data-stu-id="a2496-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="a2496-167">Если да, конструкция изменения пытается сопоставить последние семь цифр девятизначного Идентификационный номер работодателя США (EIN).</span><span class="sxs-lookup"><span data-stu-id="a2496-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a2496-168">В противном случае она пытается сопоставить девятизначный Номер социального страхования США (SSN).</span><span class="sxs-lookup"><span data-stu-id="a2496-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="a2496-169">Возможные интерпретации шаблона регулярного выражения `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` показаны в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="a2496-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a2496-170">Шаблон</span><span class="sxs-lookup"><span data-stu-id="a2496-170">Pattern</span></span>|<span data-ttu-id="a2496-171">Описание</span><span class="sxs-lookup"><span data-stu-id="a2496-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a2496-172">Начало на границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="a2496-173">Сопоставьте нулевое или единичное вхождение двух цифр с дефисом.</span><span class="sxs-lookup"><span data-stu-id="a2496-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="a2496-174">Установка для группы имени `n2`.</span><span class="sxs-lookup"><span data-stu-id="a2496-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="a2496-175">Проверка наличия сопоставления `n2` во входной строке.</span><span class="sxs-lookup"><span data-stu-id="a2496-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="a2496-176">Если есть сопоставление `n2` , сопоставляются семь десятичных цифр.</span><span class="sxs-lookup"><span data-stu-id="a2496-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="a2496-177">Если сопоставления нет `n2` , сопоставляются три десятичных цифры, дефис, две десятичных цифры, еще один дефис и четыре десятичных цифры.</span><span class="sxs-lookup"><span data-stu-id="a2496-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a2496-178">Соответствует границе слова.</span><span class="sxs-lookup"><span data-stu-id="a2496-178">Match a word boundary.</span></span>|  

<span data-ttu-id="a2496-179">В следующем примере показана вариация этого примера, в котором вместо именованной группы используется нумерованная.</span><span class="sxs-lookup"><span data-stu-id="a2496-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="a2496-180">Шаблон регулярного выражения выглядит следующим образом: `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`</span><span class="sxs-lookup"><span data-stu-id="a2496-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a2496-181">См. также</span><span class="sxs-lookup"><span data-stu-id="a2496-181">See also</span></span>

- [<span data-ttu-id="a2496-182">Элементы языка регулярных выражений — краткий справочник</span><span class="sxs-lookup"><span data-stu-id="a2496-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
