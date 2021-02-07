---
description: 'Дополнительные сведения: <customTrackingQueries>'
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 3601950742eb002f43969bea4612e830d8365509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719063"
---
# \<customTrackingQueries>

<span data-ttu-id="ad405-102">Представляет коллекцию запросов, используемых для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="ad405-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ad405-103">Запрос необходим, чтобы участник отслеживания подписался на пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ad405-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ad405-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="ad405-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="ad405-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad405-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad405-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ad405-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ad405-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ad405-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad405-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ad405-108">Attributes</span></span>  

 <span data-ttu-id="ad405-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ad405-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad405-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ad405-110">Child Elements</span></span>  
  
|<span data-ttu-id="ad405-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="ad405-111">Element</span></span>|<span data-ttu-id="ad405-112">Описание</span><span class="sxs-lookup"><span data-stu-id="ad405-112">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="ad405-113">Запрос, который используется для отслеживания событий, определенных в действиях кода.</span><span class="sxs-lookup"><span data-stu-id="ad405-113">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad405-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ad405-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ad405-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="ad405-115">Element</span></span>|<span data-ttu-id="ad405-116">Описание</span><span class="sxs-lookup"><span data-stu-id="ad405-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="ad405-117">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ad405-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad405-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ad405-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ad405-119">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="ad405-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ad405-120">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="ad405-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
