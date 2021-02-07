---
description: 'Дополнительные сведения: <arguments>'
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 3887fc6f4a106c8f76a76fcb768ef1376f9c7e7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748860"
---
# \<arguments>

<span data-ttu-id="63c0b-102">Представляет коллекцию аргументов, связанных с запросом состояния действия.</span><span class="sxs-lookup"><span data-stu-id="63c0b-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="63c0b-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="63c0b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="63c0b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="63c0b-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c0b-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="63c0b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="63c0b-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="63c0b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c0b-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="63c0b-107">Attributes</span></span>  

 <span data-ttu-id="63c0b-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="63c0b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63c0b-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="63c0b-109">Child Elements</span></span>  
  
|<span data-ttu-id="63c0b-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="63c0b-110">Element</span></span>|<span data-ttu-id="63c0b-111">Описание</span><span class="sxs-lookup"><span data-stu-id="63c0b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="63c0b-112">Аргумент, связанный с запросом состояния действия.</span><span class="sxs-lookup"><span data-stu-id="63c0b-112">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63c0b-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="63c0b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="63c0b-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="63c0b-114">Element</span></span>|<span data-ttu-id="63c0b-115">Описание</span><span class="sxs-lookup"><span data-stu-id="63c0b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="63c0b-116">Представляет элемент конфигурации, используемый для отслеживания запросов на отмену дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="63c0b-116">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="63c0b-117">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="63c0b-117">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c0b-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="63c0b-118">Remarks</span></span>  

 <span data-ttu-id="63c0b-119">Уникальной возможностью ActivityStateQuery является возможность извлекать данные во время отслеживания выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="63c0b-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="63c0b-120">Это обеспечивает дополнительный контекст при доступе к записям отслеживания после выполнения.</span><span class="sxs-lookup"><span data-stu-id="63c0b-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="63c0b-121">Можно использовать [\<arguments>](arguments.md) [\<states>](states.md) элементы, и [\<states>](states.md) для извлечения любой переменной или аргумента из любого действия в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="63c0b-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="63c0b-122">В следующем примере показан запрос состояния действия, который извлекает переменные и аргументы при создании записи отслеживания действия `Closed`.</span><span class="sxs-lookup"><span data-stu-id="63c0b-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="63c0b-123">Переменные и аргументы могут извлекаться только с помощью Активитистатерекорд, поэтому они подписываются в профиле отслеживания с помощью [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="63c0b-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63c0b-124">См. также</span><span class="sxs-lookup"><span data-stu-id="63c0b-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63c0b-125">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="63c0b-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63c0b-126">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="63c0b-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
