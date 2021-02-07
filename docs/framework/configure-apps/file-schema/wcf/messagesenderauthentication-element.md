---
description: 'Дополнительные сведения о: <messageSenderAuthentication> element'
title: <messageSenderAuthentication> - элемент
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 03c1cd626e7c3ad71026c076df3d757419810d74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749341"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="b11a3-103">Элемент \<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="b11a3-103">\<messageSenderAuthentication> element</span></span>

<span data-ttu-id="b11a3-104">Задает параметры проверки подлинности для одноранговых отправителей сообщений.</span><span class="sxs-lookup"><span data-stu-id="b11a3-104">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="b11a3-105">Дополнительные сведения о одноранговых программах см. в разделе одноранговая [сеть](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="b11a3-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="b11a3-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b11a3-106">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b11a3-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b11a3-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b11a3-108">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b11a3-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b11a3-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b11a3-109">Attributes</span></span>  
  
|<span data-ttu-id="b11a3-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b11a3-110">Attribute</span></span>|<span data-ttu-id="b11a3-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="b11a3-112">Тип и сборка, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="b11a3-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="b11a3-113">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="b11a3-114">Задает один из трех режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="b11a3-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="b11a3-115">Если свойству присвоено значение `Custom`, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-115">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="b11a3-116">Один из режимов, используемых для проверки списков отозванных сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="b11a3-116">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="b11a3-117">Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-117">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b11a3-118">Данное значение используется при согласовании сертификата службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="b11a3-118">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="b11a3-119">Проверка выполняется для хранилища **доверенных лиц** в указанном расположении магазина.</span><span class="sxs-lookup"><span data-stu-id="b11a3-119">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="b11a3-120">Атрибут customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="b11a3-120">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="b11a3-121">Значение</span><span class="sxs-lookup"><span data-stu-id="b11a3-121">Value</span></span>|<span data-ttu-id="b11a3-122">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b11a3-123">Строка</span><span class="sxs-lookup"><span data-stu-id="b11a3-123">String</span></span>|<span data-ttu-id="b11a3-124">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="b11a3-124">Optional.</span></span> <span data-ttu-id="b11a3-125">Задает имя типа и сборку, а также другие данные, используемые для поиска типа.</span><span class="sxs-lookup"><span data-stu-id="b11a3-125">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="b11a3-126">Требуется, как минимум, пространство имен и имя типа.</span><span class="sxs-lookup"><span data-stu-id="b11a3-126">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="b11a3-127">К дополнительным сведениям относятся: имя сборки, номер версии, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="b11a3-127">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="b11a3-128">Атрибут certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b11a3-128">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="b11a3-129">Значение</span><span class="sxs-lookup"><span data-stu-id="b11a3-129">Value</span></span>|<span data-ttu-id="b11a3-130">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b11a3-131">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b11a3-131">Enumeration</span></span>|<span data-ttu-id="b11a3-132">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b11a3-132">Optional.</span></span> <span data-ttu-id="b11a3-133">Одно из следующих значений: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-133">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="b11a3-134">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-134">The default is `ChainTrust`.</span></span> <span data-ttu-id="b11a3-135">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-135">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="b11a3-136">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b11a3-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="b11a3-137">Атрибут revocationMode</span><span class="sxs-lookup"><span data-stu-id="b11a3-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="b11a3-138">Значение</span><span class="sxs-lookup"><span data-stu-id="b11a3-138">Value</span></span>|<span data-ttu-id="b11a3-139">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b11a3-140">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b11a3-140">Enumeration</span></span>|<span data-ttu-id="b11a3-141">Одно из следующих значений: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-141">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="b11a3-142">Значение по умолчанию — `Online`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-142">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="b11a3-143">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b11a3-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="b11a3-144">Атрибут trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b11a3-144">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="b11a3-145">Значение</span><span class="sxs-lookup"><span data-stu-id="b11a3-145">Value</span></span>|<span data-ttu-id="b11a3-146">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b11a3-147">Перечисление</span><span class="sxs-lookup"><span data-stu-id="b11a3-147">Enumeration</span></span>|<span data-ttu-id="b11a3-148">Одно из следующих значений: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-148">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b11a3-149">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-149">The default is `CurrentUser`.</span></span> <span data-ttu-id="b11a3-150">Если клиентское приложение выполняется под учетной записью системы, сертификат обычно находится в расположении `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-150">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="b11a3-151">Если клиентское приложение выполняется под учетной записью пользователя, то сертификат обычно находится в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-151">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="b11a3-152">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-152">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b11a3-153">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b11a3-153">Child Elements</span></span>  

 <span data-ttu-id="b11a3-154">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b11a3-154">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b11a3-155">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b11a3-155">Parent Elements</span></span>  
  
|<span data-ttu-id="b11a3-156">Элемент</span><span class="sxs-lookup"><span data-stu-id="b11a3-156">Element</span></span>|<span data-ttu-id="b11a3-157">Описание</span><span class="sxs-lookup"><span data-stu-id="b11a3-157">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="b11a3-158">Задает учетные данные, используемые для проверки подлинности клиента при подключении к одноранговой службе.</span><span class="sxs-lookup"><span data-stu-id="b11a3-158">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b11a3-159">Remarks</span><span class="sxs-lookup"><span data-stu-id="b11a3-159">Remarks</span></span>  

 <span data-ttu-id="b11a3-160">Этот элемент должен быть настроен, если выбрана проверка подлинности сообщения.</span><span class="sxs-lookup"><span data-stu-id="b11a3-160">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="b11a3-161">Для выходных каналов каждое сообщение подписывается с помощью сертификата, предоставленного [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b11a3-161">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="b11a3-162">Во всех сообщениях перед доставкой приложению проверяются учетные данные сообщения с помощью модуля проверки, заданного атрибутом `customCertificateValidatorType` этого элемента.</span><span class="sxs-lookup"><span data-stu-id="b11a3-162">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="b11a3-163">Модуль проверки может принять или отклонить учетные данные.</span><span class="sxs-lookup"><span data-stu-id="b11a3-163">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b11a3-164">Пример</span><span class="sxs-lookup"><span data-stu-id="b11a3-164">Example</span></span>  

 <span data-ttu-id="b11a3-165">В приведенном ниже примере кода устанавливается режим проверки отправителя сообщения `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b11a3-165">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="b11a3-166">См. также</span><span class="sxs-lookup"><span data-stu-id="b11a3-166">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="b11a3-167">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="b11a3-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b11a3-168">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="b11a3-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="b11a3-169">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b11a3-169">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="b11a3-170">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b11a3-170">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="b11a3-171">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="b11a3-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
