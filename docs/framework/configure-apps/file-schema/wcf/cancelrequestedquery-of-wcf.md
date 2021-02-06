---
description: 'Дополнительные сведения о: <cancelRequestedQuery> из WCF'
title: <cancelRequestedQuery> WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: e477e33650eb901cf2e9275570d8538196c52b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639176"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="83a12-103">\<cancelRequestedQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="83a12-103">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="83a12-104">Представляет запрос, используемый для отслеживания запросов по отмене дочернего действия родительским.</span><span class="sxs-lookup"><span data-stu-id="83a12-104">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="83a12-105">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="83a12-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="83a12-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="83a12-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="83a12-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83a12-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83a12-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="83a12-108">Attributes and elements</span></span>

<span data-ttu-id="83a12-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="83a12-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="83a12-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="83a12-110">Attributes</span></span>  
  
|<span data-ttu-id="83a12-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="83a12-111">Attribute</span></span>|<span data-ttu-id="83a12-112">Описание</span><span class="sxs-lookup"><span data-stu-id="83a12-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="83a12-113">Строка, задающая имя действия, которое запрашивает отмену.</span><span class="sxs-lookup"><span data-stu-id="83a12-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="83a12-114">Строка, указывающая имя дочернего действия, для которого была запрошена отмена.</span><span class="sxs-lookup"><span data-stu-id="83a12-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83a12-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="83a12-115">Child elements</span></span>

<span data-ttu-id="83a12-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="83a12-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="83a12-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="83a12-117">Parent elements</span></span>
  
|<span data-ttu-id="83a12-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="83a12-118">Element</span></span>|<span data-ttu-id="83a12-119">Описание</span><span class="sxs-lookup"><span data-stu-id="83a12-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="83a12-120">Представляет коллекцию запросов, используемых для отслеживания запросов по отмене дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="83a12-120">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83a12-121">См. также</span><span class="sxs-lookup"><span data-stu-id="83a12-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="83a12-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="83a12-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="83a12-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="83a12-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
