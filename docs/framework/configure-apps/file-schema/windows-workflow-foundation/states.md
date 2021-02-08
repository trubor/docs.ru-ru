---
description: 'Дополнительные сведения: <states>'
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 9a66a1ce460db1f5f55fb99a191368635220f32f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781978"
---
# \<states>

<span data-ttu-id="b5c83-102">Представляет коллекцию состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b5c83-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="b5c83-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="b5c83-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="b5c83-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5c83-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5c83-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b5c83-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b5c83-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b5c83-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5c83-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b5c83-107">Attributes</span></span>  

 <span data-ttu-id="b5c83-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b5c83-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5c83-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b5c83-109">Child Elements</span></span>  
  
|<span data-ttu-id="b5c83-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="b5c83-110">Element</span></span>|<span data-ttu-id="b5c83-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b5c83-111">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="b5c83-112">Подписанное состояние от экземпляра рабочего процесса, который отслеживается в момент создания записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b5c83-112">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5c83-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b5c83-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b5c83-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="b5c83-114">Element</span></span>|<span data-ttu-id="b5c83-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b5c83-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="b5c83-116">Запрос, отслеживающий изменения жизненного цикла экземпляра рабочего процесса, например начавшиеся и завершенные события.</span><span class="sxs-lookup"><span data-stu-id="b5c83-116">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c83-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5c83-117">Remarks</span></span>  

 <span data-ttu-id="b5c83-118">Возвращаемые записи фильтруются по состояниям в этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="b5c83-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="b5c83-119">Допустимые значения состояния описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b5c83-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="b5c83-120">Состояние</span><span class="sxs-lookup"><span data-stu-id="b5c83-120">State</span></span>|<span data-ttu-id="b5c83-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b5c83-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b5c83-122">Прерывание</span><span class="sxs-lookup"><span data-stu-id="b5c83-122">Aborted</span></span>|<span data-ttu-id="b5c83-123">Экземпляр рабочего процесса прерван.</span><span class="sxs-lookup"><span data-stu-id="b5c83-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b5c83-124">Завершено</span><span class="sxs-lookup"><span data-stu-id="b5c83-124">Completed</span></span>|<span data-ttu-id="b5c83-125">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="b5c83-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="b5c83-126">Удаленная</span><span class="sxs-lookup"><span data-stu-id="b5c83-126">Deleted</span></span>|<span data-ttu-id="b5c83-127">Экземпляр рабочего процесса удален.</span><span class="sxs-lookup"><span data-stu-id="b5c83-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="b5c83-128">Бездействие</span><span class="sxs-lookup"><span data-stu-id="b5c83-128">Idle</span></span>|<span data-ttu-id="b5c83-129">Экземпляр рабочего процесса простаивает.</span><span class="sxs-lookup"><span data-stu-id="b5c83-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="b5c83-130">Persisted</span><span class="sxs-lookup"><span data-stu-id="b5c83-130">Persisted</span></span>|<span data-ttu-id="b5c83-131">Экземпляр рабочего процесса сохранен.</span><span class="sxs-lookup"><span data-stu-id="b5c83-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="b5c83-132">Возобновление</span><span class="sxs-lookup"><span data-stu-id="b5c83-132">Resumed</span></span>|<span data-ttu-id="b5c83-133">Экземпляр рабочего процесса возобновлен.</span><span class="sxs-lookup"><span data-stu-id="b5c83-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="b5c83-134">Запуск</span><span class="sxs-lookup"><span data-stu-id="b5c83-134">Started</span></span>|<span data-ttu-id="b5c83-135">Экземпляр рабочего процесса запущен.</span><span class="sxs-lookup"><span data-stu-id="b5c83-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="b5c83-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="b5c83-136">UnhandledException</span></span>|<span data-ttu-id="b5c83-137">Экземпляр рабочего процесса встретил необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="b5c83-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="b5c83-138">Выгружен</span><span class="sxs-lookup"><span data-stu-id="b5c83-138">Unloaded</span></span>|<span data-ttu-id="b5c83-139">Экземпляр рабочего процесса выгружен.</span><span class="sxs-lookup"><span data-stu-id="b5c83-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="b5c83-140">Отменено</span><span class="sxs-lookup"><span data-stu-id="b5c83-140">Canceled</span></span>|<span data-ttu-id="b5c83-141">Выполнение экземпляра рабочего процесса отменено.</span><span class="sxs-lookup"><span data-stu-id="b5c83-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="b5c83-142">Приостановлена</span><span class="sxs-lookup"><span data-stu-id="b5c83-142">Suspended</span></span>|<span data-ttu-id="b5c83-143">Выполнение экземпляра рабочего процесса приостановлено.</span><span class="sxs-lookup"><span data-stu-id="b5c83-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="b5c83-144">Завершен</span><span class="sxs-lookup"><span data-stu-id="b5c83-144">Terminated</span></span>|<span data-ttu-id="b5c83-145">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="b5c83-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="b5c83-146">Возобновлено</span><span class="sxs-lookup"><span data-stu-id="b5c83-146">Unsuspended</span></span>|<span data-ttu-id="b5c83-147">Выполнение экземпляра рабочего процесса возобновлено.</span><span class="sxs-lookup"><span data-stu-id="b5c83-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b5c83-148">Пример</span><span class="sxs-lookup"><span data-stu-id="b5c83-148">Example</span></span>  

 <span data-ttu-id="b5c83-149">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="b5c83-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5c83-150">См. также</span><span class="sxs-lookup"><span data-stu-id="b5c83-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b5c83-151">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="b5c83-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b5c83-152">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="b5c83-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
