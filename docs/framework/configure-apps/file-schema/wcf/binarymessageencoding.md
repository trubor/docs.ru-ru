---
description: 'Дополнительные сведения: <binaryMessageEncoding>'
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 910b8b70bab40c1eb099ed2b54c0545e73e96c6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639501"
---
# \<binaryMessageEncoding>

<span data-ttu-id="0a9ff-102">Определяет кодировщик двоичных сообщений, кодирующий сообщения Windows Communication Foundation (WCF) в двоичном формате в сети.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="0a9ff-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a9ff-103">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a9ff-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0a9ff-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0a9ff-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a9ff-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0a9ff-106">Attributes</span></span>  
  
|<span data-ttu-id="0a9ff-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0a9ff-107">Attribute</span></span>|<span data-ttu-id="0a9ff-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0a9ff-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a9ff-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="0a9ff-109">maxReadPoolSize</span></span>|<span data-ttu-id="0a9ff-110">Целое число, определяющее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых средств чтения.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-110">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="0a9ff-111">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-111">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a9ff-112">Значение по умолчанию — 64.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-112">The default is 64.</span></span>|  
|<span data-ttu-id="0a9ff-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="0a9ff-113">maxSessionSize</span></span>|<span data-ttu-id="0a9ff-114">Положительное целое число, задающее размер буфера, используемого для кодирования (в байтах).</span><span class="sxs-lookup"><span data-stu-id="0a9ff-114">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="0a9ff-115">Буфер большего размера повышает скорость кодирования за счет размера рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-115">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="0a9ff-116">Значение по умолчанию — 2048.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-116">The default is 2048.</span></span>|  
|<span data-ttu-id="0a9ff-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="0a9ff-117">maxWritePoolSize</span></span>|<span data-ttu-id="0a9ff-118">Целое число, обозначающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых средств записи.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-118">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="0a9ff-119">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a9ff-120">Значение по умолчанию равно 16.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-120">The default is 16.</span></span>|  
|<span data-ttu-id="0a9ff-121">messageVersion</span><span class="sxs-lookup"><span data-stu-id="0a9ff-121">messageVersion</span></span>|<span data-ttu-id="0a9ff-122">Определяет используемые или ожидаемые версии сообщения SOAP и WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-122">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a9ff-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0a9ff-123">Child Elements</span></span>  
  
|<span data-ttu-id="0a9ff-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="0a9ff-124">Element</span></span>|<span data-ttu-id="0a9ff-125">Описание</span><span class="sxs-lookup"><span data-stu-id="0a9ff-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="0a9ff-126">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0a9ff-127">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a9ff-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0a9ff-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0a9ff-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="0a9ff-129">Element</span></span>|<span data-ttu-id="0a9ff-130">Описание</span><span class="sxs-lookup"><span data-stu-id="0a9ff-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0a9ff-131">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a9ff-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a9ff-132">Remarks</span></span>  

 <span data-ttu-id="0a9ff-133">Кодирование — это процесс преобразования сообщения в последовательность байтов.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="0a9ff-134">Декодирование представляет собой обратный процесс.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-134">Decoding is the reverse process.</span></span> <span data-ttu-id="0a9ff-135">В Windows Communication Foundation (WCF) имеется три типа кодирования для сообщений SOAP: Text, Binary и MTOM.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-135">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="0a9ff-136">Элемент `binaryMessageEncoding` указывает двоичный формат .NET для XML и содержит параметры, задающие кодировку символов и версию SOAP и WS-Addressing для использования.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-136">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="0a9ff-137">Кодировщик двоичных сообщений кодирует сообщения Windows Communication Foundation (WCF) в двоичном формате в сети.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-137">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="0a9ff-138">Результатом этой кодировки является очень быстрая передача сообщений, однако вследствие этого теряются возможности взаимодействия, основанные на стандартах WS-\*.</span><span class="sxs-lookup"><span data-stu-id="0a9ff-138">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a9ff-139">Пример</span><span class="sxs-lookup"><span data-stu-id="0a9ff-139">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="0a9ff-140">См. также</span><span class="sxs-lookup"><span data-stu-id="0a9ff-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="0a9ff-141">Message Encoding</span><span class="sxs-lookup"><span data-stu-id="0a9ff-141">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="0a9ff-142">Выбор кодировщика сообщений</span><span class="sxs-lookup"><span data-stu-id="0a9ff-142">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="0a9ff-143">Привязки</span><span class="sxs-lookup"><span data-stu-id="0a9ff-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0a9ff-144">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="0a9ff-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0a9ff-145">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="0a9ff-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
