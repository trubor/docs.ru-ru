---
description: 'Дополнительные сведения <security> о: <wsFederationHttpBinding>'
title: <security> из <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c01c7a50b05f1723b3620407eb5e5761bae35cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786802"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="df9dd-103">\<security> из \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="df9dd-103">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="df9dd-104">Определяет параметры безопасности для [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="df9dd-104">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="df9dd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="df9dd-105">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df9dd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="df9dd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="df9dd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="df9dd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df9dd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="df9dd-108">Attributes</span></span>  
  
|<span data-ttu-id="df9dd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="df9dd-109">Attribute</span></span>|<span data-ttu-id="df9dd-110">Описание</span><span class="sxs-lookup"><span data-stu-id="df9dd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df9dd-111">Режим</span><span class="sxs-lookup"><span data-stu-id="df9dd-111">Mode</span></span>|<span data-ttu-id="df9dd-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="df9dd-112">Optional.</span></span> <span data-ttu-id="df9dd-113">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="df9dd-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="df9dd-114">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="df9dd-114">The default value is `Message`.</span></span> <span data-ttu-id="df9dd-115">Это атрибут типа <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="df9dd-115">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="df9dd-116">Атрибут Mode</span><span class="sxs-lookup"><span data-stu-id="df9dd-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="df9dd-117">Значение</span><span class="sxs-lookup"><span data-stu-id="df9dd-117">Value</span></span>|<span data-ttu-id="df9dd-118">Описание</span><span class="sxs-lookup"><span data-stu-id="df9dd-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="df9dd-119">None</span><span class="sxs-lookup"><span data-stu-id="df9dd-119">None</span></span>|<span data-ttu-id="df9dd-120">Во время передачи сообщение SOAP не защищено.</span><span class="sxs-lookup"><span data-stu-id="df9dd-120">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="df9dd-121">Сообщение</span><span class="sxs-lookup"><span data-stu-id="df9dd-121">Message</span></span>|<span data-ttu-id="df9dd-122">Целостность, конфиденциальность, проверка подлинности сервера и проверка подлинности клиента обеспечиваются с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="df9dd-122">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="df9dd-123">По умолчанию текст сообщений шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="df9dd-123">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="df9dd-124">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="df9dd-124">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="df9dd-125">Проверка подлинности клиента осуществляется с использованием маркера, выданного клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="df9dd-125">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="df9dd-126">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="df9dd-126">TransportWithMessageCredential</span></span>|<span data-ttu-id="df9dd-127">Целостность, конфиденциальность и проверка подлинности сервера обеспечиваются с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="df9dd-127">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="df9dd-128">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="df9dd-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="df9dd-129">Проверка подлинности клиента выполняется с помощью средств безопасности сообщений SOAP и основана на маркере, выданном клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="df9dd-129">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df9dd-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="df9dd-130">Child Elements</span></span>  
  
|<span data-ttu-id="df9dd-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="df9dd-131">Element</span></span>|<span data-ttu-id="df9dd-132">Описание</span><span class="sxs-lookup"><span data-stu-id="df9dd-132">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="df9dd-133">Определяет параметры безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="df9dd-133">Defines the settings for the message-level security.</span></span> <span data-ttu-id="df9dd-134">Это элемент типа <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="df9dd-134">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df9dd-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="df9dd-135">Parent Elements</span></span>  
  
|<span data-ttu-id="df9dd-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="df9dd-136">Element</span></span>|<span data-ttu-id="df9dd-137">Описание</span><span class="sxs-lookup"><span data-stu-id="df9dd-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="df9dd-138">Определяет все возможности привязки [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="df9dd-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df9dd-139">См. также</span><span class="sxs-lookup"><span data-stu-id="df9dd-139">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="df9dd-140">Практическое руководство. Создание WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="df9dd-140">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="df9dd-141">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="df9dd-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="df9dd-142">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="df9dd-142">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="df9dd-143">Привязки</span><span class="sxs-lookup"><span data-stu-id="df9dd-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="df9dd-144">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="df9dd-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="df9dd-145">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="df9dd-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
