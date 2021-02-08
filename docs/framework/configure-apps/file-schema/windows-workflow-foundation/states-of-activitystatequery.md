---
description: 'Дополнительные сведения <states> о: <activityStateQuery>'
title: <states> из <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 16a0af865508f0ebc50d16728c35188310c95043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773281"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="71ab3-103">\<states> из \<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="71ab3-103">\<states> of \<activityStateQuery></span></span>

<span data-ttu-id="71ab3-104">Коллекция элементов конфигурации, содержащих состояния действия, на которое установлена подписка и для которого необходимо создать запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="71ab3-104">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="71ab3-105">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="71ab3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="71ab3-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71ab3-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71ab3-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="71ab3-107">Attributes and Elements</span></span>  

 <span data-ttu-id="71ab3-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="71ab3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71ab3-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="71ab3-109">Attributes</span></span>  

 <span data-ttu-id="71ab3-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="71ab3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71ab3-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="71ab3-111">Child Elements</span></span>  
  
|<span data-ttu-id="71ab3-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="71ab3-112">Element</span></span>|<span data-ttu-id="71ab3-113">Описание</span><span class="sxs-lookup"><span data-stu-id="71ab3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](state-of-states.md)|<span data-ttu-id="71ab3-114">Элемент конфигурации, содержащий состояния подписанного действия, для которого необходимо создать запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="71ab3-114">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71ab3-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="71ab3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="71ab3-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="71ab3-116">Element</span></span>|<span data-ttu-id="71ab3-117">Описание</span><span class="sxs-lookup"><span data-stu-id="71ab3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="71ab3-118">Представляет элемент конфигурации, используемый для отслеживания запросов на отмену дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="71ab3-118">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="71ab3-119">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="71ab3-119">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71ab3-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="71ab3-120">Remarks</span></span>  

 <span data-ttu-id="71ab3-121">Уникальной возможностью ActivityStateQuery является возможность извлекать данные во время отслеживания выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="71ab3-121">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="71ab3-122">Это обеспечивает дополнительный контекст при доступе к записям отслеживания после выполнения.</span><span class="sxs-lookup"><span data-stu-id="71ab3-122">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="71ab3-123">Можно использовать [\<arguments>](arguments.md) [\<states>](states.md) элементы, и [\<states>](states.md) для извлечения любой переменной или аргумента из любого действия в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="71ab3-123">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="71ab3-124">В следующем примере показан запрос состояния действия, который извлекает переменные и аргументы при создании записи отслеживания действия `Closed`.</span><span class="sxs-lookup"><span data-stu-id="71ab3-124">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="71ab3-125">Переменные и аргументы могут извлекаться только с помощью Активитистатерекорд, поэтому они подписываются в профиле отслеживания с помощью [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="71ab3-125">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71ab3-126">См. также</span><span class="sxs-lookup"><span data-stu-id="71ab3-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="71ab3-127">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="71ab3-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="71ab3-128">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="71ab3-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
