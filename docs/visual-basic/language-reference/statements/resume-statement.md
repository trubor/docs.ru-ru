---
description: Дополнительные сведения о инструкции Resume
title: Оператор Resume
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: fd3a02fc2606355d7e3a34f5c0d69eef577809de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741189"
---
# <a name="resume-statement"></a><span data-ttu-id="08632-103">Оператор Resume</span><span class="sxs-lookup"><span data-stu-id="08632-103">Resume Statement</span></span>

<span data-ttu-id="08632-104">Возобновляет выполнение по завершении подпрограммы обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="08632-104">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="08632-105">Мы рекомендуем использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и `On Error` `Resume` инструкций и.</span><span class="sxs-lookup"><span data-stu-id="08632-105">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="08632-106">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08632-106">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08632-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08632-107">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="08632-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="08632-108">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="08632-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="08632-109">Required.</span></span> <span data-ttu-id="08632-110">Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="08632-110">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="08632-111">Если ошибка произошла в вызванной процедуре, выполнение возобновляется с оператора, который последний раз вызывался из процедуры, содержащей подпрограмму обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="08632-111">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="08632-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="08632-112">Optional.</span></span> <span data-ttu-id="08632-113">Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, следующей за инструкцией, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="08632-113">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="08632-114">Если ошибка произошла в вызванной процедуре, выполнение возобновляется с помощью инструкции, следующей за инструкцией, которая последний раз вызвала процедуру, содержащую подпрограмму обработки ошибок (или `On Error Resume Next` ).</span><span class="sxs-lookup"><span data-stu-id="08632-114">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="08632-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="08632-115">Optional.</span></span> <span data-ttu-id="08632-116">Выполнение возобновляется в строке, указанной в `line` аргументе Required.</span><span class="sxs-lookup"><span data-stu-id="08632-116">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="08632-117">`line`Аргумент является меткой строки или номером строки и должен находиться в той же процедуре, что и обработчик ошибок.</span><span class="sxs-lookup"><span data-stu-id="08632-117">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08632-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="08632-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08632-119">Рекомендуется использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и `On Error` `Resume` инструкций и.</span><span class="sxs-lookup"><span data-stu-id="08632-119">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="08632-120">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08632-120">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="08632-121">При использовании `Resume` инструкции в любом месте, кроме в подпрограммы обработки ошибок, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="08632-121">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="08632-122">`Resume`Инструкция не может быть использована в любой процедуре, содержащей `Try...Catch...Finally` оператор.</span><span class="sxs-lookup"><span data-stu-id="08632-122">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08632-123">Пример</span><span class="sxs-lookup"><span data-stu-id="08632-123">Example</span></span>  

 <span data-ttu-id="08632-124">В этом примере `Resume` оператор используется для завершения обработки ошибок в процедуре, а затем возобновляется выполнение с инструкцией, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="08632-124">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="08632-125">Номер ошибки 55 создается для демонстрации использования `Resume` инструкции.</span><span class="sxs-lookup"><span data-stu-id="08632-125">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="08632-126">Требования</span><span class="sxs-lookup"><span data-stu-id="08632-126">Requirements</span></span>  

 <span data-ttu-id="08632-127">**Пространство имен:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="08632-127">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="08632-128">**Сборка:** Библиотека времени выполнения Visual Basic (в Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="08632-128">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08632-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="08632-129">See also</span></span>

- [<span data-ttu-id="08632-130">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="08632-130">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="08632-131">Оператор Error</span><span class="sxs-lookup"><span data-stu-id="08632-131">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="08632-132">Оператор On Error</span><span class="sxs-lookup"><span data-stu-id="08632-132">On Error Statement</span></span>](on-error-statement.md)
