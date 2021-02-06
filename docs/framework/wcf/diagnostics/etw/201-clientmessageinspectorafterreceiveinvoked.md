---
description: 'Дополнительные сведения: 201-Клиентмессажеинспекторафтеррецеивеинвокед'
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 511f8bd039219d031c311f7def7b360b74df1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645156"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="6e34c-103">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="6e34c-103">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="6e34c-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="6e34c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e34c-105">ID</span><span class="sxs-lookup"><span data-stu-id="6e34c-105">ID</span></span>|<span data-ttu-id="6e34c-106">201</span><span class="sxs-lookup"><span data-stu-id="6e34c-106">201</span></span>|  
|<span data-ttu-id="6e34c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="6e34c-107">Keywords</span></span>|<span data-ttu-id="6e34c-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6e34c-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6e34c-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="6e34c-109">Level</span></span>|<span data-ttu-id="6e34c-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="6e34c-110">Information</span></span>|  
|<span data-ttu-id="6e34c-111">Канал</span><span class="sxs-lookup"><span data-stu-id="6e34c-111">Channel</span></span>|<span data-ttu-id="6e34c-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6e34c-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6e34c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="6e34c-113">Description</span></span>  

 <span data-ttu-id="6e34c-114">Это событие создается после того, как модель службы вызывает метод `AfterReceiveReply` для инспектора сообщений клиента.</span><span class="sxs-lookup"><span data-stu-id="6e34c-114">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6e34c-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="6e34c-115">Message</span></span>  

 <span data-ttu-id="6e34c-116">Диспетчер вызвал AfterReceiveReply относительно ClientMessageInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="6e34c-116">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6e34c-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="6e34c-117">Details</span></span>  
  
|<span data-ttu-id="6e34c-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="6e34c-118">Data Item Name</span></span>|<span data-ttu-id="6e34c-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="6e34c-119">Data Item Type</span></span>|<span data-ttu-id="6e34c-120">Описание</span><span class="sxs-lookup"><span data-stu-id="6e34c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6e34c-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="6e34c-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="6e34c-122">Имя CLR FullName типа вызванного инспектора.</span><span class="sxs-lookup"><span data-stu-id="6e34c-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="6e34c-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="6e34c-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="6e34c-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="6e34c-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6e34c-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="6e34c-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6e34c-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="6e34c-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6e34c-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="6e34c-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6e34c-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6e34c-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
