---
description: 'Дополнительные сведения <security> о: <peerTransport>'
title: <security> из <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 592f886377a2d5f2008be900a9e7586385fb3782
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786828"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="36b2c-103">\<security> из \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="36b2c-103">\<security> of \<peerTransport></span></span>

<span data-ttu-id="36b2c-104">Содержит параметры безопасности, связанные с одноранговым каналом, включая используемый тип проверки подлинности и механизм безопасности, применяемый при транспортировке сообщений.</span><span class="sxs-lookup"><span data-stu-id="36b2c-104">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="36b2c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36b2c-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36b2c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="36b2c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="36b2c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="36b2c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36b2c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="36b2c-108">Attributes</span></span>  
  
|<span data-ttu-id="36b2c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="36b2c-109">Attribute</span></span>|<span data-ttu-id="36b2c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="36b2c-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="36b2c-111">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="36b2c-111">Specifies the type of security to be applied.</span></span> <span data-ttu-id="36b2c-112">Значение по умолчанию - Message.</span><span class="sxs-lookup"><span data-stu-id="36b2c-112">The default value is Message.</span></span> <span data-ttu-id="36b2c-113">Это атрибут типа <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="36b2c-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="36b2c-114">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="36b2c-114">mode Attribute</span></span>  
  
|<span data-ttu-id="36b2c-115">Значение</span><span class="sxs-lookup"><span data-stu-id="36b2c-115">Value</span></span>|<span data-ttu-id="36b2c-116">Описание</span><span class="sxs-lookup"><span data-stu-id="36b2c-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="36b2c-117">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="36b2c-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="36b2c-118">Безопасность обеспечивается с помощью протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="36b2c-118">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="36b2c-119">Механизм безопасности SOAP обеспечивает целостность, конфиденциальность и проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="36b2c-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="36b2c-120">HTTPS обеспечивает конфиденциальность и проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="36b2c-120">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="36b2c-121">Сообщения SOAP предоставляют различные типы учетных данных.</span><span class="sxs-lookup"><span data-stu-id="36b2c-121">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36b2c-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="36b2c-122">Child Elements</span></span>  
  
|<span data-ttu-id="36b2c-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="36b2c-123">Element</span></span>|<span data-ttu-id="36b2c-124">Описание</span><span class="sxs-lookup"><span data-stu-id="36b2c-124">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="36b2c-125">Определяет одноранговый транспорт для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="36b2c-125">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="36b2c-126">Этот элемент имеет атрибут `clientCredentialType`, который задает учетные данные для использования при взаимодействии со службой.</span><span class="sxs-lookup"><span data-stu-id="36b2c-126">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="36b2c-127">Это атрибут типа <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="36b2c-127">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="36b2c-128">Это элемент типа <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="36b2c-128">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36b2c-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="36b2c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="36b2c-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="36b2c-130">Element</span></span>|<span data-ttu-id="36b2c-131">Описание</span><span class="sxs-lookup"><span data-stu-id="36b2c-131">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="36b2c-132">Определяет одноранговый транспорт для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="36b2c-132">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36b2c-133">См. также</span><span class="sxs-lookup"><span data-stu-id="36b2c-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="36b2c-134">Безопасность транспорта</span><span class="sxs-lookup"><span data-stu-id="36b2c-134">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="36b2c-135">Транспорты</span><span class="sxs-lookup"><span data-stu-id="36b2c-135">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="36b2c-136">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="36b2c-136">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="36b2c-137">Привязки</span><span class="sxs-lookup"><span data-stu-id="36b2c-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="36b2c-138">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="36b2c-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="36b2c-139">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="36b2c-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
