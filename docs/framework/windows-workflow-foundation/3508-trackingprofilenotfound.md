---
description: 'Дополнительные сведения: 3508-Траккингпрофиленотфаунд'
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 3e97af1689a868fb103b06413a0c4f28b0c1f652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778013"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="34593-103">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="34593-103">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="34593-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="34593-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34593-105">ID</span><span class="sxs-lookup"><span data-stu-id="34593-105">ID</span></span>|<span data-ttu-id="34593-106">3508</span><span class="sxs-lookup"><span data-stu-id="34593-106">3508</span></span>|  
|<span data-ttu-id="34593-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="34593-107">Keywords</span></span>|<span data-ttu-id="34593-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="34593-108">WFServices</span></span>|  
|<span data-ttu-id="34593-109">Level</span><span class="sxs-lookup"><span data-stu-id="34593-109">Level</span></span>|<span data-ttu-id="34593-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="34593-110">Verbose</span></span>|  
|<span data-ttu-id="34593-111">Канал</span><span class="sxs-lookup"><span data-stu-id="34593-111">Channel</span></span>|<span data-ttu-id="34593-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="34593-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34593-113">Описание</span><span class="sxs-lookup"><span data-stu-id="34593-113">Description</span></span>  

 <span data-ttu-id="34593-114">Указывает, что либо профиль TrackingProfile не найден в файле конфигурации, либо обнаружено несоответствие ActivityDefinitionId профилю.</span><span class="sxs-lookup"><span data-stu-id="34593-114">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34593-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="34593-115">Message</span></span>  

 <span data-ttu-id="34593-116">Не найден TrackingProfile «%1» для ActivityDefinitionId «%2».</span><span class="sxs-lookup"><span data-stu-id="34593-116">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="34593-117">Профиль TrackingProfile не найден в файле конфигурации, или обнаружено несоответствие ActivityDefinitionId.</span><span class="sxs-lookup"><span data-stu-id="34593-117">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34593-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="34593-118">Details</span></span>  
  
|<span data-ttu-id="34593-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="34593-119">Data Item Name</span></span>|<span data-ttu-id="34593-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="34593-120">Data Item Type</span></span>|<span data-ttu-id="34593-121">Описание</span><span class="sxs-lookup"><span data-stu-id="34593-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34593-122">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="34593-122">TrackingProfile</span></span>|<span data-ttu-id="34593-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="34593-123">xs:string</span></span>|<span data-ttu-id="34593-124">Имя профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="34593-124">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="34593-125">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="34593-125">ActivityDefinitionId</span></span>|<span data-ttu-id="34593-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="34593-126">xs:string</span></span>|<span data-ttu-id="34593-127">Идентификатор определения действия.</span><span class="sxs-lookup"><span data-stu-id="34593-127">The activity definition id.</span></span>|  
|<span data-ttu-id="34593-128">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="34593-128">AppDomain</span></span>|<span data-ttu-id="34593-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="34593-129">xs:string</span></span>|<span data-ttu-id="34593-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="34593-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
