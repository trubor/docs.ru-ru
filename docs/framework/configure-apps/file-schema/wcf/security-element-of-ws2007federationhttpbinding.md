---
description: 'Дополнительные сведения о: <security> element элемента <ws2007FederationHttpBinding>'
title: Элемент <security> для <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 0caa2c3791c0dc3c8db0d9ee27175a28e52f6baa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683298"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="1b4b7-103">Элемент \<security> для \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1b4b7-103">\<security> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="1b4b7-104">Определяет параметры безопасности [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-104">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="1b4b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b4b7-105">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b4b7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1b4b7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1b4b7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b4b7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1b4b7-108">Attributes</span></span>  
  
|<span data-ttu-id="1b4b7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1b4b7-109">Attribute</span></span>|<span data-ttu-id="1b4b7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="1b4b7-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="1b4b7-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-111">Optional.</span></span> <span data-ttu-id="1b4b7-112">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="1b4b7-113">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-113">The default value is `Message`.</span></span> <span data-ttu-id="1b4b7-114">Это атрибут типа <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1b4b7-115">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="1b4b7-115">mode Attribute</span></span>  
  
|<span data-ttu-id="1b4b7-116">Значение</span><span class="sxs-lookup"><span data-stu-id="1b4b7-116">Value</span></span>|<span data-ttu-id="1b4b7-117">Описание</span><span class="sxs-lookup"><span data-stu-id="1b4b7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b4b7-118">None</span><span class="sxs-lookup"><span data-stu-id="1b4b7-118">None</span></span>|<span data-ttu-id="1b4b7-119">Во время передачи сообщение SOAP не защищено.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="1b4b7-120">Сообщение</span><span class="sxs-lookup"><span data-stu-id="1b4b7-120">Message</span></span>|<span data-ttu-id="1b4b7-121">Целостность, конфиденциальность, проверка подлинности сервера и проверка подлинности клиента обеспечиваются с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="1b4b7-122">По умолчанию текст сообщений шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="1b4b7-123">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-123">The service must be configured with a certificate.</span></span> <span data-ttu-id="1b4b7-124">Проверка подлинности клиента основана на маркере, выданного клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-124">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="1b4b7-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1b4b7-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="1b4b7-126">Целостность, конфиденциальность и проверка подлинности сервера обеспечиваются с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="1b4b7-127">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="1b4b7-128">Проверка подлинности клиента выполняется с помощью средств безопасности сообщений SOAP и основана на маркере, выданном клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b4b7-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1b4b7-129">Child Elements</span></span>  
  
|<span data-ttu-id="1b4b7-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="1b4b7-130">Element</span></span>|<span data-ttu-id="1b4b7-131">Описание</span><span class="sxs-lookup"><span data-stu-id="1b4b7-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="1b4b7-132">Определяет параметры безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="1b4b7-133">Это элемент типа <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b4b7-134">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1b4b7-134">Parent Elements</span></span>  
  
|<span data-ttu-id="1b4b7-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="1b4b7-135">Element</span></span>|<span data-ttu-id="1b4b7-136">Описание</span><span class="sxs-lookup"><span data-stu-id="1b4b7-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1b4b7-137">Определяет все возможности привязки [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1b4b7-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b4b7-138">См. также</span><span class="sxs-lookup"><span data-stu-id="1b4b7-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="1b4b7-139">Практическое руководство. Создание WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1b4b7-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="1b4b7-140">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="1b4b7-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1b4b7-141">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="1b4b7-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="1b4b7-142">Привязки</span><span class="sxs-lookup"><span data-stu-id="1b4b7-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b4b7-143">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="1b4b7-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1b4b7-144">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="1b4b7-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
