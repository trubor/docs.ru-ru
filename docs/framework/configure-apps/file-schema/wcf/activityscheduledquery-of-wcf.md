---
description: 'Дополнительные сведения о: <activityScheduledQuery> из WCF'
title: <activityScheduledQuery> WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b1b5f971dccfbc650ee12a08a9ae2fa7b745db50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802363"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="1ec25-103">\<activityScheduledQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="1ec25-103">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="1ec25-104">Представляет коллекцию запросов, которые используются для отслеживания действия, выполнение которого запланировано родительским действием.</span><span class="sxs-lookup"><span data-stu-id="1ec25-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1ec25-105">Этот запрос необходим, чтобы участник отслеживания подписался на записи запланированных действий.</span><span class="sxs-lookup"><span data-stu-id="1ec25-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="1ec25-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="1ec25-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="1ec25-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ec25-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ec25-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="1ec25-108">Attributes and elements</span></span>  

<span data-ttu-id="1ec25-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1ec25-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ec25-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1ec25-110">Attributes</span></span>  
  
|<span data-ttu-id="1ec25-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1ec25-111">Attribute</span></span>|<span data-ttu-id="1ec25-112">Описание</span><span class="sxs-lookup"><span data-stu-id="1ec25-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="1ec25-113">Строка, задающая имя действия, которое запрашивает отмену.</span><span class="sxs-lookup"><span data-stu-id="1ec25-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="1ec25-114">Строка, указывающая имя дочернего действия, для которого была запрошена отмена.</span><span class="sxs-lookup"><span data-stu-id="1ec25-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ec25-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1ec25-115">Child elements</span></span>

<span data-ttu-id="1ec25-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1ec25-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="1ec25-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1ec25-117">Parent elements</span></span>  
  
|<span data-ttu-id="1ec25-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="1ec25-118">Element</span></span>|<span data-ttu-id="1ec25-119">Описание</span><span class="sxs-lookup"><span data-stu-id="1ec25-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="1ec25-120">Коллекция запросов, которая используется для трассировки действия, запланированного на выполнение родительским действием.</span><span class="sxs-lookup"><span data-stu-id="1ec25-120">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ec25-121">См. также</span><span class="sxs-lookup"><span data-stu-id="1ec25-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="1ec25-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="1ec25-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1ec25-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="1ec25-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
