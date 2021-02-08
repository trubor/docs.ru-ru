---
description: 'Дополнительные сведения: 217-Клиентоператионпрепаред'
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: eab6a9a654e6e48a8831f238cdf3a3bf7a9f62d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794355"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="5d0df-103">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="5d0df-103">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="5d0df-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="5d0df-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d0df-105">ID</span><span class="sxs-lookup"><span data-stu-id="5d0df-105">ID</span></span>|<span data-ttu-id="5d0df-106">217</span><span class="sxs-lookup"><span data-stu-id="5d0df-106">217</span></span>|  
|<span data-ttu-id="5d0df-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="5d0df-107">Keywords</span></span>|<span data-ttu-id="5d0df-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d0df-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5d0df-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="5d0df-109">Level</span></span>|<span data-ttu-id="5d0df-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="5d0df-110">Information</span></span>|  
|<span data-ttu-id="5d0df-111">Канал</span><span class="sxs-lookup"><span data-stu-id="5d0df-111">Channel</span></span>|<span data-ttu-id="5d0df-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5d0df-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5d0df-113">Описание</span><span class="sxs-lookup"><span data-stu-id="5d0df-113">Description</span></span>  

 <span data-ttu-id="5d0df-114">Это событие создается клиентом непосредственно перед отправкой операции службе.</span><span class="sxs-lookup"><span data-stu-id="5d0df-114">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5d0df-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="5d0df-115">Message</span></span>  

 <span data-ttu-id="5d0df-116">Клиент выполняет действие «%1», связанное с контрактом «%2».</span><span class="sxs-lookup"><span data-stu-id="5d0df-116">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="5d0df-117">Сообщение будет отправлено «%3».</span><span class="sxs-lookup"><span data-stu-id="5d0df-117">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d0df-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="5d0df-118">Details</span></span>  
  
|<span data-ttu-id="5d0df-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="5d0df-119">Data Item Name</span></span>|<span data-ttu-id="5d0df-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="5d0df-120">Data Item Type</span></span>|<span data-ttu-id="5d0df-121">Описание</span><span class="sxs-lookup"><span data-stu-id="5d0df-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5d0df-122">Действие</span><span class="sxs-lookup"><span data-stu-id="5d0df-122">Action</span></span>|`xs:string`|<span data-ttu-id="5d0df-123">Заголовок действия SOAP исходящего сообщения.</span><span class="sxs-lookup"><span data-stu-id="5d0df-123">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="5d0df-124">Contract Name</span><span class="sxs-lookup"><span data-stu-id="5d0df-124">Contract Name</span></span>|`xs:string`|<span data-ttu-id="5d0df-125">Имя контракта.</span><span class="sxs-lookup"><span data-stu-id="5d0df-125">The name of the contract.</span></span> <span data-ttu-id="5d0df-126">Пример: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="5d0df-126">Example: ICalculator.</span></span>|  
|<span data-ttu-id="5d0df-127">Назначение</span><span class="sxs-lookup"><span data-stu-id="5d0df-127">Destination</span></span>|`xs:string`|<span data-ttu-id="5d0df-128">Адрес конечной точки службы, которой отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="5d0df-128">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="5d0df-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="5d0df-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="5d0df-130">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="5d0df-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5d0df-131">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="5d0df-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5d0df-132">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="5d0df-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5d0df-133">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="5d0df-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5d0df-134">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5d0df-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
