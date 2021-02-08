---
description: 'Дополнительные сведения о: <defaultCertificate> element'
title: Элемент <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 580236e521e91c8b475586f6c6378630960f233c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803923"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="b1782-103">Элемент \<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="b1782-103">\<defaultCertificate> Element</span></span>

<span data-ttu-id="b1782-104">Задает сертификат X.509 для использования, когда служба или служба маркеров безопасности не предоставляет сертификат посредством протокола согласования.</span><span class="sxs-lookup"><span data-stu-id="b1782-104">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="b1782-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1782-105">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1782-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b1782-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b1782-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b1782-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1782-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b1782-108">Attributes</span></span>  
  
|<span data-ttu-id="b1782-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b1782-109">Attribute</span></span>|<span data-ttu-id="b1782-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1782-111">findValue</span><span class="sxs-lookup"><span data-stu-id="b1782-111">findValue</span></span>|<span data-ttu-id="b1782-112">Строка.</span><span class="sxs-lookup"><span data-stu-id="b1782-112">String.</span></span> <span data-ttu-id="b1782-113">Значение, которое нужно найти.</span><span class="sxs-lookup"><span data-stu-id="b1782-113">The value to search for.</span></span>|  
|<span data-ttu-id="b1782-114">x509FindType</span><span class="sxs-lookup"><span data-stu-id="b1782-114">x509FindType</span></span>|<span data-ttu-id="b1782-115">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="b1782-115">Enumeration.</span></span> <span data-ttu-id="b1782-116">Одно из полей сертификата, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="b1782-116">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="b1782-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="b1782-117">storeLocation</span></span>|<span data-ttu-id="b1782-118">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="b1782-118">Enumeration.</span></span> <span data-ttu-id="b1782-119">Одно из двух системных расположений хранилища, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="b1782-119">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="b1782-120">storeName</span><span class="sxs-lookup"><span data-stu-id="b1782-120">storeName</span></span>|<span data-ttu-id="b1782-121">Перечисление.</span><span class="sxs-lookup"><span data-stu-id="b1782-121">Enumeration.</span></span> <span data-ttu-id="b1782-122">Одно из системных хранилищ, где следует проводить поиск.</span><span class="sxs-lookup"><span data-stu-id="b1782-122">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="b1782-123">Атрибут findValue</span><span class="sxs-lookup"><span data-stu-id="b1782-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="b1782-124">Значение</span><span class="sxs-lookup"><span data-stu-id="b1782-124">Value</span></span>|<span data-ttu-id="b1782-125">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1782-126">Строка</span><span class="sxs-lookup"><span data-stu-id="b1782-126">String</span></span>|<span data-ttu-id="b1782-127">Значение зависит от поля (заданного атрибутом x509FindType), поиск которого выполняется.</span><span class="sxs-lookup"><span data-stu-id="b1782-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="b1782-128">Например, при поиске отпечатка значение должно быть строкой шестнадцатеричных чисел.</span><span class="sxs-lookup"><span data-stu-id="b1782-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="b1782-129">Атрибут x509FindType</span><span class="sxs-lookup"><span data-stu-id="b1782-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="b1782-130">Значение</span><span class="sxs-lookup"><span data-stu-id="b1782-130">Value</span></span>|<span data-ttu-id="b1782-131">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1782-132">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b1782-132">Enumeration</span></span>|<span data-ttu-id="b1782-133">К числу значений относятся следующие: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="b1782-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="b1782-134">Атрибут storeLocation</span><span class="sxs-lookup"><span data-stu-id="b1782-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="b1782-135">Значение</span><span class="sxs-lookup"><span data-stu-id="b1782-135">Value</span></span>|<span data-ttu-id="b1782-136">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1782-137">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b1782-137">Enumeration</span></span>|<span data-ttu-id="b1782-138">CurrentUser или LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="b1782-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="b1782-139">Атрибут storeName</span><span class="sxs-lookup"><span data-stu-id="b1782-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="b1782-140">Значение</span><span class="sxs-lookup"><span data-stu-id="b1782-140">Value</span></span>|<span data-ttu-id="b1782-141">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1782-142">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b1782-142">Enumeration</span></span>|<span data-ttu-id="b1782-143">К числу значений относятся следующие: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople и TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="b1782-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1782-144">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b1782-144">Child Elements</span></span>  

 <span data-ttu-id="b1782-145">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b1782-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1782-146">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b1782-146">Parent Elements</span></span>  
  
|<span data-ttu-id="b1782-147">Элемент</span><span class="sxs-lookup"><span data-stu-id="b1782-147">Element</span></span>|<span data-ttu-id="b1782-148">Описание</span><span class="sxs-lookup"><span data-stu-id="b1782-148">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="b1782-149">Задает сертификат для использования при проверке подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="b1782-149">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1782-150">Remarks</span><span class="sxs-lookup"><span data-stu-id="b1782-150">Remarks</span></span>  

 <span data-ttu-id="b1782-151">Для привязок, использующих безопасность сообщений на основе сертификатов, сертификат, заданный этим элементом конфигурации, используется для шифрования сообщений службе; предполагается также, что он будет использоваться службой для подписи ответов клиенту.</span><span class="sxs-lookup"><span data-stu-id="b1782-151">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="b1782-152">Он сохраняет один сертификат для использования при отсутствии сертификата, заданного службой сертификата.</span><span class="sxs-lookup"><span data-stu-id="b1782-152">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1782-153">Пример</span><span class="sxs-lookup"><span data-stu-id="b1782-153">Example</span></span>  

 <span data-ttu-id="b1782-154">В следующем примере указывается сертификат, который будет использоваться для конечных точек, URI которых начинается с `http://www.contoso.com` , и сертификат, который будет использоваться для всех остальных конечных точек, не выполняющих согласование сертификатов.</span><span class="sxs-lookup"><span data-stu-id="b1782-154">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="b1782-155">См. также</span><span class="sxs-lookup"><span data-stu-id="b1782-155">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="b1782-156">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="b1782-156">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="b1782-157">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="b1782-157">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b1782-158">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="b1782-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
