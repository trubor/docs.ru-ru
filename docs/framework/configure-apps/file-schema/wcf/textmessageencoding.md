---
description: 'Дополнительные сведения: <textMessageEncoding>'
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: a8c7820b2e22152850d6d21c5091e328feb7a9f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786607"
---
# \<textMessageEncoding>

<span data-ttu-id="fea24-102">Указывает кодировку символов и управление версиями сообщений для текстовых сообщений XML.</span><span class="sxs-lookup"><span data-stu-id="fea24-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="fea24-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fea24-103">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fea24-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fea24-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fea24-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fea24-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fea24-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fea24-106">Attributes</span></span>  
  
|<span data-ttu-id="fea24-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fea24-107">Attribute</span></span>|<span data-ttu-id="fea24-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fea24-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fea24-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="fea24-109">maxReadPoolSize</span></span>|<span data-ttu-id="fea24-110">Целое число, задающее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых модулей чтения.</span><span class="sxs-lookup"><span data-stu-id="fea24-110">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="fea24-111">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="fea24-111">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="fea24-112">Значение по умолчанию — 64.</span><span class="sxs-lookup"><span data-stu-id="fea24-112">The default is 64.</span></span>|  
|<span data-ttu-id="fea24-113">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="fea24-113">maxWritePoolSize</span></span>|<span data-ttu-id="fea24-114">Целое число, задающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых модулей записи.</span><span class="sxs-lookup"><span data-stu-id="fea24-114">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="fea24-115">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="fea24-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="fea24-116">Значение по умолчанию равно 16.</span><span class="sxs-lookup"><span data-stu-id="fea24-116">The default is 16.</span></span>|  
|<span data-ttu-id="fea24-117">messageVersion</span><span class="sxs-lookup"><span data-stu-id="fea24-117">messageVersion</span></span>|<span data-ttu-id="fea24-118">Задает версию SOAP сообщений, отправленных с помощью привязки.</span><span class="sxs-lookup"><span data-stu-id="fea24-118">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="fea24-119">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="fea24-119">Valid values are</span></span><br /><br /> <span data-ttu-id="fea24-120">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="fea24-120">-   Soap11Addressing10</span></span><br /><span data-ttu-id="fea24-121">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="fea24-121">-   Soap12Addressing10</span></span><br /><span data-ttu-id="fea24-122">-Soap11</span><span class="sxs-lookup"><span data-stu-id="fea24-122">-   Soap11</span></span><br /><span data-ttu-id="fea24-123">-Soap12</span><span class="sxs-lookup"><span data-stu-id="fea24-123">-  Soap12</span></span><br /><br /><span data-ttu-id="fea24-124">Значение по умолчанию - Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="fea24-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="fea24-125">Это атрибут типа <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="fea24-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="fea24-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="fea24-126">writeEncoding</span></span>|<span data-ttu-id="fea24-127">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="fea24-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="fea24-128">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="fea24-128">Valid values are</span></span><br /><br /> <span data-ttu-id="fea24-129">-Уникодефффетекстенкодинг: Юникод байтов кодировка</span><span class="sxs-lookup"><span data-stu-id="fea24-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="fea24-130">-Utf16TextEncoding: Кодировка Юникода</span><span class="sxs-lookup"><span data-stu-id="fea24-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="fea24-131">-Utf8TextEncoding: 8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="fea24-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="fea24-132">Значение по умолчанию - Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="fea24-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="fea24-133">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="fea24-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fea24-134">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fea24-134">Child Elements</span></span>  
  
|<span data-ttu-id="fea24-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="fea24-135">Element</span></span>|<span data-ttu-id="fea24-136">Описание</span><span class="sxs-lookup"><span data-stu-id="fea24-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="fea24-137">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="fea24-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fea24-138">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fea24-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fea24-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fea24-139">Parent Elements</span></span>  
  
|<span data-ttu-id="fea24-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="fea24-140">Element</span></span>|<span data-ttu-id="fea24-141">Описание</span><span class="sxs-lookup"><span data-stu-id="fea24-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fea24-142">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="fea24-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea24-143">Remarks</span><span class="sxs-lookup"><span data-stu-id="fea24-143">Remarks</span></span>  

 <span data-ttu-id="fea24-144">Кодирование — это процесс преобразования сообщения в последовательность байтов.</span><span class="sxs-lookup"><span data-stu-id="fea24-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="fea24-145">Декодирование представляет собой обратный процесс.</span><span class="sxs-lookup"><span data-stu-id="fea24-145">Decoding is the reverse process.</span></span> <span data-ttu-id="fea24-146">В Windows Communication Foundation (WCF) имеется три типа кодирования для сообщений SOAP: Text, Binary и MTOM.</span><span class="sxs-lookup"><span data-stu-id="fea24-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="fea24-147">Кодировка текста, представленная элементом `textMessageEncoding`, дает наибольшие возможности взаимодействия, но является наименее эффективной для сообщений XML.</span><span class="sxs-lookup"><span data-stu-id="fea24-147">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="fea24-148">Кодировщик текста создает текстовые сообщения в сети.</span><span class="sxs-lookup"><span data-stu-id="fea24-148">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="fea24-149">Сообщения, созданные этим кодировщиком, подходят для взаимодействия на базе +WS-\*.</span><span class="sxs-lookup"><span data-stu-id="fea24-149">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="fea24-150">Веб-служба или клиент веб-службы в общем могут понимать XML в текстовом виде.</span><span class="sxs-lookup"><span data-stu-id="fea24-150">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="fea24-151">Однако передача больших блоков двоичных данных в виде текста является наименее эффективным методом для кодировки сообщений XML.</span><span class="sxs-lookup"><span data-stu-id="fea24-151">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea24-152">Пример</span><span class="sxs-lookup"><span data-stu-id="fea24-152">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="fea24-153">См. также</span><span class="sxs-lookup"><span data-stu-id="fea24-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="fea24-154">Выбор кодировщика сообщений</span><span class="sxs-lookup"><span data-stu-id="fea24-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="fea24-155">Message Encoding</span><span class="sxs-lookup"><span data-stu-id="fea24-155">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="fea24-156">Привязки</span><span class="sxs-lookup"><span data-stu-id="fea24-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fea24-157">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="fea24-157">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fea24-158">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="fea24-158">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
