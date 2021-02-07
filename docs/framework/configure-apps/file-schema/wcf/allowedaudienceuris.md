---
description: 'Дополнительные сведения: <allowedAudienceUris>'
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: d556a9dcb71222ff52f38e43ad2608e1046e1a60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749978"
---
# \<allowedAudienceUris>

<span data-ttu-id="57353-102">Представляет коллекцию целевых универсальных кодов ресурса (URI), для которых может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы они считались допустимыми для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="57353-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="57353-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="57353-103">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57353-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="57353-104">Attributes and Elements</span></span>  

 <span data-ttu-id="57353-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="57353-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57353-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="57353-106">Attributes</span></span>  

 <span data-ttu-id="57353-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="57353-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57353-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="57353-108">Child Elements</span></span>  
  
|<span data-ttu-id="57353-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="57353-109">Element</span></span>|<span data-ttu-id="57353-110">Описание</span><span class="sxs-lookup"><span data-stu-id="57353-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|<span data-ttu-id="57353-111">Добавляет целевой универсальный код ресурса, для которого может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="57353-111">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57353-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="57353-112">Parent Elements</span></span>  
  
|<span data-ttu-id="57353-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="57353-113">Element</span></span>|<span data-ttu-id="57353-114">Описание</span><span class="sxs-lookup"><span data-stu-id="57353-114">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="57353-115">Задает маркер, выданный в качестве учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="57353-115">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57353-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="57353-116">Remarks</span></span>  

 <span data-ttu-id="57353-117">Данную коллекцию следует использовать в федеративном приложении, которое использует службу маркеров безопасности (STS), выдающую маркеры безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="57353-117">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="57353-118">При выпуске маркера безопасности служба STS также может указать универсальный код ресурса (URI) веб-служб, для которых предназначен маркер безопасности, добавив выражение <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> к маркеру безопасности.</span><span class="sxs-lookup"><span data-stu-id="57353-118">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="57353-119">Это позволяет коду <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> для веб-службы получателя проверить, что выданный маркер безопасности предназначен для данной службы, указав на необходимость выполнения соответствующей проверки. Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="57353-119">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="57353-120">Присвойте атрибуту `audienceUriMode` элемента `<issuedTokenAuthentication>` значение <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> или <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="57353-120">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="57353-121">Задайте набор допустимых универсальных кодов ресурса (URI), добавив их в данную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="57353-121">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="57353-122">Для получения дополнительной информации см. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="57353-122">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="57353-123">Дополнительные сведения об использовании этого элемента конфигурации см. в разделе [как настроить учетные данные на служба федерации](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="57353-123">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57353-124">См. также</span><span class="sxs-lookup"><span data-stu-id="57353-124">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="57353-125">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="57353-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="57353-126">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="57353-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="57353-127">Практическое руководство. Настройка учетных данных службы федерации</span><span class="sxs-lookup"><span data-stu-id="57353-127">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
