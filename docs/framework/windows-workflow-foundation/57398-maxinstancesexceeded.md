---
description: 'Дополнительные сведения: 57398-Максинстанцесексцеедед'
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: 104c466cb2e0ee8156e2b268caf5e757353dfb09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720232"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="57fe3-103">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="57fe3-103">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="57fe3-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="57fe3-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57fe3-105">ID</span><span class="sxs-lookup"><span data-stu-id="57fe3-105">ID</span></span>|<span data-ttu-id="57fe3-106">57398</span><span class="sxs-lookup"><span data-stu-id="57fe3-106">57398</span></span>|  
|<span data-ttu-id="57fe3-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="57fe3-107">Keywords</span></span>|<span data-ttu-id="57fe3-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="57fe3-108">WFServices</span></span>|  
|<span data-ttu-id="57fe3-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="57fe3-109">Level</span></span>|<span data-ttu-id="57fe3-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="57fe3-110">Warning</span></span>|  
|<span data-ttu-id="57fe3-111">Канал</span><span class="sxs-lookup"><span data-stu-id="57fe3-111">Channel</span></span>|<span data-ttu-id="57fe3-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="57fe3-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57fe3-113">Описание</span><span class="sxs-lookup"><span data-stu-id="57fe3-113">Description</span></span>  

 <span data-ttu-id="57fe3-114">Указывает, что система достигла предела, заданного для ограничителя MaxConcurrentInstances.</span><span class="sxs-lookup"><span data-stu-id="57fe3-114">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57fe3-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="57fe3-115">Message</span></span>  

 <span data-ttu-id="57fe3-116">Система достигла предела, заданного для ограничителя «MaxConcurrentInstances».</span><span class="sxs-lookup"><span data-stu-id="57fe3-116">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="57fe3-117">Для этого ограничителя был задан предел %1.</span><span class="sxs-lookup"><span data-stu-id="57fe3-117">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="57fe3-118">Значение ограничителя можно изменить, изменив атрибут maxConcurrentInstances в элементе serviceThrottle или свойство MaxConcurrentInstances для поведения ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="57fe3-118">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57fe3-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="57fe3-119">Details</span></span>  
  
|<span data-ttu-id="57fe3-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="57fe3-120">Data Item Name</span></span>|<span data-ttu-id="57fe3-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="57fe3-121">Data Item Type</span></span>|<span data-ttu-id="57fe3-122">Описание</span><span class="sxs-lookup"><span data-stu-id="57fe3-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57fe3-123">Имя</span><span class="sxs-lookup"><span data-stu-id="57fe3-123">Name</span></span>|<span data-ttu-id="57fe3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="57fe3-124">xs:string</span></span>|<span data-ttu-id="57fe3-125">Имя элемента.</span><span class="sxs-lookup"><span data-stu-id="57fe3-125">The name of the item.</span></span>|  
|<span data-ttu-id="57fe3-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="57fe3-126">AppDomain</span></span>|<span data-ttu-id="57fe3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="57fe3-127">xs:string</span></span>|<span data-ttu-id="57fe3-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="57fe3-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
