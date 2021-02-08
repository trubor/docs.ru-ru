---
description: 'Дополнительные сведения: 1015-Старткомплетионворкитем'
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6c79a02b144aa1176eb1cb334c8430c8f0babc3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792925"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="f1c48-103">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="f1c48-103">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="f1c48-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="f1c48-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1c48-105">ID</span><span class="sxs-lookup"><span data-stu-id="f1c48-105">ID</span></span>|<span data-ttu-id="f1c48-106">1015</span><span class="sxs-lookup"><span data-stu-id="f1c48-106">1015</span></span>|  
|<span data-ttu-id="f1c48-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f1c48-107">Keywords</span></span>|<span data-ttu-id="f1c48-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f1c48-108">WFRuntime</span></span>|  
|<span data-ttu-id="f1c48-109">Level</span><span class="sxs-lookup"><span data-stu-id="f1c48-109">Level</span></span>|<span data-ttu-id="f1c48-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="f1c48-110">Verbose</span></span>|  
|<span data-ttu-id="f1c48-111">Канал</span><span class="sxs-lookup"><span data-stu-id="f1c48-111">Channel</span></span>|<span data-ttu-id="f1c48-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f1c48-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f1c48-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f1c48-113">Description</span></span>  

 <span data-ttu-id="f1c48-114">Указывает, что выполнение CompletionWorkItem начинается.</span><span class="sxs-lookup"><span data-stu-id="f1c48-114">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f1c48-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="f1c48-115">Message</span></span>  

 <span data-ttu-id="f1c48-116">Начато выполнение CompletionWorkItem для родительского действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="f1c48-116">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="f1c48-117">Завершено действие «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="f1c48-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f1c48-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="f1c48-118">Details</span></span>  
  
|<span data-ttu-id="f1c48-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="f1c48-119">Data Item Name</span></span>|<span data-ttu-id="f1c48-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="f1c48-120">Data Item Type</span></span>|<span data-ttu-id="f1c48-121">Описание</span><span class="sxs-lookup"><span data-stu-id="f1c48-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f1c48-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="f1c48-122">ParentActivity</span></span>|<span data-ttu-id="f1c48-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-123">xs:string</span></span>|<span data-ttu-id="f1c48-124">Имя типа родительского действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="f1c48-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="f1c48-125">ParentDisplayName</span></span>|<span data-ttu-id="f1c48-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-126">xs:string</span></span>|<span data-ttu-id="f1c48-127">Отображаемое имя родительского действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="f1c48-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="f1c48-128">ParentInstanceId</span></span>|<span data-ttu-id="f1c48-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-129">xs:string</span></span>|<span data-ttu-id="f1c48-130">Идентификатор экземпляра родительского действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="f1c48-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="f1c48-131">CompletedActivity</span></span>|<span data-ttu-id="f1c48-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-132">xs:string</span></span>|<span data-ttu-id="f1c48-133">Имя типа завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="f1c48-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f1c48-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="f1c48-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-135">xs:string</span></span>|<span data-ttu-id="f1c48-136">Отображаемое имя завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="f1c48-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f1c48-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="f1c48-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-138">xs:string</span></span>|<span data-ttu-id="f1c48-139">Идентификатор экземпляра завершенного действия.</span><span class="sxs-lookup"><span data-stu-id="f1c48-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="f1c48-140">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="f1c48-140">AppDomain</span></span>|<span data-ttu-id="f1c48-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="f1c48-141">xs:string</span></span>|<span data-ttu-id="f1c48-142">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f1c48-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
