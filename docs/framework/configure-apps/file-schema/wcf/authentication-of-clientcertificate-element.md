---
description: 'Дополнительные сведения о: <authentication> <clientCertificate> element'
title: <authentication> элемента <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 346e1012fd9d799b093be15381aebbc026ea2591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749900"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="7719d-103">\<authentication> элемента \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="7719d-103">\<authentication> of \<clientCertificate> Element</span></span>

<span data-ttu-id="7719d-104">Указывает расширения функциональности аутентификации для сертификатов клиентов, используемых службой.</span><span class="sxs-lookup"><span data-stu-id="7719d-104">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="7719d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7719d-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7719d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7719d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7719d-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7719d-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7719d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7719d-108">Attributes</span></span>  
  
|<span data-ttu-id="7719d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7719d-109">Attribute</span></span>|<span data-ttu-id="7719d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7719d-111">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="7719d-111">customCertificateValidatorType</span></span>|<span data-ttu-id="7719d-112">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="7719d-112">Optional string.</span></span> <span data-ttu-id="7719d-113">Тип и сборка, используемые для проверки пользовательского типа.</span><span class="sxs-lookup"><span data-stu-id="7719d-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7719d-114">Этот атрибут должен быть задан, когда `certificateValidationMode` имеет значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7719d-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="7719d-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7719d-115">certificateValidationMode</span></span>|<span data-ttu-id="7719d-116">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="7719d-116">Optional enumeration.</span></span> <span data-ttu-id="7719d-117">Задает один из режимов для проверки учетных данных.</span><span class="sxs-lookup"><span data-stu-id="7719d-117">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="7719d-118">Это атрибут типа <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="7719d-118">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="7719d-119">Если свойству присвоено значение <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, также необходимо указать свойство `customCertificateValidator`.</span><span class="sxs-lookup"><span data-stu-id="7719d-119">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="7719d-120">Значение по умолчанию — <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7719d-120">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="7719d-121">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="7719d-121">includeWindowsGroups</span></span>|<span data-ttu-id="7719d-122">Необязательный логический атрибут.</span><span class="sxs-lookup"><span data-stu-id="7719d-122">Optional Boolean.</span></span> <span data-ttu-id="7719d-123">Указывает, включены ли группы Windows в контекст безопасности.</span><span class="sxs-lookup"><span data-stu-id="7719d-123">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="7719d-124">Установка для этого атрибута значения `true` снижает производительность, поскольку приводит к расширению всей группы.</span><span class="sxs-lookup"><span data-stu-id="7719d-124">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="7719d-125">Если нет необходимости устанавливать список групп, к которым принадлежит пользователь, установите для этого атрибута значение `false`.</span><span class="sxs-lookup"><span data-stu-id="7719d-125">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="7719d-126">мапклиентцертификатетовиндовсаккаунт</span><span class="sxs-lookup"><span data-stu-id="7719d-126">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="7719d-127">Логическое.</span><span class="sxs-lookup"><span data-stu-id="7719d-127">Boolean.</span></span> <span data-ttu-id="7719d-128">Указывает, может ли клиент сопоставляться с удостоверением Windows с помощью сертификата.</span><span class="sxs-lookup"><span data-stu-id="7719d-128">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="7719d-129">Для этого необходимо включить службу Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7719d-129">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="7719d-130">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7719d-130">revocationMode</span></span>|<span data-ttu-id="7719d-131">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="7719d-131">Optional enumeration.</span></span> <span data-ttu-id="7719d-132">Один из режимов, используемых для проверки списков отозванных сертификатов (RCL).</span><span class="sxs-lookup"><span data-stu-id="7719d-132">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="7719d-133">Значение по умолчанию — `Online`.</span><span class="sxs-lookup"><span data-stu-id="7719d-133">The default is `Online`.</span></span> <span data-ttu-id="7719d-134">Это значение не учитывается при использовании безопасности транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="7719d-134">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="7719d-135">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7719d-135">trustedStoreLocation</span></span>|<span data-ttu-id="7719d-136">Необязательное перечисление.</span><span class="sxs-lookup"><span data-stu-id="7719d-136">Optional enumeration.</span></span> <span data-ttu-id="7719d-137">Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7719d-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7719d-138">Данное значение используется при согласовании сертификата службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="7719d-138">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7719d-139">Проверка выполняется для хранилища **доверенных лиц** в указанном расположении магазина.</span><span class="sxs-lookup"><span data-stu-id="7719d-139">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="7719d-140">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7719d-140">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="7719d-141">Атрибут customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="7719d-141">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="7719d-142">Значение</span><span class="sxs-lookup"><span data-stu-id="7719d-142">Value</span></span>|<span data-ttu-id="7719d-143">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7719d-144">Строка</span><span class="sxs-lookup"><span data-stu-id="7719d-144">String</span></span>|<span data-ttu-id="7719d-145">Задает имя типа и сборку, а также другие данные, используемые для поиска типа.</span><span class="sxs-lookup"><span data-stu-id="7719d-145">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7719d-146">Атрибут certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7719d-146">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7719d-147">Значение</span><span class="sxs-lookup"><span data-stu-id="7719d-147">Value</span></span>|<span data-ttu-id="7719d-148">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7719d-149">Перечисление</span><span class="sxs-lookup"><span data-stu-id="7719d-149">Enumeration</span></span>|<span data-ttu-id="7719d-150">Одно из следующих значений: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="7719d-150">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="7719d-151">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7719d-151">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7719d-152">Атрибут revocationMode</span><span class="sxs-lookup"><span data-stu-id="7719d-152">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7719d-153">Значение</span><span class="sxs-lookup"><span data-stu-id="7719d-153">Value</span></span>|<span data-ttu-id="7719d-154">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7719d-155">Перечисление</span><span class="sxs-lookup"><span data-stu-id="7719d-155">Enumeration</span></span>|<span data-ttu-id="7719d-156">Одно из следующих значений: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="7719d-156">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="7719d-157">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7719d-157">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7719d-158">Атрибут trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7719d-158">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7719d-159">Значение</span><span class="sxs-lookup"><span data-stu-id="7719d-159">Value</span></span>|<span data-ttu-id="7719d-160">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7719d-161">Перечисление</span><span class="sxs-lookup"><span data-stu-id="7719d-161">Enumeration</span></span>|<span data-ttu-id="7719d-162">Одно из следующих значений: `LocalMachine` или `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7719d-162">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7719d-163">Значение по умолчанию — `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7719d-163">The default is `CurrentUser`.</span></span> <span data-ttu-id="7719d-164">Если клиентское приложение выполняется под учетной записью системы, сертификат обычно находится в расположении `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="7719d-164">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="7719d-165">Если клиентское приложение выполняется под учетной записью пользователя, то сертификат обычно находится в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7719d-165">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7719d-166">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7719d-166">Child Elements</span></span>  

 <span data-ttu-id="7719d-167">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7719d-167">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7719d-168">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7719d-168">Parent Elements</span></span>  
  
|<span data-ttu-id="7719d-169">Элемент</span><span class="sxs-lookup"><span data-stu-id="7719d-169">Element</span></span>|<span data-ttu-id="7719d-170">Описание</span><span class="sxs-lookup"><span data-stu-id="7719d-170">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="7719d-171">Определяет сертификат X.509, используемый для проверки подлинности клиента по отношению к службе.</span><span class="sxs-lookup"><span data-stu-id="7719d-171">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7719d-172">Remarks</span><span class="sxs-lookup"><span data-stu-id="7719d-172">Remarks</span></span>  

 <span data-ttu-id="7719d-173">Элемент `<authentication>` соответствует классу <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="7719d-173">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="7719d-174">Это дает возможность настраивать способ проверки подлинности клиентов.</span><span class="sxs-lookup"><span data-stu-id="7719d-174">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="7719d-175">Для атрибута `certificateValidationMode` можно задать значение `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust` или `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7719d-175">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="7719d-176">По умолчанию уровень имеет значение `ChainTrust` , которое указывает, что каждый сертификат должен быть найден в иерархии сертификатов, которые заканчиваются *корневым центром* в верхней части цепочки.</span><span class="sxs-lookup"><span data-stu-id="7719d-176">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="7719d-177">Это наиболее безопасный режим.</span><span class="sxs-lookup"><span data-stu-id="7719d-177">This is the most secure mode.</span></span> <span data-ttu-id="7719d-178">Также можно установить значение `PeerOrChainTrust`, в этом случае будут приниматься как самостоятельно выдаваемые сертификаты (доверие одноранговой группы), так и сертификаты, которые находятся в цепи доверия.</span><span class="sxs-lookup"><span data-stu-id="7719d-178">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="7719d-179">Данное значение используется при разработке и отладке клиентов и служб, так как самостоятельно выданные сертификаты не нужно приобретать у доверенного центра сертификации.</span><span class="sxs-lookup"><span data-stu-id="7719d-179">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="7719d-180">При развертывании клиента вместо этого значения следует использовать значение `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7719d-180">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="7719d-181">Также можно установить значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7719d-181">You can also set the value to `Custom`.</span></span> <span data-ttu-id="7719d-182">При установке значения `Custom` необходимо также задать атрибут `customCertificateValidatorType` для сборки и тип, который используется при проверке сертификата.</span><span class="sxs-lookup"><span data-stu-id="7719d-182">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="7719d-183">Для создания собственного пользовательского модуля проверки необходимо наследование от абстрактного класса <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="7719d-183">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="7719d-184">Дополнительные сведения см. [в разделе инструкции. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="7719d-184">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7719d-185">Пример</span><span class="sxs-lookup"><span data-stu-id="7719d-185">Example</span></span>  

 <span data-ttu-id="7719d-186">В следующем примере кода задается сертификат X.509 и пользовательский тип проверки в элементе `<authentication>`.</span><span class="sxs-lookup"><span data-stu-id="7719d-186">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="7719d-187">См. также</span><span class="sxs-lookup"><span data-stu-id="7719d-187">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="7719d-188">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="7719d-188">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7719d-189">Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов</span><span class="sxs-lookup"><span data-stu-id="7719d-189">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="7719d-190">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="7719d-190">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
