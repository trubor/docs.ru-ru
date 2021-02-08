---
description: 'Дополнительные сведения <state> о: <states>'
title: <state> из <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 748044986143f182faa0edafb0cfe299a79a704e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781991"
---
# <a name="state-of-states"></a><span data-ttu-id="feba5-103">\<state> из \<states></span><span class="sxs-lookup"><span data-stu-id="feba5-103">\<state> of \<states></span></span>

<span data-ttu-id="feba5-104">Элемент конфигурации, содержащий состояние подписанного действия, для которого необходимо создать запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="feba5-104">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="feba5-105">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="feba5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="feba5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="feba5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feba5-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="feba5-107">Attributes and Elements</span></span>  

 <span data-ttu-id="feba5-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="feba5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feba5-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="feba5-109">Attributes</span></span>  
  
|<span data-ttu-id="feba5-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="feba5-110">Attribute</span></span>|<span data-ttu-id="feba5-111">Описание</span><span class="sxs-lookup"><span data-stu-id="feba5-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="feba5-112">name</span><span class="sxs-lookup"><span data-stu-id="feba5-112">name</span></span>|<span data-ttu-id="feba5-113">Строка, содержащая состояние подписанного действия, для которого необходимо создать запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="feba5-113">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="feba5-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="feba5-114">Child Elements</span></span>  

 <span data-ttu-id="feba5-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="feba5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="feba5-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="feba5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="feba5-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="feba5-117">Element</span></span>|<span data-ttu-id="feba5-118">Описание</span><span class="sxs-lookup"><span data-stu-id="feba5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="feba5-119">Коллекция элементов конфигурации, содержащих состояния действия, на которое установлена подписка и для которого необходимо создать запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="feba5-119">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feba5-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="feba5-120">Remarks</span></span>  

 <span data-ttu-id="feba5-121">Уникальной возможностью ActivityStateQuery является возможность извлекать данные во время отслеживания выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="feba5-121">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="feba5-122">Это обеспечивает дополнительный контекст при доступе к записям отслеживания после выполнения.</span><span class="sxs-lookup"><span data-stu-id="feba5-122">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="feba5-123">Можно использовать [\<arguments>](arguments.md) [\<states>](states.md) элементы, и [\<states>](states.md) для извлечения любой переменной или аргумента из любого действия в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="feba5-123">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="feba5-124">В следующем примере показан запрос состояния действия, который извлекает переменные и аргументы при создании записи отслеживания действия `Closed`.</span><span class="sxs-lookup"><span data-stu-id="feba5-124">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="feba5-125">Переменные и аргументы могут извлекаться только с помощью Активитистатерекорд, поэтому они подписываются в профиле отслеживания с помощью [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="feba5-125">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="feba5-126">См. также</span><span class="sxs-lookup"><span data-stu-id="feba5-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="feba5-127">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="feba5-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="feba5-128">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="feba5-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
