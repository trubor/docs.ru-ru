---
description: 'Дополнительные сведения о: <faultPropagationQueries> из WCF'
title: <faultPropagationQueries> WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: e3ed504b3aada87246fabe54c0b32ef5ad60b34b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684442"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="68629-103">\<faultPropagationQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="68629-103">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="68629-104">Представляет коллекцию запросов, которые используются для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="68629-104">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="68629-105">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="68629-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="68629-106">Такой запрос следует использовать для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="68629-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="68629-107">Этот запрос необходим, чтобы участник отслеживания подписался на записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="68629-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="68629-108">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="68629-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="68629-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68629-109">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68629-110">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="68629-110">Attributes and elements</span></span>

<span data-ttu-id="68629-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="68629-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="68629-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="68629-112">Attributes</span></span>

<span data-ttu-id="68629-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="68629-113">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="68629-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="68629-114">Child elements</span></span>

|<span data-ttu-id="68629-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="68629-115">Element</span></span>|<span data-ttu-id="68629-116">Описание</span><span class="sxs-lookup"><span data-stu-id="68629-116">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="68629-117">Запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="68629-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="68629-118">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="68629-118">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68629-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="68629-119">Parent elements</span></span>  
  
|<span data-ttu-id="68629-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="68629-120">Element</span></span>|<span data-ttu-id="68629-121">Описание</span><span class="sxs-lookup"><span data-stu-id="68629-121">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="68629-122">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="68629-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68629-123">См. также</span><span class="sxs-lookup"><span data-stu-id="68629-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="68629-124">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="68629-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="68629-125">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="68629-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
