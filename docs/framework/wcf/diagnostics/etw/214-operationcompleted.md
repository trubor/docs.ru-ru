---
description: 'Дополнительные сведения: 214-Оператионкомплетед'
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: aad1ac49667a2ebbf172b5132507584e05d0f03e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794394"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="ffdda-103">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="ffdda-103">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="ffdda-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="ffdda-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffdda-105">ID</span><span class="sxs-lookup"><span data-stu-id="ffdda-105">ID</span></span>|<span data-ttu-id="ffdda-106">214</span><span class="sxs-lookup"><span data-stu-id="ffdda-106">214</span></span>|  
|<span data-ttu-id="ffdda-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="ffdda-107">Keywords</span></span>|<span data-ttu-id="ffdda-108">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ffdda-108">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ffdda-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="ffdda-109">Level</span></span>|<span data-ttu-id="ffdda-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="ffdda-110">Information</span></span>|  
|<span data-ttu-id="ffdda-111">Канал</span><span class="sxs-lookup"><span data-stu-id="ffdda-111">Channel</span></span>|<span data-ttu-id="ffdda-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ffdda-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffdda-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ffdda-113">Description</span></span>  

 <span data-ttu-id="ffdda-114">Данное событие создается, когда `OperationInvoker` по умолчанию модели завершает вызов метода, который не сформировал исключение.</span><span class="sxs-lookup"><span data-stu-id="ffdda-114">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffdda-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="ffdda-115">Message</span></span>  

 <span data-ttu-id="ffdda-116">OperationInvoker завершил вызов метода «%1».</span><span class="sxs-lookup"><span data-stu-id="ffdda-116">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="ffdda-117">Длительность вызова метода составила «%2» мс.</span><span class="sxs-lookup"><span data-stu-id="ffdda-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffdda-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="ffdda-118">Details</span></span>  
  
|<span data-ttu-id="ffdda-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="ffdda-119">Data Item Name</span></span>|<span data-ttu-id="ffdda-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="ffdda-120">Data Item Type</span></span>|<span data-ttu-id="ffdda-121">Описание</span><span class="sxs-lookup"><span data-stu-id="ffdda-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffdda-122">Имя метода</span><span class="sxs-lookup"><span data-stu-id="ffdda-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="ffdda-123">Имя CLR метода, который был вызван `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="ffdda-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="ffdda-124">Длительность</span><span class="sxs-lookup"><span data-stu-id="ffdda-124">Duration</span></span>|`xs:long`|<span data-ttu-id="ffdda-125">Время в миллисекундах, которое потребовалось `OperationInvoker`, чтобы вызвать метод.</span><span class="sxs-lookup"><span data-stu-id="ffdda-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="ffdda-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="ffdda-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="ffdda-127">Для служб, размещенных на сервере, это поле служит уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="ffdda-127">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ffdda-128">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="ffdda-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ffdda-129">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="ffdda-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ffdda-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="ffdda-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ffdda-131">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ffdda-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
