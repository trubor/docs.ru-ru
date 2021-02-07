---
description: 'Дополнительные сведения: <bookmarkResumptionQuery>'
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 4e6637b6edd54d9c1cf1a44986b362eb616bf14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725250"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="51ddc-102">Представляет запрос, используемый для отслеживания возобновления закладки в экземпляре рабочего потока.</span><span class="sxs-lookup"><span data-stu-id="51ddc-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="51ddc-103">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="51ddc-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="51ddc-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="51ddc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="51ddc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="51ddc-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51ddc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="51ddc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="51ddc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="51ddc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51ddc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="51ddc-108">Attributes</span></span>  
  
|<span data-ttu-id="51ddc-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="51ddc-109">Attribute</span></span>|<span data-ttu-id="51ddc-110">Описание</span><span class="sxs-lookup"><span data-stu-id="51ddc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51ddc-111">name</span><span class="sxs-lookup"><span data-stu-id="51ddc-111">name</span></span>|<span data-ttu-id="51ddc-112">Строка, задающая имя записи закладки, которое используется для подписки.</span><span class="sxs-lookup"><span data-stu-id="51ddc-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51ddc-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="51ddc-113">Child Elements</span></span>  

 <span data-ttu-id="51ddc-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="51ddc-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51ddc-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="51ddc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="51ddc-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="51ddc-116">Element</span></span>|<span data-ttu-id="51ddc-117">Описание</span><span class="sxs-lookup"><span data-stu-id="51ddc-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="51ddc-118">Представляет коллекцию запросов, используемых для отслеживания возобновления чтения с закладок в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="51ddc-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51ddc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="51ddc-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="51ddc-120">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="51ddc-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="51ddc-121">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="51ddc-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
