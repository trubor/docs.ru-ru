---
description: 'Дополнительные сведения о: <participants> из WCF'
title: <participants> WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 4e0285025864a8c70c75bc409a79bc61002f29a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683831"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="1a9da-103">\<participants> WCF</span><span class="sxs-lookup"><span data-stu-id="1a9da-103">\<participants> of WCF</span></span>

<span data-ttu-id="1a9da-104">Настройте список участников отслеживания, которые будут прослушивать записи отслеживания, прямо исходящие из среды выполнения, и обрабатывать их (в зависимости от настройки).</span><span class="sxs-lookup"><span data-stu-id="1a9da-104">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="1a9da-105">Включает запись результата в определенном виде (например, в виде файла, консоли, ETW), обработку или сбор записей или любое другое требуемое сочетание.</span><span class="sxs-lookup"><span data-stu-id="1a9da-105">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="1a9da-106">Дополнительные сведения об участниках отслеживания и отслеживания рабочих процессов см. в статье участники [отслеживания рабочих процессов и трассировки](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) и [отслеживания](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="1a9da-106">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="1a9da-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a9da-107">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a9da-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1a9da-108">Attributes and Elements</span></span>  

 <span data-ttu-id="1a9da-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1a9da-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a9da-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1a9da-110">Attributes</span></span>  

 <span data-ttu-id="1a9da-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1a9da-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a9da-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1a9da-112">Child Elements</span></span>  
  
|<span data-ttu-id="1a9da-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="1a9da-113">Element</span></span>|<span data-ttu-id="1a9da-114">Описание</span><span class="sxs-lookup"><span data-stu-id="1a9da-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="1a9da-115">Содержит настройки участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1a9da-115">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a9da-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1a9da-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1a9da-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="1a9da-117">Element</span></span>|<span data-ttu-id="1a9da-118">Описание</span><span class="sxs-lookup"><span data-stu-id="1a9da-118">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="1a9da-119">Представляет раздел конфигурации для определения настроек отслеживания для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1a9da-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a9da-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a9da-120">Remarks</span></span>  

 <span data-ttu-id="1a9da-121">Участники отслеживания используются для выдачи данных отслеживания из рабочего процесса и их сохранения на различные носители.</span><span class="sxs-lookup"><span data-stu-id="1a9da-121">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="1a9da-122">Подобным образом любая последующая обработка записей отслеживания также может быть выполнена внутри участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1a9da-122">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="1a9da-123">События отслеживания могут использоваться несколькими участниками отслеживания одновременно.</span><span class="sxs-lookup"><span data-stu-id="1a9da-123">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="1a9da-124">Каждый участник отслеживания может быть связан с отдельным профилем отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1a9da-124">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="1a9da-125">Имеется стандартный участник отслеживания, который вносит записи отслеживания в сеанс ETW.</span><span class="sxs-lookup"><span data-stu-id="1a9da-125">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1a9da-126">Участник настраивается в службе рабочего процесса путем добавления в файл конфигурации поведения, связанного с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="1a9da-126">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="1a9da-127">Включив участника отслеживания ETW, можно будет просматривать записи отслеживания в обозревателе событий.</span><span class="sxs-lookup"><span data-stu-id="1a9da-127">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="1a9da-128">Если это не отвечает заданным требованиям, то можно создать своего собственного участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1a9da-128">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a9da-129">Пример</span><span class="sxs-lookup"><span data-stu-id="1a9da-129">Example</span></span>  

 <span data-ttu-id="1a9da-130">В следующем примере конфигурации показан стандартный участник отслеживания ETW, который настраивается в файле Web.config.</span><span class="sxs-lookup"><span data-stu-id="1a9da-130">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="1a9da-131">Идентификатор поставщика, который используется участником отслеживания ETW для внесения записей отслеживания в ETW, задан в разделе `<diagnostics>`.</span><span class="sxs-lookup"><span data-stu-id="1a9da-131">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="1a9da-132">Участник отслеживания имеет связанный с ним профиль для указания записей отслеживания, на которые он подписан.</span><span class="sxs-lookup"><span data-stu-id="1a9da-132">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="1a9da-133">Это определяется атрибутом `profileName` элемента `<add>`.</span><span class="sxs-lookup"><span data-stu-id="1a9da-133">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="1a9da-134">После их определения участник отслеживания добавляется к поведению службы `<etwTracking>`.</span><span class="sxs-lookup"><span data-stu-id="1a9da-134">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="1a9da-135">При этом выбранные участники отслеживания добавляются в расширения экземпляра рабочего процесса, чтобы они начали получать записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1a9da-135">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1a9da-136">См. также</span><span class="sxs-lookup"><span data-stu-id="1a9da-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="1a9da-137">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="1a9da-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1a9da-138">Участники отслеживания</span><span class="sxs-lookup"><span data-stu-id="1a9da-138">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
