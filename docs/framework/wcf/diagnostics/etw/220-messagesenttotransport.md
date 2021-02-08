---
description: 'Дополнительные сведения: 220-Мессажесенттотранспорт'
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 8d76f147c8a31a5aa08c21073cd03e63436095ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794316"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="613fb-103">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="613fb-103">220 - MessageSentToTransport</span></span>

## <a name="properties"></a><span data-ttu-id="613fb-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="613fb-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="613fb-105">Идентификатор</span><span class="sxs-lookup"><span data-stu-id="613fb-105">Id</span></span>|<span data-ttu-id="613fb-106">220</span><span class="sxs-lookup"><span data-stu-id="613fb-106">220</span></span>|  
|<span data-ttu-id="613fb-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="613fb-107">Keywords</span></span>|<span data-ttu-id="613fb-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="613fb-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="613fb-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="613fb-109">Level</span></span>|<span data-ttu-id="613fb-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="613fb-110">Information</span></span>|  
|<span data-ttu-id="613fb-111">Канал</span><span class="sxs-lookup"><span data-stu-id="613fb-111">Channel</span></span>|<span data-ttu-id="613fb-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="613fb-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="613fb-113">Описание</span><span class="sxs-lookup"><span data-stu-id="613fb-113">Description</span></span>  

 <span data-ttu-id="613fb-114">Это событие создается, когда модель службы отправляет сообщение в транспорт.</span><span class="sxs-lookup"><span data-stu-id="613fb-114">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="613fb-115">Это событие не создается для односторонних транспортов.</span><span class="sxs-lookup"><span data-stu-id="613fb-115">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="613fb-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="613fb-116">Message</span></span>  

 <span data-ttu-id="613fb-117">Диспетчер отправил сообщение транспорту.</span><span class="sxs-lookup"><span data-stu-id="613fb-117">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="613fb-118">Идентификатор корреляции == «%1».</span><span class="sxs-lookup"><span data-stu-id="613fb-118">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="613fb-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="613fb-119">Details</span></span>  
  
|<span data-ttu-id="613fb-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="613fb-120">Data Item Name</span></span>|<span data-ttu-id="613fb-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="613fb-121">Data Item Type</span></span>|<span data-ttu-id="613fb-122">Описание</span><span class="sxs-lookup"><span data-stu-id="613fb-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="613fb-123">Идентификатор корреляции</span><span class="sxs-lookup"><span data-stu-id="613fb-123">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="613fb-124">Идентификатор действия, используемый для корреляции события `MessageSentToTransport` из службы или клиента с соответствующим транспортом `MessageReceivedFromTransport` на другом конце.</span><span class="sxs-lookup"><span data-stu-id="613fb-124">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="613fb-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="613fb-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="613fb-126">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="613fb-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="613fb-127">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="613fb-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="613fb-128">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="613fb-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="613fb-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="613fb-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="613fb-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="613fb-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
