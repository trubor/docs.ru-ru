---
description: 'Дополнительные сведения: 1009-Активитисчедулед'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755555"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="18b21-103">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="18b21-103">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="18b21-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="18b21-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18b21-105">ID</span><span class="sxs-lookup"><span data-stu-id="18b21-105">ID</span></span>|<span data-ttu-id="18b21-106">1009</span><span class="sxs-lookup"><span data-stu-id="18b21-106">1009</span></span>|  
|<span data-ttu-id="18b21-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="18b21-107">Keywords</span></span>|<span data-ttu-id="18b21-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="18b21-108">WFRuntime</span></span>|  
|<span data-ttu-id="18b21-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="18b21-109">Level</span></span>|<span data-ttu-id="18b21-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="18b21-110">Information</span></span>|  
|<span data-ttu-id="18b21-111">Канал</span><span class="sxs-lookup"><span data-stu-id="18b21-111">Channel</span></span>|<span data-ttu-id="18b21-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="18b21-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="18b21-113">Описание</span><span class="sxs-lookup"><span data-stu-id="18b21-113">Description</span></span>  

 <span data-ttu-id="18b21-114">Указывает, что действие запланировано для выполнения.</span><span class="sxs-lookup"><span data-stu-id="18b21-114">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="18b21-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="18b21-115">Message</span></span>  

 <span data-ttu-id="18b21-116">Родительское действие «%1» (отображаемое имя «%2», ИД экземпляра «%3») запланировало дочернее действие «%4» (отображаемое имя «%5», ИД экземпляра «%6»).</span><span class="sxs-lookup"><span data-stu-id="18b21-116">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="18b21-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="18b21-117">Details</span></span>  
  
|<span data-ttu-id="18b21-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="18b21-118">Data Item Name</span></span>|<span data-ttu-id="18b21-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="18b21-119">Data Item Type</span></span>|<span data-ttu-id="18b21-120">Описание</span><span class="sxs-lookup"><span data-stu-id="18b21-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="18b21-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="18b21-121">ParentActivity</span></span>|<span data-ttu-id="18b21-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-122">xs:string</span></span>|<span data-ttu-id="18b21-123">Имя типа родительского действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="18b21-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="18b21-124">ParentDisplayName</span></span>|<span data-ttu-id="18b21-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-125">xs:string</span></span>|<span data-ttu-id="18b21-126">Отображаемое имя родительского действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="18b21-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="18b21-127">ParentInstanceId</span></span>|<span data-ttu-id="18b21-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-128">xs:string</span></span>|<span data-ttu-id="18b21-129">Идентификатор экземпляра родительского действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="18b21-130">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="18b21-130">ChildActivity</span></span>|<span data-ttu-id="18b21-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-131">xs:string</span></span>|<span data-ttu-id="18b21-132">Имя типа запланированного дочернего действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-132">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="18b21-133">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="18b21-133">ChildDisplayName</span></span>|<span data-ttu-id="18b21-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-134">xs:string</span></span>|<span data-ttu-id="18b21-135">Отображаемое имя запланированного дочернего действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-135">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="18b21-136">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="18b21-136">ChildInstanceId</span></span>|<span data-ttu-id="18b21-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-137">xs:string</span></span>|<span data-ttu-id="18b21-138">Идентификатор экземпляра запланированного дочернего действия.</span><span class="sxs-lookup"><span data-stu-id="18b21-138">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="18b21-139">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="18b21-139">AppDomain</span></span>|<span data-ttu-id="18b21-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="18b21-140">xs:string</span></span>|<span data-ttu-id="18b21-141">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="18b21-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
