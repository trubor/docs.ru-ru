---
description: 'Дополнительные сведения <add> о: <participants>'
title: <add> из <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 58e8fa9b0e9685421a044cf2f11473cb73d8ae6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748938"
---
# <a name="add-of-participants"></a><span data-ttu-id="79b53-103">\<add> из \<participants></span><span class="sxs-lookup"><span data-stu-id="79b53-103">\<add> of \<participants></span></span>

<span data-ttu-id="79b53-104">Настройте участника отслеживания, который будет прослушивать записи отслеживания, прямо исходящие из среды выполнения, и обрабатывать их (в зависимости от настройки).</span><span class="sxs-lookup"><span data-stu-id="79b53-104">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="79b53-105">Включает запись результата в определенном виде (например, в виде файла, консоли, ETW), обработку или сбор записей или любое другое требуемое сочетание.</span><span class="sxs-lookup"><span data-stu-id="79b53-105">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="79b53-106">Дополнительные сведения об участниках отслеживания и отслеживания рабочих процессов см. в статье участники [отслеживания рабочих процессов и трассировки](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) и [отслеживания](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="79b53-106">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="79b53-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79b53-107">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79b53-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="79b53-108">Attributes and Elements</span></span>  

 <span data-ttu-id="79b53-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="79b53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79b53-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="79b53-110">Attributes</span></span>  
  
|<span data-ttu-id="79b53-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="79b53-111">Element</span></span>|<span data-ttu-id="79b53-112">Описание</span><span class="sxs-lookup"><span data-stu-id="79b53-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79b53-113">name</span><span class="sxs-lookup"><span data-stu-id="79b53-113">name</span></span>|<span data-ttu-id="79b53-114">Строка, задающая имя участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-114">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="79b53-115">profileName</span><span class="sxs-lookup"><span data-stu-id="79b53-115">profileName</span></span>|<span data-ttu-id="79b53-116">Строка, задающая имя профиля отслеживания, который определяет, на какие записи отслеживания подписан участник.</span><span class="sxs-lookup"><span data-stu-id="79b53-116">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="79b53-117">тип</span><span class="sxs-lookup"><span data-stu-id="79b53-117">type</span></span>|<span data-ttu-id="79b53-118">Строка, задающая тип участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-118">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79b53-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="79b53-119">Child Elements</span></span>  

 <span data-ttu-id="79b53-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="79b53-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79b53-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="79b53-121">Parent Elements</span></span>  
  
|<span data-ttu-id="79b53-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="79b53-122">Element</span></span>|<span data-ttu-id="79b53-123">Описание</span><span class="sxs-lookup"><span data-stu-id="79b53-123">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="79b53-124">Список участников отслеживания</span><span class="sxs-lookup"><span data-stu-id="79b53-124">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79b53-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="79b53-125">Remarks</span></span>  

 <span data-ttu-id="79b53-126">Участники отслеживания используются для выдачи данных отслеживания из рабочего процесса и их сохранения на различные носители.</span><span class="sxs-lookup"><span data-stu-id="79b53-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="79b53-127">Подобным образом любая последующая обработка записей отслеживания также может быть выполнена внутри участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="79b53-128">События отслеживания могут использоваться несколькими участниками отслеживания одновременно.</span><span class="sxs-lookup"><span data-stu-id="79b53-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="79b53-129">Каждый участник отслеживания может быть связан с отдельным профилем отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="79b53-130">Имеется стандартный участник отслеживания, который вносит записи отслеживания в сеанс ETW.</span><span class="sxs-lookup"><span data-stu-id="79b53-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="79b53-131">Участник настраивается в службе рабочего процесса путем добавления в файл конфигурации поведения, связанного с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="79b53-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="79b53-132">Включив участника отслеживания ETW, можно будет просматривать записи отслеживания в обозревателе событий.</span><span class="sxs-lookup"><span data-stu-id="79b53-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="79b53-133">Если это не отвечает заданным требованиям, то можно создать своего собственного участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79b53-134">Пример</span><span class="sxs-lookup"><span data-stu-id="79b53-134">Example</span></span>  

 <span data-ttu-id="79b53-135">В следующем примере конфигурации показан стандартный участник отслеживания ETW, который настраивается в файле Web.config.</span><span class="sxs-lookup"><span data-stu-id="79b53-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="79b53-136">Идентификатор поставщика, используемый участником отслеживания ETW для записи записей отслеживания в ETW, определяется в **\<diagnostics>** разделе.</span><span class="sxs-lookup"><span data-stu-id="79b53-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="79b53-137">Участник отслеживания имеет связанный с ним профиль для указания записей отслеживания, на которые он подписан.</span><span class="sxs-lookup"><span data-stu-id="79b53-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="79b53-138">Это определяется атрибутом **filename** **\<add>** элемента.</span><span class="sxs-lookup"><span data-stu-id="79b53-138">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="79b53-139">После того как они определены, участник отслеживания добавляется к **\<etwTracking>** поведению службы.</span><span class="sxs-lookup"><span data-stu-id="79b53-139">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="79b53-140">При этом выбранные участники отслеживания добавляются в расширения экземпляра рабочего процесса, чтобы они начали получать записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="79b53-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
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
  
## <a name="see-also"></a><span data-ttu-id="79b53-141">См. также</span><span class="sxs-lookup"><span data-stu-id="79b53-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="79b53-142">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="79b53-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="79b53-143">Участники отслеживания</span><span class="sxs-lookup"><span data-stu-id="79b53-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
