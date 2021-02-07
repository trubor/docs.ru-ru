---
description: 'Дополнительные сведения: отслеживание участников'
title: Участники отслеживания
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 2fa4edd0f93e72bff0ee4c9a07ad6f6988f3e040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755178"
---
# <a name="tracking-participants"></a><span data-ttu-id="b3504-103">Участники отслеживания</span><span class="sxs-lookup"><span data-stu-id="b3504-103">Tracking Participants</span></span>

<span data-ttu-id="b3504-104">Участниками отслеживания являются точки расширения, обеспечивающие разработчику рабочего процесса доступ к объектам <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> и возможность их обработки.</span><span class="sxs-lookup"><span data-stu-id="b3504-104">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b3504-105">включает стандартного участника отслеживания, который пишет записи отслеживания в виде средства трассировки событий для Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b3504-105">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="b3504-106">Если это не отвечает заданным требованиям, то можно создать своего собственного участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b3504-106">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="b3504-107">Участники отслеживания</span><span class="sxs-lookup"><span data-stu-id="b3504-107">Tracking Participants</span></span>  

 <span data-ttu-id="b3504-108">Инфраструктура отслеживания позволяет применять фильтр к исходящим записям отслеживания таким образом, что участник может подписаться на подмножество записей.</span><span class="sxs-lookup"><span data-stu-id="b3504-108">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="b3504-109">Фильтр применяется через профиль отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b3504-109">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="b3504-110">Windows Workflow Foundation (WF) в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] предоставляет участник отслеживания, записывающий записи отслеживания в сеанс ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-110">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b3504-111">Участник настраивается в службе рабочего процесса путем добавления в файл конфигурации поведения, связанного с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="b3504-111">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b3504-112">Включив участника отслеживания ETW, можно будет просматривать записи отслеживания в обозревателе событий.</span><span class="sxs-lookup"><span data-stu-id="b3504-112">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b3504-113">Образец пакета SDK для отслеживания на основе ETW помогает освоиться с отслеживанием WF с помощью участника отслеживания на основе ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-113">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="b3504-114">Участник отслеживания ETW</span><span class="sxs-lookup"><span data-stu-id="b3504-114">ETW Tracking Participant</span></span>  

 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="b3504-115">включает участника отслеживания ETW, который вносит записи в сеанс ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-115">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b3504-116">Это делается очень эффективно, с минимальным воздействием на работу приложения и пропускную способность сервера.</span><span class="sxs-lookup"><span data-stu-id="b3504-116">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="b3504-117">Преимущество использования стандартного участника отслеживания трассировки событий Windows в том, что получаемые им записи отслеживания можно просматривать в других приложениях и системных журналах в обозревателе событий Windows.</span><span class="sxs-lookup"><span data-stu-id="b3504-117">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="b3504-118">Cтандартный участник отслеживания ETW настраивается в файле Web.config, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b3504-118">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="b3504-119">Если имя `trackingProfile` не указано (например, это просто `<etwTracking/>` или `<etwTracking profileName=""/>`), используется по умолчанию профиль отслеживания, установленный с [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] в файле Machine.config.</span><span class="sxs-lookup"><span data-stu-id="b3504-119">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="b3504-120">По умолчанию профиль отслеживания в файле Machine.config подписывается на записи и сбои экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b3504-120">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="b3504-121">В ETW события записываются в сеанс ETW через идентификатор поставщика.</span><span class="sxs-lookup"><span data-stu-id="b3504-121">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="b3504-122">Идентификатор поставщика, используемый участником отслеживания ETW для внесения записей отслеживания в ETW, определяется в разделе diagnostics файла Web.config (в `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="b3504-122">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="b3504-123">Как показано в следующем примере, если идентификатор поставщика не задан, по умолчанию участник отслеживания ETW использует стандартный идентификатор.</span><span class="sxs-lookup"><span data-stu-id="b3504-123">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="b3504-124">На следующей иллюстрации показан поток данных отслеживания, проходящих через участника отслеживание ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-124">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="b3504-125">Когда данные отслеживания попадают в сеанс ETW, обратиться к ним можно несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="b3504-125">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="b3504-126">Обращаться к этим событиям лучше всего с помощью обозревателя событий - простого инструмента Windows для просмотра журналов и данных трассировки, полученных от приложений и служб.</span><span class="sxs-lookup"><span data-stu-id="b3504-126">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![Поток отслеживания данных с помощью поставщика отслеживания ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="b3504-128">Данные события участника отслеживания</span><span class="sxs-lookup"><span data-stu-id="b3504-128">Tracking Participant Event Data</span></span>  

 <span data-ttu-id="b3504-129">Участник отслеживания сериализует данные отслеживания события в сеансе ETW в формате «одно событие - одна запись отслеживания».</span><span class="sxs-lookup"><span data-stu-id="b3504-129">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="b3504-130">Событие определяется по идентификатору в диапазоне от 100 до 199.</span><span class="sxs-lookup"><span data-stu-id="b3504-130">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="b3504-131">Определения записей событий отслеживания, созданных участником отслеживания, см. в разделе [Отслеживание событий отслеживания](tracking-events-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="b3504-131">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="b3504-132">Размер события ETW ограничен меньшей из двух величин: размером буфера ETW и максимальным размером полезных данных о событии ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-132">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="b3504-133">Если размер события превышает любое из этих ограничений ETW, событие усекается и его содержание удаляется случайным образом.</span><span class="sxs-lookup"><span data-stu-id="b3504-133">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="b3504-134">Переменные, аргументы, заметки и настраиваемые данные не удаляются выборочно.</span><span class="sxs-lookup"><span data-stu-id="b3504-134">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="b3504-135">В случае усечения все они усекаются независимо от значения, из-за которого размер события превысил предела ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-135">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="b3504-136">Удаленные данные заменяются `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="b3504-136">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="b3504-137">Сложные типы в переменных, аргументах и пользовательских элементах данных сериализуются в запись событий ETW с помощью <xref:System.Runtime.Serialization.NetDataContractSerializer> класса.</span><span class="sxs-lookup"><span data-stu-id="b3504-137">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="b3504-138">Этот класс включает информацию о типе CLR в сериализованном XML-потоке.</span><span class="sxs-lookup"><span data-stu-id="b3504-138">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="b3504-139">Усечение полезных данных из-за ограничений ETW может привести к дублированию записей отслеживания, которые направляются в сеанс ETW.</span><span class="sxs-lookup"><span data-stu-id="b3504-139">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="b3504-140">Это может произойти, если события прослушиваются несколькими сеансами с разной предельной полезной нагрузкой для событий.</span><span class="sxs-lookup"><span data-stu-id="b3504-140">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="b3504-141">В сеансе с более низкой границей событие может быть усечено.</span><span class="sxs-lookup"><span data-stu-id="b3504-141">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="b3504-142">Участник отслеживания трассировки событий Windows не имеет сведений о числе сеансов, прослушивающих события; если событие усекается для сеанса, то участник трассировки событий Windows пытается отправить событие повторно один раз.</span><span class="sxs-lookup"><span data-stu-id="b3504-142">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="b3504-143">В этом случае сеанс, настроенный на прием полезных данных большего объема, получит событие дважды (неусеченное и усеченное событие).</span><span class="sxs-lookup"><span data-stu-id="b3504-143">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="b3504-144">Дублирование можно предотвратить, задав для всех сеансов трассировки событий Windows одинаковый предельный размер буфера.</span><span class="sxs-lookup"><span data-stu-id="b3504-144">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="b3504-145">Доступ к данным отслеживания из участника ETW в обозревателе событий</span><span class="sxs-lookup"><span data-stu-id="b3504-145">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  

 <span data-ttu-id="b3504-146">Обратиться к событиям, записанным участником отслеживания ETW в сеансе ETW, можно с помощью обозревателя событий (если по умолчанию используется идентификатор поставщика).</span><span class="sxs-lookup"><span data-stu-id="b3504-146">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="b3504-147">Это позволяет быстро просмотреть записи отслеживания, созданные рабочим процессом.</span><span class="sxs-lookup"><span data-stu-id="b3504-147">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3504-148">События записей отслеживания, записанные в сеансах ETW, используют идентификаторы событий в диапазоне от 100 до 199.</span><span class="sxs-lookup"><span data-stu-id="b3504-148">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="b3504-149">Включение просмотра записей отслеживания в обозревателе событий</span><span class="sxs-lookup"><span data-stu-id="b3504-149">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="b3504-150">Запустите обозреватель событий (EVENTVWR.EXE)</span><span class="sxs-lookup"><span data-stu-id="b3504-150">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="b3504-151">Выберите **Просмотр событий, журналы приложений и служб, Microsoft, Windows, сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="b3504-151">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="b3504-152">Щелкните правой кнопкой мыши и убедитесь, что выбран пункт **Просмотр, Показать журналы аналитики и отладки** .</span><span class="sxs-lookup"><span data-stu-id="b3504-152">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="b3504-153">Если он еще не выбран, выберите его, чтобы рядом появилась галочка.</span><span class="sxs-lookup"><span data-stu-id="b3504-153">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="b3504-154">Отобразятся журналы **аналитики**, **производительности** и **отладки** .</span><span class="sxs-lookup"><span data-stu-id="b3504-154">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="b3504-155">Щелкните правой кнопкой мыши **аналитический** журнал и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="b3504-155">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="b3504-156">Журнал будет существовать в файле %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl.</span><span class="sxs-lookup"><span data-stu-id="b3504-156">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="b3504-157">Настраиваемый участник отслеживания</span><span class="sxs-lookup"><span data-stu-id="b3504-157">Custom Tracking Participant</span></span>  

 <span data-ttu-id="b3504-158">API участника отслеживания позволяет расширить среду выполнения отслеживания с помощью пользовательского участника отслеживания, который может включать настраиваемую логику для обработки записей отслеживания, созданных средой рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b3504-158">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="b3504-159">Чтобы создать настраиваемого участника отслеживания, разработчик должен реализовать метод `Track` в классе <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b3504-159">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="b3504-160">Этот метод вызывается, когда среда рабочего процесса выпускает запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b3504-160">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="b3504-161">Участники отслеживания являются производными от класса <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b3504-161">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="b3504-162">Предоставляемый системой <xref:System.Activities.Tracking.EtwTrackingParticipant> выпускает событие Event Tracking для Windows (ETW) для каждой из полученных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b3504-162">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="b3504-163">Чтоб создать настраиваемого участника отслеживания, создается класс, производный от <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b3504-163">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="b3504-164">Чтобы обеспечить основные функции отслеживания, переопределите метод <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3504-164">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="b3504-165"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> вызывается, когда среда выполнения отправляет отслеживаемую запись и эта запись может быть обработана нужным способом.</span><span class="sxs-lookup"><span data-stu-id="b3504-165"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="b3504-166">В следующем примере определяется настраиваемый класс участника отслеживания, который выдает все записи отслеживания в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="b3504-166">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="b3504-167">Можно также использовать объект <xref:System.Activities.Tracking.TrackingParticipant>, обрабатывающий записи отслеживания асинхронно с помощью методов `BeginTrack` и `EndTrack`</span><span class="sxs-lookup"><span data-stu-id="b3504-167">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b3504-168">Чтобы использовать конкретного участника отслеживания, зарегистрируйте его с экземпляром рабочего процесса, который хотите отследить, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b3504-168">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="b3504-169">В следующем примере создается рабочий процесс, состоящий из действия <xref:System.Activities.Statements.Sequence>, включающего действие <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="b3504-169">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="b3504-170">`ConsoleTrackingParticipant` добавляется к расширениям, и вызывается рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="b3504-170">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3504-171">См. также</span><span class="sxs-lookup"><span data-stu-id="b3504-171">See also</span></span>

- <span data-ttu-id="b3504-172">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b3504-172">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="b3504-173">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b3504-173">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
