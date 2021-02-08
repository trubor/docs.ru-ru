---
description: 'Дополнительные сведения: 218-Клиентоператионкомплетед'
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 3719b77ce653c5177cf7b92901ecd51982504b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794342"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="b6483-103">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="b6483-103">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="b6483-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="b6483-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6483-105">ID</span><span class="sxs-lookup"><span data-stu-id="b6483-105">ID</span></span>|<span data-ttu-id="b6483-106">218</span><span class="sxs-lookup"><span data-stu-id="b6483-106">218</span></span>|  
|<span data-ttu-id="b6483-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b6483-107">Keywords</span></span>|<span data-ttu-id="b6483-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b6483-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b6483-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="b6483-109">Level</span></span>|<span data-ttu-id="b6483-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="b6483-110">Information</span></span>|  
|<span data-ttu-id="b6483-111">Канал</span><span class="sxs-lookup"><span data-stu-id="b6483-111">Channel</span></span>|<span data-ttu-id="b6483-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b6483-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b6483-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b6483-113">Description</span></span>  

 <span data-ttu-id="b6483-114">Это событие создается клиентом сразу после завершения операции.</span><span class="sxs-lookup"><span data-stu-id="b6483-114">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="b6483-115">Для односторонних операций оно создается сразу после успешной отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="b6483-115">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="b6483-116">Для операций типа «запрос-ответ» оно создается после получения ответа.</span><span class="sxs-lookup"><span data-stu-id="b6483-116">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b6483-117">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b6483-117">Message</span></span>  

 <span data-ttu-id="b6483-118">Клиент завершил выполнение действия «%1», связанного с контрактом «%2».</span><span class="sxs-lookup"><span data-stu-id="b6483-118">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="b6483-119">Сообщение было отправлено «%3».</span><span class="sxs-lookup"><span data-stu-id="b6483-119">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b6483-120">Сведения</span><span class="sxs-lookup"><span data-stu-id="b6483-120">Details</span></span>  
  
|<span data-ttu-id="b6483-121">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="b6483-121">Data Item Name</span></span>|<span data-ttu-id="b6483-122">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="b6483-122">Data Item Type</span></span>|<span data-ttu-id="b6483-123">Описание</span><span class="sxs-lookup"><span data-stu-id="b6483-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b6483-124">Действие</span><span class="sxs-lookup"><span data-stu-id="b6483-124">Action</span></span>|<span data-ttu-id="b6483-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6483-125">xs:string</span></span>|<span data-ttu-id="b6483-126">Заголовок действия SOAP исходящего сообщения.</span><span class="sxs-lookup"><span data-stu-id="b6483-126">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="b6483-127">Contract Name</span><span class="sxs-lookup"><span data-stu-id="b6483-127">Contract Name</span></span>|`xs:string`|<span data-ttu-id="b6483-128">Имя контракта.</span><span class="sxs-lookup"><span data-stu-id="b6483-128">The name of the contract.</span></span> <span data-ttu-id="b6483-129">Пример: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="b6483-129">Example: ICalculator.</span></span>|  
|<span data-ttu-id="b6483-130">Назначение</span><span class="sxs-lookup"><span data-stu-id="b6483-130">Destination</span></span>|`xs:string`|<span data-ttu-id="b6483-131">Адрес конечной точки службы, которой было отправлено сообщение.</span><span class="sxs-lookup"><span data-stu-id="b6483-131">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="b6483-132">HostReference</span><span class="sxs-lookup"><span data-stu-id="b6483-132">HostReference</span></span>|`xs:string`|<span data-ttu-id="b6483-133">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="b6483-133">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b6483-134">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b6483-134">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b6483-135">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b6483-135">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b6483-136">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="b6483-136">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b6483-137">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b6483-137">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
