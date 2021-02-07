---
description: 'Дополнительные сведения: <faultPropagationQuery>'
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 08786bfa66d74f5f29353c4d6a86a2abd34df8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748704"
---
# \<faultPropagationQuery>

<span data-ttu-id="ab04b-102">Представляет запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ab04b-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ab04b-103">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="ab04b-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ab04b-104">Такой запрос следует использовать для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ab04b-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ab04b-105">Этот запрос необходим, чтобы участник отслеживания подписался на записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="ab04b-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="ab04b-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ab04b-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="ab04b-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab04b-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ab04b-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ab04b-108">Attributes and Elements</span></span>

<span data-ttu-id="ab04b-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ab04b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab04b-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ab04b-110">Attributes</span></span>

|<span data-ttu-id="ab04b-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ab04b-111">Attribute</span></span>|<span data-ttu-id="ab04b-112">Описание</span><span class="sxs-lookup"><span data-stu-id="ab04b-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ab04b-113">activityName</span><span class="sxs-lookup"><span data-stu-id="ab04b-113">activityName</span></span>|<span data-ttu-id="ab04b-114">Строка, указывающая имя действия обработчика сбоев, которое распространило ошибку.</span><span class="sxs-lookup"><span data-stu-id="ab04b-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="ab04b-115">Значение по умолчанию - «\*», которое указывает на то, что записи распространения ошибок возвращаются для всех действий.</span><span class="sxs-lookup"><span data-stu-id="ab04b-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="ab04b-116">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="ab04b-116">faultHandlerActivityName</span></span>|<span data-ttu-id="ab04b-117">Строка, указывающая имя действия, ставшего источником ошибки.</span><span class="sxs-lookup"><span data-stu-id="ab04b-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ab04b-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ab04b-118">Child Elements</span></span>

<span data-ttu-id="ab04b-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ab04b-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab04b-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ab04b-120">Parent Elements</span></span>

|<span data-ttu-id="ab04b-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="ab04b-121">Element</span></span>|<span data-ttu-id="ab04b-122">Описание</span><span class="sxs-lookup"><span data-stu-id="ab04b-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="ab04b-123">Представляет список элементов конфигурации, которые используются для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="ab04b-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ab04b-124">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="ab04b-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ab04b-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ab04b-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ab04b-126">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="ab04b-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ab04b-127">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="ab04b-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
