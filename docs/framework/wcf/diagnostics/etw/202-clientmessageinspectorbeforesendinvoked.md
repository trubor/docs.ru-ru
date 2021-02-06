---
description: 'Дополнительные сведения: 202-Клиентмессажеинспекторбефоресендинвокед'
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 0267304ba805c8f23109c820c8516a27958c3040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645052"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="c2395-103">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="c2395-103">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="c2395-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c2395-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2395-105">ID</span><span class="sxs-lookup"><span data-stu-id="c2395-105">ID</span></span>|<span data-ttu-id="c2395-106">202</span><span class="sxs-lookup"><span data-stu-id="c2395-106">202</span></span>|  
|<span data-ttu-id="c2395-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c2395-107">Keywords</span></span>|<span data-ttu-id="c2395-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c2395-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c2395-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c2395-109">Level</span></span>|<span data-ttu-id="c2395-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="c2395-110">Information</span></span>|  
|<span data-ttu-id="c2395-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c2395-111">Channel</span></span>|<span data-ttu-id="c2395-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c2395-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c2395-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c2395-113">Description</span></span>  

 <span data-ttu-id="c2395-114">Это событие создается после того, как модель службы вызывает метод `BeforeSendRequest` для инспектора сообщений клиента.</span><span class="sxs-lookup"><span data-stu-id="c2395-114">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c2395-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c2395-115">Message</span></span>  

 <span data-ttu-id="c2395-116">Диспетчер вызвал BeforeSendRequest для ClientMessageInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="c2395-116">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c2395-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="c2395-117">Details</span></span>  
  
|<span data-ttu-id="c2395-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c2395-118">Data Item Name</span></span>|<span data-ttu-id="c2395-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c2395-119">Data Item Type</span></span>|<span data-ttu-id="c2395-120">Описание</span><span class="sxs-lookup"><span data-stu-id="c2395-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c2395-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="c2395-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="c2395-122">Имя CLR FullName типа вызванного инспектора.</span><span class="sxs-lookup"><span data-stu-id="c2395-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="c2395-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="c2395-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="c2395-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c2395-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c2395-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c2395-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c2395-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c2395-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c2395-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c2395-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c2395-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c2395-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
