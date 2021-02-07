---
description: 'Дополнительные сведения: <cancelRequestedQueries>'
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: a508de97bce604284d9af00a3344fe5f35dc8bea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698080"
---
# \<cancelRequestedQueries>

<span data-ttu-id="b6442-102">Представляет коллекцию запросов, используемых для отслеживания запросов по отмене дочернего действия родительским действием.</span><span class="sxs-lookup"><span data-stu-id="b6442-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b6442-103">Этот запрос необходим, чтобы участник отслеживания подписался на объекты записей запросов на отмену.</span><span class="sxs-lookup"><span data-stu-id="b6442-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="b6442-104">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="b6442-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b6442-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b6442-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6442-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b6442-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b6442-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b6442-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6442-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b6442-108">Attributes</span></span>  

 <span data-ttu-id="b6442-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b6442-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6442-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b6442-110">Child Elements</span></span>  
  
|<span data-ttu-id="b6442-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="b6442-111">Element</span></span>|<span data-ttu-id="b6442-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b6442-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="b6442-113">Запрос, используемый для отслеживания запросов по отмене дочернего действия родительским.</span><span class="sxs-lookup"><span data-stu-id="b6442-113">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6442-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b6442-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b6442-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="b6442-115">Element</span></span>|<span data-ttu-id="b6442-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b6442-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="b6442-117">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="b6442-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6442-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b6442-118">See also</span></span>

- [<span data-ttu-id="b6442-119">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="b6442-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b6442-120">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="b6442-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
