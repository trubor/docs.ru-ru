---
description: 'Дополнительные сведения: <cancelRequestedQuery>'
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: efd908fb52d2bc32bf05fce9099c7105abdc9b1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652644"
---
# \<cancelRequestedQuery>

<span data-ttu-id="29ea9-102">Представляет запрос, используемый для отслеживания запросов по отмене дочернего действия родительским.</span><span class="sxs-lookup"><span data-stu-id="29ea9-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="29ea9-103">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="29ea9-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="29ea9-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="29ea9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="29ea9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="29ea9-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29ea9-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="29ea9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="29ea9-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="29ea9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29ea9-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="29ea9-108">Attributes</span></span>  
  
|<span data-ttu-id="29ea9-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="29ea9-109">Attribute</span></span>|<span data-ttu-id="29ea9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="29ea9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29ea9-111">activityName</span><span class="sxs-lookup"><span data-stu-id="29ea9-111">activityName</span></span>|<span data-ttu-id="29ea9-112">Строка, задающая имя действия, которое запрашивает отмену.</span><span class="sxs-lookup"><span data-stu-id="29ea9-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="29ea9-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="29ea9-113">childActivityName</span></span>|<span data-ttu-id="29ea9-114">Строка, указывающая имя дочернего действия, для которого была запрошена отмена.</span><span class="sxs-lookup"><span data-stu-id="29ea9-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29ea9-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="29ea9-115">Child Elements</span></span>  

 <span data-ttu-id="29ea9-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="29ea9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29ea9-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="29ea9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="29ea9-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="29ea9-118">Element</span></span>|<span data-ttu-id="29ea9-119">Описание</span><span class="sxs-lookup"><span data-stu-id="29ea9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="29ea9-120">Представляет список элементов конфигурации, которые используются для отслеживания запросов на отмену дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="29ea9-120">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="29ea9-121">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="29ea9-121">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29ea9-122">См. также</span><span class="sxs-lookup"><span data-stu-id="29ea9-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="29ea9-123">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="29ea9-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="29ea9-124">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="29ea9-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
