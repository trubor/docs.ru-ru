---
description: 'Дополнительные сведения: создание многоадресных приложений с помощью транспорта UDP'
title: Создание приложений многоадресной рассылки с помощью транспорта определяемой пользователем функции
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: cea76bc1256d52dabebe525b0fdd8b64c08f9e7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705165"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="f1306-103">Создание приложений многоадресной рассылки с помощью транспорта определяемой пользователем функции</span><span class="sxs-lookup"><span data-stu-id="f1306-103">Creating Multicasting Applications using the UDP Transport</span></span>

<span data-ttu-id="f1306-104">Приложения многоадресной рассылки одновременно отправляют маленькие сообщения большому количеству получателей без необходимости установления прямого соединения.</span><span class="sxs-lookup"><span data-stu-id="f1306-104">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="f1306-105">Подобные приложения прежде всего ориентируются на скорость выполнения, а не надежность.</span><span class="sxs-lookup"><span data-stu-id="f1306-105">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="f1306-106">Другими словами, отправка данных точно в срок важнее обеспечения доставки конкретного сообщения.</span><span class="sxs-lookup"><span data-stu-id="f1306-106">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="f1306-107">WCF теперь поддерживает создание приложений многоадресной рассылки с помощью <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f1306-107">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="f1306-108">Этот транспорт может оказаться полезным в случаях, когда служба должна одновременно отправлять маленькие сообщения множеству клиентов.</span><span class="sxs-lookup"><span data-stu-id="f1306-108">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="f1306-109">Пример подобной службы - приложение, работающее с биржевыми сводками.</span><span class="sxs-lookup"><span data-stu-id="f1306-109">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="f1306-110">Реализация приложения многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="f1306-110">Implementing a Multicast Application</span></span>  

 <span data-ttu-id="f1306-111">Чтобы реализовать приложение многоадресной рассылки, определите контракт службы и реализуйте контракт службы для каждого программного компонента, который должен отвечать на сообщения многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-111">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="f1306-112">Например, приложение для работы с биржевыми сводками может определить такой контракт:</span><span class="sxs-lookup"><span data-stu-id="f1306-112">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="f1306-113">Каждое приложение, которому нужно получать сообщения многоадресной рассылки, должно разместить службу, реализующую данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f1306-113">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="f1306-114">Ниже представлен образец кода, демонстрирующий получение сообщений многоадресной рассылки:</span><span class="sxs-lookup"><span data-stu-id="f1306-114">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="f1306-115">Приложение задает UDP-адрес, который будут прослушивать все службы.</span><span class="sxs-lookup"><span data-stu-id="f1306-115">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="f1306-116">Создается новый объект <xref:System.ServiceModel.ServiceHost> и предоставляется конечная точка службы с помощью <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f1306-116">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="f1306-117">Затем открывается <xref:System.ServiceModel.ServiceHost> и начинает прослушивание в ожидании входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="f1306-117">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="f1306-118">В подобном варианте работы приложения клиент отправляет сообщения многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-118">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="f1306-119">Сообщения многоадресной рассылки получит каждая служба, прослушивающая правильный UDP-адрес.</span><span class="sxs-lookup"><span data-stu-id="f1306-119">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="f1306-120">Ниже приведен пример клиента, который отправляет сообщения многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-120">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="f1306-121">Данный код создает сводку биржевых данных, а затем использует контракт службы IStockTicker для многоадресной отправки сообщений и вызова служб, слушающих определенный UDP-адрес.</span><span class="sxs-lookup"><span data-stu-id="f1306-121">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="f1306-122">Протокол UDP и надежный обмен сообщениями</span><span class="sxs-lookup"><span data-stu-id="f1306-122">UDP and Reliable Messaging</span></span>  

  <span data-ttu-id="f1306-123">Привязка к UDP-протоколу не обеспечивает надежный обмен сообщениями из-за особенностей самого протокола UDP.</span><span class="sxs-lookup"><span data-stu-id="f1306-123">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="f1306-124">Если необходимо подтвердить получение сообщений удаленной конечной точкой, используйте транспорт, поддерживающий надежный обмен сообщениями, например протокол HTTP или TCP.</span><span class="sxs-lookup"><span data-stu-id="f1306-124">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="f1306-125">Дополнительные сведения о надежном обмене сообщениями см. в разделе <https://go.microsoft.com/fwlink/?LinkId=231830> .</span><span class="sxs-lookup"><span data-stu-id="f1306-125">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="f1306-126">Двусторонняя многоадресная отправка сообщений</span><span class="sxs-lookup"><span data-stu-id="f1306-126">Two-way Multicast Messaging</span></span>  

 <span data-ttu-id="f1306-127">Хотя сообщения многоадресной рассылки обычно отправляются в одну сторону, транспорт UdpBinding поддерживает обмен сообщениями в режиме «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="f1306-127">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="f1306-128">Сообщения, отправленные с помощью транспорта UDP, содержат адреса отправителя и получателя.</span><span class="sxs-lookup"><span data-stu-id="f1306-128">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="f1306-129">Следует соблюдать предосторожность при использовании адреса отправителя, так как он может быть изменен злоумышленниками в ходе доставки сообщения.</span><span class="sxs-lookup"><span data-stu-id="f1306-129">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="f1306-130">Адрес можно проверить с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="f1306-130">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="f1306-131">Данный код проверяет первый байт из адреса отправителя, чтобы определить, содержит ли он байт 0xE0, который означает, что это адрес многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-131">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="f1306-132">Соображения безопасности</span><span class="sxs-lookup"><span data-stu-id="f1306-132">Security Considerations</span></span>  

 <span data-ttu-id="f1306-133">При прослушивании сообщений многоадресной рассылки маршрутизатору отправляется ICMP-пакет, извещающий его о прослушивании адреса многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-133">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="f1306-134">Любой пользователь локальной подсети, имеющий соответствующие разрешения, может прослушивать пакеты подобных типов и определять прослушиваемый адрес и порт и многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="f1306-134">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="f1306-135">Не используйте IP-адрес отправителя по соображениям безопасности.</span><span class="sxs-lookup"><span data-stu-id="f1306-135">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="f1306-136">Возможна фальсификация этой информации, и приложение может начать отправлять ответы другому компьютеру.</span><span class="sxs-lookup"><span data-stu-id="f1306-136">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="f1306-137">Включение безопасности на уровне сообщения позволяет устранить подобную угрозу.</span><span class="sxs-lookup"><span data-stu-id="f1306-137">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="f1306-138">На уровне сети используйте протокол IPSec (Internet Protocol Security) или NAP (Network Access Protection).</span><span class="sxs-lookup"><span data-stu-id="f1306-138">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
