---
description: 'Дополнительные сведения: <workflowInstanceQueries>'
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 7672bcd574c15f130b8553881e53994afe9cda93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697846"
---
# \<workflowInstanceQueries>

<span data-ttu-id="6f0ca-102">Представляет коллекцию элементов конфигурации, которые отслеживают изменения жизненного цикла экземпляра рабочего процесса, например события «запущен» или «завершен».</span><span class="sxs-lookup"><span data-stu-id="6f0ca-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="6f0ca-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="6f0ca-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="6f0ca-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6f0ca-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f0ca-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6f0ca-105">Attributes and Elements</span></span>  

<span data-ttu-id="6f0ca-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6f0ca-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f0ca-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6f0ca-107">Attributes</span></span>  

<span data-ttu-id="6f0ca-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6f0ca-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f0ca-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6f0ca-109">Child Elements</span></span>  
  
|<span data-ttu-id="6f0ca-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="6f0ca-110">Element</span></span>|<span data-ttu-id="6f0ca-111">Описание</span><span class="sxs-lookup"><span data-stu-id="6f0ca-111">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="6f0ca-112">Запрос, используемый для отслеживания изменений жизненного цикла экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="6f0ca-112">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f0ca-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6f0ca-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6f0ca-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="6f0ca-114">Element</span></span>|<span data-ttu-id="6f0ca-115">Описание</span><span class="sxs-lookup"><span data-stu-id="6f0ca-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="6f0ca-116">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="6f0ca-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f0ca-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="6f0ca-117">Remarks</span></span>  

<span data-ttu-id="6f0ca-118">Запрос <xref:System.Activities.Tracking.WorkflowInstanceQuery> используется для подписки на следующие объекты <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="6f0ca-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="6f0ca-119">Пример</span><span class="sxs-lookup"><span data-stu-id="6f0ca-119">Example</span></span>  

<span data-ttu-id="6f0ca-120">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="6f0ca-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f0ca-121">См. также</span><span class="sxs-lookup"><span data-stu-id="6f0ca-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6f0ca-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="6f0ca-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6f0ca-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="6f0ca-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
