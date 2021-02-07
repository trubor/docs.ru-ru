---
description: Дополнительные сведения о операторе "завершение" (Visual Basic)
title: Оператор Stop
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 1e25eb88d1b85f38a53023dfb7dfbc877f498e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741085"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="8db19-103">Оператор Stop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8db19-103">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="8db19-104">Приостанавливает выполнение.</span><span class="sxs-lookup"><span data-stu-id="8db19-104">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db19-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8db19-105">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="8db19-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="8db19-106">Remarks</span></span>  

 <span data-ttu-id="8db19-107">Операторы можно разместить `Stop` в любом месте процедуры, чтобы приостановить выполнение.</span><span class="sxs-lookup"><span data-stu-id="8db19-107">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="8db19-108">Использование `Stop` инструкции аналогично установке точки останова в коде.</span><span class="sxs-lookup"><span data-stu-id="8db19-108">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="8db19-109">`Stop`Инструкция приостанавливает выполнение, но в отличие от этого `End` она не закрывает никакие файлы и не очищает переменные, если она не обнаружена в скомпилированном исполняемом файле (exe).</span><span class="sxs-lookup"><span data-stu-id="8db19-109">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8db19-110">Если `Stop` инструкция обнаружена в коде, который выполняется вне интегрированной среды разработки (IDE), вызывается отладчик.</span><span class="sxs-lookup"><span data-stu-id="8db19-110">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="8db19-111">Это справедливо независимо от того, был ли код скомпилирован в режиме отладки или розничной торговли.</span><span class="sxs-lookup"><span data-stu-id="8db19-111">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8db19-112">Пример</span><span class="sxs-lookup"><span data-stu-id="8db19-112">Example</span></span>  

 <span data-ttu-id="8db19-113">В этом примере используется `Stop` оператор для приостановки выполнения для каждой итерации в `For...Next` цикле.</span><span class="sxs-lookup"><span data-stu-id="8db19-113">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="8db19-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8db19-114">See also</span></span>

- [<span data-ttu-id="8db19-115">End, инструкция</span><span class="sxs-lookup"><span data-stu-id="8db19-115">End Statement</span></span>](end-statement.md)
