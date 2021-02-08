---
description: 'Дополнительные сведения: Общие сведения об обнаружении WCF'
title: Общие сведения об обнаружении WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: d6acfb86ce0961ea7fbfba7695bece067e3dcec2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779651"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="683ae-103">Общие сведения об обнаружении WCF</span><span class="sxs-lookup"><span data-stu-id="683ae-103">WCF Discovery Overview</span></span>

<span data-ttu-id="683ae-104">API обнаружения предоставляют унифицированную модель программирования для динамичной публикации и обнаружения веб-служб с использованием протокола WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="683ae-104">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="683ae-105">Эти API позволяют службам публиковать себя, а также позволяют клиентам находить опубликованные службы.</span><span class="sxs-lookup"><span data-stu-id="683ae-105">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="683ae-106">После того как служба была включена для обнаружения, она получает возможность отправлять объявляющие сообщения, а также прослушивать и отвечать на запросы обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-106">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="683ae-107">Службы, доступные для обнаружения, могут отправлять сообщения Hello для оповещения о своем появлении в сети и сообщения Bye для оповещения об уходе из сети.</span><span class="sxs-lookup"><span data-stu-id="683ae-107">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="683ae-108">Для нахождения службы клиенты отправляют запрос `Probe`, содержащий заданные критерии, например тип контракта службы, ключевые слова и область в сети.</span><span class="sxs-lookup"><span data-stu-id="683ae-108">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="683ae-109">Службы получают запрос `Probe` и определяют, соответствуют ли они критериям.</span><span class="sxs-lookup"><span data-stu-id="683ae-109">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="683ae-110">Если служба им соответствует, она отвечает, отправляя клиенту сообщение `ProbeMatch`, содержащее сведения, необходимые для установки связи со службой.</span><span class="sxs-lookup"><span data-stu-id="683ae-110">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="683ae-111">Клиенты также могут отправлять запросы `Resolve`, позволяющие им находить службы, изменившие адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="683ae-111">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="683ae-112">Соответствующие службы отвечают на запросы `Resolve`, отправляя клиенту сообщение `ResolveMatch`.</span><span class="sxs-lookup"><span data-stu-id="683ae-112">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="683ae-113">Нерегламентированный и управляемый режимы</span><span class="sxs-lookup"><span data-stu-id="683ae-113">Ad-Hoc and Managed Modes</span></span>  

 <span data-ttu-id="683ae-114">API обнаружения поддерживают два режима: управляемый и нерегламентированный.</span><span class="sxs-lookup"><span data-stu-id="683ae-114">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="683ae-115">В управляемом режиме существует централизованный сервер, называемый прокси-сервером обнаружения, содержащий сведения о доступных службах.</span><span class="sxs-lookup"><span data-stu-id="683ae-115">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="683ae-116">Этот прокси-сервер обнаружения может быть наполнен сведениями о службах несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="683ae-116">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="683ae-117">Например, службы могут отправлять при запуске сообщения объявления прокси-серверу обнаружения или же прокси-сервер может считывать данные из базы данных или файла конфигурации для определения доступных служб.</span><span class="sxs-lookup"><span data-stu-id="683ae-117">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="683ae-118">Метод заполнения прокси-сервера обнаружения определяется разработчиком.</span><span class="sxs-lookup"><span data-stu-id="683ae-118">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="683ae-119">Клиенты используют прокси-сервер обнаружения для получения сведений о доступных службах.</span><span class="sxs-lookup"><span data-stu-id="683ae-119">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="683ae-120">Когда клиент выполняет поиск службы, он отправляет сообщение `Probe` прокси-серверу обнаружения, а тот определяет, соответствуют ли известные ему службы той службе, которую ищет клиент.</span><span class="sxs-lookup"><span data-stu-id="683ae-120">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="683ae-121">Если совпадения присутствуют, прокси-сервер обнаружения отправляет клиенту ответ `ProbeMatch`.</span><span class="sxs-lookup"><span data-stu-id="683ae-121">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="683ae-122">Затем клиент может связаться со службой напрямую, используя сведения о службе, возвращенные прокси-сервером.</span><span class="sxs-lookup"><span data-stu-id="683ae-122">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="683ae-123">Основной принцип управляемого режима - отправка запросов обнаружения в одноадресном режиме одному прокси-серверу обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-123">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="683ae-124">Платформа .NET Framework содержит ключевые компоненты, позволяющие создавать собственные прокси-серверы.</span><span class="sxs-lookup"><span data-stu-id="683ae-124">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="683ae-125">Клиенты и службы могут находить прокси-сервер несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="683ae-125">Clients and services can locate the proxy by multiple methods:</span></span>  
  
- <span data-ttu-id="683ae-126">Прокси-сервер может отвечать на нерегламентированные сообщения.</span><span class="sxs-lookup"><span data-stu-id="683ae-126">The proxy can respond to ad-hoc messages.</span></span>  
  
- <span data-ttu-id="683ae-127">Прокси-сервер может отправлять сообщение объявления при запуске.</span><span class="sxs-lookup"><span data-stu-id="683ae-127">The proxy can send an announcement message during start up.</span></span>  
  
- <span data-ttu-id="683ae-128">Клиенты и службы могут быть настроены на поиск определенной известной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="683ae-128">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="683ae-129">В нерегламентированном режиме централизованного сервера не существует.</span><span class="sxs-lookup"><span data-stu-id="683ae-129">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="683ae-130">Все сообщения обнаружения, например объявления служб и запросы клиентов, отправляются многоканально.</span><span class="sxs-lookup"><span data-stu-id="683ae-130">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="683ae-131">По умолчанию платформа .NET Framework поддерживает нерегламентированное обнаружение по протоколу UDP.</span><span class="sxs-lookup"><span data-stu-id="683ae-131">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="683ae-132">Например, если служба настроена на отправку объявления «Hello» при запуске, она отправит его по известному множеству адресов с использованием протокола UDP.</span><span class="sxs-lookup"><span data-stu-id="683ae-132">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="683ae-133">Клиенты должны активно прослушивать данные объявления и проводить их обработку необходимым образом.</span><span class="sxs-lookup"><span data-stu-id="683ae-133">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="683ae-134">Если клиент отправляет сообщение `Probe` службе, то оно отправляется по сети с использованием многоканального протокола.</span><span class="sxs-lookup"><span data-stu-id="683ae-134">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="683ae-135">Каждая получившая запрос служба определяет, соответствует ли она критериям в сообщении `Probe`, и напрямую отвечает клиенту сообщением `ProbeMatch` в случае, если служба соответствует критериям из сообщения `Probe`.</span><span class="sxs-lookup"><span data-stu-id="683ae-135">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="683ae-136">Преимущества использования обнаружения WCF</span><span class="sxs-lookup"><span data-stu-id="683ae-136">Benefits of Using WCF Discovery</span></span>  

 <span data-ttu-id="683ae-137">Поскольку обнаружение WCF реализуется с использованием протокола WS-Discovery, оно может взаимодействовать с другими клиентами, службами и прокси-серверами, которые также реализуют протокол WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="683ae-137">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="683ae-138">Обнаружение WCF построено на основе существующих API WCF, что облегчает добавление функциональных возможностей обнаружения в существующие службы и клиенты.</span><span class="sxs-lookup"><span data-stu-id="683ae-138">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="683ae-139">Возможность обнаружения служб может быть легко добавлена через настройки конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="683ae-139">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="683ae-140">Кроме того, обнаружение WCF также поддерживает использование протокола обнаружения с другими видами транспорта, такими как одноранговая сеть, перекрытие имен и HTTP.</span><span class="sxs-lookup"><span data-stu-id="683ae-140">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="683ae-141">Обнаружение WCF поддерживает использование управляемого режима работы с использованием прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-141">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="683ae-142">Это может снизить сетевой трафик, поскольку сообщения отправляются напрямую на прокси-сервер обнаружения, а не рассылаются многоканально по всей сети.</span><span class="sxs-lookup"><span data-stu-id="683ae-142">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="683ae-143">Обнаружение WCF также обеспечивает большую гибкость при работе с веб-службами.</span><span class="sxs-lookup"><span data-stu-id="683ae-143">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="683ae-144">Например, можно изменить адрес службы без изменения настройки клиента или службы.</span><span class="sxs-lookup"><span data-stu-id="683ae-144">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="683ae-145">Если клиент должен получить доступ к службе, он может отправить сообщение `Probe` с помощью запроса `Find`, при этом служба вышлет ответ на его текущий адрес.</span><span class="sxs-lookup"><span data-stu-id="683ae-145">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="683ae-146">Обнаружение WCF позволяет клиентам выполнять поиск служб, основываясь на различных критериях, включая типы контрактов, элементы привязки, пространство имен, область, ключевые слова и номера версий.</span><span class="sxs-lookup"><span data-stu-id="683ae-146">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="683ae-147">Обнаружение WCF позволяет выполнять обнаружение во время разработки и во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="683ae-147">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="683ae-148">Добавленное в приложение обнаружение может быть использовано для включения других сценариев, например отказоустойчивости или автоматической настройки.</span><span class="sxs-lookup"><span data-stu-id="683ae-148">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="683ae-149">Публикация службы</span><span class="sxs-lookup"><span data-stu-id="683ae-149">Service Publication</span></span>  

 <span data-ttu-id="683ae-150">Чтобы сделать службу доступной для обнаружения, необходимо добавить объект <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> в узел службы, а также добавить конечную точку обнаружения для указания того, где следует прослушивать сообщения обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-150">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="683ae-151">В следующем примере кода показано, как можно изменить резидентную службу, сделав ее доступной для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-151">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="683ae-152">Чтобы сделать службу доступной для обнаружения, необходимо добавить экземпляр <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> в описание службы.</span><span class="sxs-lookup"><span data-stu-id="683ae-152">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="683ae-153">В узел службы нужно добавить экземпляр <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>, чтобы сообщить службе, где следует выполнять прослушивание запросов обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-153">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="683ae-154">В данном примере добавляется объект <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (производный от <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>), используемый для настройки службы на прослушивание запросов обнаружения через многоканальный транспорт UDP.</span><span class="sxs-lookup"><span data-stu-id="683ae-154">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="683ae-155">При использовании нерегламентированного обнаружения используется <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, поскольку все сообщения отправляются многоканально.</span><span class="sxs-lookup"><span data-stu-id="683ae-155">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="683ae-156">Объявление</span><span class="sxs-lookup"><span data-stu-id="683ae-156">Announcement</span></span>  

 <span data-ttu-id="683ae-157">По умолчанию при публикации службы сообщения оповещения не рассылаются.</span><span class="sxs-lookup"><span data-stu-id="683ae-157">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="683ae-158">Службу нужно настроить для отправки сообщений оповещения.</span><span class="sxs-lookup"><span data-stu-id="683ae-158">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="683ae-159">Это предоставляет разработчикам служб дополнительную гибкость, поскольку можно объявить службу отдельно от прослушивания сообщений обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-159">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="683ae-160">Объявления служб также могут быть использованы в качестве механизма регистрации служб на прокси-сервере обнаружения или в других службах.</span><span class="sxs-lookup"><span data-stu-id="683ae-160">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="683ae-161">В следующем коде показывается, как можно настроить службу для отправки сообщений с объявлениями по привязке UDP.</span><span class="sxs-lookup"><span data-stu-id="683ae-161">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="683ae-162">Обнаружение служб</span><span class="sxs-lookup"><span data-stu-id="683ae-162">Service Discovery</span></span>  

 <span data-ttu-id="683ae-163">Клиентское приложение может использовать класс <xref:System.ServiceModel.Discovery.DiscoveryClient> для поиска служб.</span><span class="sxs-lookup"><span data-stu-id="683ae-163">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="683ae-164">Разработчик создает экземпляр класса <xref:System.ServiceModel.Discovery.DiscoveryClient>, передающего конечную точку обнаружения, указывающую, куда следует отправлять сообщения `Probe` или `Resolve`.</span><span class="sxs-lookup"><span data-stu-id="683ae-164">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="683ae-165">После этого клиент вызывает метод <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, задающий критерии поиска в экземпляре <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="683ae-165">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="683ae-166">Если соответствующие службы найдены, метод <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> возвращает коллекцию <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="683ae-166">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="683ae-167">В следующем примере кода показывается, как вызвать метод `Find` и установить соединение с найденной службой.</span><span class="sxs-lookup"><span data-stu-id="683ae-167">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="683ae-168">Обнаружение и безопасность на уровне сообщения</span><span class="sxs-lookup"><span data-stu-id="683ae-168">Discovery and Message Level Security</span></span>  

 <span data-ttu-id="683ae-169">При использовании безопасности на уровне сообщения необходимо указать идентификатор <xref:System.ServiceModel.EndpointIdentity> конечной точки обнаружения службы и соответствующий идентификатор <xref:System.ServiceModel.EndpointIdentity> конечной точки обнаружения клиента.</span><span class="sxs-lookup"><span data-stu-id="683ae-169">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="683ae-170">Дополнительные сведения о безопасности на уровне сообщений см. в разделе [безопасность сообщений](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="683ae-170">For more information about message level security, see [Message Security](message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="683ae-171">Обнаружение и службы, размещенные на веб-сайтах</span><span class="sxs-lookup"><span data-stu-id="683ae-171">Discovery and Web Hosted Services</span></span>  

 <span data-ttu-id="683ae-172">Чтобы службы WCF могли быть обнаружены, они должны выполняться.</span><span class="sxs-lookup"><span data-stu-id="683ae-172">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="683ae-173">Службы WCF, размещенные на серверах IIS и WAS, не выполняются, пока сервер IIS/WAS не получит сообщение, привязанное к службе, и, следовательно, не могут быть обнаружены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="683ae-173">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="683ae-174">Сделать службы, размещаемые на веб-сайтах, обнаруживаемыми можно двумя способами:</span><span class="sxs-lookup"><span data-stu-id="683ae-174">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1. <span data-ttu-id="683ae-175">С помощью возможности автозапуска фабрики приложений Windows Server</span><span class="sxs-lookup"><span data-stu-id="683ae-175">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2. <span data-ttu-id="683ae-176">С помощью прокси-сервера обнаружения для установления связи от имени службы</span><span class="sxs-lookup"><span data-stu-id="683ae-176">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="683ae-177">В фабрике приложений Windows Server имеется возможность автозапуска, которая позволяет службе запускаться до получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="683ae-177">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="683ae-178">С помощью параметра автозапуска службу, размещенную в службах IIS/WAS, можно настроить для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-178">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="683ae-179">Дополнительные сведения о функции автоматического запуска см. в разделе [функция автоматического запуска Windows Server AppFabric](/previous-versions/appfabric/ee677260(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="683ae-179">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](/previous-versions/appfabric/ee677260(v=azure.10)).</span></span> <span data-ttu-id="683ae-180">Одновременно с включением возможности автозапуска необходимо настроить службу для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="683ae-180">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="683ae-181">Дополнительные сведения см. в разделе [как программно добавить возможность обнаружения в службу WCF и клиент](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Настройка обнаружения в файле конфигурации](configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="683ae-181">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="683ae-182">Прокси-сервер обнаружения может использоваться для связи от имени службы WCF, когда служба не выполняется.</span><span class="sxs-lookup"><span data-stu-id="683ae-182">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="683ae-183">Прокси-сервер может прослушивать входящие сообщения или сообщения разрешения и отвечать клиенту.</span><span class="sxs-lookup"><span data-stu-id="683ae-183">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="683ae-184">Клиент может затем отправлять сообщения непосредственно службе.</span><span class="sxs-lookup"><span data-stu-id="683ae-184">The client can then send messages directly to the service.</span></span> <span data-ttu-id="683ae-185">При отправке клиентом сообщения службе она будет запущена для ответа на сообщение.</span><span class="sxs-lookup"><span data-stu-id="683ae-185">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="683ae-186">Дополнительные сведения о реализации прокси-сервера обнаружения см. в разделе [Реализация прокси-сервера обнаружения](implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="683ae-186">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="683ae-187">Для правильной работы обнаружения WCF все сетевые карты (контроллер сетевого интерфейса) должны иметь только один IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="683ae-187">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
