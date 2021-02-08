---
description: 'Дополнительные сведения <security> о: <netPeerBinding>'
title: <security> из <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: f67cfa445a5a605b99783cfd67dd1bae6e17b51e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786841"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="d374a-103">\<security> из \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="d374a-103">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="d374a-104">Определяет параметры безопасности [\<netPeerTcpBinding>](netpeertcpbinding.md) , включая тип используемой проверки подлинности и безопасность, используемую для транспорта сообщений.</span><span class="sxs-lookup"><span data-stu-id="d374a-104">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d374a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d374a-105">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d374a-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d374a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d374a-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d374a-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d374a-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d374a-108">Attributes</span></span>  
  
|<span data-ttu-id="d374a-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d374a-109">Attribute</span></span>|<span data-ttu-id="d374a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d374a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d374a-111">mode</span><span class="sxs-lookup"><span data-stu-id="d374a-111">mode</span></span>|<span data-ttu-id="d374a-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="d374a-112">Optional.</span></span> <span data-ttu-id="d374a-113">Указывает тип безопасности, используемый одноранговыми узлами, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="d374a-113">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="d374a-114">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="d374a-114">The default value is `Message`.</span></span> <span data-ttu-id="d374a-115">Это атрибут типа <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d374a-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d374a-116">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="d374a-116">mode Attribute</span></span>  
  
|<span data-ttu-id="d374a-117">Значение</span><span class="sxs-lookup"><span data-stu-id="d374a-117">Value</span></span>|<span data-ttu-id="d374a-118">Описание</span><span class="sxs-lookup"><span data-stu-id="d374a-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d374a-119">Сообщение</span><span class="sxs-lookup"><span data-stu-id="d374a-119">Message</span></span>|<span data-ttu-id="d374a-120">Механизм безопасности SOAP обеспечивает целостность, конфиденциальность и проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="d374a-120">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="d374a-121">None</span><span class="sxs-lookup"><span data-stu-id="d374a-121">None</span></span>|<span data-ttu-id="d374a-122">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="d374a-122">Security is disabled.</span></span>|  
|<span data-ttu-id="d374a-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="d374a-123">Transport</span></span>|<span data-ttu-id="d374a-124">Безопасность обеспечивается с помощью протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d374a-124">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="d374a-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d374a-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="d374a-126">HTTPS обеспечивает конфиденциальность и проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="d374a-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="d374a-127">Сообщения SOAP предоставляют различные типы учетных данных.</span><span class="sxs-lookup"><span data-stu-id="d374a-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d374a-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d374a-128">Child Elements</span></span>  
  
|<span data-ttu-id="d374a-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="d374a-129">Element</span></span>|<span data-ttu-id="d374a-130">Описание</span><span class="sxs-lookup"><span data-stu-id="d374a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="d374a-131">Определяет тип транспорта для безопасных сообщений, отправленных одноранговыми узлами, настроенными с помощью этой привязки.</span><span class="sxs-lookup"><span data-stu-id="d374a-131">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="d374a-132">Это элемент типа <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d374a-132">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d374a-133">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d374a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d374a-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="d374a-134">Element</span></span>|<span data-ttu-id="d374a-135">Описание</span><span class="sxs-lookup"><span data-stu-id="d374a-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d374a-136">Определяет все возможности привязки [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d374a-136">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d374a-137">Remarks</span><span class="sxs-lookup"><span data-stu-id="d374a-137">Remarks</span></span>  

 <span data-ttu-id="d374a-138">Безопасность может определяться как на уровне сообщений, так и на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="d374a-138">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d374a-139">См. также</span><span class="sxs-lookup"><span data-stu-id="d374a-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="d374a-140">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d374a-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d374a-141">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="d374a-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d374a-142">Привязки</span><span class="sxs-lookup"><span data-stu-id="d374a-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d374a-143">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="d374a-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d374a-144">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d374a-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
