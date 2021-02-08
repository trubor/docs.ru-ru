---
description: 'Дополнительные сведения: 303-Усердефинединформатионевентоккуред'
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 51c4acd5d10a2d563dd7fbcebf90b75c64ff20ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794238"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="2778c-103">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="2778c-103">303 - UserDefinedInformationEventOccured</span></span>

## <a name="properties"></a><span data-ttu-id="2778c-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="2778c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2778c-105">ID</span><span class="sxs-lookup"><span data-stu-id="2778c-105">ID</span></span>|<span data-ttu-id="2778c-106">303</span><span class="sxs-lookup"><span data-stu-id="2778c-106">303</span></span>|  
|<span data-ttu-id="2778c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2778c-107">Keywords</span></span>|<span data-ttu-id="2778c-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="2778c-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="2778c-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="2778c-109">Level</span></span>|<span data-ttu-id="2778c-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="2778c-110">Information</span></span>|  
|<span data-ttu-id="2778c-111">Канал</span><span class="sxs-lookup"><span data-stu-id="2778c-111">Channel</span></span>|<span data-ttu-id="2778c-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2778c-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2778c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="2778c-113">Description</span></span>  

 <span data-ttu-id="2778c-114">Это событие создается в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="2778c-114">This event is emitted from user code.</span></span> <span data-ttu-id="2778c-115">Разработчик может создавать это событие при возникновении определенных пользователем информационных событий в его службе.</span><span class="sxs-lookup"><span data-stu-id="2778c-115">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="2778c-116">Это можно сделать при помощи API-интерфейсов <xref:System.Diagnostics.Eventing>.</span><span class="sxs-lookup"><span data-stu-id="2778c-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="2778c-117">Помимо этого, есть образец WCF, который включает этот API-интерфейс и показывает, как правильно создать это событие.</span><span class="sxs-lookup"><span data-stu-id="2778c-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2778c-118">Сообщение</span><span class="sxs-lookup"><span data-stu-id="2778c-118">Message</span></span>  

 <span data-ttu-id="2778c-119">Имя: «%1», ссылка: «%2», полезные данные: %3</span><span class="sxs-lookup"><span data-stu-id="2778c-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="2778c-120">Сведения</span><span class="sxs-lookup"><span data-stu-id="2778c-120">Details</span></span>  
  
|<span data-ttu-id="2778c-121">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="2778c-121">Data Item Name</span></span>|<span data-ttu-id="2778c-122">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="2778c-122">Data Item Type</span></span>|<span data-ttu-id="2778c-123">Описание</span><span class="sxs-lookup"><span data-stu-id="2778c-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2778c-124">Имя</span><span class="sxs-lookup"><span data-stu-id="2778c-124">Name</span></span>|`xs:string`|<span data-ttu-id="2778c-125">Определенное пользователем имя события.</span><span class="sxs-lookup"><span data-stu-id="2778c-125">The user-defined name of the event</span></span>|  
|<span data-ttu-id="2778c-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="2778c-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="2778c-127">Для служб, размещенных на веб-узле, это поле служит уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="2778c-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2778c-128">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="2778c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2778c-129">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="2778c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2778c-130">Payload</span><span class="sxs-lookup"><span data-stu-id="2778c-130">Payload</span></span>|`xs:string`|<span data-ttu-id="2778c-131">Определенные пользователем полезные данные события.</span><span class="sxs-lookup"><span data-stu-id="2778c-131">The user-defined payload of the event.</span></span>|
