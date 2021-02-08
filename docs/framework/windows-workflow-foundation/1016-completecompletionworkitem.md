---
description: 'Дополнительные сведения: 1016-Комплетекомплетионворкитем'
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 849e192d63b5db19e5beea31befcdc38d4340c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792912"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="9ac5e-103">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="9ac5e-103">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="9ac5e-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="9ac5e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ac5e-105">ID</span><span class="sxs-lookup"><span data-stu-id="9ac5e-105">ID</span></span>|<span data-ttu-id="9ac5e-106">1016</span><span class="sxs-lookup"><span data-stu-id="9ac5e-106">1016</span></span>|  
|<span data-ttu-id="9ac5e-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9ac5e-107">Keywords</span></span>|<span data-ttu-id="9ac5e-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ac5e-108">WFRuntime</span></span>|  
|<span data-ttu-id="9ac5e-109">Level</span><span class="sxs-lookup"><span data-stu-id="9ac5e-109">Level</span></span>|<span data-ttu-id="9ac5e-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="9ac5e-110">Verbose</span></span>|  
|<span data-ttu-id="9ac5e-111">Канал</span><span class="sxs-lookup"><span data-stu-id="9ac5e-111">Channel</span></span>|<span data-ttu-id="9ac5e-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9ac5e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ac5e-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9ac5e-113">Description</span></span>  

 <span data-ttu-id="9ac5e-114">Указывает на завершение CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-114">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ac5e-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9ac5e-115">Message</span></span>  

 <span data-ttu-id="9ac5e-116">CompletionWorkItem завершен для родительского действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="9ac5e-116">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="9ac5e-117">Завершено действие «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="9ac5e-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ac5e-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="9ac5e-118">Details</span></span>  
  
|<span data-ttu-id="9ac5e-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="9ac5e-119">Data Item Name</span></span>|<span data-ttu-id="9ac5e-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="9ac5e-120">Data Item Type</span></span>|<span data-ttu-id="9ac5e-121">Описание</span><span class="sxs-lookup"><span data-stu-id="9ac5e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ac5e-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="9ac5e-122">ParentActivity</span></span>|<span data-ttu-id="9ac5e-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-123">xs:string</span></span>|<span data-ttu-id="9ac5e-124">Имя типа родительского действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="9ac5e-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="9ac5e-125">ParentDisplayName</span></span>|<span data-ttu-id="9ac5e-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-126">xs:string</span></span>|<span data-ttu-id="9ac5e-127">Отображаемое имя родительского действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="9ac5e-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="9ac5e-128">ParentInstanceId</span></span>|<span data-ttu-id="9ac5e-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-129">xs:string</span></span>|<span data-ttu-id="9ac5e-130">Идентификатор экземпляра родительского действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="9ac5e-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="9ac5e-131">CompletedActivity</span></span>|<span data-ttu-id="9ac5e-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-132">xs:string</span></span>|<span data-ttu-id="9ac5e-133">Имя типа завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="9ac5e-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9ac5e-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="9ac5e-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-135">xs:string</span></span>|<span data-ttu-id="9ac5e-136">Отображаемое имя завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="9ac5e-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9ac5e-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="9ac5e-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-138">xs:string</span></span>|<span data-ttu-id="9ac5e-139">Идентификатор экземпляра завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="9ac5e-140">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="9ac5e-140">AppDomain</span></span>|<span data-ttu-id="9ac5e-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac5e-141">xs:string</span></span>|<span data-ttu-id="9ac5e-142">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ac5e-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
