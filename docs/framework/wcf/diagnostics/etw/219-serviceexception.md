---
description: 'Дополнительные сведения: 219-ServiceException'
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794329"
---
# <a name="219---serviceexception"></a><span data-ttu-id="9b047-103">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="9b047-103">219 - ServiceException</span></span>

## <a name="properties"></a><span data-ttu-id="9b047-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="9b047-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b047-105">ID</span><span class="sxs-lookup"><span data-stu-id="9b047-105">ID</span></span>|<span data-ttu-id="9b047-106">219</span><span class="sxs-lookup"><span data-stu-id="9b047-106">219</span></span>|  
|<span data-ttu-id="9b047-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9b047-107">Keywords</span></span>|<span data-ttu-id="9b047-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9b047-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9b047-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="9b047-109">Level</span></span>|<span data-ttu-id="9b047-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="9b047-110">Error</span></span>|  
|<span data-ttu-id="9b047-111">Канал</span><span class="sxs-lookup"><span data-stu-id="9b047-111">Channel</span></span>|<span data-ttu-id="9b047-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9b047-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9b047-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9b047-113">Description</span></span>  

 <span data-ttu-id="9b047-114">Это событие создается при обнаружении службой WCF необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="9b047-114">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="9b047-115">В число необработанных входят исключения, возникшие во время активации, обработки сообщений и выполнения пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="9b047-115">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9b047-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9b047-116">Message</span></span>  

 <span data-ttu-id="9b047-117">Во время обработки сообщения возникло необработанное исключение типа «%2».</span><span class="sxs-lookup"><span data-stu-id="9b047-117">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="9b047-118">Полное исключение ToString: %1.</span><span class="sxs-lookup"><span data-stu-id="9b047-118">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9b047-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="9b047-119">Details</span></span>  
  
|<span data-ttu-id="9b047-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="9b047-120">Data Item Name</span></span>|<span data-ttu-id="9b047-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="9b047-121">Data Item Type</span></span>|<span data-ttu-id="9b047-122">Описание</span><span class="sxs-lookup"><span data-stu-id="9b047-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9b047-123">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="9b047-123">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="9b047-124">Результат вызова метода `ToString`() относительно исключения CLR.</span><span class="sxs-lookup"><span data-stu-id="9b047-124">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="9b047-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="9b047-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="9b047-126">Имя CLR FullName типа исключения.</span><span class="sxs-lookup"><span data-stu-id="9b047-126">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="9b047-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="9b047-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="9b047-128">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="9b047-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9b047-129">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="9b047-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9b047-130">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="9b047-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9b047-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="9b047-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9b047-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9b047-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
