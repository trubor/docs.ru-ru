---
description: 'Дополнительные сведения: 222-Оператионфаилед'
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: ea07dbabb651413f213db6789f2af8059d2595c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794303"
---
# <a name="222---operationfailed"></a><span data-ttu-id="96b8a-103">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="96b8a-103">222 - OperationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="96b8a-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="96b8a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96b8a-105">ID</span><span class="sxs-lookup"><span data-stu-id="96b8a-105">ID</span></span>|<span data-ttu-id="96b8a-106">222</span><span class="sxs-lookup"><span data-stu-id="96b8a-106">222</span></span>|  
|<span data-ttu-id="96b8a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="96b8a-107">Keywords</span></span>|<span data-ttu-id="96b8a-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="96b8a-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="96b8a-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="96b8a-109">Level</span></span>|<span data-ttu-id="96b8a-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="96b8a-110">Warning</span></span>|  
|<span data-ttu-id="96b8a-111">Канал</span><span class="sxs-lookup"><span data-stu-id="96b8a-111">Channel</span></span>|<span data-ttu-id="96b8a-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="96b8a-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96b8a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="96b8a-113">Description</span></span>  

 <span data-ttu-id="96b8a-114">Это событие создается в том случае, когда `OperationInvoker` модели службы по умолчанию обнаруживает исключение при вызове его метода.</span><span class="sxs-lookup"><span data-stu-id="96b8a-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="96b8a-115">Обратите внимание, что исключения, производные от `FaultException`, не вызывают это событие.</span><span class="sxs-lookup"><span data-stu-id="96b8a-115">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96b8a-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="96b8a-116">Message</span></span>  

 <span data-ttu-id="96b8a-117">Метод «%1» вызвал необработанное исключение после того, как был вызван OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="96b8a-117">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="96b8a-118">Длительность вызова метода составила «%2» мс.</span><span class="sxs-lookup"><span data-stu-id="96b8a-118">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="96b8a-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="96b8a-119">Details</span></span>  
  
|<span data-ttu-id="96b8a-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="96b8a-120">Data Item Name</span></span>|<span data-ttu-id="96b8a-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="96b8a-121">Data Item Type</span></span>|<span data-ttu-id="96b8a-122">Описание</span><span class="sxs-lookup"><span data-stu-id="96b8a-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96b8a-123">Имя метода</span><span class="sxs-lookup"><span data-stu-id="96b8a-123">Method Name</span></span>|`xs:string`|<span data-ttu-id="96b8a-124">Имя CLR метода, который был вызван `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="96b8a-124">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="96b8a-125">Длительность</span><span class="sxs-lookup"><span data-stu-id="96b8a-125">Duration</span></span>|`xs:long`|<span data-ttu-id="96b8a-126">Время в миллисекундах, которое потребовалось `OperationInvoker`, чтобы вызвать метод.</span><span class="sxs-lookup"><span data-stu-id="96b8a-126">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="96b8a-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="96b8a-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="96b8a-128">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="96b8a-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="96b8a-129">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="96b8a-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="96b8a-130">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="96b8a-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="96b8a-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="96b8a-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="96b8a-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96b8a-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
