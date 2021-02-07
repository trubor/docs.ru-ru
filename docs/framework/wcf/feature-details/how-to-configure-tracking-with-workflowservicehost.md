---
description: Дополнительные сведения см. в статье Настройка отслеживания с помощью WorkflowServiceHost.
title: Практическое руководство. Как настроить отслеживание с помощью WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 11c48c3989ab9b788c1e6834d8cbfe53e2b8a53e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734832"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="f6b2c-103">Практическое руководство. Как настроить отслеживание с помощью WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="f6b2c-103">How to: Configure Tracking with WorkflowServiceHost</span></span>

<span data-ttu-id="f6b2c-104">В этом разделе описывается настройка отслеживания для рабочего процесса платформы [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], размещенного в <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-104">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="f6b2c-105">Она осуществляется с помощью файла Web.config, в котором задается поведение службы.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-105">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="f6b2c-106">Настройка отслеживания в конфигурации</span><span class="sxs-lookup"><span data-stu-id="f6b2c-106">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="f6b2c-107">Добавьте <xref:System.Activities.Tracking.EtwTrackingParticipant> с помощью элемента <`behavior`> в файл конфигурации, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-107">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="f6b2c-108">В предыдущем образце конфигурации используется упрощенная конфигурация.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-108">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="f6b2c-109">Дополнительные сведения см. в разделе [упрощенная конфигурация](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-109">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="f6b2c-110">В предыдущем образце конфигурации добавляется участник <xref:System.Activities.Tracking.EtwTrackingParticipant> и задается имя профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-110">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="f6b2c-111">Профили отслеживания создаются в элементе <`trackingProfile`> в `tracking` элементе <>.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-111">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="f6b2c-112">Профиль отслеживания содержит запросы отслеживания, позволяющие участнику отслеживания подписываться на события рабочего процесса, создаваемые в момент изменения состояния экземпляра рабочего процесса в ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-112">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="f6b2c-113">Создание профиля отслеживания показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-113">The following example shows how to create a tracking profile.</span></span>  
  
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
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="f6b2c-114">Дополнительные сведения о профилях отслеживания см. в разделе [Профили отслеживания](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-114">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="f6b2c-115">Дополнительные сведения об отслеживании в целом см. в разделе [Отслеживание и трассировка рабочих процессов](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-115">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="f6b2c-116">Настройка отслеживания в коде</span><span class="sxs-lookup"><span data-stu-id="f6b2c-116">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="f6b2c-117">С помощью объекта <xref:System.Activities.Tracking.EtwTrackingParticipant> добавьте в код участника <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-117">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="f6b2c-118">В предыдущем образце кода добавляется участник <xref:System.Activities.Tracking.EtwTrackingParticipant> и задается имя профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-118">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="f6b2c-119">Профили отслеживания создаются в элементе <`trackingProfile`> в `tracking` элементе <>, как показано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-119">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="f6b2c-120">Дополнительные сведения о профилях отслеживания см. в разделе [Профили отслеживания](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-120">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="f6b2c-121">Дополнительные сведения об отслеживании в целом см. в разделе [Отслеживание и трассировка рабочих процессов](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-121">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="f6b2c-122">Пример настройки отслеживания программным способом см. в разделе [Настройка отслеживания для рабочего процесса](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-122">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b2c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="f6b2c-123">See also</span></span>

- [<span data-ttu-id="f6b2c-124">Упрощенная конфигурация служб WCF</span><span class="sxs-lookup"><span data-stu-id="f6b2c-124">Simplified Configuration for WCF Services</span></span>](../samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="f6b2c-125">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f6b2c-125">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="f6b2c-126">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="f6b2c-126">Tracking Profiles</span></span>](../../windows-workflow-foundation/tracking-profiles.md)
