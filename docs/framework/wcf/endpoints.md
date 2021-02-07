---
description: 'Дополнительные сведения: Windows Communication Foundation конечных точек'
title: Конечные точки Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: caa918f2dd7ca7b0289cc1faf6d189270596808b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756777"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="548bd-103">Конечные точки Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="548bd-103">Windows Communication Foundation Endpoints</span></span>

<span data-ttu-id="548bd-104">Все взаимодействия со службой Windows Communication Foundation (WCF) осуществляется через *конечные точки* службы.</span><span class="sxs-lookup"><span data-stu-id="548bd-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="548bd-105">Конечные точки предоставляют клиентам доступ к функциональным возможностям, предлагаемым службой WCF.</span><span class="sxs-lookup"><span data-stu-id="548bd-105">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="548bd-106">Общие сведения о создании конечной точки см. в разделе [Общие сведения о создании конечной точки](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="548bd-106">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="548bd-107">Каждая конечная точка содержит:</span><span class="sxs-lookup"><span data-stu-id="548bd-107">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="548bd-108">адрес, показывающий, где можно найти конечную точку;</span><span class="sxs-lookup"><span data-stu-id="548bd-108">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="548bd-109">привязку, показывающую, как клиент может связаться с конечной точкой;</span><span class="sxs-lookup"><span data-stu-id="548bd-109">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="548bd-110">контракт, определяющий доступные методы.</span><span class="sxs-lookup"><span data-stu-id="548bd-110">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="548bd-111">Дополнительные сведения по способам задания этих отдельных частей конечной точки см. в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="548bd-111">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="548bd-112">Задание адреса конечной точки</span><span class="sxs-lookup"><span data-stu-id="548bd-112">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="548bd-113">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="548bd-113">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="548bd-114">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="548bd-114">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="548bd-115">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="548bd-115">In This Section</span></span>  

 [<span data-ttu-id="548bd-116">Общие сведения о создании конечных точек</span><span class="sxs-lookup"><span data-stu-id="548bd-116">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="548bd-117">Описывает структуру конечной точки и общие шаги по определению конечной точки в конфигурации и в коде, а также по использованию конечных точек по умолчанию, привязок и поведений, предоставляемых средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="548bd-117">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="548bd-118">Задание адреса конечной точки</span><span class="sxs-lookup"><span data-stu-id="548bd-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="548bd-119">Описывает, как взаимодействие со службой WCF осуществляется через конечные точки.</span><span class="sxs-lookup"><span data-stu-id="548bd-119">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="548bd-120">Практическое руководство. Создание конечной точки службы в конфигурации</span><span class="sxs-lookup"><span data-stu-id="548bd-120">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="548bd-121">Описание создания конечной точки службы в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="548bd-121">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="548bd-122">Практическое руководство. Создание конечной точки службы в коде</span><span class="sxs-lookup"><span data-stu-id="548bd-122">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="548bd-123">Описание создания конечной точки службы в коде.</span><span class="sxs-lookup"><span data-stu-id="548bd-123">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="548bd-124">Публикация конечных точек метаданных</span><span class="sxs-lookup"><span data-stu-id="548bd-124">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="548bd-125">Описание публикации метаданных путем публикации конечных точек метаданных в конфигурации и в коде.</span><span class="sxs-lookup"><span data-stu-id="548bd-125">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="548bd-126">Справочник</span><span class="sxs-lookup"><span data-stu-id="548bd-126">Reference</span></span>  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="548bd-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="548bd-127">Related Sections</span></span>  

 [<span data-ttu-id="548bd-128">Базовый жизненный цикл программирования</span><span class="sxs-lookup"><span data-stu-id="548bd-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
