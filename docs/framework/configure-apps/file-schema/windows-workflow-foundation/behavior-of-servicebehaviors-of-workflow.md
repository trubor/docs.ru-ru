---
description: 'Дополнительные сведения о: <behavior> из <serviceBehaviors> рабочего процесса'
title: <behavior> из <serviceBehaviors> рабочего процесса
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 7504e9b307286871440bb6efdb672a59d3d13cb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725289"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="dcd05-103">\<behavior> из \<serviceBehaviors> рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="dcd05-103">\<behavior> of \<serviceBehaviors> of workflow</span></span>

<span data-ttu-id="dcd05-104">Элемент **Behavior** содержит коллекцию параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="dcd05-104">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="dcd05-105">Каждое поведение индексируется по **имени**.</span><span class="sxs-lookup"><span data-stu-id="dcd05-105">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="dcd05-106">Службы могут ссылаться на каждое поведение с помощью этого имени, используя атрибут **behaviorConfiguration** [\<endpoint>](../wcf/endpoint-element.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="dcd05-106">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="dcd05-107">Это позволяет конечным точкам иметь общие конфигурации поведений без переопределения параметров.</span><span class="sxs-lookup"><span data-stu-id="dcd05-107">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="dcd05-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcd05-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd05-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="dcd05-109">Attributes and Elements</span></span>  

 <span data-ttu-id="dcd05-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="dcd05-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd05-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="dcd05-111">Attributes</span></span>  
  
|<span data-ttu-id="dcd05-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dcd05-112">Attribute</span></span>|<span data-ttu-id="dcd05-113">Описание</span><span class="sxs-lookup"><span data-stu-id="dcd05-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcd05-114">name</span><span class="sxs-lookup"><span data-stu-id="dcd05-114">name</span></span>|<span data-ttu-id="dcd05-115">Уникальная строка, содержащая имя конфигурации поведения.</span><span class="sxs-lookup"><span data-stu-id="dcd05-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="dcd05-116">Это значение является заданной пользователем строкой, которая должна быть уникальной, поскольку она действует как строка идентификации для элемента.</span><span class="sxs-lookup"><span data-stu-id="dcd05-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcd05-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="dcd05-117">Child Elements</span></span>  
  
|<span data-ttu-id="dcd05-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="dcd05-118">Element</span></span>|<span data-ttu-id="dcd05-119">Описание</span><span class="sxs-lookup"><span data-stu-id="dcd05-119">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="dcd05-120">Поведение, позволяющее службе рабочего процесса использовать обработку буфера получения, благодаря чему можно обрабатывать неупорядоченные сообщения.</span><span class="sxs-lookup"><span data-stu-id="dcd05-120">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="dcd05-121">Поведение службы позволяет ей использовать отслеживание ETW совместно с <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="dcd05-121">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="dcd05-122">Поведение службы, которое позволяет изменить уровни доступа к кэшу, параметры кэша фабрики канала и параметры кэша канала для рабочих процессов, которые отправляют сообщения в конечные точки служб с использованием действий отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="dcd05-122">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="dcd05-123">Поведение службы, позволяющее настроить функцию <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, поддерживающую сохранение сведений о состоянии для экземпляров службы рабочего процесса в базу данных SQL Server 2005 или SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dcd05-123">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="dcd05-124">Поведение службы, управляющее выгрузкой и сохранением простаивающих экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="dcd05-124">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="dcd05-125">Поведение службы, которое позволяет указать параметры, управляющие выполнением экземпляров рабочего процесса, включая сохраняемость, необработанное поведение исключения и неактивное поведение.</span><span class="sxs-lookup"><span data-stu-id="dcd05-125">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="dcd05-126">Поведение службы, позволяющее задать действие, которое будет выполнено при появлении необработанного исключения в службе рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="dcd05-126">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd05-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="dcd05-127">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd05-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="dcd05-128">Element</span></span>|<span data-ttu-id="dcd05-129">Описание</span><span class="sxs-lookup"><span data-stu-id="dcd05-129">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="dcd05-130">Коллекция элементов поведений службы.</span><span class="sxs-lookup"><span data-stu-id="dcd05-130">A collection of service behavior elements.</span></span>|
