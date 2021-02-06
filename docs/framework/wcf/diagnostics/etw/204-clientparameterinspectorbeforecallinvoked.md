---
description: 'Дополнительные сведения: 204-Клиентпараметеринспекторбефорекаллинвокед'
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: fa5646da7c48f624dc40f4fcc54a890c0758b4ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645000"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="4e9e1-103">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="4e9e1-103">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="4e9e1-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="4e9e1-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e9e1-105">ID</span><span class="sxs-lookup"><span data-stu-id="4e9e1-105">ID</span></span>|<span data-ttu-id="4e9e1-106">204</span><span class="sxs-lookup"><span data-stu-id="4e9e1-106">204</span></span>|  
|<span data-ttu-id="4e9e1-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="4e9e1-107">Keywords</span></span>|<span data-ttu-id="4e9e1-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4e9e1-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4e9e1-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="4e9e1-109">Level</span></span>|<span data-ttu-id="4e9e1-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="4e9e1-110">Information</span></span>|  
|<span data-ttu-id="4e9e1-111">Канал</span><span class="sxs-lookup"><span data-stu-id="4e9e1-111">Channel</span></span>|<span data-ttu-id="4e9e1-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4e9e1-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e9e1-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4e9e1-113">Description</span></span>  

 <span data-ttu-id="4e9e1-114">Это событие создается после того, как модель службы вызывает метод `BeforeCall` для инспектора параметров клиента.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e9e1-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="4e9e1-115">Message</span></span>  

 <span data-ttu-id="4e9e1-116">Диспетчер вызвал BeforeCall для ClientParameterInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="4e9e1-116">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e9e1-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="4e9e1-117">Details</span></span>  
  
|<span data-ttu-id="4e9e1-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="4e9e1-118">Data Item Name</span></span>|<span data-ttu-id="4e9e1-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="4e9e1-119">Data Item Type</span></span>|<span data-ttu-id="4e9e1-120">Описание</span><span class="sxs-lookup"><span data-stu-id="4e9e1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e9e1-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="4e9e1-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="4e9e1-122">Имя CLR FullName типа вызванного инспектора.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="4e9e1-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="4e9e1-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="4e9e1-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4e9e1-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="4e9e1-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4e9e1-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="4e9e1-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4e9e1-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="4e9e1-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4e9e1-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4e9e1-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
