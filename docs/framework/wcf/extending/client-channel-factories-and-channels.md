---
description: 'Дополнительные сведения: Клиент: фабрики каналов и каналы'
title: 'Клиент: Фабрики каналов и каналы'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: b61c37743899b8ba74ec18cc84397e4521e7bde7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803039"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="335e1-103">Клиент: Фабрики каналов и каналы</span><span class="sxs-lookup"><span data-stu-id="335e1-103">Client: Channel Factories and Channels</span></span>

<span data-ttu-id="335e1-104">В этом разделе рассматривается создание фабрик каналов и каналов.</span><span class="sxs-lookup"><span data-stu-id="335e1-104">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="335e1-105">Фабрики каналов и каналы</span><span class="sxs-lookup"><span data-stu-id="335e1-105">Channel Factories and Channels</span></span>  

 <span data-ttu-id="335e1-106">Фабрики каналов отвечают за создание каналов.</span><span class="sxs-lookup"><span data-stu-id="335e1-106">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="335e1-107">Каналы, создаваемые фабриками каналов, используются для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="335e1-107">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="335e1-108">Эти каналы отвечают за получение сообщения от вышестоящего уровня, выполнение той или иной обработки и отправку сообщения нижестоящему уровню.</span><span class="sxs-lookup"><span data-stu-id="335e1-108">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="335e1-109">Следующий рисунок иллюстрирует этот процесс.</span><span class="sxs-lookup"><span data-stu-id="335e1-109">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="335e1-110">![Каналы и производства клиента](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="335e1-110">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="335e1-111">Фабрика каналов создает каналы.</span><span class="sxs-lookup"><span data-stu-id="335e1-111">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="335e1-112">При закрытии фабрики каналов отвечают за закрытие всех созданных ими каналов, которые еще не закрыты.</span><span class="sxs-lookup"><span data-stu-id="335e1-112">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="335e1-113">Обратите внимание, что модель в данном случае асимметрична: когда закрывается прослушиватель каналов, он прекращает только принимать новые каналы, однако оставляет существующие каналы открытыми, чтобы они могли продолжить получать сообщения.</span><span class="sxs-lookup"><span data-stu-id="335e1-113">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="335e1-114">WCF предоставляет вспомогательные методы базового класса для этого процесса.</span><span class="sxs-lookup"><span data-stu-id="335e1-114">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="335e1-115">(Схема вспомогательных классов канала, обсуждаемых в этом разделе, см. в разделе [Общие сведения о модели каналов](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="335e1-115">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="335e1-116"><xref:System.ServiceModel.Channels.CommunicationObject>Класс реализует <xref:System.ServiceModel.ICommunicationObject> и применяет конечный автомат, описанный в шаге 2 [разработки каналов](developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="335e1-116">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="335e1-117"><xref:System.ServiceModel.Channels.ChannelManagerBase>Класс реализует <xref:System.ServiceModel.Channels.CommunicationObject> и предоставляет унифицированный базовый класс для <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> и <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="335e1-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="335e1-118">Класс <xref:System.ServiceModel.Channels.ChannelManagerBase> работает совместно с классом <xref:System.ServiceModel.Channels.ChannelBase> - базовым классом, реализующим интерфейс <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="335e1-118">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="335e1-119"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Класс реализует <xref:System.ServiceModel.Channels.ChannelManagerBase> и <xref:System.ServiceModel.Channels.IChannelFactory> объединяет `CreateChannel` перегрузки в один `OnCreateChannel` абстрактный метод.</span><span class="sxs-lookup"><span data-stu-id="335e1-119">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="335e1-120"><xref:System.ServiceModel.Channels.ChannelListenerBase>Класс реализует <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="335e1-120">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="335e1-121">Он отвечает за базовое управление состоянием.</span><span class="sxs-lookup"><span data-stu-id="335e1-121">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="335e1-122">Следующее обсуждение основано на примере [Transport: UDP](../samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="335e1-122">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="335e1-123">Создание фабрики каналов</span><span class="sxs-lookup"><span data-stu-id="335e1-123">Creating a Channel Factory</span></span>  

 <span data-ttu-id="335e1-124">Фабрика`UdpChannelFactory` наследуется от класса <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="335e1-124">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="335e1-125">В образце переопределяется метод <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> для обеспечения доступа к версии сообщения кодировщика сообщений.</span><span class="sxs-lookup"><span data-stu-id="335e1-125">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="335e1-126">Также переопределяется метод <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> для уничтожения созданного экземпляра класса <xref:System.ServiceModel.Channels.BufferManager> при переходе конечного автомата в другое состояние.</span><span class="sxs-lookup"><span data-stu-id="335e1-126">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="335e1-127">Выходной канал UDP</span><span class="sxs-lookup"><span data-stu-id="335e1-127">The UDP Output Channel</span></span>  

 <span data-ttu-id="335e1-128">Класс`UdpOutputChannel` реализует интерфейс <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="335e1-128">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="335e1-129">Конструктор проверяет аргументы и создает целевой объект <xref:System.Net.EndPoint> на основании переданного ему адреса <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="335e1-129">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="335e1-130">Переопределение метода <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> создает сокет, используемый для отправки сообщений этому объекту <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="335e1-130">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="335e1-131">Канал может быть закрыт правильно или неправильно.</span><span class="sxs-lookup"><span data-stu-id="335e1-131">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="335e1-132">При верном закрытии канала сокет закрывается и вызывается метод `OnClose` базового класса.</span><span class="sxs-lookup"><span data-stu-id="335e1-132">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="335e1-133">Если при этом создается исключение, инфраструктура вызывает метод `Abort`, чтоб обеспечить очистку канала.</span><span class="sxs-lookup"><span data-stu-id="335e1-133">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="335e1-134">Реализуйте `Send()` и `BeginSend()` / `EndSend()` .</span><span class="sxs-lookup"><span data-stu-id="335e1-134">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="335e1-135">Реализация делится на две принципиальные части.</span><span class="sxs-lookup"><span data-stu-id="335e1-135">This breaks down into two main sections.</span></span> <span data-ttu-id="335e1-136">Сначала сериализуйте сообщение в байтовый массив:</span><span class="sxs-lookup"><span data-stu-id="335e1-136">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="335e1-137">Затем отправьте получившиеся данные по сети:</span><span class="sxs-lookup"><span data-stu-id="335e1-137">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="335e1-138">См. также</span><span class="sxs-lookup"><span data-stu-id="335e1-138">See also</span></span>

- [<span data-ttu-id="335e1-139">Разработка каналов</span><span class="sxs-lookup"><span data-stu-id="335e1-139">Developing Channels</span></span>](developing-channels.md)
