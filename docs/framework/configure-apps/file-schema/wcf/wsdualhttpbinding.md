---
description: 'Дополнительные сведения: <wsDualHttpBinding>'
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 14a575d867f2fcd3754d28616e8e2b9d3903f1fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682115"
---
# \<wsDualHttpBinding>

<span data-ttu-id="9f210-102">Определяет безопасную, надежную привязку с возможностью взаимодействия, которая подходит для дуплексных контрактов службы или связи посредством посредников протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="9f210-102">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9f210-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f210-103">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f210-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9f210-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9f210-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9f210-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f210-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9f210-106">Attributes</span></span>  
  
|<span data-ttu-id="9f210-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9f210-107">Attribute</span></span>|<span data-ttu-id="9f210-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9f210-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f210-109">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="9f210-109">bypassProxyOnLocal</span></span>|<span data-ttu-id="9f210-110">Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="9f210-110">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9f210-111">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="9f210-111">The default is `false`.</span></span>|  
|<span data-ttu-id="9f210-112">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="9f210-112">clientBaseAddress</span></span>|<span data-ttu-id="9f210-113">Универсальный код ресурса (URI), задающий базовый адрес, который клиент прослушивает для получения сообщений ответа от службы.</span><span class="sxs-lookup"><span data-stu-id="9f210-113">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="9f210-114">Если значение задано, для прослушивания используется этот адрес (плюс per-channelGUID).</span><span class="sxs-lookup"><span data-stu-id="9f210-114">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="9f210-115">Если значение не задано, базовый адрес клиента создается в соответствии с транспортом.</span><span class="sxs-lookup"><span data-stu-id="9f210-115">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="9f210-116">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="9f210-116">The default is `null`.</span></span>|  
|<span data-ttu-id="9f210-117">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="9f210-117">closeTimeout</span></span>|<span data-ttu-id="9f210-118">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="9f210-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9f210-119">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f210-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f210-120">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f210-120">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9f210-121">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="9f210-121">hostnameComparisonMode</span></span>|<span data-ttu-id="9f210-122">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="9f210-122">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9f210-123">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="9f210-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9f210-124">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="9f210-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="9f210-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9f210-125">maxBufferPoolSize</span></span>|<span data-ttu-id="9f210-126">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-126">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9f210-127">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="9f210-127">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9f210-128">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="9f210-128">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9f210-129">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="9f210-129">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9f210-130">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="9f210-130">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9f210-131">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="9f210-131">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="9f210-132">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9f210-132">maxReceivedMessageSize</span></span>|<span data-ttu-id="9f210-133">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-133">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9f210-134">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="9f210-134">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="9f210-135">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="9f210-135">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9f210-136">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="9f210-136">The default is 65536.</span></span>|  
|<span data-ttu-id="9f210-137">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="9f210-137">messageEncoding</span></span>|<span data-ttu-id="9f210-138">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="9f210-138">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="9f210-139">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="9f210-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9f210-140">-Text: использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="9f210-140">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9f210-141">-MTOM: используйте кодировщик обмена сообщениями, механизм передачи сообщений 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9f210-141">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="9f210-142">— Значение по умолчанию — Text.</span><span class="sxs-lookup"><span data-stu-id="9f210-142">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="9f210-143">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="9f210-143">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="9f210-144">name</span><span class="sxs-lookup"><span data-stu-id="9f210-144">name</span></span>|<span data-ttu-id="9f210-145">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-145">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9f210-146">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-146">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9f210-147">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="9f210-147">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9f210-148">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9f210-148">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="9f210-149">openTimeout</span><span class="sxs-lookup"><span data-stu-id="9f210-149">openTimeout</span></span>|<span data-ttu-id="9f210-150">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="9f210-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9f210-151">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f210-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f210-152">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f210-152">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9f210-153">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="9f210-153">proxyAddress</span></span>|<span data-ttu-id="9f210-154">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f210-154">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="9f210-155">Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="9f210-155">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="9f210-156">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="9f210-156">The default is `null`.</span></span>|  
|<span data-ttu-id="9f210-157">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="9f210-157">receiveTimeout</span></span>|<span data-ttu-id="9f210-158">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="9f210-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9f210-159">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f210-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f210-160">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f210-160">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9f210-161">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="9f210-161">sendTimeout</span></span>|<span data-ttu-id="9f210-162">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="9f210-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9f210-163">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9f210-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9f210-164">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9f210-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9f210-165">textEncoding</span><span class="sxs-lookup"><span data-stu-id="9f210-165">textEncoding</span></span>|<span data-ttu-id="9f210-166">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="9f210-166">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9f210-167">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="9f210-167">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9f210-168">-BigEndianUnicode: Юникод байтов Encoding.</span><span class="sxs-lookup"><span data-stu-id="9f210-168">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="9f210-169">-Unicode: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="9f210-169">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9f210-170">-UTF8:8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="9f210-170">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9f210-171">По умолчанию используется значение UTF8.</span><span class="sxs-lookup"><span data-stu-id="9f210-171">The default is UTF8.</span></span> <span data-ttu-id="9f210-172">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9f210-172">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="9f210-173">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="9f210-173">transactionFlow</span></span>|<span data-ttu-id="9f210-174">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="9f210-174">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9f210-175">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="9f210-175">The default is `false`.</span></span>|  
|<span data-ttu-id="9f210-176">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="9f210-176">useDefaultWebProxy</span></span>|<span data-ttu-id="9f210-177">Логическое значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f210-177">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="9f210-178">Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан).</span><span class="sxs-lookup"><span data-stu-id="9f210-178">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="9f210-179">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="9f210-179">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f210-180">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9f210-180">Child Elements</span></span>  
  
|<span data-ttu-id="9f210-181">Элемент</span><span class="sxs-lookup"><span data-stu-id="9f210-181">Element</span></span>|<span data-ttu-id="9f210-182">Описание</span><span class="sxs-lookup"><span data-stu-id="9f210-182">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="9f210-183">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-183">Defines the security settings for the binding.</span></span> <span data-ttu-id="9f210-184">Это элемент типа <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9f210-184">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9f210-185">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="9f210-185">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9f210-186">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9f210-186">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="9f210-187">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="9f210-187">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f210-188">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9f210-188">Parent Elements</span></span>  
  
|<span data-ttu-id="9f210-189">Элемент</span><span class="sxs-lookup"><span data-stu-id="9f210-189">Element</span></span>|<span data-ttu-id="9f210-190">Описание</span><span class="sxs-lookup"><span data-stu-id="9f210-190">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="9f210-191">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="9f210-191">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f210-192">Remarks</span><span class="sxs-lookup"><span data-stu-id="9f210-192">Remarks</span></span>  

 <span data-ttu-id="9f210-193">Объект `WSDualHttpBinding` предоставляет такую же поддержку протоколам веб-служб, как и объект `WSHttpBinding`, но применяется для дуплексных контрактов.</span><span class="sxs-lookup"><span data-stu-id="9f210-193">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="9f210-194">`WSDualHttpBinding` поддерживает только безопасность SOAP и требует надежного обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="9f210-194">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="9f210-195">Для этой привязки необходимо, чтобы клиент имел открытый универсальный код ресурса (URI), предоставляющий конечную точку обратного вызова для службы.</span><span class="sxs-lookup"><span data-stu-id="9f210-195">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="9f210-196">Это обеспечивается атрибутом `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="9f210-196">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="9f210-197">Двойная привязка предоставляет службе IP-адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="9f210-197">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="9f210-198">Клиенту следует использовать механизм безопасности, чтобы гарантировать, что подключение выполняется только к доверенным службам.</span><span class="sxs-lookup"><span data-stu-id="9f210-198">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="9f210-199">Эту привязку можно использовать для надежной связи посредством одного или нескольких посредников протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="9f210-199">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="9f210-200">По умолчанию эта привязка создает стек времени выполнения с WS-ReliableMessaging для надежности, WS-Security для безопасности и проверки подлинности сообщений, HTTP для доставки сообщений и кодировкой сообщений Text/XML.</span><span class="sxs-lookup"><span data-stu-id="9f210-200">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f210-201">Пример</span><span class="sxs-lookup"><span data-stu-id="9f210-201">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f210-202">См. также</span><span class="sxs-lookup"><span data-stu-id="9f210-202">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="9f210-203">Привязки</span><span class="sxs-lookup"><span data-stu-id="9f210-203">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f210-204">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="9f210-204">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9f210-205">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9f210-205">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
