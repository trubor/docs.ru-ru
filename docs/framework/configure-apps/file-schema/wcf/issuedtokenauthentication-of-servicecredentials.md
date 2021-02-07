---
description: 'Дополнительные сведения <issuedTokenAuthentication> о: <serviceCredentials>'
title: <issuedTokenAuthentication> из <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 62c60cc467217312c349ecdbe8e98b04dd022ddf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725679"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="83627-103">\<issuedTokenAuthentication> из \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="83627-103">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="83627-104">Определяет пользовательский маркер, выданный в качестве учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="83627-104">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="83627-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83627-105">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83627-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="83627-106">Attributes and Elements</span></span>  

 <span data-ttu-id="83627-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="83627-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83627-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="83627-108">Attributes</span></span>  
  
|<span data-ttu-id="83627-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="83627-109">Attribute</span></span>|<span data-ttu-id="83627-110">Описание</span><span class="sxs-lookup"><span data-stu-id="83627-110">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="83627-111">Возвращает набор целевых универсальных кодов ресурса (URI), для которых может быть предназначен маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым в экземпляре <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="83627-111">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="83627-112">Дополнительные сведения об использовании этого атрибута см. в разделе <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="83627-112">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="83627-113">Логическое значение, которое указывает, допускаются ли недоверенные издатели сертификатов RSA.</span><span class="sxs-lookup"><span data-stu-id="83627-113">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="83627-114">Сертификаты подписываются центрами сертификации (ЦС) для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="83627-114">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="83627-115">Недоверенным издателем является ЦС, который не указан как надежный для подписания сертификатов.</span><span class="sxs-lookup"><span data-stu-id="83627-115">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="83627-116">Возвращает значение, которое указывает, должно ли проверяться свойство <xref:System.IdentityModel.Tokens.SamlSecurityToken> маркера безопасности <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>.</span><span class="sxs-lookup"><span data-stu-id="83627-116">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="83627-117">Это значение имеет тип <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="83627-117">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="83627-118">Дополнительные сведения об использовании этого атрибута см. в разделе <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="83627-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="83627-119">Устанавливает режим проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="83627-119">Sets the certificate validation mode.</span></span> <span data-ttu-id="83627-120">Одно из допустимых значений для <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="83627-120">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="83627-121">Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="83627-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="83627-122">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="83627-122">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="83627-123">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="83627-123">Optional string.</span></span> <span data-ttu-id="83627-124">Тип и сборка, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="83627-124">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="83627-125">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="83627-125">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="83627-126">Задает режим отзыва, который указывает, проводится ли проверка списка отозванных сертификатов; этот режим также определяет способ проверки: с подключением к сети или автономно.</span><span class="sxs-lookup"><span data-stu-id="83627-126">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="83627-127">Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="83627-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="83627-128">Необязательный строковый атрибут, который задает тип SamlSerializer, который используется для учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="83627-128">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="83627-129">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="83627-129">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="83627-130">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="83627-130">Optional enumeration.</span></span> <span data-ttu-id="83627-131">Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="83627-131">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83627-132">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="83627-132">Child Elements</span></span>  
  
|<span data-ttu-id="83627-133">Элемент</span><span class="sxs-lookup"><span data-stu-id="83627-133">Element</span></span>|<span data-ttu-id="83627-134">Описание</span><span class="sxs-lookup"><span data-stu-id="83627-134">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="83627-135">Задает коллекцию элементов <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>, которая задает доверенных издателей для учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="83627-135">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83627-136">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="83627-136">Parent Elements</span></span>  
  
|<span data-ttu-id="83627-137">Элемент</span><span class="sxs-lookup"><span data-stu-id="83627-137">Element</span></span>|<span data-ttu-id="83627-138">Описание</span><span class="sxs-lookup"><span data-stu-id="83627-138">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="83627-139">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="83627-139">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83627-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="83627-140">Remarks</span></span>  

 <span data-ttu-id="83627-141">В сценарии с выданным маркером имеется три этапа.</span><span class="sxs-lookup"><span data-stu-id="83627-141">The issued token scenario has three stages.</span></span> <span data-ttu-id="83627-142">На первом этапе клиент, пытающийся получить доступ к службе, ссылается на *службу маркеров безопасности*.</span><span class="sxs-lookup"><span data-stu-id="83627-142">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="83627-143">Затем служба маркеров безопасности проводит проверку подлинности клиента и выдает клиенту маркер, обычно на языке Security Assertions Markup Language (SAML).</span><span class="sxs-lookup"><span data-stu-id="83627-143">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="83627-144">После этого клиент возвращается к службе с этим маркером.</span><span class="sxs-lookup"><span data-stu-id="83627-144">The client then returns to the service with the token.</span></span> <span data-ttu-id="83627-145">Служба проверяет наличие в маркере данных, позволяющих проверить подлинность маркера и, соответственно, самого клиента.</span><span class="sxs-lookup"><span data-stu-id="83627-145">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="83627-146">Для проверки подлинности маркера сертификат, используемый службой маркеров безопасности, должен быть известен службе.</span><span class="sxs-lookup"><span data-stu-id="83627-146">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="83627-147">Этот элемент является хранилищем подобных сертификатов службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="83627-147">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="83627-148">Чтобы добавить сертификаты, используйте [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="83627-148">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="83627-149">Вставьте [\<add>](add-of-knowncertificates.md) для каждого сертификата, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="83627-149">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="83627-150">По умолчанию сертификаты должны быть получены от службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="83627-150">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="83627-151">Эти "известные" сертификаты гарантируют, что доступ к службе могут получить только допустимые клиенты.</span><span class="sxs-lookup"><span data-stu-id="83627-151">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="83627-152">Дополнительные сведения об использовании этого элемента конфигурации см. в разделе [как настроить учетные данные на служба федерации](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="83627-152">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83627-153">См. также</span><span class="sxs-lookup"><span data-stu-id="83627-153">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="83627-154">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="83627-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="83627-155">Практическое руководство. Настройка учетных данных службы федерации</span><span class="sxs-lookup"><span data-stu-id="83627-155">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
