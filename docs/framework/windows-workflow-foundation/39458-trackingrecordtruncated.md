---
description: 'Дополнительные сведения: 39458-Траккингрекордтрункатед'
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: bb9a46dc5bd9bc4f4709a740dd0e7ec47ca826e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631285"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="e668c-103">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="e668c-103">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="e668c-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="e668c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e668c-105">ID</span><span class="sxs-lookup"><span data-stu-id="e668c-105">ID</span></span>|<span data-ttu-id="e668c-106">39458</span><span class="sxs-lookup"><span data-stu-id="e668c-106">39458</span></span>|  
|<span data-ttu-id="e668c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e668c-107">Keywords</span></span>|<span data-ttu-id="e668c-108">WFTracking</span><span class="sxs-lookup"><span data-stu-id="e668c-108">WFTracking</span></span>|  
|<span data-ttu-id="e668c-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="e668c-109">Level</span></span>|<span data-ttu-id="e668c-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="e668c-110">Warning</span></span>|  
|<span data-ttu-id="e668c-111">Канал</span><span class="sxs-lookup"><span data-stu-id="e668c-111">Channel</span></span>|<span data-ttu-id="e668c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e668c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e668c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="e668c-113">Description</span></span>  

 <span data-ttu-id="e668c-114">Указывает, что запись отслеживания была усечена.</span><span class="sxs-lookup"><span data-stu-id="e668c-114">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="e668c-115">Данные переменных, заметок, пользователей удалены.</span><span class="sxs-lookup"><span data-stu-id="e668c-115">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e668c-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="e668c-116">Message</span></span>  

 <span data-ttu-id="e668c-117">Усеченная запись отслеживания %1 записана в сеанс трассировки событий Windows с использованием поставщика %2.</span><span class="sxs-lookup"><span data-stu-id="e668c-117">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="e668c-118">Данные переменных, заметок, пользователей удалены</span><span class="sxs-lookup"><span data-stu-id="e668c-118">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="e668c-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="e668c-119">Details</span></span>  
  
|<span data-ttu-id="e668c-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="e668c-120">Data Item Name</span></span>|<span data-ttu-id="e668c-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="e668c-121">Data Item Type</span></span>|<span data-ttu-id="e668c-122">Описание</span><span class="sxs-lookup"><span data-stu-id="e668c-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e668c-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="e668c-123">RecordNumber</span></span>|<span data-ttu-id="e668c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e668c-124">xs:string</span></span>|<span data-ttu-id="e668c-125">Номер записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="e668c-125">The tracking record number.</span></span>|  
|<span data-ttu-id="e668c-126">ProviderId</span><span class="sxs-lookup"><span data-stu-id="e668c-126">ProviderId</span></span>|<span data-ttu-id="e668c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e668c-127">xs:string</span></span>|<span data-ttu-id="e668c-128">Идентификатор поставщика трассировки событий Windows.</span><span class="sxs-lookup"><span data-stu-id="e668c-128">The ETW provider id.</span></span>|  
|<span data-ttu-id="e668c-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="e668c-129">AppDomain</span></span>|<span data-ttu-id="e668c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e668c-130">xs:string</span></span>|<span data-ttu-id="e668c-131">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e668c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
