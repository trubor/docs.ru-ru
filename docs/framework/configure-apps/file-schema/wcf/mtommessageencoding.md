---
description: 'Дополнительные сведения: <mtomMessageEncoding>'
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 37ac0be5f3de84a4c310b8ec2a09ed6f3c4def56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684117"
---
# \<mtomMessageEncoding>

<span data-ttu-id="8102f-102">Определяет метод шифрования и управления версиями сообщений для сообщений, использующих механизм оптимизации передачи сообщений SOAP (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8102f-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="8102f-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8102f-103">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8102f-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8102f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8102f-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8102f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8102f-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8102f-106">Attributes</span></span>  
  
|<span data-ttu-id="8102f-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8102f-107">Attribute</span></span>|<span data-ttu-id="8102f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8102f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8102f-109">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8102f-109">maxBufferSize</span></span>|<span data-ttu-id="8102f-110">Целое число, задающее максимальный допустимый размер буфера.</span><span class="sxs-lookup"><span data-stu-id="8102f-110">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="8102f-111">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8102f-111">maxReadPoolSize</span></span>|<span data-ttu-id="8102f-112">Целое число, задающее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых модулей чтения.</span><span class="sxs-lookup"><span data-stu-id="8102f-112">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="8102f-113">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="8102f-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8102f-114">Значение по умолчанию — 64.</span><span class="sxs-lookup"><span data-stu-id="8102f-114">The default is 64.</span></span>|  
|<span data-ttu-id="8102f-115">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8102f-115">maxWritePoolSize</span></span>|<span data-ttu-id="8102f-116">Целое число, задающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых модулей записи.</span><span class="sxs-lookup"><span data-stu-id="8102f-116">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="8102f-117">Пул больших размеров повышает устойчивость системы при всплесках активности за счет большего рабочего набора.</span><span class="sxs-lookup"><span data-stu-id="8102f-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8102f-118">Значение по умолчанию равно 16.</span><span class="sxs-lookup"><span data-stu-id="8102f-118">The default is 16.</span></span>|  
|<span data-ttu-id="8102f-119">messageVersion</span><span class="sxs-lookup"><span data-stu-id="8102f-119">messageVersion</span></span>|<span data-ttu-id="8102f-120">Задает версию SOAP сообщений, отправленных с помощью привязки.</span><span class="sxs-lookup"><span data-stu-id="8102f-120">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8102f-121">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="8102f-121">Valid values are</span></span><br /><br /> <span data-ttu-id="8102f-122">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="8102f-122">-   Soap11Addressing1</span></span><br /><span data-ttu-id="8102f-123">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="8102f-123">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="8102f-124">Значение по умолчанию - Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="8102f-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="8102f-125">Это атрибут типа <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="8102f-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="8102f-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="8102f-126">writeEncoding</span></span>|<span data-ttu-id="8102f-127">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="8102f-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8102f-128">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="8102f-128">Valid values are</span></span><br /><br /> <span data-ttu-id="8102f-129">-Уникодефффетекстенкодинг: Юникод байтов кодировка</span><span class="sxs-lookup"><span data-stu-id="8102f-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="8102f-130">-Utf16TextEncoding: Кодировка Юникода</span><span class="sxs-lookup"><span data-stu-id="8102f-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="8102f-131">-Utf8TextEncoding: 8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="8102f-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="8102f-132">Значение по умолчанию - Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="8102f-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="8102f-133">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8102f-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8102f-134">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8102f-134">Child Elements</span></span>  
  
|<span data-ttu-id="8102f-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="8102f-135">Element</span></span>|<span data-ttu-id="8102f-136">Описание</span><span class="sxs-lookup"><span data-stu-id="8102f-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="8102f-137">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="8102f-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8102f-138">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8102f-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8102f-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8102f-139">Parent Elements</span></span>  
  
|<span data-ttu-id="8102f-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="8102f-140">Element</span></span>|<span data-ttu-id="8102f-141">Описание</span><span class="sxs-lookup"><span data-stu-id="8102f-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8102f-142">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="8102f-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8102f-143">Remarks</span><span class="sxs-lookup"><span data-stu-id="8102f-143">Remarks</span></span>  

 <span data-ttu-id="8102f-144">Кодирование — это процесс преобразования сообщения в последовательность байтов.</span><span class="sxs-lookup"><span data-stu-id="8102f-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="8102f-145">Декодирование представляет собой обратный процесс.</span><span class="sxs-lookup"><span data-stu-id="8102f-145">Decoding is the reverse process.</span></span> <span data-ttu-id="8102f-146">В Windows Communication Foundation (WCF) имеется три типа кодирования для сообщений SOAP: Text, Binary и MTOM.</span><span class="sxs-lookup"><span data-stu-id="8102f-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="8102f-147">Элемент `MtomMessageEncoding` указывает кодировку символов, управление версиями сообщений и другие параметры для сообщений, использующих кодировку MTOM.</span><span class="sxs-lookup"><span data-stu-id="8102f-147">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="8102f-148">MTOM - это эффективный способ передачи двоичных данных в сообщениях WCF.</span><span class="sxs-lookup"><span data-stu-id="8102f-148">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="8102f-149">Кодировщик MTOM пытается сохранить баланс между эффективностью и совместимостью.</span><span class="sxs-lookup"><span data-stu-id="8102f-149">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="8102f-150">При кодировке MTOM большая часть XML-кода передается в текстовой форме, однако выполняется оптимизация больших блоков двоичных данных путем передачи их в исходном виде, без преобразования их в базовый формат base64.</span><span class="sxs-lookup"><span data-stu-id="8102f-150">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8102f-151">Пример</span><span class="sxs-lookup"><span data-stu-id="8102f-151">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="8102f-152">См. также</span><span class="sxs-lookup"><span data-stu-id="8102f-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="8102f-153">Message Encoding</span><span class="sxs-lookup"><span data-stu-id="8102f-153">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="8102f-154">Выбор кодировщика сообщений</span><span class="sxs-lookup"><span data-stu-id="8102f-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8102f-155">Привязки</span><span class="sxs-lookup"><span data-stu-id="8102f-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8102f-156">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="8102f-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8102f-157">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="8102f-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
