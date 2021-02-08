---
description: 'Дополнительные сведения: объявления обнаружения и клиент объявлений'
title: Объявления обнаружения и клиент объявления
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 2076b4dbdc57bd3de47fccdb4a51ef9e6fc48366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802974"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="33c5a-103">Объявления обнаружения и клиент объявления</span><span class="sxs-lookup"><span data-stu-id="33c5a-103">Discovery Announcements and Announcement Client</span></span>

<span data-ttu-id="33c5a-104">Функция обнаружения WCF позволяет компонентам объявлять их доступность.</span><span class="sxs-lookup"><span data-stu-id="33c5a-104">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="33c5a-105">При соответствующей настройке служба отправляет объявления Hello и Bye.</span><span class="sxs-lookup"><span data-stu-id="33c5a-105">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="33c5a-106">Клиенты или другие компоненты могут прослушивать данные сообщения с объявлениями и действовать необходимым образом.</span><span class="sxs-lookup"><span data-stu-id="33c5a-106">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="33c5a-107">Это дает клиенту альтернативный метод получения данных о службах.</span><span class="sxs-lookup"><span data-stu-id="33c5a-107">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="33c5a-108">Функция объявлений может использоваться несколькими разными способами. Например, если службы часто входят в сеть и выходят из сети, то объявления могут стать альтернативой их поиску.</span><span class="sxs-lookup"><span data-stu-id="33c5a-108">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="33c5a-109">Такой подход дает возможность снизить нагрузку на сеть, а клиенту - получать больше сведений о наличии или отсутствии службы по мере получения объявлений.</span><span class="sxs-lookup"><span data-stu-id="33c5a-109">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>

## <a name="discovery-announcements"></a><span data-ttu-id="33c5a-110">Объявления обнаружения</span><span class="sxs-lookup"><span data-stu-id="33c5a-110">Discovery Announcements</span></span>

<span data-ttu-id="33c5a-111">Когда служба, настроенная для объявлений, подключается к сети и становится доступной для обнаружения, она отправляет сообщение Hello, которое объявляет прослушивающим клиентам о ее доступности.</span><span class="sxs-lookup"><span data-stu-id="33c5a-111">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="33c5a-112">Сообщение содержит сведения, связанные с обнаружением службы, например контракт, адрес конечной точки и соответствующие области.</span><span class="sxs-lookup"><span data-stu-id="33c5a-112">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="33c5a-113">В классе <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> можно указать, куда отправляется сообщение с объявлением.</span><span class="sxs-lookup"><span data-stu-id="33c5a-113">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="33c5a-114">Если конечной точкой объявления является <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, то сообщения Hello и Bye одновременно передаются нескольким абонентам. Если же конечная точка объявления является одноадресной рассылкой, то сообщения передаются непосредственно указанной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="33c5a-114">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="33c5a-115">Объявления отправляются при открытии и закрытии узла службы.</span><span class="sxs-lookup"><span data-stu-id="33c5a-115">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="33c5a-116">Если эти вызовы не завершаются должным образом, сообщение с объявлением, возможно, не будет отправлено. Например, если происходит сбой службы, то сообщение с объявлением Bye не отправляется.</span><span class="sxs-lookup"><span data-stu-id="33c5a-116">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>

> [!TIP]
> <span data-ttu-id="33c5a-117">Функцию объявлений можно настроить на отправку объявлений в заданных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="33c5a-117">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="33c5a-118">определяет <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> и <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> как стандартные конечные точки, позволяя службам и клиентам отправлять объявления Hello и Bye.</span><span class="sxs-lookup"><span data-stu-id="33c5a-118">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>

### <a name="announcements-on-the-service"></a><span data-ttu-id="33c5a-119">Объявления в службе</span><span class="sxs-lookup"><span data-stu-id="33c5a-119">Announcements on the Service</span></span>

<span data-ttu-id="33c5a-120">Чтобы настроить отправку объявлений службой, добавьте <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> с конечной точкой объявления.</span><span class="sxs-lookup"><span data-stu-id="33c5a-120">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="33c5a-121">В следующем примере показано, как программным способом добавить это поведение в узел службы.</span><span class="sxs-lookup"><span data-stu-id="33c5a-121">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="33c5a-122">В этом примере используется `UdpAnnouncementEndpoint`, которая подразумевает, что сообщения являются многоадресной рассылкой в расположения, указываемые конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="33c5a-122">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

<span data-ttu-id="33c5a-123">Это поведение можно также настроить в файле конфигурации, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="33c5a-123">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>

```xml
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="33c5a-124">В предыдущих примерах служба настраивается для автоматической отправки сообщений с объявлениями.</span><span class="sxs-lookup"><span data-stu-id="33c5a-124">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="33c5a-125">Можно также отправлять сообщения с объявлениями явным образом с помощью класса <xref:System.ServiceModel.Discovery.AnnouncementClient>.</span><span class="sxs-lookup"><span data-stu-id="33c5a-125">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>

### <a name="announcements-on-the-client"></a><span data-ttu-id="33c5a-126">Объявления на клиенте</span><span class="sxs-lookup"><span data-stu-id="33c5a-126">Announcements on the Client</span></span>

<span data-ttu-id="33c5a-127">В клиентском приложение должна быть размещена служба объявлений, которая занимается обработкой сообщений Hello и Bye и подписана на события <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> и <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived>.</span><span class="sxs-lookup"><span data-stu-id="33c5a-127">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="33c5a-128">В приведенном ниже примере показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="33c5a-128">The following example shows how to do this.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;

// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();

    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}
```

<span data-ttu-id="33c5a-129">При входящей обработке сообщения Hello или Bye метаданные обнаружения конечной точки доступны через <xref:System.ServiceModel.Discovery.AnnouncementEventArgs>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="33c5a-129">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}
```
