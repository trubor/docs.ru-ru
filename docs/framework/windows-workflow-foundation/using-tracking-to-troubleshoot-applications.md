---
description: Дополнительные сведения см. в статье об устранении неполадок приложений с помощью функции отслеживания.
title: Использование отслеживания для устранения неполадок приложений
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 9ff2c1b9a4a35a75a9f4d2229b5b43d6607e7557
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754996"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="8fc6d-103">Использование отслеживания для устранения неполадок приложений</span><span class="sxs-lookup"><span data-stu-id="8fc6d-103">Using Tracking to Troubleshoot Applications</span></span>

<span data-ttu-id="8fc6d-104">Windows Workflow Foundation (WF) позволяет отслеживанию сведений, связанных с рабочим процессом, чтобы предоставить подробные сведения о выполнении Windows Workflow Foundation приложения или службы.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-104">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="8fc6d-105">Узлы Windows Workflow Foundation могут собирать события рабочего процесса во время выполнения экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-105">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="8fc6d-106">Если рабочий процесс создает ошибки или исключения, можно использовать сведения об отслеживании Windows Workflow Foundation для устранения неполадок обработки.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-106">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="8fc6d-107">Устранение неполадок WF с помощью отслеживания WF</span><span class="sxs-lookup"><span data-stu-id="8fc6d-107">Troubleshooting a WF using WF Tracking</span></span>  

 <span data-ttu-id="8fc6d-108">Чтобы обнаружить ошибки в процессе обработки Windows Workflow Foundation действия, можно включить отслеживание с помощью профиля отслеживания, который запрашивает <xref:System.Activities.Tracking.ActivityStateRecord> состояние с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-108">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="8fc6d-109">Соответствующий запрос задан в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-109">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="8fc6d-110">Если ошибка передается и обрабатывается в обработчике ошибок (например, в действии <xref:System.Activities.Statements.TryCatch>), это можно обнаружить с помощью записи <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-110">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="8fc6d-111">Запись <xref:System.Activities.Tracking.FaultPropagationRecord> указывает исходное действие, вызвавшее ошибку, и имя обработчика ошибок.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="8fc6d-112"><xref:System.Activities.Tracking.FaultPropagationRecord>Содержит сведения об ошибке в виде стека исключений для ошибки.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-112">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="8fc6d-113">Запрос для подписки на объект <xref:System.Activities.Tracking.FaultPropagationRecord> показан в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-113">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="8fc6d-114">Если ошибка не обрабатывается в рабочем процессе, это создает необработанное исключение в экземпляре рабочего процесса, и работа экземпляра рабочего процесса прерывается.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-114">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="8fc6d-115">Для получения сведений о необработанном исключении профиль отслеживания должен запросить запись экземпляра рабочего процесса с состоянием `state name="UnhandledException"`, как указано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-115">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="8fc6d-116">Когда экземпляр рабочего процесса обнаруживает необработанное исключение, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> объект создается, если включено отслеживание Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-116">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="8fc6d-117">Эта запись отслеживания содержит сведения об ошибке в виде стека исключений.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-117">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="8fc6d-118">Он содержит подробные сведения об источнике ошибки (например, о действии), вызвавшем сбой, и привело к необработанному исключению. Чтобы подписываться на события сбоя из Windows Workflow Foundation, включите отслеживание, добавив участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-118">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="8fc6d-119">Настройте участника с профилем отслеживания, запрашивающим запись `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord> и `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-119">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="8fc6d-120">Если отслеживание включено с использованием участника отслеживания ETW, события ошибок создаются в сеансе ETW.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-120">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="8fc6d-121">События можно просмотреть с помощью средства «Просмотр событий».</span><span class="sxs-lookup"><span data-stu-id="8fc6d-121">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="8fc6d-122">Его можно найти в разделе **журналы приложений и служб Просмотр событий >. >Microsoft->Windows->сервер приложений — приложения** в канале аналитики.</span><span class="sxs-lookup"><span data-stu-id="8fc6d-122">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc6d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="8fc6d-123">See also</span></span>

- <span data-ttu-id="8fc6d-124">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8fc6d-124">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="8fc6d-125">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8fc6d-125">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
