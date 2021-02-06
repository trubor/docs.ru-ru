---
description: 'Дополнительные сведения: 203-Клиентпараметеринспекторафтеркаллинвокед'
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: bacdc2a74fc2cef6d7e473fa58c0cbbcffffcf16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645026"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="b1b78-103">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b1b78-103">203 - ClientParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="b1b78-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="b1b78-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1b78-105">ID</span><span class="sxs-lookup"><span data-stu-id="b1b78-105">ID</span></span>|<span data-ttu-id="b1b78-106">203</span><span class="sxs-lookup"><span data-stu-id="b1b78-106">203</span></span>|  
|<span data-ttu-id="b1b78-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b1b78-107">Keywords</span></span>|<span data-ttu-id="b1b78-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1b78-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b1b78-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="b1b78-109">Level</span></span>|<span data-ttu-id="b1b78-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="b1b78-110">Information</span></span>|  
|<span data-ttu-id="b1b78-111">Канал</span><span class="sxs-lookup"><span data-stu-id="b1b78-111">Channel</span></span>|<span data-ttu-id="b1b78-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b1b78-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1b78-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b1b78-113">Description</span></span>  

 <span data-ttu-id="b1b78-114">Это событие создается после того, как модель службы вызывает метод `AfterCall` для инспектора параметров клиента.</span><span class="sxs-lookup"><span data-stu-id="b1b78-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1b78-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b1b78-115">Message</span></span>  

 <span data-ttu-id="b1b78-116">Диспетчер вызвал «AfterCall» для ClientParameterInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="b1b78-116">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1b78-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="b1b78-117">Details</span></span>  
  
|<span data-ttu-id="b1b78-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="b1b78-118">Data Item Name</span></span>|<span data-ttu-id="b1b78-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="b1b78-119">Data Item Type</span></span>|<span data-ttu-id="b1b78-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b1b78-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1b78-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="b1b78-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="b1b78-122">Имя CLR FullName типа вызванного инспектора.</span><span class="sxs-lookup"><span data-stu-id="b1b78-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b1b78-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="b1b78-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="b1b78-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="b1b78-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b1b78-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b1b78-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b1b78-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b1b78-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b1b78-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="b1b78-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b1b78-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b1b78-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
