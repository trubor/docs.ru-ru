---
description: 'Дополнительные сведения о: <scopedCertificates> element'
title: Элемент <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 7aa108031831539396e8f737a214982655dd6bb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683337"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="d270f-103">Элемент \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="d270f-103">\<scopedCertificates> Element</span></span>

<span data-ttu-id="d270f-104">Представляет коллекцию сертификатов X.509, предоставленную конкретными службами (в области действия) для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d270f-104">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="d270f-105">Эта коллекция обычно используется, чтобы задать сертификаты служб для служб маркеров безопасности в федеративной инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="d270f-105">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="d270f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d270f-106">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d270f-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d270f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="d270f-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d270f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d270f-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d270f-109">Attributes</span></span>  

 <span data-ttu-id="d270f-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d270f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d270f-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d270f-111">Child Elements</span></span>  
  
|<span data-ttu-id="d270f-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="d270f-112">Element</span></span>|<span data-ttu-id="d270f-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d270f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="d270f-114">Добавляет сертификат X.509 в коллекцию сертификатов в области действия.</span><span class="sxs-lookup"><span data-stu-id="d270f-114">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d270f-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d270f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d270f-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="d270f-116">Element</span></span>|<span data-ttu-id="d270f-117">Описание</span><span class="sxs-lookup"><span data-stu-id="d270f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="d270f-118">Задает сертификат для использования при проверке подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="d270f-118">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d270f-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d270f-119">Remarks</span></span>  

 <span data-ttu-id="d270f-120">Эта коллекция позволяет клиенту настроить сертификаты служб для использования на основе URL-адреса службы, с которой он связывается.</span><span class="sxs-lookup"><span data-stu-id="d270f-120">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="d270f-121">Это особенно полезно в сценариях с выданным маркером, в которых клиент может связываться с несколькими службами (с конечной службой, а также с промежуточными службами маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="d270f-121">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="d270f-122">Для привязок, в которых используется безопасность сообщений на основе сертификатов, этот сертификат используется для шифрования сообщений службе; предполагается также, что он будет использоваться службой для подписи ответов клиенту.</span><span class="sxs-lookup"><span data-stu-id="d270f-122">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="d270f-123">Если для привязки необходим сертификат для службы, а конкретный сертификат для URL-адреса службы в элементе ScopedCertificates отсутствует, то используется сертификат по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d270f-123">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="d270f-124">Дополнительные сведения см. в разделе «сертификаты с заданной областью» раздела [о создании федеративного клиента](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="d270f-124">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d270f-125">Пример</span><span class="sxs-lookup"><span data-stu-id="d270f-125">Example</span></span>  

 <span data-ttu-id="d270f-126">В следующем примере задается сертификат службы, используемый клиентом при взаимодействии с конечными точками, доменное имя которых находится `http://www.contoso.com` по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="d270f-126">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="d270f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="d270f-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="d270f-128">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="d270f-128">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d270f-129">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="d270f-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="d270f-130">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="d270f-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d270f-131">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d270f-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
