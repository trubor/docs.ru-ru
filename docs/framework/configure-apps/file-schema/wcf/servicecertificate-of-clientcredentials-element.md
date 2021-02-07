---
description: 'Дополнительные сведения о: <serviceCertificate> <clientCredentials> element'
title: <serviceCertificate> элемента <clientCredentials>
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 5503c1a60b2d37f4f9359a2f49c019c37df71619
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682908"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="5b688-103">\<serviceCertificate> элемента \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5b688-103">\<serviceCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="5b688-104">Задает сертификат для использования при проверке подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="5b688-104">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5b688-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b688-105">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b688-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5b688-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5b688-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5b688-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b688-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5b688-108">Attributes</span></span>  

 <span data-ttu-id="5b688-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5b688-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b688-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5b688-110">Child Elements</span></span>  
  
|<span data-ttu-id="5b688-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="5b688-111">Element</span></span>|<span data-ttu-id="5b688-112">Описание</span><span class="sxs-lookup"><span data-stu-id="5b688-112">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="5b688-113">Задает сертификат X.509 для использования, когда служба или служба маркеров безопасности не предоставляет сертификат посредством протокола согласования.</span><span class="sxs-lookup"><span data-stu-id="5b688-113">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="5b688-114">Представляет коллекцию сертификатов X.509, предоставленную конкретными службами (в области действия) для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="5b688-114">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="5b688-115">Эта коллекция обычно используется, чтобы задать сертификаты служб для служб маркеров безопасности в федеративной инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="5b688-115">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="5b688-116">Задает поведение проверки подлинности для сертификатов служб, используемых клиентом.</span><span class="sxs-lookup"><span data-stu-id="5b688-116">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b688-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5b688-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5b688-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="5b688-118">Element</span></span>|<span data-ttu-id="5b688-119">Описание</span><span class="sxs-lookup"><span data-stu-id="5b688-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="5b688-120">Задает учетные данные, используемые клиентом для подтверждения своей подлинности при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="5b688-120">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b688-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="5b688-121">Remarks</span></span>  

 <span data-ttu-id="5b688-122">Этот элемент конфигурации содержит параметры, используемые клиентом для проверки сертификата, представленного службой с помощью проверки подлинности SSL.</span><span class="sxs-lookup"><span data-stu-id="5b688-122">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="5b688-123">Он также содержит сертификат для службы, который явно задан в клиенте для шифрования сообщений для службы с помощью безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="5b688-123">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="5b688-124">Атрибуты `serviceCertificate` элемента идентичны атрибутам объекта [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5b688-124">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b688-125">См. также</span><span class="sxs-lookup"><span data-stu-id="5b688-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="5b688-126">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="5b688-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5b688-127">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="5b688-127">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5b688-128">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="5b688-128">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5b688-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="5b688-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
