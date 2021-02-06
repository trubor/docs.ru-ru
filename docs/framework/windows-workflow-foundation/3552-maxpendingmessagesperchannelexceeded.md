---
description: 'Дополнительные сведения: 3552-Макспендингмессажесперчаннелексцеедед'
title: 3552 – MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: 5fb2d27f7d68716cebf2cfaafd21851226a456e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631441"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="08468-103">3552 – MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="08468-103">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="08468-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="08468-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08468-105">ID</span><span class="sxs-lookup"><span data-stu-id="08468-105">ID</span></span>|<span data-ttu-id="08468-106">3552</span><span class="sxs-lookup"><span data-stu-id="08468-106">3552</span></span>|  
|<span data-ttu-id="08468-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="08468-107">Keywords</span></span>|<span data-ttu-id="08468-108">Quota, WFServices</span><span class="sxs-lookup"><span data-stu-id="08468-108">Quota, WFServices</span></span>|  
|<span data-ttu-id="08468-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="08468-109">Level</span></span>|<span data-ttu-id="08468-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="08468-110">Warning</span></span>|  
|<span data-ttu-id="08468-111">Канал</span><span class="sxs-lookup"><span data-stu-id="08468-111">Channel</span></span>|<span data-ttu-id="08468-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="08468-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08468-113">Описание</span><span class="sxs-lookup"><span data-stu-id="08468-113">Description</span></span>  

 <span data-ttu-id="08468-114">Указывает, что был достигнут предел регулирования «MaxPendingMessagesPerChannel».</span><span class="sxs-lookup"><span data-stu-id="08468-114">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08468-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="08468-115">Message</span></span>  

 <span data-ttu-id="08468-116">Был достигнут предел регулирования «MaxPendingMessagesPerChannel» для «%1».</span><span class="sxs-lookup"><span data-stu-id="08468-116">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="08468-117">Для увеличения этого предела настройте свойство MaxPendingMessagesPerChannel для поведения BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="08468-117">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08468-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="08468-118">Details</span></span>  
  
|<span data-ttu-id="08468-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="08468-119">Data Item Name</span></span>|<span data-ttu-id="08468-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="08468-120">Data Item Type</span></span>|<span data-ttu-id="08468-121">Описание</span><span class="sxs-lookup"><span data-stu-id="08468-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08468-122">Ограничение</span><span class="sxs-lookup"><span data-stu-id="08468-122">Limit</span></span>|<span data-ttu-id="08468-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="08468-123">xs:string</span></span>|<span data-ttu-id="08468-124">Был достигнут предел регулирования «MaxPendingMessagesPerChannel».</span><span class="sxs-lookup"><span data-stu-id="08468-124">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="08468-125">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="08468-125">AppDomain</span></span>|<span data-ttu-id="08468-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="08468-126">xs:string</span></span>|<span data-ttu-id="08468-127">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="08468-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
