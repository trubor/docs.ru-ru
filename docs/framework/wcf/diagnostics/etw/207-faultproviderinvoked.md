---
description: 'Дополнительные сведения: 207-Фаултпровидеринвокед'
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 03c4f1669fc61019ccf4d23d2994f136e231fbec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728071"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="f1e36-103">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="f1e36-103">207 - FaultProviderInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="f1e36-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="f1e36-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1e36-105">ID</span><span class="sxs-lookup"><span data-stu-id="f1e36-105">ID</span></span>|<span data-ttu-id="f1e36-106">207</span><span class="sxs-lookup"><span data-stu-id="f1e36-106">207</span></span>|  
|<span data-ttu-id="f1e36-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f1e36-107">Keywords</span></span>|<span data-ttu-id="f1e36-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f1e36-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f1e36-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="f1e36-109">Level</span></span>|<span data-ttu-id="f1e36-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="f1e36-110">Information</span></span>|  
|<span data-ttu-id="f1e36-111">Канал</span><span class="sxs-lookup"><span data-stu-id="f1e36-111">Channel</span></span>|<span data-ttu-id="f1e36-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f1e36-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f1e36-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f1e36-113">Description</span></span>  

 <span data-ttu-id="f1e36-114">Это событие создается после вызова `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="f1e36-114">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f1e36-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="f1e36-115">Message</span></span>  

 <span data-ttu-id="f1e36-116">Диспетчер вызвал FaultProvider типа «%1» с исключением типа «%2».</span><span class="sxs-lookup"><span data-stu-id="f1e36-116">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f1e36-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="f1e36-117">Details</span></span>  
  
|<span data-ttu-id="f1e36-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="f1e36-118">Data Item Name</span></span>|<span data-ttu-id="f1e36-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="f1e36-119">Data Item Type</span></span>|<span data-ttu-id="f1e36-120">Описание</span><span class="sxs-lookup"><span data-stu-id="f1e36-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f1e36-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="f1e36-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="f1e36-122">Имя CLR FullName типа вызванного инспектора `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="f1e36-122">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="f1e36-123">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="f1e36-123">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="f1e36-124">Имя CLR FullName исключения, обработанного `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="f1e36-124">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="f1e36-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f1e36-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f1e36-126">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="f1e36-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f1e36-127">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="f1e36-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f1e36-128">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="f1e36-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f1e36-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="f1e36-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f1e36-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f1e36-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
