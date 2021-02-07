---
description: 'Дополнительные сведения: <workflowRuntime>'
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 9c234073bbbbfc8f1b5bb1579ff1dfa54a744ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682224"
---
# \<workflowRuntime>

<span data-ttu-id="de857-102">Задает параметры экземпляра <xref:System.Workflow.Runtime.WorkflowRuntime> для размещения служб Windows Communication Foundation (WCF) на основе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="de857-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="de857-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de857-103">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de857-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="de857-104">Attributes and Elements</span></span>  

 <span data-ttu-id="de857-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="de857-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de857-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="de857-106">Attributes</span></span>  
  
|<span data-ttu-id="de857-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="de857-107">Attribute</span></span>|<span data-ttu-id="de857-108">Описание</span><span class="sxs-lookup"><span data-stu-id="de857-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de857-109">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="de857-109">cachedInstanceExpiration</span></span>|<span data-ttu-id="de857-110">Необязательное значение <xref:System.TimeSpan>, определяющее максимальный период времени, в течение которого экземпляр рабочего процесса может оставаться в памяти в неактивном состоянии до принудительной выгрузки или прекращения.</span><span class="sxs-lookup"><span data-stu-id="de857-110">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="de857-111">Если среда выполнения рабочего процесса имеет параметр `PersistenceService`, выполняющий unloadOnIdle, этот атрибут игнорируется.</span><span class="sxs-lookup"><span data-stu-id="de857-111">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="de857-112">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="de857-112">enablePerformanceCounters</span></span>|<span data-ttu-id="de857-113">Необязательное логическое значение, определяющее, включены ли счетчики производительности.</span><span class="sxs-lookup"><span data-stu-id="de857-113">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="de857-114">Счетчики производительности предоставляют статистические данные о различных рабочих процессах, но они могут вызывать снижение производительности при запуске подсистемы среды выполнения рабочего процесса и при выполнении экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="de857-114">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="de857-115">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="de857-115">The default value is `true`.</span></span>|  
|<span data-ttu-id="de857-116">name</span><span class="sxs-lookup"><span data-stu-id="de857-116">name</span></span>|<span data-ttu-id="de857-117">Строка, содержащая имя подсистемы среды выполнения рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="de857-117">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="de857-118">Имя используется в выходных данных для различения данной среды выполнения от других сред выполнения, которые могут выполняться в системе, например в счетчиках производительности.</span><span class="sxs-lookup"><span data-stu-id="de857-118">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="de857-119">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="de857-119">The default is an empty string.</span></span>|  
|<span data-ttu-id="de857-120">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="de857-120">validateOnCreate</span></span>|<span data-ttu-id="de857-121">Необязательное логическое значение, указывающее, будет ли выполняться проверка определения рабочего процесса при открытии WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="de857-121">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="de857-122">Если этому атрибуту задано значение `true`, проверка рабочего процесса выполняется при каждом вызове `WorkflowServiceHost.Open`.</span><span class="sxs-lookup"><span data-stu-id="de857-122">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="de857-123">В случае обнаружения ошибок проверки возникает ошибка <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException>.</span><span class="sxs-lookup"><span data-stu-id="de857-123">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="de857-124">Если это свойство имеет значение `false`, проверка определения рабочего процесса не выполняется.</span><span class="sxs-lookup"><span data-stu-id="de857-124">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="de857-125">Значение по умолчанию для этого свойства — `true`.</span><span class="sxs-lookup"><span data-stu-id="de857-125">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de857-126">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="de857-126">Child Elements</span></span>  
  
|<span data-ttu-id="de857-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="de857-127">Element</span></span>|<span data-ttu-id="de857-128">Описание</span><span class="sxs-lookup"><span data-stu-id="de857-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de857-129">commonParameters</span><span class="sxs-lookup"><span data-stu-id="de857-129">commonParameters</span></span>|<span data-ttu-id="de857-130">Коллекция общих параметров, используемых службой.</span><span class="sxs-lookup"><span data-stu-id="de857-130">A collection of common parameters used by services.</span></span> <span data-ttu-id="de857-131">Эта коллекция, как правило, включает строку подключения базы данных, которая может совместно использоваться постоянными службами.</span><span class="sxs-lookup"><span data-stu-id="de857-131">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="de857-132">services;</span><span class="sxs-lookup"><span data-stu-id="de857-132">services</span></span>|<span data-ttu-id="de857-133">Коллекция служб, добавляемая в механизм <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="de857-133">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="de857-134">Элементы имеют тип <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de857-134">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="de857-135">Службы, указанные в коллекции, инициализируются механизмом среды выполнения рабочих процессов и добавляются в службы при вызове соответствующего конструктора <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="de857-135">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="de857-136">Таким образом, службы, указанные в коллекции, должны отвечать определенным правилам в отношении сигнатур конструкторов.</span><span class="sxs-lookup"><span data-stu-id="de857-136">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="de857-137">Подробнее см. в разделе <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de857-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de857-138">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="de857-138">Parent Elements</span></span>  
  
|<span data-ttu-id="de857-139">Элемент</span><span class="sxs-lookup"><span data-stu-id="de857-139">Element</span></span>|<span data-ttu-id="de857-140">Описание</span><span class="sxs-lookup"><span data-stu-id="de857-140">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="de857-141">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="de857-141">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de857-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="de857-142">Remarks</span></span>  

 <span data-ttu-id="de857-143">Дополнительные сведения об использовании файла конфигурации для управления поведением <xref:System.Workflow.Runtime.WorkflowRuntime> объекта Windows Workflow Foundation ведущего приложения см. в разделе [файлы конфигурации рабочего процесса](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="de857-143">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de857-144">Пример</span><span class="sxs-lookup"><span data-stu-id="de857-144">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="de857-145">См. также</span><span class="sxs-lookup"><span data-stu-id="de857-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="de857-146">[Файлы конфигурации рабочих процессов](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de857-146">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
