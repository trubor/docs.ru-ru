---
description: 'Дополнительные сведения: <serviceCredentials>'
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: c6fd39226ca2235d8f8253a7d2f2e363522870e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682869"
---
# \<serviceCredentials>

<span data-ttu-id="0bd49-102">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="0bd49-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="0bd49-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bd49-103">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bd49-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0bd49-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0bd49-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0bd49-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bd49-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0bd49-106">Attributes</span></span>  
  
|<span data-ttu-id="0bd49-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0bd49-107">Attribute</span></span>|<span data-ttu-id="0bd49-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0bd49-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0bd49-109">Строка, задающая тип данного элемента конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0bd49-109">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bd49-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0bd49-110">Child Elements</span></span>  
  
|<span data-ttu-id="0bd49-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="0bd49-111">Element</span></span>|<span data-ttu-id="0bd49-112">Описание</span><span class="sxs-lookup"><span data-stu-id="0bd49-112">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="0bd49-113">Задает сертификат для использования, когда сертификат клиента доступен внештатно.</span><span class="sxs-lookup"><span data-stu-id="0bd49-113">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="0bd49-114">Этот элемент также задает параметры проверки сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="0bd49-114">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="0bd49-115">Это элемент типа <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="0bd49-116">Задает для этой службы текущий выданный маркер.</span><span class="sxs-lookup"><span data-stu-id="0bd49-116">Specifies the current issued token for this service.</span></span> <span data-ttu-id="0bd49-117">Это элемент типа <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-117">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="0bd49-118">Задает текущие учетные данные для однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="0bd49-118">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="0bd49-119">Это элемент типа <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-119">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="0bd49-120">Задает текущие учетные данные для безопасного сеанса.</span><span class="sxs-lookup"><span data-stu-id="0bd49-120">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="0bd49-121">Это элемент типа <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-121">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="0bd49-122">Задает сертификат, используемый службой для своей идентификации.</span><span class="sxs-lookup"><span data-stu-id="0bd49-122">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="0bd49-123">Это элемент типа <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-123">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="0bd49-124">Задает параметры для проверки имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="0bd49-124">Specifies the settings for username password validation.</span></span> <span data-ttu-id="0bd49-125">Это элемент типа <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-125">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="0bd49-126">Задает параметры для проверки учетных данных ОС Windows.</span><span class="sxs-lookup"><span data-stu-id="0bd49-126">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="0bd49-127">Это элемент типа <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bd49-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bd49-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0bd49-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0bd49-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="0bd49-129">Element</span></span>|<span data-ttu-id="0bd49-130">Описание</span><span class="sxs-lookup"><span data-stu-id="0bd49-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0bd49-131">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="0bd49-131">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bd49-132">См. также</span><span class="sxs-lookup"><span data-stu-id="0bd49-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="0bd49-133">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="0bd49-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
