---
description: 'Дополнительные сведения: <netNamedPipeBinding>'
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b6ee706337d3dd33c653bfa0d2b91f4eda0fcea5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683948"
---
# \<netNamedPipeBinding>

<span data-ttu-id="a90b6-102">Это безопасная и надежная привязка, оптимизированная для обмена данными между процессами компьютера.</span><span class="sxs-lookup"><span data-stu-id="a90b6-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="a90b6-103">По умолчанию она создает стек связи среды выполнения, использующей WS-ReliableMessaging для обеспечения надежности, режим безопасности транспорта в целях безопасности передачи, именованные каналы для доставки сообщений, а также кодирование двоичных сообщений.</span><span class="sxs-lookup"><span data-stu-id="a90b6-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="a90b6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a90b6-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a90b6-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a90b6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a90b6-106">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a90b6-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a90b6-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a90b6-107">Attributes</span></span>  
  
|<span data-ttu-id="a90b6-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a90b6-108">Attribute</span></span>|<span data-ttu-id="a90b6-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a90b6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a90b6-110">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a90b6-110">closeTimeout</span></span>|<span data-ttu-id="a90b6-111">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="a90b6-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a90b6-112">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a90b6-113">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a90b6-113">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a90b6-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a90b6-114">hostNameComparisonMode</span></span>|<span data-ttu-id="a90b6-115">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="a90b6-115">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a90b6-116">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="a90b6-116">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a90b6-117">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="a90b6-117">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="a90b6-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a90b6-118">maxBufferPoolSize</span></span>|<span data-ttu-id="a90b6-119">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a90b6-120">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="a90b6-120">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="a90b6-121">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="a90b6-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a90b6-122">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a90b6-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a90b6-123">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="a90b6-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a90b6-124">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="a90b6-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="a90b6-125">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a90b6-125">maxBufferSize</span></span>|<span data-ttu-id="a90b6-126">Положительное целое число, указывающее максимальный размер буфера, используемого для хранения сообщений в памяти (в байтах).</span><span class="sxs-lookup"><span data-stu-id="a90b6-126">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="a90b6-127">Если буфер полон, избыточные данные остаются в основном сокете до тех пор, пока буфер не освободится.</span><span class="sxs-lookup"><span data-stu-id="a90b6-127">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="a90b6-128">Данное значение не может быть меньше значения атрибута `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-128">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="a90b6-129">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="a90b6-129">The default is 65536.</span></span> <span data-ttu-id="a90b6-130">Для получения дополнительной информации см. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-130">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="a90b6-131">maxConnections</span><span class="sxs-lookup"><span data-stu-id="a90b6-131">maxConnections</span></span>|<span data-ttu-id="a90b6-132">Целое число, указывающее максимальное число входящих и исходящих подключений, которые будут созданы/приняты службой.</span><span class="sxs-lookup"><span data-stu-id="a90b6-132">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="a90b6-133">Входящие и исходящие подключения считаются относительно отдельного предела, определенного этим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="a90b6-133">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="a90b6-134">Входящие соединения сверх указанного предела помещаются в очередь и обрабатываются по мере освобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a90b6-134">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="a90b6-135">Исходящие соединения сверх указанного предела помещаются в очередь и обрабатываются по мере освобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a90b6-135">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="a90b6-136">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="a90b6-136">The default is 10.</span></span>|  
|<span data-ttu-id="a90b6-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a90b6-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="a90b6-138">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a90b6-139">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="a90b6-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="a90b6-140">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a90b6-141">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="a90b6-141">The default is 65536.</span></span>|  
|<span data-ttu-id="a90b6-142">name</span><span class="sxs-lookup"><span data-stu-id="a90b6-142">name</span></span>|<span data-ttu-id="a90b6-143">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a90b6-144">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a90b6-145">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="a90b6-145">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a90b6-146">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a90b6-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="a90b6-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a90b6-147">openTimeout</span></span>|<span data-ttu-id="a90b6-148">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="a90b6-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a90b6-149">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a90b6-150">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a90b6-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a90b6-151">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a90b6-151">receiveTimeout</span></span>|<span data-ttu-id="a90b6-152">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="a90b6-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a90b6-153">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a90b6-154">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a90b6-154">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="a90b6-155">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a90b6-155">sendTimeout</span></span>|<span data-ttu-id="a90b6-156">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a90b6-157">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a90b6-158">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a90b6-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a90b6-159">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a90b6-159">transactionFlow</span></span>|<span data-ttu-id="a90b6-160">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="a90b6-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a90b6-161">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-161">The default is `false`.</span></span>|  
|<span data-ttu-id="a90b6-162">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a90b6-162">transactionProtocol</span></span>|<span data-ttu-id="a90b6-163">Указывает протокол транзакций, используемый с данной привязкой.</span><span class="sxs-lookup"><span data-stu-id="a90b6-163">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="a90b6-164">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="a90b6-164">Valid values are</span></span><br /><br /> <span data-ttu-id="a90b6-165">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="a90b6-165">-   OleTransactions</span></span><br /><span data-ttu-id="a90b6-166">— WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="a90b6-166">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="a90b6-167">Значение по умолчанию - OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="a90b6-167">The default is OleTransactions.</span></span> <span data-ttu-id="a90b6-168">Это атрибут типа <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-168">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="a90b6-169">transferMode</span><span class="sxs-lookup"><span data-stu-id="a90b6-169">transferMode</span></span>|<span data-ttu-id="a90b6-170">Значение <xref:System.ServiceModel.TransferMode>, которое указывает, следует ли помещать сообщения в буфер или передавать их потоком по запросу или отклику.</span><span class="sxs-lookup"><span data-stu-id="a90b6-170">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a90b6-171">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a90b6-171">Child Elements</span></span>  
  
|<span data-ttu-id="a90b6-172">Элемент</span><span class="sxs-lookup"><span data-stu-id="a90b6-172">Element</span></span>|<span data-ttu-id="a90b6-173">Описание</span><span class="sxs-lookup"><span data-stu-id="a90b6-173">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="a90b6-174">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-174">Defines the security settings for the binding.</span></span> <span data-ttu-id="a90b6-175">Это элемент типа <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-175">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="a90b6-176">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a90b6-177">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a90b6-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a90b6-178">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a90b6-178">Parent Elements</span></span>  
  
|<span data-ttu-id="a90b6-179">Элемент</span><span class="sxs-lookup"><span data-stu-id="a90b6-179">Element</span></span>|<span data-ttu-id="a90b6-180">Описание</span><span class="sxs-lookup"><span data-stu-id="a90b6-180">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="a90b6-181">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="a90b6-181">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a90b6-182">Remarks</span><span class="sxs-lookup"><span data-stu-id="a90b6-182">Remarks</span></span>  

 <span data-ttu-id="a90b6-183">`NetNamedPipeBinding` создает стек связи среды выполнения по умолчанию, использующий режим безопасности транспорта, именованные каналы для доставки сообщений, а также кодирование двоичных сообщений.</span><span class="sxs-lookup"><span data-stu-id="a90b6-183">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="a90b6-184">Эта привязка предоставляется системой Windows Communication Foundation (WCF) в качестве средства обмена данными на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a90b6-184">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="a90b6-185">Она также поддерживает транзакции.</span><span class="sxs-lookup"><span data-stu-id="a90b6-185">It also supports transactions.</span></span>  
  
 <span data-ttu-id="a90b6-186">Конфигурация по умолчанию для `NetNamedPipeBinding` аналогична конфигурации, предоставленной `NetTcpBinding`, но она существенно проще, поскольку реализация WCF предназначена только для использования в пределах компьютера и, следовательно, содержит меньшее число предоставляемых функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="a90b6-186">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="a90b6-187">Наиболее существенным отличием является то, что параметр `securityMode` содержит только значения `None` и `Transport`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-187">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="a90b6-188">Поддержка безопасности SOAP не предусмотрена.</span><span class="sxs-lookup"><span data-stu-id="a90b6-188">SOAP security support is not an included option.</span></span> <span data-ttu-id="a90b6-189">Режим безопасности настраивается с помощью дополнительного атрибута `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a90b6-190">Пример</span><span class="sxs-lookup"><span data-stu-id="a90b6-190">Example</span></span>  

 <span data-ttu-id="a90b6-191">В следующем примере демонстрируется применение привязки NetNamedPipeBinding, обеспечивающей обмен данными между процессами одного компьютера.</span><span class="sxs-lookup"><span data-stu-id="a90b6-191">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="a90b6-192">Использование именованных каналов для обмена данными между компьютерами не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="a90b6-192">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="a90b6-193">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="a90b6-193">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="a90b6-194">Тип привязки указывается в атрибуте `binding` элемента `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-194">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="a90b6-195">Чтобы настроить привязку netNamedPipeBinding и изменить некоторые ее параметры, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="a90b6-195">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="a90b6-196">Конечная точка должна ссылаться на конфигурацию привязки по имени с атрибутом `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a90b6-196">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="a90b6-197">В этом примере конфигурации привязки присвоено имя «Binding1».</span><span class="sxs-lookup"><span data-stu-id="a90b6-197">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="a90b6-198">См. также</span><span class="sxs-lookup"><span data-stu-id="a90b6-198">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="a90b6-199">Привязки</span><span class="sxs-lookup"><span data-stu-id="a90b6-199">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a90b6-200">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="a90b6-200">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a90b6-201">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="a90b6-201">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
