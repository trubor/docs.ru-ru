---
description: 'Дополнительные сведения: <activityScheduledQueries>'
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 1f43642edffea782a9e5257a3568868645994a46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729840"
---
# \<activityScheduledQueries>

<span data-ttu-id="4ef32-102">Представляет коллекцию запросов, которые используются для отслеживания действия, выполнение которого запланировано родительским действием.</span><span class="sxs-lookup"><span data-stu-id="4ef32-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4ef32-103">Этот запрос необходим, чтобы участник отслеживания подписался на записи запланированных действий.</span><span class="sxs-lookup"><span data-stu-id="4ef32-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="4ef32-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="4ef32-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="4ef32-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ef32-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ef32-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4ef32-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4ef32-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4ef32-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ef32-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4ef32-108">Attributes</span></span>  

 <span data-ttu-id="4ef32-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4ef32-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ef32-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4ef32-110">Child Elements</span></span>  
  
|<span data-ttu-id="4ef32-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="4ef32-111">Element</span></span>|<span data-ttu-id="4ef32-112">Описание</span><span class="sxs-lookup"><span data-stu-id="4ef32-112">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="4ef32-113">Запрос, который используется для отслеживания действия, запланированного к исполнению родительским действием.</span><span class="sxs-lookup"><span data-stu-id="4ef32-113">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ef32-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4ef32-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4ef32-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="4ef32-115">Element</span></span>|<span data-ttu-id="4ef32-116">Описание</span><span class="sxs-lookup"><span data-stu-id="4ef32-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="4ef32-117">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="4ef32-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ef32-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4ef32-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4ef32-119">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="4ef32-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ef32-120">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="4ef32-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
