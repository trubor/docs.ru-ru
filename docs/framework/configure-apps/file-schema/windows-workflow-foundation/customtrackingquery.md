---
description: 'Дополнительные сведения: <customTrackingQuery>'
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 24857aca39aad825a3dd4eca83fa3a51ec440b25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795096"
---
# \<customTrackingQuery>

<span data-ttu-id="a2ee3-102">Представляет коллекцию запросов, используемых для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a2ee3-103">Запрос необходим, чтобы участник отслеживания подписался на пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="a2ee3-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="a2ee3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a2ee3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2ee3-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2ee3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a2ee3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a2ee3-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2ee3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a2ee3-108">Attributes</span></span>  
  
|<span data-ttu-id="a2ee3-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a2ee3-109">Attribute</span></span>|<span data-ttu-id="a2ee3-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a2ee3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2ee3-111">activityName</span><span class="sxs-lookup"><span data-stu-id="a2ee3-111">activityName</span></span>|<span data-ttu-id="a2ee3-112">Строка, задающая имя действия, сформировавшего запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="a2ee3-113">name</span><span class="sxs-lookup"><span data-stu-id="a2ee3-113">name</span></span>|<span data-ttu-id="a2ee3-114">Строка, задающая имя выдаваемой пользовательской записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2ee3-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a2ee3-115">Child Elements</span></span>  

 <span data-ttu-id="a2ee3-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2ee3-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a2ee3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a2ee3-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="a2ee3-118">Element</span></span>|<span data-ttu-id="a2ee3-119">Описание</span><span class="sxs-lookup"><span data-stu-id="a2ee3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="a2ee3-120">Запрос, который используется для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="a2ee3-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2ee3-121">См. также</span><span class="sxs-lookup"><span data-stu-id="a2ee3-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a2ee3-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="a2ee3-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a2ee3-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="a2ee3-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
