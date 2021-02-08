---
description: 'Дополнительные сведения: 1019-Комплетеканцелактивитиворкитем'
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 33e58931562d7244987dd8c0d9cf5d34fb894190
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792873"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="4e717-103">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4e717-103">1019 - CompleteCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="4e717-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="4e717-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e717-105">ID</span><span class="sxs-lookup"><span data-stu-id="4e717-105">ID</span></span>|<span data-ttu-id="4e717-106">1019</span><span class="sxs-lookup"><span data-stu-id="4e717-106">1019</span></span>|  
|<span data-ttu-id="4e717-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="4e717-107">Keywords</span></span>|<span data-ttu-id="4e717-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4e717-108">WFRuntime</span></span>|  
|<span data-ttu-id="4e717-109">Level</span><span class="sxs-lookup"><span data-stu-id="4e717-109">Level</span></span>|<span data-ttu-id="4e717-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="4e717-110">Verbose</span></span>|  
|<span data-ttu-id="4e717-111">Канал</span><span class="sxs-lookup"><span data-stu-id="4e717-111">Channel</span></span>|<span data-ttu-id="4e717-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4e717-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e717-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4e717-113">Description</span></span>  

 <span data-ttu-id="4e717-114">Указывает, что CancelActivityWorkItem завершено.</span><span class="sxs-lookup"><span data-stu-id="4e717-114">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e717-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="4e717-115">Message</span></span>  

 <span data-ttu-id="4e717-116">CancelActivityWorkItem завершен для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="4e717-116">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e717-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="4e717-117">Details</span></span>  
  
|<span data-ttu-id="4e717-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="4e717-118">Data Item Name</span></span>|<span data-ttu-id="4e717-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="4e717-119">Data Item Type</span></span>|<span data-ttu-id="4e717-120">Описание</span><span class="sxs-lookup"><span data-stu-id="4e717-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e717-121">Действие</span><span class="sxs-lookup"><span data-stu-id="4e717-121">Activity</span></span>|<span data-ttu-id="4e717-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e717-122">xs:string</span></span>|<span data-ttu-id="4e717-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="4e717-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4e717-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4e717-124">DisplayName</span></span>|<span data-ttu-id="4e717-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e717-125">xs:string</span></span>|<span data-ttu-id="4e717-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="4e717-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4e717-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4e717-127">InstanceId</span></span>|<span data-ttu-id="4e717-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e717-128">xs:string</span></span>|<span data-ttu-id="4e717-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="4e717-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4e717-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="4e717-130">AppDomain</span></span>|<span data-ttu-id="4e717-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e717-131">xs:string</span></span>|<span data-ttu-id="4e717-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4e717-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
