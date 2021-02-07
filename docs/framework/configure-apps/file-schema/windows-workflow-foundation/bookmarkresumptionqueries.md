---
description: 'Дополнительные сведения: <bookmarkResumptionQueries>'
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: e8ff21e2183fe31411674e9d4de6bf3d99d14836
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698158"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="6077c-102">Представляет коллекцию запросов, используемых для отслеживания возобновления чтения с закладок в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="6077c-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6077c-103">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="6077c-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="6077c-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="6077c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="6077c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6077c-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6077c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6077c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6077c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6077c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6077c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6077c-108">Attributes</span></span>  

 <span data-ttu-id="6077c-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6077c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6077c-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6077c-110">Child Elements</span></span>  
  
|<span data-ttu-id="6077c-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="6077c-111">Element</span></span>|<span data-ttu-id="6077c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="6077c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="6077c-113">Запрос, используемый для отслеживания возобновления закладки в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="6077c-113">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6077c-114">Этот запрос необходим, чтобы участник отслеживания мог подписываться на записи о возобновлении чтения с закладок.</span><span class="sxs-lookup"><span data-stu-id="6077c-114">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6077c-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6077c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6077c-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="6077c-116">Element</span></span>|<span data-ttu-id="6077c-117">Описание</span><span class="sxs-lookup"><span data-stu-id="6077c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="6077c-118">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="6077c-118">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6077c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6077c-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6077c-120">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="6077c-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6077c-121">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="6077c-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
