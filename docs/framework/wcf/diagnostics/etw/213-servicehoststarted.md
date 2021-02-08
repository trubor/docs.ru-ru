---
description: 'Дополнительные сведения: 213-Сервицехостстартед'
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 5e2b5b7c633ef053c449ad62c4f8fee40798a386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794420"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="c1f64-103">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="c1f64-103">213 - ServiceHostStarted</span></span>

## <a name="properties"></a><span data-ttu-id="c1f64-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c1f64-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1f64-105">ID</span><span class="sxs-lookup"><span data-stu-id="c1f64-105">ID</span></span>|<span data-ttu-id="c1f64-106">213</span><span class="sxs-lookup"><span data-stu-id="c1f64-106">213</span></span>|  
|<span data-ttu-id="c1f64-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c1f64-107">Keywords</span></span>|<span data-ttu-id="c1f64-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="c1f64-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="c1f64-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c1f64-109">Level</span></span>|<span data-ttu-id="c1f64-110">LogAlways</span><span class="sxs-lookup"><span data-stu-id="c1f64-110">LogAlways</span></span>|  
|<span data-ttu-id="c1f64-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c1f64-111">Channel</span></span>|<span data-ttu-id="c1f64-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c1f64-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c1f64-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c1f64-113">Description</span></span>  

 <span data-ttu-id="c1f64-114">Это событие создается при запуске службы, размещенной на веб-сервере.</span><span class="sxs-lookup"><span data-stu-id="c1f64-114">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="c1f64-115">Обычно это происходит, когда служба активируется сообщением.</span><span class="sxs-lookup"><span data-stu-id="c1f64-115">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="c1f64-116">Это также может произойти, если служба настроена для автоматического запуска.</span><span class="sxs-lookup"><span data-stu-id="c1f64-116">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c1f64-117">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c1f64-117">Message</span></span>  

 <span data-ttu-id="c1f64-118">ServiceHost запущена: «%1».</span><span class="sxs-lookup"><span data-stu-id="c1f64-118">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c1f64-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="c1f64-119">Details</span></span>  
  
|<span data-ttu-id="c1f64-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c1f64-120">Data Item Name</span></span>|<span data-ttu-id="c1f64-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c1f64-121">Data Item Type</span></span>|<span data-ttu-id="c1f64-122">Описание</span><span class="sxs-lookup"><span data-stu-id="c1f64-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c1f64-123">Имя типа службы</span><span class="sxs-lookup"><span data-stu-id="c1f64-123">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="c1f64-124">Имя CLR FullName типа реализации службы.</span><span class="sxs-lookup"><span data-stu-id="c1f64-124">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="c1f64-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="c1f64-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="c1f64-126">Для служб, размещенных на веб-узле, это поле служит уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c1f64-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c1f64-127">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c1f64-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c1f64-128">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c1f64-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c1f64-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c1f64-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c1f64-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c1f64-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
