---
description: 'Дополнительные сведения: <knownCertificates>'
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 0180db56c775f4f6f17de8da58781c15a412bc81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802233"
---
# \<knownCertificates>

<span data-ttu-id="d8712-102">Представляет коллекцию сертификатов X.509, которые предоставляются для проверки подлинности учетных данных безопасности, выданных службой маркеров безопасности (STS).</span><span class="sxs-lookup"><span data-stu-id="d8712-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="d8712-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8712-103">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8712-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d8712-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d8712-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d8712-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8712-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d8712-106">Attributes</span></span>  

 <span data-ttu-id="d8712-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d8712-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8712-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d8712-108">Child Elements</span></span>  
  
|<span data-ttu-id="d8712-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="d8712-109">Element</span></span>|<span data-ttu-id="d8712-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d8712-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="d8712-111">Добавляет сертификат X.509 в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="d8712-111">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8712-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d8712-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d8712-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="d8712-113">Element</span></span>|<span data-ttu-id="d8712-114">Описание</span><span class="sxs-lookup"><span data-stu-id="d8712-114">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="d8712-115">Задает маркер, выданный в качестве учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="d8712-115">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8712-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8712-116">Remarks</span></span>  

 <span data-ttu-id="d8712-117">В сценарии с выданным маркером имеется три этапа.</span><span class="sxs-lookup"><span data-stu-id="d8712-117">The issued token scenario has three stages.</span></span> <span data-ttu-id="d8712-118">На первом этапе клиент, пытающийся получить доступ к службе, ссылается на *службу маркеров безопасности*.</span><span class="sxs-lookup"><span data-stu-id="d8712-118">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="d8712-119">Затем служба маркеров безопасности проводит проверку подлинности клиента и выдает клиенту маркер, обычно на языке Security Assertions Markup Language (SAML).</span><span class="sxs-lookup"><span data-stu-id="d8712-119">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="d8712-120">После этого клиент возвращается к службе с этим маркером.</span><span class="sxs-lookup"><span data-stu-id="d8712-120">The client then returns to the service with the token.</span></span> <span data-ttu-id="d8712-121">Служба проверяет наличие в маркере данных, позволяющих проверить подлинность маркера и, соответственно, самого клиента.</span><span class="sxs-lookup"><span data-stu-id="d8712-121">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="d8712-122">Для проверки подлинности маркера сертификат, используемый службой маркеров безопасности, должен быть известен службе.</span><span class="sxs-lookup"><span data-stu-id="d8712-122">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="d8712-123">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Элемент является репозиторием для всех таких сертификатов службы безопасных маркеров.</span><span class="sxs-lookup"><span data-stu-id="d8712-123">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="d8712-124">Чтобы добавить сертификаты, используйте [ \<knownCertificates> элемент](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="d8712-124">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="d8712-125">Вставьте [\<add>](add-of-knowncertificates.md) для каждого сертификата, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d8712-125">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="d8712-126">По умолчанию сертификаты должны быть получены от службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="d8712-126">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="d8712-127">Эти "известные" сертификаты гарантируют, что доступ к службе могут получить только допустимые клиенты.</span><span class="sxs-lookup"><span data-stu-id="d8712-127">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="d8712-128">Чтобы просмотреть условия, необходимые для проверки подлинности клиента в Федеративной службе, а также дополнительные сведения об использовании этого элемента конфигурации, см. раздел [как настроить учетные данные на служба федерации](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="d8712-128">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="d8712-129">Дополнительные сведения о федеративных сценариях см. в разделе [Федерация и выданные токены](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="d8712-129">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="d8712-130">Пример, демонстрирующий заполнение коллекции в конфигурации, см. в разделе [\<add>](add-of-knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="d8712-130">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8712-131">См. также</span><span class="sxs-lookup"><span data-stu-id="d8712-131">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="d8712-132">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="d8712-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d8712-133">Практическое руководство. Настройка учетных данных службы федерации</span><span class="sxs-lookup"><span data-stu-id="d8712-133">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="d8712-134">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="d8712-134">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d8712-135">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="d8712-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="d8712-136">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d8712-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
