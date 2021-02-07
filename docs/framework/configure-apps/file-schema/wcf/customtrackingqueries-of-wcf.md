---
description: 'Дополнительные сведения о: <customTrackingQueries> из WCF'
title: <customTrackingQueries> WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: ac1cdcc074201b97344b3727f6957e1b62c88dab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754476"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="cf5b2-103">\<customTrackingQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="cf5b2-103">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="cf5b2-104">Представляет коллекцию запросов, используемых для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-104">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="cf5b2-105">Запрос необходим, чтобы участник отслеживания подписался на пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="cf5b2-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cf5b2-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="cf5b2-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf5b2-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf5b2-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="cf5b2-108">Attributes and elements</span></span>

<span data-ttu-id="cf5b2-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf5b2-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="cf5b2-110">Attributes</span></span>

<span data-ttu-id="cf5b2-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="cf5b2-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="cf5b2-112">Child elements</span></span>
  
|<span data-ttu-id="cf5b2-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="cf5b2-113">Element</span></span>|<span data-ttu-id="cf5b2-114">Описание</span><span class="sxs-lookup"><span data-stu-id="cf5b2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="cf5b2-115">Запрос, который используется для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-115">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf5b2-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="cf5b2-116">Parent elements</span></span>  
  
|<span data-ttu-id="cf5b2-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="cf5b2-117">Element</span></span>|<span data-ttu-id="cf5b2-118">Описание</span><span class="sxs-lookup"><span data-stu-id="cf5b2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="cf5b2-119">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="cf5b2-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf5b2-120">См. также</span><span class="sxs-lookup"><span data-stu-id="cf5b2-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cf5b2-121">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="cf5b2-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cf5b2-122">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="cf5b2-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
