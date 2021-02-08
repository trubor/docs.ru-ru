---
description: 'Дополнительные сведения: 224-Мессажесроттлеатсевентиперцент'
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 14c08371c5db7e6f7deb0a5851a1d24dfc94475e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794277"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="9ff83-103">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="9ff83-103">224 - MessageThrottleAtSeventyPercent</span></span>

## <a name="properties"></a><span data-ttu-id="9ff83-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="9ff83-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ff83-105">ID</span><span class="sxs-lookup"><span data-stu-id="9ff83-105">ID</span></span>|<span data-ttu-id="9ff83-106">224</span><span class="sxs-lookup"><span data-stu-id="9ff83-106">224</span></span>|  
|<span data-ttu-id="9ff83-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9ff83-107">Keywords</span></span>|<span data-ttu-id="9ff83-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9ff83-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9ff83-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="9ff83-109">Level</span></span>|<span data-ttu-id="9ff83-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="9ff83-110">Warning</span></span>|  
|<span data-ttu-id="9ff83-111">Канал</span><span class="sxs-lookup"><span data-stu-id="9ff83-111">Channel</span></span>|<span data-ttu-id="9ff83-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9ff83-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ff83-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9ff83-113">Description</span></span>  

 <span data-ttu-id="9ff83-114">При превышении одного из основных ограничителей службы создается событие `MessageThrottleExceeded`.</span><span class="sxs-lookup"><span data-stu-id="9ff83-114">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="9ff83-115">Если всплеск активности уменьшился и текущее значение ограничителя составляет 70 процентов от текущего предела, то создается это событие.</span><span class="sxs-lookup"><span data-stu-id="9ff83-115">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="9ff83-116">Обратите внимание, что это событие создается только один раз при замедлении активности.</span><span class="sxs-lookup"><span data-stu-id="9ff83-116">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="9ff83-117">Если текущее значение находится вблизи отметки 70 процентов (например, 70, 69, 70, 71, 69), то только первое значение 70 процентов приводит к созданию события.</span><span class="sxs-lookup"><span data-stu-id="9ff83-117">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="9ff83-118">После возникновения события все последующие превышения предела регулирования приводят к возникновению события `MessageThrottleExceeded`.</span><span class="sxs-lookup"><span data-stu-id="9ff83-118">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ff83-119">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9ff83-119">Message</span></span>  

 <span data-ttu-id="9ff83-120">Предел ограничителя %1 из %2 находится на отметке 70%%.</span><span class="sxs-lookup"><span data-stu-id="9ff83-120">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ff83-121">Сведения</span><span class="sxs-lookup"><span data-stu-id="9ff83-121">Details</span></span>  
  
|<span data-ttu-id="9ff83-122">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="9ff83-122">Data Item Name</span></span>|<span data-ttu-id="9ff83-123">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="9ff83-123">Data Item Type</span></span>|<span data-ttu-id="9ff83-124">Описание</span><span class="sxs-lookup"><span data-stu-id="9ff83-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ff83-125">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="9ff83-125">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="9ff83-126">Имя превышенного ограничителя.</span><span class="sxs-lookup"><span data-stu-id="9ff83-126">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="9ff83-127">`MaxConcurrentCalls`, `MaxConcurrentInstances` либо `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="9ff83-127">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="9ff83-128">Ограничение</span><span class="sxs-lookup"><span data-stu-id="9ff83-128">Limit</span></span>|`xs:long`|<span data-ttu-id="9ff83-129">Заданный в данный момент предел ограничителя.</span><span class="sxs-lookup"><span data-stu-id="9ff83-129">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="9ff83-130">HostReference</span><span class="sxs-lookup"><span data-stu-id="9ff83-130">HostReference</span></span>|`xs:string`|<span data-ttu-id="9ff83-131">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="9ff83-131">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9ff83-132">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="9ff83-132">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9ff83-133">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="9ff83-133">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9ff83-134">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="9ff83-134">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9ff83-135">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ff83-135">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
