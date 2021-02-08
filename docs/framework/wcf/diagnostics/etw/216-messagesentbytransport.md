---
description: 'Дополнительные сведения: 216-Мессажесентбитранспорт'
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: 34c10fbbf61adde102641cb44db6645ea648a646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794381"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="f8546-103">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="f8546-103">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="f8546-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="f8546-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8546-105">ID</span><span class="sxs-lookup"><span data-stu-id="f8546-105">ID</span></span>|<span data-ttu-id="f8546-106">216</span><span class="sxs-lookup"><span data-stu-id="f8546-106">216</span></span>|  
|<span data-ttu-id="f8546-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f8546-107">Keywords</span></span>|<span data-ttu-id="f8546-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f8546-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f8546-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="f8546-109">Level</span></span>|<span data-ttu-id="f8546-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="f8546-110">Information</span></span>|  
|<span data-ttu-id="f8546-111">Канал</span><span class="sxs-lookup"><span data-stu-id="f8546-111">Channel</span></span>|<span data-ttu-id="f8546-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f8546-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f8546-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f8546-113">Description</span></span>  

 <span data-ttu-id="f8546-114">Это событие возникает при отправке сообщения транспортом на основе TCP.</span><span class="sxs-lookup"><span data-stu-id="f8546-114">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="f8546-115">Обратите внимание, что в рамках одной операции между клиентом и службой может быть передано несколько сообщений уровня транспорта.</span><span class="sxs-lookup"><span data-stu-id="f8546-115">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="f8546-116">Это может быть вызвано особенностями инфраструктуры (и требования безопасности - хороший пример).</span><span class="sxs-lookup"><span data-stu-id="f8546-116">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="f8546-117">Таким образом, количество выдаваемых событий **мессажесентбитранспорт** зависит от привязки службы и ее конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f8546-117">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f8546-118">Сообщение</span><span class="sxs-lookup"><span data-stu-id="f8546-118">Message</span></span>  

 <span data-ttu-id="f8546-119">Транспорт отправил сообщение «%1».</span><span class="sxs-lookup"><span data-stu-id="f8546-119">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f8546-120">Сведения</span><span class="sxs-lookup"><span data-stu-id="f8546-120">Details</span></span>  
  
|<span data-ttu-id="f8546-121">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="f8546-121">Data Item Name</span></span>|<span data-ttu-id="f8546-122">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="f8546-122">Data Item Type</span></span>|<span data-ttu-id="f8546-123">Описание</span><span class="sxs-lookup"><span data-stu-id="f8546-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f8546-124">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="f8546-124">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="f8546-125">Адрес, на который было отправлено сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="f8546-125">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="f8546-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="f8546-126">HostReference</span></span>|<span data-ttu-id="f8546-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8546-127">xs:string</span></span>|<span data-ttu-id="f8546-128">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="f8546-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f8546-129">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="f8546-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f8546-130">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="f8546-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f8546-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="f8546-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f8546-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f8546-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
