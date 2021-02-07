---
description: 'Дополнительные сведения: <activityStateQueries>'
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad324d88c481016d85b8e58ccc0857b7773d8328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748964"
---
# \<activityStateQueries>

<span data-ttu-id="257d3-102">Представляет коллекцию запросов, которые используются для отслеживания изменений жизненного цикла действий, составляющих экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="257d3-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="257d3-103">Например, вы можете захотеть отследить каждый раз, когда действие "отправить электронное письмо" завершается в рамках экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="257d3-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="257d3-104">Этот запрос необходим, чтобы участник отслеживания мог подписываться на объекты записей состояния действия.</span><span class="sxs-lookup"><span data-stu-id="257d3-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="257d3-105">Состояния, доступные для подписки, указаны в ActivtyStates.</span><span class="sxs-lookup"><span data-stu-id="257d3-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="257d3-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="257d3-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="257d3-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="257d3-107">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="257d3-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="257d3-108">Attributes and Elements</span></span>  

 <span data-ttu-id="257d3-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="257d3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="257d3-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="257d3-110">Attributes</span></span>  

 <span data-ttu-id="257d3-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="257d3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="257d3-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="257d3-112">Child Elements</span></span>  
  
|<span data-ttu-id="257d3-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="257d3-113">Element</span></span>|<span data-ttu-id="257d3-114">Описание</span><span class="sxs-lookup"><span data-stu-id="257d3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="257d3-115">Запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="257d3-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="257d3-116">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="257d3-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="257d3-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="257d3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="257d3-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="257d3-118">Element</span></span>|<span data-ttu-id="257d3-119">Описание</span><span class="sxs-lookup"><span data-stu-id="257d3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="257d3-120">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="257d3-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="257d3-121">См. также</span><span class="sxs-lookup"><span data-stu-id="257d3-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="257d3-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="257d3-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="257d3-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="257d3-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
