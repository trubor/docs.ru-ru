---
description: 'Дополнительные сведения о: <tracking> из WCF'
title: <tracking> WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e372139623cd0b92bde74a6b19761d8a4c5ad6db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773827"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="0fa5c-103">\<tracking> WCF</span><span class="sxs-lookup"><span data-stu-id="0fa5c-103">\<tracking> of WCF</span></span>

<span data-ttu-id="0fa5c-104">Представляет раздел конфигурации для определения настроек отслеживания для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-104">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="0fa5c-105">Дополнительные сведения об отслеживании рабочих процессов и его конфигурации см. в разделе Отслеживание рабочего процесса [и трассировка](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) и [Настройка отслеживания рабочего процесса](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="0fa5c-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="0fa5c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fa5c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
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
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fa5c-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0fa5c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="0fa5c-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fa5c-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0fa5c-109">Attributes</span></span>  

 <span data-ttu-id="0fa5c-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fa5c-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0fa5c-111">Child Elements</span></span>  
  
|<span data-ttu-id="0fa5c-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="0fa5c-112">Element</span></span>|<span data-ttu-id="0fa5c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="0fa5c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="0fa5c-114">Коллекция элементов конфигурации, которые определяют участников, подписанных на записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-114">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="0fa5c-115">Участники содержат логику обработки полезных данных из записей отслеживания (например, они могут записать данные в файл).</span><span class="sxs-lookup"><span data-stu-id="0fa5c-115">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="0fa5c-116">Профиль отслеживания для фильтрации записей отслеживания, выдаваемых экземпляром рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-116">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fa5c-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0fa5c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0fa5c-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="0fa5c-118">Element</span></span>|<span data-ttu-id="0fa5c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="0fa5c-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fa5c-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0fa5c-120">system.ServiceModel</span></span>|<span data-ttu-id="0fa5c-121">Корневой элемент всех элементов конфигурации рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fa5c-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="0fa5c-122">Remarks</span></span>  

 <span data-ttu-id="0fa5c-123">Отслеживание позволяет исследовать выполнение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-123">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="0fa5c-124">Инфраструктура отслеживания рабочего процесса инструментирует процесс таким образом, что выдаются записи, отражающие ключевые события выполнения.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-124">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="0fa5c-125">Например, записи отслеживания создаются при запуске и завершении экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-125">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="0fa5c-126">Отслеживание также позволяет извлекать важные бизнес-данные, связанные с переменными рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-126">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="0fa5c-127">Например, если рабочий процесс представляет собой систему обработки заказов, то вместе с записью отслеживания можно извлечь идентификатор заказа.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-127">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="0fa5c-128">В общем, функции отслеживания WF обеспечивают диагностику и анализ исполнения рабочих задач.</span><span class="sxs-lookup"><span data-stu-id="0fa5c-128">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa5c-129">См. также</span><span class="sxs-lookup"><span data-stu-id="0fa5c-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="0fa5c-130">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="0fa5c-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
