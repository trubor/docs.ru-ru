---
description: 'Дополнительные сведения: имя источника, указанное в EventLogSource, зарегистрировано в журнале, отличном от указанного в EventLogName'
title: Имя источника, указанное в EventLogSource, зарегистрировано в журнале, отличном от указанного в EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: d6b9c1265276f94369d37e6ac55604b761fb9bcc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455461"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="d627b-103">Имя источника, указанное в EventLogSource, зарегистрировано в журнале, отличном от указанного в EventLogName</span><span class="sxs-lookup"><span data-stu-id="d627b-103">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>

<span data-ttu-id="d627b-104">`EventLog` пытается сослаться на источник, который зарегистрирован в другом журнале.</span><span class="sxs-lookup"><span data-stu-id="d627b-104">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="d627b-105">Для добавления записей в журнал событий необходимо задать свойство <xref:System.Diagnostics.EventLog.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="d627b-105">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="d627b-106">Свойство <xref:System.Diagnostics.EventLog.Source%2A> регистрирует компонент в журнале событий в качестве допустимого источника записей.</span><span class="sxs-lookup"><span data-stu-id="d627b-106">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="d627b-107">Один источник может быть связан только с одним журналом событий одновременно (и поэтому может добавлять записи только в него).</span><span class="sxs-lookup"><span data-stu-id="d627b-107">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="d627b-108">По умолчанию при попытке добавить запись в журнал без предварительной регистрации компонента в качестве разрешенного источника система автоматически регистрирует его в этом журнале, используя значение свойства <xref:System.Diagnostics.EventLog.Source%2A> в качестве строки источника.</span><span class="sxs-lookup"><span data-stu-id="d627b-108">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d627b-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d627b-109">To correct this error</span></span>  
  
- <span data-ttu-id="d627b-110">Убедитесь в том, что источник зарегистрирован в соответствующем журнале.</span><span class="sxs-lookup"><span data-stu-id="d627b-110">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="d627b-111">Для этого используйте метод <xref:System.Diagnostics.EventLog.CreateEventSource%2A> или одну из его перегрузок, чтобы указать строку, однозначно идентифицирующую компонент в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="d627b-111">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d627b-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d627b-112">See also</span></span>

- <span data-ttu-id="d627b-113">[Администрирование журналов событий](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d627b-113">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="d627b-114">[Ссылки на журнал событий](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d627b-114">[Event Log References](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span></span>
- <span data-ttu-id="d627b-115">[Как добавить приложение в качестве источника записей журнала событий](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d627b-115">[How to: Add Your Application as a Source of Event Log Entries](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span></span>
- <span data-ttu-id="d627b-116">[Как удалить источник события](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d627b-116">[How to: Remove an Event Source](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span></span>
