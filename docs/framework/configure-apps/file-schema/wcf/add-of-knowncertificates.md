---
description: 'Дополнительные сведения <add> о: <knownCertificates>'
title: <add> из <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 1669495e6119a35543e39230fc5dcc986ee2dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750290"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="4edec-103">\<add> из \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="4edec-103">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="4edec-104">Добавляет сертификат X.509 в коллекцию известных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="4edec-104">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4edec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4edec-105">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4edec-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4edec-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4edec-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4edec-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4edec-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4edec-108">Attributes</span></span>  
  
|<span data-ttu-id="4edec-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4edec-109">Attribute</span></span>|<span data-ttu-id="4edec-110">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4edec-111">findValue</span><span class="sxs-lookup"><span data-stu-id="4edec-111">findValue</span></span>|<span data-ttu-id="4edec-112">Строка.</span><span class="sxs-lookup"><span data-stu-id="4edec-112">String.</span></span> <span data-ttu-id="4edec-113">Значение, которое нужно найти.</span><span class="sxs-lookup"><span data-stu-id="4edec-113">The value to search for.</span></span>|  
|<span data-ttu-id="4edec-114">storeLocation</span><span class="sxs-lookup"><span data-stu-id="4edec-114">storeLocation</span></span>|<span data-ttu-id="4edec-115">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="4edec-115">Enumeration.</span></span> <span data-ttu-id="4edec-116">Одно из двух местоположений хранилища, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="4edec-116">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="4edec-117">storeName</span><span class="sxs-lookup"><span data-stu-id="4edec-117">storeName</span></span>|<span data-ttu-id="4edec-118">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="4edec-118">Enumeration.</span></span> <span data-ttu-id="4edec-119">Одно из системных хранилищ, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="4edec-119">One of the system stores to search.</span></span>|  
|<span data-ttu-id="4edec-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="4edec-120">x509FindType</span></span>|<span data-ttu-id="4edec-121">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="4edec-121">Enumeration.</span></span> <span data-ttu-id="4edec-122">Одно из полей сертификата, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="4edec-122">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="4edec-123">Атрибут findValue</span><span class="sxs-lookup"><span data-stu-id="4edec-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="4edec-124">Значение</span><span class="sxs-lookup"><span data-stu-id="4edec-124">Value</span></span>|<span data-ttu-id="4edec-125">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4edec-126">Строка</span><span class="sxs-lookup"><span data-stu-id="4edec-126">String</span></span>|<span data-ttu-id="4edec-127">Значение зависит от поля (заданного атрибутом x509FindType), поиск которого выполняется.</span><span class="sxs-lookup"><span data-stu-id="4edec-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="4edec-128">Например, при поиске отпечатка значение должно быть строкой шестнадцатеричных чисел.</span><span class="sxs-lookup"><span data-stu-id="4edec-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="4edec-129">Атрибут x509FindType</span><span class="sxs-lookup"><span data-stu-id="4edec-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="4edec-130">Значение</span><span class="sxs-lookup"><span data-stu-id="4edec-130">Value</span></span>|<span data-ttu-id="4edec-131">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4edec-132">Перечисление</span><span class="sxs-lookup"><span data-stu-id="4edec-132">Enumeration</span></span>|<span data-ttu-id="4edec-133">К числу значений относятся следующие: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="4edec-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="4edec-134">Атрибут storeLocation</span><span class="sxs-lookup"><span data-stu-id="4edec-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="4edec-135">Значение</span><span class="sxs-lookup"><span data-stu-id="4edec-135">Value</span></span>|<span data-ttu-id="4edec-136">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4edec-137">Перечисление</span><span class="sxs-lookup"><span data-stu-id="4edec-137">Enumeration</span></span>|<span data-ttu-id="4edec-138">CurrentUser или LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4edec-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="4edec-139">Атрибут storeName</span><span class="sxs-lookup"><span data-stu-id="4edec-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="4edec-140">Значение</span><span class="sxs-lookup"><span data-stu-id="4edec-140">Value</span></span>|<span data-ttu-id="4edec-141">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4edec-142">Перечисление</span><span class="sxs-lookup"><span data-stu-id="4edec-142">Enumeration</span></span>|<span data-ttu-id="4edec-143">К числу значений относятся следующие: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople и TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="4edec-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4edec-144">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4edec-144">Child Elements</span></span>  

 <span data-ttu-id="4edec-145">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4edec-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4edec-146">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4edec-146">Parent Elements</span></span>  
  
|<span data-ttu-id="4edec-147">Элемент</span><span class="sxs-lookup"><span data-stu-id="4edec-147">Element</span></span>|<span data-ttu-id="4edec-148">Описание</span><span class="sxs-lookup"><span data-stu-id="4edec-148">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="4edec-149">Представляет коллекцию сертификатов X.509, предоставленную службой STS для проверки маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="4edec-149">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4edec-150">Remarks</span><span class="sxs-lookup"><span data-stu-id="4edec-150">Remarks</span></span>  

 <span data-ttu-id="4edec-151">В сценарии с выданным маркером имеется три этапа.</span><span class="sxs-lookup"><span data-stu-id="4edec-151">The issued token scenario has three stages.</span></span> <span data-ttu-id="4edec-152">На первом этапе клиент, пытающийся получить доступ к службе, ссылается на *службу маркеров безопасности*.</span><span class="sxs-lookup"><span data-stu-id="4edec-152">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="4edec-153">Затем служба маркеров безопасности проводит проверку подлинности клиента и выдает клиенту маркер, обычно на языке Security Assertions Markup Language (SAML).</span><span class="sxs-lookup"><span data-stu-id="4edec-153">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="4edec-154">После этого клиент возвращается к службе с этим маркером.</span><span class="sxs-lookup"><span data-stu-id="4edec-154">The client then returns to the service with the token.</span></span> <span data-ttu-id="4edec-155">Служба проверяет наличие в маркере данных, позволяющих проверить подлинность маркера и, соответственно, самого клиента.</span><span class="sxs-lookup"><span data-stu-id="4edec-155">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="4edec-156">Для проверки подлинности маркера сертификат, используемый службой маркеров безопасности, должен быть известен службе.</span><span class="sxs-lookup"><span data-stu-id="4edec-156">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="4edec-157">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Элемент является репозиторием для всех таких сертификатов службы безопасных маркеров.</span><span class="sxs-lookup"><span data-stu-id="4edec-157">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="4edec-158">Чтобы добавить сертификаты, используйте [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="4edec-158">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="4edec-159">Вставьте [ \<add> \<knownCertificates> элемент element](add-of-knowncertificates.md) для каждого сертификата, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4edec-159">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="4edec-160">По умолчанию сертификаты должны быть получены от службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="4edec-160">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="4edec-161">Эти "известные" сертификаты гарантируют, что доступ к службе могут получить только допустимые клиенты.</span><span class="sxs-lookup"><span data-stu-id="4edec-161">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="4edec-162">Чтобы просмотреть условия, необходимые для проверки подлинности клиента в Федеративной службе, а также дополнительные сведения об использовании этого элемента конфигурации, см. раздел [как настроить учетные данные на служба федерации](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="4edec-162">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="4edec-163">Дополнительные сведения о федеративных сценариях см. в разделе [Федерация и выданные токены](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="4edec-163">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4edec-164">Пример</span><span class="sxs-lookup"><span data-stu-id="4edec-164">Example</span></span>  

 <span data-ttu-id="4edec-165">В следующем примере демонстрируется добавление сертификата в хранилище сертификатов службы STS.</span><span class="sxs-lookup"><span data-stu-id="4edec-165">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="4edec-166">См. также</span><span class="sxs-lookup"><span data-stu-id="4edec-166">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="4edec-167">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="4edec-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4edec-168">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="4edec-168">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4edec-169">Практическое руководство. Настройка учетных данных службы федерации</span><span class="sxs-lookup"><span data-stu-id="4edec-169">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="4edec-170">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="4edec-170">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
