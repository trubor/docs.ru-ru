---
description: 'Дополнительные сведения <add> о: <allowedAudienceUris>'
title: <add> из <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: caa61da0ee7e00691213b95e31c943f5d81eea32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782210"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="501d6-103">\<add> из \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="501d6-103">\<add> of \<allowedAudienceUris></span></span>

<span data-ttu-id="501d6-104">Добавляет целевой универсальный код ресурса, для которого может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="501d6-104">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="501d6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="501d6-105">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="501d6-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="501d6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="501d6-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="501d6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="501d6-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="501d6-108">Attributes</span></span>  
  
|<span data-ttu-id="501d6-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="501d6-109">Attribute</span></span>|<span data-ttu-id="501d6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="501d6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="501d6-111">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="501d6-111">allowedAudienceUri</span></span>|<span data-ttu-id="501d6-112">Строка, содержащая целевой универсальный код ресурса, для которого может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым в экземпляре <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="501d6-112">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="501d6-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="501d6-113">Child Elements</span></span>  

 <span data-ttu-id="501d6-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="501d6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="501d6-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="501d6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="501d6-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="501d6-116">Element</span></span>|<span data-ttu-id="501d6-117">Описание</span><span class="sxs-lookup"><span data-stu-id="501d6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="501d6-118">Представляет коллекцию целевых универсальных кодов ресурса (URI), для которых может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы они считались допустимыми для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="501d6-118">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="501d6-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="501d6-119">Remarks</span></span>  

 <span data-ttu-id="501d6-120">Данную коллекцию следует использовать в федеративном приложении, которое использует службу маркеров безопасности (STS), выдающую маркеры безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="501d6-120">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="501d6-121">При выпуске маркера безопасности служба STS также может указать универсальный код ресурса (URI) веб-служб, для которых предназначен маркер безопасности, добавив выражение <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> к маркеру безопасности.</span><span class="sxs-lookup"><span data-stu-id="501d6-121">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="501d6-122">Это позволяет коду <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> для веб-службы получателя проверить, что выданный маркер безопасности предназначен для данной службы, указав на необходимость выполнения соответствующей проверки. Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="501d6-122">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="501d6-123">Присвойте атрибуту `audienceUriMode` элемента `<issuedTokenAuthentication>` значение <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> или <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="501d6-123">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="501d6-124">Задайте набор допустимых универсальных кодов ресурса (URI), добавив их в данную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="501d6-124">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="501d6-125">Для получения дополнительной информации см. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="501d6-125">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="501d6-126">Дополнительные сведения об использовании этого элемента конфигурации см. в разделе [как настроить учетные данные на служба федерации](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="501d6-126">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501d6-127">См. также</span><span class="sxs-lookup"><span data-stu-id="501d6-127">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="501d6-128">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="501d6-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="501d6-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="501d6-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="501d6-130">Практическое руководство. Настройка учетных данных службы федерации</span><span class="sxs-lookup"><span data-stu-id="501d6-130">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
