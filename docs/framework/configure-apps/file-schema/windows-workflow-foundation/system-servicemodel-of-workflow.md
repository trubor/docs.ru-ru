---
description: 'Дополнительные сведения: <System. serviceModel> рабочего процесса'
title: <> System. serviceModel рабочего процесса
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 393c1055d6b136ed27a297e00133f5b53d12fd38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681751"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="a5c6c-103">\<system.serviceModel> рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="a5c6c-103">\<system.serviceModel> of workflow</span></span>

<span data-ttu-id="a5c6c-104">В этом разделе конфигурации содержатся все элементы конфигурации рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a5c6c-104">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="a5c6c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5c6c-105">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore
          connectionStringName="String"
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>
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
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5c6c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a5c6c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a5c6c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a5c6c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5c6c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a5c6c-108">Attributes</span></span>  

 <span data-ttu-id="a5c6c-109">None</span><span class="sxs-lookup"><span data-stu-id="a5c6c-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5c6c-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a5c6c-110">Child Elements</span></span>  
  
|<span data-ttu-id="a5c6c-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="a5c6c-111">Element</span></span>|<span data-ttu-id="a5c6c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="a5c6c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="a5c6c-113">В этом разделе определяется коллекция **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="a5c6c-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="a5c6c-114">Каждый элемент в коллекции определяет элементы поведения, используемые службами.</span><span class="sxs-lookup"><span data-stu-id="a5c6c-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="a5c6c-115">Каждый элемент поведения определяется с помощью уникального атрибута **имени** .</span><span class="sxs-lookup"><span data-stu-id="a5c6c-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="a5c6c-116">Представляет раздел конфигурации для определения настроек отслеживания для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a5c6c-116">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="a5c6c-117">Дополнительные сведения об отслеживании рабочих процессов и его конфигурации см. в разделе Отслеживание рабочего процесса [и трассировка](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) и [Настройка отслеживания рабочего процесса](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a5c6c-117">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5c6c-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a5c6c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a5c6c-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="a5c6c-119">Element</span></span>|<span data-ttu-id="a5c6c-120">Описание</span><span class="sxs-lookup"><span data-stu-id="a5c6c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="a5c6c-121">Корневой элемент для всех элементов конфигурации в файле конфигурации .NET.</span><span class="sxs-lookup"><span data-stu-id="a5c6c-121">The root element for all configuration elements in a .NET configuration file.</span></span>|
