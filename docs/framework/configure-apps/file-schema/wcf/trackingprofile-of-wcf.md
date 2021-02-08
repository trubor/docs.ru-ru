---
description: 'Дополнительные сведения о: <trackingProfile> из WCF'
title: <trackingProfile> WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: d896457f45905739abd61892ac6058ddfc0f5034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773775"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="4ce0e-103">\<trackingProfile> WCF</span><span class="sxs-lookup"><span data-stu-id="4ce0e-103">\<trackingProfile> of WCF</span></span>

<span data-ttu-id="4ce0e-104">Представляет раздел конфигурации для создания подписки на записи отслеживания рабочего процесса в участнике отслеживания.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-104">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="4ce0e-105">Профиль отслеживания содержит запросы отслеживания, позволяющие участнику отслеживания подписываться на события рабочего процесса, формируемые во время выполнения при изменении состояния экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-105">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="4ce0e-106">Запросы, заданные в разделе профиля отслеживания, определяют виды событий, возвращаемых подпиской.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-106">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="4ce0e-107">Дополнительные сведения об отслеживании рабочих процессов и его конфигурации см. в разделе [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Track Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4ce0e-107">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="4ce0e-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ce0e-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ce0e-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4ce0e-109">Attributes and Elements</span></span>  

<span data-ttu-id="4ce0e-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ce0e-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4ce0e-111">Attributes</span></span>  
  
|<span data-ttu-id="4ce0e-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4ce0e-112">Attribute</span></span>|<span data-ttu-id="4ce0e-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce0e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ce0e-114">name</span><span class="sxs-lookup"><span data-stu-id="4ce0e-114">name</span></span>|<span data-ttu-id="4ce0e-115">Строка, задающая имя профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-115">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ce0e-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4ce0e-116">Child Elements</span></span>  
  
|<span data-ttu-id="4ce0e-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="4ce0e-117">Element</span></span>|<span data-ttu-id="4ce0e-118">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce0e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="4ce0e-119">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-119">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ce0e-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4ce0e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ce0e-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="4ce0e-121">Element</span></span>|<span data-ttu-id="4ce0e-122">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce0e-122">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="4ce0e-123">Представляет раздел конфигурации для определения настроек отслеживания для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ce0e-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ce0e-124">Remarks</span></span>  

 <span data-ttu-id="4ce0e-125">Профиль отслеживания содержит запросы отслеживания, которые позволяют участнику подписываться на события рабочего потока, создаваемые при изменении состояния экземпляра рабочего процесса в ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-125">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="4ce0e-126">Исходя из потребностей, можно написать профиль с низкой детализацией, который будет подписан на небольшой набор изменений состояния высокого уровня в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-126">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="4ce0e-127">И наоборот, можно создать очень детальный профиль, результирующие события которого будут достаточно подробными для последующего воспроизведения всего потока выполнения.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-127">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="4ce0e-128">Профили отслеживания структурированы в форме объявляющих подписок на записи отслеживания, которые позволяют выполнять запросы к среде выполнения рабочего процесса в отношении определенных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-128">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="4ce0e-129">Существует несколько типов запросов, которые позволяют подписываться на разные классы <xref:System.Activities.Tracking.TrackingRecord> объектов.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-129">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="4ce0e-130">Полный список запросов см. в разделе [\<participants>](../windows-workflow-foundation/participants.md) и [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4ce0e-130">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="4ce0e-131">В следующем примере показан профиль отслеживания в файле конфигурации, который позволяет участнику отслеживания подписываться на `Started` `Completed` события рабочего процесса и.</span><span class="sxs-lookup"><span data-stu-id="4ce0e-131">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="4ce0e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="4ce0e-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="4ce0e-133">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="4ce0e-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ce0e-134">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="4ce0e-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
