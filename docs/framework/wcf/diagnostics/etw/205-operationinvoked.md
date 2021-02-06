---
description: 'Дополнительные сведения: 205-Оператионинвокед'
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: 09afe4c29c5f56b06bbf524dd13d88ddf2319063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644974"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="c889b-103">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="c889b-103">205 - OperationInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="c889b-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c889b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c889b-105">ID</span><span class="sxs-lookup"><span data-stu-id="c889b-105">ID</span></span>|<span data-ttu-id="c889b-106">205</span><span class="sxs-lookup"><span data-stu-id="c889b-106">205</span></span>|  
|<span data-ttu-id="c889b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c889b-107">Keywords</span></span>|<span data-ttu-id="c889b-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c889b-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c889b-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c889b-109">Level</span></span>|<span data-ttu-id="c889b-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="c889b-110">Information</span></span>|  
|<span data-ttu-id="c889b-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c889b-111">Channel</span></span>|<span data-ttu-id="c889b-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c889b-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c889b-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c889b-113">Description</span></span>  

 <span data-ttu-id="c889b-114">Это событие создается непосредственно перед тем, как `OperationInvoker` по умолчанию модели службы начнет вызов метода.</span><span class="sxs-lookup"><span data-stu-id="c889b-114">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c889b-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c889b-115">Message</span></span>  

 <span data-ttu-id="c889b-116">OperationInvoker вызвал метод «%1».</span><span class="sxs-lookup"><span data-stu-id="c889b-116">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="c889b-117">Сведения о вызывающем объекте: «%2».</span><span class="sxs-lookup"><span data-stu-id="c889b-117">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c889b-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="c889b-118">Details</span></span>  
  
|<span data-ttu-id="c889b-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c889b-119">Data Item Name</span></span>|<span data-ttu-id="c889b-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c889b-120">Data Item Type</span></span>|<span data-ttu-id="c889b-121">Описание</span><span class="sxs-lookup"><span data-stu-id="c889b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c889b-122">Имя метода</span><span class="sxs-lookup"><span data-stu-id="c889b-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="c889b-123">Имя CLR метода, который был вызван `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="c889b-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c889b-124">Сведения о вызывающем</span><span class="sxs-lookup"><span data-stu-id="c889b-124">Caller Information</span></span>|`xs:string`|<span data-ttu-id="c889b-125">IP-адрес и номер порта клиента в формате «IPAddress:PortNumber».</span><span class="sxs-lookup"><span data-stu-id="c889b-125">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="c889b-126">Эти два значения извлекаются из свойства сообщения «System.ServiceModel.Channels.RemoteEndpointMessageProperty» в контексте операции.</span><span class="sxs-lookup"><span data-stu-id="c889b-126">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="c889b-127">Следует отметить, что для привязок, отличных от TCP, это значение `null`.</span><span class="sxs-lookup"><span data-stu-id="c889b-127">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="c889b-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="c889b-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="c889b-129">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c889b-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c889b-130">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c889b-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c889b-131">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c889b-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c889b-132">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c889b-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c889b-133">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c889b-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
