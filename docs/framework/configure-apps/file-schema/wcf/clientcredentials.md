---
description: 'Дополнительные сведения: <clientCredentials>'
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: b10e046f8e4994e367db69d5863e54a0bfa07db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638812"
---
# \<clientCredentials>

<span data-ttu-id="8fdf1-102">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="8fdf1-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8fdf1-103">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fdf1-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8fdf1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8fdf1-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fdf1-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8fdf1-106">Attributes</span></span>  
  
|<span data-ttu-id="8fdf1-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8fdf1-107">Attribute</span></span>|<span data-ttu-id="8fdf1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8fdf1-108">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="8fdf1-109">Логическое значение, которое указывает, может ли текущий пользователь принимать участие в выборе учетных данных клиента во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-109">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="8fdf1-110">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-110">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="8fdf1-111">Строка, задающая тип данного элемента конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-111">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fdf1-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8fdf1-112">Child Elements</span></span>  
  
|<span data-ttu-id="8fdf1-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="8fdf1-113">Element</span></span>|<span data-ttu-id="8fdf1-114">Описание</span><span class="sxs-lookup"><span data-stu-id="8fdf1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="8fdf1-115">Задает сертификат, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-115">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="8fdf1-116">Это элемент типа <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-116">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="8fdf1-117">Задает хэш-код, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-117">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="8fdf1-118">Это элемент типа <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-118">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="8fdf1-119">Задает тип пользовательского маркера, используемого для проверки подлинности клиента при подключении к службе маркеров безопасности (STS).</span><span class="sxs-lookup"><span data-stu-id="8fdf1-119">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="8fdf1-120">Это элемент типа <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-120">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="8fdf1-121">Задает учетные данные текущего однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-121">Specifies a current peer credential.</span></span> <span data-ttu-id="8fdf1-122">Это элемент типа <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-122">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="8fdf1-123">Задает сертификат, используемый при проверки подлинности службы для клиента, и предоставляет структуру для настройки параметров сертификата.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-123">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="8fdf1-124">Данный сертификат должен быть предоставлен вне диапазона службой клиенту.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-124">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="8fdf1-125">Это элемент типа <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-125">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="8fdf1-126">Задает учетные данные Windows.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-126">Specifies a Windows credential.</span></span> <span data-ttu-id="8fdf1-127">Значением по умолчанию являются учетные данные текущего потока.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-127">The default is the credential of the current thread.</span></span> <span data-ttu-id="8fdf1-128">Это элемент типа <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-128">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fdf1-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8fdf1-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8fdf1-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="8fdf1-130">Element</span></span>|<span data-ttu-id="8fdf1-131">Описание</span><span class="sxs-lookup"><span data-stu-id="8fdf1-131">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8fdf1-132">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-132">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fdf1-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="8fdf1-133">Remarks</span></span>  

 <span data-ttu-id="8fdf1-134">Учетные данные клиента используются для проверки подлинности клиента при подключении к службам в случаях, когда требуется взаимная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-134">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="8fdf1-135">Данный раздел конфигурации также можно использовать для задания сертификатов служб для сценариев, где клиент должен обеспечить защиту сообщений, передаваемых службе, с помощью сертификатов службы.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-135">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fdf1-136">См. также</span><span class="sxs-lookup"><span data-stu-id="8fdf1-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="8fdf1-137">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="8fdf1-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8fdf1-138">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="8fdf1-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
