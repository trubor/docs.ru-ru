---
description: 'Дополнительные сведения о: <message> element элемента <ws2007FederationHttpBinding>'
title: Элемент <message> для <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: f9116a5075f30421dfb26adc29ec0b167db33673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725458"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="13aa3-103">Элемент \<message> для \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="13aa3-103">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="13aa3-104">Определяет параметры безопасности на уровне сообщений для [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="13aa3-104">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="13aa3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13aa3-105">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13aa3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="13aa3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="13aa3-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="13aa3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13aa3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="13aa3-108">Attributes</span></span>  
  
|<span data-ttu-id="13aa3-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="13aa3-109">Attribute</span></span>|<span data-ttu-id="13aa3-110">Описание</span><span class="sxs-lookup"><span data-stu-id="13aa3-110">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="13aa3-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="13aa3-111">Optional.</span></span> <span data-ttu-id="13aa3-112">Задает алгоритмы шифрования сообщений, сигнатуры и ключей.</span><span class="sxs-lookup"><span data-stu-id="13aa3-112">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="13aa3-113">Алгоритмы и размеры ключей определяются классом <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="13aa3-113">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="13aa3-114">Эти алгоритмы соответствуют алгоритмам, заданным в спецификации языка политики безопасности (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="13aa3-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="13aa3-115">В следующей таблице приводятся возможные значения.</span><span class="sxs-lookup"><span data-stu-id="13aa3-115">See the following table for possible values.</span></span> <span data-ttu-id="13aa3-116">Значение по умолчанию - Basic256.</span><span class="sxs-lookup"><span data-stu-id="13aa3-116">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="13aa3-117">Задает тип выдаваемого ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="13aa3-118">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="13aa3-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="13aa3-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="13aa3-119">-   SymmetricKey</span></span><br /><span data-ttu-id="13aa3-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="13aa3-120">-   PublicKey</span></span><br /><span data-ttu-id="13aa3-121">-Беареркэй</span><span class="sxs-lookup"><span data-stu-id="13aa3-121">-   BearerKey</span></span><br /><br /> <span data-ttu-id="13aa3-122">Значение по умолчанию - SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="13aa3-122">The default is SymmetricKey.</span></span> <span data-ttu-id="13aa3-123">Это атрибут типа <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="13aa3-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="13aa3-124">Универсальный код ресурса (URI), который задает тип выдаваемых маркеров.</span><span class="sxs-lookup"><span data-stu-id="13aa3-124">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="13aa3-125">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="13aa3-125">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="13aa3-126">Значение, которое определяет, должен ли проводиться обмен учетными данными службы в рамках процесса согласования, или эти данные доступны вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="13aa3-126">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="13aa3-127">Значением по умолчанию является `true`, означающее, что учетные данные службы согласуются.</span><span class="sxs-lookup"><span data-stu-id="13aa3-127">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="13aa3-128">Атрибут algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="13aa3-128">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="13aa3-129">Значение</span><span class="sxs-lookup"><span data-stu-id="13aa3-129">Value</span></span>|<span data-ttu-id="13aa3-130">Описание</span><span class="sxs-lookup"><span data-stu-id="13aa3-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13aa3-131">Basic128</span><span class="sxs-lookup"><span data-stu-id="13aa3-131">Basic128</span></span>|<span data-ttu-id="13aa3-132">Используется шифрование Aes128, Sha1 для хэша и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-132">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-133">Basic192</span><span class="sxs-lookup"><span data-stu-id="13aa3-133">Basic192</span></span>|<span data-ttu-id="13aa3-134">Используется шифрование Aes192, Sha1 для хэша и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-134">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-135">Basic256</span><span class="sxs-lookup"><span data-stu-id="13aa3-135">Basic256</span></span>|<span data-ttu-id="13aa3-136">Используется шифрование Aes256, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-136">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-137">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-137">Basic256Rsa15</span></span>|<span data-ttu-id="13aa3-138">Используется Aes256 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-138">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-139">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-139">Basic192Rsa15</span></span>|<span data-ttu-id="13aa3-140">Используется Aes192 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-140">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-141">TripleDes</span><span class="sxs-lookup"><span data-stu-id="13aa3-141">TripleDes</span></span>|<span data-ttu-id="13aa3-142">Используется шифрование TripleDes, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-142">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-143">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-143">Basic128Rsa15</span></span>|<span data-ttu-id="13aa3-144">Используется Aes128 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-144">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-145">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-145">TripleDesRsa15</span></span>|<span data-ttu-id="13aa3-146">Используется TripleDes для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-146">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-147">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="13aa3-147">Basic128Sha256</span></span>|<span data-ttu-id="13aa3-148">Используется Aes256 для шифрования сообщения, Sha256 для хэша и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-148">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-149">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="13aa3-149">Basic192Sha256</span></span>|<span data-ttu-id="13aa3-150">Используется Aes192 для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-150">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-151">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="13aa3-151">Basic256Sha256</span></span>|<span data-ttu-id="13aa3-152">Используется Aes256 для шифрования сообщения, Sha256 для хэша и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-152">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-153">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="13aa3-153">TripleDesSha256</span></span>|<span data-ttu-id="13aa3-154">Используется TripleDes для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-154">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-155">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-155">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="13aa3-156">Используется Aes128 для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-156">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-157">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-157">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="13aa3-158">Используется Aes192 для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-158">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-159">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-159">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="13aa3-160">Используется Aes256 для шифрования сообщения, Sha256 для хэша и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-160">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="13aa3-161">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="13aa3-161">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="13aa3-162">Используется TripleDes для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="13aa3-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13aa3-163">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="13aa3-163">Child Elements</span></span>  
  
|<span data-ttu-id="13aa3-164">Элемент</span><span class="sxs-lookup"><span data-stu-id="13aa3-164">Element</span></span>|<span data-ttu-id="13aa3-165">Описание</span><span class="sxs-lookup"><span data-stu-id="13aa3-165">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="13aa3-166">Задает коллекцию типов утверждений для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="13aa3-166">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="13aa3-167">Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="13aa3-167">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="13aa3-168">Задает конечную точку, которая выдает маркер безопасности.</span><span class="sxs-lookup"><span data-stu-id="13aa3-168">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="13aa3-169">Это элемент типа <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="13aa3-169">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="13aa3-170">Задает адрес конечной точки издателя.</span><span class="sxs-lookup"><span data-stu-id="13aa3-170">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="13aa3-171">Коллекция параметров запроса маркера.</span><span class="sxs-lookup"><span data-stu-id="13aa3-171">A collection of token request parameters.</span></span> <span data-ttu-id="13aa3-172">Каждый параметр представляет собой элемент XML.</span><span class="sxs-lookup"><span data-stu-id="13aa3-172">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13aa3-173">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="13aa3-173">Parent Elements</span></span>  
  
|<span data-ttu-id="13aa3-174">Элемент</span><span class="sxs-lookup"><span data-stu-id="13aa3-174">Element</span></span>|<span data-ttu-id="13aa3-175">Описание</span><span class="sxs-lookup"><span data-stu-id="13aa3-175">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="13aa3-176">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="13aa3-176">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13aa3-177">См. также</span><span class="sxs-lookup"><span data-stu-id="13aa3-177">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="13aa3-178">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="13aa3-178">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="13aa3-179">Привязки</span><span class="sxs-lookup"><span data-stu-id="13aa3-179">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="13aa3-180">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="13aa3-180">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="13aa3-181">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="13aa3-181">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
