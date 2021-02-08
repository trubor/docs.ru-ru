---
description: 'Дополнительные сведения: 221-Мессажерецеиведфромтранспорт'
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 0cc15fa95ae321083afa2792810807971e909e6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803507"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="cd543-103">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="cd543-103">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="cd543-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="cd543-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd543-105">ID</span><span class="sxs-lookup"><span data-stu-id="cd543-105">ID</span></span>|<span data-ttu-id="cd543-106">221</span><span class="sxs-lookup"><span data-stu-id="cd543-106">221</span></span>|  
|<span data-ttu-id="cd543-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="cd543-107">Keywords</span></span>|<span data-ttu-id="cd543-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cd543-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="cd543-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="cd543-109">Level</span></span>|<span data-ttu-id="cd543-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="cd543-110">Information</span></span>|  
|<span data-ttu-id="cd543-111">Канал</span><span class="sxs-lookup"><span data-stu-id="cd543-111">Channel</span></span>|<span data-ttu-id="cd543-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="cd543-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd543-113">Описание</span><span class="sxs-lookup"><span data-stu-id="cd543-113">Description</span></span>  

 <span data-ttu-id="cd543-114">Это событие вызывается при получении моделью службы сообщения от транспортной подсистемы.</span><span class="sxs-lookup"><span data-stu-id="cd543-114">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd543-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="cd543-115">Message</span></span>  

 <span data-ttu-id="cd543-116">Диспетчер получил сообщение от транспорта.</span><span class="sxs-lookup"><span data-stu-id="cd543-116">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="cd543-117">Идентификатор корреляции == «%1».</span><span class="sxs-lookup"><span data-stu-id="cd543-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd543-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="cd543-118">Details</span></span>  
  
|<span data-ttu-id="cd543-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="cd543-119">Data Item Name</span></span>|<span data-ttu-id="cd543-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="cd543-120">Data Item Type</span></span>|<span data-ttu-id="cd543-121">Описание</span><span class="sxs-lookup"><span data-stu-id="cd543-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cd543-122">Идентификатор корреляции</span><span class="sxs-lookup"><span data-stu-id="cd543-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="cd543-123">Идентификатор действия, используемый для корреляции события `MessageSentToTransport` из службы или клиента с соответствующим транспортом `MessageReceivedFromTransport` на другом конце.</span><span class="sxs-lookup"><span data-stu-id="cd543-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="cd543-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="cd543-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="cd543-125">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="cd543-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="cd543-126">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="cd543-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="cd543-127">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="cd543-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="cd543-128">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="cd543-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cd543-129">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cd543-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
