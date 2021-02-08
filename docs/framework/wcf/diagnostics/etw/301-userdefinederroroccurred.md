---
description: 'Дополнительные сведения: 301-Усердефинедерророккурред'
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 15e12bb27e3626f80747498a1387aa90fc461d28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794251"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="8d17e-103">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="8d17e-103">301 - UserDefinedErrorOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="8d17e-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="8d17e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d17e-105">ID</span><span class="sxs-lookup"><span data-stu-id="8d17e-105">ID</span></span>|<span data-ttu-id="8d17e-106">301</span><span class="sxs-lookup"><span data-stu-id="8d17e-106">301</span></span>|  
|<span data-ttu-id="8d17e-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8d17e-107">Keywords</span></span>|<span data-ttu-id="8d17e-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="8d17e-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="8d17e-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="8d17e-109">Level</span></span>|<span data-ttu-id="8d17e-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="8d17e-110">Error</span></span>|  
|<span data-ttu-id="8d17e-111">Канал</span><span class="sxs-lookup"><span data-stu-id="8d17e-111">Channel</span></span>|<span data-ttu-id="8d17e-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8d17e-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8d17e-113">Описание</span><span class="sxs-lookup"><span data-stu-id="8d17e-113">Description</span></span>  

 <span data-ttu-id="8d17e-114">Это событие создается в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="8d17e-114">This event is emitted from user code.</span></span> <span data-ttu-id="8d17e-115">Разработчики могут создать это событие, если определенная пользователем ошибка возникает в принадлежащей им службе.</span><span class="sxs-lookup"><span data-stu-id="8d17e-115">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="8d17e-116">Это можно сделать при помощи API-интерфейсов <xref:System.Diagnostics.Eventing>.</span><span class="sxs-lookup"><span data-stu-id="8d17e-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="8d17e-117">Помимо этого, есть образец WCF, который включает этот API-интерфейс и показывает, как правильно создать это событие.</span><span class="sxs-lookup"><span data-stu-id="8d17e-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8d17e-118">Сообщение</span><span class="sxs-lookup"><span data-stu-id="8d17e-118">Message</span></span>  

 <span data-ttu-id="8d17e-119">Имя: «%1», ссылка: «%2», полезные данные: %3</span><span class="sxs-lookup"><span data-stu-id="8d17e-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="8d17e-120">Сведения</span><span class="sxs-lookup"><span data-stu-id="8d17e-120">Details</span></span>  
  
|<span data-ttu-id="8d17e-121">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="8d17e-121">Data Item Name</span></span>|<span data-ttu-id="8d17e-122">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="8d17e-122">Data Item Type</span></span>|<span data-ttu-id="8d17e-123">Описание</span><span class="sxs-lookup"><span data-stu-id="8d17e-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8d17e-124">Имя</span><span class="sxs-lookup"><span data-stu-id="8d17e-124">Name</span></span>|`xs:string`|<span data-ttu-id="8d17e-125">Определенное пользователем имя события.</span><span class="sxs-lookup"><span data-stu-id="8d17e-125">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="8d17e-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="8d17e-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="8d17e-127">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="8d17e-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8d17e-128">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8d17e-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8d17e-129">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="8d17e-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8d17e-130">Payload</span><span class="sxs-lookup"><span data-stu-id="8d17e-130">Payload</span></span>|`xs:string`|<span data-ttu-id="8d17e-131">Определенные пользователем полезные данные события.</span><span class="sxs-lookup"><span data-stu-id="8d17e-131">The user-defined payload of the event.</span></span>|
