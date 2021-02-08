---
description: 'Дополнительные сведения: <customBinding>'
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: a4d297750d107648aa10b349c6febc1a8929a30b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803949"
---
# \<customBinding>

<span data-ttu-id="29688-102">Обеспечивает пользователю полный контроль над стеком обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="29688-102">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="29688-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="29688-103">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29688-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="29688-104">Attributes and Elements</span></span>

<span data-ttu-id="29688-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="29688-105">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="29688-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="29688-106">Attributes</span></span>

|<span data-ttu-id="29688-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="29688-107">Attribute</span></span>|<span data-ttu-id="29688-108">Описание</span><span class="sxs-lookup"><span data-stu-id="29688-108">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="29688-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="29688-109">closeTimeout</span></span>|<span data-ttu-id="29688-110">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="29688-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="29688-111">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29688-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29688-112">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29688-112">The default is 00:01:00.</span></span>|
|<span data-ttu-id="29688-113">name</span><span class="sxs-lookup"><span data-stu-id="29688-113">name</span></span>|<span data-ttu-id="29688-114">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-114">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="29688-115">Это значение является определяемой пользователем строкой, которая используется как строка идентификации для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-115">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="29688-116">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="29688-116">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="29688-117">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="29688-117">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="29688-118">openTimeout</span><span class="sxs-lookup"><span data-stu-id="29688-118">openTimeout</span></span>|<span data-ttu-id="29688-119">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="29688-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="29688-120">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29688-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29688-121">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29688-121">The default is 00:01:00.</span></span>|
|<span data-ttu-id="29688-122">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="29688-122">receiveTimeout</span></span>|<span data-ttu-id="29688-123">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="29688-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="29688-124">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29688-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29688-125">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29688-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="29688-126">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="29688-126">sendTimeout</span></span>|<span data-ttu-id="29688-127">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="29688-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="29688-128">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="29688-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29688-129">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="29688-129">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="29688-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="29688-130">Child Elements</span></span>

|<span data-ttu-id="29688-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="29688-131">Element</span></span>|<span data-ttu-id="29688-132">Описание</span><span class="sxs-lookup"><span data-stu-id="29688-132">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="29688-133">Определяет двусторонний обмен сообщениями в пользовательской привязке.</span><span class="sxs-lookup"><span data-stu-id="29688-133">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="29688-134">Используется транспортными протоколами, которые не имеют встроенной поддержки дуплексной связи, например HTTP.</span><span class="sxs-lookup"><span data-stu-id="29688-134">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="29688-135">Напротив, протокол TCP имеет встроенную поддержку дуплексной связи, и для него не требуется использовать этот элемент привязки для службы при отправке сообщений обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="29688-135">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="29688-136">Для осуществления контакта и установления подключения клиент должен предоставить службе адрес.</span><span class="sxs-lookup"><span data-stu-id="29688-136">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="29688-137">Этот адрес клиента предоставляется атрибутом `ClientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="29688-137">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="29688-138">Это элемент типа <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-138">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="29688-139">Определяет распознавателя имен узлов в протоколе однорангового разрешения имен (PNRP).</span><span class="sxs-lookup"><span data-stu-id="29688-139">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="29688-140">Это элемент типа <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-140">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="29688-141">Определяет параметры WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="29688-141">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="29688-142">Когда этот элемент добавляется к пользовательской привязке, получаемый канал может поддерживать гарантии доставки только один раз.</span><span class="sxs-lookup"><span data-stu-id="29688-142">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="29688-143">Это элемент типа <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-143">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="29688-144">Определяет параметры безопасности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-144">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="29688-145">Это элемент типа <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-145">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="29688-146">Определяет параметры безопасности привязки потока SSL.</span><span class="sxs-lookup"><span data-stu-id="29688-146">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="29688-147">Это элемент типа <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-147">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="29688-148">Указывает, что привязка поддерживает поток транзакций, и задает используемый протокол в атрибуте `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="29688-148">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="29688-149">Это элемент типа <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-149">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="29688-150">Определяет параметры для потоковой безопасности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-150">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="29688-151">Это элемент типа <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="29688-151">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29688-152">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="29688-152">Parent Elements</span></span>

|<span data-ttu-id="29688-153">Элемент</span><span class="sxs-lookup"><span data-stu-id="29688-153">Element</span></span>|<span data-ttu-id="29688-154">Описание</span><span class="sxs-lookup"><span data-stu-id="29688-154">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="29688-155">привязки</span><span class="sxs-lookup"><span data-stu-id="29688-155">bindings</span></span>|<span data-ttu-id="29688-156">Содержит все привязки для приложений Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="29688-156">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29688-157">Remarks</span><span class="sxs-lookup"><span data-stu-id="29688-157">Remarks</span></span>

<span data-ttu-id="29688-158">Пользовательские привязки предоставляют полный контроль над стеком обмена сообщениями WCF.</span><span class="sxs-lookup"><span data-stu-id="29688-158">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="29688-159">Путем добавления элементов конфигурации к определенным сущностям можно создавать специально настроенные привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-159">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="29688-160">Например, чтобы создать надежную и безопасную привязку на основе протокола HTTPS, пользователь может объединить разделы `httpsTransport`, `reliableSession` и `security`.</span><span class="sxs-lookup"><span data-stu-id="29688-160">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="29688-161">Отдельная привязка определяет стек обмена сообщениями, задавая элементы конфигурации для элементов стека в том порядке, в котором они присутствуют в стеке.</span><span class="sxs-lookup"><span data-stu-id="29688-161">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="29688-162">Каждый элемент определяет и задает параметры одного элемента стека.</span><span class="sxs-lookup"><span data-stu-id="29688-162">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="29688-163">В каждой пользовательской привязке должен быть один и только один транспортный элемент.</span><span class="sxs-lookup"><span data-stu-id="29688-163">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="29688-164">Без этого элемента стек обмена сообщениями является неполным.</span><span class="sxs-lookup"><span data-stu-id="29688-164">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="29688-165">Важен порядок, в котором элементы присутствуют в стеке, поскольку именно в этом порядке к сообщению применяются операции.</span><span class="sxs-lookup"><span data-stu-id="29688-165">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="29688-166">Рекомендуется следующий порядок элементов стека:</span><span class="sxs-lookup"><span data-stu-id="29688-166">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="29688-167">Транзакции (необязательный)</span><span class="sxs-lookup"><span data-stu-id="29688-167">Transactions (optional)</span></span>

2. <span data-ttu-id="29688-168">Надежный обмен сообщениями (необязательный)</span><span class="sxs-lookup"><span data-stu-id="29688-168">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="29688-169">Безопасность (необязательный)</span><span class="sxs-lookup"><span data-stu-id="29688-169">Security (optional)</span></span>

4. <span data-ttu-id="29688-170">Транспорт</span><span class="sxs-lookup"><span data-stu-id="29688-170">Transport</span></span>

5. <span data-ttu-id="29688-171">Кодировщик (необязательный)</span><span class="sxs-lookup"><span data-stu-id="29688-171">Encoder (optional)</span></span>

<span data-ttu-id="29688-172">Используйте пользовательские привязки в случае, когда ни одна из системных привязок не соответствует требованиям службы.</span><span class="sxs-lookup"><span data-stu-id="29688-172">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="29688-173">Так, с помощью пользовательской привязки можно разрешить использование нового транспорта или нового кодировщика в конечной точке службы.</span><span class="sxs-lookup"><span data-stu-id="29688-173">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="29688-174">Пользовательская привязка создается с использованием одного из <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> из коллекции элементов привязки, которые располагаются в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="29688-174">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="29688-175">Вверху расположен необязательный элемент <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, который разрешает поток транзакций.</span><span class="sxs-lookup"><span data-stu-id="29688-175">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="29688-176">Далее следует необязательный элемент <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>, который предоставляет сеанс и механизм сортировки в соответствии со спецификацией WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="29688-176">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="29688-177">Это понятие сеанса может выходить за пределы посредников SOAP и транспорта.</span><span class="sxs-lookup"><span data-stu-id="29688-177">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="29688-178">Далее следует необязательный элемент привязки безопасности, который предоставляет функции безопасности, например авторизацию, проверку подлинности, защиту и конфиденциальность.</span><span class="sxs-lookup"><span data-stu-id="29688-178">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="29688-179">Windows Communication Foundation (WCF) предоставляет следующие элементы привязки безопасности:</span><span class="sxs-lookup"><span data-stu-id="29688-179">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="29688-180">Далее следуют необязательные шаблоны сообщений, задаваемые элементами привязки.</span><span class="sxs-lookup"><span data-stu-id="29688-180">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="29688-181">Затем — необязательные элементы привязки обновлений/поддержки транспорта.</span><span class="sxs-lookup"><span data-stu-id="29688-181">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="29688-182">Далее следует обязательный элемент привязки для кодирования сообщений.</span><span class="sxs-lookup"><span data-stu-id="29688-182">Next is a required message encoding binding element.</span></span> <span data-ttu-id="29688-183">Можно использовать собственный транспорт или одну из следующих привязок кодирования сообщений.</span><span class="sxs-lookup"><span data-stu-id="29688-183">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="29688-184">Внизу расположен обязательный элемент транспорта.</span><span class="sxs-lookup"><span data-stu-id="29688-184">At the bottom is a required transport element.</span></span> <span data-ttu-id="29688-185">Можно использовать собственный транспорт или один из элементов привязки транспорта, предоставляемых Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="29688-185">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="29688-186">В следующей таблице приведены сводные данные по параметрам каждого уровня.</span><span class="sxs-lookup"><span data-stu-id="29688-186">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="29688-187">Уровень</span><span class="sxs-lookup"><span data-stu-id="29688-187">Layer</span></span>|<span data-ttu-id="29688-188">Параметры</span><span class="sxs-lookup"><span data-stu-id="29688-188">Options</span></span>|<span data-ttu-id="29688-189">Обязательно</span><span class="sxs-lookup"><span data-stu-id="29688-189">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="29688-190">Поток транзакций</span><span class="sxs-lookup"><span data-stu-id="29688-190">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="29688-191">Нет</span><span class="sxs-lookup"><span data-stu-id="29688-191">No</span></span>|
|<span data-ttu-id="29688-192">Надежность</span><span class="sxs-lookup"><span data-stu-id="29688-192">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="29688-193">Нет</span><span class="sxs-lookup"><span data-stu-id="29688-193">No</span></span>|
|<span data-ttu-id="29688-194">Безопасность</span><span class="sxs-lookup"><span data-stu-id="29688-194">Security</span></span>|<span data-ttu-id="29688-195">Симметричный, асимметричный, транспортного уровня</span><span class="sxs-lookup"><span data-stu-id="29688-195">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="29688-196">Нет</span><span class="sxs-lookup"><span data-stu-id="29688-196">No</span></span>|
|<span data-ttu-id="29688-197">Изменение формы</span><span class="sxs-lookup"><span data-stu-id="29688-197">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="29688-198">Нет</span><span class="sxs-lookup"><span data-stu-id="29688-198">No</span></span>|
|<span data-ttu-id="29688-199">Обновления транспорта</span><span class="sxs-lookup"><span data-stu-id="29688-199">Transport Upgrades</span></span>|<span data-ttu-id="29688-200">Поток SSL, поток Windows, распознаватель одноранговых узлов</span><span class="sxs-lookup"><span data-stu-id="29688-200">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="29688-201">Нет</span><span class="sxs-lookup"><span data-stu-id="29688-201">No</span></span>|
|<span data-ttu-id="29688-202">Кодирование</span><span class="sxs-lookup"><span data-stu-id="29688-202">Encoding</span></span>|<span data-ttu-id="29688-203">Текстовая, двоичная, MTOM, пользовательская</span><span class="sxs-lookup"><span data-stu-id="29688-203">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="29688-204">Да</span><span class="sxs-lookup"><span data-stu-id="29688-204">Yes</span></span>|
|<span data-ttu-id="29688-205">Транспорт</span><span class="sxs-lookup"><span data-stu-id="29688-205">Transport</span></span>|<span data-ttu-id="29688-206">TCP, именованные каналы, HTTP, HTTPS, разновидности MSMQ, пользовательский</span><span class="sxs-lookup"><span data-stu-id="29688-206">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="29688-207">Да</span><span class="sxs-lookup"><span data-stu-id="29688-207">Yes</span></span>|

<span data-ttu-id="29688-208">Кроме того, можно определить собственные элементы привязки и вставить их между любыми из приведенных выше заданных уровней.</span><span class="sxs-lookup"><span data-stu-id="29688-208">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="29688-209">Обсуждение того, как использовать пользовательскую привязку для изменения привязок, предоставляемых системой, см. в разделе [как настроить привязку System-Provided](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="29688-209">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29688-210">См. также</span><span class="sxs-lookup"><span data-stu-id="29688-210">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="29688-211">Привязки</span><span class="sxs-lookup"><span data-stu-id="29688-211">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29688-212">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="29688-212">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="29688-213">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="29688-213">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="29688-214">customBinding, элемент</span><span class="sxs-lookup"><span data-stu-id="29688-214">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="29688-215">Привязки</span><span class="sxs-lookup"><span data-stu-id="29688-215">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29688-216">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="29688-216">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="29688-217">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="29688-217">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
