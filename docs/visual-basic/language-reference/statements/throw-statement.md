---
description: 'Дополнительные сведения о инструкции: Throw (Visual Basic)'
title: Оператор Throw
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: b7fa4183b5997e5dac8045502a8eed1afe66fc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740942"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="0b32d-103">Оператор Throw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b32d-103">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="0b32d-104">Создает исключение в процедуре.</span><span class="sxs-lookup"><span data-stu-id="0b32d-104">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b32d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b32d-105">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="0b32d-106">Отделение</span><span class="sxs-lookup"><span data-stu-id="0b32d-106">Part</span></span>

`expression`\
<span data-ttu-id="0b32d-107">Предоставляет сведения о вызываемом исключении.</span><span class="sxs-lookup"><span data-stu-id="0b32d-107">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="0b32d-108">Необязательно, если размещен в `Catch` операторе, в противном случае является обязательным.</span><span class="sxs-lookup"><span data-stu-id="0b32d-108">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b32d-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b32d-109">Remarks</span></span>

<span data-ttu-id="0b32d-110">`Throw`Оператор создает исключение, которое можно обработать с помощью структурированного кода обработки исключений ( `Try` ... `Catch` ...`Finally`) или неструктурированный код обработки исключений ( `On Error GoTo` ).</span><span class="sxs-lookup"><span data-stu-id="0b32d-110">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="0b32d-111">Можно использовать `Throw` инструкцию для перехвата ошибок в коде, так как Visual Basic перемещается вверх по стеку вызовов до тех пор, пока не найдет соответствующий код обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="0b32d-111">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="0b32d-112">`Throw`Инструкцию без выражения можно использовать только в `Catch` операторе, в этом случае инструкция повторно создает исключение, которое в настоящее время обрабатывается `Catch` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="0b32d-112">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="0b32d-113">`Throw`Инструкция сбрасывает стек вызовов для `expression` исключения.</span><span class="sxs-lookup"><span data-stu-id="0b32d-113">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="0b32d-114">Если `expression` параметр не указан, стек вызовов остается без изменений.</span><span class="sxs-lookup"><span data-stu-id="0b32d-114">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="0b32d-115">Доступ к стеку вызовов для исключения можно получить с помощью <xref:System.Exception.StackTrace%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="0b32d-115">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="0b32d-116">Пример</span><span class="sxs-lookup"><span data-stu-id="0b32d-116">Example</span></span>

<span data-ttu-id="0b32d-117">Следующий код использует `Throw` инструкцию для создания исключения:</span><span class="sxs-lookup"><span data-stu-id="0b32d-117">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="0b32d-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0b32d-118">See also</span></span>

- [<span data-ttu-id="0b32d-119">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="0b32d-119">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="0b32d-120">Оператор On Error</span><span class="sxs-lookup"><span data-stu-id="0b32d-120">On Error Statement</span></span>](on-error-statement.md)
