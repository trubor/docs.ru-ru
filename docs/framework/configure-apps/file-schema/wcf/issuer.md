---
description: 'Дополнительные сведения: <issuer>'
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 771fb8d0bee4e78b598bd20c4d99ec5180f9fb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725640"
---
# \<issuer>

<span data-ttu-id="7232e-102">Задает службу маркеров безопасности, выдающую маркеры безопасности.</span><span class="sxs-lookup"><span data-stu-id="7232e-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="7232e-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7232e-103">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
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
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7232e-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7232e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7232e-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7232e-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7232e-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7232e-106">Attributes</span></span>  
  
|<span data-ttu-id="7232e-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7232e-107">Attribute</span></span>|<span data-ttu-id="7232e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7232e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7232e-109">address</span><span class="sxs-lookup"><span data-stu-id="7232e-109">address</span></span>|<span data-ttu-id="7232e-110">Обязательная строка.</span><span class="sxs-lookup"><span data-stu-id="7232e-110">Required string.</span></span> <span data-ttu-id="7232e-111">URL-адрес для службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="7232e-111">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7232e-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7232e-112">Child Elements</span></span>  
  
|<span data-ttu-id="7232e-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="7232e-113">Element</span></span>|<span data-ttu-id="7232e-114">Описание</span><span class="sxs-lookup"><span data-stu-id="7232e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="7232e-115">Коллекция заголовков адресов для конечных точек, которые может создать конструктор.</span><span class="sxs-lookup"><span data-stu-id="7232e-115">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="7232e-116">При использовании выданного маркера задает параметры, позволяющие клиенту проверить подлинность сервера.</span><span class="sxs-lookup"><span data-stu-id="7232e-116">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7232e-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7232e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7232e-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="7232e-118">Element</span></span>|<span data-ttu-id="7232e-119">Описание</span><span class="sxs-lookup"><span data-stu-id="7232e-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7232e-120">Определяет параметры безопасности на уровне сообщений для [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="7232e-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7232e-121">См. также</span><span class="sxs-lookup"><span data-stu-id="7232e-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="7232e-122">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="7232e-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7232e-123">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="7232e-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7232e-124">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="7232e-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7232e-125">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="7232e-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7232e-126">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="7232e-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7232e-127">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="7232e-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
