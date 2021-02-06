---
description: 'Дополнительные сведения о: <bookmarkResumptionQueries> из WCF'
title: <bookmarkResumptionQueries> WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: dfe631865549915760255b1df22ee970b806e368
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639371"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="e9606-103">\<bookmarkResumptionQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="e9606-103">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="e9606-104">Представляет коллекцию запросов, используемых для отслеживания возобновления чтения с закладок в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="e9606-104">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e9606-105">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="e9606-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="e9606-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e9606-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="e9606-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9606-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9606-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="e9606-108">Attributes and elements</span></span>  
  
<span data-ttu-id="e9606-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e9606-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9606-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e9606-110">Attributes</span></span>  
  
<span data-ttu-id="e9606-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e9606-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9606-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e9606-112">Child elements</span></span>  
  
|<span data-ttu-id="e9606-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="e9606-113">Element</span></span>|<span data-ttu-id="e9606-114">Описание</span><span class="sxs-lookup"><span data-stu-id="e9606-114">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="e9606-115">Запрос, используемый для отслеживания возобновления закладки в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="e9606-115">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e9606-116">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="e9606-116">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9606-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e9606-117">Parent elements</span></span>  
  
|<span data-ttu-id="e9606-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="e9606-118">Element</span></span>|<span data-ttu-id="e9606-119">Описание</span><span class="sxs-lookup"><span data-stu-id="e9606-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e9606-120">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="e9606-120">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9606-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e9606-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e9606-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="e9606-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e9606-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="e9606-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
