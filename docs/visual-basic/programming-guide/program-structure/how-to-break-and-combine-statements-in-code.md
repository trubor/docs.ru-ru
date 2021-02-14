---
description: Дополнительные сведения о том, как разрывать и объединять операторы в коде (Visual Basic)
title: Практическое руководство. Разбиение и объединение инструкций в коде
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 33a8b87171c4ee14e73ada564cff406637e96783
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475998"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="a4f5c-103">Практическое руководство. Разбиение и объединение инструкций в коде (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-103">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="a4f5c-104">При написании кода иногда можно создавать длинные операторы, требующие горизонтальной прокрутки в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-104">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="a4f5c-105">Хотя это не влияет на способ выполнения кода, он затрудняет чтение кода в том виде, в котором он отображается на мониторе.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-105">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="a4f5c-106">В таких случаях следует рассмотреть возможность разбиения одного длинного оператора на несколько строк.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-106">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="a4f5c-107">Разбиение одного оператора на несколько строк</span><span class="sxs-lookup"><span data-stu-id="a4f5c-107">To break a single statement into multiple lines</span></span>

<span data-ttu-id="a4f5c-108">Используйте символ продолжения строки, который является подчеркиванием ( `_` ), в точке, в которой должна прерываться линия.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-108">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="a4f5c-109">Символу подчеркивания должен предшествовать пробел и сразу за ним следует символ конца строки (возврат каретки) или (начиная с версии 16,0) комментарий, за которым следует символ возврата каретки.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-109">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a4f5c-110">В некоторых случаях, если опустить символ продолжения строки, компилятор Visual Basic неявно продолжит инструкцию на следующей строке кода.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-110">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="a4f5c-111">Список элементов синтаксиса, для которых можно опустить символ продолжения строки, см. в разделе «неявные продолжения строки» в [инструкциях](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f5c-111">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../language-features/statements.md).</span></span>

  <span data-ttu-id="a4f5c-112">В следующем примере инструкция разбивается на четыре строки с символами продолжения строки, завершающими все, кроме последней строки.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-112">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="a4f5c-113">Использование этой последовательности упрощает чтение кода в сети и при печати.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="a4f5c-114">Символ продолжения строки должен быть последним символом в строке.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="a4f5c-115">Вы не можете подписаться на него другим в той же строке.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-115">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="a4f5c-116">Существуют некоторые ограничения, в которых можно использовать символ продолжения строки. Например, нельзя использовать его в середине имени аргумента.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="a4f5c-117">Можно прервать список аргументов с помощью символа продолжения строки, но отдельные имена аргументов должны оставаться неизменными.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="a4f5c-118">Комментарий нельзя продолжить с помощью символа продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="a4f5c-119">Компилятор не проверяет символы в комментарии на наличие специального значения.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="a4f5c-120">Для многострочного комментария повторите символ комментария ( `'` ) в каждой строке.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="a4f5c-121">Хотя размещение каждой инструкции в отдельной строке является рекомендуемым методом, Visual Basic также позволяет размещать несколько инструкций в одной строке.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-121">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="a4f5c-122">Размещение нескольких инструкций на одной строке</span><span class="sxs-lookup"><span data-stu-id="a4f5c-122">To place multiple statements on the same line</span></span>

<span data-ttu-id="a4f5c-123">Разделяйте операторы двоеточием ( `:` ), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-123">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="a4f5c-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4f5c-124">See also</span></span>

- [<span data-ttu-id="a4f5c-125">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="a4f5c-125">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="a4f5c-126">Операторы</span><span class="sxs-lookup"><span data-stu-id="a4f5c-126">Statements</span></span>](../language-features/statements.md)
