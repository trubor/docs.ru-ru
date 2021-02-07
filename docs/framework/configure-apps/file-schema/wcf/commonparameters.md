---
description: 'Дополнительные сведения: <commonParameters>'
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a9d230fb0f205315dc52357119e6b35752abc96d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698379"
---
# \<commonParameters>

<span data-ttu-id="3ad95-102">Представляет коллекцию параметров, используемых глобально в нескольких службах.</span><span class="sxs-lookup"><span data-stu-id="3ad95-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="3ad95-103">Эта коллекция, как правило, включает строку подключения базы данных, которая может совместно использоваться постоянными службами.</span><span class="sxs-lookup"><span data-stu-id="3ad95-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="3ad95-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ad95-104">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ad95-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3ad95-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3ad95-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3ad95-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ad95-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3ad95-107">Attributes</span></span>  

 <span data-ttu-id="3ad95-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3ad95-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ad95-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3ad95-109">Child Elements</span></span>  
  
|<span data-ttu-id="3ad95-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="3ad95-110">Element</span></span>|<span data-ttu-id="3ad95-111">Описание</span><span class="sxs-lookup"><span data-stu-id="3ad95-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="3ad95-112">Добавляет в коллекцию пару общих параметров вида «имя-значение», используемых службами.</span><span class="sxs-lookup"><span data-stu-id="3ad95-112">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ad95-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3ad95-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3ad95-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="3ad95-114">Element</span></span>|<span data-ttu-id="3ad95-115">Описание</span><span class="sxs-lookup"><span data-stu-id="3ad95-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="3ad95-116">Задает параметры экземпляра <xref:System.Workflow.Runtime.WorkflowRuntime> для размещения служб Windows Communication Foundation (WCF) на основе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="3ad95-116">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ad95-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ad95-117">Remarks</span></span>  

 <span data-ttu-id="3ad95-118">Элемент `<commonParameters>` определяет любые параметры, которые используются глобально несколькими службами, например `ConnectionString` при использовании <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="3ad95-118">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ad95-119">Служба отслеживания SQL не использует постоянно значение `ConnectionString`, если оно задано в разделе `<commonParameters>`.</span><span class="sxs-lookup"><span data-stu-id="3ad95-119">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="3ad95-120">В некоторых операциях, например при извлечении свойства `StateMachineWorkflowInstance.StateHistory`, может произойти ошибка.</span><span class="sxs-lookup"><span data-stu-id="3ad95-120">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="3ad95-121">Чтобы обойти эту проблему, задайте атрибут `ConnectionString` в разделе конфигурации для поставщика отслеживания, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3ad95-121">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="3ad95-122">Для служб, фиксирующих рабочие пакеты в постоянных хранилищах, таких как <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> и <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, можно включить режим повторения попытки транзакции, используя параметр `EnableRetries`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3ad95-122">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="3ad95-123">Обратите внимание, что `EnableRetries` параметр можно задать либо на глобальном уровне (как показано в разделе *общиепараметры* ), либо в отдельных службах, которые поддерживают `EnableRetries` (как показано в разделе *службы* ).</span><span class="sxs-lookup"><span data-stu-id="3ad95-123">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="3ad95-124">В следующем примере кода показано, как программно изменить общие параметры:</span><span class="sxs-lookup"><span data-stu-id="3ad95-124">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="3ad95-125">Дополнительные сведения об использовании файла конфигурации для управления поведением <xref:System.Workflow.Runtime.WorkflowRuntime> объекта Windows Workflow Foundation ведущего приложения см. в разделе [файлы конфигурации рабочего процесса](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3ad95-125">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad95-126">Пример</span><span class="sxs-lookup"><span data-stu-id="3ad95-126">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="3ad95-127">См. также</span><span class="sxs-lookup"><span data-stu-id="3ad95-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="3ad95-128">[Файлы конфигурации рабочих процессов](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3ad95-128">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
