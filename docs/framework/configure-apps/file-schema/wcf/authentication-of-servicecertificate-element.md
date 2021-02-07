---
description: 'Дополнительные сведения о: <authentication> <serviceCertificate> element'
title: <authentication> элемента <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 35a94f4f9c089f86aef38e7e9a1115a7cd22a325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749887"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="6287e-103">\<authentication> элемента \<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="6287e-103">\<authentication> of \<serviceCertificate> Element</span></span>

<span data-ttu-id="6287e-104">Задает параметры, которые использует прокси клиента для проверки подлинности сертификатов службы, полученных при помощи согласования SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="6287e-104">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="6287e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6287e-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6287e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6287e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6287e-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6287e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6287e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6287e-108">Attributes</span></span>  
  
|<span data-ttu-id="6287e-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="6287e-109">Attribute</span></span>|<span data-ttu-id="6287e-110">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6287e-111">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="6287e-111">customCertificateValidatorType</span></span>|<span data-ttu-id="6287e-112">Строка.</span><span class="sxs-lookup"><span data-stu-id="6287e-112">String.</span></span> <span data-ttu-id="6287e-113">Тип и сборка, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="6287e-113">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="6287e-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="6287e-114">certificateValidationMode</span></span>|<span data-ttu-id="6287e-115">Задает один из трех режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="6287e-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6287e-116">Если задано значение `Custom`, также необходимо предоставить customCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="6287e-116">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="6287e-117">Значение по умолчанию — `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6287e-117">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="6287e-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6287e-118">revocationMode</span></span>|<span data-ttu-id="6287e-119">Один из режимов, используемых для проверки списков отозванных сертификатов (CRL).</span><span class="sxs-lookup"><span data-stu-id="6287e-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="6287e-120">Значение по умолчанию — `Online`.</span><span class="sxs-lookup"><span data-stu-id="6287e-120">The default is `Online`.</span></span>|  
|<span data-ttu-id="6287e-121">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6287e-121">trustedStoreLocation</span></span>|<span data-ttu-id="6287e-122">Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6287e-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6287e-123">Данное значение используется при согласовании сертификата службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="6287e-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6287e-124">Проверка выполняется для хранилища **доверенных лиц** в указанном расположении магазина.</span><span class="sxs-lookup"><span data-stu-id="6287e-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="6287e-125">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6287e-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="6287e-126">Атрибут customCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="6287e-126">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="6287e-127">Значение</span><span class="sxs-lookup"><span data-stu-id="6287e-127">Value</span></span>|<span data-ttu-id="6287e-128">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6287e-129">Строка</span><span class="sxs-lookup"><span data-stu-id="6287e-129">String</span></span>|<span data-ttu-id="6287e-130">Задает имя типа и сборку, а также другие данные, используемые для поиска типа.</span><span class="sxs-lookup"><span data-stu-id="6287e-130">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6287e-131">Атрибут certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="6287e-131">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6287e-132">Значение</span><span class="sxs-lookup"><span data-stu-id="6287e-132">Value</span></span>|<span data-ttu-id="6287e-133">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6287e-134">Перечисление</span><span class="sxs-lookup"><span data-stu-id="6287e-134">Enumeration</span></span>|<span data-ttu-id="6287e-135">Одно из следующих значений: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="6287e-135">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="6287e-136">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6287e-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6287e-137">Атрибут revocationMode</span><span class="sxs-lookup"><span data-stu-id="6287e-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6287e-138">Значение</span><span class="sxs-lookup"><span data-stu-id="6287e-138">Value</span></span>|<span data-ttu-id="6287e-139">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6287e-140">Перечисление</span><span class="sxs-lookup"><span data-stu-id="6287e-140">Enumeration</span></span>|<span data-ttu-id="6287e-141">Одно из следующих значений: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="6287e-141">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="6287e-142">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6287e-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6287e-143">Атрибут trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6287e-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6287e-144">Значение</span><span class="sxs-lookup"><span data-stu-id="6287e-144">Value</span></span>|<span data-ttu-id="6287e-145">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6287e-146">Перечисление</span><span class="sxs-lookup"><span data-stu-id="6287e-146">Enumeration</span></span>|<span data-ttu-id="6287e-147">Одно из следующих значений: LocalMachine или CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6287e-147">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="6287e-148">Значение по умолчанию — CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6287e-148">The default is CurrentUser.</span></span> <span data-ttu-id="6287e-149">Если клиентское приложение выполняется в контексте системной учетной записи, сертификат обычно находится в LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="6287e-149">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="6287e-150">Если клиентское приложение выполняется в контексте учетной записи пользователя, то сертификат обычно находится в CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6287e-150">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6287e-151">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6287e-151">Child Elements</span></span>  

 <span data-ttu-id="6287e-152">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6287e-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6287e-153">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6287e-153">Parent Elements</span></span>  
  
|<span data-ttu-id="6287e-154">Элемент</span><span class="sxs-lookup"><span data-stu-id="6287e-154">Element</span></span>|<span data-ttu-id="6287e-155">Описание</span><span class="sxs-lookup"><span data-stu-id="6287e-155">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="6287e-156">Задает сертификат для использования при проверке подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="6287e-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6287e-157">Remarks</span><span class="sxs-lookup"><span data-stu-id="6287e-157">Remarks</span></span>  

 <span data-ttu-id="6287e-158">Атрибут `certificateValidationMode` данного элемента конфигурации указывает уровень доверия, который используется при проверке подлинности сертификатов.</span><span class="sxs-lookup"><span data-stu-id="6287e-158">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="6287e-159">По умолчанию для уровня устанавливается значение `ChainTrust`, которое указывает, что каждый сертификат должен находиться в иерархии сертификатов, которая на самом верху цепи завершается доверенным центром сертификации.</span><span class="sxs-lookup"><span data-stu-id="6287e-159">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="6287e-160">Это наиболее безопасный режим.</span><span class="sxs-lookup"><span data-stu-id="6287e-160">This is the most secure mode.</span></span> <span data-ttu-id="6287e-161">Также можно установить значение `PeerOrChainTrust`, в этом случае будут приниматься как самостоятельно выдаваемые сертификаты (доверие одноранговой группы), так и сертификаты, которые находятся в цепи доверия.</span><span class="sxs-lookup"><span data-stu-id="6287e-161">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="6287e-162">Данное значение используется при разработке и отладке клиентов и служб, так как самостоятельно выданные сертификаты не нужно приобретать у доверенного центра сертификации.</span><span class="sxs-lookup"><span data-stu-id="6287e-162">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="6287e-163">При развертывании клиента вместо этого значения следует использовать значение `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6287e-163">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="6287e-164">Также можно задать значение `Custom` или `None`.</span><span class="sxs-lookup"><span data-stu-id="6287e-164">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="6287e-165">Чтобы использовать значение `Custom`, необходимо также установить атрибут `customCertificateValidator` для сборки и типа, которые используются при проверке сертификата.</span><span class="sxs-lookup"><span data-stu-id="6287e-165">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="6287e-166">Для создания собственного пользовательского проверяющего элемента управления необходимо унаследовать его от абстрактного класса X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="6287e-166">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="6287e-167">Дополнительные сведения см. [в разделе инструкции. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="6287e-167">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="6287e-168">Атрибут `revocationMode` указывает способ проверки отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="6287e-168">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="6287e-169">По умолчанию используется значение `online`, которое указывает, что проверка, является ли сертификат отозванным, будет выполняться автоматически.</span><span class="sxs-lookup"><span data-stu-id="6287e-169">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="6287e-170">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6287e-170">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6287e-171">Пример</span><span class="sxs-lookup"><span data-stu-id="6287e-171">Example</span></span>  

 <span data-ttu-id="6287e-172">В следующем примере выполняется две задачи.</span><span class="sxs-lookup"><span data-stu-id="6287e-172">The following example does two tasks.</span></span> <span data-ttu-id="6287e-173">Сначала он указывает сертификат службы, который будет использоваться клиентом при взаимодействии с конечными точками, доменное имя которых находится `www.contoso.com` по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="6287e-173">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="6287e-174">Во-вторых, в этом примере указывается режим отзыва и место хранения, которые используются при проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="6287e-174">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="6287e-175">См. также</span><span class="sxs-lookup"><span data-stu-id="6287e-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="6287e-176">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="6287e-176">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6287e-177">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="6287e-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6287e-178">Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов</span><span class="sxs-lookup"><span data-stu-id="6287e-178">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="6287e-179">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="6287e-179">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6287e-180">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="6287e-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
