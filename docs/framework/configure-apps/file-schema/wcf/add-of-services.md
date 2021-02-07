---
description: 'Дополнительные сведения <add> о: <services>'
title: <add> из <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 868a4ef9fafcc42ca4620880b2c6f1cb499cab4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750030"
---
# <a name="add-of-services"></a><span data-ttu-id="9d6c2-103">\<add> из \<services></span><span class="sxs-lookup"><span data-stu-id="9d6c2-103">\<add> of \<services></span></span>

<span data-ttu-id="9d6c2-104">Задает параметры экземпляра <xref:System.Workflow.Runtime.WorkflowRuntime> для размещения служб Windows Communication Foundation (WCF) на основе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-104">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="9d6c2-105">Это элемент типа <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-105">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9d6c2-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d6c2-106">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d6c2-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9d6c2-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9d6c2-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d6c2-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9d6c2-109">Attributes</span></span>  
  
|<span data-ttu-id="9d6c2-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9d6c2-110">Attribute</span></span>|<span data-ttu-id="9d6c2-111">Описание</span><span class="sxs-lookup"><span data-stu-id="9d6c2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d6c2-112">type</span><span class="sxs-lookup"><span data-stu-id="9d6c2-112">type</span></span>|<span data-ttu-id="9d6c2-113">Строка, задающая имя типа с указанием сборки для службы, которую необходимо инициализировать.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-113">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="9d6c2-114">Заданная служба должна соответствовать определенным правилам, связанным с сигнатурами их конструкторов.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-114">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d6c2-115">Подробнее см. в разделе <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-115">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d6c2-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9d6c2-116">Child Elements</span></span>  

 <span data-ttu-id="9d6c2-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d6c2-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9d6c2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9d6c2-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="9d6c2-119">Element</span></span>|<span data-ttu-id="9d6c2-120">Описание</span><span class="sxs-lookup"><span data-stu-id="9d6c2-120">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="9d6c2-121">Коллекция служб, добавляемая в механизм <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-121">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="9d6c2-122">Элементы имеют тип <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-122">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="9d6c2-123">Службы, указанные в коллекции, инициализируются механизмом среды выполнения рабочих процессов и добавляются в службы при вызове соответствующего конструктора <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-123">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9d6c2-124">Таким образом, службы, указанные в коллекции, должны отвечать определенным правилам в отношении сигнатур конструкторов.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-124">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d6c2-125">Подробнее см. в разделе <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-125">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6c2-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="9d6c2-126">Remarks</span></span>  

 <span data-ttu-id="9d6c2-127">Служба, указанная в данном элементе, инициализируется механизмом среды выполнения рабочих процессов и добавляется в службы при вызове соответствующего конструктора <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-127">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9d6c2-128">Поэтому заданная служба должна соответствовать определенным правилам, относящимся к сигнатурам конструкторов.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-128">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d6c2-129">Подробнее см. в разделе <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-129">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d6c2-130">Пример</span><span class="sxs-lookup"><span data-stu-id="9d6c2-130">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="9d6c2-131">См. также</span><span class="sxs-lookup"><span data-stu-id="9d6c2-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="9d6c2-132">[Файлы конфигурации рабочих процессов](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9d6c2-132">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
