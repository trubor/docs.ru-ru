---
description: Дополнительные сведения см. в статье как настроить поведение при простое с помощью WorkflowServiceHost.
title: Практическое руководство. Как настроить неактивное поведение с помощью WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 530ab1833f3f8bb91d39b19161070bc75c45f11a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780054"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="47c79-103">Практическое руководство. Как настроить неактивное поведение с помощью WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="47c79-103">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="47c79-104">Рабочие процессы переходят в режим бездействия, когда обнаруживают закладку, выполнение которой должно быть возобновлено по внешнему сигналу, например когда экземпляр рабочего процесса ожидает доставки сообщения с помощью действия <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="47c79-104">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="47c79-105">Поведение<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> позволяет задать время между переходом экземпляра службы в неактивное состояние и его сохранением или выгрузкой.</span><span class="sxs-lookup"><span data-stu-id="47c79-105"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="47c79-106">Содержит два свойства, которые позволяют задавать значения для этих периодов времени.</span><span class="sxs-lookup"><span data-stu-id="47c79-106">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="47c79-107">Атрибут<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> определяет период времени между переходом экземпляра службы Workflow Service в состояние бездействия и сохранением экземпляра службы Workflow Service.</span><span class="sxs-lookup"><span data-stu-id="47c79-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="47c79-108">Свойство<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> определяет период времени между переходом экземпляра службы Workflow Service в состояние бездействия и моментом выгрузки экземпляра рабочего процесса, где выгрузка означает сохранение экземпляра в хранилище экземпляров с удалением из памяти.</span><span class="sxs-lookup"><span data-stu-id="47c79-108"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="47c79-109">В этом разделе описана настройка <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="47c79-109">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="47c79-110">Настройка WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="47c79-110">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="47c79-111">Добавьте `workflowIdle` элемент> <в `behavior` элемент <> в элементе <`serviceBehaviors`>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="47c79-111">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="47c79-112">Атрибут `timeToUnload` определяет период времени между переходом экземпляра службы рабочего процесса в состояние бездействия и выгрузкой службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="47c79-112">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="47c79-113">Атрибут `timeToPersist` определяет период времени между переходом экземпляра службы рабочего процесса в состояние бездействия и сохранением экземпляра службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="47c79-113">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="47c79-114">Значение `timeToUnload` по умолчанию составляет 1 минуту.</span><span class="sxs-lookup"><span data-stu-id="47c79-114">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="47c79-115">По умолчанию для объекта `timeToPersist` установлено значение <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="47c79-115">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="47c79-116">Если ожидающие экземпляры нужно оставить в памяти, но сохранить для надежности, задайте значения так, чтобы выполнялось неравенство `timeToPersist` < `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="47c79-116">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="47c79-117">Если требуется, чтобы ожидающие экземпляры не выгружались, задайте параметру `timeToUnload` значение <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="47c79-117">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="47c79-118">Дополнительные сведения о см. в <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> разделе [Расширяемость узла службы рабочих процессов](workflow-service-host-extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="47c79-118">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="47c79-119">В предыдущем образце конфигурации используется упрощенная конфигурация.</span><span class="sxs-lookup"><span data-stu-id="47c79-119">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="47c79-120">Дополнительные сведения см. в разделе [упрощенная конфигурация](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="47c79-120">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="47c79-121">Изменение поведения во время ожидания в коде</span><span class="sxs-lookup"><span data-stu-id="47c79-121">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="47c79-122">В следующем примере программным способом изменяется время ожидания перед сохранением и выгрузкой.</span><span class="sxs-lookup"><span data-stu-id="47c79-122">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="47c79-123">См. также</span><span class="sxs-lookup"><span data-stu-id="47c79-123">See also</span></span>

- [<span data-ttu-id="47c79-124">Расширяемость узла службы рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="47c79-124">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="47c79-125">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="47c79-125">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="47c79-126">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="47c79-126">Workflow Services</span></span>](workflow-services.md)
