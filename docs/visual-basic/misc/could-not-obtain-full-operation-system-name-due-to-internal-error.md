---
description: 'Дополнительные сведения: не удалось получить полное имя операционной системы из-за внутренней ошибки'
title: Не удалось получить полное имя операционной системы из-за внутренней ошибки
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: d274a08728b084b21309862de69e2fded5c164da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463498"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="dd799-103">Не удалось получить полное имя операционной системы из-за внутренней ошибки</span><span class="sxs-lookup"><span data-stu-id="dd799-103">Could not obtain full operation system name due to internal error</span></span>

<span data-ttu-id="dd799-104">Не удалось получить полное имя операционной системы из-за внутренней ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd799-104">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="dd799-105">Это может быть вызвано отсутствием WMI на текущем компьютере.</span><span class="sxs-lookup"><span data-stu-id="dd799-105">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="dd799-106">Не удалось выполнить вызов свойства `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="dd799-106">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="dd799-107">Возможная причина этой ошибки может заключаться в том, что на текущем компьютере не установлен инструментарий управления Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="dd799-107">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd799-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="dd799-108">To correct this error</span></span>  
  
1. <span data-ttu-id="dd799-109">Добавьте блок `Try...Catch` вокруг вызова свойства `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="dd799-109">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="dd799-110">Дополнительные сведения об инструментарии WMI и способах его установки см. в статье "инструментарий управления Windows (WMI) Core".</span><span class="sxs-lookup"><span data-stu-id="dd799-110">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd799-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd799-111">See also</span></span>

- [<span data-ttu-id="dd799-112">My. Computer. info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="dd799-112">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="dd799-113">Обработка и создание исключений в .NET</span><span class="sxs-lookup"><span data-stu-id="dd799-113">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="dd799-114">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="dd799-114">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
