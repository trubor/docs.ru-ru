---
description: 'Дополнительные сведения: 209-Мессажеинспекторбефоресендинвокед'
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 337ed7d4c62d41d72cb2b4710c9f98f863305aee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728006"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="b1a04-103">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="b1a04-103">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="b1a04-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="b1a04-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1a04-105">ID</span><span class="sxs-lookup"><span data-stu-id="b1a04-105">ID</span></span>|<span data-ttu-id="b1a04-106">209</span><span class="sxs-lookup"><span data-stu-id="b1a04-106">209</span></span>|  
|<span data-ttu-id="b1a04-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b1a04-107">Keywords</span></span>|<span data-ttu-id="b1a04-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1a04-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b1a04-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="b1a04-109">Level</span></span>|<span data-ttu-id="b1a04-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="b1a04-110">Information</span></span>|  
|<span data-ttu-id="b1a04-111">Канал</span><span class="sxs-lookup"><span data-stu-id="b1a04-111">Channel</span></span>|<span data-ttu-id="b1a04-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b1a04-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1a04-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b1a04-113">Description</span></span>  

 <span data-ttu-id="b1a04-114">Это событие создается после того, как модель службы вызвала метод `BeforeSend` для инспектора сообщений.</span><span class="sxs-lookup"><span data-stu-id="b1a04-114">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1a04-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b1a04-115">Message</span></span>  

 <span data-ttu-id="b1a04-116">Диспетчер вызвал BeforeSendRequest для MessageInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="b1a04-116">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1a04-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="b1a04-117">Details</span></span>  
  
|<span data-ttu-id="b1a04-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="b1a04-118">Data Item Name</span></span>|<span data-ttu-id="b1a04-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="b1a04-119">Data Item Type</span></span>|<span data-ttu-id="b1a04-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b1a04-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1a04-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="b1a04-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="b1a04-122">Имя CLR FullName типа вызванного инспектора `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="b1a04-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="b1a04-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="b1a04-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="b1a04-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="b1a04-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b1a04-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b1a04-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b1a04-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b1a04-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b1a04-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="b1a04-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b1a04-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b1a04-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
