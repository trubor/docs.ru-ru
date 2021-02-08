---
description: 'Дополнительные сведения о: канал фрагментирования'
title: Фрагментирование канала
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 826db33186aa8e01ade9123d6b0d8b696b7e77ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778780"
---
# <a name="chunking-channel"></a><span data-ttu-id="2fa0e-103">Фрагментирование канала</span><span class="sxs-lookup"><span data-stu-id="2fa0e-103">Chunking Channel</span></span>

<span data-ttu-id="2fa0e-104">При отправке больших сообщений с помощью Windows Communication Foundation (WCF) часто желательно ограничить объем памяти, используемой для буферизации этих сообщений.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-104">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="2fa0e-105">Одним из возможных решений является потоковая передача тела сообщения (предполагая, что основной объем данных содержится в теле сообщения).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-105">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="2fa0e-106">Однако для некоторых протоколов требуется буферизация всего сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-106">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="2fa0e-107">Например, при надежном обмене сообщениями и необходимости обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-107">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="2fa0e-108">Другим возможным решением является разделение большого сообщения на маленькие, называемые фрагментами, и отправка этих фрагментов поочередно с последующим восстановлением большого сообщения на получающей стороне.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-108">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="2fa0e-109">Приложение может выполнить фрагментацию и дефрагментацию самостоятельно или воспользоваться пользовательским каналом.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-109">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="2fa0e-110">В примере канала фрагментации показано, как можно использовать пользовательский протокол или многоуровневый канал для фрагментации и дефрагментации сообщений произвольного большого размера.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-110">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="2fa0e-111">Фрагментация всегда должна применяться только после полного создания сообщения для отправки.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-111">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="2fa0e-112">Канал фрагментации всегда должен располагаться под каналом безопасности и каналом надежного сеанса.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-112">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="2fa0e-113">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fa0e-114">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fa0e-115">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2fa0e-116">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fa0e-117">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="2fa0e-118">Канал фрагментации: допущения и ограничения</span><span class="sxs-lookup"><span data-stu-id="2fa0e-118">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="2fa0e-119">Структура сообщения</span><span class="sxs-lookup"><span data-stu-id="2fa0e-119">Message Structure</span></span>

<span data-ttu-id="2fa0e-120">Предполагается, что фрагментируемые сообщения, передаваемые в канал фрагментации, имеют следующую структуру.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-120">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

<span data-ttu-id="2fa0e-121">При использовании пространства имен ServiceModel входные сообщения операций контракта, в которых используется один входной параметр, соответствуют этой форме сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-121">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="2fa0e-122">Аналогичным образом, выходные сообщения операций контракта, в которых имеется один выходной параметр или одно возвращаемое значение, соответствуют этой форме сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-122">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="2fa0e-123">Ниже приводятся примеры таких операций.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-123">The following are examples of such operations:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    Stream EchoStream(Stream stream);

    [OperationContract]
    Stream DownloadStream();

    [OperationContract(IsOneWay = true)]
    void UploadStream(Stream stream);
}
```

### <a name="sessions"></a><span data-ttu-id="2fa0e-124">Сеансы</span><span class="sxs-lookup"><span data-stu-id="2fa0e-124">Sessions</span></span>

<span data-ttu-id="2fa0e-125">Требуется, чтобы сообщения доставлялись в канал фрагментации ровно один раз в порядке доставки сообщений (фрагментов).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-125">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="2fa0e-126">Это означает, что базовый стек канала должен быть сеансовым.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-126">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="2fa0e-127">Сеансы могу предоставляться транспортом (например, транспортом TCP) или сеансовым каналом протокола (например, каналом ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-127">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="2fa0e-128">Асинхронные отправка и получение</span><span class="sxs-lookup"><span data-stu-id="2fa0e-128">Asynchronous Send and Receive</span></span>

<span data-ttu-id="2fa0e-129">Методы асинхронной отправки и получения не реализуются в этой версии образца канала фрагментации.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-129">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="2fa0e-130">Протокол фрагментации</span><span class="sxs-lookup"><span data-stu-id="2fa0e-130">Chunking Protocol</span></span>

<span data-ttu-id="2fa0e-131">Канал фрагментации определяет протокол, указывающий начало и конец последовательностей фрагментов, а также порядковый номер каждого фрагмента.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-131">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="2fa0e-132">В следующих трех примерах сообщений показаны исходное сообщение, фрагментированное сообщение и конечное сообщение с комментариями, описывающими основные аспекты.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-132">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="2fa0e-133">Исходное сообщение</span><span class="sxs-lookup"><span data-stu-id="2fa0e-133">Start Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>
<!--
Original message is assigned a unique id that is transmitted
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.
-->
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">
53f183ee-04aa-44a0-b8d3-e45224563109
</MessageId>
<!--
ChunkingStart header signals the start of a chunked message.
-->
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />
<!--
Original message action is transmitted in OriginalAction.
This is required to re-create the original message on the other side.
-->
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">
http://tempuri.org/ITestService/EchoStream
    </OriginalAction>
   <!--
    All original message headers are included here.
   -->
  </s:Header>
  <s:Body>
<!--
Chunking assumes this structure of Body content:
<element>
  <childelement>large data to be chunked<childelement>
</element>
The start message contains just <element> and <childelement> without
the data to be chunked.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

### <a name="chunk-message"></a><span data-ttu-id="2fa0e-134">Фрагментированное сообщение</span><span class="sxs-lookup"><span data-stu-id="2fa0e-134">Chunk Message</span></span>

```xml
<s:Envelope
  xmlns:a="http://www.w3.org/2005/08/addressing"
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
   <!--
    All chunking protocol messages have this action.
   -->
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
The sequence number of the chunk.
This number restarts at 1 with each new sequence of chunks.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      1096
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The chunked data is wrapped in a chunk element.
The encoding of this data (and the entire message)
depends on the encoder used. The chunking channel does not mandate an encoding.
-->
    <chunk xmlns="http://samples.microsoft.com/chunking">
kfSr2QcBlkHTvQ==
    </chunk>
  </s:Body>
</s:Envelope>
```

### <a name="end-message"></a><span data-ttu-id="2fa0e-135">Конечное сообщение</span><span class="sxs-lookup"><span data-stu-id="2fa0e-135">End Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
ChunkingEnd header signals the end of a chunk sequence.
-->
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"
                 xmlns="http://samples.microsoft.com/chunking" />
<!--
ChunkingEnd messages have a sequence number.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      79
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The ChunkingEnd message has the same <element><childelement> structure
as the ChunkingStart message.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

## <a name="chunking-channel-architecture"></a><span data-ttu-id="2fa0e-136">Архитектура канала фрагментации</span><span class="sxs-lookup"><span data-stu-id="2fa0e-136">Chunking Channel Architecture</span></span>

<span data-ttu-id="2fa0e-137">Канал фрагментации является каналом `IDuplexSessionChannel`, следующим стандартной архитектуре каналов на высоком уровне.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-137">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="2fa0e-138">`ChunkingBindingElement` может выполнить построение `ChunkingChannelFactory` и `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-138">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="2fa0e-139">`ChunkingChannelFactory` создает экземпляры `ChunkingChannel` при соответствующем запросе.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-139">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="2fa0e-140">`ChunkingChannelListener` создает экземпляры `ChunkingChannel`, когда принимается новый внутренний канал.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-140">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="2fa0e-141">`ChunkingChannel` отвечает за отправку и получение сообщений.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-141">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="2fa0e-142">На следующем более низком уровне `ChunkingChannel` основывается на нескольких компонентах для реализации протокола фрагментации.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-142">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="2fa0e-143">На отправляющей стороне канал использует пользовательский <xref:System.Xml.XmlDictionaryWriter>, называемый `ChunkingWriter`, который непосредственно выполняет фрагментацию.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-143">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="2fa0e-144">`ChunkingWriter` непосредственно использует внутренний канал для отправки фрагментов данных.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-144">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="2fa0e-145">Использование пользовательского средства записи `XmlDictionaryWriter` позволяет отправлять фрагменты одновременно с записью большого тела исходного сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-145">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="2fa0e-146">Это означает, что все исходное сообщение не буферизуется.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-146">This means we do not buffer the entire original message.</span></span>

![Схема, на которой показана архитектура отправки канала фрагментации.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="2fa0e-148">На получающей стороне `ChunkingChannel` извлекает сообщения из внутреннего канала и передает их в пользовательский <xref:System.Xml.XmlDictionaryReader>, называемый `ChunkingReader`, который восстанавливает исходное сообщение из входящих фрагментов данных.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-148">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="2fa0e-149">`ChunkingChannel` выступает в роли оболочки `ChunkingReader` в пользовательской реализации `Message`, называемой `ChunkingMessage`, и возвращает это сообщение на уровень выше.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-149">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="2fa0e-150">Данное сочетание `ChunkingReader` и `ChunkingMessage` позволяет дефрагментировать текст исходного сообщения в процессе его считывания вышележащим уровнем вместо необходимости помещения в буфер всего текста исходного сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-150">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="2fa0e-151">`ChunkingReader` имеет очередь, в которой буферизуются входящие фрагменты данных, пока их количество не достигнет заданного.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-151">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="2fa0e-152">При достижении максимального количества средство чтения ожидает, пока сообщения не будут извлечены из очереди вышестоящим уровнем (то есть прочитаны из тела исходного сообщения) или пока не истечет время ожидания получения максимального количества сообщений.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-152">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Схема, на которой показана архитектура получения канала фрагментации.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="2fa0e-154">Модель программирования фрагментации</span><span class="sxs-lookup"><span data-stu-id="2fa0e-154">Chunking Programming Model</span></span>

<span data-ttu-id="2fa0e-155">Разработчики службы могут указать, какие сообщения фрагментируются с применением атрибута `ChunkingBehavior` к операциям в контракте.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-155">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="2fa0e-156">Атрибут предоставляет свойство `AppliesTo`, позволяющее разработчику указать, применяется ли фрагментация к входящему или исходящему сообщению или к обоим сообщениям.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-156">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="2fa0e-157">В следующем примере показано применение атрибута `ChunkingBehavior`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-157">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.Both)]
    Stream EchoStream(Stream stream);

    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]
    Stream DownloadStream();

    [OperationContract(IsOneWay=true)]
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]
    void UploadStream(Stream stream);

}
```

<span data-ttu-id="2fa0e-158">В этой модели программирования `ChunkingBindingElement` компилирует список универсальных кодов ресурса (URI) действия, в котором определяются фрагментируемые сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-158">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="2fa0e-159">Действие каждого исходящего сообщения сопоставляется с этим списком для определения, фрагментируется ли сообщение или отправляется непосредственно.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-159">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="2fa0e-160">Реализация операции отправки</span><span class="sxs-lookup"><span data-stu-id="2fa0e-160">Implementing the Send Operation</span></span>

<span data-ttu-id="2fa0e-161">На высоком уровне операция отправки вначале проверяет, следует ли фрагментировать исходящее сообщение, и, если фрагментация не требуется, отправляет сообщение непосредственно по внутреннему каналу.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-161">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="2fa0e-162">Если сообщение должно быть фрагментировано, операция отправки создает новое средство записи `ChunkingWriter` и вызывает `WriteBodyContents` для исходящего сообщения, передавая его в `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-162">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="2fa0e-163">Затем `ChunkingWriter` выполняет фрагментацию сообщения (с копированием заголовков исходного сообщения в начальный фрагмент сообщения) и отправляет фрагменты по внутреннему каналу.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-163">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="2fa0e-164">Следует отметить следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-164">A few details worth noting:</span></span>

- <span data-ttu-id="2fa0e-165">Операция отправки сначала вызывает `ThrowIfDisposedOrNotOpened`, чтобы убедиться в том, что `CommunicationState` - открыто.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-165">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="2fa0e-166">Операция отправки синхронизируется таким образом, что во время каждого сеанса может быть отправлено только одно сообщение.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-166">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="2fa0e-167">Существует событие `ManualResetEvent` с именем `sendingDone`, которое сбрасывается при отправке фрагментированного сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-167">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="2fa0e-168">Это событие задается при отправке последнего фрагмента сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-168">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="2fa0e-169">Перед отправкой исходящего сообщения метод отправки ожидает задания этого события.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-169">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="2fa0e-170">Метод отправки блокирует `CommunicationObject.ThisLock` для предотвращения изменения состояния синхронизации при отправке.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-170">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="2fa0e-171">См. документацию по <xref:System.ServiceModel.Channels.CommunicationObject> для получения дополнительной информации о конечных автоматах и состояниях <xref:System.ServiceModel.Channels.CommunicationObject>.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-171">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="2fa0e-172">Время ожидания, передаваемое в метод отправки, используется как время ожидания выполнения всей операции отправки, то есть отправки всех фрагментов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-172">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="2fa0e-173">Пользовательская разработка <xref:System.Xml.XmlDictionaryWriter> выбрана с целью избежать буферизации всего тела исходного сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-173">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="2fa0e-174">При необходимости применить <xref:System.Xml.XmlDictionaryReader> к телу сообщения, используя `message.GetReaderAtBodyContents`, была бы выполнена буферизация всего тела сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-174">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="2fa0e-175">Вместо этого у нас есть пользовательский объект  <xref:System.Xml.XmlDictionaryWriter> , который передается в `message.WriteBodyContents` .</span><span class="sxs-lookup"><span data-stu-id="2fa0e-175">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="2fa0e-176">Так как сообщение вызывает WriteBase64 для средства записи, средство записи упаковывает фрагменты в сообщения и отправляет их по внутреннему каналу.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-176">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="2fa0e-177">WriteBase64 выполняет блокировку пока фрагмент не будет отправлен.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-177">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="2fa0e-178">Реализация операции получения</span><span class="sxs-lookup"><span data-stu-id="2fa0e-178">Implementing the Receive Operation</span></span>

<span data-ttu-id="2fa0e-179">На высоком уровне операция получения сперва проверяет, что входящее сообщение не является `null` и его действием является `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-179">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="2fa0e-180">Если сообщение не соответствует обоим указанным критериям, оно возвращается из операции получения без изменений.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-180">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="2fa0e-181">В противном случае операция получения создает новое средство чтения `ChunkingReader` и новое `ChunkingMessage`, для которого оно является оболочкой (вызывая `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-181">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="2fa0e-182">Перед возвратом нового `ChunkingMessage`, операция получения использует поток из пула потоков для выполнения операции `ReceiveChunkLoop`, которая вызывает в цикле метод `innerChannel.Receive` и передает фрагменты в `ChunkingReader`, пока не будет получен последний фрагмент сообщения или не истечет время ожидания выполнения операции получения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-182">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="2fa0e-183">Следует отметить следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-183">A few details worth noting:</span></span>

- <span data-ttu-id="2fa0e-184">Аналогично операции отправки, операция получения сначала вызывает `ThrowIfDisposedOrNotOepned`, чтобы убедиться в том, что `CommunicationState` - открыто.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-184">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="2fa0e-185">Операция получения также синхронизируется таким образом, что во время каждого сеанса может быть получено только одно сообщение.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-185">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="2fa0e-186">Это особенно важно, так как после того, как получен начальный фрагмент сообщения, ожидается, что все последующие сообщения являются фрагментами этой новой последовательности фрагментов до получения конечного фрагмента сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-186">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="2fa0e-187">Операция получения не может извлекать сообщения из внутреннего канала до тех пор, пока все фрагменты сообщения, дефрагментируемого в настоящий момент, не будут получены.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-187">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="2fa0e-188">Чтобы выполнить это действие, операция получения использует событие `ManualResetEvent` с именем `currentMessageCompleted`, которое задается при получении последнего фрагмента сообщения и сбрасывается при получении нового начального фрагмента сообщения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-188">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="2fa0e-189">В отличие от операции отправки, операция получения не препятствует синхронизированным переходам между состояниями при получении.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-189">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="2fa0e-190">Например, операция "Закрыть" может быть вызвана при выполнении операции получения; она будет выполнена по окончании получения исходного сообщения или по истечении заданного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-190">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="2fa0e-191">Время ожидания, передаваемое в метод получения, используется как время ожидания выполнения всей операции получения, то есть получения всех фрагментов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-191">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="2fa0e-192">Если уровень, считывающий сообщение, считывает тело сообщения с частотой более низкой, чем частота входящих фрагментов сообщения, `ChunkingReader` выполняет буферизацию входящих фрагментов до предела, установленного `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-192">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="2fa0e-193">При достижении заданного предела фрагменты не извлекаются из более низкого уровня до тех пор, пока не будет считан буферизованный фрагмент или не истечет время ожидания выполнения операции получения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-193">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="2fa0e-194">CommunicationObject - переопределения</span><span class="sxs-lookup"><span data-stu-id="2fa0e-194">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="2fa0e-195">OnOpen</span><span class="sxs-lookup"><span data-stu-id="2fa0e-195">OnOpen</span></span>

<span data-ttu-id="2fa0e-196">`OnOpen` вызывает `innerChannel.Open`, чтобы открыть внутренний канал.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-196">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="2fa0e-197">OnClose</span><span class="sxs-lookup"><span data-stu-id="2fa0e-197">OnClose</span></span>

<span data-ttu-id="2fa0e-198">`OnClose` сначала задает `stopReceive` значение `true`, чтобы указать, что требуется остановить выполняющийся `ReceiveChunkLoop`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-198">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="2fa0e-199">Затем он ожидает `receiveStopped` <xref:System.Threading.ManualResetEvent> , который задается при `ReceiveChunkLoop` остановке.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-199">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="2fa0e-200">Предполагая, что `ReceiveChunkLoop` остановится в течение заданного времени ожидания, `OnClose` вызывает `innerChannel.Close` с остающимся временем ожидания.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-200">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="2fa0e-201">OnAbort</span><span class="sxs-lookup"><span data-stu-id="2fa0e-201">OnAbort</span></span>

<span data-ttu-id="2fa0e-202">`OnAbort` вызывает `innerChannel.Abort`, чтобы прервать внутренний канал.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-202">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="2fa0e-203">Если имеется выполняемый `ReceiveChunkLoop`, он возвращает исключение от выполняемого вызова `innerChannel.Receive`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-203">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="2fa0e-204">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="2fa0e-204">OnFaulted</span></span>

<span data-ttu-id="2fa0e-205">Для `ChunkingChannel` не требуется специальное поведение при возникновении ошибки в канале, поэтому `OnFaulted` не переопределяется.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-205">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="2fa0e-206">Реализация фабрики каналов</span><span class="sxs-lookup"><span data-stu-id="2fa0e-206">Implementing Channel Factory</span></span>

<span data-ttu-id="2fa0e-207">`ChunkingChannelFactory` отвечает за создание экземпляров каналов `ChunkingDuplexSessionChannel` и выполнение каскадных переходов состояний в фабрику внутренних каналов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-207">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="2fa0e-208">`OnCreateChannel` использует фабрику внутренних каналов для создания внутреннего канала `IDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-208">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="2fa0e-209">Затем метод создает новый `ChunkingDuplexSessionChannel`, передавая ему этот внутренний канал вместе со списком действий фрагментируемых сообщений и максимальным количеством фрагментов, буферизуемых при получении.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-209">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="2fa0e-210">Список фрагментируемых сообщений и максимальное количество буферизуемых фрагментов - это два параметра, передаваемые `ChunkingChannelFactory` в его конструкторе.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-210">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="2fa0e-211">В разделе об `ChunkingBindingElement` описывается, откуда возникают эти значения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-211">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="2fa0e-212">Методы `OnOpen`, `OnClose`, `OnAbort` и их асинхронные эквиваленты вызывают соответствующий метод перехода между состояниями в фабрике внутренних каналов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-212">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="2fa0e-213">Реализация прослушивателя каналов</span><span class="sxs-lookup"><span data-stu-id="2fa0e-213">Implementing Channel Listener</span></span>

<span data-ttu-id="2fa0e-214">`ChunkingChannelListener` является оболочкой прослушивателя внутренних каналов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-214">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="2fa0e-215">Его основной функцией, помимо делегирования вызовов в прослушиватель внутренних каналов, является создание новой программы-оболочки `ChunkingDuplexSessionChannels` для каналов, принимаемых из прослушивателя внутренних каналов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-215">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="2fa0e-216">Это выполняется в методах `OnAcceptChannel` и `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-216">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="2fa0e-217">Созданная `ChunkingDuplexSessionChannel` передается во внутренний канал вместе с другими ранее описанными параметрами.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-217">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="2fa0e-218">Реализация элемента привязки и привязки</span><span class="sxs-lookup"><span data-stu-id="2fa0e-218">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="2fa0e-219">Элемент `ChunkingBindingElement` отвечает за создание фабрики `ChunkingChannelFactory` и прослушивателя `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-219">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="2fa0e-220">`ChunkingBindingElement`Проверяет, относится ли T к `CanBuildChannelFactory` \<T> `CanBuildChannelListener` \<T> типу `IDuplexSessionChannel` (единственный канал, поддерживаемый каналом фрагментирования), и что другие элементы привязки в привязке поддерживают этот тип канала.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-220">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="2fa0e-221">`BuildChannelFactory`\<T> сначала проверяет, можно ли построить запрошенный тип канала, а затем получает список действий с сообщениями, которые будут фрагментированы.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-221">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="2fa0e-222">Дополнительные сведения приведены в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-222">For more information, see the following section.</span></span> <span data-ttu-id="2fa0e-223">Затем метод создает новую фабрику `ChunkingChannelFactory`, передавая ей фабрику внутренних каналов (возвращенную из `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), список действий фрагментируемых сообщений и максимальное количество буферизуемых фрагментов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-223">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="2fa0e-224">Максимальное количество фрагментов определяется свойством `MaxBufferedChunks`, предоставляемым `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-224">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="2fa0e-225">`BuildChannelListener<T>` имеет аналогичную реализацию для создания прослушивателя `ChunkingChannelListener` и передаче его прослушивателю внутреннего канала.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-225">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="2fa0e-226">Пример привязки включен в пример `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-226">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="2fa0e-227">Эта привязка состоит из двух элементов привязки: `TcpTransportBindingElement` и `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-227">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="2fa0e-228">Помимо предоставления свойства `MaxBufferedChunks`, привязка также задает некоторые свойства `TcpTransportBindingElement`, например `MaxReceivedMessageSize` (задает ему значение `ChunkingUtils.ChunkSize` + 100 КБ байтов для заголовков).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-228">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="2fa0e-229">`TcpChunkingBinding` также реализует `IBindingRuntimePreferences` и возвращает значение "true" из метода `ReceiveSynchronously`, означающее, что реализуются только синхронные вызовы операции получения.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-229">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="2fa0e-230">Какие сообщения следует фрагментировать</span><span class="sxs-lookup"><span data-stu-id="2fa0e-230">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="2fa0e-231">Канал фрагментации фрагментирует только сообщения, определенные посредством атрибута `ChunkingBehavior`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-231">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="2fa0e-232">Класс `ChunkingBehavior` реализует метод `IOperationBehavior` и реализуется с помощью вызова метода `AddBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-232">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="2fa0e-233">В этом методе `ChunkingBehavior` проверяет значение свойства `AppliesTo` (`InMessage`, `OutMessage` или обоих), чтобы определить, какие сообщения следует фрагментировать.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-233">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="2fa0e-234">Затем он возвращает действие для каждого сообщения (из коллекции сообщений в `OperationDescription`) и добавляет их в коллекцию строк, содержащуюся в экземпляре `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-234">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="2fa0e-235">Затем он добавляет этот параметр `ChunkingBindingParameter` в предоставленную коллекцию `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-235">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="2fa0e-236">`BindingParameterCollection` передается внутри `BindingContext` каждому элементу привязки в привязке при построении этим элементом привязки фабрики каналов или прослушивателя каналов.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-236">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="2fa0e-237">`ChunkingBindingElement`Реализация `BuildChannelFactory<T>` и извлечение `BuildChannelListener<T>` этого `ChunkingBindingParameter` объекта из `BindingContext’` s `BindingParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="2fa0e-237">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="2fa0e-238">Коллекция действий, содержащихся в параметре `ChunkingBindingParameter`, затем передается в фабрику `ChunkingChannelFactory` или прослушиватель `ChunkingChannelListener`, которые, в свою очередь, передают ее в канал `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-238">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="2fa0e-239">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="2fa0e-239">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fa0e-240">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="2fa0e-240">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2fa0e-241">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-241">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="2fa0e-242">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-242">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="2fa0e-243">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-243">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="2fa0e-244">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fa0e-244">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="2fa0e-245">Сначала запустите файл Service.exe, затем Client.exe и наблюдайте результат в обоих окнах консоли.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-245">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="2fa0e-246">При выполнении этого образца ожидаются следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="2fa0e-246">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="2fa0e-247">Клиент:</span><span class="sxs-lookup"><span data-stu-id="2fa0e-247">Client:</span></span>

```console
Press enter when service is available

 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

<span data-ttu-id="2fa0e-248">Сервер: </span><span class="sxs-lookup"><span data-stu-id="2fa0e-248">Server:</span></span>

```console
Service started, press enter to exit
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```
