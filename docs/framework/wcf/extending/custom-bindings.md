---
description: 'Дополнительные сведения: пользовательские привязки'
title: Пользовательские привязки
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: ced0f9ada7238b43216a246d75dd391aa6eb3f2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735352"
---
# <a name="custom-bindings"></a><span data-ttu-id="ad1c6-103">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="ad1c6-103">Custom Bindings</span></span>

<span data-ttu-id="ad1c6-104">Класс <xref:System.ServiceModel.Channels.CustomBinding> можно использовать, когда ни одна из системных привязок не соответствует требованиям службы.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-104">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="ad1c6-105">Все привязки создаются из упорядоченных наборов элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-105">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="ad1c6-106">Пользовательские привязки можно создавать из набора предоставляемых системой элементов привязки или в них можно включать определяемые пользователем элементы привязки.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-106">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="ad1c6-107">Пользовательские элементы привязки можно применять, например, для использования в конечной точке службы новых транспортов или кодировщиков.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-107">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="ad1c6-108">Рабочие примеры см. в разделе [образцы пользовательских привязок](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ad1c6-108">For working examples, see [Custom Binding Samples](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="ad1c6-109">Дополнительные сведения см. на веб-сайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad1c6-109">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="ad1c6-110">Создание пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="ad1c6-110">Construction of a Custom Binding</span></span>

<span data-ttu-id="ad1c6-111">Пользовательские привязки создаются с использованием одного из конструкторов <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> из коллекции элементов привязки, которые располагаются в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-111">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="ad1c6-112">Вверху расположен необязательный класс <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, который разрешает поток транзакций.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-112">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="ad1c6-113">Далее следует необязательный класс <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>, который обеспечивает сеанс и механизмы сортировки, в соответствии со спецификацией WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-113">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="ad1c6-114">Сеанс может включать посредников SOAP и транспорта.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-114">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="ad1c6-115">Далее следует необязательный класс <xref:System.ServiceModel.Channels.SecurityBindingElement>, который предоставляет возможности безопасности, такие как авторизация, проверка подлинности, защита и конфиденциальность.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-115">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="ad1c6-116">Далее следует необязательный класс <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>, который обеспечивает возможность двусторонней дуплексной связи с транспортным протоколом, изначально не поддерживающим дуплексную связь, таким как HTTP.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-116">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="ad1c6-117">Далее следует необязательный класс <xref:System.ServiceModel.Channels.OneWayBindingElement>), который обеспечивает одностороннюю связь.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-117">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="ad1c6-118">Далее следует обязательный элемент привязки безопасности потока, который может быть одним из следующих.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-118">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="ad1c6-119">Далее следует обязательный элемент привязки для кодирования сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-119">Next is a required message encoding binding element.</span></span> <span data-ttu-id="ad1c6-120">Можно использовать свой кодировщик транспорта или одну из трех привязок кодировки сообщений:</span><span class="sxs-lookup"><span data-stu-id="ad1c6-120">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="ad1c6-121">Внизу расположен обязательный элемент транспорта.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-121">At the bottom is a required transport element.</span></span> <span data-ttu-id="ad1c6-122">Вы можете использовать собственный транспорт или один из следующих элементов привязки транспорта Windows Communication Foundation (WCF) предоставляет следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-122">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="ad1c6-123">В следующей таблице приведены сводные данные по параметрам каждого уровня.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-123">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="ad1c6-124">Уровень</span><span class="sxs-lookup"><span data-stu-id="ad1c6-124">Layer</span></span>|<span data-ttu-id="ad1c6-125">Параметры</span><span class="sxs-lookup"><span data-stu-id="ad1c6-125">Options</span></span>|<span data-ttu-id="ad1c6-126">Обязательно</span><span class="sxs-lookup"><span data-stu-id="ad1c6-126">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="ad1c6-127">Transactions</span><span class="sxs-lookup"><span data-stu-id="ad1c6-127">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="ad1c6-128">Нет</span><span class="sxs-lookup"><span data-stu-id="ad1c6-128">No</span></span>|
|<span data-ttu-id="ad1c6-129">Надежность</span><span class="sxs-lookup"><span data-stu-id="ad1c6-129">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="ad1c6-130">Нет</span><span class="sxs-lookup"><span data-stu-id="ad1c6-130">No</span></span>|
|<span data-ttu-id="ad1c6-131">Безопасность</span><span class="sxs-lookup"><span data-stu-id="ad1c6-131">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="ad1c6-132">Нет</span><span class="sxs-lookup"><span data-stu-id="ad1c6-132">No</span></span>|
|<span data-ttu-id="ad1c6-133">Кодирование</span><span class="sxs-lookup"><span data-stu-id="ad1c6-133">Encoding</span></span>|<span data-ttu-id="ad1c6-134">Текст, двоичное, механизм оптимизации передачи сообщений (MTOM), пользовательское</span><span class="sxs-lookup"><span data-stu-id="ad1c6-134">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="ad1c6-135">Да</span><span class="sxs-lookup"><span data-stu-id="ad1c6-135">Yes</span></span>|
|<span data-ttu-id="ad1c6-136">Транспорт</span><span class="sxs-lookup"><span data-stu-id="ad1c6-136">Transport</span></span>|<span data-ttu-id="ad1c6-137">TCP, HTTP, HTTPS, именованные каналы (также называются IPC), одноранговый (P2P), очередь сообщений (также называется MSMQ), пользовательский</span><span class="sxs-lookup"><span data-stu-id="ad1c6-137">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="ad1c6-138">Да</span><span class="sxs-lookup"><span data-stu-id="ad1c6-138">Yes</span></span>|

<span data-ttu-id="ad1c6-139">Кроме того, можно определить собственные элементы привязки и вставить их между любыми из приведенных выше заданных уровней.</span><span class="sxs-lookup"><span data-stu-id="ad1c6-139">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad1c6-140">См. также</span><span class="sxs-lookup"><span data-stu-id="ad1c6-140">See also</span></span>

- [<span data-ttu-id="ad1c6-141">Общие сведения о создании конечных точек</span><span class="sxs-lookup"><span data-stu-id="ad1c6-141">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="ad1c6-142">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="ad1c6-142">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ad1c6-143">Привязки, предоставляемые системой</span><span class="sxs-lookup"><span data-stu-id="ad1c6-143">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="ad1c6-144">Практическое руководство. Изменение привязки, предоставляемой системой</span><span class="sxs-lookup"><span data-stu-id="ad1c6-144">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="ad1c6-145">Пользовательская привязка</span><span class="sxs-lookup"><span data-stu-id="ad1c6-145">Custom Binding</span></span>](../samples/custom-binding.md)
