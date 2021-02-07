---
description: Дополнительные сведения см. в статье транспорты в Windows Communication Foundation
title: Транспорты в Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: e80a1730de107c0433949b7d476944f38e386702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752617"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="5205b-103">Транспорты в Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5205b-103">Transports in Windows Communication Foundation</span></span>

<span data-ttu-id="5205b-104">Транспортный уровень является самым нижним уровнем стека каналов.</span><span class="sxs-lookup"><span data-stu-id="5205b-104">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="5205b-105">Основными транспортами, используемыми в Windows Communication Foundation (WCF), являются HTTP, HTTPS, TCP и именованные каналы.</span><span class="sxs-lookup"><span data-stu-id="5205b-105">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="5205b-106">В подразделах данного раздела рассматриваются выбор типа транспорта среди названных выше типов, настройка транспорта и задание свойств настройки.</span><span class="sxs-lookup"><span data-stu-id="5205b-106">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="5205b-107">В состав WCF входят дополнительные транспорты.</span><span class="sxs-lookup"><span data-stu-id="5205b-107">WCF includes additional transports.</span></span> <span data-ttu-id="5205b-108">Дополнительные сведения о службе очередей сообщений (MSMQ) см. в статье [очереди и надежные сеансы](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-108">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="5205b-109">Дополнительные сведения о одноранговом транспорте см. в разделе одноранговая [сеть](peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-109">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5205b-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="5205b-110">In This Section</span></span>  

 [<span data-ttu-id="5205b-111">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="5205b-111">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="5205b-112">Описываются три основных типа транспорта и рассматриваются вопросы выбора транспорта.</span><span class="sxs-lookup"><span data-stu-id="5205b-112">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="5205b-113">Выбор кодировщика сообщений</span><span class="sxs-lookup"><span data-stu-id="5205b-113">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="5205b-114">Описываются факторы, которые необходимо принять во внимание при выборе элемента привязки для кодирования сообщений.</span><span class="sxs-lookup"><span data-stu-id="5205b-114">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="5205b-115">Потоковая передача сообщений</span><span class="sxs-lookup"><span data-stu-id="5205b-115">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="5205b-116">Описывается настройка транспортного уровня для выполнения потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="5205b-116">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="5205b-117">Настройка HTTP и HTTPS</span><span class="sxs-lookup"><span data-stu-id="5205b-117">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="5205b-118">Описывается настройка элементов привязки транспорта HTTP и HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5205b-118">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="5205b-119">Практическое руководство. Как заменить URL-резервирование WCF на ограниченное резервирование</span><span class="sxs-lookup"><span data-stu-id="5205b-119">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="5205b-120">Описывает, как использовать ограниченные резервирования ВКФУРЛ.</span><span class="sxs-lookup"><span data-stu-id="5205b-120">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="5205b-121">Квоты транспорта</span><span class="sxs-lookup"><span data-stu-id="5205b-121">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="5205b-122">Рассматриваются вопросы задания квот, доступных на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="5205b-122">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="5205b-123">Работа со средствами NAT и брандмауэрами</span><span class="sxs-lookup"><span data-stu-id="5205b-123">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="5205b-124">Описывается настройка транспортного уровня при отправке или получении сообщений за брандмауэром или при использовании преобразования сетевых адресов (NAT).</span><span class="sxs-lookup"><span data-stu-id="5205b-124">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="5205b-125">Совместное использование портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5205b-125">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="5205b-126">Описывает, как использовать компонент совместного использования портов net. TCP в WCF.</span><span class="sxs-lookup"><span data-stu-id="5205b-126">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5205b-127">Справочник</span><span class="sxs-lookup"><span data-stu-id="5205b-127">Reference</span></span>  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="5205b-128">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="5205b-128">Related Sections</span></span>  

 [<span data-ttu-id="5205b-129">Привязки</span><span class="sxs-lookup"><span data-stu-id="5205b-129">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="5205b-130">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="5205b-130">Extending Bindings</span></span>](../extending/extending-bindings.md)
