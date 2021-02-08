---
description: 'Дополнительные сведения: 499-Трансферемиттед'
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: d9802ef718ce6091abe1d1092ad6bb7e7fff108a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783577"
---
# <a name="499---transferemitted"></a><span data-ttu-id="98879-103">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="98879-103">499 - TransferEmitted</span></span>

## <a name="properties"></a><span data-ttu-id="98879-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="98879-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="98879-105">ID</span><span class="sxs-lookup"><span data-stu-id="98879-105">ID</span></span>|<span data-ttu-id="98879-106">499</span><span class="sxs-lookup"><span data-stu-id="98879-106">499</span></span>|  
|<span data-ttu-id="98879-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="98879-107">Keywords</span></span>|<span data-ttu-id="98879-108">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="98879-108">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="98879-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="98879-109">Level</span></span>|<span data-ttu-id="98879-110">LogAlways</span><span class="sxs-lookup"><span data-stu-id="98879-110">LogAlways</span></span>|  
|<span data-ttu-id="98879-111">Канал</span><span class="sxs-lookup"><span data-stu-id="98879-111">Channel</span></span>|<span data-ttu-id="98879-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="98879-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="98879-113">Описание</span><span class="sxs-lookup"><span data-stu-id="98879-113">Description</span></span>  

 <span data-ttu-id="98879-114">Это событие формируется при возникновении события передачи.</span><span class="sxs-lookup"><span data-stu-id="98879-114">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="98879-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="98879-115">Message</span></span>  

 <span data-ttu-id="98879-116">Произошло событие передачи.</span><span class="sxs-lookup"><span data-stu-id="98879-116">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="98879-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="98879-117">Details</span></span>  
  
|<span data-ttu-id="98879-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="98879-118">Data Item Name</span></span>|<span data-ttu-id="98879-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="98879-119">Data Item Type</span></span>|<span data-ttu-id="98879-120">Описание</span><span class="sxs-lookup"><span data-stu-id="98879-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="98879-121">HostReference</span><span class="sxs-lookup"><span data-stu-id="98879-121">HostReference</span></span>|`xs:string`|<span data-ttu-id="98879-122">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="98879-122">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="98879-123">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="98879-123">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="98879-124">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="98879-124">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="98879-125">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="98879-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="98879-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="98879-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
