---
description: 'Дополнительные сведения о: <workflowInstanceQueries> из WCF'
title: <workflowInstanceQueries> WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: d4dc4827cba5a1732070b5269350ca3dd9bf2c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682336"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="fce81-103">\<workflowInstanceQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="fce81-103">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="fce81-104">Представляет коллекцию элементов конфигурации, которые отслеживают изменения жизненного цикла экземпляра рабочего процесса, например события «запущен» или «завершен».</span><span class="sxs-lookup"><span data-stu-id="fce81-104">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="fce81-105">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="fce81-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="fce81-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fce81-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fce81-107">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="fce81-107">Attributes and elements</span></span>

<span data-ttu-id="fce81-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fce81-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fce81-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fce81-109">Attributes</span></span>  

<span data-ttu-id="fce81-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fce81-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fce81-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fce81-111">Child elements</span></span>  
  
|<span data-ttu-id="fce81-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="fce81-112">Element</span></span>|<span data-ttu-id="fce81-113">Описание</span><span class="sxs-lookup"><span data-stu-id="fce81-113">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="fce81-114">Запрос, используемый для отслеживания изменений жизненного цикла экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="fce81-114">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fce81-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fce81-115">Parent elements</span></span>  
  
|<span data-ttu-id="fce81-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="fce81-116">Element</span></span>|<span data-ttu-id="fce81-117">Описание</span><span class="sxs-lookup"><span data-stu-id="fce81-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="fce81-118">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством [ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) .</span><span class="sxs-lookup"><span data-stu-id="fce81-118">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fce81-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="fce81-119">Remarks</span></span>

<span data-ttu-id="fce81-120">Запрос <xref:System.Activities.Tracking.WorkflowInstanceQuery> используется для подписки на следующие объекты <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="fce81-120">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="fce81-121">Пример</span><span class="sxs-lookup"><span data-stu-id="fce81-121">Example</span></span>  

<span data-ttu-id="fce81-122">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="fce81-122">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="fce81-123">См. также</span><span class="sxs-lookup"><span data-stu-id="fce81-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fce81-124">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="fce81-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fce81-125">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="fce81-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
