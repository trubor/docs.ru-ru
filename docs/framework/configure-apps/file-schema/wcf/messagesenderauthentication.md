---
description: 'Дополнительные сведения: <messageSenderAuthentication>'
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e98388eafce24b0f19647364b6bbec94ee6ba135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749327"
---
# \<messageSenderAuthentication>

<span data-ttu-id="faeea-102">Задает параметры проверки подлинности для однорангового сертификата, используемого отправителем сообщения.</span><span class="sxs-lookup"><span data-stu-id="faeea-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="faeea-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="faeea-103">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faeea-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="faeea-104">Attributes and Elements</span></span>  

 <span data-ttu-id="faeea-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="faeea-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faeea-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="faeea-106">Attributes</span></span>  
  
|<span data-ttu-id="faeea-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="faeea-107">Attribute</span></span>|<span data-ttu-id="faeea-108">Описание</span><span class="sxs-lookup"><span data-stu-id="faeea-108">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="faeea-109">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="faeea-109">Optional enumeration.</span></span> <span data-ttu-id="faeea-110">Задает один из пяти режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="faeea-110">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="faeea-111">Это атрибут типа <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="faeea-111">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="faeea-112">Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="faeea-112">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="faeea-113">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="faeea-113">Optional string.</span></span> <span data-ttu-id="faeea-114">Задает тип и сборку, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="faeea-114">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="faeea-115">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="faeea-115">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="faeea-116">Это атрибут типа <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="faeea-116">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="faeea-117">Windows Communication Foundation (WCF) предоставляет средство проверки однорангового сертификата по умолчанию, которое проверяет одноранговый сертификат в хранилище доверенных лиц.</span><span class="sxs-lookup"><span data-stu-id="faeea-117">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="faeea-118">Он также проверяет цепочку сертификатов вплоть до действительного корня.</span><span class="sxs-lookup"><span data-stu-id="faeea-118">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="faeea-119">Можно реализовать пользовательский модуль проверки для задания другого поведения и использовать этот атрибут для указания на пользовательский модуль проверки.</span><span class="sxs-lookup"><span data-stu-id="faeea-119">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="faeea-120">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="faeea-120">Optional enumeration.</span></span> <span data-ttu-id="faeea-121">Задает режим отзыва сертификатов.</span><span class="sxs-lookup"><span data-stu-id="faeea-121">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="faeea-122">Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="faeea-122">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="faeea-123">Система проверяет, что одноранговый сертификат не отозван, проводя его поиск в списке отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="faeea-123">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="faeea-124">Эта проверка выполняется либо в сети, либо в кэшированном списке отзыва.</span><span class="sxs-lookup"><span data-stu-id="faeea-124">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="faeea-125">Проверку отзыва сертификатов можно отключить, задав этому атрибуту значение NoCheck.</span><span class="sxs-lookup"><span data-stu-id="faeea-125">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="faeea-126">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="faeea-126">Optional enumeration.</span></span> <span data-ttu-id="faeea-127">Указывает расположение доверенного хранилища, в котором система безопасности WCF проверяет сертификат однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="faeea-127">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="faeea-128">Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="faeea-128">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="faeea-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="faeea-129">Child Elements</span></span>  

 <span data-ttu-id="faeea-130">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="faeea-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faeea-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="faeea-131">Parent Elements</span></span>  
  
|<span data-ttu-id="faeea-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="faeea-132">Element</span></span>|<span data-ttu-id="faeea-133">Описание</span><span class="sxs-lookup"><span data-stu-id="faeea-133">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="faeea-134">Задает текущие учетные данные для однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="faeea-134">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faeea-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="faeea-135">Remarks</span></span>  

 <span data-ttu-id="faeea-136">Этот элемент должен быть настроен, если выбрана проверка подлинности сообщения.</span><span class="sxs-lookup"><span data-stu-id="faeea-136">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="faeea-137">Для выходных каналов каждое сообщение подписывается с помощью сертификата, предоставленного [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="faeea-137">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="faeea-138">Во всех сообщениях перед доставкой приложению проверяются учетные данные сообщения с помощью модуля проверки, заданного атрибутом `customCertificateValidatorType` этого элемента.</span><span class="sxs-lookup"><span data-stu-id="faeea-138">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="faeea-139">Модуль проверки может принять или отклонить учетные данные.</span><span class="sxs-lookup"><span data-stu-id="faeea-139">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeea-140">См. также</span><span class="sxs-lookup"><span data-stu-id="faeea-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="faeea-141">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="faeea-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="faeea-142">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="faeea-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="faeea-143">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="faeea-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="faeea-144">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="faeea-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="faeea-145">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="faeea-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
