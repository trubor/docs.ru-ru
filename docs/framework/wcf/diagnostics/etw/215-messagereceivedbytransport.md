---
description: 'Дополнительные сведения: 215-Мессажерецеиведбитранспорт'
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: e9645cfc8c4013f8891cb645db7df35477a57412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794368"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="8a861-103">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="8a861-103">215 - MessageReceivedByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="8a861-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="8a861-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a861-105">ID</span><span class="sxs-lookup"><span data-stu-id="8a861-105">ID</span></span>|<span data-ttu-id="8a861-106">215</span><span class="sxs-lookup"><span data-stu-id="8a861-106">215</span></span>|  
|<span data-ttu-id="8a861-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8a861-107">Keywords</span></span>|<span data-ttu-id="8a861-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8a861-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8a861-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="8a861-109">Level</span></span>|<span data-ttu-id="8a861-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="8a861-110">Information</span></span>|  
|<span data-ttu-id="8a861-111">Канал</span><span class="sxs-lookup"><span data-stu-id="8a861-111">Channel</span></span>|<span data-ttu-id="8a861-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8a861-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8a861-113">Описание</span><span class="sxs-lookup"><span data-stu-id="8a861-113">Description</span></span>  

 <span data-ttu-id="8a861-114">Это событие происходит, когда транспорт на основе TCP получает сообщение.</span><span class="sxs-lookup"><span data-stu-id="8a861-114">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="8a861-115">Обратите внимание, что на транспортном уровне для одной операции между клиентом и службой может быть передано несколько сообщений.</span><span class="sxs-lookup"><span data-stu-id="8a861-115">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="8a861-116">Это может зависеть от инфраструктуры, и требования безопасности - хороший пример.</span><span class="sxs-lookup"><span data-stu-id="8a861-116">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="8a861-117">Следовательно, количество создаваемых событий `MessageReceivedByTransport` может отличаться в зависимости от привязки службы и ее настроек.</span><span class="sxs-lookup"><span data-stu-id="8a861-117">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a861-118">Это событие не создается для односторонних транспортов.</span><span class="sxs-lookup"><span data-stu-id="8a861-118">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8a861-119">Сообщение</span><span class="sxs-lookup"><span data-stu-id="8a861-119">Message</span></span>  

 <span data-ttu-id="8a861-120">Диспетчер получил сообщение от «%1».</span><span class="sxs-lookup"><span data-stu-id="8a861-120">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8a861-121">Сведения</span><span class="sxs-lookup"><span data-stu-id="8a861-121">Details</span></span>  
  
|<span data-ttu-id="8a861-122">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="8a861-122">Data Item Name</span></span>|<span data-ttu-id="8a861-123">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="8a861-123">Data Item Type</span></span>|<span data-ttu-id="8a861-124">Описание</span><span class="sxs-lookup"><span data-stu-id="8a861-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8a861-125">Listen Address</span><span class="sxs-lookup"><span data-stu-id="8a861-125">Listen Address</span></span>|`xs:string`|<span data-ttu-id="8a861-126">Адрес, получивший сообщение.</span><span class="sxs-lookup"><span data-stu-id="8a861-126">The address that received the message.</span></span>|  
|<span data-ttu-id="8a861-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="8a861-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="8a861-128">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="8a861-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8a861-129">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8a861-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8a861-130">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="8a861-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8a861-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="8a861-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8a861-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8a861-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
