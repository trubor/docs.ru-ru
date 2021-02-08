---
description: 'Подробнее о: протокол надежного обмена сообщениями версии 1,0'
title: Протокол надежного обмена сообщениями, версия 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: dbd0184fd6ea9f92c96639d71088ac61bec20f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793601"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="4e37b-103">Протокол надежного обмена сообщениями, версия 1.0</span><span class="sxs-lookup"><span data-stu-id="4e37b-103">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="4e37b-104">В этом разделе рассматриваются сведения о реализации Windows Communication Foundation (WCF) по протоколу WS-Reliable Messaging 2005 (версия 1,0), необходимый для взаимодействия с помощью транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e37b-104">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="4e37b-105">WCF использует спецификацию обмена сообщениями WS-Reliable с ограничениями и пояснениями, описанными в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="4e37b-105">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="4e37b-106">Обратите внимание, что протокол WS-ReliableMessaging версии 1,0 реализуется, начиная с WinFX.</span><span class="sxs-lookup"><span data-stu-id="4e37b-106">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="4e37b-107">Протокол WS-Reliable Messaging 2005 реализован в WCF с помощью <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="4e37b-107">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="4e37b-108">Для удобства объяснения в этом разделе используются следующие роли:</span><span class="sxs-lookup"><span data-stu-id="4e37b-108">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="4e37b-109">инициатор: клиент, инициирующий создание последовательности сообщений WS-Reliable;</span><span class="sxs-lookup"><span data-stu-id="4e37b-109">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="4e37b-110">респондент: служба, получающая запросы инициатора.</span><span class="sxs-lookup"><span data-stu-id="4e37b-110">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="4e37b-111">В этом документе используются префиксы и пространства имен, описанные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="4e37b-111">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="4e37b-112">Prefix</span><span class="sxs-lookup"><span data-stu-id="4e37b-112">Prefix</span></span>|<span data-ttu-id="4e37b-113">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="4e37b-113">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="4e37b-114">wsrm</span><span class="sxs-lookup"><span data-stu-id="4e37b-114">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="4e37b-115">netrm</span><span class="sxs-lookup"><span data-stu-id="4e37b-115">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="4e37b-116">s</span><span class="sxs-lookup"><span data-stu-id="4e37b-116">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="4e37b-117">wsa</span><span class="sxs-lookup"><span data-stu-id="4e37b-117">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="4e37b-118">wsse</span><span class="sxs-lookup"><span data-stu-id="4e37b-118">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="4e37b-119">Обмен сообщениями</span><span class="sxs-lookup"><span data-stu-id="4e37b-119">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="4e37b-120">Сообщения установления последовательности</span><span class="sxs-lookup"><span data-stu-id="4e37b-120">Sequence Establishment Messages</span></span>

<span data-ttu-id="4e37b-121">WCF реализует `CreateSequence` и `CreateSequenceResponse` сообщения для установления надежной последовательности сообщений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-121">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="4e37b-122">Действуют следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-122">The following constraints apply:</span></span>

- <span data-ttu-id="4e37b-123">B1101: инициатор WCF не создает необязательный элемент Expires в `CreateSequence` сообщении или, в случае, если `CreateSequence` сообщение содержит `Offer` элемент, необязательный `Expires` элемент в `Offer` элементе.</span><span class="sxs-lookup"><span data-stu-id="4e37b-123">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="4e37b-124">B1102: при доступе к `CreateSequence` сообщению WCF `Responder` отправляет и получает оба `Expires` элемента, если они существуют, но не использует их значения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-124">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="4e37b-125">Протокол WS-Reliable Messaging использует механизм `Offer` для формирования двух коррелированных встречных последовательностей, которые составляют сеанс.</span><span class="sxs-lookup"><span data-stu-id="4e37b-125">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="4e37b-126">R1103: если сообщение `CreateSequence` содержит элемент `Offer`, респондент системы надежного обмена сообщениями должен либо принять последовательности и выдать ответ `CreateSequenceResponse`, который содержит элемент `wsrm:Accept`, образующий две коррелированных встречных последовательности, либо отклонить запрос `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-126">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="4e37b-127">R1104: `SequenceAcknowledgement` и сообщения приложения, передаваемые во встречной последовательности, должны быть отправлены по адресу ссылки конечной последовательности `ReplyTo` в `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-127">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="4e37b-128">R1105: адреса ссылок на конечные точки `AcksTo` и `ReplyTo` в сообщении `CreateSequence` должны совпадать на уровне октетов.</span><span class="sxs-lookup"><span data-stu-id="4e37b-128">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="4e37b-129">Перед созданием последовательности в WCF-ответчике проверяется, что часть URI `AcksTo` и `ReplyTo` епрс идентичны.</span><span class="sxs-lookup"><span data-stu-id="4e37b-129">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="4e37b-130">R1106: ссылки на конечные точки `AcksTo` и `ReplyTo` в сообщении `CreateSequence` должны иметь один и тот же набор параметров ссылок.</span><span class="sxs-lookup"><span data-stu-id="4e37b-130">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="4e37b-131">WCF не применяет принудительное применение, но предполагает, что [параметры ссылки] в `AcksTo` и `ReplyTo` On `CreateSequence` идентичны, и использует [ссылочные параметры] из `ReplyTo` ссылки на конечную точку для подтверждения и последовательного обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="4e37b-131">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="4e37b-132">R1107: при установке двух встречных последовательностей с помощью механизма `Offer` сообщение `SequenceAcknowledgement` и сообщения приложения во встречных последовательностях должны отправляться по ссылке на конечную точку `ReplyTo` в сообщении `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-132">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="4e37b-133">R1108: при установке двух встречных последовательностей с помощью механизма "Offer" свойство `[address]` дочернего элемента ссылки на конечную точку `wsrm:AcksTo` элемента `wsrm:Accept` в сообщении `CreateSequenceResponse` должно с точностью до байта совпадать с универсальным кодом ресурса (URI) назначения сообщения `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-133">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="4e37b-134">R1109: при установке двух встречных последовательностей с помощью механизма `Offer` сообщения, отправленные инициатором, и подтверждения на сообщения респондента должны отправляться по одной и той же ссылке на конечную точку.</span><span class="sxs-lookup"><span data-stu-id="4e37b-134">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="4e37b-135">WCF использует WS-Reliable обмена сообщениями для установления надежных сеансов между инициатором и ответчиком.</span><span class="sxs-lookup"><span data-stu-id="4e37b-135">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="4e37b-136">Реализация обмена сообщениями WS-Reliable WCF обеспечивает надежный сеанс для односторонних, однонаправленных и полноценных шаблонов обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="4e37b-136">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="4e37b-137">Механизм обмена сообщениями WS-Reliable `Offer` в `CreateSequence` / `CreateSequenceResponse` позволяет установить две коррелированные последовательности обратной связи и предоставляет протокол сеанса, подходящий для всех конечных точек сообщений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-137">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="4e37b-138">Поскольку WCF предоставляет гарантию безопасности для такого сеанса, включая сквозную защиту для целостности сеанса, целесообразно убедиться, что сообщения, предназначенные для одной и той же стороны, поступают в одно и то же место назначения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-138">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="4e37b-139">Кроме того, это делает возможным передачу подтверждений последовательностей в сообщениях приложений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-139">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="4e37b-140">Таким образом, ограничения R1104, R1105 и R1108 применяются к WCF.</span><span class="sxs-lookup"><span data-stu-id="4e37b-140">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="4e37b-141">Пример сообщения `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-141">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="4e37b-142">Пример сообщения `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-142">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="4e37b-143">Последовательность</span><span class="sxs-lookup"><span data-stu-id="4e37b-143">Sequence</span></span>

<span data-ttu-id="4e37b-144">Ниже приведен список ограничений, относящихся к последовательностям.</span><span class="sxs-lookup"><span data-stu-id="4e37b-144">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="4e37b-145">B1201: WCF создает и обращается к порядковым номерам не выше `xs:long` максимального включительного значения 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="4e37b-145">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="4e37b-146">B1202: WCF всегда создает Последнее сообщение Empty-воплощающего с универсальным кодом ресурса (URI) действия `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="4e37b-146">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="4e37b-147">B1203: WCF получает и доставляет сообщение с заголовком последовательности, содержащим `LastMessage` элемент, если URI действия не имеет значение `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="4e37b-147">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="4e37b-148">Пример заголовка последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-148">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="4e37b-149">Заголовок AckRequested</span><span class="sxs-lookup"><span data-stu-id="4e37b-149">AckRequested Header</span></span>

<span data-ttu-id="4e37b-150">WCF использует `AckRequested` заголовок в качестве механизма поддержания активности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-150">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="4e37b-151">WCF не создает необязательный `MessageNumber` элемент.</span><span class="sxs-lookup"><span data-stu-id="4e37b-151">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="4e37b-152">При получении сообщения с `AckRequested` заголовком, содержащим `MessageNumber` элемент, WCF игнорирует `MessageNumber` значение элемента, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4e37b-152">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="4e37b-153">Заголовок SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4e37b-153">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="4e37b-154">WCF использует механизм свинка для подтверждения последовательностей, предоставляемых в WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="4e37b-154">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="4e37b-155">R1401: при установке двух встречных последовательностей с помощью механизма `Offer` заголовок `SequenceAcknowledgement` может включаться в любое сообщение приложения, передаваемое определенному получателю.</span><span class="sxs-lookup"><span data-stu-id="4e37b-155">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="4e37b-156">B1402: когда WCF должен создать подтверждение перед получением любых сообщений последовательности (например, для удовлетворения `AckRequested` сообщения), WCF создает `SequenceAcknowledgement` заголовок, содержащий диапазон 0-0, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4e37b-156">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="4e37b-157">B1403: WCF не создает `SequenceAcknowledgement` заголовки, содержащие элемент, `Nack` но поддерживает `Nack` элементы.</span><span class="sxs-lookup"><span data-stu-id="4e37b-157">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="4e37b-158">Ошибки протокола WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="4e37b-158">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="4e37b-159">Ниже приведен список ограничений, которые применяются к реализации WCF ошибок обмена сообщениями WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="4e37b-159">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="4e37b-160">B1501: WCF не создает `MessageNumberRollover` ошибки.</span><span class="sxs-lookup"><span data-stu-id="4e37b-160">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="4e37b-161">B1502: в конечной точке WCF могут возникать `CreateSequenceRefused` ошибки, описанные в спецификации.</span><span class="sxs-lookup"><span data-stu-id="4e37b-161">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="4e37b-162">B1503: когда конечная точка службы достигает предельного числа подключений и не может обработать новые соединения, WCF создает дополнительный `CreateSequenceRefused` код ошибки, `netrm:ConnectionLimitReached` как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4e37b-162">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="4e37b-163">Ошибки WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="4e37b-163">WS-Addressing Faults</span></span>

<span data-ttu-id="4e37b-164">Поскольку WS-Reliable Messaging использует WS-Addressing, реализация WCF WS-Reliable Messaging может формировать WS-Addressing ошибок.</span><span class="sxs-lookup"><span data-stu-id="4e37b-164">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="4e37b-165">В этом разделе рассматриваются ошибки WS-Addressing, которые WCF явно создает на уровне WS-Reliable Messaging:</span><span class="sxs-lookup"><span data-stu-id="4e37b-165">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="4e37b-166">B1601: WCF создает заголовок адресации сообщения об ошибке, если выполняется одно из следующих условий.</span><span class="sxs-lookup"><span data-stu-id="4e37b-166">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="4e37b-167">в сообщении отсутствуют заголовки `Sequence` и `Action`;</span><span class="sxs-lookup"><span data-stu-id="4e37b-167">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="4e37b-168">в сообщении `CreateSequence` отсутствует заголовок `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-168">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="4e37b-169">в сообщении `CreateSequence` отсутствует заголовок `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-169">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="4e37b-170">B1602: WCF создает действие сбоя, не поддерживаемое в ответ на сообщение, в котором отсутствует `Sequence` заголовок и `Action` заголовок, который не распознается в спецификации обмена сообщениями WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="4e37b-170">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="4e37b-171">B1603: WCF создает конечную точку сбоя, чтобы указать, что конечная точка не обрабатывает последовательность на основе проверки `CreateSequence` заголовков адресации сообщения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-171">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="4e37b-172">Сочетаемость протокола</span><span class="sxs-lookup"><span data-stu-id="4e37b-172">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="4e37b-173">Сочетаемость с WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="4e37b-173">Composition with WS-Addressing</span></span>

<span data-ttu-id="4e37b-174">WCF поддерживает две версии WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] и рекомендации КОНСОРЦИУМа WS-Addressing 1,0 [WS-ADDR-CORE] и [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="4e37b-174">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="4e37b-175">Поскольку в спецификации протокола WS-Reliable Messaging указана только версия WS-Addressing 2004/08, он не накладывает ограничений на используемую версию WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4e37b-175">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="4e37b-176">Ниже приведен список ограничений, применяемых к WCF.</span><span class="sxs-lookup"><span data-stu-id="4e37b-176">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4e37b-177">R2101:с протоколом WS-Reliable Messaging можно использовать как версию WS-Addressing 2004/08, так и версию WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="4e37b-177">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="4e37b-178">R2102: одна версия WS-Addressing должна использоваться во всей заданной последовательности сообщений WS-Reliable или парой обратных последовательностей, коррелированных с помощью `wsrm:Offer` механизма.</span><span class="sxs-lookup"><span data-stu-id="4e37b-178">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="4e37b-179">Сочетаемость с SOAP</span><span class="sxs-lookup"><span data-stu-id="4e37b-179">Composition with SOAP</span></span>

<span data-ttu-id="4e37b-180">WCF поддерживает использование SOAP 1,1 и SOAP 1,2 с WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="4e37b-180">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="4e37b-181">Сочетаемость с WS-Security и WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="4e37b-181">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="4e37b-182">WCF обеспечивает защиту для последовательностей обмена сообщениями WS-Reliable с помощью защищенного транспорта (HTTPS), композиции с WS-Security и компоновки с WS-Secure диалога.</span><span class="sxs-lookup"><span data-stu-id="4e37b-182">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="4e37b-183">Ниже приведен список ограничений, применяемых к WCF.</span><span class="sxs-lookup"><span data-stu-id="4e37b-183">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4e37b-184">R2301. чтобы защитить целостность последовательности обмена сообщениями WS-Reliable в дополнение к целостности и конфиденциальности отдельных сообщений, WCF требует, чтобы использовался WS-Secure диалог.</span><span class="sxs-lookup"><span data-stu-id="4e37b-184">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="4e37b-185">R2302:перед установкой последовательностей WS-Reliable Messaging должен быть установлен сеанс WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="4e37b-185">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="4e37b-186">R2303: если время существования последовательности WS-Reliable Messaging превышает время существования сеанса WS-Secure Conversation, необходимо с помощью привязки обновления WS-Secure Conversation обновить маркер `SecurityContextToken`, созданный протоколом WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="4e37b-186">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="4e37b-187">B2304:последовательность WS-Reliable Messaging или пара встречных последовательностей всегда ограничены одним сеансом WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="4e37b-187">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="4e37b-188">Источник WCF создает `wsse:SecurityTokenReference` элемент в разделе "Расширяемость элементов" `CreateSequence` сообщения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-188">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="4e37b-189">R2305: при составлении с WS-Secure диалога `CreateSequence` сообщение должно содержать `wsse:SecurityTokenReference` элемент.</span><span class="sxs-lookup"><span data-stu-id="4e37b-189">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="4e37b-190">Утверждение WS-Reliable Messaging WS-Policy</span><span class="sxs-lookup"><span data-stu-id="4e37b-190">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="4e37b-191">`wsrm:RMAssertion`Для описания возможностей конечных точек WCF использует утверждение WS-Policy Messaging WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="4e37b-191">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="4e37b-192">Ниже приведен список ограничений, применяемых к WCF.</span><span class="sxs-lookup"><span data-stu-id="4e37b-192">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4e37b-193">B3001: WCF присоединяет `wsrm:RMAssertion` WS-Policy утверждения к `wsdl:binding` элементам.</span><span class="sxs-lookup"><span data-stu-id="4e37b-193">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="4e37b-194">WCF поддерживает как вложения, так `wsdl:binding` и `wsdl:port` элементы.</span><span class="sxs-lookup"><span data-stu-id="4e37b-194">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="4e37b-195">B3002: WCF поддерживает следующие необязательные свойства утверждения сообщений WS-Reliable и обеспечивает контроль над ними в WCF `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="4e37b-195">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="4e37b-196">Пример.</span><span class="sxs-lookup"><span data-stu-id="4e37b-196">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="4e37b-197">Расширение WS-Reliable Messaging для управления потоком</span><span class="sxs-lookup"><span data-stu-id="4e37b-197">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="4e37b-198">WCF использует WS-Reliable расширяемости обмена сообщениями для предоставления дополнительного более строгого контроля над потоком сообщений последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-198">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="4e37b-199">Управление потоком включается путем присвоения <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> свойству значения `true` .</span><span class="sxs-lookup"><span data-stu-id="4e37b-199">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="4e37b-200">Ниже приведен список ограничений, применяемых к WCF.</span><span class="sxs-lookup"><span data-stu-id="4e37b-200">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4e37b-201">B4001. Если включен механизм надежного управления потоком сообщений, WCF создает `netrm:BufferRemaining` элемент в расширяемости элемента `SequenceAcknowledgement` заголовка.</span><span class="sxs-lookup"><span data-stu-id="4e37b-201">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="4e37b-202">B4002: при включении управления потоком надежного обмена сообщениями WCF не требует наличия `netrm:BufferRemaining` элемента в `SequenceAcknowledgement` заголовке, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4e37b-202">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="4e37b-203">B4003: WCF использует `netrm:BufferRemaining` , чтобы указать, сколько новых сообщений может быть помещено в буфер назначения надежного обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="4e37b-203">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="4e37b-204">B4004. служба надежного обмена сообщениями WCF регулирует количество сообщений, передаваемых, когда приложение назначения надежного обмена сообщениями не может быстро получить сообщения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-204">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="4e37b-205">Точка назначения системы надежного обмена сообщениями помещает сообщения в буфер, и значение элемента снижается до 0.</span><span class="sxs-lookup"><span data-stu-id="4e37b-205">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="4e37b-206">B4005: WCF создает `netrm:BufferRemaining` целочисленные значения от 0 до 4096 включительно и считывает целочисленные значения от 0 до `xs:int` `maxInclusive` значения 214748364 включительно.</span><span class="sxs-lookup"><span data-stu-id="4e37b-206">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="4e37b-207">Шаблоны обмена сообщениями</span><span class="sxs-lookup"><span data-stu-id="4e37b-207">Message Exchange Patterns</span></span>

<span data-ttu-id="4e37b-208">В этом разделе описывается поведение WCF при использовании WS-Reliable обмена сообщениями для различных шаблонов обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="4e37b-208">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="4e37b-209">Для каждого шаблона обмена сообщениями рассматриваются два варианта развертывания:</span><span class="sxs-lookup"><span data-stu-id="4e37b-209">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="4e37b-210">неадресуемый инициатор - инициатор расположен за брандмауэром, респондент может отправлять инициатору сообщения только с HTTP-ответами;</span><span class="sxs-lookup"><span data-stu-id="4e37b-210">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="4e37b-211">адресуемый инициатор - как инициатор, так и респондент могут принимать HTTP-запросы, т. е. можно установить два встречных HTTP-подключения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-211">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="4e37b-212">Односторонний неадресуемый инициатор</span><span class="sxs-lookup"><span data-stu-id="4e37b-212">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4e37b-213">Привязка</span><span class="sxs-lookup"><span data-stu-id="4e37b-213">Binding</span></span>

<span data-ttu-id="4e37b-214">WCF предоставляет односторонний шаблон обмена сообщениями, используя одну последовательность по одному каналу HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e37b-214">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="4e37b-215">WCF использует HTTP-запросы для передачи всех сообщений из RMS в панель RMD и HTTP-ответ для передачи всех сообщений из панели RMD в RMS.</span><span class="sxs-lookup"><span data-stu-id="4e37b-215">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4e37b-216">Обмен сообщениями CreateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-216">CreateSequence Exchange</span></span>

<span data-ttu-id="4e37b-217">Инициатор WCF создает сообщение без `CreateSequence` предложения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-217">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="4e37b-218">WCF-ответчик `CreateSequence` перед созданием последовательности гарантирует, что не имеет предложения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-218">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="4e37b-219">WCF-ответчик отвечает на `CreateSequence` запрос с `CreateSequenceResponse` сообщением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-219">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="4e37b-220">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4e37b-220">SequenceAcknowledgement</span></span>

<span data-ttu-id="4e37b-221">Инициатор WCF обрабатывает подтверждения по ответу всех сообщений, за исключением `CreateSequence` сообщений и сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="4e37b-221">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="4e37b-222">WCF-ответчик всегда создает изолированное подтверждение в ответ на как последовательность, так и `AckRequested` сообщения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-222">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="4e37b-223">Сообщение TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-223">TerminateSequence message</span></span>

<span data-ttu-id="4e37b-224">WCF обрабатывается `TerminateSequence` как односторонняя операция, то есть HTTP-ответ содержит пустой текст и код состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-224">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="4e37b-225">Односторонний адресуемый инициатор</span><span class="sxs-lookup"><span data-stu-id="4e37b-225">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4e37b-226">Привязка</span><span class="sxs-lookup"><span data-stu-id="4e37b-226">Binding</span></span>

<span data-ttu-id="4e37b-227">WCF предоставляет односторонний шаблон обмена сообщениями, используя одну последовательность для входящего и исходящего HTTP-канала.</span><span class="sxs-lookup"><span data-stu-id="4e37b-227">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="4e37b-228">WCF использует HTTP-запросы для передачи всех сообщений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-228">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4e37b-229">Все HTTP-ответы имеют пустое тело и код состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-229">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4e37b-230">Обмен сообщениями CreateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-230">CreateSequence Exchange</span></span>

<span data-ttu-id="4e37b-231">Инициатор WCF создает сообщение без `CreateSequence` предложения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-231">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="4e37b-232">WCF-ответчик гарантирует, что `CreateSequence` перед созданием последовательности предложение не будет иметь предложения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-232">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="4e37b-233">Приложение WCF передает `CreateSequenceResponse` сообщение по HTTP-запросу, адресованному по ссылке на `ReplyTo` конечную точку.</span><span class="sxs-lookup"><span data-stu-id="4e37b-233">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="4e37b-234">Дуплексный адресуемый инициатор</span><span class="sxs-lookup"><span data-stu-id="4e37b-234">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4e37b-235">Привязка</span><span class="sxs-lookup"><span data-stu-id="4e37b-235">Binding</span></span>

<span data-ttu-id="4e37b-236">WCF предоставляет полностью асинхронный шаблон обмена сообщениями с использованием двух последовательностей через входящий и исходящий канал HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e37b-236">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="4e37b-237">WCF использует HTTP-запросы для передачи всех сообщений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-237">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4e37b-238">Все HTTP-ответы имеют пустое тело и код состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-238">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4e37b-239">Обмен сообщениями CreateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-239">CreateSequence Exchange</span></span>

<span data-ttu-id="4e37b-240">Инициатор WCF создает `CreateSequence` сообщение с предложением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-240">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="4e37b-241">WCF-ответчик обеспечивает наличие `CreateSequence` предложения перед созданием последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-241">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="4e37b-242">WCF отправляет в `CreateSequenceResponse` HTTP-запрос, адресованный в `CreateSequence` `ReplyTo` ссылку на конечную точку.</span><span class="sxs-lookup"><span data-stu-id="4e37b-242">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="4e37b-243">Время существования последовательности</span><span class="sxs-lookup"><span data-stu-id="4e37b-243">Sequence Lifetime</span></span>

<span data-ttu-id="4e37b-244">WCF рассматривает две последовательности как один полностью дуплексный сеанс.</span><span class="sxs-lookup"><span data-stu-id="4e37b-244">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="4e37b-245">При создании ошибки, которая не выполняет одну последовательность, WCF ждет, что удаленная конечная точка будет выполнять обе последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-245">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="4e37b-246">При чтении ошибки, которая не выполняет одну последовательность, WCF завершает обе последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-246">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="4e37b-247">WCF может закрыть свою исходящую последовательность и продолжить обработку сообщений на его входящей последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-247">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="4e37b-248">И наоборот, WCF может обработать закрытие входящей последовательности и продолжить отправку сообщений по исходящей последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-248">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="4e37b-249">Обмен сообщениями запрос-ответ, неадресуемый инициатор</span><span class="sxs-lookup"><span data-stu-id="4e37b-249">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4e37b-250">Привязка</span><span class="sxs-lookup"><span data-stu-id="4e37b-250">Binding</span></span>

<span data-ttu-id="4e37b-251">WCF предоставляет односторонний шаблон обмена сообщениями типа «запрос-ответ» с использованием двух последовательностей по одному каналу HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e37b-251">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="4e37b-252">WCF использует HTTP-запросы для передачи сообщений последовательности запросов и использует HTTP-ответы для передачи сообщений последовательности ответов.</span><span class="sxs-lookup"><span data-stu-id="4e37b-252">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4e37b-253">Обмен сообщениями CreateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-253">CreateSequence Exchange</span></span>

<span data-ttu-id="4e37b-254">Инициатор WCF создает `CreateSequence` сообщение с предложением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-254">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="4e37b-255">WCF-ответчик обеспечивает наличие `CreateSequence` предложения перед созданием последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-255">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="4e37b-256">WCF-ответчик отвечает на `CreateSequence` запрос с `CreateSequenceResponse` сообщением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-256">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="4e37b-257">Односторонний обмен сообщениями</span><span class="sxs-lookup"><span data-stu-id="4e37b-257">One-way Message</span></span>

<span data-ttu-id="4e37b-258">Чтобы успешно завершить односторонний протокол обмена сообщениями, инициатор WCF передает сообщение последовательности запросов по HTTP-запросу и получает отдельное `SequenceAcknowledgement` сообщение для HTTP-ответа.</span><span class="sxs-lookup"><span data-stu-id="4e37b-258">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="4e37b-259">Сообщение `SequenceAcknowledgement` должно подтвердить передачу сообщения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-259">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="4e37b-260">WCF-ответчик может ответить на запрос с помощью подтверждения, ошибки или ответа с пустым телом и кодом состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-260">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="4e37b-261">Двусторонний обмен сообщениями</span><span class="sxs-lookup"><span data-stu-id="4e37b-261">Two Way Messages</span></span>

<span data-ttu-id="4e37b-262">Для успешного завершения двустороннего обмена сообщениями инициатор WCF передает сообщение последовательности запросов по HTTP-запросу и получает сообщение последовательности ответов в ответе HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e37b-262">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="4e37b-263">Ответ должен содержать подтверждение `SequenceAcknowledgement` того, что сообщение последовательности запросов было передано.</span><span class="sxs-lookup"><span data-stu-id="4e37b-263">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="4e37b-264">WCF-ответчик может ответить на запрос с ответом на приложение, ошибку или ответ с пустым телом и кодом состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-264">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="4e37b-265">Из-за наличия односторонних сообщений и временных параметров ответов приложения номера последовательности запросов и номера последовательности ответов не коррелируют между собой.</span><span class="sxs-lookup"><span data-stu-id="4e37b-265">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="4e37b-266">Повторные попытки ответов</span><span class="sxs-lookup"><span data-stu-id="4e37b-266">Retrying Replies</span></span>

<span data-ttu-id="4e37b-267">WCF использует корреляцию HTTP-ответа "запрос — ответ" для двусторонней корреляции протокола обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="4e37b-267">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="4e37b-268">По этой причине инициатор WCF не прекращает повторную попытку сообщения последовательности запроса, когда сообщение последовательностей запроса подтверждено, а когда HTTP-ответ содержит подтверждение, сообщение пользователя или сбой.</span><span class="sxs-lookup"><span data-stu-id="4e37b-268">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="4e37b-269">WCF-ответчик повторяет ответы на стороне запроса HTTP, к которому коррелирован ответ.</span><span class="sxs-lookup"><span data-stu-id="4e37b-269">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="4e37b-270">Обмен сообщениями LastMessage</span><span class="sxs-lookup"><span data-stu-id="4e37b-270">LastMessage Exchange</span></span>

<span data-ttu-id="4e37b-271">Инициатор WCF создает и передает пустое Последнее сообщение воплощающего в конце HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="4e37b-271">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="4e37b-272">WCF требует ответа, но не учитывает фактическое ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="4e37b-272">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="4e37b-273">WCF-ответчик отвечает на Последнее сообщение воплощающего последовательности запросов с последним сообщением о последовательности ответов Empty-воплощающего.</span><span class="sxs-lookup"><span data-stu-id="4e37b-273">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="4e37b-274">Если WCF-ответчик получает Последнее сообщение, в котором нет URI действия `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF отправляет ответ с последним сообщением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-274">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="4e37b-275">В случае протокола двустороннего обмена сообщениями последнее сообщение содержит сообщение приложения, а в случае протокола одностороннего обмена сообщениями последнее сообщение будет пустым.</span><span class="sxs-lookup"><span data-stu-id="4e37b-275">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="4e37b-276">В WCF-ответчике не требуется подтверждение для последнего сообщения воплощающего последовательности ответов.</span><span class="sxs-lookup"><span data-stu-id="4e37b-276">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="4e37b-277">Обмен сообщениями TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-277">TerminateSequence Exchange</span></span>

<span data-ttu-id="4e37b-278">Когда все запросы получили допустимый ответ, инициатор WCF создает и передает сообщение последовательности запроса `TerminateSequence` на стороне HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="4e37b-278">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="4e37b-279">WCF требует ответа, но не учитывает фактическое ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="4e37b-279">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="4e37b-280">WCF отвечает на сообщение последовательности запросов `TerminateSequence` с `TerminateSequence` сообщением последовательности ответов.</span><span class="sxs-lookup"><span data-stu-id="4e37b-280">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="4e37b-281">В обычной последовательности отключения оба сообщения `TerminateSequence` содержат полный набор `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="4e37b-281">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="4e37b-282">Обмен сообщениями запрос-ответ, адресуемый инициатор</span><span class="sxs-lookup"><span data-stu-id="4e37b-282">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4e37b-283">Привязка</span><span class="sxs-lookup"><span data-stu-id="4e37b-283">Binding</span></span>

<span data-ttu-id="4e37b-284">WCF предоставляет шаблон обмена сообщениями типа «запрос-ответ» с использованием двух последовательностей для входящего и исходящего HTTP-канала.</span><span class="sxs-lookup"><span data-stu-id="4e37b-284">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="4e37b-285">WCF использует HTTP-запросы для передачи всех сообщений.</span><span class="sxs-lookup"><span data-stu-id="4e37b-285">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4e37b-286">Все HTTP-ответы имеют пустое тело и код состояния HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4e37b-286">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4e37b-287">Обмен сообщениями CreateSequence</span><span class="sxs-lookup"><span data-stu-id="4e37b-287">CreateSequence Exchange</span></span>

<span data-ttu-id="4e37b-288">Инициатор WCF создает `CreateSequence` сообщение с предложением.</span><span class="sxs-lookup"><span data-stu-id="4e37b-288">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="4e37b-289">WCF-ответчик обеспечивает наличие `CreateSequence` предложения перед созданием последовательности.</span><span class="sxs-lookup"><span data-stu-id="4e37b-289">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="4e37b-290">WCF отправляет в `CreateSequenceResponse` HTTP-запрос, адресованный в `CreateSequence` `ReplyTo` ссылку на конечную точку.</span><span class="sxs-lookup"><span data-stu-id="4e37b-290">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="4e37b-291">Корреляция запросов и ответов</span><span class="sxs-lookup"><span data-stu-id="4e37b-291">Request/Reply Correlation</span></span>

<span data-ttu-id="4e37b-292">Инициатор WCF гарантирует, что все сообщения запроса приложения поставили `MessageId` и `ReplyTo` ссылку на конечную точку.</span><span class="sxs-lookup"><span data-stu-id="4e37b-292">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="4e37b-293">Инициатор WCF применяет `CreateSequence` ссылку на `ReplyTo` конечную точку сообщения для каждого сообщения запроса приложения.</span><span class="sxs-lookup"><span data-stu-id="4e37b-293">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="4e37b-294">Для WCF-ответчика требуется, чтобы входящие сообщения запроса представили a `MessageId` и `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="4e37b-294">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="4e37b-295">WCF обеспечивает идентичность универсального кода ресурса (URI) ссылки на конечную точку для `CreateSequence` всех сообщений запроса приложения и.</span><span class="sxs-lookup"><span data-stu-id="4e37b-295">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
