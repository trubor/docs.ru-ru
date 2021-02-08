---
description: 'Дополнительные сведения: 1014-Счедулекомплетионворкитем'
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 85bbd9b749c1dd34d026d90d708ea7f880665fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792938"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="ab3e0-103">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="ab3e0-103">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="ab3e0-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="ab3e0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab3e0-105">ID</span><span class="sxs-lookup"><span data-stu-id="ab3e0-105">ID</span></span>|<span data-ttu-id="ab3e0-106">1014</span><span class="sxs-lookup"><span data-stu-id="ab3e0-106">1014</span></span>|  
|<span data-ttu-id="ab3e0-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="ab3e0-107">Keywords</span></span>|<span data-ttu-id="ab3e0-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ab3e0-108">WFRuntime</span></span>|  
|<span data-ttu-id="ab3e0-109">Level</span><span class="sxs-lookup"><span data-stu-id="ab3e0-109">Level</span></span>|<span data-ttu-id="ab3e0-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="ab3e0-110">Verbose</span></span>|  
|<span data-ttu-id="ab3e0-111">Канал</span><span class="sxs-lookup"><span data-stu-id="ab3e0-111">Channel</span></span>|<span data-ttu-id="ab3e0-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ab3e0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ab3e0-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ab3e0-113">Description</span></span>  

 <span data-ttu-id="ab3e0-114">Указывает, что элемент CompletionWorkItem был запланирован.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-114">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ab3e0-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="ab3e0-115">Message</span></span>  

 <span data-ttu-id="ab3e0-116">Комплетионворкитем был запланирован для родительского действия "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="ab3e0-116">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ab3e0-117">Завершено действие «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="ab3e0-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ab3e0-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="ab3e0-118">Details</span></span>  
  
|<span data-ttu-id="ab3e0-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="ab3e0-119">Data Item Name</span></span>|<span data-ttu-id="ab3e0-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="ab3e0-120">Data Item Type</span></span>|<span data-ttu-id="ab3e0-121">Описание</span><span class="sxs-lookup"><span data-stu-id="ab3e0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ab3e0-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="ab3e0-122">ParentActivity</span></span>|<span data-ttu-id="ab3e0-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-123">xs:string</span></span>|<span data-ttu-id="ab3e0-124">Имя типа родительского действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="ab3e0-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="ab3e0-125">ParentDisplayName</span></span>|<span data-ttu-id="ab3e0-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-126">xs:string</span></span>|<span data-ttu-id="ab3e0-127">Отображаемое имя родительского действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="ab3e0-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="ab3e0-128">ParentInstanceId</span></span>|<span data-ttu-id="ab3e0-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-129">xs:string</span></span>|<span data-ttu-id="ab3e0-130">Идентификатор экземпляра родительского действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="ab3e0-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="ab3e0-131">CompletedActivity</span></span>|<span data-ttu-id="ab3e0-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-132">xs:string</span></span>|<span data-ttu-id="ab3e0-133">Имя типа завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="ab3e0-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ab3e0-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="ab3e0-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-135">xs:string</span></span>|<span data-ttu-id="ab3e0-136">Отображаемое имя завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="ab3e0-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ab3e0-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="ab3e0-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-138">xs:string</span></span>|<span data-ttu-id="ab3e0-139">Идентификатор экземпляра завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="ab3e0-140">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="ab3e0-140">AppDomain</span></span>|<span data-ttu-id="ab3e0-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="ab3e0-141">xs:string</span></span>|<span data-ttu-id="ab3e0-142">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ab3e0-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
