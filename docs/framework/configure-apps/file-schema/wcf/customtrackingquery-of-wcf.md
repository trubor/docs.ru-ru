---
description: 'Дополнительные сведения о: <customTrackingQuery> из WCF'
title: <customTrackingQuery> WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 3eac26ee94a95b480d743e3c6ec554a84b8747a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754463"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="85795-103">\<customTrackingQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="85795-103">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="85795-104">Представляет запрос, который используется для трассировки событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="85795-104">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="85795-105">Запрос необходим, чтобы участник отслеживания подписался на пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="85795-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="85795-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="85795-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="85795-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85795-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85795-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="85795-108">Attributes and elements</span></span>  

<span data-ttu-id="85795-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="85795-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85795-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="85795-110">Attributes</span></span>  
  
|<span data-ttu-id="85795-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="85795-111">Attribute</span></span>|<span data-ttu-id="85795-112">Описание</span><span class="sxs-lookup"><span data-stu-id="85795-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="85795-113">Строка, задающая имя действия, сформировавшего запись отслеживания.</span><span class="sxs-lookup"><span data-stu-id="85795-113">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="85795-114">Строка, задающая имя выдаваемой пользовательской записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="85795-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85795-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="85795-115">Child elements</span></span>

<span data-ttu-id="85795-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="85795-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85795-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="85795-117">Parent elements</span></span>

|<span data-ttu-id="85795-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="85795-118">Element</span></span>|<span data-ttu-id="85795-119">Описание</span><span class="sxs-lookup"><span data-stu-id="85795-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="85795-120">Представляет коллекцию запросов, используемых для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="85795-120">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="85795-121">См. также</span><span class="sxs-lookup"><span data-stu-id="85795-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="85795-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="85795-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85795-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="85795-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
