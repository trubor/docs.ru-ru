---
description: 'Дополнительные сведения: <faultPropagationQueries>'
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 13bd19a3673846bfbd641cd2f8eeafc20b8186f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719074"
---
# \<faultPropagationQueries>

<span data-ttu-id="5393b-102">Представляет коллекцию запросов, которые используются для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="5393b-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5393b-103">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="5393b-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5393b-104">Такой запрос следует использовать для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="5393b-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5393b-105">Этот запрос необходим, чтобы участник отслеживания подписался на записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="5393b-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="5393b-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5393b-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="5393b-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5393b-107">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5393b-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5393b-108">Attributes and Elements</span></span>  

 <span data-ttu-id="5393b-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5393b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5393b-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5393b-110">Attributes</span></span>  

 <span data-ttu-id="5393b-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5393b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5393b-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5393b-112">Child Elements</span></span>  
  
|<span data-ttu-id="5393b-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="5393b-113">Element</span></span>|<span data-ttu-id="5393b-114">Описание</span><span class="sxs-lookup"><span data-stu-id="5393b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="5393b-115">Запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="5393b-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5393b-116">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="5393b-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5393b-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5393b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5393b-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="5393b-118">Element</span></span>|<span data-ttu-id="5393b-119">Описание</span><span class="sxs-lookup"><span data-stu-id="5393b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="5393b-120">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, определяемого свойством **ActivityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="5393b-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5393b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="5393b-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5393b-122">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="5393b-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5393b-123">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="5393b-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
