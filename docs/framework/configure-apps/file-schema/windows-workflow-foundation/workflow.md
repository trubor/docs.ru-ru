---
description: 'Дополнительные сведения: <workflow>'
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 2d35f03c2715fcba7cf868a3550855066d747d82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697976"
---
# \<workflow>

<span data-ttu-id="d9e80-102">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9e80-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d9e80-103">Дополнительные сведения об отслеживании рабочих процессов и его конфигурации см. в разделе [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Track Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d9e80-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**  
  
## <a name="syntax"></a><span data-ttu-id="d9e80-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9e80-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9e80-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d9e80-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d9e80-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d9e80-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9e80-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d9e80-107">Attributes</span></span>  
  
|<span data-ttu-id="d9e80-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d9e80-108">Attribute</span></span>|<span data-ttu-id="d9e80-109">Описание</span><span class="sxs-lookup"><span data-stu-id="d9e80-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9e80-110">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="d9e80-110">activityDefinitionId</span></span>|<span data-ttu-id="d9e80-111">Строка, указывающая идентификатор определения действия отслеживаемого рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-111">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9e80-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d9e80-112">Child Elements</span></span>  
  
|<span data-ttu-id="d9e80-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="d9e80-113">Element</span></span>|<span data-ttu-id="d9e80-114">Описание</span><span class="sxs-lookup"><span data-stu-id="d9e80-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|<span data-ttu-id="d9e80-115">Представляет коллекцию запросов, которые используются для отслеживания действия, выполнение которого запланировано родительским действием.</span><span class="sxs-lookup"><span data-stu-id="d9e80-115">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d9e80-116">Этот запрос необходим, чтобы участник отслеживания подписался на записи запланированных действий.</span><span class="sxs-lookup"><span data-stu-id="d9e80-116">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[\<activityStateQueries>](activitystatequeries.md)|<span data-ttu-id="d9e80-117">Представляет коллекцию запросов, которые используются для отслеживания изменений жизненного цикла действий, составляющих экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-117">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d9e80-118">Например, вы можете захотеть отследить каждый раз, когда действие "отправить электронное письмо" завершается в рамках экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-118">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d9e80-119">Этот запрос необходим, чтобы участник отслеживания мог подписываться на объекты записей состояния действия.</span><span class="sxs-lookup"><span data-stu-id="d9e80-119">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d9e80-120">Состояния, доступные для подписки, указаны в ActivtyStates.</span><span class="sxs-lookup"><span data-stu-id="d9e80-120">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="d9e80-121">Представляет коллекцию запросов, используемых для отслеживания возобновления чтения с закладок в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-121">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d9e80-122">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="d9e80-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|<span data-ttu-id="d9e80-123">Представляет коллекцию запросов, используемых для отслеживания запросов по отмене дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="d9e80-123">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d9e80-124">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="d9e80-124">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[\<customTrackingQueries>](customtrackingqueries.md)|<span data-ttu-id="d9e80-125">Представляет коллекцию запросов, используемых для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="d9e80-125">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d9e80-126">Запрос необходим, чтобы участник отслеживания подписался на пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d9e80-126">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="d9e80-127">Представляет коллекцию запросов, которые используются для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="d9e80-127">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="d9e80-128">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="d9e80-128">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="d9e80-129">Такой запрос следует использовать для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="d9e80-129">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="d9e80-130">Этот запрос необходим, чтобы участник отслеживания подписался на записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="d9e80-130">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="d9e80-131">Представляет коллекцию элементов конфигурации, которые отслеживают изменения жизненного цикла экземпляра рабочего процесса, например события «запущен» или «завершен».</span><span class="sxs-lookup"><span data-stu-id="d9e80-131">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9e80-132">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d9e80-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d9e80-133">Элемент</span><span class="sxs-lookup"><span data-stu-id="d9e80-133">Element</span></span>|<span data-ttu-id="d9e80-134">Описание</span><span class="sxs-lookup"><span data-stu-id="d9e80-134">Description</span></span>|  
|-------------|-----------------|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="d9e80-135">Представляет раздел конфигурации для создания подписки на записи отслеживания рабочего процесса в участнике отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d9e80-135">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="d9e80-136">Профиль отслеживания содержит запросы отслеживания, позволяющие участнику отслеживания подписываться на события рабочего процесса, формируемые во время выполнения при изменении состояния экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-136">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d9e80-137">Запросы, заданные в разделе профиля отслеживания, определяют виды событий, возвращаемых подпиской.</span><span class="sxs-lookup"><span data-stu-id="d9e80-137">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e80-138">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9e80-138">Remarks</span></span>  

 <span data-ttu-id="d9e80-139">Профили отслеживания содержат запросы отслеживания, позволяющие участнику отслеживания подписываться на события рабочего процесса, создаваемые в результате изменения состояния экземпляра рабочего процесса в ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="d9e80-139">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="d9e80-140">Этот элемент конфигурации определяет отслеживаемый экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d9e80-140">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="d9e80-141">Исходя из потребностей, можно написать профиль с низкой детализацией, который будет подписан на небольшой набор изменений состояния высокого уровня в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="d9e80-141">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d9e80-142">И наоборот, можно создать очень детальный профиль, результирующие события которого будут достаточно подробными для последующего воспроизведения всего потока выполнения.</span><span class="sxs-lookup"><span data-stu-id="d9e80-142">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="d9e80-143">Профили отслеживания структурированы в форме объявляющих подписок на записи отслеживания, которые позволяют выполнять запросы к среде выполнения рабочего процесса в отношении определенных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d9e80-143">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="d9e80-144">Существует множество типов запросов, которые позволяют подписаться на различные классы записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d9e80-144">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="d9e80-145">Полный список запросов см. в списке дочерних элементов этого раздела и [профилях отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d9e80-145">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="d9e80-146">В следующем примере показан профиль отслеживания в файле конфигурации, который позволяет участнику отслеживания подписываться на `Started` `Completed` события рабочего процесса и.</span><span class="sxs-lookup"><span data-stu-id="d9e80-146">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>
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
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9e80-147">См. также</span><span class="sxs-lookup"><span data-stu-id="d9e80-147">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="d9e80-148">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="d9e80-148">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d9e80-149">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="d9e80-149">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
