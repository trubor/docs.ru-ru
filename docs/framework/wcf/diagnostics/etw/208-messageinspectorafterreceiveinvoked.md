---
description: 'Дополнительные сведения: 208-Мессажеинспекторафтеррецеивеинвокед'
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 29935f5dc8c5dd53c0bf427bfdc9b3858d7fb8fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728058"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="737de-103">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="737de-103">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="737de-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="737de-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="737de-105">ID</span><span class="sxs-lookup"><span data-stu-id="737de-105">ID</span></span>|<span data-ttu-id="737de-106">208</span><span class="sxs-lookup"><span data-stu-id="737de-106">208</span></span>|  
|<span data-ttu-id="737de-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="737de-107">Keywords</span></span>|<span data-ttu-id="737de-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="737de-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="737de-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="737de-109">Level</span></span>|<span data-ttu-id="737de-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="737de-110">Information</span></span>|  
|<span data-ttu-id="737de-111">Канал</span><span class="sxs-lookup"><span data-stu-id="737de-111">Channel</span></span>|<span data-ttu-id="737de-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="737de-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="737de-113">Описание</span><span class="sxs-lookup"><span data-stu-id="737de-113">Description</span></span>  

 <span data-ttu-id="737de-114">Это событие создается после того, как модель службы вызвала метод `AfterReceive` для инспектора сообщений.</span><span class="sxs-lookup"><span data-stu-id="737de-114">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="737de-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="737de-115">Message</span></span>  

 <span data-ttu-id="737de-116">Диспетчер вызвал AfterReceiveReply относительно MessageInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="737de-116">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="737de-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="737de-117">Details</span></span>  
  
|<span data-ttu-id="737de-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="737de-118">Data Item Name</span></span>|<span data-ttu-id="737de-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="737de-119">Data Item Type</span></span>|<span data-ttu-id="737de-120">Описание</span><span class="sxs-lookup"><span data-stu-id="737de-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="737de-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="737de-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="737de-122">Имя CLR FullName типа вызванного инспектора `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="737de-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="737de-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="737de-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="737de-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="737de-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="737de-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="737de-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="737de-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="737de-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="737de-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="737de-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="737de-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="737de-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
