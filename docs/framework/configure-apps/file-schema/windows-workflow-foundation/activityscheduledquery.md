---
description: 'Дополнительные сведения: <activityScheduledQuery>'
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 72aa9c2d3480488d4468d008fa8a4306929c190d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802116"
---
# \<activityScheduledQuery>

<span data-ttu-id="2a39c-102">Представляет коллекцию запросов, которые используются для отслеживания действия, выполнение которого запланировано родительским действием.</span><span class="sxs-lookup"><span data-stu-id="2a39c-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2a39c-103">Этот запрос необходим, чтобы участник отслеживания подписался на записи запланированных действий.</span><span class="sxs-lookup"><span data-stu-id="2a39c-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2a39c-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="2a39c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="2a39c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2a39c-105">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a39c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2a39c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2a39c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2a39c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a39c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2a39c-108">Attributes</span></span>  
  
|<span data-ttu-id="2a39c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2a39c-109">Attribute</span></span>|<span data-ttu-id="2a39c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2a39c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a39c-111">activityName</span><span class="sxs-lookup"><span data-stu-id="2a39c-111">activityName</span></span>|<span data-ttu-id="2a39c-112">Строка, задающая имя действия, которое запрашивает отмену.</span><span class="sxs-lookup"><span data-stu-id="2a39c-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="2a39c-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="2a39c-113">childActivityName</span></span>|<span data-ttu-id="2a39c-114">Строка, указывающая имя дочернего действия, для которого была запрошена отмена.</span><span class="sxs-lookup"><span data-stu-id="2a39c-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a39c-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2a39c-115">Child Elements</span></span>  

 <span data-ttu-id="2a39c-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2a39c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a39c-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2a39c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2a39c-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="2a39c-118">Element</span></span>|<span data-ttu-id="2a39c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="2a39c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="2a39c-120">Запрос, который используется для отслеживания действия, запланированного к исполнению родительским действием.</span><span class="sxs-lookup"><span data-stu-id="2a39c-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a39c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="2a39c-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2a39c-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="2a39c-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a39c-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="2a39c-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
