---
description: Дополнительные сведения см. в статье как сопоставить строку с шаблоном (Visual Basic)
title: Практическое руководство. Сравнение строки на соответствие с шаблоном
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: f3e3426f85d420726571f03c88546d181cdccf97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461948"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="f88fa-103">Практическое руководство. Сравнение строки на соответствие с шаблоном (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f88fa-103">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="f88fa-104">Если нужно выяснить, удовлетворяет ли выражение [строкового типа данных](../../../language-reference/data-types/string-data-type.md) шаблону, можно использовать [оператор Like](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f88fa-104">If you want to find out if an expression of the [String Data Type](../../../language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="f88fa-105">`Like` принимает два операнда.</span><span class="sxs-lookup"><span data-stu-id="f88fa-105">`Like` takes two operands.</span></span> <span data-ttu-id="f88fa-106">Левый операнд является строковым выражением, а правый — строкой, содержащей шаблон, используемый для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="f88fa-106">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="f88fa-107">`Like` Возвращает `Boolean` значение, указывающее, удовлетворяет ли строковое выражение шаблону.</span><span class="sxs-lookup"><span data-stu-id="f88fa-107">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="f88fa-108">Каждый символ в строковом выражении можно сопоставить с конкретным символом, символом-шаблоном, списком символов или диапазоном символов.</span><span class="sxs-lookup"><span data-stu-id="f88fa-108">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="f88fa-109">Положения спецификаций в строке шаблона соответствуют позициям символов, которые должны быть сопоставлены в строковом выражении.</span><span class="sxs-lookup"><span data-stu-id="f88fa-109">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="f88fa-110">Сопоставление символа в строковом выражении с конкретным символом</span><span class="sxs-lookup"><span data-stu-id="f88fa-110">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="f88fa-111">Помещает конкретный символ непосредственно в строку шаблона.</span><span class="sxs-lookup"><span data-stu-id="f88fa-111">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="f88fa-112">Некоторые специальные символы должны быть заключены в квадратные скобки ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="f88fa-112">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="f88fa-113">Дополнительные сведения см. [в разделе Оператор Like](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f88fa-113">For more information, see [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="f88fa-114">В следующем примере проверяется `myString` , состоит ли только из одного символа `H` .</span><span class="sxs-lookup"><span data-stu-id="f88fa-114">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="f88fa-115">Сопоставление символа в строковом выражении с подстановочным знаком</span><span class="sxs-lookup"><span data-stu-id="f88fa-115">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="f88fa-116">Добавьте вопросительный знак ( `?` ) в строку шаблона.</span><span class="sxs-lookup"><span data-stu-id="f88fa-116">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="f88fa-117">Любой допустимый символ в этой позиции делает успешное совпадение.</span><span class="sxs-lookup"><span data-stu-id="f88fa-117">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="f88fa-118">В следующем примере проверяется, состоит ли из `myString` одного символа, `W` за которым следует ровно два символа любого значения.</span><span class="sxs-lookup"><span data-stu-id="f88fa-118">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="f88fa-119">Сопоставление символа в строковом выражении со списком символов</span><span class="sxs-lookup"><span data-stu-id="f88fa-119">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="f88fa-120">Вставьте квадратные скобки ( `[ ]` ) в строку шаблона, а внутри квадратных скобок вставьте список символов.</span><span class="sxs-lookup"><span data-stu-id="f88fa-120">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="f88fa-121">Не разделяйте символы запятыми или любым другим разделителем.</span><span class="sxs-lookup"><span data-stu-id="f88fa-121">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="f88fa-122">Любой отдельный символ в списке успешно выполняет сопоставление.</span><span class="sxs-lookup"><span data-stu-id="f88fa-122">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="f88fa-123">В следующем примере проверяется, `myString` состоит ли из любого допустимого символа, за которым следует только один из символов `A` , `C` или `E` .</span><span class="sxs-lookup"><span data-stu-id="f88fa-123">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="f88fa-124">Обратите внимание, что в этом совпадении учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="f88fa-124">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="f88fa-125">Сопоставление символа в строковом выражении с диапазоном символов</span><span class="sxs-lookup"><span data-stu-id="f88fa-125">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="f88fa-126">Вставьте квадратные скобки ( `[ ]` ) в строку шаблона, а внутри квадратных скобок — наименьшие и максимальные символы в диапазоне, разделенные дефисом ( `–` ).</span><span class="sxs-lookup"><span data-stu-id="f88fa-126">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="f88fa-127">Любой отдельный символ в диапазоне выполняет успешное совпадение.</span><span class="sxs-lookup"><span data-stu-id="f88fa-127">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="f88fa-128">В следующем примере проверяется `myString` , состоит ли из символов `num` , за которыми следует только один из символов:,,,, `i` `j` `k` `l` `m` или `n` .</span><span class="sxs-lookup"><span data-stu-id="f88fa-128">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="f88fa-129">Обратите внимание, что в этом совпадении учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="f88fa-129">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="f88fa-130">Совпадающие пустые строки</span><span class="sxs-lookup"><span data-stu-id="f88fa-130">Matching Empty Strings</span></span>

<span data-ttu-id="f88fa-131">`Like` обрабатывает последовательность `[]` как строку нулевой длины ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="f88fa-131">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="f88fa-132">Можно использовать `[]` для проверки, является ли все строковое выражение пустым, но нельзя использовать его для проверки того, что определенная позицией в строковом выражении пуста.</span><span class="sxs-lookup"><span data-stu-id="f88fa-132">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="f88fa-133">Если пустое расположение является одним из параметров, которые необходимо проверить, можно использовать `Like` более одного раза.</span><span class="sxs-lookup"><span data-stu-id="f88fa-133">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="f88fa-134">Сопоставление символа в строковом выражении со списком символов или без символа</span><span class="sxs-lookup"><span data-stu-id="f88fa-134">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="f88fa-135">Дважды вызовите `Like` оператор для того же строкового выражения и соедините два вызова с помощью [оператора OR](../../../language-reference/operators/or-operator.md) или [оператора OrElse](../../../language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f88fa-135">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../language-reference/operators/or-operator.md) or the [OrElse Operator](../../../language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="f88fa-136">В строке шаблона для первого `Like` предложения включите список символов, заключенный в квадратные скобки ( `[ ]` ).</span><span class="sxs-lookup"><span data-stu-id="f88fa-136">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="f88fa-137">В строке шаблона для второго `Like` предложения не помещайте ни один символ в позиции.</span><span class="sxs-lookup"><span data-stu-id="f88fa-137">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="f88fa-138">В следующем примере проверяется номер телефона, состоящий из семи цифр `phoneNum` , для ровно трех цифр, за которыми следует пробел, дефис ( `–` ), точка ( `.` ) или вообще нет символа, за которыми следует только четыре цифры.</span><span class="sxs-lookup"><span data-stu-id="f88fa-138">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="f88fa-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f88fa-139">See also</span></span>

- [<span data-ttu-id="f88fa-140">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="f88fa-140">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="f88fa-141">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="f88fa-141">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="f88fa-142">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="f88fa-142">Like Operator</span></span>](../../../language-reference/operators/like-operator.md)
- [<span data-ttu-id="f88fa-143">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="f88fa-143">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
