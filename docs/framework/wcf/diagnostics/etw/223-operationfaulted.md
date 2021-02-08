---
description: 'Дополнительные сведения: 223-Оператионфаултед'
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: e4155516e07568d4ee4ca76d63754ec4171e1064
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794290"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="c21e8-103">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="c21e8-103">223 - OperationFaulted</span></span>

## <a name="properties"></a><span data-ttu-id="c21e8-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c21e8-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c21e8-105">ID</span><span class="sxs-lookup"><span data-stu-id="c21e8-105">ID</span></span>|<span data-ttu-id="c21e8-106">223</span><span class="sxs-lookup"><span data-stu-id="c21e8-106">223</span></span>|  
|<span data-ttu-id="c21e8-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c21e8-107">Keywords</span></span>|<span data-ttu-id="c21e8-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c21e8-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c21e8-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c21e8-109">Level</span></span>|<span data-ttu-id="c21e8-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="c21e8-110">Warning</span></span>|  
|<span data-ttu-id="c21e8-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c21e8-111">Channel</span></span>|<span data-ttu-id="c21e8-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c21e8-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c21e8-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c21e8-113">Description</span></span>  

 <span data-ttu-id="c21e8-114">Это событие вызывается в том случае, если при вызове `OperationInvoker` модели службы по умолчанию обнаружено исключение, производное от `FaultException`.</span><span class="sxs-lookup"><span data-stu-id="c21e8-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c21e8-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c21e8-115">Message</span></span>  

 <span data-ttu-id="c21e8-116">Метод «%1» вызывал исключение FaultException после того, как был вызван OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="c21e8-116">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="c21e8-117">Длительность вызова метода составила «%2» мс.</span><span class="sxs-lookup"><span data-stu-id="c21e8-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c21e8-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="c21e8-118">Details</span></span>  
  
|<span data-ttu-id="c21e8-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c21e8-119">Data Item Name</span></span>|<span data-ttu-id="c21e8-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c21e8-120">Data Item Type</span></span>|<span data-ttu-id="c21e8-121">Описание</span><span class="sxs-lookup"><span data-stu-id="c21e8-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c21e8-122">MethodName</span><span class="sxs-lookup"><span data-stu-id="c21e8-122">MethodName</span></span>|`xs:string`|<span data-ttu-id="c21e8-123">Имя CLR метода, который был вызван `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="c21e8-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c21e8-124">Длительность</span><span class="sxs-lookup"><span data-stu-id="c21e8-124">Duration</span></span>|`xs:long`|<span data-ttu-id="c21e8-125">Время в миллисекундах, которое потребовалось `OperationInvoker`, чтобы вызвать метод.</span><span class="sxs-lookup"><span data-stu-id="c21e8-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="c21e8-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c21e8-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c21e8-127">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c21e8-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c21e8-128">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c21e8-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c21e8-129">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c21e8-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c21e8-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c21e8-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c21e8-131">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c21e8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
