---
description: 'Дополнительные сведения: <state>'
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: c04ba8a791d08e65337ffc28cd86f5a4a6af150f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729762"
---
# \<state>

<span data-ttu-id="06918-102">Представляет коллекцию состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="06918-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="06918-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="06918-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="06918-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="06918-104">Syntax</span></span>  
  
```xml  
<tracking>
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
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06918-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="06918-105">Attributes and Elements</span></span>  

 <span data-ttu-id="06918-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="06918-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06918-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="06918-107">Attributes</span></span>  
  
|<span data-ttu-id="06918-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="06918-108">Attribute</span></span>|<span data-ttu-id="06918-109">Описание</span><span class="sxs-lookup"><span data-stu-id="06918-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06918-110">name</span><span class="sxs-lookup"><span data-stu-id="06918-110">name</span></span>|<span data-ttu-id="06918-111">Строка, указывающая состояние подписки отслеживаемого экземпляра рабочего потока в момент создания записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="06918-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06918-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="06918-112">Child Elements</span></span>  

 <span data-ttu-id="06918-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="06918-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06918-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="06918-114">Parent Elements</span></span>  
  
|<span data-ttu-id="06918-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="06918-115">Element</span></span>|<span data-ttu-id="06918-116">Описание</span><span class="sxs-lookup"><span data-stu-id="06918-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="06918-117">Коллекция состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="06918-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06918-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="06918-118">Remarks</span></span>  

 <span data-ttu-id="06918-119">Возвращаемые записи фильтруются по состояниям в этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="06918-119">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="06918-120">Допустимые значения состояния описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="06918-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="06918-121">Состояние</span><span class="sxs-lookup"><span data-stu-id="06918-121">State</span></span>|<span data-ttu-id="06918-122">Описание</span><span class="sxs-lookup"><span data-stu-id="06918-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06918-123">Прерывание</span><span class="sxs-lookup"><span data-stu-id="06918-123">Aborted</span></span>|<span data-ttu-id="06918-124">Экземпляр рабочего процесса прерван.</span><span class="sxs-lookup"><span data-stu-id="06918-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="06918-125">Завершено</span><span class="sxs-lookup"><span data-stu-id="06918-125">Completed</span></span>|<span data-ttu-id="06918-126">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="06918-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="06918-127">Удаленная</span><span class="sxs-lookup"><span data-stu-id="06918-127">Deleted</span></span>|<span data-ttu-id="06918-128">Экземпляр рабочего процесса удален.</span><span class="sxs-lookup"><span data-stu-id="06918-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="06918-129">Бездействие</span><span class="sxs-lookup"><span data-stu-id="06918-129">Idle</span></span>|<span data-ttu-id="06918-130">Экземпляр рабочего процесса простаивает.</span><span class="sxs-lookup"><span data-stu-id="06918-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="06918-131">Persisted</span><span class="sxs-lookup"><span data-stu-id="06918-131">Persisted</span></span>|<span data-ttu-id="06918-132">Экземпляр рабочего процесса сохранен.</span><span class="sxs-lookup"><span data-stu-id="06918-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="06918-133">Возобновление</span><span class="sxs-lookup"><span data-stu-id="06918-133">Resumed</span></span>|<span data-ttu-id="06918-134">Экземпляр рабочего процесса возобновлен.</span><span class="sxs-lookup"><span data-stu-id="06918-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="06918-135">Запуск</span><span class="sxs-lookup"><span data-stu-id="06918-135">Started</span></span>|<span data-ttu-id="06918-136">Экземпляр рабочего процесса запущен.</span><span class="sxs-lookup"><span data-stu-id="06918-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="06918-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="06918-137">UnhandledException</span></span>|<span data-ttu-id="06918-138">Экземпляр рабочего процесса встретил необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="06918-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="06918-139">Выгружен</span><span class="sxs-lookup"><span data-stu-id="06918-139">Unloaded</span></span>|<span data-ttu-id="06918-140">Экземпляр рабочего процесса выгружен.</span><span class="sxs-lookup"><span data-stu-id="06918-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="06918-141">Отменено</span><span class="sxs-lookup"><span data-stu-id="06918-141">Canceled</span></span>|<span data-ttu-id="06918-142">Выполнение экземпляра рабочего процесса отменено.</span><span class="sxs-lookup"><span data-stu-id="06918-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="06918-143">Приостановлена</span><span class="sxs-lookup"><span data-stu-id="06918-143">Suspended</span></span>|<span data-ttu-id="06918-144">Выполнение экземпляра рабочего процесса приостановлено.</span><span class="sxs-lookup"><span data-stu-id="06918-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="06918-145">Завершен</span><span class="sxs-lookup"><span data-stu-id="06918-145">Terminated</span></span>|<span data-ttu-id="06918-146">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="06918-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="06918-147">Возобновлено</span><span class="sxs-lookup"><span data-stu-id="06918-147">Unsuspended</span></span>|<span data-ttu-id="06918-148">Выполнение экземпляра рабочего процесса возобновлено.</span><span class="sxs-lookup"><span data-stu-id="06918-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06918-149">Пример</span><span class="sxs-lookup"><span data-stu-id="06918-149">Example</span></span>  

 <span data-ttu-id="06918-150">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="06918-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06918-151">См. также</span><span class="sxs-lookup"><span data-stu-id="06918-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="06918-152">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="06918-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06918-153">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="06918-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
