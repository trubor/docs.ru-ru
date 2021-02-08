---
description: 'Дополнительные сведения: 1020-CreateBookmark'
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 39796eaf68d9cb52e9faa2605fc21955a2c167ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792847"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="ad258-103">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="ad258-103">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="ad258-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="ad258-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad258-105">ID</span><span class="sxs-lookup"><span data-stu-id="ad258-105">ID</span></span>|<span data-ttu-id="ad258-106">1020</span><span class="sxs-lookup"><span data-stu-id="ad258-106">1020</span></span>|  
|<span data-ttu-id="ad258-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="ad258-107">Keywords</span></span>|<span data-ttu-id="ad258-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ad258-108">WFRuntime</span></span>|  
|<span data-ttu-id="ad258-109">Level</span><span class="sxs-lookup"><span data-stu-id="ad258-109">Level</span></span>|<span data-ttu-id="ad258-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="ad258-110">Verbose</span></span>|  
|<span data-ttu-id="ad258-111">Канал</span><span class="sxs-lookup"><span data-stu-id="ad258-111">Channel</span></span>|<span data-ttu-id="ad258-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ad258-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad258-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ad258-113">Description</span></span>  

 <span data-ttu-id="ad258-114">Указывает, что для действия создана закладка.</span><span class="sxs-lookup"><span data-stu-id="ad258-114">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad258-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="ad258-115">Message</span></span>  

 <span data-ttu-id="ad258-116">Создана закладка для действия "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="ad258-116">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ad258-117">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="ad258-117">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad258-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="ad258-118">Details</span></span>  
  
|<span data-ttu-id="ad258-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="ad258-119">Data Item Name</span></span>|<span data-ttu-id="ad258-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="ad258-120">Data Item Type</span></span>|<span data-ttu-id="ad258-121">Описание</span><span class="sxs-lookup"><span data-stu-id="ad258-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad258-122">Действие</span><span class="sxs-lookup"><span data-stu-id="ad258-122">Activity</span></span>|<span data-ttu-id="ad258-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-123">xs:string</span></span>|<span data-ttu-id="ad258-124">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="ad258-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="ad258-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ad258-125">DisplayName</span></span>|<span data-ttu-id="ad258-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-126">xs:string</span></span>|<span data-ttu-id="ad258-127">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="ad258-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="ad258-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ad258-128">InstanceId</span></span>|<span data-ttu-id="ad258-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-129">xs:string</span></span>|<span data-ttu-id="ad258-130">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="ad258-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ad258-131">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="ad258-131">BookmarkName</span></span>|<span data-ttu-id="ad258-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-132">xs:string</span></span>|<span data-ttu-id="ad258-133">Имя закладки.</span><span class="sxs-lookup"><span data-stu-id="ad258-133">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ad258-134">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ad258-134">BookmarkScope</span></span>|<span data-ttu-id="ad258-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-135">xs:string</span></span>|<span data-ttu-id="ad258-136">Область закладки.</span><span class="sxs-lookup"><span data-stu-id="ad258-136">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ad258-137">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="ad258-137">AppDomain</span></span>|<span data-ttu-id="ad258-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad258-138">xs:string</span></span>|<span data-ttu-id="ad258-139">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ad258-139">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
