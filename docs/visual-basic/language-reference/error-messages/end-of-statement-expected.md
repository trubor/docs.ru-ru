---
description: 'Дополнительные сведения о: BC30205: Ожидается окончание оператора'
title: Ожидается окончание оператора
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: a3f309a4674f6de34c0be8abfef31e293a10dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796552"
---
# <a name="bc30205-end-of-statement-expected"></a><span data-ttu-id="e1ffb-103">BC30205: Ожидается конец оператора</span><span class="sxs-lookup"><span data-stu-id="e1ffb-103">BC30205: End of statement expected</span></span>

<span data-ttu-id="e1ffb-104">Инструкция является синтаксически завершенной, но дополнительный программный элемент следует за элементом, который завершает инструкцию.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-104">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="e1ffb-105">В конце каждой инструкции требуется признак конца строки.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-105">A line terminator is required at the end of every statement.</span></span>

 <span data-ttu-id="e1ffb-106">Признак конца строки делит символы Visual Basic исходного файла на строки.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-106">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="e1ffb-107">Примерами признаков конца строки являются символ возврата каретки в Юникоде (&HD), символ перевода строки в Юникоде (&HA) и символ возврата каретки в Юникоде, за которым следует символ перевода строки в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-107">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="e1ffb-108">Дополнительные сведения о знаках конца строки см. в разделе [Спецификация языка Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="e1ffb-108">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>

 <span data-ttu-id="e1ffb-109">**Идентификатор ошибки:** BC30205</span><span class="sxs-lookup"><span data-stu-id="e1ffb-109">**Error ID:** BC30205</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e1ffb-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e1ffb-110">To correct this error</span></span>

1. <span data-ttu-id="e1ffb-111">Убедитесь, что две разные инструкции случайно были помещены в одну и ту же строку.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-111">Check to see if two different statements have inadvertently been put on the same line.</span></span>

2. <span data-ttu-id="e1ffb-112">Вставьте признак конца строки после элемента, который завершает инструкцию.</span><span class="sxs-lookup"><span data-stu-id="e1ffb-112">Insert a line terminator after the element that completes the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ffb-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e1ffb-113">See also</span></span>

- [<span data-ttu-id="e1ffb-114">Практическое руководство. Разбиение и объединение инструкций в коде</span><span class="sxs-lookup"><span data-stu-id="e1ffb-114">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="e1ffb-115">Операторы</span><span class="sxs-lookup"><span data-stu-id="e1ffb-115">Statements</span></span>](../../programming-guide/language-features/statements.md)
