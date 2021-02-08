---
description: 'Дополнительные сведения о: <message> element элемента <wsFederationHttpBinding>'
title: Элемент <message> для <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 64978902081ec9e5a603804fed3b378da12fe42e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802194"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="e3d49-103">Элемент \<message> для \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e3d49-103">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="e3d49-104">Определяет параметры безопасности на уровне сообщений для [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e3d49-104">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="e3d49-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3d49-105">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3d49-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e3d49-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e3d49-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e3d49-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3d49-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e3d49-108">Attributes</span></span>  
  
|<span data-ttu-id="e3d49-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e3d49-109">Attribute</span></span>|<span data-ttu-id="e3d49-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e3d49-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3d49-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e3d49-111">algorithmSuite</span></span>|<span data-ttu-id="e3d49-112">Задает алгоритмы шифрования сообщений и ключей.</span><span class="sxs-lookup"><span data-stu-id="e3d49-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e3d49-113">Допустимые значения этого атрибута см. в таблице «Атрибут algorithmSuite».</span><span class="sxs-lookup"><span data-stu-id="e3d49-113">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="e3d49-114">Значение по умолчанию — `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="e3d49-114">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="e3d49-115">Это атрибут типа <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="e3d49-115">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="e3d49-116">Эти алгоритмы соответствуют алгоритмам, заданным в спецификации языка политики безопасности (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="e3d49-116">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="e3d49-117">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="e3d49-117">issuedKeyType</span></span>|<span data-ttu-id="e3d49-118">Задает тип выдаваемого ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-118">Specifies the type of key to be issued.</span></span> <span data-ttu-id="e3d49-119">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="e3d49-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e3d49-120">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="e3d49-120">-   SymmetricKey</span></span><br /><span data-ttu-id="e3d49-121">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="e3d49-121">-   PublicKey</span></span><br /><br /> <span data-ttu-id="e3d49-122">Значение по умолчанию — `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="e3d49-122">The default is `SymmetricKey`.</span></span> <span data-ttu-id="e3d49-123">Это атрибут типа <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="e3d49-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="e3d49-124">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="e3d49-124">issuedTokenType</span></span>|<span data-ttu-id="e3d49-125">Строка, содержащая универсальный код ресурса (URI), который задает тип выдаваемых маркеров.</span><span class="sxs-lookup"><span data-stu-id="e3d49-125">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="e3d49-126">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="e3d49-126">The default is `null`.</span></span>|  
|<span data-ttu-id="e3d49-127">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="e3d49-127">negotiateServiceCredential</span></span>|<span data-ttu-id="e3d49-128">Логическое значение, которое определяет, должен ли проводиться обмен учетными данными службы в рамках процесса согласования, или допустимо использование внештатного канала.</span><span class="sxs-lookup"><span data-stu-id="e3d49-128">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="e3d49-129">Значением по умолчанию является `true`, означающее, что учетные данные службы согласуются.</span><span class="sxs-lookup"><span data-stu-id="e3d49-129">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="e3d49-130">Атрибут algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e3d49-130">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="e3d49-131">Значение</span><span class="sxs-lookup"><span data-stu-id="e3d49-131">Value</span></span>|<span data-ttu-id="e3d49-132">Описание</span><span class="sxs-lookup"><span data-stu-id="e3d49-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3d49-133">Basic128</span><span class="sxs-lookup"><span data-stu-id="e3d49-133">Basic128</span></span>|<span data-ttu-id="e3d49-134">Используется шифрование Basic128, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-134">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-135">Basic192</span><span class="sxs-lookup"><span data-stu-id="e3d49-135">Basic192</span></span>|<span data-ttu-id="e3d49-136">Используется шифрование Basic192, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-136">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-137">Basic256</span><span class="sxs-lookup"><span data-stu-id="e3d49-137">Basic256</span></span>|<span data-ttu-id="e3d49-138">Используется шифрование Basic256, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-138">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-139">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-139">Basic256Rsa15</span></span>|<span data-ttu-id="e3d49-140">Используется Basic256 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-140">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-141">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-141">Basic192Rsa15</span></span>|<span data-ttu-id="e3d49-142">Используется Basic192 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-142">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-143">TripleDes</span><span class="sxs-lookup"><span data-stu-id="e3d49-143">TripleDes</span></span>|<span data-ttu-id="e3d49-144">Используется шифрование TripleDes, Sha1 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-144">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-145">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-145">Basic128Rsa15</span></span>|<span data-ttu-id="e3d49-146">Используется Basic128 для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-146">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-147">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-147">TripleDesRsa15</span></span>|<span data-ttu-id="e3d49-148">Используется TripleDes для шифрования сообщения, Sha1 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-148">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-149">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="e3d49-149">Basic128Sha256</span></span>|<span data-ttu-id="e3d49-150">Используется Basic128 для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-150">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-151">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="e3d49-151">Basic192Sha256</span></span>|<span data-ttu-id="e3d49-152">Используется Basic192 для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-152">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-153">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="e3d49-153">Basic256Sha256</span></span>|<span data-ttu-id="e3d49-154">Используется Basic256 для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-154">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-155">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="e3d49-155">TripleDesSha256</span></span>|<span data-ttu-id="e3d49-156">Используется TripleDes для шифрования сообщения, Sha256 для хэш-кода и Rsa-oaep-mgf1p для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-156">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-157">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-157">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="e3d49-158">Используется Basic128 для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-158">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-159">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-159">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="e3d49-160">Используется Aes192 для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-160">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-161">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-161">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="e3d49-162">Используется Basic256 для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-162">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e3d49-163">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e3d49-163">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="e3d49-164">Используется TripleDes для шифрования сообщения, Sha256 для хэш-кода и Rsa15 для шифрования ключа.</span><span class="sxs-lookup"><span data-stu-id="e3d49-164">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3d49-165">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e3d49-165">Child Elements</span></span>  
  
|<span data-ttu-id="e3d49-166">Элемент</span><span class="sxs-lookup"><span data-stu-id="e3d49-166">Element</span></span>|<span data-ttu-id="e3d49-167">Описание</span><span class="sxs-lookup"><span data-stu-id="e3d49-167">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="e3d49-168">Задает коллекцию типов утверждений для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="e3d49-168">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="e3d49-169">Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e3d49-169">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="e3d49-170">issuer</span><span class="sxs-lookup"><span data-stu-id="e3d49-170">issuer</span></span>|<span data-ttu-id="e3d49-171">Задает конечную точку, которая выдает маркер безопасности.</span><span class="sxs-lookup"><span data-stu-id="e3d49-171">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="e3d49-172">Это элемент типа <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="e3d49-172">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="e3d49-173">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="e3d49-173">issuerMetadata</span></span>|<span data-ttu-id="e3d49-174">Задает адрес конечной точки издателя.</span><span class="sxs-lookup"><span data-stu-id="e3d49-174">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="e3d49-175">Коллекция параметров запроса маркера.</span><span class="sxs-lookup"><span data-stu-id="e3d49-175">A collection of token request parameters.</span></span> <span data-ttu-id="e3d49-176">Каждый параметр представляет собой элемент XML.</span><span class="sxs-lookup"><span data-stu-id="e3d49-176">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3d49-177">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e3d49-177">Parent Elements</span></span>  
  
|<span data-ttu-id="e3d49-178">Элемент</span><span class="sxs-lookup"><span data-stu-id="e3d49-178">Element</span></span>|<span data-ttu-id="e3d49-179">Описание</span><span class="sxs-lookup"><span data-stu-id="e3d49-179">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="e3d49-180">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="e3d49-180">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3d49-181">См. также</span><span class="sxs-lookup"><span data-stu-id="e3d49-181">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="e3d49-182">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="e3d49-182">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e3d49-183">Привязки</span><span class="sxs-lookup"><span data-stu-id="e3d49-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e3d49-184">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="e3d49-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e3d49-185">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="e3d49-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
