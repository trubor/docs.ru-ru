---
description: 'Дополнительные сведения о: <add> <scopedCertificates> element'
title: <add> элемента <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 4c267164ccf065edee79a6aaaa9aaddc14d95909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750277"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="034f7-103">\<add> элемента \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="034f7-103">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="034f7-104">Добавляет сертификат X.509 в коллекцию сертификатов в области действия.</span><span class="sxs-lookup"><span data-stu-id="034f7-104">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="034f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="034f7-105">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="034f7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="034f7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="034f7-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="034f7-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="034f7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="034f7-108">Attributes</span></span>  
  
|<span data-ttu-id="034f7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="034f7-109">Attribute</span></span>|<span data-ttu-id="034f7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="034f7-111">targetUri</span><span class="sxs-lookup"><span data-stu-id="034f7-111">targetUri</span></span>|<span data-ttu-id="034f7-112">Строка.</span><span class="sxs-lookup"><span data-stu-id="034f7-112">String.</span></span> <span data-ttu-id="034f7-113">Задает универсальный код ресурса (URI) службы, связанной с сертификатом.</span><span class="sxs-lookup"><span data-stu-id="034f7-113">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="034f7-114">findValue</span><span class="sxs-lookup"><span data-stu-id="034f7-114">findValue</span></span>|<span data-ttu-id="034f7-115">Строка.</span><span class="sxs-lookup"><span data-stu-id="034f7-115">String.</span></span> <span data-ttu-id="034f7-116">Значение, которое нужно найти.</span><span class="sxs-lookup"><span data-stu-id="034f7-116">The value to search for.</span></span>|  
|<span data-ttu-id="034f7-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="034f7-117">x509FindType</span></span>|<span data-ttu-id="034f7-118">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="034f7-118">Enumeration.</span></span> <span data-ttu-id="034f7-119">Одно из полей сертификата, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="034f7-119">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="034f7-120">storeLocation</span><span class="sxs-lookup"><span data-stu-id="034f7-120">storeLocation</span></span>|<span data-ttu-id="034f7-121">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="034f7-121">Enumeration.</span></span> <span data-ttu-id="034f7-122">Одно из двух местоположений хранилища, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="034f7-122">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="034f7-123">storeName</span><span class="sxs-lookup"><span data-stu-id="034f7-123">storeName</span></span>|<span data-ttu-id="034f7-124">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="034f7-124">Enumeration.</span></span> <span data-ttu-id="034f7-125">Одно из системных хранилищ, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="034f7-125">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="034f7-126">Атрибут findValue</span><span class="sxs-lookup"><span data-stu-id="034f7-126">findValue Attribute</span></span>  
  
|<span data-ttu-id="034f7-127">Значение</span><span class="sxs-lookup"><span data-stu-id="034f7-127">Value</span></span>|<span data-ttu-id="034f7-128">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="034f7-129">Строка</span><span class="sxs-lookup"><span data-stu-id="034f7-129">String</span></span>|<span data-ttu-id="034f7-130">Значение зависит от поля (заданного атрибутом x509FindType), поиск которого выполняется.</span><span class="sxs-lookup"><span data-stu-id="034f7-130">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="034f7-131">Например, при поиске отпечатка значение должно быть строкой шестнадцатеричных чисел.</span><span class="sxs-lookup"><span data-stu-id="034f7-131">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="034f7-132">Атрибут x509FindType</span><span class="sxs-lookup"><span data-stu-id="034f7-132">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="034f7-133">Значение</span><span class="sxs-lookup"><span data-stu-id="034f7-133">Value</span></span>|<span data-ttu-id="034f7-134">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="034f7-135">Перечисление</span><span class="sxs-lookup"><span data-stu-id="034f7-135">Enumeration</span></span>|<span data-ttu-id="034f7-136">К числу значений относятся следующие: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="034f7-136">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="034f7-137">Атрибут storeLocation</span><span class="sxs-lookup"><span data-stu-id="034f7-137">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="034f7-138">Значение</span><span class="sxs-lookup"><span data-stu-id="034f7-138">Value</span></span>|<span data-ttu-id="034f7-139">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="034f7-140">Перечисление</span><span class="sxs-lookup"><span data-stu-id="034f7-140">Enumeration</span></span>|<span data-ttu-id="034f7-141">CurrentUser или LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="034f7-141">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="034f7-142">Атрибут storeName</span><span class="sxs-lookup"><span data-stu-id="034f7-142">storeName Attribute</span></span>  
  
|<span data-ttu-id="034f7-143">Значение</span><span class="sxs-lookup"><span data-stu-id="034f7-143">Value</span></span>|<span data-ttu-id="034f7-144">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="034f7-145">Перечисление</span><span class="sxs-lookup"><span data-stu-id="034f7-145">Enumeration</span></span>|<span data-ttu-id="034f7-146">К числу значений относятся следующие: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople и TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="034f7-146">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="034f7-147">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="034f7-147">Child Elements</span></span>  

 <span data-ttu-id="034f7-148">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="034f7-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="034f7-149">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="034f7-149">Parent Elements</span></span>  
  
|<span data-ttu-id="034f7-150">Элемент</span><span class="sxs-lookup"><span data-stu-id="034f7-150">Element</span></span>|<span data-ttu-id="034f7-151">Описание</span><span class="sxs-lookup"><span data-stu-id="034f7-151">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="034f7-152">Представляет коллекцию сертификатов X.509, предоставленную конкретными службами (в области действия) для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="034f7-152">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="034f7-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="034f7-153">Remarks</span></span>  

 <span data-ttu-id="034f7-154">Этот элемент позволяет клиенту настроить сертификат службы для использования на основе URL-адреса службы, с которой он связывается.</span><span class="sxs-lookup"><span data-stu-id="034f7-154">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="034f7-155">Это особенно полезно в сценариях с выданным маркером, в которых клиент может связываться с несколькими службами (с конечной службой, а также с промежуточными службами маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="034f7-155">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="034f7-156">Для привязок, в которых используется безопасность сообщений на основе сертификатов, этот сертификат используется для шифрования сообщений службе; предполагается также, что он будет использоваться службой для подписи ответов клиенту.</span><span class="sxs-lookup"><span data-stu-id="034f7-156">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="034f7-157">Если для привязки необходим сертификат для службы, а конкретный сертификат для URL-адреса службы в элементе ScopedCertificates отсутствует, то используется сертификат по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="034f7-157">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="034f7-158">Дополнительные сведения см. в разделе «сертификаты с заданной областью» раздела [о создании федеративного клиента](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="034f7-158">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="034f7-159">Пример</span><span class="sxs-lookup"><span data-stu-id="034f7-159">Example</span></span>  

 <span data-ttu-id="034f7-160">В следующем примере к коллекции добавляется сертификат X.509.</span><span class="sxs-lookup"><span data-stu-id="034f7-160">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="034f7-161">См. также</span><span class="sxs-lookup"><span data-stu-id="034f7-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="034f7-162">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="034f7-162">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="034f7-163">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="034f7-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="034f7-164">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="034f7-164">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="034f7-165">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="034f7-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
