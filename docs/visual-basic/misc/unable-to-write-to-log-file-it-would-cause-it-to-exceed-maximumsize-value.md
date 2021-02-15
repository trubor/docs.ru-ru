---
description: 'Дополнительные сведения о: не удается выполнить запись в файл журнала, так как запись в него приведет к превышению значения MaximumSize'
title: Невозможно произвести запись в файл журнала, так как это приведет к превышению значения MaximumSize.
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 5c305c550f7a63183a0ac529adc788fa79b5794f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456943"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="a4f6b-103">Невозможно произвести запись в файл журнала, так как это приведет к превышению значения MaximumSize.</span><span class="sxs-lookup"><span data-stu-id="a4f6b-103">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>

<span data-ttu-id="a4f6b-104">Класс <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> не может выполнить запись в файл журнала, так как:</span><span class="sxs-lookup"><span data-stu-id="a4f6b-104">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="a4f6b-105">размер файла журнала (в байтах) больше, чем значение свойства <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="a4f6b-105">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="a4f6b-106">—и—</span><span class="sxs-lookup"><span data-stu-id="a4f6b-106">—and—</span></span>  
  
- <span data-ttu-id="a4f6b-107">значение свойства <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> равно <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="a4f6b-107">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4f6b-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a4f6b-108">To correct this error</span></span>  
  
1. <span data-ttu-id="a4f6b-109">Архивируйте существующие журналы и удалите их с компьютера, чтобы разрешить объекту <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> создавать новые журналы.</span><span class="sxs-lookup"><span data-stu-id="a4f6b-109">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="a4f6b-110">Измените значение свойства <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> , чтобы разрешить журналы больших размеров.</span><span class="sxs-lookup"><span data-stu-id="a4f6b-110">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="a4f6b-111">Задайте для свойства <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> значение <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> , чтобы отменить сообщения без предупреждения, если журнал окажется слишком большим.</span><span class="sxs-lookup"><span data-stu-id="a4f6b-111">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f6b-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4f6b-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="a4f6b-113">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="a4f6b-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="a4f6b-114">My. Application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="a4f6b-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
