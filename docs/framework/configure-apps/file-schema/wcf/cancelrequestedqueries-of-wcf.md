---
description: 'Дополнительные сведения о: <cancelRequestedQueries> из WCF'
title: <cancelRequestedQueries> WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 3850d7efd01f9092312567a0eba68a6e9547baad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639189"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="14204-103">\<cancelRequestedQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="14204-103">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="14204-104">Представляет коллекцию запросов, используемых для отслеживания запросов по отмене дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="14204-104">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="14204-105">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="14204-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="14204-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="14204-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="14204-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14204-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14204-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="14204-108">Attributes and elements</span></span>  

<span data-ttu-id="14204-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="14204-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14204-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="14204-110">Attributes</span></span>

<span data-ttu-id="14204-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="14204-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="14204-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="14204-112">Child elements</span></span>
  
|<span data-ttu-id="14204-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="14204-113">Element</span></span>|<span data-ttu-id="14204-114">Описание</span><span class="sxs-lookup"><span data-stu-id="14204-114">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="14204-115">Запрос, используемый для отслеживания запросов по отмене дочернего действия родительским.</span><span class="sxs-lookup"><span data-stu-id="14204-115">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14204-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="14204-116">Parent elements</span></span>  
  
|<span data-ttu-id="14204-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="14204-117">Element</span></span>|<span data-ttu-id="14204-118">Описание</span><span class="sxs-lookup"><span data-stu-id="14204-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="14204-119">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId>.</span><span class="sxs-lookup"><span data-stu-id="14204-119">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14204-120">См. также</span><span class="sxs-lookup"><span data-stu-id="14204-120">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="14204-121">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="14204-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14204-122">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="14204-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
