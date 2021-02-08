---
description: 'Дополнительные сведения: 302-Усердефинедварнингоккурред'
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: eb79e32d8993ec60c05e5aaaee1b5e15ee7e32e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794225"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="4a100-103">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="4a100-103">302 - UserDefinedWarningOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="4a100-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="4a100-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a100-105">ID</span><span class="sxs-lookup"><span data-stu-id="4a100-105">ID</span></span>|<span data-ttu-id="4a100-106">302</span><span class="sxs-lookup"><span data-stu-id="4a100-106">302</span></span>|  
|<span data-ttu-id="4a100-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="4a100-107">Keywords</span></span>|<span data-ttu-id="4a100-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="4a100-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="4a100-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="4a100-109">Level</span></span>|<span data-ttu-id="4a100-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="4a100-110">Warning</span></span>|  
|<span data-ttu-id="4a100-111">Канал</span><span class="sxs-lookup"><span data-stu-id="4a100-111">Channel</span></span>|<span data-ttu-id="4a100-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4a100-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4a100-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4a100-113">Description</span></span>  

 <span data-ttu-id="4a100-114">Это событие создается в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="4a100-114">This event is emitted from user code.</span></span> <span data-ttu-id="4a100-115">Разработчики могут создать это событие, если определенное пользователем событие предупреждения возникло в принадлежащей им службе.</span><span class="sxs-lookup"><span data-stu-id="4a100-115">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="4a100-116">Это можно сделать при помощи API-интерфейсов <xref:System.Diagnostics.Eventing>.</span><span class="sxs-lookup"><span data-stu-id="4a100-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="4a100-117">Помимо этого, есть образец WCF, который включает этот API-интерфейс и показывает, как правильно создать это событие.</span><span class="sxs-lookup"><span data-stu-id="4a100-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4a100-118">Сообщение</span><span class="sxs-lookup"><span data-stu-id="4a100-118">Message</span></span>  

 <span data-ttu-id="4a100-119">Имя: «%1», ссылка: «%2», полезные данные: %3</span><span class="sxs-lookup"><span data-stu-id="4a100-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="4a100-120">Сведения</span><span class="sxs-lookup"><span data-stu-id="4a100-120">Details</span></span>  
  
|<span data-ttu-id="4a100-121">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="4a100-121">Data Item Name</span></span>|<span data-ttu-id="4a100-122">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="4a100-122">Data Item Type</span></span>|<span data-ttu-id="4a100-123">Описание</span><span class="sxs-lookup"><span data-stu-id="4a100-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4a100-124">Имя</span><span class="sxs-lookup"><span data-stu-id="4a100-124">Name</span></span>|`xs:string`|<span data-ttu-id="4a100-125">Определенное пользователем имя события.</span><span class="sxs-lookup"><span data-stu-id="4a100-125">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="4a100-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="4a100-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="4a100-127">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="4a100-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4a100-128">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="4a100-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4a100-129">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="4a100-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4a100-130">Payload</span><span class="sxs-lookup"><span data-stu-id="4a100-130">Payload</span></span>|`xs:string`|<span data-ttu-id="4a100-131">Определенные пользователем полезные данные события.</span><span class="sxs-lookup"><span data-stu-id="4a100-131">The user-defined payload of the event.</span></span>|
