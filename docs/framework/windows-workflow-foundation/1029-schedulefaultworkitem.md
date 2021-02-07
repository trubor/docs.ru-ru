---
description: 'Дополнительные сведения: 1029-Счедулефаултворкитем'
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: e5f0463626882d6c8c48412326582fafa7be4670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755451"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="9aabb-103">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="9aabb-103">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="9aabb-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="9aabb-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9aabb-105">ID</span><span class="sxs-lookup"><span data-stu-id="9aabb-105">ID</span></span>|<span data-ttu-id="9aabb-106">1029</span><span class="sxs-lookup"><span data-stu-id="9aabb-106">1029</span></span>|  
|<span data-ttu-id="9aabb-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9aabb-107">Keywords</span></span>|<span data-ttu-id="9aabb-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9aabb-108">WFRuntime</span></span>|  
|<span data-ttu-id="9aabb-109">Level</span><span class="sxs-lookup"><span data-stu-id="9aabb-109">Level</span></span>|<span data-ttu-id="9aabb-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="9aabb-110">Verbose</span></span>|  
|<span data-ttu-id="9aabb-111">Канал</span><span class="sxs-lookup"><span data-stu-id="9aabb-111">Channel</span></span>|<span data-ttu-id="9aabb-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9aabb-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9aabb-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9aabb-113">Description</span></span>  

 <span data-ttu-id="9aabb-114">Указывает, что FaultWorkItem было предназначено.</span><span class="sxs-lookup"><span data-stu-id="9aabb-114">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9aabb-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9aabb-115">Message</span></span>  

 <span data-ttu-id="9aabb-116">Фаултворкитем был запланирован для действия "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="9aabb-116">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9aabb-117">Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="9aabb-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9aabb-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="9aabb-118">Details</span></span>  
  
|<span data-ttu-id="9aabb-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="9aabb-119">Data Item Name</span></span>|<span data-ttu-id="9aabb-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="9aabb-120">Data Item Type</span></span>|<span data-ttu-id="9aabb-121">Описание</span><span class="sxs-lookup"><span data-stu-id="9aabb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9aabb-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="9aabb-122">FaultActivity</span></span>|<span data-ttu-id="9aabb-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-123">xs:string</span></span>|<span data-ttu-id="9aabb-124">Имя типа действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9aabb-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="9aabb-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9aabb-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="9aabb-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-126">xs:string</span></span>|<span data-ttu-id="9aabb-127">Отображаемое имя действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9aabb-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="9aabb-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9aabb-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="9aabb-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-129">xs:string</span></span>|<span data-ttu-id="9aabb-130">Идентификатор экземпляра действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9aabb-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="9aabb-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="9aabb-131">ExceptionActivity</span></span>|<span data-ttu-id="9aabb-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-132">xs:string</span></span>|<span data-ttu-id="9aabb-133">Имя типа действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="9aabb-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aabb-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9aabb-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="9aabb-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-135">xs:string</span></span>|<span data-ttu-id="9aabb-136">Отображаемое имя действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="9aabb-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aabb-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9aabb-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="9aabb-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-138">xs:string</span></span>|<span data-ttu-id="9aabb-139">Идентификатор экземпляра действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="9aabb-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aabb-140">Исключение</span><span class="sxs-lookup"><span data-stu-id="9aabb-140">Exception</span></span>|<span data-ttu-id="9aabb-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-141">xs:string</span></span>|<span data-ttu-id="9aabb-142">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="9aabb-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="9aabb-143">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="9aabb-143">AppDomain</span></span>|<span data-ttu-id="9aabb-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="9aabb-144">xs:string</span></span>|<span data-ttu-id="9aabb-145">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9aabb-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
