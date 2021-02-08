---
description: 'Дополнительные сведения о: <activityStateQueries> из WCF'
title: <activityStateQueries> WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 00795a26a37f62fae8aa884b5a4188be79453186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782238"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="e6028-103">\<activityStateQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="e6028-103">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="e6028-104">Представляет коллекцию запросов, которые используются для отслеживания изменений жизненного цикла действий, составляющих экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="e6028-104">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="e6028-105">Например, вы можете захотеть отследить каждый раз, когда действие "отправить электронное письмо" завершается в рамках экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="e6028-105">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="e6028-106">Этот запрос необходим, чтобы участник отслеживания мог подписываться на объекты записей состояния действия.</span><span class="sxs-lookup"><span data-stu-id="e6028-106">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="e6028-107">Состояния, доступные для подписки, указаны в ActivtyStates.</span><span class="sxs-lookup"><span data-stu-id="e6028-107">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="e6028-108">Дополнительные сведения о запросах профиля отслеживания см. в разделе [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6028-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="e6028-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6028-109">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="e6028-110">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="e6028-110">Attributes and elements</span></span>

<span data-ttu-id="e6028-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e6028-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e6028-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e6028-112">Attributes</span></span>  

<span data-ttu-id="e6028-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e6028-113">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="e6028-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e6028-114">Child elements</span></span>

|<span data-ttu-id="e6028-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6028-115">Element</span></span>|<span data-ttu-id="e6028-116">Описание</span><span class="sxs-lookup"><span data-stu-id="e6028-116">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="e6028-117">Запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="e6028-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e6028-118">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e6028-118">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6028-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e6028-119">Parent elements</span></span>

|<span data-ttu-id="e6028-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6028-120">Element</span></span>|<span data-ttu-id="e6028-121">Описание</span><span class="sxs-lookup"><span data-stu-id="e6028-121">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e6028-122">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="e6028-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e6028-123">См. также</span><span class="sxs-lookup"><span data-stu-id="e6028-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="e6028-124">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="e6028-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e6028-125">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="e6028-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
