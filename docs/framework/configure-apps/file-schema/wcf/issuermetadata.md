---
description: 'Дополнительные сведения: <issuerMetadata>'
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 86671b6b704f5753cf4bd45c2dfd90a368070b22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725536"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="6d53f-102">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d53f-102">Syntax</span></span>  
  
```xml  
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
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d53f-103">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6d53f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6d53f-104">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6d53f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d53f-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6d53f-105">Attributes</span></span>  
  
|<span data-ttu-id="6d53f-106">Атрибут</span><span class="sxs-lookup"><span data-stu-id="6d53f-106">Attribute</span></span>|<span data-ttu-id="6d53f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6d53f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d53f-108">address</span><span class="sxs-lookup"><span data-stu-id="6d53f-108">address</span></span>|<span data-ttu-id="6d53f-109">Обязательный атрибут элемента `string`.</span><span class="sxs-lookup"><span data-stu-id="6d53f-109">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="6d53f-110">Задает адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="6d53f-110">Specifies the address of the endpoint.</span></span> <span data-ttu-id="6d53f-111">Адрес должен быть абсолютным универсальным кодом ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="6d53f-111">The address must be an absolute URI.</span></span> <span data-ttu-id="6d53f-112">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="6d53f-112">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d53f-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6d53f-113">Child Elements</span></span>  
  
|<span data-ttu-id="6d53f-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="6d53f-114">Element</span></span>|<span data-ttu-id="6d53f-115">Описание</span><span class="sxs-lookup"><span data-stu-id="6d53f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="6d53f-116">Коллекция заголовков адреса.</span><span class="sxs-lookup"><span data-stu-id="6d53f-116">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="6d53f-117">Удостоверение, обеспечивающее проверку подлинности конечной точки другими конечными точками, которые обмениваются с ней сообщениями.</span><span class="sxs-lookup"><span data-stu-id="6d53f-117">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d53f-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6d53f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6d53f-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="6d53f-119">Element</span></span>|<span data-ttu-id="6d53f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="6d53f-120">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="6d53f-121">Определяет параметры безопасности на уровне сообщений для [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="6d53f-121">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d53f-122">См. также</span><span class="sxs-lookup"><span data-stu-id="6d53f-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="6d53f-123">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="6d53f-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6d53f-124">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="6d53f-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6d53f-125">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="6d53f-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6d53f-126">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="6d53f-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
