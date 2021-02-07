---
description: 'Дополнительные сведения: <ws2007FederationHttpBinding>'
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 90635805573e5bee64d8adf0f79de827733f178b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682193"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="9a218-102">Безопасная и взаимодействующая привязка, производная от [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) и поддерживающая Федеративные системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="9a218-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9a218-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a218-103">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
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
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a218-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9a218-104">Attributes and Elements</span></span>

<span data-ttu-id="9a218-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9a218-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a218-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9a218-106">Attributes</span></span>

|<span data-ttu-id="9a218-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9a218-107">Attribute</span></span>|<span data-ttu-id="9a218-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9a218-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="9a218-109">Значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="9a218-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9a218-110">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="9a218-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="9a218-111">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="9a218-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9a218-112">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a218-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a218-113">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a218-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="9a218-114">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="9a218-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9a218-115">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="9a218-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9a218-116">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="9a218-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="9a218-117">Максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9a218-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9a218-118">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="9a218-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9a218-119">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="9a218-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9a218-120">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="9a218-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9a218-121">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="9a218-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9a218-122">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="9a218-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="9a218-123">Максимальный размер сообщения (в байтах), включая заголовки, которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9a218-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9a218-124">Отправитель сообщения, которое превысит это ограничение, получает ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="9a218-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="9a218-125">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="9a218-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9a218-126">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="9a218-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="9a218-127">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="9a218-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="9a218-128">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="9a218-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9a218-129">-Text: использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="9a218-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9a218-130">-MTOM: используйте кодировщик обмена сообщениями, механизм передачи сообщений 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9a218-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9a218-131">Значение по умолчанию - Text.</span><span class="sxs-lookup"><span data-stu-id="9a218-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="9a218-132">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="9a218-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="9a218-133">Имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="9a218-133">The configuration name of the binding.</span></span> <span data-ttu-id="9a218-134">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="9a218-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9a218-135">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="9a218-135">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9a218-136">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9a218-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="9a218-137">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="9a218-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9a218-138">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a218-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a218-139">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a218-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="9a218-140">Универсальный код ресурса (URI), определяющий расположение примечания о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="9a218-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="9a218-141">Версия текущего примечания о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="9a218-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="9a218-142">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a218-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="9a218-143">Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="9a218-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="9a218-144">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="9a218-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="9a218-145">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="9a218-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9a218-146">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a218-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a218-147">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9a218-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="9a218-148">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="9a218-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9a218-149">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9a218-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9a218-150">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9a218-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="9a218-151">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="9a218-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9a218-152">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="9a218-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9a218-153">-BigEndianUnicode: кодировка с обратным порядком байтов Юникода.</span><span class="sxs-lookup"><span data-stu-id="9a218-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="9a218-154">-Unicode: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="9a218-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9a218-155">-UTF8:8-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="9a218-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="9a218-156">По умолчанию используется значение UTF8.</span><span class="sxs-lookup"><span data-stu-id="9a218-156">The default is UTF8.</span></span> <span data-ttu-id="9a218-157">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9a218-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="9a218-158">Значение, определяющее, поддерживает ли привязка потоки WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="9a218-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9a218-159">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="9a218-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="9a218-160">Значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a218-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="9a218-161">Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан).</span><span class="sxs-lookup"><span data-stu-id="9a218-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="9a218-162">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="9a218-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9a218-163">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9a218-163">Child Elements</span></span>

|<span data-ttu-id="9a218-164">Элемент</span><span class="sxs-lookup"><span data-stu-id="9a218-164">Element</span></span>|<span data-ttu-id="9a218-165">Описание</span><span class="sxs-lookup"><span data-stu-id="9a218-165">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="9a218-166">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="9a218-166">Defines the security settings for the message.</span></span> <span data-ttu-id="9a218-167">Это элемент типа <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9a218-167">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9a218-168">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9a218-168">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9a218-169">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9a218-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="9a218-170">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="9a218-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9a218-171">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9a218-171">Parent Elements</span></span>

|<span data-ttu-id="9a218-172">Элемент</span><span class="sxs-lookup"><span data-stu-id="9a218-172">Element</span></span>|<span data-ttu-id="9a218-173">Описание</span><span class="sxs-lookup"><span data-stu-id="9a218-173">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="9a218-174">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="9a218-174">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a218-175">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a218-175">Remarks</span></span>

<span data-ttu-id="9a218-176">Федерация - это возможность совместного использования удостоверений между несколькими предприятиями или доверенными доменами в целях проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="9a218-176">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="9a218-177">Для сопоставления представления идентификации между доверенными доменами используется протокол WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="9a218-177">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="9a218-178">Федеративная привязка HTTP поддерживает безопасность SOAP, а также безопасность в смешанном режиме, но она не поддерживает безопасность транспорта.</span><span class="sxs-lookup"><span data-stu-id="9a218-178">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="9a218-179">Службы, настроенные с использованием этой привязки, должны использовать транспорт HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a218-179">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="9a218-180">Дополнительные сведения см. на веб-сайте [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9a218-180">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a218-181">Пример</span><span class="sxs-lookup"><span data-stu-id="9a218-181">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9a218-182">См. также</span><span class="sxs-lookup"><span data-stu-id="9a218-182">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="9a218-183">Привязки</span><span class="sxs-lookup"><span data-stu-id="9a218-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a218-184">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="9a218-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9a218-185">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9a218-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
