---
description: Дополнительные сведения о переносе
title: Перенос
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: ce88a71d87c7dd09f321ee58f603f7c4672a6df9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758064"
---
# <a name="transfer"></a><span data-ttu-id="f8aa7-103">Перенос</span><span class="sxs-lookup"><span data-stu-id="f8aa7-103">Transfer</span></span>

<span data-ttu-id="f8aa7-104">В этом разделе описывается перемещение в модели трассировки действий Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8aa7-104">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="f8aa7-105">Определение перенаправления</span><span class="sxs-lookup"><span data-stu-id="f8aa7-105">Transfer Definition</span></span>  

 <span data-ttu-id="f8aa7-106">Перенаправления между действиями передают причинно-следственную связь между событиями в связанных действиях внутри конечных точек.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-106">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="f8aa7-107">Два действия связываются перенаправлениями при потоке управления от одного из этих действий к другому, например когда вызов метода пересекает границы действия.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-107">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="f8aa7-108">В WCF, когда в службе поступают байты, действие Listen on передается в действие Receive Bytes, где создается объект Message.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-108">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="f8aa7-109">Список комплексных сценариев трассировки и их соответствующих действий и структуры трассировки см. в разделе [Сценарии сквозной трассировки](end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="f8aa7-109">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="f8aa7-110">Для выдачи трассировки перенаправлений задайте параметр `ActivityTracing` в источнике трассировки, как показано в предыдущем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-110">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="f8aa7-111">Использование перенаправления для корреляции действий внутри конечных точек</span><span class="sxs-lookup"><span data-stu-id="f8aa7-111">Using Transfer to Correlate Activities Within Endpoints</span></span>  

 <span data-ttu-id="f8aa7-112">Действия и перенаправления позволяют пользователю с определенной вероятностью найти первопричину ошибки.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-112">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="f8aa7-113">Например, если при перенаправлении от действия M на действие N и обратно (в компонентах M и N соответственно) сразу же после перенаправления обратно на M происходит сбой, можно сделать вывод, что это скорее всего связано с передачей действием N данных обратно действию M.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-113">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="f8aa7-114">Трассировка перенаправления выдается от действия M на действие N при передаче управления от M к N. Например, N выполняет некоторую обработку для M в связи с тем, что вызов метода пересекает границы действий.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-114">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="f8aa7-115">Действие N может уже существовать или быть создано.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-115">N may already exist or has been created.</span></span> <span data-ttu-id="f8aa7-116">Действие N порождается действием M, когда N представляет собой новое действие, выполняющее некоторую обработку для M.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-116">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="f8aa7-117">За перенаправлением от M на N не обязательно следует перенаправление обратно от N на M. Это связано с тем, что M может породить некоторую обработку в N и не следит за тем, когда N завершит эту обработку.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-117">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="f8aa7-118">Фактически действие M может быть прекращено до того, как N завершит свою задачу.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-118">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="f8aa7-119">Это происходит в действии Open ServiceHost (M), которое порождает действия прослушивателя (N) и затем завершается.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-119">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="f8aa7-120">Перенаправление обратно от N на M означает, что действие N завершило обработку, относящуюся к действию M.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-120">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="f8aa7-121">Действие N может продолжать выполнять другую обработку, не относящуюся к действию M, например существующее действие структуры проверки подлинности (N) продолжит получать запросы на вход (M) от других действий входа.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-121">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="f8aa7-122">Между действиями M и N необязательно должно существовать отношение вложенности. Это может произойти по двум причинам.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-122">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="f8aa7-123">Первая — когда действие M не осуществляет мониторинг обработки, выполняемой действием N, даже хотя действие M инициировало действие N. Вторая — когда действия N уже существует.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-123">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="f8aa7-124">Пример перенаправления</span><span class="sxs-lookup"><span data-stu-id="f8aa7-124">Example of Transfers</span></span>  

 <span data-ttu-id="f8aa7-125">Ниже приведено два примера перенаправления.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-125">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="f8aa7-126">При создании узла службы конструктор получает управление от вызывающего кода, или вызывающий код выполняет перенаправление на конструктор.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-126">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="f8aa7-127">По завершении выполнения конструктор возвращает управление вызывающему коду, или конструктор выполняет перенаправление обратно на вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-127">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="f8aa7-128">Это случай отношения вложенности.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-128">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="f8aa7-129">Когда прослушиватель начинает обрабатывать данные транспорта, он создает новый поток и передает действию Receive Bytes соответствующий контекст для обработки, т. е. передает управление и данные.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-129">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="f8aa7-130">По завершении обработки запроса этим потоком действие Receive Bytes ничего не передает обратно прослушивателю.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-130">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="f8aa7-131">В этом случае имеет место перенаправление на новое действие потока, однако перенаправления от действия потока не происходит.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-131">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="f8aa7-132">Два действия связаны, но не являются вложенными.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-132">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="f8aa7-133">Последовательность перенаправления между действиями</span><span class="sxs-lookup"><span data-stu-id="f8aa7-133">Activity Transfer Sequence</span></span>  

 <span data-ttu-id="f8aa7-134">Корректная последовательность перенаправления между действиями включает следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-134">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="f8aa7-135">Начало нового действия (заключается в выборе нового идентификатора gAId).</span><span class="sxs-lookup"><span data-stu-id="f8aa7-135">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="f8aa7-136">Выдача трассировки перенаправления на этот новый идентификатор gAId от текущего идентификатора действия.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-136">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="f8aa7-137">Задание нового идентификатора в локальной памяти потока.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-137">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="f8aa7-138">Выдача трассировки Start, обозначающей начало нового действия.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-138">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="f8aa7-139">Возврат к исходному действию заключается в следующем:</span><span class="sxs-lookup"><span data-stu-id="f8aa7-139">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="f8aa7-140">выдача трассировки перенаправления к исходному идентификатору gAId;</span><span class="sxs-lookup"><span data-stu-id="f8aa7-140">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="f8aa7-141">выдача трассировки Stop, обозначающей конец нового действия;</span><span class="sxs-lookup"><span data-stu-id="f8aa7-141">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="f8aa7-142">присвоение локальной памяти потока старого идентификатора gAId.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-142">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="f8aa7-143">В следующем примере кода показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-143">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="f8aa7-144">В этом примере предполагается, что при перенаправлении на новое действие совершается блокирующий вызов, и приводятся трассировки приостановки/возобновления.</span><span class="sxs-lookup"><span data-stu-id="f8aa7-144">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8aa7-145">См. также</span><span class="sxs-lookup"><span data-stu-id="f8aa7-145">See also</span></span>

- [<span data-ttu-id="f8aa7-146">Настройка трассировки</span><span class="sxs-lookup"><span data-stu-id="f8aa7-146">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="f8aa7-147">Использование программы Service Trace Viewer для просмотра скоррелированных трассировок и устранения неполадок</span><span class="sxs-lookup"><span data-stu-id="f8aa7-147">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="f8aa7-148">Сценарии сквозной трассировки</span><span class="sxs-lookup"><span data-stu-id="f8aa7-148">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="f8aa7-149">Программа Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f8aa7-149">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
