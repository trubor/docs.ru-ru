---
description: 'Дополнительные сведения: типы ошибок (Visual Basic)'
title: Типы ошибок
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: cc4fce5e0ce77a4e402ba832fd6f4e36e6feed07
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423775"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="22f11-103">Типы ошибок (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22f11-103">Error Types (Visual Basic)</span></span>

<span data-ttu-id="22f11-104">В Visual Basic ошибки относятся к одной из трех категорий: синтаксические ошибки, ошибки времени выполнения и логические ошибки.</span><span class="sxs-lookup"><span data-stu-id="22f11-104">In Visual Basic, errors fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>

## <a name="syntax-errors"></a><span data-ttu-id="22f11-105">Синтаксические ошибки</span><span class="sxs-lookup"><span data-stu-id="22f11-105">Syntax Errors</span></span>

 <span data-ttu-id="22f11-106">*Синтаксические ошибки* — это те, которые появляются при написании кода.</span><span class="sxs-lookup"><span data-stu-id="22f11-106">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="22f11-107">Если вы используете Visual Studio, Visual Basic проверяет код по мере его ввода в окне **редактора кода** и предупреждает об ошибке, например при неправильном написании слова или использовании элемента языка.</span><span class="sxs-lookup"><span data-stu-id="22f11-107">If you're using Visual Studio, Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="22f11-108">При компиляции из командной строки Visual Basic отображает ошибку компилятора со сведениями о синтаксических ошибках.</span><span class="sxs-lookup"><span data-stu-id="22f11-108">If you compile from the command line, Visual Basic displays a compiler error with information about the syntax error.</span></span> <span data-ttu-id="22f11-109">Синтаксические ошибки — наиболее распространенный тип ошибок.</span><span class="sxs-lookup"><span data-stu-id="22f11-109">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="22f11-110">Вы можете легко исправить их в среде программирования, как только они появятся.</span><span class="sxs-lookup"><span data-stu-id="22f11-110">You can fix them easily in the coding environment as soon as they occur.</span></span>

> [!NOTE]
> <span data-ttu-id="22f11-111">`Option Explicit`Оператор является одним из способов предотвращения синтаксических ошибок.</span><span class="sxs-lookup"><span data-stu-id="22f11-111">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="22f11-112">Он заставляет заранее объявить все переменные, которые будут использоваться в приложении.</span><span class="sxs-lookup"><span data-stu-id="22f11-112">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="22f11-113">Таким образом, если эти переменные используются в коде, любые типографские ошибки сразу же перехватываются и могут быть исправлены.</span><span class="sxs-lookup"><span data-stu-id="22f11-113">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="22f11-114">Ошибки Run-Time</span><span class="sxs-lookup"><span data-stu-id="22f11-114">Run-Time Errors</span></span>

 <span data-ttu-id="22f11-115">*Ошибки времени выполнения* — это те, которые отображаются только после компиляции и выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="22f11-115">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="22f11-116">В их число входит код, который может показаться правильным в том, что он не содержит синтаксических ошибок, но не будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="22f11-116">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="22f11-117">Например, вы можете правильно написать строку кода, чтобы открыть файл.</span><span class="sxs-lookup"><span data-stu-id="22f11-117">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="22f11-118">Но если файл не существует, приложение не сможет открыть файл и выдаст исключение.</span><span class="sxs-lookup"><span data-stu-id="22f11-118">But if the file does not exist, the application cannot open the file, and it throws an exception.</span></span> <span data-ttu-id="22f11-119">Большинство ошибок во время выполнения можно устранить путем перезаписи неисправного кода или с помощью [обработки исключений](../../language-reference/statements/try-catch-finally-statement.md), а затем перекомпиляции и повторного запуска.</span><span class="sxs-lookup"><span data-stu-id="22f11-119">You can fix most run-time errors by rewriting the faulty code or by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md), and then recompiling and rerunning it.</span></span>
  
## <a name="logic-errors"></a><span data-ttu-id="22f11-120">Логические ошибки</span><span class="sxs-lookup"><span data-stu-id="22f11-120">Logic Errors</span></span>

 <span data-ttu-id="22f11-121">*Логические ошибки* — это те, которые появляются после использования приложения.</span><span class="sxs-lookup"><span data-stu-id="22f11-121">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="22f11-122">Чаще всего они ошибочно допущены разработчиком, или нежелательные или непредвиденные результаты в ответ на действия пользователя.</span><span class="sxs-lookup"><span data-stu-id="22f11-122">They are most often faulty assumptions made by the developer, or unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="22f11-123">Например, неверно типизированный ключ может предоставить методу неверную информацию или предположить, что в случае, если это не так, может быть предоставлено допустимое значение для метода.</span><span class="sxs-lookup"><span data-stu-id="22f11-123">For example, a mistyped key might provide incorrect information to a method, or you may assume that a valid value is always supplied to a method when that is not the case.</span></span> <span data-ttu-id="22f11-124">Несмотря на то, что логические ошибки могут обрабатываться с помощью [обработки исключений](../../language-reference/statements/try-catch-finally-statement.md) (например, путем проверки того, что аргумент является `Nothing` и создает исключение <xref:System.ArgumentNullException> ), чаще всего они должны быть устранены путем исправления ошибки в логике и повторной компиляции приложения.</span><span class="sxs-lookup"><span data-stu-id="22f11-124">Although logic errors can be handled by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md) (for example, by testing whether an argument is `Nothing` and throwing an <xref:System.ArgumentNullException>), most commonly they should be addressed by correcting the error in logic and recompiling the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="22f11-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="22f11-125">See also</span></span>

- [<span data-ttu-id="22f11-126">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="22f11-126">Try...Catch...Finally Statement</span></span>](../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="22f11-127">Основы отладки</span><span class="sxs-lookup"><span data-stu-id="22f11-127">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
