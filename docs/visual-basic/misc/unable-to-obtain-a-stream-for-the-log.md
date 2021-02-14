---
description: 'Дополнительные сведения о: не удается получить поток для журнала'
title: Невозможно получить поток для журнала
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 6eda12eb4dc2b3cf303e543a66e1f2f7d739eb6b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455279"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="f7d4d-103">Невозможно получить поток для журнала</span><span class="sxs-lookup"><span data-stu-id="f7d4d-103">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="f7d4d-104">Невозможно получить поток для журнала.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-104">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="f7d4d-105">Потенциальные имена файлов, основанные на \<name> , уже используются.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-105">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f7d4d-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Классу не удалось создать новый файл журнала, так как все возможные имена файлов журналов на основе \<name> уже используются.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-106">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f7d4d-107">Наличие слишком большого количества файлов журнала может быть признаком проблем с архитектурой приложения.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-107">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="f7d4d-108">Дополнительные сведения содержатся в документации по классу <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f7d4d-108">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7d4d-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f7d4d-109">To correct this error</span></span>  
  
1. <span data-ttu-id="f7d4d-110">Установите свойство <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> в значение <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> или <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> , чтобы включить метку даты в имя файла журнала.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="f7d4d-111">Архивируйте существующие журналы и удалите их с компьютера, чтобы разрешить объекту <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> создавать новые журналы.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-111">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d4d-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f7d4d-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="f7d4d-113">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="f7d4d-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="f7d4d-114">My. Application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="f7d4d-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
