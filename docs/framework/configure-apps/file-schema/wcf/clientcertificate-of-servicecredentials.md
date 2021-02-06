---
description: 'Дополнительные сведения <clientCertificate> о: <serviceCredentials>'
title: <clientCertificate> из <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: c3e6378f9646ec30188e2de3d1c832f363904ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638825"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="e8e54-103">\<clientCertificate> из \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e8e54-103">\<clientCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="e8e54-104">Задает файл сертификата X.509, используемый для подписания и шифрования сообщений к клиенту от службы при дуплексном обмене данными.</span><span class="sxs-lookup"><span data-stu-id="e8e54-104">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="e8e54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8e54-105">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8e54-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e8e54-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e8e54-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e8e54-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8e54-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e8e54-108">Attributes</span></span>  

 <span data-ttu-id="e8e54-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e8e54-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8e54-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e8e54-110">Child Elements</span></span>  
  
|<span data-ttu-id="e8e54-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="e8e54-111">Element</span></span>|<span data-ttu-id="e8e54-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e8e54-112">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="e8e54-113">Задает параметры проверки подлинности для сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="e8e54-113">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="e8e54-114">Задает тип сертификата для использования.</span><span class="sxs-lookup"><span data-stu-id="e8e54-114">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8e54-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e8e54-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e8e54-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="e8e54-116">Element</span></span>|<span data-ttu-id="e8e54-117">Описание</span><span class="sxs-lookup"><span data-stu-id="e8e54-117">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="e8e54-118">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="e8e54-118">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8e54-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8e54-119">Remarks</span></span>  

 <span data-ttu-id="e8e54-120">Этот элемент используется в случаях, когда служба должна получить клиентский сертификат заранее для безопасного обмена данными с клиентом.</span><span class="sxs-lookup"><span data-stu-id="e8e54-120">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="e8e54-121">Это характерно для дуплексного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="e8e54-121">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="e8e54-122">В более распространенном варианте «запрос/отклик» клиент включает сертификат в запрос, который используется службой для шифрования и подписания отклика.</span><span class="sxs-lookup"><span data-stu-id="e8e54-122">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="e8e54-123">Тем не менее при дуплексном обмене данными служба не получает запроса от клиента, и ей, таким образом, необходим сертификат клиента заранее, чтобы обеспечить защиту сообщения, отправляемого клиенту.</span><span class="sxs-lookup"><span data-stu-id="e8e54-123">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="e8e54-124">Следовательно, необходимо получить сертификат клиента при согласовании вне диапазона и указать сертификат с помощью этого элемента.</span><span class="sxs-lookup"><span data-stu-id="e8e54-124">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="e8e54-125">Дополнительные сведения о дуплексных службах см. [в разделе инструкции. Создание дуплексного контракта](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e8e54-125">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="e8e54-126">Заданный в этом элементе сертификат используется для шифрования сообщений к клиенту только для привязок, которые настроены с использованием режима проверки подлинности `MutualCertificateDuplex`.</span><span class="sxs-lookup"><span data-stu-id="e8e54-126">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e54-127">См. также</span><span class="sxs-lookup"><span data-stu-id="e8e54-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="e8e54-128">Практическое руководство. Создание двухстороннего контракта</span><span class="sxs-lookup"><span data-stu-id="e8e54-128">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="e8e54-129">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="e8e54-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e8e54-130">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="e8e54-130">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
