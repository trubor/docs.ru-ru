---
description: 'Дополнительные сведения о: <faultPropagationQuery> из WCF'
title: <faultPropagationQuery> WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cd26bf76fec54371ef0455b93c98650bdab19068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782069"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="ba50c-103">\<faultPropagationQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="ba50c-103">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="ba50c-104">Представляет запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ba50c-104">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ba50c-105">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="ba50c-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ba50c-106">Такой запрос следует использовать для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ba50c-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ba50c-107">Этот запрос необходим, чтобы участник отслеживания подписался на записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="ba50c-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="ba50c-108">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ba50c-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="ba50c-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba50c-109">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba50c-110">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="ba50c-110">Attributes and elements</span></span>

<span data-ttu-id="ba50c-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ba50c-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba50c-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ba50c-112">Attributes</span></span>

|<span data-ttu-id="ba50c-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ba50c-113">Attribute</span></span>|<span data-ttu-id="ba50c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="ba50c-114">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="ba50c-115">Строка, указывающая имя действия обработчика сбоев, которое распространило ошибку.</span><span class="sxs-lookup"><span data-stu-id="ba50c-115">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="ba50c-116">Значение по умолчанию — \* , что означает, что для всех действий возвращаются записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="ba50c-116">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="ba50c-117">Строка, указывающая имя действия, ставшего источником ошибки.</span><span class="sxs-lookup"><span data-stu-id="ba50c-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ba50c-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ba50c-118">Child elements</span></span>

<span data-ttu-id="ba50c-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ba50c-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba50c-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ba50c-120">Parent elements</span></span>

|<span data-ttu-id="ba50c-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="ba50c-121">Element</span></span>|<span data-ttu-id="ba50c-122">Описание</span><span class="sxs-lookup"><span data-stu-id="ba50c-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="ba50c-123">Представляет список элементов конфигурации, которые используются для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ba50c-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ba50c-124">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="ba50c-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ba50c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ba50c-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ba50c-126">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="ba50c-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ba50c-127">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="ba50c-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
