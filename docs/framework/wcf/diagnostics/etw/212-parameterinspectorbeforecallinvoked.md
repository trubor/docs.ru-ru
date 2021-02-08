---
description: 'Дополнительные сведения: 212-Параметеринспекторбефорекаллинвокед'
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: aa02ff22b533855716c212d312396e6de23ace42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794407"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="c523a-103">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="c523a-103">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="c523a-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="c523a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c523a-105">ID</span><span class="sxs-lookup"><span data-stu-id="c523a-105">ID</span></span>|<span data-ttu-id="c523a-106">212</span><span class="sxs-lookup"><span data-stu-id="c523a-106">212</span></span>|  
|<span data-ttu-id="c523a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c523a-107">Keywords</span></span>|<span data-ttu-id="c523a-108">Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c523a-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c523a-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="c523a-109">Level</span></span>|<span data-ttu-id="c523a-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="c523a-110">Information</span></span>|  
|<span data-ttu-id="c523a-111">Канал</span><span class="sxs-lookup"><span data-stu-id="c523a-111">Channel</span></span>|<span data-ttu-id="c523a-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c523a-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c523a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c523a-113">Description</span></span>  

 <span data-ttu-id="c523a-114">Это событие создается после того, как модель службы вызывает метод `BeforeCall` для `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="c523a-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c523a-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="c523a-115">Message</span></span>  

 <span data-ttu-id="c523a-116">Диспетчер вызвал BeforeCall для ParameterInspector типа «%1».</span><span class="sxs-lookup"><span data-stu-id="c523a-116">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c523a-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="c523a-117">Details</span></span>  
  
|<span data-ttu-id="c523a-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="c523a-118">Data Item Name</span></span>|<span data-ttu-id="c523a-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="c523a-119">Data Item Type</span></span>|<span data-ttu-id="c523a-120">Описание</span><span class="sxs-lookup"><span data-stu-id="c523a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c523a-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="c523a-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="c523a-122">Имя CLR FullName типа вызванного инспектора.</span><span class="sxs-lookup"><span data-stu-id="c523a-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="c523a-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="c523a-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="c523a-124">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="c523a-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c523a-125">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c523a-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c523a-126">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c523a-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c523a-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="c523a-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c523a-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c523a-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
