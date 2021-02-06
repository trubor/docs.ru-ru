---
description: 'Дополнительные сведения: <byteStreamMessageEncoding>'
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 9cbb4eacb1a960481ee262db662160b5a342e27f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639293"
---
# \<byteStreamMessageEncoding>

<span data-ttu-id="e22ac-102">Указывает кодировку сообщения в виде потока байтов, также позволяет указать кодировку символов.</span><span class="sxs-lookup"><span data-stu-id="e22ac-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="e22ac-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e22ac-103">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e22ac-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e22ac-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e22ac-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e22ac-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e22ac-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e22ac-106">Attributes</span></span>  
  
|<span data-ttu-id="e22ac-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e22ac-107">Attribute</span></span>|<span data-ttu-id="e22ac-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e22ac-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e22ac-109">messageVersion</span><span class="sxs-lookup"><span data-stu-id="e22ac-109">messageVersion</span></span>|<span data-ttu-id="e22ac-110">Задает версию SOAP сообщений, отправленных с помощью привязки.</span><span class="sxs-lookup"><span data-stu-id="e22ac-110">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="e22ac-111">Этому свойству может быть задано только значение версии сообщения <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="e22ac-111">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="e22ac-112">Составной кодировщик сообщений потока байтов не поддерживает другие версии сообщений.</span><span class="sxs-lookup"><span data-stu-id="e22ac-112">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="e22ac-113">Это атрибут типа <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="e22ac-113">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e22ac-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e22ac-114">Child Elements</span></span>  
  
|<span data-ttu-id="e22ac-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="e22ac-115">Element</span></span>|<span data-ttu-id="e22ac-116">Описание</span><span class="sxs-lookup"><span data-stu-id="e22ac-116">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="e22ac-117">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="e22ac-117">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e22ac-118">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e22ac-118">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e22ac-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e22ac-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e22ac-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="e22ac-120">Element</span></span>|<span data-ttu-id="e22ac-121">Описание</span><span class="sxs-lookup"><span data-stu-id="e22ac-121">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e22ac-122">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="e22ac-122">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e22ac-123">См. также</span><span class="sxs-lookup"><span data-stu-id="e22ac-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="e22ac-124">Message Encoding</span><span class="sxs-lookup"><span data-stu-id="e22ac-124">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e22ac-125">Выбор кодировщика сообщений</span><span class="sxs-lookup"><span data-stu-id="e22ac-125">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e22ac-126">Привязки</span><span class="sxs-lookup"><span data-stu-id="e22ac-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e22ac-127">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="e22ac-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e22ac-128">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="e22ac-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
