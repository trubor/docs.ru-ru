---
description: Дополнительные сведения о размещении службы данных (службы данных WCF)
title: Размещение служб данных (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 519adde3a3e054d68ff9a1b7acf7ff06c0ca7532
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765793"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="3e0e7-103">Размещение служб данных (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="3e0e7-103">Hosting the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="3e0e7-104">С помощью службы данных WCF можно создать службу, которая предоставляет данные в виде веб-канала Open Data Protocol (OData).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-104">By using WCF Data Services, you can create a service that exposes data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="3e0e7-105">Эта служба данных определена в качестве класса, наследуемого от <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-105">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="3e0e7-106">Этот класс предоставляет функции, необходимые для обработки сообщений запросов, выполнения обновлений для источника данных и создания сообщений ответов в соответствии с требованиями OData.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-106">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="3e0e7-107">Однако служба данных не привязывается к сетевому сокету и не может его прослушивать в ожидании входящих HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-107">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="3e0e7-108">Реализацию этой обязательной функциональности служба данных возлагает на размещающий компонент.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-108">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="3e0e7-109">Узел службы данных выполняет следующие задачи от имени источника данных:</span><span class="sxs-lookup"><span data-stu-id="3e0e7-109">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="3e0e7-110">Прослушивает запросы и перенаправляет их службе данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-110">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="3e0e7-111">Создает экземпляр службы данных для каждого запроса.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-111">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="3e0e7-112">Запрашивает обработку входящего запроса службой данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-112">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="3e0e7-113">Отправляет ответ от имени службы данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-113">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="3e0e7-114">Для упрощения размещения службы данных службы данных WCF предназначен для интеграции с Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-114">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3e0e7-115">Служба данных предоставляет реализацию WCF по умолчанию, которая служит узлом службы данных в приложении ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-115">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="3e0e7-116">Следовательно, службу данных можно разместить одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="3e0e7-116">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="3e0e7-117">В приложении ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-117">In an ASP.NET application.</span></span>

- <span data-ttu-id="3e0e7-118">В управляемом приложении, которое поддерживает резидентные службы WCF.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-118">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="3e0e7-119">В других специализированных узлах службы данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-119">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="3e0e7-120">Размещение службы данных в приложении ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3e0e7-120">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="3e0e7-121">При использовании диалогового окна **Добавление нового элемента** в Visual Studio 2015 для определения службы данных в приложении ASP.NET это средство создает два новых файла в проекте.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-121">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="3e0e7-122">Первый файл имеет расширение `.svc` и определяет для среды выполнения WCF способ создания экземпляра службы данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-122">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="3e0e7-123">Ниже приведен пример этого файла для образца службы данных Northwind, созданного при выполнении [краткого руководства](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-123">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="3e0e7-124">Эта директива используется для инструкции приложения для создания узла службы для именованного класса службы данных путем использования класса <xref:System.Data.Services.DataServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-124">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="3e0e7-125">Страница с выделенным кодом для файла `.svc` содержит класс, являющийся реализацией самой службы данных, определенной следующим образом для образца службы данных Northwind:</span><span class="sxs-lookup"><span data-stu-id="3e0e7-125">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="3e0e7-126">Так как служба данных ведет себя как служба WCF, служба данных интегрируется с ASP.NET и соответствует модели веб-программирования WCF.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-126">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="3e0e7-127">Дополнительные сведения см. в статьях [службы WCF и ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) и [модель программирования веб-HTTP WCF](../../wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-127">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="3e0e7-128">Резидентные службы WCF</span><span class="sxs-lookup"><span data-stu-id="3e0e7-128">Self-Hosted WCF Services</span></span>

 <span data-ttu-id="3e0e7-129">Так как она включает реализацию WCF, службы данных WCF поддерживает самостоятельное размещение службы данных в качестве службы WCF.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-129">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="3e0e7-130">Служба может быть размещена самостоятельно в любом приложении платформа .NET Framework, например в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-130">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="3e0e7-131">Класс <xref:System.Data.Services.DataServiceHost>, наследуемый от <xref:System.ServiceModel.Web.WebServiceHost>, используется для создания экземпляров службы данных по определенному адресу.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-131">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="3e0e7-132">Резидентное размещение можно использовать для разработки и тестирования, поскольку оно упрощает развертывание и диагностику службы.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-132">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="3e0e7-133">Однако этот тип размещения не предоставляет расширенные функции размещения и управления, предоставляемые ASP.NET или службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-133">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="3e0e7-134">Дополнительные сведения см. [в разделе Размещение в управляемом приложении](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="3e0e7-134">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="3e0e7-135">Определение специализированных узлов служб данных</span><span class="sxs-lookup"><span data-stu-id="3e0e7-135">Defining a Custom Data Service Host</span></span>

 <span data-ttu-id="3e0e7-136">В случае если ограничения, связанные с реализацией узла WCF, неприемлемы, для службы данных можно также определить настраиваемый узел.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-136">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="3e0e7-137">Любой класс, реализующий интерфейс <xref:System.Data.Services.IDataServiceHost>, можно использовать в качестве сетевого узла для службы данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-137">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="3e0e7-138">Настраиваемый узел должен реализовать интерфейс <xref:System.Data.Services.IDataServiceHost> и поддерживать следующие основные функции узла службы данных:</span><span class="sxs-lookup"><span data-stu-id="3e0e7-138">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="3e0e7-139">Обеспечивать службу данных корневым путем службы.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-139">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="3e0e7-140">Обрабатывать данные заголовков запроса и ответа в соответствующей реализации элемента <xref:System.Data.Services.IDataServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-140">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="3e0e7-141">Обрабатывать исключения, сформированные службой данных.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-141">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="3e0e7-142">Проверять параметры в строке запроса.</span><span class="sxs-lookup"><span data-stu-id="3e0e7-142">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e0e7-143">См. также</span><span class="sxs-lookup"><span data-stu-id="3e0e7-143">See also</span></span>

- [<span data-ttu-id="3e0e7-144">Определение служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="3e0e7-144">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="3e0e7-145">Предоставление данных как службы</span><span class="sxs-lookup"><span data-stu-id="3e0e7-145">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="3e0e7-146">Настройка службы данных</span><span class="sxs-lookup"><span data-stu-id="3e0e7-146">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
