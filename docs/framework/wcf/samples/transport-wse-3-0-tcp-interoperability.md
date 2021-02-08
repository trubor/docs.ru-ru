---
description: 'Дополнительные сведения см. в статье транспорт: расширение возможностей протокола TCP WSE 3,0'
title: 'Транспорт: TCP-взаимодействие WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 2e0a5927b8f16116dc07910970268ff6ec35f396
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798242"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="0e047-103">Транспорт: TCP-взаимодействие WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="0e047-103">Transport: WSE 3.0 TCP Interoperability</span></span>

<span data-ttu-id="0e047-104">В примере транспорта TCP-взаимодействия WSE 3,0 показано, как реализовать дуплексный сеанс TCP в качестве настраиваемого транспорта Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0e047-104">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="0e047-105">Также демонстрируется использование расширяемости уровня канала для создания интерфейса по сети с существующими развернутыми системами.</span><span class="sxs-lookup"><span data-stu-id="0e047-105">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="0e047-106">Ниже показано, как создать этот настраиваемый транспорт WCF.</span><span class="sxs-lookup"><span data-stu-id="0e047-106">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="0e047-107">Начиная с сокета TCP, создайте клиентские и серверные реализации интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, использующие кадрирование DIME для разграничения границ сообщений.</span><span class="sxs-lookup"><span data-stu-id="0e047-107">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="0e047-108">Создайте фабрику каналов, которая подключается к службе TCP WSE и передает кадрированные сообщения через клиентские интерфейсы <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="0e047-108">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="0e047-109">Создайте прослушиватель канала для приема входящих подключений TCP и создания соответствующих каналов.</span><span class="sxs-lookup"><span data-stu-id="0e047-109">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="0e047-110">Убедитесь, что все исключения, связанные с сетью, нормализованы в соответствующий класс, унаследованный от <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="0e047-110">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="0e047-111">Добавьте элемент привязки, добавляющий пользовательский транспорт в стек каналов.</span><span class="sxs-lookup"><span data-stu-id="0e047-111">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="0e047-112">Дополнительные сведения см. в разделе [Добавление элемента привязки].</span><span class="sxs-lookup"><span data-stu-id="0e047-112">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="0e047-113">Создание IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="0e047-113">Creating IDuplexSessionChannel</span></span>  

 <span data-ttu-id="0e047-114">Первый этап создания транспорта взаимодействия TCP WSE 3.0 - это реализация интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel> на основе класса <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="0e047-114">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="0e047-115">Интерфейс `WseTcpDuplexSessionChannel` является производным от интерфейса <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="0e047-115">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="0e047-116">Логика передачи сообщения состоит из двух основных частей: (1) кодирование сообщения в байты и (2) кадрирование этих байтов и передача их по сети.</span><span class="sxs-lookup"><span data-stu-id="0e047-116">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="0e047-117">Кроме того, устанавливается блокировка, чтобы вызовы Send() сохраняли гарантию порядка IDuplexSessionChannel и чтобы вызовы соответствующего сокета были правильно синхронизированы.</span><span class="sxs-lookup"><span data-stu-id="0e047-117">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="0e047-118">`WseTcpDuplexSessionChannel` использует <xref:System.ServiceModel.Channels.MessageEncoder> для преобразования <xref:System.ServiceModel.Channels.Message> в массив byte[] и из него.</span><span class="sxs-lookup"><span data-stu-id="0e047-118">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="0e047-119">Так как это транспорт, канал `WseTcpDuplexSessionChannel` также отвечает за использование удаленного адреса, с которым был настроен канал.</span><span class="sxs-lookup"><span data-stu-id="0e047-119">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="0e047-120">`EncodeMessage` инкапсулирует логику для этого преобразования.</span><span class="sxs-lookup"><span data-stu-id="0e047-120">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="0e047-121">После того как сообщение <xref:System.ServiceModel.Channels.Message> закодировано в байты, оно должно быть передано по сети.</span><span class="sxs-lookup"><span data-stu-id="0e047-121">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="0e047-122">Для этого требуется система определения границ сообщения.</span><span class="sxs-lookup"><span data-stu-id="0e047-122">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="0e047-123">WSE 3,0 использует версию [Dime](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) в качестве протокола кадрирования.</span><span class="sxs-lookup"><span data-stu-id="0e047-123">WSE 3.0 uses a version of [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="0e047-124">`WriteData` инкапсулирует логику кадрирования для заключения массива byte[] в набор записей DIME.</span><span class="sxs-lookup"><span data-stu-id="0e047-124">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="0e047-125">Логика получения сообщений аналогична.</span><span class="sxs-lookup"><span data-stu-id="0e047-125">The logic for receiving messages is similar.</span></span> <span data-ttu-id="0e047-126">Основной сложностью является обработка того факта, что считанный сокет может вернуть меньше байтов, чем было запрошено.</span><span class="sxs-lookup"><span data-stu-id="0e047-126">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="0e047-127">Чтобы принять сообщение, `WseTcpDuplexSessionChannel` считывает байты из сети, декодирует кадрирование DIME, затем использует <xref:System.ServiceModel.Channels.MessageEncoder> для преобразования массива byte[] в сообщение <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="0e047-127">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="0e047-128">Базовый класс `WseTcpDuplexSessionChannel` предполагает, что он получает подключенный сокет.</span><span class="sxs-lookup"><span data-stu-id="0e047-128">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="0e047-129">Базовый класс обрабатывает завершение работы сокета.</span><span class="sxs-lookup"><span data-stu-id="0e047-129">The base class handles socket shutdown.</span></span> <span data-ttu-id="0e047-130">Существуют три места, взаимодействующих с закрытием сокета:</span><span class="sxs-lookup"><span data-stu-id="0e047-130">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="0e047-131">OnAbort - закрыть сокет некорректно (жесткое закрытие).</span><span class="sxs-lookup"><span data-stu-id="0e047-131">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="0e047-132">On[Begin]Close - закрыть сокет корректно (мягкое закрытие).</span><span class="sxs-lookup"><span data-stu-id="0e047-132">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="0e047-133">сессии. Вызова CloseOutputSession — завершение потока исходящих данных (половина закрытия).</span><span class="sxs-lookup"><span data-stu-id="0e047-133">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="0e047-134">Фабрика каналов</span><span class="sxs-lookup"><span data-stu-id="0e047-134">Channel Factory</span></span>  

 <span data-ttu-id="0e047-135">Следующий этап создания транспорта TCP - реализация <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов.</span><span class="sxs-lookup"><span data-stu-id="0e047-135">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="0e047-136">`WseTcpChannelFactory`является производным от <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="0e047-136">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="0e047-137">Это фабрика, которая переопределяет `OnCreateChannel` для создания каналов клиентов.</span><span class="sxs-lookup"><span data-stu-id="0e047-137">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="0e047-138">`ClientWseTcpDuplexSessionChannel` Добавляет логику к базе `WseTcpDuplexSessionChannel` для подключения к TCP-серверу в `channel.Open` момент времени.</span><span class="sxs-lookup"><span data-stu-id="0e047-138">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="0e047-139">Сначала имя узла разрешается в IP-адрес, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="0e047-139">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="0e047-140">Затем имя узла подключается в цикле к первому доступному IP-адресу, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="0e047-140">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="0e047-141">Как часть контракта канала, все специфичные для домена расширения заключаются в оболочку, как `SocketException` в <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="0e047-141">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="0e047-142">Прослушиватель канала</span><span class="sxs-lookup"><span data-stu-id="0e047-142">Channel Listener</span></span>  

 <span data-ttu-id="0e047-143">Следующий этап создания транспорта TCP - реализация <xref:System.ServiceModel.Channels.IChannelListener> для приема каналов сервера.</span><span class="sxs-lookup"><span data-stu-id="0e047-143">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="0e047-144">`WseTcpChannelListener`является производным от <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> и переопределяет метод [begin] Open и on [begin] Close для управления временем существования прослушивающего сокета.</span><span class="sxs-lookup"><span data-stu-id="0e047-144">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="0e047-145">В OnOpen создается сокет для прослушивания по IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="0e047-145">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="0e047-146">Более сложные реализации могут создавать второй сокет для прослушивания также и по IPv6.</span><span class="sxs-lookup"><span data-stu-id="0e047-146">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="0e047-147">Они могут также допускать задание IP-адреса в имени узла.</span><span class="sxs-lookup"><span data-stu-id="0e047-147">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="0e047-148">Когда принимается новый сокет, инициализируется новый канал сервера с этим сокетом.</span><span class="sxs-lookup"><span data-stu-id="0e047-148">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="0e047-149">Все операции ввода и вывода уже реализованы в базовом классе, поэтому этот канал отвечает за инициализацию сокета.</span><span class="sxs-lookup"><span data-stu-id="0e047-149">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="0e047-150">Добавление элемента привязки</span><span class="sxs-lookup"><span data-stu-id="0e047-150">Adding a Binding Element</span></span>  

 <span data-ttu-id="0e047-151">Теперь, когда фабрики и каналы построены, они должны быть предоставлены среде выполнения ServiceModel через привязку.</span><span class="sxs-lookup"><span data-stu-id="0e047-151">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="0e047-152">Привязка - это коллекция элементов привязки, представляющая стек связи для адреса службы.</span><span class="sxs-lookup"><span data-stu-id="0e047-152">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="0e047-153">Каждый элемент стека представлен элементом привязки.</span><span class="sxs-lookup"><span data-stu-id="0e047-153">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="0e047-154">В этом примере в качестве элемента привязки выступает элемент `WseTcpTransportBindingElement`, являющийся производным элемента <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="0e047-154">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="0e047-155">Он поддерживает <xref:System.ServiceModel.Channels.IDuplexSessionChannel> и переопределяет следующие методы создания фабрик, связанных с нашей привязкой.</span><span class="sxs-lookup"><span data-stu-id="0e047-155">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="0e047-156">Он также содержит члены для клонирования элемента `BindingElement` и возврата схемы (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="0e047-156">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="0e047-157">Тестовая консоль WSE TCP</span><span class="sxs-lookup"><span data-stu-id="0e047-157">The WSE TCP Test Console</span></span>  

 <span data-ttu-id="0e047-158">Тестовый код для использования этого образца транспорта находится в файле TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="0e047-158">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="0e047-159">Ниже показано, как выполнить построение и запуск образца `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="0e047-159">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="0e047-160">Тестовый код создает пользовательскую привязку, которая использует MTOM для кодирования и `WseTcpTransport` для транспорта.</span><span class="sxs-lookup"><span data-stu-id="0e047-160">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="0e047-161">Он также настраивает AddressingVersion для соответствия WSE 3.0, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="0e047-161">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="0e047-162">Он состоит из двух тестов - один тест настраивает типизированного клиента с помощью кода, созданного из WSE 3.0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="0e047-162">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="0e047-163">Второй тест использует WCF как клиент и сервер, отправляя сообщения непосредственно через интерфейсы API канала.</span><span class="sxs-lookup"><span data-stu-id="0e047-163">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="0e047-164">При выполнении этого образца ожидаются следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="0e047-164">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="0e047-165">Клиент:</span><span class="sxs-lookup"><span data-stu-id="0e047-165">Client:</span></span>  
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="0e047-166">Сервер: </span><span class="sxs-lookup"><span data-stu-id="0e047-166">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="0e047-167">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="0e047-167">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0e047-168">Для работы с этим примером необходимы [улучшения веб-служб (WSE) 3,0 для Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) и `TcpSyncStockService` установлен пример WSE.</span><span class="sxs-lookup"><span data-stu-id="0e047-168">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0e047-169">Поскольку WSE 3,0 не поддерживается в Windows Server 2008, вы не можете установить или запустить этот `TcpSyncStockService` пример в этой операционной системе.</span><span class="sxs-lookup"><span data-stu-id="0e047-169">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="0e047-170">После установки примера `TcpSyncStockService` выполните следующие операции.</span><span class="sxs-lookup"><span data-stu-id="0e047-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="0e047-171">Откройте `TcpSyncStockService` в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e047-171">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="0e047-172">(Пример Ткпсинкстокксервице устанавливается с помощью WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e047-172">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="0e047-173">Это не часть кода этого примера.)</span><span class="sxs-lookup"><span data-stu-id="0e047-173">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="0e047-174">Задайте проект Стокксервице в качестве запускаемого проекта.</span><span class="sxs-lookup"><span data-stu-id="0e047-174">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="0e047-175">Откройте файл StockService.cs в проекте StockService и закомментируйте атрибут [Policy] класса `StockService`.</span><span class="sxs-lookup"><span data-stu-id="0e047-175">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="0e047-176">Таким образом в примере отключается безопасность.</span><span class="sxs-lookup"><span data-stu-id="0e047-176">This disables security from the sample.</span></span> <span data-ttu-id="0e047-177">Несмотря на то, что WCF может взаимодействовать с защищенными конечными точками WSE 3,0, Безопасность отключена, чтобы не усложнять этот пример на настраиваемом TCP-транспорте.</span><span class="sxs-lookup"><span data-stu-id="0e047-177">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="0e047-178">Нажмите клавишу F5, чтобы запустить `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="0e047-178">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="0e047-179">Служба запускается в новом окне консоли.</span><span class="sxs-lookup"><span data-stu-id="0e047-179">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="0e047-180">Откройте пример транспорта TCP в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e047-180">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="0e047-181">Обновите переменную "hostname" в файле TestCode.cs, чтобы она соответствовала имени компьютера, на котором запущена служба `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="0e047-181">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="0e047-182">Нажмите клавишу F5, чтобы запустить пример транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="0e047-182">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="0e047-183">Тестовый клиент транспорта TCP запускается в новой консоли.</span><span class="sxs-lookup"><span data-stu-id="0e047-183">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="0e047-184">Клиент запрашивает у службы цены акций и отображает результаты в своем окне консоли.</span><span class="sxs-lookup"><span data-stu-id="0e047-184">The client requests stock quotes from the service and then displays the results in its console window.</span></span>
