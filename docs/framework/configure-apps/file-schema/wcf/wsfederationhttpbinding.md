---
description: 'Дополнительные сведения: <wsFederationHttpBinding>'
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 1217c4e46fe18ea5df478b8a790be4da33590c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682102"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="fc778-102">Определяет привязку, которая поддерживает спецификацию WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="fc778-102">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="fc778-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc778-103">Syntax</span></span>

```xml
<wsFederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc778-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fc778-104">Attributes and Elements</span></span>

<span data-ttu-id="fc778-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fc778-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc778-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fc778-106">Attributes</span></span>

|<span data-ttu-id="fc778-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fc778-107">Attribute</span></span>|<span data-ttu-id="fc778-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fc778-108">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fc778-109">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="fc778-109">bypassProxyOnLocal</span></span>|<span data-ttu-id="fc778-110">Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="fc778-110">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="fc778-111">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="fc778-111">The default is `false`.</span></span>|
|<span data-ttu-id="fc778-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fc778-112">closeTimeout</span></span>|<span data-ttu-id="fc778-113">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="fc778-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fc778-114">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc778-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc778-115">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc778-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="fc778-116">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="fc778-116">hostnameComparisonMode</span></span>|<span data-ttu-id="fc778-117">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="fc778-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="fc778-118">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="fc778-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="fc778-119">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="fc778-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="fc778-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="fc778-120">maxBufferPoolSize</span></span>|<span data-ttu-id="fc778-121">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="fc778-122">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="fc778-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="fc778-123">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="fc778-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="fc778-124">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fc778-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="fc778-125">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="fc778-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="fc778-126">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="fc778-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="fc778-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="fc778-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="fc778-128">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="fc778-129">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="fc778-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="fc778-130">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="fc778-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="fc778-131">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="fc778-131">The default is 65536.</span></span>|
|<span data-ttu-id="fc778-132">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="fc778-132">messageEncoding</span></span>|<span data-ttu-id="fc778-133">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="fc778-133">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="fc778-134">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fc778-134">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fc778-135">-Text: использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="fc778-135">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="fc778-136">-MTOM: используйте кодировщик обмена сообщениями, механизм передачи сообщений 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="fc778-136">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="fc778-137">Значение по умолчанию - Text.</span><span class="sxs-lookup"><span data-stu-id="fc778-137">The default is Text.</span></span><br /><br /> <span data-ttu-id="fc778-138">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="fc778-138">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="fc778-139">name</span><span class="sxs-lookup"><span data-stu-id="fc778-139">name</span></span>|<span data-ttu-id="fc778-140">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-140">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fc778-141">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fc778-142">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="fc778-142">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fc778-143">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc778-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="fc778-144">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fc778-144">openTimeout</span></span>|<span data-ttu-id="fc778-145">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="fc778-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fc778-146">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc778-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc778-147">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc778-147">The default is 00:01:00.</span></span>|
|<span data-ttu-id="fc778-148">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="fc778-148">privacyNoticeAt</span></span>|<span data-ttu-id="fc778-149">Строка, задающая универсальный код ресурса (URI), определяющий расположение примечания о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="fc778-149">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="fc778-150">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="fc778-150">privacyNoticeVersion</span></span>|<span data-ttu-id="fc778-151">Целое число, определяющее версию текущего уведомления о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="fc778-151">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="fc778-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="fc778-152">proxyAddress</span></span>|<span data-ttu-id="fc778-153">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="fc778-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="fc778-154">Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="fc778-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="fc778-155">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="fc778-155">The default is `null`.</span></span>|
|<span data-ttu-id="fc778-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fc778-156">receiveTimeout</span></span>|<span data-ttu-id="fc778-157">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="fc778-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fc778-158">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc778-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc778-159">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fc778-159">The default is 00:10:00.</span></span>|
|<span data-ttu-id="fc778-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fc778-160">sendTimeout</span></span>|<span data-ttu-id="fc778-161">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="fc778-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fc778-162">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fc778-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fc778-163">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fc778-163">The default is 00:01:00.</span></span>|
|<span data-ttu-id="fc778-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="fc778-164">textEncoding</span></span>|<span data-ttu-id="fc778-165">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="fc778-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="fc778-166">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fc778-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fc778-167">-BigEndianUnicode: Юникод байтов Encoding.</span><span class="sxs-lookup"><span data-stu-id="fc778-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="fc778-168">-Unicode: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="fc778-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="fc778-169">-UTF8:8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="fc778-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="fc778-170">По умолчанию используется значение UTF8.</span><span class="sxs-lookup"><span data-stu-id="fc778-170">The default is UTF8.</span></span> <span data-ttu-id="fc778-171">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="fc778-171">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="fc778-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="fc778-172">transactionFlow</span></span>|<span data-ttu-id="fc778-173">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="fc778-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="fc778-174">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="fc778-174">The default is `false`.</span></span>|
|<span data-ttu-id="fc778-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="fc778-175">useDefaultWebProxy</span></span>|<span data-ttu-id="fc778-176">Логическое значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="fc778-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="fc778-177">Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан).</span><span class="sxs-lookup"><span data-stu-id="fc778-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="fc778-178">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="fc778-178">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fc778-179">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fc778-179">Child Elements</span></span>

|<span data-ttu-id="fc778-180">Элемент</span><span class="sxs-lookup"><span data-stu-id="fc778-180">Element</span></span>|<span data-ttu-id="fc778-181">Описание</span><span class="sxs-lookup"><span data-stu-id="fc778-181">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="fc778-182">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="fc778-182">Defines the security settings for the message.</span></span> <span data-ttu-id="fc778-183">Это элемент типа <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fc778-183">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="fc778-184">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fc778-185">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fc778-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="fc778-186">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="fc778-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fc778-187">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fc778-187">Parent Elements</span></span>

|<span data-ttu-id="fc778-188">Элемент</span><span class="sxs-lookup"><span data-stu-id="fc778-188">Element</span></span>|<span data-ttu-id="fc778-189">Описание</span><span class="sxs-lookup"><span data-stu-id="fc778-189">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="fc778-190">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="fc778-190">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc778-191">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc778-191">Remarks</span></span>

<span data-ttu-id="fc778-192">Федерация - это возможность совместного использования удостоверений в нескольких системах в целях проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="fc778-192">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="fc778-193">Эти удостоверения могут ссылаться на пользователей или на компьютеры.</span><span class="sxs-lookup"><span data-stu-id="fc778-193">These identities can refer to users or to machines.</span></span> <span data-ttu-id="fc778-194">Федеративный протокол HTTP поддерживает безопасность SOAP и безопасность в смешанном режиме, но не поддерживает использование исключительно безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="fc778-194">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="fc778-195">Эта привязка обеспечивает поддержку Windows Communication Foundation (WCF) для протокола WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="fc778-195">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="fc778-196">Службы, настроенные с использованием этой привязки, должны использовать транспорт HTTP.</span><span class="sxs-lookup"><span data-stu-id="fc778-196">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="fc778-197">Привязки состоят из стека элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-197">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="fc778-198">Стек элементов привязки в</span><span class="sxs-lookup"><span data-stu-id="fc778-198">The stack of binding elements in</span></span>

<span data-ttu-id="fc778-199">`wsFederationHttpBinding` идентичен тому, что содержится в `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="fc778-199">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="fc778-200">Если [\<security>](security-of-wsfederationhttpbinding.md) для задано значение по умолчанию <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="fc778-200">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="fc778-201">Элемент `wsFederationHttpBinding` управления определяет сведения о параметрах безопасности сообщений в [\<message>](message-element-of-wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="fc778-201">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="fc778-202">Обратите внимание, что [\<security>](security-of-wsfederationhttpbinding.md) элемент предоставляет доступ get, только так как безопасность, используемая привязкой, не может быть изменена после создания привязки.</span><span class="sxs-lookup"><span data-stu-id="fc778-202">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="fc778-203">`wsFederationHttpBinding`Также предоставляет атрибут привацинотицеат для задания и получения универсального кода ресурса (URI), в котором находится уведомление о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="fc778-203">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="fc778-204">Обеспечение безопасности политики особенно важно в федеративных сценариях.</span><span class="sxs-lookup"><span data-stu-id="fc778-204">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="fc778-205">Для защиты политики от злоумышленников рекомендуется использовать определенную систему безопасности, например протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fc778-205">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="fc778-206">В федеративных сценариях с использованием этой привязки политика службы потенциально содержит важные сведения, например ключ для шифрования выдаваемого маркера (SAML), тип утверждений, помещаемых в маркер, и так далее.</span><span class="sxs-lookup"><span data-stu-id="fc778-206">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="fc778-207">Если политика подделана, атакующий может обнаружить ключ выданного маркера, что приводит к дальнейшим подделкам, раскрытию сведений и другим вредоносным действиям.</span><span class="sxs-lookup"><span data-stu-id="fc778-207">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="fc778-208">Чтобы предупредить злонамеренные действия, политика должна быть получена от службы безопасным способом (например, с помощью протокола HTTPS).</span><span class="sxs-lookup"><span data-stu-id="fc778-208">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="fc778-209">Дополнительные сведения об этой привязке см. в разделе [инструкции. Создание WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fc778-209">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc778-210">Пример</span><span class="sxs-lookup"><span data-stu-id="fc778-210">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fc778-211">См. также</span><span class="sxs-lookup"><span data-stu-id="fc778-211">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="fc778-212">Практическое руководство. Создание WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fc778-212">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="fc778-213">Привязки</span><span class="sxs-lookup"><span data-stu-id="fc778-213">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fc778-214">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="fc778-214">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fc778-215">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fc778-215">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
