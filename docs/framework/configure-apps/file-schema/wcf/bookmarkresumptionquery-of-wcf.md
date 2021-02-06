---
description: 'Дополнительные сведения о: <bookmarkResumptionQuery> из WCF'
title: <bookmarkResumptionQuery> WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 9dadab3e304a2507a404bf43c377df46d5b33dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639332"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="28ce8-103">\<bookmarkResumptionQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="28ce8-103">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="28ce8-104">Представляет запрос, используемый для отслеживания возобновления закладки в экземпляре рабочего потока.</span><span class="sxs-lookup"><span data-stu-id="28ce8-104">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="28ce8-105">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="28ce8-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="28ce8-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="28ce8-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="28ce8-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28ce8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28ce8-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="28ce8-108">Attributes and elements</span></span>

<span data-ttu-id="28ce8-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="28ce8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28ce8-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="28ce8-110">Attributes</span></span>  
  
|<span data-ttu-id="28ce8-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="28ce8-111">Attribute</span></span>|<span data-ttu-id="28ce8-112">Описание</span><span class="sxs-lookup"><span data-stu-id="28ce8-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="28ce8-113">Строка, задающая имя записи закладки, которое используется для подписки.</span><span class="sxs-lookup"><span data-stu-id="28ce8-113">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28ce8-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="28ce8-114">Child elements</span></span>

<span data-ttu-id="28ce8-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="28ce8-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="28ce8-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="28ce8-116">Parent elements</span></span>  
  
|<span data-ttu-id="28ce8-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="28ce8-117">Element</span></span>|<span data-ttu-id="28ce8-118">Описание</span><span class="sxs-lookup"><span data-stu-id="28ce8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="28ce8-119">Представляет коллекцию запросов, используемых для отслеживания возобновления чтения с закладок в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="28ce8-119">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28ce8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="28ce8-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="28ce8-121">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="28ce8-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="28ce8-122">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="28ce8-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
