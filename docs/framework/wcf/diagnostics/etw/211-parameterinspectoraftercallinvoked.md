---
description: 'Дополнительные сведения: 211-Параметеринспекторафтеркаллинвокед'
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 6168528fb001b5669e80595c8327dc57651e815e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794433"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="c71bc-103">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="c71bc-103">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="c71bc-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c71bc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c71bc-105">ID</span><span class="sxs-lookup"><span data-stu-id="c71bc-105">ID</span></span>|<span data-ttu-id="c71bc-106">211</span><span class="sxs-lookup"><span data-stu-id="c71bc-106">211</span></span>|  
|<span data-ttu-id="c71bc-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c71bc-107">Keywords</span></span>|<span data-ttu-id="c71bc-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c71bc-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c71bc-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c71bc-109">Level</span></span>|<span data-ttu-id="c71bc-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="c71bc-110">Information</span></span>|  
|<span data-ttu-id="c71bc-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c71bc-111">Channel</span></span>|<span data-ttu-id="c71bc-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c71bc-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c71bc-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c71bc-113">Description</span></span>  

 <span data-ttu-id="c71bc-114">Это событие создается после того, как модель службы вызывает метод `AfterCall` для `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="c71bc-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c71bc-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c71bc-115">Message</span></span>  

 <span data-ttu-id="c71bc-116">Диспетчер вызвал AfterCall относительно ParameterInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="c71bc-116">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c71bc-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="c71bc-117">Details</span></span>  
  
|<span data-ttu-id="c71bc-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c71bc-118">Data Item Name</span></span>|<span data-ttu-id="c71bc-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c71bc-119">Data Item Type</span></span>|<span data-ttu-id="c71bc-120">Описание</span><span class="sxs-lookup"><span data-stu-id="c71bc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c71bc-121">Имя типа</span><span class="sxs-lookup"><span data-stu-id="c71bc-121">Type Name</span></span>|`xs:string`|<span data-ttu-id="c71bc-122">Имя CLR FullName типа вызванного инспектора `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="c71bc-122">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="c71bc-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="c71bc-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="c71bc-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c71bc-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c71bc-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c71bc-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c71bc-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c71bc-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c71bc-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c71bc-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c71bc-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c71bc-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
