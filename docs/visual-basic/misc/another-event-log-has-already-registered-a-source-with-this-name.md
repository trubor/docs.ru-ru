---
description: 'Дополнительные сведения: другой журнал событий уже зарегистрировал источник с таким именем'
title: Другой журнал событий уже зарегистрировал источник с таким именем
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: ec6ae0b3ef12452a0135e5bf17dbdd5844c0f478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787361"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="af170-103">Другой журнал событий уже зарегистрировал источник с таким именем</span><span class="sxs-lookup"><span data-stu-id="af170-103">Another event log has already registered a source with this name</span></span>

<span data-ttu-id="af170-104">Предпринята попытка выполнить запись в журнал событий, когда указанный источник уже зарегистрирован другим журналом событий.</span><span class="sxs-lookup"><span data-stu-id="af170-104">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="af170-105">Перед внесением компонента записи в журнал необходимо задать свойство <xref:System.Diagnostics.EventLog.Source%2A> вашего экземпляра компонента <xref:System.Diagnostics.EventLog> .</span><span class="sxs-lookup"><span data-stu-id="af170-105">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="af170-106">В этом случае система проверяет, что указанный источник зарегистрирован в журнале событий, в который компонент осуществляет запись, и при необходимости вызывает <xref:System.Diagnostics.EventLog.CreateEventSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="af170-106">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af170-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="af170-107">To correct this error</span></span>  
  
1. <span data-ttu-id="af170-108">Удалите связь источника с первым журналом с помощью метода <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> или <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="af170-108">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="af170-109">Зарегистрируйте источник для нового журнала.</span><span class="sxs-lookup"><span data-stu-id="af170-109">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af170-110">См. также</span><span class="sxs-lookup"><span data-stu-id="af170-110">See also</span></span>

- [<span data-ttu-id="af170-111">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="af170-111">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
