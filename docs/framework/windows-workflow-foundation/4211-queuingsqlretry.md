---
description: 'Дополнительные сведения: 4211-Куеуингсклретри'
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: 674914ee105bb0a48f8c32efbd573c685d22d9f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742710"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="e2c78-103">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="e2c78-103">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="e2c78-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="e2c78-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2c78-105">ID</span><span class="sxs-lookup"><span data-stu-id="e2c78-105">ID</span></span>|<span data-ttu-id="e2c78-106">4211</span><span class="sxs-lookup"><span data-stu-id="e2c78-106">4211</span></span>|  
|<span data-ttu-id="e2c78-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e2c78-107">Keywords</span></span>|<span data-ttu-id="e2c78-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e2c78-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="e2c78-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="e2c78-109">Level</span></span>|<span data-ttu-id="e2c78-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="e2c78-110">Warning</span></span>|  
|<span data-ttu-id="e2c78-111">Канал</span><span class="sxs-lookup"><span data-stu-id="e2c78-111">Channel</span></span>|<span data-ttu-id="e2c78-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e2c78-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2c78-113">Описание</span><span class="sxs-lookup"><span data-stu-id="e2c78-113">Description</span></span>  

 <span data-ttu-id="e2c78-114">Указывает на повтор SQL с задержкой.</span><span class="sxs-lookup"><span data-stu-id="e2c78-114">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2c78-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="e2c78-115">Message</span></span>  

 <span data-ttu-id="e2c78-116">Повторная попытка поместить SQL в очередь с задержкой %1 мс.</span><span class="sxs-lookup"><span data-stu-id="e2c78-116">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2c78-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="e2c78-117">Details</span></span>  
  
|<span data-ttu-id="e2c78-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="e2c78-118">Data Item Name</span></span>|<span data-ttu-id="e2c78-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="e2c78-119">Data Item Type</span></span>|<span data-ttu-id="e2c78-120">Описание</span><span class="sxs-lookup"><span data-stu-id="e2c78-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2c78-121">Задержка</span><span class="sxs-lookup"><span data-stu-id="e2c78-121">Delay</span></span>|<span data-ttu-id="e2c78-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c78-122">xs:string</span></span>|<span data-ttu-id="e2c78-123">Задержка между повторными попытками.</span><span class="sxs-lookup"><span data-stu-id="e2c78-123">The delay between retries.</span></span>|  
|<span data-ttu-id="e2c78-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="e2c78-124">AppDomain</span></span>|<span data-ttu-id="e2c78-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c78-125">xs:string</span></span>|<span data-ttu-id="e2c78-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2c78-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
