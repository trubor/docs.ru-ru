---
description: 'Дополнительные сведения: профили отслеживания'
title: Профили отслеживания
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9748f0452a1699e08760372f826f2458d82f4b79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755152"
---
# <a name="tracking-profiles"></a><span data-ttu-id="1cc59-103">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="1cc59-103">Tracking Profiles</span></span>

<span data-ttu-id="1cc59-104">Профили отслеживания содержат запросы отслеживания, позволяющие участнику подписываться на события рабочего потока, создаваемые в момент изменения состояния экземпляра рабочего процесса во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1cc59-104">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="1cc59-105">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="1cc59-105">Tracking Profiles</span></span>

<span data-ttu-id="1cc59-106">С помощью профилей отслеживания можно определять, какие данные отслеживания создаются для экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1cc59-106">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="1cc59-107">Если этот профиль не указан, создаются все события отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-107">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="1cc59-108">Если профиль указан, будут создаваться события, определенные в профиле отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-108">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="1cc59-109">Исходя из потребностей можно написать профиль с обычной гранулярностью, который будет подписан на небольшой набор изменений состояния высокого уровня в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="1cc59-109">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="1cc59-110">И наоборот, можно создать очень детальный профиль, результирующие события которого будут достаточно подробными для воспроизведения всего потока выполнения в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="1cc59-110">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="1cc59-111">Профили отслеживания сами являются XML-элементами в стандартном платформа .NET Framework файле конфигурации или задаются в коде.</span><span class="sxs-lookup"><span data-stu-id="1cc59-111">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="1cc59-112">В следующем примере показан профиль отслеживания [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] в файле конфигурации, который позволяет участнику отслеживания подписаться на события рабочих процессов `Started` и `Completed`.</span><span class="sxs-lookup"><span data-stu-id="1cc59-112">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

<span data-ttu-id="1cc59-113">В следующем примере показан соответствующий профиль отслеживания, созданный с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="1cc59-113">The following example shows the equivalent tracking profile created using code.</span></span>

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

<span data-ttu-id="1cc59-114">Записи отслеживания фильтруются посредством режима видимости в рамках профиля отслеживания при помощи атрибута <xref:System.Activities.Tracking.ImplementationVisibility>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-114">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="1cc59-115">Составное действие является действием верхнего уровня, которое содержит другие действия, образующие его реализацию.</span><span class="sxs-lookup"><span data-stu-id="1cc59-115">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="1cc59-116">Режим видимости задает записи отслеживания, созданные из композитных действий в действии рабочего процесса, с целью указания, отслеживаются ли действия, образующие реализацию.</span><span class="sxs-lookup"><span data-stu-id="1cc59-116">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="1cc59-117">Режим видимости применяется на уровне профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-117">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="1cc59-118">Фильтрацией записей отслеживания для отдельно взятых действий в рабочем процессе управляют при помощи запросов в профиле отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-118">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="1cc59-119">Дополнительные сведения см. в разделе **типы запросов профиля отслеживания** в этом документе.</span><span class="sxs-lookup"><span data-stu-id="1cc59-119">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="1cc59-120">Два режима видимости, задаваемые атрибутом `implementationVisibility` в профиле отслеживания, - `RootScope` и `All`.</span><span class="sxs-lookup"><span data-stu-id="1cc59-120">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="1cc59-121">Использование режима `RootScope` удаляет записи отслеживания для действий, образующих реализацию действия в том случае, когда композитное действие не является корневым действием в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="1cc59-121">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="1cc59-122">Это предполагает, что, когда действие, реализуемое при помощи других действий, добавляется в рабочий процесс и параметр `implementationVisibility` имеет значение RootScope, будут отслеживаться только события верхнего уровня внутри этого композитного действия.</span><span class="sxs-lookup"><span data-stu-id="1cc59-122">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="1cc59-123">Если действие является корневым для рабочего процесса, реализация действия - это сам рабочий процесс, а записи отслеживания создаются для действий, образующих реализацию.</span><span class="sxs-lookup"><span data-stu-id="1cc59-123">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="1cc59-124">Использование режима «Все» позволяет создавать записи отслеживания для корневого действия и всех его композитных действий.</span><span class="sxs-lookup"><span data-stu-id="1cc59-124">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="1cc59-125">Например, предположим, что *MyActivity* является составным действием, реализация которого содержит два действия: *Activity1* и *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="1cc59-125">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="1cc59-126">При добавлении этого действия в рабочий процесс и включении отслеживания с помощью профиля отслеживания с параметром `implementationVisibility` `RootScope` , записи отслеживания создаются только для *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="1cc59-126">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="1cc59-127">Однако для действий *Activity1* и *Activity2* не создаются никакие записи.</span><span class="sxs-lookup"><span data-stu-id="1cc59-127">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="1cc59-128">Однако если для `implementationVisibility` атрибута профиля отслеживания задано значение `All` , записи отслеживания передаются не только для *MyActivity*, но и для действий *Activity1* и *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="1cc59-128">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="1cc59-129">Флажок `implementationVisibility` применяется для следующих типов записей отслеживания:</span><span class="sxs-lookup"><span data-stu-id="1cc59-129">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="1cc59-130">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="1cc59-130">ActivityStateRecord</span></span>

- <span data-ttu-id="1cc59-131">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="1cc59-131">FaultPropagationRecord</span></span>

- <span data-ttu-id="1cc59-132">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="1cc59-132">CancelRequestedRecord</span></span>

- <span data-ttu-id="1cc59-133">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="1cc59-133">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="1cc59-134">Запись CustomTrackingRecords, создаваемая из реализации действия, не фильтруется параметром implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="1cc59-134">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="1cc59-135">Функция `implementationVisibility` задается как <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> в профиле отслеживания в коде следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1cc59-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="1cc59-136">Функция `implementationVisibility` может задается как <xref:System.Activities.Tracking.ImplementationVisibility.All> в профиле отслеживания в файле конфигурации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1cc59-136">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

<span data-ttu-id="1cc59-137">Параметр `ImplementationVisibility` в профиле отслеживания является необязательным.</span><span class="sxs-lookup"><span data-stu-id="1cc59-137">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="1cc59-138">По умолчанию он имеет значение `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="1cc59-138">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="1cc59-139">Значения для этого атрибута также учитывают регистр.</span><span class="sxs-lookup"><span data-stu-id="1cc59-139">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="1cc59-140">Отслеживание типов запросов профиля</span><span class="sxs-lookup"><span data-stu-id="1cc59-140">Tracking Profile Query Types</span></span>

<span data-ttu-id="1cc59-141">Профили отслеживания структурированы в форме объявляющих подписок на записи отслеживания, которые позволяют выполнять запросы к среде выполнения рабочего процесса в отношении определенных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-141">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="1cc59-142">Существует множество типов запросов, которые позволяют подписаться на различные классы объектов <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-142">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="1cc59-143">Профили отслеживания могут быть заданы в конфигурации или посредством кода.</span><span class="sxs-lookup"><span data-stu-id="1cc59-143">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="1cc59-144">Ниже приводятся наиболее распространенные типы запросов.</span><span class="sxs-lookup"><span data-stu-id="1cc59-144">Here are the most common query types:</span></span>

- <span data-ttu-id="1cc59-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - используйте этот запрос для отслеживания изменений жизненного цикла экземпляра рабочего процесса, таких как ранее представленные события `Started` и `Completed`.</span><span class="sxs-lookup"><span data-stu-id="1cc59-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="1cc59-146">Запрос <xref:System.Activities.Tracking.WorkflowInstanceQuery> используется для подписки на следующие объекты <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-146">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="1cc59-147">Состояния, на которые можно подписаться, задаются классом <xref:System.Activities.Tracking.WorkflowInstanceStates>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-147">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="1cc59-148">Конфигурация или код, используемые для подписки на записи отслеживания на уровне экземпляра рабочего процесса для состояния экземпляра `Started` при помощи запроса <xref:System.Activities.Tracking.WorkflowInstanceQuery>, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-148">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <span data-ttu-id="1cc59-149"><xref:System.Activities.Tracking.ActivityStateQuery> - используйте этот запрос для отслеживания изменений жизненного цикла действий, составляющих экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1cc59-149"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="1cc59-150">Например, вы можете захотеть отследить каждый раз, когда действие "отправить электронное письмо" завершается в рамках экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1cc59-150">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="1cc59-151">Этот запрос необходим, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.ActivityStateRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-151">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="1cc59-152">Состояния, доступные для подписки, указаны в <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-152">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="1cc59-153">Конфигурация и код, используемые для подписки на записи отслеживания состояний действий при помощи запроса <xref:System.Activities.Tracking.ActivityStateQuery> для действия `SendEmailActivity`, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-153">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > <span data-ttu-id="1cc59-154">Если несколько элементов activityStateQuery имеют одинаковые имена, то только состояния в последнем элементе используются в профиле отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-154">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="1cc59-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - этот запрос позволяет отслеживать действие, запланированное к исполнению родительским действием.</span><span class="sxs-lookup"><span data-stu-id="1cc59-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1cc59-156">Этот запрос необходимо, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.ActivityScheduledRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-156">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="1cc59-157">Конфигурация и код, используемые для подписки на записи, связанные с дочерним действием `SendEmailActivity`, планируемым при помощи запроса <xref:System.Activities.Tracking.ActivityScheduledQuery>, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-157">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="1cc59-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - используйте такой запрос для отслеживания обработки ошибок, возникающих во время действия.</span><span class="sxs-lookup"><span data-stu-id="1cc59-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1cc59-159">Этот запрос необходимо, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-159">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="1cc59-160">Конфигурация и код, используемые для подписки на записи, связанные с распространением ошибок при помощи запроса <xref:System.Activities.Tracking.FaultPropagationQuery>, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-160">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <span data-ttu-id="1cc59-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - используйте этот запрос для отслеживания запросов по отмене дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="1cc59-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1cc59-162">Этот запрос необходимо, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.CancelRequestedRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-162">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="1cc59-163">В следующем примере показана конфигурация и код, используемые для подписки на записи, связанные с отменой действий с помощью <xref:System.Activities.Tracking.CancelRequestedQuery> .</span><span class="sxs-lookup"><span data-stu-id="1cc59-163">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="1cc59-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - используйте этот запрос для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="1cc59-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="1cc59-165">Этот запрос необходимо, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.CustomTrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-165">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="1cc59-166">Конфигурация и код, используемые для подписки на записи, связанные с пользовательскими записями отслеживания при помощи запроса <xref:System.Activities.Tracking.CustomTrackingQuery>, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-166">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="1cc59-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - используйте этот запрос для отслеживания возобновления закладки в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1cc59-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1cc59-168">Этот запрос необходим, чтобы участник <xref:System.Activities.Tracking.TrackingParticipant> мог подписаться на объекты <xref:System.Activities.Tracking.BookmarkResumptionRecord>.</span><span class="sxs-lookup"><span data-stu-id="1cc59-168">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="1cc59-169">Конфигурация и код, используемые для подписки на записи, связанные с возобновлением закладок при помощи запроса <xref:System.Activities.Tracking.BookmarkResumptionQuery>, показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-169">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a><span data-ttu-id="1cc59-170">Заметки</span><span class="sxs-lookup"><span data-stu-id="1cc59-170">Annotations</span></span>

<span data-ttu-id="1cc59-171">Заметки позволяют произвольно добавлять теги для записей отслеживания со значением, которое можно изменить после построения.</span><span class="sxs-lookup"><span data-stu-id="1cc59-171">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="1cc59-172">Например, может потребоваться, чтобы несколько записей отслеживания в нескольких рабочих процессах были помечены как "почтовый сервер" = = "почта Server1".</span><span class="sxs-lookup"><span data-stu-id="1cc59-172">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="1cc59-173">Это упростит поиск всех записей с этим тегом при последующем составлении запроса записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-173">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="1cc59-174">Для этого к запросу отслеживания добавляется заметка, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1cc59-174">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="1cc59-175">Создание профиля отслеживания</span><span class="sxs-lookup"><span data-stu-id="1cc59-175">How to Create a Tracking Profile</span></span>

<span data-ttu-id="1cc59-176">Элементы отслеживания запросов используются для создания профиля отслеживания с помощью XML-файла конфигурации или [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] кода.</span><span class="sxs-lookup"><span data-stu-id="1cc59-176">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="1cc59-177">Ниже приводится пример профиля отслеживания, созданного при помощи файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1cc59-177">Here is an example of a tracking profile created using a configuration file.</span></span>

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> <span data-ttu-id="1cc59-178">Для WF с использованием узла служб рабочих процессов профиль отслеживания обычно создается при помощи файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1cc59-178">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="1cc59-179">Также можно создать профиль отслеживания при помощи кода, используя профиль отслеживания и API-интерфейс запросов отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-179">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="1cc59-180">Профиль, настроенный как XML-файл конфигурации, применяется к участнику отслеживания при помощи расширения поведения.</span><span class="sxs-lookup"><span data-stu-id="1cc59-180">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="1cc59-181">Он добавляется к WorkflowServiceHost, как описано в следующем разделе [Настройка отслеживания для рабочего процесса](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1cc59-181">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="1cc59-182">Детализация записей отслеживания, создаваемых узлом, определяется параметрами конфигурации в профиле отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-182">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="1cc59-183">Участник отслеживания подписывается на записи отслеживания путем добавления запросов в профиль отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-183">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="1cc59-184">Чтобы подписываться на все записи отслеживания, профиль отслеживания должен указать все запросы отслеживания, используя " \* " в полях "имя" в каждом запросе.</span><span class="sxs-lookup"><span data-stu-id="1cc59-184">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="1cc59-185">Ниже приводятся некоторые распространенные примеры профилей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-185">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="1cc59-186">Профиль отслеживания для получения записей экземпляра рабочего процесса и ошибок.</span><span class="sxs-lookup"><span data-stu-id="1cc59-186">A tracking profile to obtain workflow instance records and faults.</span></span>

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- <span data-ttu-id="1cc59-187">Профиль отслеживания для получения всех пользовательских записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1cc59-187">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="1cc59-188">См. также</span><span class="sxs-lookup"><span data-stu-id="1cc59-188">See also</span></span>

- [<span data-ttu-id="1cc59-189">Отслеживание SQL</span><span class="sxs-lookup"><span data-stu-id="1cc59-189">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="1cc59-190">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1cc59-190">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="1cc59-191">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1cc59-191">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
