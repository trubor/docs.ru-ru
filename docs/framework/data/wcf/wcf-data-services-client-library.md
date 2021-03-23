---
title: Библиотека клиентов служб данных WCF
description: Узнайте, как использовать клиентские библиотеки службы данных WCF для доступа к данным и их изменения из клиентского приложения платформа .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 3d8a0f869454ce24d847127c2097239886f3395b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805666"
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="e707e-103">Библиотека клиентов служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="e707e-103">WCF Data Services Client Library</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="e707e-104">Любое приложение может взаимодействовать со службой данных на основе Open Data Protocol (OData), если она может отправить HTTP-запрос и обработать канал OData, возвращаемый службой данных.</span><span class="sxs-lookup"><span data-stu-id="e707e-104">Any application can interact with an Open Data Protocol (OData)-based data service if it can send an HTTP request and process the OData feed that a data service returns.</span></span> <span data-ttu-id="e707e-105">Такое взаимодействие позволяет получать доступ к службам на основе OData из широкого спектра веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="e707e-105">This interoperability enables you to access OData-based services from a broad range of Web-enabled applications.</span></span> <span data-ttu-id="e707e-106">Службы данных WCF включает клиентские библиотеки, обеспечивающие более широкие возможности программирования при использовании веб-каналов OData из платформа .NET Framework или приложений на основе Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e707e-106">WCF Data Services includes client libraries that provide a richer programming experience when you consume OData feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="e707e-107">Клиентская библиотека содержит два основных класса: <xref:System.Data.Services.Client.DataServiceContext> и <xref:System.Data.Services.Client.DataServiceQuery%601>.</span><span class="sxs-lookup"><span data-stu-id="e707e-107">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="e707e-108">Класс <xref:System.Data.Services.Client.DataServiceContext> инкапсулирует операции, поддерживающие работу с конкретной службой данных.</span><span class="sxs-lookup"><span data-stu-id="e707e-108">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="e707e-109">Несмотря на то, что службы OData не имеют состояния, контекст не имеет.</span><span class="sxs-lookup"><span data-stu-id="e707e-109">Although OData services are stateless, the context is not.</span></span> <span data-ttu-id="e707e-110">Таким образом, класс можно использовать <xref:System.Data.Services.Client.DataServiceContext> для поддержания состояния на стороне клиента между взаимодействием со службой данных для поддержки таких функций, как управление изменениями.</span><span class="sxs-lookup"><span data-stu-id="e707e-110">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="e707e-111">Этот класс также управляет идентификаторами и отслеживает изменения.</span><span class="sxs-lookup"><span data-stu-id="e707e-111">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="e707e-112">Класс <xref:System.Data.Services.Client.DataServiceQuery%601> представляет запрос к определенному набору сущностей.</span><span class="sxs-lookup"><span data-stu-id="e707e-112">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="e707e-113">Этот раздел описывает использование клиентских библиотек для доступа и изменения данных из клиентского приложения .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e707e-113">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="e707e-114">Дополнительные сведения об использовании клиентской библиотеки службы данных WCF с приложением на основе Silverlight см. в разделе [службы данных WCF (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span><span class="sxs-lookup"><span data-stu-id="e707e-114">For more information about how to use the WCF Data Services client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span></span> <span data-ttu-id="e707e-115">Доступны другие клиентские библиотеки, позволяющие использовать канал OData в приложениях других типов.</span><span class="sxs-lookup"><span data-stu-id="e707e-115">Other client libraries are available that enable you to consume an OData feed in other kinds of applications.</span></span> <span data-ttu-id="e707e-116">Дополнительные сведения о пакете OData SDK см. в разделе [пример кода для ODATA SDK](https://www.odata.org/ecosystem/#sdk).</span><span class="sxs-lookup"><span data-stu-id="e707e-116">For more information on OData SDK, see [OData SDK - Sample Code](https://www.odata.org/ecosystem/#sdk).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e707e-117">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="e707e-117">In This Section</span></span>  

 [<span data-ttu-id="e707e-118">Создание библиотеки клиентов службы данных</span><span class="sxs-lookup"><span data-stu-id="e707e-118">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="e707e-119">Описывает, как создать клиентскую библиотеку и клиентские классы службы данных, основанные на каналах OData.</span><span class="sxs-lookup"><span data-stu-id="e707e-119">Describes how to generate a client library and client data service classes that are based on OData feeds.</span></span>  
  
 [<span data-ttu-id="e707e-120">Выполнение запросов к службе данных</span><span class="sxs-lookup"><span data-stu-id="e707e-120">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="e707e-121">Описывает выполнение запросов к службе данных из приложения на основе .NET Framework с помощью клиентских библиотек.</span><span class="sxs-lookup"><span data-stu-id="e707e-121">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="e707e-122">Загрузка отложенного содержимого</span><span class="sxs-lookup"><span data-stu-id="e707e-122">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="e707e-123">Описывает загрузку дополнительного содержимого, не включенного в первоначальный ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="e707e-123">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="e707e-124">Обновление службы данных</span><span class="sxs-lookup"><span data-stu-id="e707e-124">Updating the Data Service</span></span>](updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="e707e-125">Описывает создание, изменение и удаление сущностей и отношений с помощью клиентских библиотек.</span><span class="sxs-lookup"><span data-stu-id="e707e-125">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="e707e-126">Асинхронные операции</span><span class="sxs-lookup"><span data-stu-id="e707e-126">Asynchronous Operations</span></span>](asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="e707e-127">Описывает возможности, предоставляемые клиентскими библиотеками для асинхронной работы со службой данных.</span><span class="sxs-lookup"><span data-stu-id="e707e-127">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="e707e-128">Пакетные операции</span><span class="sxs-lookup"><span data-stu-id="e707e-128">Batching Operations</span></span>](batching-operations-wcf-data-services.md)  
 <span data-ttu-id="e707e-129">Описывает отправку нескольких запросов к службе данных в одном пакете с помощью клиентских библиотек.</span><span class="sxs-lookup"><span data-stu-id="e707e-129">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="e707e-130">Привязка данных к элементам управления</span><span class="sxs-lookup"><span data-stu-id="e707e-130">Binding Data to Controls</span></span>](binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="e707e-131">Описывает, как привязать элементы управления к каналу OData, возвращенному службой данных.</span><span class="sxs-lookup"><span data-stu-id="e707e-131">Describes how to bind controls to a OData feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="e707e-132">Вызов операций служб</span><span class="sxs-lookup"><span data-stu-id="e707e-132">Calling Service Operations</span></span>](calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="e707e-133">Описывает, как использовать клиентскую библиотеку для вызова операций службы.</span><span class="sxs-lookup"><span data-stu-id="e707e-133">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="e707e-134">Управление контекстом службы данных</span><span class="sxs-lookup"><span data-stu-id="e707e-134">Managing the Data Service Context</span></span>](managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="e707e-135">Описывает параметры управления режимом работы клиентской библиотеки.</span><span class="sxs-lookup"><span data-stu-id="e707e-135">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="e707e-136">Работа с двоичными данными</span><span class="sxs-lookup"><span data-stu-id="e707e-136">Working with Binary Data</span></span>](working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="e707e-137">Описывает доступ к двоичным данным, возвращенным службой данных в виде потока данных, и их изменение.</span><span class="sxs-lookup"><span data-stu-id="e707e-137">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e707e-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e707e-138">See also</span></span>

- [<span data-ttu-id="e707e-139">Определение служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="e707e-139">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="e707e-140">Начало работы</span><span class="sxs-lookup"><span data-stu-id="e707e-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
