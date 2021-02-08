---
description: 'Дополнительные сведения <add> о: <commonParameters>'
title: <add> из <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d7a1b78ed79b7eab472460b364b90bd372ecf6bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804014"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="e9382-103">\<add> из \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="e9382-103">\<add> of \<commonParameters></span></span>

<span data-ttu-id="e9382-104">Определяет пару параметров «имя-значение», которые используются глобально в нескольких службах.</span><span class="sxs-lookup"><span data-stu-id="e9382-104">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="e9382-105">Как правило, этот параметр включает строку подключения базы данных, которая может совместно использоваться долговременными службами.</span><span class="sxs-lookup"><span data-stu-id="e9382-105">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e9382-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9382-106">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9382-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e9382-107">Attributes and Elements</span></span>  

 <span data-ttu-id="e9382-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e9382-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9382-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e9382-109">Attributes</span></span>  
  
|<span data-ttu-id="e9382-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e9382-110">Attribute</span></span>|<span data-ttu-id="e9382-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e9382-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9382-112">name</span><span class="sxs-lookup"><span data-stu-id="e9382-112">name</span></span>|<span data-ttu-id="e9382-113">Имя параметра, заданного для службы.</span><span class="sxs-lookup"><span data-stu-id="e9382-113">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="e9382-114">значение</span><span class="sxs-lookup"><span data-stu-id="e9382-114">value</span></span>|<span data-ttu-id="e9382-115">Значение параметра, заданного для службы.</span><span class="sxs-lookup"><span data-stu-id="e9382-115">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9382-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e9382-116">Child Elements</span></span>  

 <span data-ttu-id="e9382-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e9382-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9382-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e9382-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e9382-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="e9382-119">Element</span></span>|<span data-ttu-id="e9382-120">Описание</span><span class="sxs-lookup"><span data-stu-id="e9382-120">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="e9382-121">Коллекция общих параметров, используемых службой.</span><span class="sxs-lookup"><span data-stu-id="e9382-121">A collection of common parameters used by services.</span></span> <span data-ttu-id="e9382-122">Эта коллекция, как правило, включает строку подключения базы данных, которая может совместно использоваться постоянными службами.</span><span class="sxs-lookup"><span data-stu-id="e9382-122">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9382-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="e9382-123">Remarks</span></span>  

 <span data-ttu-id="e9382-124">Элемент `<commonParameters>` определяет любые параметры, которые используются глобально несколькими службами, например `ConnectionString` при использовании <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="e9382-124">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="e9382-125">Для служб, фиксирующих рабочие пакеты в постоянных хранилищах, таких как <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> и <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, можно включить режим повторения попытки транзакции, используя параметр `EnableRetries`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e9382-125">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="e9382-126">Обратите внимание, что `EnableRetries` параметр может быть установлен на глобальном уровне (как показано в разделе *общиепараметры* ) или для отдельных служб, которые поддерживают `EnableRetries` (как показано в разделе *службы* ).</span><span class="sxs-lookup"><span data-stu-id="e9382-126">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="e9382-127">Дополнительные сведения об использовании файла конфигурации для управления поведением <xref:System.Workflow.Runtime.WorkflowRuntime> объекта Windows Workflow Foundation ведущего приложения см. в разделе [файлы конфигурации рабочего процесса](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e9382-127">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9382-128">Пример</span><span class="sxs-lookup"><span data-stu-id="e9382-128">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9382-129">См. также</span><span class="sxs-lookup"><span data-stu-id="e9382-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="e9382-130">[Файлы конфигурации рабочих процессов](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e9382-130">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
