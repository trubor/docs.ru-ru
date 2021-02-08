---
description: 'Дополнительные сведения о: <activityScheduledQueries> из WCF'
title: <activityScheduledQueries> WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: b92bb2827b4c8bce43e4ee0b8dc03c7be124e3da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782251"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="3c781-103">\<activityScheduledQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="3c781-103">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="3c781-104">Представляет коллекцию запросов, которые используются для отслеживания действия, выполнение которого запланировано родительским действием.</span><span class="sxs-lookup"><span data-stu-id="3c781-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="3c781-105">Этот запрос необходим, чтобы участник отслеживания подписался на записи запланированных действий.</span><span class="sxs-lookup"><span data-stu-id="3c781-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="3c781-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="3c781-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="3c781-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c781-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c781-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="3c781-108">Attributes and elements</span></span>  

<span data-ttu-id="3c781-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3c781-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c781-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3c781-110">Attributes</span></span>  

<span data-ttu-id="3c781-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3c781-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c781-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3c781-112">Child elements</span></span>  
  
|<span data-ttu-id="3c781-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="3c781-113">Element</span></span>|<span data-ttu-id="3c781-114">Описание</span><span class="sxs-lookup"><span data-stu-id="3c781-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="3c781-115">Запрос, который используется для отслеживания действия, запланированного к исполнению родительским действием.</span><span class="sxs-lookup"><span data-stu-id="3c781-115">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c781-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3c781-116">Parent elements</span></span>  
  
|<span data-ttu-id="3c781-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="3c781-117">Element</span></span>|<span data-ttu-id="3c781-118">Описание</span><span class="sxs-lookup"><span data-stu-id="3c781-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="3c781-119">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="3c781-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c781-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3c781-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="3c781-121">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="3c781-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3c781-122">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="3c781-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
