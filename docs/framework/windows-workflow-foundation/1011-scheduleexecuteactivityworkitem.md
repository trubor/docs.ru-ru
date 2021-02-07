---
description: 'Дополнительные сведения: 1011-Счедуликсекутеактивитиворкитем'
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 81010390de2ad01ec3063f2ac89608b97dcb713e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703358"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="31b22-103">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="31b22-103">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="31b22-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="31b22-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31b22-105">ID</span><span class="sxs-lookup"><span data-stu-id="31b22-105">ID</span></span>|<span data-ttu-id="31b22-106">1011</span><span class="sxs-lookup"><span data-stu-id="31b22-106">1011</span></span>|  
|<span data-ttu-id="31b22-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="31b22-107">Keywords</span></span>|<span data-ttu-id="31b22-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31b22-108">WFRuntime</span></span>|  
|<span data-ttu-id="31b22-109">Level</span><span class="sxs-lookup"><span data-stu-id="31b22-109">Level</span></span>|<span data-ttu-id="31b22-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="31b22-110">Verbose</span></span>|  
|<span data-ttu-id="31b22-111">Канал</span><span class="sxs-lookup"><span data-stu-id="31b22-111">Channel</span></span>|<span data-ttu-id="31b22-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="31b22-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31b22-113">Описание</span><span class="sxs-lookup"><span data-stu-id="31b22-113">Description</span></span>  

 <span data-ttu-id="31b22-114">Указывает, что элемент ExecuteActivityWorkItem запланирован.</span><span class="sxs-lookup"><span data-stu-id="31b22-114">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31b22-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="31b22-115">Message</span></span>  

 <span data-ttu-id="31b22-116">ExecuteActivityWorkItem запланирован для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="31b22-116">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31b22-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="31b22-117">Details</span></span>  
  
|<span data-ttu-id="31b22-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="31b22-118">Data Item Name</span></span>|<span data-ttu-id="31b22-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="31b22-119">Data Item Type</span></span>|<span data-ttu-id="31b22-120">Описание</span><span class="sxs-lookup"><span data-stu-id="31b22-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31b22-121">Действие</span><span class="sxs-lookup"><span data-stu-id="31b22-121">Activity</span></span>|<span data-ttu-id="31b22-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="31b22-122">xs:string</span></span>|<span data-ttu-id="31b22-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="31b22-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="31b22-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="31b22-124">DisplayName</span></span>|<span data-ttu-id="31b22-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="31b22-125">xs:string</span></span>|<span data-ttu-id="31b22-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="31b22-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="31b22-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="31b22-127">InstanceId</span></span>|<span data-ttu-id="31b22-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="31b22-128">xs:string</span></span>|<span data-ttu-id="31b22-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="31b22-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="31b22-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="31b22-130">AppDomain</span></span>|<span data-ttu-id="31b22-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="31b22-131">xs:string</span></span>|<span data-ttu-id="31b22-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="31b22-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
