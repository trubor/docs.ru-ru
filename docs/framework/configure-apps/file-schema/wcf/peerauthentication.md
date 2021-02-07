---
description: 'Дополнительные сведения: <peerAuthentication>'
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b640b4aac296c40fadcc5f4070ba58e5f92fd265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683662"
---
# \<peerAuthentication>

<span data-ttu-id="1e2af-102">Задает параметры проверки подлинности для сертификата однорангового узла, используемого одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="1e2af-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="1e2af-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e2af-103">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e2af-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1e2af-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1e2af-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1e2af-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e2af-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1e2af-106">Attributes</span></span>  
  
|<span data-ttu-id="1e2af-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1e2af-107">Attribute</span></span>|<span data-ttu-id="1e2af-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1e2af-108">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="1e2af-109">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="1e2af-109">Optional enumeration.</span></span> <span data-ttu-id="1e2af-110">Задает один из трех режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="1e2af-110">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1e2af-111">Это атрибут типа <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="1e2af-111">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="1e2af-112">Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="1e2af-112">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="1e2af-113">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="1e2af-113">Optional string.</span></span> <span data-ttu-id="1e2af-114">Задает тип и сборку, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="1e2af-114">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1e2af-115">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="1e2af-115">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="1e2af-116">Это атрибут типа <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="1e2af-116">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1e2af-117">Windows Communication Foundation (WCF) предоставляет средство проверки однорангового сертификата по умолчанию, которое проверяет одноранговый сертификат в хранилище доверенных лиц.</span><span class="sxs-lookup"><span data-stu-id="1e2af-117">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="1e2af-118">Он также проверяет цепочку сертификатов вплоть до действительного корня.</span><span class="sxs-lookup"><span data-stu-id="1e2af-118">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="1e2af-119">Можно реализовать пользовательский модуль проверки для задания другого поведения и использовать этот атрибут для указания на пользовательский модуль проверки.</span><span class="sxs-lookup"><span data-stu-id="1e2af-119">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="1e2af-120">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="1e2af-120">Optional enumeration.</span></span> <span data-ttu-id="1e2af-121">Задает режим отзыва сертификатов.</span><span class="sxs-lookup"><span data-stu-id="1e2af-121">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="1e2af-122">Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="1e2af-122">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="1e2af-123">Система проверяет, что одноранговый сертификат не отозван, проводя его поиск в списке отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="1e2af-123">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="1e2af-124">Эта проверка выполняется либо в сети, либо в кэшированном списке отзыва.</span><span class="sxs-lookup"><span data-stu-id="1e2af-124">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="1e2af-125">Проверку отзыва сертификатов можно отключить, задав этому атрибуту значение NoCheck.</span><span class="sxs-lookup"><span data-stu-id="1e2af-125">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="1e2af-126">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="1e2af-126">Optional enumeration.</span></span> <span data-ttu-id="1e2af-127">Указывает расположение доверенного хранилища, в котором система безопасности WCF проверяет сертификат однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="1e2af-127">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="1e2af-128">Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="1e2af-128">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e2af-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1e2af-129">Child Elements</span></span>  

 <span data-ttu-id="1e2af-130">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1e2af-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e2af-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1e2af-131">Parent Elements</span></span>  
  
|<span data-ttu-id="1e2af-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="1e2af-132">Element</span></span>|<span data-ttu-id="1e2af-133">Описание</span><span class="sxs-lookup"><span data-stu-id="1e2af-133">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="1e2af-134">Задает текущие учетные данные для однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="1e2af-134">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e2af-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e2af-135">Remarks</span></span>  

 <span data-ttu-id="1e2af-136">Элемент `<authentication>` соответствует классу <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="1e2af-136">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="1e2af-137">Этот элемент задает модуль проверки, который вызывается во время проверки подлинности «от соседа к соседу» в сетке.</span><span class="sxs-lookup"><span data-stu-id="1e2af-137">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="1e2af-138">Когда новый одноранговый узел пытается установить соединение с соседним узлом, он передает свои учетные данные в отвечающий одноранговый узел.</span><span class="sxs-lookup"><span data-stu-id="1e2af-138">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="1e2af-139">Для проверки учетных данных удаленной стороны вызывается проверяющий элемент управления отвечающего узла.</span><span class="sxs-lookup"><span data-stu-id="1e2af-139">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="1e2af-140">Как только в сетке устанавливается одноранговое соединение, оба одноранговых узла выполняют взаимную проверку подлинности. Это означает, что вызываются проверяющие элементы управления на обоих концах.</span><span class="sxs-lookup"><span data-stu-id="1e2af-140">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2af-141">См. также</span><span class="sxs-lookup"><span data-stu-id="1e2af-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="1e2af-142">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="1e2af-142">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1e2af-143">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="1e2af-143">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="1e2af-144">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e2af-144">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1e2af-145">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e2af-145">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1e2af-146">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="1e2af-146">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
