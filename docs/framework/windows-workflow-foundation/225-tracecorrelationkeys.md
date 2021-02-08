---
description: 'Дополнительные сведения: 225-Трацекоррелатионкэйс'
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: c5fdb9305815cdc4df6bbae3e54209d2b5cffd9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778117"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="eb675-103">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="eb675-103">225 - TraceCorrelationKeys</span></span>

## <a name="properties"></a><span data-ttu-id="eb675-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="eb675-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb675-105">ID</span><span class="sxs-lookup"><span data-stu-id="eb675-105">ID</span></span>|<span data-ttu-id="eb675-106">225</span><span class="sxs-lookup"><span data-stu-id="eb675-106">225</span></span>|  
|<span data-ttu-id="eb675-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="eb675-107">Keywords</span></span>|<span data-ttu-id="eb675-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eb675-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="eb675-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="eb675-109">Level</span></span>|<span data-ttu-id="eb675-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="eb675-110">Information</span></span>|  
|<span data-ttu-id="eb675-111">Канал</span><span class="sxs-lookup"><span data-stu-id="eb675-111">Channel</span></span>|<span data-ttu-id="eb675-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="eb675-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eb675-113">Описание</span><span class="sxs-lookup"><span data-stu-id="eb675-113">Description</span></span>  

 <span data-ttu-id="eb675-114">Это событие создается, если в качестве службы рабочего процесса используется корреляция на основе содержимого.</span><span class="sxs-lookup"><span data-stu-id="eb675-114">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="eb675-115">Оно содержит ключи, применяемые для корреляции сообщения с экземпляром.</span><span class="sxs-lookup"><span data-stu-id="eb675-115">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eb675-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="eb675-116">Message</span></span>  

 <span data-ttu-id="eb675-117">Вычисленный ключ корреляции «%1» с использованием значений «%2» в родительской области «%3».</span><span class="sxs-lookup"><span data-stu-id="eb675-117">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eb675-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="eb675-118">Details</span></span>  
  
|<span data-ttu-id="eb675-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="eb675-119">Data Item Name</span></span>|<span data-ttu-id="eb675-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="eb675-120">Data Item Type</span></span>|<span data-ttu-id="eb675-121">Описание</span><span class="sxs-lookup"><span data-stu-id="eb675-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eb675-122">Instance Key</span><span class="sxs-lookup"><span data-stu-id="eb675-122">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="eb675-123">Ключ, созданный из значений корреляции.</span><span class="sxs-lookup"><span data-stu-id="eb675-123">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="eb675-124">Значения</span><span class="sxs-lookup"><span data-stu-id="eb675-124">Values</span></span>|`xs:string`|<span data-ttu-id="eb675-125">Значения, использованные для вычисления ключа экземпляра корреляции.</span><span class="sxs-lookup"><span data-stu-id="eb675-125">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="eb675-126">Parent Scope</span><span class="sxs-lookup"><span data-stu-id="eb675-126">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="eb675-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="eb675-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="eb675-128">Для служб, размещенных на веб-узле, это поле служит уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="eb675-128">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="eb675-129">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="eb675-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="eb675-130">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="eb675-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="eb675-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="eb675-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="eb675-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="eb675-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
