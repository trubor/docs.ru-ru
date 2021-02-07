---
description: 'Дополнительные сведения: <variables>'
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: e77c4fb1d4d16a655cd1918bb9460177b7ff3266
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698015"
---
# \<variables>

<span data-ttu-id="34420-102">Представляет коллекцию переменных, связанных с этим запросом действия.</span><span class="sxs-lookup"><span data-stu-id="34420-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="34420-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="34420-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**  
  
## <a name="syntax"></a><span data-ttu-id="34420-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="34420-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34420-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="34420-105">Attributes and Elements</span></span>  

 <span data-ttu-id="34420-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="34420-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34420-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="34420-107">Attributes</span></span>  

 <span data-ttu-id="34420-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="34420-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34420-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="34420-109">Child Elements</span></span>  
  
|<span data-ttu-id="34420-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="34420-110">Element</span></span>|<span data-ttu-id="34420-111">Описание</span><span class="sxs-lookup"><span data-stu-id="34420-111">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="34420-112">Переменная, связанная с запросом состояния действия.</span><span class="sxs-lookup"><span data-stu-id="34420-112">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34420-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="34420-113">Parent Elements</span></span>  
  
|<span data-ttu-id="34420-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="34420-114">Element</span></span>|<span data-ttu-id="34420-115">Описание</span><span class="sxs-lookup"><span data-stu-id="34420-115">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="34420-116">Представляет элемент конфигурации, используемый для отслеживания запросов на отмену дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="34420-116">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="34420-117">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="34420-117">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34420-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="34420-118">Remarks</span></span>  

 <span data-ttu-id="34420-119">Уникальной возможностью ActivityStateQuery является возможность извлекать данные во время отслеживания выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="34420-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="34420-120">Это обеспечивает дополнительный контекст при доступе к записям отслеживания после выполнения.</span><span class="sxs-lookup"><span data-stu-id="34420-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="34420-121">Можно использовать [\<arguments>](arguments.md) [\<states>](states.md) элементы, и [\<states>](states.md) для извлечения любой переменной или аргумента из любого действия в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="34420-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="34420-122">В следующем примере показан запрос состояния действия, который извлекает переменные и аргументы при создании записи отслеживания действия `Closed`.</span><span class="sxs-lookup"><span data-stu-id="34420-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="34420-123">Переменные и аргументы могут извлекаться только с помощью Активитистатерекорд, поэтому они подписываются в профиле отслеживания с помощью [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="34420-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34420-124">См. также</span><span class="sxs-lookup"><span data-stu-id="34420-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="34420-125">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="34420-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="34420-126">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="34420-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
