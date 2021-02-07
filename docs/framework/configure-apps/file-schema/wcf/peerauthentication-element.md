---
description: 'Дополнительные сведения о: <peerAuthentication> element'
title: Элемент <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 887b65a4a2a7da9d545bc25636be0ea6c646f6fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683727"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="71a44-103">Элемент \<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="71a44-103">\<peerAuthentication> Element</span></span>

<span data-ttu-id="71a44-104">Задает параметры проверки подлинности для одноранговых клиентов.</span><span class="sxs-lookup"><span data-stu-id="71a44-104">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="71a44-105">Дополнительные сведения о одноранговых программах см. в разделе одноранговая [сеть](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="71a44-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="71a44-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71a44-106">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71a44-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="71a44-107">Attributes and Elements</span></span>  

 <span data-ttu-id="71a44-108">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="71a44-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71a44-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="71a44-109">Attributes</span></span>  
  
|<span data-ttu-id="71a44-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="71a44-110">Attribute</span></span>|<span data-ttu-id="71a44-111">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="71a44-112">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="71a44-112">Optional string.</span></span> <span data-ttu-id="71a44-113">Тип и сборка, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="71a44-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="71a44-114">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="71a44-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="71a44-115">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="71a44-115">Optional enumeration.</span></span> <span data-ttu-id="71a44-116">Задает один из трех режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="71a44-116">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="71a44-117">Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="71a44-117">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="71a44-118">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="71a44-118">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="71a44-119">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="71a44-119">Optional enumeration.</span></span> <span data-ttu-id="71a44-120">Один из режимов, используемых для проверки списков отозванных сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="71a44-120">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="71a44-121">Значение по умолчанию — `Online`.</span><span class="sxs-lookup"><span data-stu-id="71a44-121">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="71a44-122">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="71a44-122">Optional enumeration.</span></span> <span data-ttu-id="71a44-123">Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="71a44-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="71a44-124">Данное значение используется при согласовании сертификата службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="71a44-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="71a44-125">Проверка выполняется для хранилища **доверенных лиц** в указанном расположении магазина.</span><span class="sxs-lookup"><span data-stu-id="71a44-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="71a44-126">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="71a44-126">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="71a44-127">Атрибут customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="71a44-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="71a44-128">Значение</span><span class="sxs-lookup"><span data-stu-id="71a44-128">Value</span></span>|<span data-ttu-id="71a44-129">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71a44-130">Строка</span><span class="sxs-lookup"><span data-stu-id="71a44-130">String</span></span>|<span data-ttu-id="71a44-131">Задает имя типа и сборку, а также другие данные, используемые для поиска типа.</span><span class="sxs-lookup"><span data-stu-id="71a44-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="71a44-132">Требуется, как минимум, пространство имен и имя типа.</span><span class="sxs-lookup"><span data-stu-id="71a44-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="71a44-133">К дополнительным сведениям относятся: имя сборки, номер версии, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="71a44-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="71a44-134">Атрибут certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="71a44-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="71a44-135">Значение</span><span class="sxs-lookup"><span data-stu-id="71a44-135">Value</span></span>|<span data-ttu-id="71a44-136">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71a44-137">Перечисление</span><span class="sxs-lookup"><span data-stu-id="71a44-137">Enumeration</span></span>|<span data-ttu-id="71a44-138">Одно из следующих значений: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="71a44-138">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="71a44-139">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="71a44-139">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="71a44-140">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="71a44-140">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="71a44-141">Атрибут revocationMode</span><span class="sxs-lookup"><span data-stu-id="71a44-141">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="71a44-142">Значение</span><span class="sxs-lookup"><span data-stu-id="71a44-142">Value</span></span>|<span data-ttu-id="71a44-143">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71a44-144">Перечисление</span><span class="sxs-lookup"><span data-stu-id="71a44-144">Enumeration</span></span>|<span data-ttu-id="71a44-145">Одно из следующих значений: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="71a44-145">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="71a44-146">Значение по умолчанию — `Online`.</span><span class="sxs-lookup"><span data-stu-id="71a44-146">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="71a44-147">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="71a44-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="71a44-148">Атрибут trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="71a44-148">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="71a44-149">Значение</span><span class="sxs-lookup"><span data-stu-id="71a44-149">Value</span></span>|<span data-ttu-id="71a44-150">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71a44-151">Перечисление</span><span class="sxs-lookup"><span data-stu-id="71a44-151">Enumeration</span></span>|<span data-ttu-id="71a44-152">Одно из следующих значений: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="71a44-152">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="71a44-153">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="71a44-153">The default is `CurrentUser`.</span></span> <span data-ttu-id="71a44-154">Если клиентское приложение выполняется под учетной записью системы, сертификат обычно находится в расположении `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="71a44-154">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="71a44-155">Если клиентское приложение выполняется под учетной записью пользователя, то сертификат обычно находится в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="71a44-155">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71a44-156">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="71a44-156">Child Elements</span></span>  

 <span data-ttu-id="71a44-157">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="71a44-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71a44-158">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="71a44-158">Parent Elements</span></span>  
  
|<span data-ttu-id="71a44-159">Элемент</span><span class="sxs-lookup"><span data-stu-id="71a44-159">Element</span></span>|<span data-ttu-id="71a44-160">Описание</span><span class="sxs-lookup"><span data-stu-id="71a44-160">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="71a44-161">Задает учетные данные, используемые для проверки подлинности клиента при подключении к одноранговой службе.</span><span class="sxs-lookup"><span data-stu-id="71a44-161">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71a44-162">Remarks</span><span class="sxs-lookup"><span data-stu-id="71a44-162">Remarks</span></span>  

 <span data-ttu-id="71a44-163">Элемент `<authentication>` соответствует классу <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="71a44-163">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="71a44-164">Этот элемент задает модуль проверки, который вызывается во время проверки подлинности «от соседа к соседу» в сетке.</span><span class="sxs-lookup"><span data-stu-id="71a44-164">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="71a44-165">Когда новый одноранговый узел пытается установить соединение с соседним узлом, он передает свои учетные данные в отвечающий одноранговый узел.</span><span class="sxs-lookup"><span data-stu-id="71a44-165">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="71a44-166">Для проверки учетных данных удаленной стороны вызывается проверяющий элемент управления отвечающего узла.</span><span class="sxs-lookup"><span data-stu-id="71a44-166">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="71a44-167">Как только в сетке устанавливается одноранговое соединение, оба одноранговых узла выполняют взаимную проверку подлинности. Это означает, что вызываются проверяющие элементы управления на обоих концах.</span><span class="sxs-lookup"><span data-stu-id="71a44-167">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71a44-168">Пример</span><span class="sxs-lookup"><span data-stu-id="71a44-168">Example</span></span>  

 <span data-ttu-id="71a44-169">В приведенном ниже примере кода режиму проверки сертификата присваивается значение `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="71a44-169">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="71a44-170">См. также</span><span class="sxs-lookup"><span data-stu-id="71a44-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="71a44-171">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="71a44-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="71a44-172">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="71a44-172">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="71a44-173">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="71a44-173">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="71a44-174">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="71a44-174">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="71a44-175">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="71a44-175">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
