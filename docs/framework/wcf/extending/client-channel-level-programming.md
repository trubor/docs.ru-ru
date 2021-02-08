---
description: 'Дополнительные сведения: программирование Channel-Level клиента'
title: Программирование клиентов на уровне канала
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 7e4e977231339fbbede7111e38a67054eb24eed9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803000"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="1bf9d-103">Программирование клиентов на уровне канала</span><span class="sxs-lookup"><span data-stu-id="1bf9d-103">Client Channel-Level Programming</span></span>

<span data-ttu-id="1bf9d-104">В этом разделе описывается Написание клиентского приложения Windows Communication Foundation (WCF) без использования <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> класса и связанной с ним объектной модели.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-104">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="1bf9d-105">отправка сообщений</span><span class="sxs-lookup"><span data-stu-id="1bf9d-105">Sending Messages</span></span>  

 <span data-ttu-id="1bf9d-106">Чтобы подготовиться к отправке сообщений и получению и обработке ответов, необходимы следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-106">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="1bf9d-107">Создайте привязку.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-107">Create a binding.</span></span>  
  
2. <span data-ttu-id="1bf9d-108">Создайте фабрику каналов.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-108">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="1bf9d-109">Создание канала.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-109">Create a channel.</span></span>  
  
4. <span data-ttu-id="1bf9d-110">Отправьте запрос и прочитайте ответ.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-110">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="1bf9d-111">Закройте все объекты каналов.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-111">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="1bf9d-112">Создание привязки</span><span class="sxs-lookup"><span data-stu-id="1bf9d-112">Creating a Binding</span></span>  

 <span data-ttu-id="1bf9d-113">Как и в случае с получением (см. [службу Channel-Level программирование](service-channel-level-programming.md)), отправка сообщений начинается с создания привязки.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-113">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="1bf9d-114">В данном примере создается новая привязка <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, и в коллекцию ее элементов добавляется элемент <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-114">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="1bf9d-115">Создание фабрики каналов</span><span class="sxs-lookup"><span data-stu-id="1bf9d-115">Building a ChannelFactory</span></span>  

 <span data-ttu-id="1bf9d-116">На этот раз вместо того чтобы создавать прослушиватель каналов <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, следует создать производство каналов <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> вызовом метода <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> в привязке с параметром типа <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-116">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1bf9d-117">Прослушиватели каналов используются ожидающей входящих сообщений стороной, а фабрики каналов - стороной, которая инициирует связь для создания канала.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-117">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="1bf9d-118">Точно так же, как при работе с прослушивателями каналов, фабрики каналов можно использовать только после того, как они будут открыты.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-118">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="1bf9d-119">Создание канала</span><span class="sxs-lookup"><span data-stu-id="1bf9d-119">Creating a Channel</span></span>  

 <span data-ttu-id="1bf9d-120">Затем, чтобы создать канал <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>, необходимо вызвать метод <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-120">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="1bf9d-121">Этот вызов принимает адрес конечной точки, с которой необходимо установить связь, используя вновь создаваемый канал.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-121">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="1bf9d-122">После создания канала необходимо вызвать для него функцию "Открыть", чтобы подготовить его к взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-122">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="1bf9d-123">В зависимости от особенностей транспорта подобный вызов функции "Открыть" может инициировать соединение с целевой конечной точкой или не выполнить никаких действий в сети.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-123">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="1bf9d-124">Отправка запроса и чтение ответа</span><span class="sxs-lookup"><span data-stu-id="1bf9d-124">Sending a Request and Reading the Reply</span></span>  

 <span data-ttu-id="1bf9d-125">После открытия канала можно создать сообщение, воспользоваться методом запроса канала для отправки запроса и ожидать ответа.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-125">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="1bf9d-126">По возвращении этого метода приходит ответное сообщение, прочитав которое, можно узнать, каков был ответ конечной точки.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-126">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="1bf9d-127">Закрытие объектов</span><span class="sxs-lookup"><span data-stu-id="1bf9d-127">Closing Objects</span></span>  

 <span data-ttu-id="1bf9d-128">Во избежание утечки ресурсов следует закрывать объекты, используемые во взаимодействии, если они больше не требуются.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-128">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="1bf9d-129">В следующем примере кода показан основной клиент, использующий фабрику каналов для отправки сообщения и чтения ответа.</span><span class="sxs-lookup"><span data-stu-id="1bf9d-129">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
