---
description: 'Дополнительные сведения: 206-Еррорхандлеринвокед'
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: addbcbdea25c7f8e7515b743e98e426476fa0b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783785"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="da82c-103">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="da82c-103">206 - ErrorHandlerInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="da82c-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="da82c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da82c-105">ID</span><span class="sxs-lookup"><span data-stu-id="da82c-105">ID</span></span>|<span data-ttu-id="da82c-106">206</span><span class="sxs-lookup"><span data-stu-id="da82c-106">206</span></span>|  
|<span data-ttu-id="da82c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="da82c-107">Keywords</span></span>|<span data-ttu-id="da82c-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="da82c-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="da82c-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="da82c-109">Level</span></span>|<span data-ttu-id="da82c-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="da82c-110">Information</span></span>|  
|<span data-ttu-id="da82c-111">Канал</span><span class="sxs-lookup"><span data-stu-id="da82c-111">Channel</span></span>|<span data-ttu-id="da82c-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="da82c-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="da82c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="da82c-113">Description</span></span>  

 <span data-ttu-id="da82c-114">Это событие создается после того, как обработчик `ErrorHandler` начинает обрабатывать исключение, возникшее в операции службы.</span><span class="sxs-lookup"><span data-stu-id="da82c-114">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="da82c-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="da82c-115">Message</span></span>  

 <span data-ttu-id="da82c-116">Диспетчер вызвал ErrorHandler типа "%1" с исключением типа "%3".</span><span class="sxs-lookup"><span data-stu-id="da82c-116">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="da82c-117">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="da82c-117">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="da82c-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="da82c-118">Details</span></span>  
  
|<span data-ttu-id="da82c-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="da82c-119">Data Item Name</span></span>|<span data-ttu-id="da82c-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="da82c-120">Data Item Type</span></span>|<span data-ttu-id="da82c-121">Описание</span><span class="sxs-lookup"><span data-stu-id="da82c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="da82c-122">TypeName</span><span class="sxs-lookup"><span data-stu-id="da82c-122">TypeName</span></span>|`xs:string`|<span data-ttu-id="da82c-123">Имя CLR FullName типа вызванного инспектора `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="da82c-123">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="da82c-124">Обработанные</span><span class="sxs-lookup"><span data-stu-id="da82c-124">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="da82c-125">Значение `true`, если обработчик ошибок обработал ошибку, в противном случае значение `false`.</span><span class="sxs-lookup"><span data-stu-id="da82c-125">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="da82c-126">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="da82c-126">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="da82c-127">Имя CLR FullName обрабатываемого исключения.</span><span class="sxs-lookup"><span data-stu-id="da82c-127">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="da82c-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="da82c-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="da82c-129">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="da82c-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="da82c-130">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="da82c-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="da82c-131">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="da82c-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="da82c-132">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="da82c-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="da82c-133">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="da82c-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
