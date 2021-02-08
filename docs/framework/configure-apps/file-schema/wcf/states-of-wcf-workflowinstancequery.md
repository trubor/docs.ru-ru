---
description: 'Дополнительные сведения о: <states> из WCF <workflowInstanceQuery>'
title: <states> WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 66b3008b352d1f76c30aab9a0ec038836f33d408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786646"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="6cc60-103">\<states> WCF, \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="6cc60-103">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="6cc60-104">Представляет коллекцию состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="6cc60-104">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="6cc60-105">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="6cc60-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="6cc60-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6cc60-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cc60-107">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="6cc60-107">Attributes and elements</span></span>

<span data-ttu-id="6cc60-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6cc60-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cc60-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6cc60-109">Attributes</span></span>  

<span data-ttu-id="6cc60-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6cc60-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6cc60-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6cc60-111">Child elements</span></span>
  
|<span data-ttu-id="6cc60-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="6cc60-112">Element</span></span>|<span data-ttu-id="6cc60-113">Описание</span><span class="sxs-lookup"><span data-stu-id="6cc60-113">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="6cc60-114">Подписанное состояние от экземпляра рабочего процесса, который отслеживается в момент создания записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="6cc60-114">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cc60-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6cc60-115">Parent elements</span></span>  
  
|<span data-ttu-id="6cc60-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="6cc60-116">Element</span></span>|<span data-ttu-id="6cc60-117">Описание</span><span class="sxs-lookup"><span data-stu-id="6cc60-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="6cc60-118">Запрос, отслеживающий изменения жизненного цикла экземпляра рабочего процесса, например начавшиеся и завершенные события.</span><span class="sxs-lookup"><span data-stu-id="6cc60-118">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cc60-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="6cc60-119">Remarks</span></span>

<span data-ttu-id="6cc60-120">Возвращаемые записи фильтруются по состояниям в этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="6cc60-120">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="6cc60-121">Допустимые значения состояния описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="6cc60-121">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="6cc60-122">Состояние</span><span class="sxs-lookup"><span data-stu-id="6cc60-122">State</span></span>|<span data-ttu-id="6cc60-123">Описание</span><span class="sxs-lookup"><span data-stu-id="6cc60-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cc60-124">Прерывание</span><span class="sxs-lookup"><span data-stu-id="6cc60-124">Aborted</span></span>|<span data-ttu-id="6cc60-125">Экземпляр рабочего процесса прерван.</span><span class="sxs-lookup"><span data-stu-id="6cc60-125">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="6cc60-126">Завершено</span><span class="sxs-lookup"><span data-stu-id="6cc60-126">Completed</span></span>|<span data-ttu-id="6cc60-127">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="6cc60-127">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="6cc60-128">Удаленная</span><span class="sxs-lookup"><span data-stu-id="6cc60-128">Deleted</span></span>|<span data-ttu-id="6cc60-129">Экземпляр рабочего процесса удален.</span><span class="sxs-lookup"><span data-stu-id="6cc60-129">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="6cc60-130">Бездействие</span><span class="sxs-lookup"><span data-stu-id="6cc60-130">Idle</span></span>|<span data-ttu-id="6cc60-131">Экземпляр рабочего процесса простаивает.</span><span class="sxs-lookup"><span data-stu-id="6cc60-131">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="6cc60-132">Persisted</span><span class="sxs-lookup"><span data-stu-id="6cc60-132">Persisted</span></span>|<span data-ttu-id="6cc60-133">Экземпляр рабочего процесса сохранен.</span><span class="sxs-lookup"><span data-stu-id="6cc60-133">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="6cc60-134">Возобновление</span><span class="sxs-lookup"><span data-stu-id="6cc60-134">Resumed</span></span>|<span data-ttu-id="6cc60-135">Экземпляр рабочего процесса возобновлен.</span><span class="sxs-lookup"><span data-stu-id="6cc60-135">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="6cc60-136">Запуск</span><span class="sxs-lookup"><span data-stu-id="6cc60-136">Started</span></span>|<span data-ttu-id="6cc60-137">Экземпляр рабочего процесса запущен.</span><span class="sxs-lookup"><span data-stu-id="6cc60-137">The workflow instance is started.</span></span>|  
|<span data-ttu-id="6cc60-138">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="6cc60-138">UnhandledException</span></span>|<span data-ttu-id="6cc60-139">Экземпляр рабочего процесса встретил необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="6cc60-139">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="6cc60-140">Выгружен</span><span class="sxs-lookup"><span data-stu-id="6cc60-140">Unloaded</span></span>|<span data-ttu-id="6cc60-141">Экземпляр рабочего процесса выгружен.</span><span class="sxs-lookup"><span data-stu-id="6cc60-141">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="6cc60-142">Отменено</span><span class="sxs-lookup"><span data-stu-id="6cc60-142">Canceled</span></span>|<span data-ttu-id="6cc60-143">Выполнение экземпляра рабочего процесса отменено.</span><span class="sxs-lookup"><span data-stu-id="6cc60-143">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="6cc60-144">Приостановлена</span><span class="sxs-lookup"><span data-stu-id="6cc60-144">Suspended</span></span>|<span data-ttu-id="6cc60-145">Выполнение экземпляра рабочего процесса приостановлено.</span><span class="sxs-lookup"><span data-stu-id="6cc60-145">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="6cc60-146">Завершен</span><span class="sxs-lookup"><span data-stu-id="6cc60-146">Terminated</span></span>|<span data-ttu-id="6cc60-147">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="6cc60-147">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="6cc60-148">Возобновлено</span><span class="sxs-lookup"><span data-stu-id="6cc60-148">Unsuspended</span></span>|<span data-ttu-id="6cc60-149">Выполнение экземпляра рабочего процесса возобновлено.</span><span class="sxs-lookup"><span data-stu-id="6cc60-149">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6cc60-150">Пример</span><span class="sxs-lookup"><span data-stu-id="6cc60-150">Example</span></span>

<span data-ttu-id="6cc60-151">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="6cc60-151">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="6cc60-152">См. также</span><span class="sxs-lookup"><span data-stu-id="6cc60-152">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6cc60-153">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="6cc60-153">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6cc60-154">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="6cc60-154">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
