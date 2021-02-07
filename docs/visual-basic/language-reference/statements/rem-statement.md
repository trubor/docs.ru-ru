---
description: 'Дополнительные сведения о инструкции: REM (Visual Basic)'
title: Оператор REM
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: c82621db98dc66060ae098ee6537ee58b24046a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741319"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="71db7-103">Оператор REM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71db7-103">REM Statement (Visual Basic)</span></span>

<span data-ttu-id="71db7-104">Используется для включения пояснительных примечаний в исходный код программы.</span><span class="sxs-lookup"><span data-stu-id="71db7-104">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71db7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71db7-105">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="71db7-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="71db7-106">Parts</span></span>  

 `comment`  
 <span data-ttu-id="71db7-107">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="71db7-107">Optional.</span></span> <span data-ttu-id="71db7-108">Текст любого комментария, который требуется включить.</span><span class="sxs-lookup"><span data-stu-id="71db7-108">The text of any comment you want to include.</span></span> <span data-ttu-id="71db7-109">Между `REM` ключевым словом и должен быть пробел `comment` .</span><span class="sxs-lookup"><span data-stu-id="71db7-109">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71db7-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="71db7-110">Remarks</span></span>  

 <span data-ttu-id="71db7-111">Оператор можно разместить `REM` только в строке или вставить в строку, следующую за другой инструкцией.</span><span class="sxs-lookup"><span data-stu-id="71db7-111">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="71db7-112">`REM`Оператор должен быть последним оператором в строке.</span><span class="sxs-lookup"><span data-stu-id="71db7-112">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="71db7-113">Если он соответствует другому оператору, он `REM` должен быть отделен от этого оператора пробелом.</span><span class="sxs-lookup"><span data-stu-id="71db7-113">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="71db7-114">Можно использовать одиночную кавычку ( `'` ) вместо `REM` .</span><span class="sxs-lookup"><span data-stu-id="71db7-114">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="71db7-115">Это верно, если ваш комментарий следует другому оператору в той же строке или расподержаться только в строке.</span><span class="sxs-lookup"><span data-stu-id="71db7-115">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71db7-116">Нельзя продолжить выполнение `REM` инструкции с помощью последовательности продолжения строки ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="71db7-116">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="71db7-117">После начала комментария компилятор не проверяет символы на предмет особого значения.</span><span class="sxs-lookup"><span data-stu-id="71db7-117">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="71db7-118">Для многострочного комментария используйте другую `REM` инструкцию или символ комментария ( `'` ) в каждой строке.</span><span class="sxs-lookup"><span data-stu-id="71db7-118">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71db7-119">Пример</span><span class="sxs-lookup"><span data-stu-id="71db7-119">Example</span></span>  

 <span data-ttu-id="71db7-120">В следующем примере показана `REM` инструкция, которая используется для включения пояснительных примечаний в программу.</span><span class="sxs-lookup"><span data-stu-id="71db7-120">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="71db7-121">Он также показывает альтернативу использованию символа одинарной кавычки ( `'` ) вместо `REM` .</span><span class="sxs-lookup"><span data-stu-id="71db7-121">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="71db7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="71db7-122">See also</span></span>

- [<span data-ttu-id="71db7-123">Комментарии в коде</span><span class="sxs-lookup"><span data-stu-id="71db7-123">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="71db7-124">Практическое руководство. Разбиение и объединение инструкций в коде</span><span class="sxs-lookup"><span data-stu-id="71db7-124">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
