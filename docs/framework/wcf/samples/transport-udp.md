---
description: 'Дополнительные сведения: Transport: UDP'
title: 'Транспорт: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: ab4afa8850f78258d2ef984a9b7be61e135cadca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685534"
---
# <a name="transport-udp"></a><span data-ttu-id="b589a-103">Транспорт: UDP</span><span class="sxs-lookup"><span data-stu-id="b589a-103">Transport: UDP</span></span>

<span data-ttu-id="b589a-104">В примере транспорта UDP демонстрируется реализация одноадресной и многоадресной рассылки по протоколу UDP в качестве настраиваемого транспорта Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b589a-104">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="b589a-105">В этом примере описывается рекомендуемая процедура создания пользовательского транспорта в WCF с помощью платформы Channel и следующих рекомендаций по WCF.</span><span class="sxs-lookup"><span data-stu-id="b589a-105">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="b589a-106">Для создания пользовательского транспорта выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b589a-106">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="b589a-107">Определите, какие из [шаблонов обмена сообщениями](#MessageExchangePatterns) каналов (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel или IReplyChannel) будут поддерживаться для ChannelFactory и ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="b589a-107">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="b589a-108">Затем решите, поддерживать ли связанные с сеансами разновидности указанных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="b589a-108">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="b589a-109">Создайте фабрику и прослушиватель каналов, которые поддерживают выбранный шаблон обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="b589a-109">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="b589a-110">Убедитесь, что все исключения, связанные с сетью, нормализованы в соответствующий класс, унаследованный от <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b589a-110">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="b589a-111">Добавьте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемент, который добавляет настраиваемый транспорт в стек каналов.</span><span class="sxs-lookup"><span data-stu-id="b589a-111">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="b589a-112">Дополнительные сведения см. [в разделе Добавление элемента привязки](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="b589a-112">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="b589a-113">Добавьте раздел расширения элементов привязки, чтобы представить новый элемент привязки системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b589a-113">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="b589a-114">Добавьте расширения метаданных, чтобы сообщить о возможностях в другие конечные точки.</span><span class="sxs-lookup"><span data-stu-id="b589a-114">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="b589a-115">Добавьте привязку, которая предварительно настраивает стек элементов привязки в соответствии с четко определенным профилем.</span><span class="sxs-lookup"><span data-stu-id="b589a-115">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="b589a-116">Дополнительные сведения см. [в разделе Добавление стандартной привязки](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="b589a-116">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="b589a-117">Добавьте раздел привязки и элемент конфигурации привязки, чтобы представить привязку системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b589a-117">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="b589a-118">Дополнительные сведения см. в разделе [Добавление поддержки конфигурации](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="b589a-118">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>

## <a name="message-exchange-patterns"></a><span data-ttu-id="b589a-119">Шаблоны обмена сообщениями</span><span class="sxs-lookup"><span data-stu-id="b589a-119">Message Exchange Patterns</span></span>  

 <span data-ttu-id="b589a-120">При создании пользовательского транспорта в первую очередь решите, какие шаблоны обмена сообщениями требуются для транспорта.</span><span class="sxs-lookup"><span data-stu-id="b589a-120">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="b589a-121">Можно выбирать из трех шаблонов обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="b589a-121">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="b589a-122">Датаграмма (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="b589a-122">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="b589a-123">При использовании шаблона обмена сообщениями "датаграмма" клиент отправляет сообщения, используя принцип "отправить и забыть".</span><span class="sxs-lookup"><span data-stu-id="b589a-123">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="b589a-124">В этом случае требуется внешнее подтверждение успешной доставки.</span><span class="sxs-lookup"><span data-stu-id="b589a-124">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="b589a-125">Сообщение может быть потеряно при передаче и может не достичь службы.</span><span class="sxs-lookup"><span data-stu-id="b589a-125">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="b589a-126">Если операция отправки успешно выполняется на стороне клиента, это не гарантирует, что удаленная конечная точка получит сообщение.</span><span class="sxs-lookup"><span data-stu-id="b589a-126">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="b589a-127">Датаграмма - фундаментальный элемент обмена сообщениями, на основе которого можно строить собственные протоколы, в том числе надежные и безопасные.</span><span class="sxs-lookup"><span data-stu-id="b589a-127">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="b589a-128">Каналы датаграмм клиентов реализуют интерфейс <xref:System.ServiceModel.Channels.IOutputChannel>, а каналы датаграмм служб - интерфейс <xref:System.ServiceModel.Channels.IInputChannel>.</span><span class="sxs-lookup"><span data-stu-id="b589a-128">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="b589a-129">Запрос-ответ (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="b589a-129">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="b589a-130">При использовании этого шаблона происходит отправка сообщения и получение ответа.</span><span class="sxs-lookup"><span data-stu-id="b589a-130">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="b589a-131">Шаблон состоит из пар «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="b589a-131">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="b589a-132">Примеры вызовов "запрос-ответ" - удаленные вызовы процедур и запросы GET браузера.</span><span class="sxs-lookup"><span data-stu-id="b589a-132">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="b589a-133">Этот шаблон также называют полудуплексным.</span><span class="sxs-lookup"><span data-stu-id="b589a-133">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="b589a-134">При использовании этого шаблона обмена сообщениями каналы клиентов реализуют интерфейс <xref:System.ServiceModel.Channels.IRequestChannel>, а каналы служб - интерфейс <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="b589a-134">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="b589a-135">Дуплекс (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="b589a-135">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="b589a-136">Дуплексный шаблон обмена сообщениями позволяет клиенту отправлять произвольное количество сообщений и принимать их в произвольном порядке.</span><span class="sxs-lookup"><span data-stu-id="b589a-136">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="b589a-137">Применение дуплексного шаблона похоже на разговор по телефону, когда каждое произносимое слово является сообщением.</span><span class="sxs-lookup"><span data-stu-id="b589a-137">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="b589a-138">Поскольку в данном случае принимать и отправлять сообщения могут обе стороны, каналы клиента и службы реализуют интерфейс <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="b589a-138">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="b589a-139">Каждый из этих шаблонов обмена сообщениями также поддерживает сеансы.</span><span class="sxs-lookup"><span data-stu-id="b589a-139">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="b589a-140">Канал, поддерживающий сеансы, содержит функции для согласования всех сообщений, отправляемых и принимаемых через канал.</span><span class="sxs-lookup"><span data-stu-id="b589a-140">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="b589a-141">Шаблон "запрос-ответ" является отдельным сеансом из двух сообщений, поскольку запрос и ответ связаны друг с другом.</span><span class="sxs-lookup"><span data-stu-id="b589a-141">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="b589a-142">В отличие от него в поддерживающем сеансы шаблоне "запрос-ответ" предполагается, что все пары "запрос-ответ" в канале связаны друг с другом.</span><span class="sxs-lookup"><span data-stu-id="b589a-142">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="b589a-143">Таким образом, можно выбирать один из шести шаблонов: датаграмма, "запрос-ответ", дуплекс, датаграмма с поддержкой сеансов, "запрос-ответ" с поддержкой сеансов и дуплекс с поддержкой сеансов.</span><span class="sxs-lookup"><span data-stu-id="b589a-143">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b589a-144">Для транспорта по протоколу UDP единственным поддерживаемым шаблоном обмена сообщениями является датаграмма, поскольку структура протокола UDP основана на принципе "отправить и забыть".</span><span class="sxs-lookup"><span data-stu-id="b589a-144">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="b589a-145">Жизненный цикл ICommunicationObject и объектов WCF</span><span class="sxs-lookup"><span data-stu-id="b589a-145">The ICommunicationObject and the WCF object lifecycle</span></span>  

 <span data-ttu-id="b589a-146">В WCF имеется общий конечный автомат, который используется для управления жизненным циклом объектов, таких как <xref:System.ServiceModel.Channels.IChannel> , <xref:System.ServiceModel.Channels.IChannelFactory> и <xref:System.ServiceModel.Channels.IChannelListener> , которые используются для обмена данными.</span><span class="sxs-lookup"><span data-stu-id="b589a-146">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="b589a-147">Эти объекты взаимодействий могут находиться в пяти состояниях.</span><span class="sxs-lookup"><span data-stu-id="b589a-147">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="b589a-148">Эти состояния, приведенные ниже, представлены перечислением <xref:System.ServiceModel.CommunicationState>.</span><span class="sxs-lookup"><span data-stu-id="b589a-148">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="b589a-149">Создано: это состояние <xref:System.ServiceModel.ICommunicationObject> при первом создании экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b589a-149">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="b589a-150">Ввод и вывод в этом состоянии не происходит.</span><span class="sxs-lookup"><span data-stu-id="b589a-150">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="b589a-151">Открытие: объекты переходят в это состояние при <xref:System.ServiceModel.ICommunicationObject.Open%2A> вызове.</span><span class="sxs-lookup"><span data-stu-id="b589a-151">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="b589a-152">В этот момент свойства перестают быть изменяемыми, и могут начинаться ввод и вывод.</span><span class="sxs-lookup"><span data-stu-id="b589a-152">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="b589a-153">Переход в это состояние возможен только из состояния Created.</span><span class="sxs-lookup"><span data-stu-id="b589a-153">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="b589a-154">Opened: в это состояние объекты переходят по окончании процесса открытия.</span><span class="sxs-lookup"><span data-stu-id="b589a-154">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="b589a-155">Переход в это состояние возможен только из состояния Opening.</span><span class="sxs-lookup"><span data-stu-id="b589a-155">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="b589a-156">С этого момента объект полностью пригоден для передачи сообщений.</span><span class="sxs-lookup"><span data-stu-id="b589a-156">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="b589a-157">Закрытие: объекты переходят в это состояние при <xref:System.ServiceModel.ICommunicationObject.Close%2A> вызове для корректного завершения работы.</span><span class="sxs-lookup"><span data-stu-id="b589a-157">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="b589a-158">Переход в это состояние возможен только из состояния Opened.</span><span class="sxs-lookup"><span data-stu-id="b589a-158">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="b589a-159">Closed: в состоянии Closed объекты использовать нельзя.</span><span class="sxs-lookup"><span data-stu-id="b589a-159">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="b589a-160">В общем случае большинство конфигураций доступны для изучения, но никакие взаимодействия происходить не могут.</span><span class="sxs-lookup"><span data-stu-id="b589a-160">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="b589a-161">Это состояние равнозначно удалению.</span><span class="sxs-lookup"><span data-stu-id="b589a-161">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="b589a-162">Faulted: в состоянии Faulted объекты доступны для изучения, но их нельзя использовать.</span><span class="sxs-lookup"><span data-stu-id="b589a-162">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="b589a-163">Объекты переходят в это состояние при возникновении неустранимой ошибки.</span><span class="sxs-lookup"><span data-stu-id="b589a-163">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="b589a-164">Единственным допустимым переходом из этого состояния является `Closed` состояние.</span><span class="sxs-lookup"><span data-stu-id="b589a-164">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="b589a-165">Есть события, возникающие при каждом изменении состояния.</span><span class="sxs-lookup"><span data-stu-id="b589a-165">There are events that fire for each state transition.</span></span> <span data-ttu-id="b589a-166"><xref:System.ServiceModel.ICommunicationObject.Abort%2A>Метод может быть вызван в любое время и приводит к тому, что объект переходит сразу из текущего состояния в состояние Closed.</span><span class="sxs-lookup"><span data-stu-id="b589a-166">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="b589a-167">Вызов <xref:System.ServiceModel.ICommunicationObject.Abort%2A> прекращает любую незаконченную работу.</span><span class="sxs-lookup"><span data-stu-id="b589a-167">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>

## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="b589a-168">Фабрика каналов и прослушиватель каналов</span><span class="sxs-lookup"><span data-stu-id="b589a-168">Channel Factory and Channel Listener</span></span>  

 <span data-ttu-id="b589a-169">Следующий этап создания пользовательского транспорта - реализация <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов и <xref:System.ServiceModel.Channels.IChannelListener> для каналов служб.</span><span class="sxs-lookup"><span data-stu-id="b589a-169">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="b589a-170">Уровень канала использует шаблон фабрики для создания каналов.</span><span class="sxs-lookup"><span data-stu-id="b589a-170">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="b589a-171">WCF предоставляет вспомогательные методы базового класса для этого процесса.</span><span class="sxs-lookup"><span data-stu-id="b589a-171">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="b589a-172">Класс <xref:System.ServiceModel.Channels.CommunicationObject> реализует интерфейс <xref:System.ServiceModel.ICommunicationObject> и принудительно создает конечный автомат, описанный ранее на шаге 2.</span><span class="sxs-lookup"><span data-stu-id="b589a-172">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="b589a-173"><xref:System.ServiceModel.Channels.ChannelManagerBase>Класс реализует <xref:System.ServiceModel.Channels.CommunicationObject> и предоставляет унифицированный базовый класс для <xref:System.ServiceModel.Channels.ChannelFactoryBase> и <xref:System.ServiceModel.Channels.ChannelListenerBase> .</span><span class="sxs-lookup"><span data-stu-id="b589a-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="b589a-174">Класс <xref:System.ServiceModel.Channels.ChannelManagerBase> работает совместно с классом <xref:System.ServiceModel.Channels.ChannelBase> - базовым классом, реализующим интерфейс <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="b589a-174">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="b589a-175"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Класс реализует <xref:System.ServiceModel.Channels.ChannelManagerBase> и <xref:System.ServiceModel.Channels.IChannelFactory> объединяет `CreateChannel` перегрузки в один `OnCreateChannel` абстрактный метод.</span><span class="sxs-lookup"><span data-stu-id="b589a-175">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="b589a-176"><xref:System.ServiceModel.Channels.ChannelListenerBase>Класс реализует <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="b589a-176">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="b589a-177">Он отвечает за базовое управление состоянием.</span><span class="sxs-lookup"><span data-stu-id="b589a-177">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="b589a-178">В этом образце реализация фабрики содержится в UdpChannelFactory.cs, а реализация прослушивателя содержится в UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="b589a-178">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="b589a-179">Реализации <xref:System.ServiceModel.Channels.IChannel> находятся в UdpOutputChannel.cs и UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="b589a-179">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="b589a-180">Фабрика канала UDP</span><span class="sxs-lookup"><span data-stu-id="b589a-180">The UDP Channel Factory</span></span>  

 <span data-ttu-id="b589a-181">Фабрика`UdpChannelFactory` наследуется от класса <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="b589a-181">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="b589a-182">В образце переопределяется метод <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> для обеспечения доступа к версии сообщения кодировщика сообщений.</span><span class="sxs-lookup"><span data-stu-id="b589a-182">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="b589a-183">Также переопределяется метод <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A>, позволяющий убрать созданный экземпляр класса <xref:System.ServiceModel.Channels.BufferManager> при переходе конечного автомата в другое состояние.</span><span class="sxs-lookup"><span data-stu-id="b589a-183">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="b589a-184">Выходной канал UDP</span><span class="sxs-lookup"><span data-stu-id="b589a-184">The UDP Output Channel</span></span>  

 <span data-ttu-id="b589a-185">Класс`UdpOutputChannel` реализует интерфейс <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="b589a-185">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="b589a-186">Конструктор проверяет аргументы и создает целевой объект <xref:System.Net.EndPoint> на основании переданного ему адреса <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="b589a-186">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="b589a-187">Канал может быть закрыт правильно или неправильно.</span><span class="sxs-lookup"><span data-stu-id="b589a-187">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="b589a-188">При верном закрытии канала сокет закрывается и вызывается метод `OnClose` базового класса.</span><span class="sxs-lookup"><span data-stu-id="b589a-188">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="b589a-189">Если при этом создается исключение, инфраструктура вызывает метод `Abort`, чтоб обеспечить очистку канала.</span><span class="sxs-lookup"><span data-stu-id="b589a-189">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="b589a-190">Затем мы реализуем `Send()` и `BeginSend()` / `EndSend()` .</span><span class="sxs-lookup"><span data-stu-id="b589a-190">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="b589a-191">Реализация делится на две принципиальные части.</span><span class="sxs-lookup"><span data-stu-id="b589a-191">This breaks down into two main sections.</span></span> <span data-ttu-id="b589a-192">Сначала сообщение сериализуется в байтовый массив.</span><span class="sxs-lookup"><span data-stu-id="b589a-192">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="b589a-193">Затем получившиеся данные отправляются по сети.</span><span class="sxs-lookup"><span data-stu-id="b589a-193">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="b589a-194">Класс UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="b589a-194">The UdpChannelListener</span></span>  

 <span data-ttu-id="b589a-195">Объект `UdpChannelListener` , который реализуется в примере, является производным от <xref:System.ServiceModel.Channels.ChannelListenerBase> класса.</span><span class="sxs-lookup"><span data-stu-id="b589a-195">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="b589a-196">Он использует один UDP-сокет для приема датаграмм.</span><span class="sxs-lookup"><span data-stu-id="b589a-196">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="b589a-197">Метод `OnOpen` принимает данные через UDP-сокет в асинхронном цикле.</span><span class="sxs-lookup"><span data-stu-id="b589a-197">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="b589a-198">Затем данные преобразуются в сообщения с помощью системы кодирования сообщений.</span><span class="sxs-lookup"><span data-stu-id="b589a-198">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="b589a-199">Поскольку один канал датаграмм представляет сообщения, приходящие из нескольких источников, `UdpChannelListener` - одноэлементный прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="b589a-199">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="b589a-200">Существует, по крайней мере, одна активная, <xref:System.ServiceModel.Channels.IChannel> связанная с этим прослушивателем за раз.</span><span class="sxs-lookup"><span data-stu-id="b589a-200">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="b589a-201">В образце создается новый экземпляр только в том случае, если канал, возвращенный методом `AcceptChannel`, был впоследствии освобожден.</span><span class="sxs-lookup"><span data-stu-id="b589a-201">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="b589a-202">Когда сообщение принято, оно ставится в очередь в этот одноэлементный канал.</span><span class="sxs-lookup"><span data-stu-id="b589a-202">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="b589a-203">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="b589a-203">UdpInputChannel</span></span>  

 <span data-ttu-id="b589a-204">`UdpInputChannel`Класс реализует `IInputChannel` .</span><span class="sxs-lookup"><span data-stu-id="b589a-204">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="b589a-205">Он состоит из очереди входящих сообщений, которая заполняется сокетом прослушивателя `UdpChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="b589a-205">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="b589a-206">Эти сообщения выводятся из очереди `IInputChannel.Receive` методом.</span><span class="sxs-lookup"><span data-stu-id="b589a-206">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>

## <a name="adding-a-binding-element"></a><span data-ttu-id="b589a-207">Добавление элемента привязки</span><span class="sxs-lookup"><span data-stu-id="b589a-207">Adding a Binding Element</span></span>  

 <span data-ttu-id="b589a-208">После создания фабрики и каналы нужно предоставить среде выполнения ServiceModel через привязку.</span><span class="sxs-lookup"><span data-stu-id="b589a-208">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="b589a-209">Привязка - это коллекция элементов привязки, представляющая стек связи для адреса службы.</span><span class="sxs-lookup"><span data-stu-id="b589a-209">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="b589a-210">Каждый элемент в стеке представлен [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элементом.</span><span class="sxs-lookup"><span data-stu-id="b589a-210">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="b589a-211">В этом примере в качестве элемента привязки выступает элемент `UdpTransportBindingElement`, являющийся производным элемента <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b589a-211">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="b589a-212">Он переопределяет следующие методы создания фабрик, связанных с привязкой.</span><span class="sxs-lookup"><span data-stu-id="b589a-212">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="b589a-213">Он также содержит члены для клонирования элемента `BindingElement` и возврата схемы (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="b589a-213">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="b589a-214">Добавление поддержки метаданных для элемента привязки транспорта</span><span class="sxs-lookup"><span data-stu-id="b589a-214">Adding Metadata Support for a Transport Binding Element</span></span>  

 <span data-ttu-id="b589a-215">Для интеграции в систему метаданных транспорт должен поддерживать как импорт, так и экспорт политики.</span><span class="sxs-lookup"><span data-stu-id="b589a-215">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="b589a-216">Это позволяет нам создавать клиенты привязок с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b589a-216">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="b589a-217">Добавление поддержки WSDL</span><span class="sxs-lookup"><span data-stu-id="b589a-217">Adding WSDL Support</span></span>  

 <span data-ttu-id="b589a-218">За экспорт и импорт адресов в метаданных отвечает элемент привязки транспорта.</span><span class="sxs-lookup"><span data-stu-id="b589a-218">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="b589a-219">При использовании привязки протокола SOAP элемент привязки транспорта должен также экспортировать в метаданных правильный URI (универсальный код ресурса) транспорта.</span><span class="sxs-lookup"><span data-stu-id="b589a-219">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="b589a-220">Экспорт WSDL</span><span class="sxs-lookup"><span data-stu-id="b589a-220">WSDL Export</span></span>  

 <span data-ttu-id="b589a-221">Для экспорта адресов элемент `UdpTransportBindingElement` реализует интерфейс `IWsdlExportExtension`.</span><span class="sxs-lookup"><span data-stu-id="b589a-221">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="b589a-222">`ExportEndpoint`Метод добавляет правильные сведения об адресации в порт WSDL.</span><span class="sxs-lookup"><span data-stu-id="b589a-222">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="b589a-223">Реализация метода `UdpTransportBindingElement` в элементе `ExportEndpoint` также экспортирует URI транспорта, когда конечная точка использует привязку SOAP.</span><span class="sxs-lookup"><span data-stu-id="b589a-223">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="b589a-224">Импорт WSDL</span><span class="sxs-lookup"><span data-stu-id="b589a-224">WSDL Import</span></span>  

 <span data-ttu-id="b589a-225">Для расширения системы импорта WSDL для обработки импорта адресов нужно добавить в файл конфигурации средства Svcutil.exe следующую конфигурацию, как показано в файле Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b589a-225">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b589a-226">При запуске Svcutil.exe существует два варианта обеспечить загрузку программой расширений импорта WSDL:</span><span class="sxs-lookup"><span data-stu-id="b589a-226">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="b589a-227">Укажите Svcutil.exe к файлу конфигурации с помощью/Свкутилконфиг: \<file> .</span><span class="sxs-lookup"><span data-stu-id="b589a-227">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b589a-228">добавить раздел конфигурации в файл Svcutil.exe.config, находящийся в том же каталоге, что и файл Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b589a-228">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="b589a-229">`UdpBindingElementImporter`Тип реализует `IWsdlImportExtension` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b589a-229">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="b589a-230">Метод `ImportEndpoint` импортирует адрес из порта WSDL.</span><span class="sxs-lookup"><span data-stu-id="b589a-230">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="b589a-231">Добавление поддержки политик</span><span class="sxs-lookup"><span data-stu-id="b589a-231">Adding Policy Support</span></span>  

 <span data-ttu-id="b589a-232">Пользовательский элемент привязки может экспортировать утверждения политики в привязке WSDL для конечной точки службы, чтобы показать возможности этого элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-232">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="b589a-233">Экспорт политики</span><span class="sxs-lookup"><span data-stu-id="b589a-233">Policy Export</span></span>  

 <span data-ttu-id="b589a-234">`UdpTransportBindingElement`Тип реализует, `IPolicyExportExtension` чтобы добавить поддержку для политики экспорта.</span><span class="sxs-lookup"><span data-stu-id="b589a-234">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="b589a-235">В результате класс `System.ServiceModel.MetadataExporter` включает элемент `UdpTransportBindingElement` при формировании политики для любой привязки, в которую он входит.</span><span class="sxs-lookup"><span data-stu-id="b589a-235">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="b589a-236">В методе `IPolicyExportExtension.ExportPolicy` добавляется утверждение для UDP и еще одно утверждение, если используется режим многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="b589a-236">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="b589a-237">Это связано с тем, что режим многоадресной рассылки влияет на построение стека связи и, следовательно, должен быть согласован обеими сторонами.</span><span class="sxs-lookup"><span data-stu-id="b589a-237">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="b589a-238">Поскольку пользовательские элементы привязки транспорта отвечают за обработку адресов, реализация `IPolicyExportExtension` в элементе `UdpTransportBindingElement` должна также обрабатывать экспорт соответствующих утверждений политики WS-Addressing для указания используемой версии WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b589a-238">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="b589a-239">Импорт политики</span><span class="sxs-lookup"><span data-stu-id="b589a-239">Policy Import</span></span>  

 <span data-ttu-id="b589a-240">Чтобы расширить систему импорта политик, нужно добавить в файл конфигурации Svcutil.exe следующую конфигурацию, как показано в файле Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b589a-240">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b589a-241">Затем мы реализуем интерфейс `IPolicyImporterExtension` из зарегистрированного нами класса (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="b589a-241">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="b589a-242">В методе `ImportPolicy()` нужно рассмотреть утверждения в нашем пространстве имен и обработать предназначенные для формирования транспорта и проверки, является ли он многоадресным.</span><span class="sxs-lookup"><span data-stu-id="b589a-242">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="b589a-243">Кроме того, нужно удалить обрабатываемые утверждения из списка утверждений привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-243">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="b589a-244">И опять при запуске Svcutil.exe существует два варианта интеграции:</span><span class="sxs-lookup"><span data-stu-id="b589a-244">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="b589a-245">Укажите Svcutil.exe к файлу конфигурации с помощью/Свкутилконфиг: \<file> .</span><span class="sxs-lookup"><span data-stu-id="b589a-245">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b589a-246">добавить раздел конфигурации в файл Svcutil.exe.config, находящийся в том же каталоге, что и файл Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b589a-246">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>

## <a name="adding-a-standard-binding"></a><span data-ttu-id="b589a-247">Добавление стандартной привязки</span><span class="sxs-lookup"><span data-stu-id="b589a-247">Adding a Standard Binding</span></span>  

 <span data-ttu-id="b589a-248">Элемент привязки можно использовать двумя следующими способами.</span><span class="sxs-lookup"><span data-stu-id="b589a-248">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="b589a-249">С помощью пользовательской привязки: пользовательская привязка позволяет пользователю создать собственную привязку на основе произвольного набора элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-249">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="b589a-250">С помощью предусмотренной в составе системы привязки, включающей наш элемент привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-250">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="b589a-251">WCF предоставляет ряд этих определяемых системой привязок, таких как `BasicHttpBinding` , `NetTcpBinding` и `WsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="b589a-251">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="b589a-252">Каждая из них связана с четко определенным профилем.</span><span class="sxs-lookup"><span data-stu-id="b589a-252">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="b589a-253">В этом образце реализуется профиль привязки в `SampleProfileUdpBinding`, производном от <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b589a-253">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b589a-254">Привязка `SampleProfileUdpBinding` содержит до четырех элементов привязки: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement` и `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b589a-254">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="b589a-255">Добавление пользовательского импортера стандартной привязки</span><span class="sxs-lookup"><span data-stu-id="b589a-255">Adding a Custom Standard Binding Importer</span></span>  

 <span data-ttu-id="b589a-256">Svcutil.exe и тип `WsdlImporter` по умолчанию распознают и импортируют определенные системой привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-256">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="b589a-257">В противном случае привязка импортируется как экземпляр `CustomBinding`.</span><span class="sxs-lookup"><span data-stu-id="b589a-257">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="b589a-258">Чтобы Svcutil.exe и тип `WsdlImporter` могли импортировать привязку `SampleProfileUdpBinding`, тип `UdpBindingElementImporter` также выступает в качестве пользовательского импортера стандартной привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-258">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="b589a-259">Пользовательский импортер стандартной привязки реализует метод `ImportEndpoint` в интерфейсе `IWsdlImportExtension`, чтобы проверить импортированный из метаданных экземпляр класса `CustomBinding` и определить, мог ли он быть сформирован определенной стандартной привязкой.</span><span class="sxs-lookup"><span data-stu-id="b589a-259">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b589a-260">Как правило, реализация пользовательского импортера стандартной привязки предусматривает проверку свойств импортированных элементов привязки на предмет того, что изменены только свойства, которые могли быть заданы стандартной привязкой, а все остальные свойства имеют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b589a-260">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="b589a-261">Простейшая стратегия для реализации импортера стандартной привязки - создать экземпляр стандартной привязки, распространить на экземпляр стандартной привязки свойства из элементов привязки, поддерживаемые стандартной привязкой, и затем сравнить элементы привязки из стандартной привязки с импортированными элементами привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-261">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>

## <a name="adding-configuration-support"></a><span data-ttu-id="b589a-262">Добавление поддержки конфигурации</span><span class="sxs-lookup"><span data-stu-id="b589a-262">Adding Configuration Support</span></span>  

 <span data-ttu-id="b589a-263">Для предоставления транспорта через конфигурацию нужно реализовать два раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b589a-263">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="b589a-264">Первый - элемент `BindingElementExtensionElement` для `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b589a-264">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="b589a-265">За счет этого реализации `CustomBinding` могут ссылаться на наш элемент привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-265">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="b589a-266">Второй - `Configuration` для `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b589a-266">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="b589a-267">Элемент привязки элемента Extension</span><span class="sxs-lookup"><span data-stu-id="b589a-267">Binding Element Extension Element</span></span>  

 <span data-ttu-id="b589a-268">Раздел `UdpTransportElement` представляет собой `BindingElementExtensionElement` , который предоставляет `UdpTransportBindingElement` системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b589a-268">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="b589a-269">С помощью нескольких простых переопределений в примере определяется имя раздела конфигурации, тип элемента привязки и способ создания элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="b589a-269">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="b589a-270">Затем можно зарегистрировать раздел расширения в файле конфигурации, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="b589a-270">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b589a-271">На расширение можно ссылаться из пользовательских привязок, чтобы использовать в качестве транспорта протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="b589a-271">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="b589a-272">Раздел привязки</span><span class="sxs-lookup"><span data-stu-id="b589a-272">Binding Section</span></span>  

 <span data-ttu-id="b589a-273">Раздел `SampleProfileUdpBindingCollectionElement` представляет собой `StandardBindingCollectionElement` , который предоставляет `SampleProfileUdpBinding` системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b589a-273">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="b589a-274">Основная часть реализации делегируется классу `SampleProfileUdpBindingConfigurationElement`, наследуемому от класса `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b589a-274">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="b589a-275">`SampleProfileUdpBindingConfigurationElement`Имеет свойства, соответствующие свойствам `SampleProfileUdpBinding` , и функциям, которые сопоставляются с `ConfigurationElement` привязкой.</span><span class="sxs-lookup"><span data-stu-id="b589a-275">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="b589a-276">Наконец, метод `OnApplyConfiguration` в классе `SampleProfileUdpBinding` переопределяется, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="b589a-276">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="b589a-277">Для регистрации этого обработчика в системе конфигурации в соответствующий файл конфигурации добавляется следующий раздел.</span><span class="sxs-lookup"><span data-stu-id="b589a-277">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="b589a-278">После этого на него можно сослаться из раздела конфигурации serviceModel.</span><span class="sxs-lookup"><span data-stu-id="b589a-278">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="b589a-279">Тестовые служба и клиент UDP</span><span class="sxs-lookup"><span data-stu-id="b589a-279">The UDP Test Service and Client</span></span>  

 <span data-ttu-id="b589a-280">Тестовый код для использования этого примера транспорта находится в каталогах UdpTestService и UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="b589a-280">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="b589a-281">Код службы состоит из двух тестов. Один из них настраивает привязки и конечные точки из кода, а другой - через конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="b589a-281">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="b589a-282">Оба теста используют две конечных точки.</span><span class="sxs-lookup"><span data-stu-id="b589a-282">Both tests use two endpoints.</span></span> <span data-ttu-id="b589a-283">Одна конечная точка использует `SampleUdpProfileBinding` параметр WITH со [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) значением `true` .</span><span class="sxs-lookup"><span data-stu-id="b589a-283">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="b589a-284">Другая конечная точка использует пользовательскую привязку с классом `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b589a-284">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="b589a-285">Это эквивалентно использованию `SampleUdpProfileBinding` параметра WITH с [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) параметром `false` .</span><span class="sxs-lookup"><span data-stu-id="b589a-285">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="b589a-286">Оба теста создают службу, добавляют для каждой привязки конечную точку, открывают службу и ожидают нажатия пользователем клавиши ВВОД перед тем, как закрыть службу.</span><span class="sxs-lookup"><span data-stu-id="b589a-286">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="b589a-287">При запуске приложения тестирования службы появится результат следующего вида.</span><span class="sxs-lookup"><span data-stu-id="b589a-287">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="b589a-288">Затем можно выполнить приложение тестирования клиента относительно опубликованных конечных точек.</span><span class="sxs-lookup"><span data-stu-id="b589a-288">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="b589a-289">Приложение тестирования клиента создает клиент для каждой конечной точки и отправляет им по пять сообщений.</span><span class="sxs-lookup"><span data-stu-id="b589a-289">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="b589a-290">Клиент получает следующий результат.</span><span class="sxs-lookup"><span data-stu-id="b589a-290">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="b589a-291">Полные результаты службы таковы.</span><span class="sxs-lookup"><span data-stu-id="b589a-291">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="b589a-292">Для выполнения клиентского приложения относительно конечных точек, опубликованных с помощью конфигурации, нажмите в службе клавишу ВВОД и снова запустите тестовый клиент.</span><span class="sxs-lookup"><span data-stu-id="b589a-292">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="b589a-293">Служба должна предоставить следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="b589a-293">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="b589a-294">Повторное выполнение клиента дает такие же результаты.</span><span class="sxs-lookup"><span data-stu-id="b589a-294">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="b589a-295">Для восстановления кода клиента и конфигурации с помощью Svcutil.exe запустите приложение службы и выполните следующий файл Svcutil.exe из корневого каталога образца.</span><span class="sxs-lookup"><span data-stu-id="b589a-295">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="b589a-296">Обратите внимание, что Svcutil.exe не создает конфигурацию расширения привязки для `SampleProfileUdpBinding`, поэтому ее нужно добавить вручную.</span><span class="sxs-lookup"><span data-stu-id="b589a-296">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b589a-297">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="b589a-297">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b589a-298">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b589a-298">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="b589a-299">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b589a-299">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b589a-300">См. раздел "Тестовые служба и клиент UDP" выше.</span><span class="sxs-lookup"><span data-stu-id="b589a-300">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b589a-301">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="b589a-301">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b589a-302">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="b589a-302">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b589a-303">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="b589a-303">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b589a-304">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="b589a-304">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
