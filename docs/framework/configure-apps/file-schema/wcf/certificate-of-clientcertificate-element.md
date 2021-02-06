---
description: 'Дополнительные сведения о: <certificate> <clientCertificate> element'
title: <certificate> элемента <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: a677c04055016c77794dd99a8c237b5eb6c13f5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639098"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="5d885-103">\<certificate> элемента \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="5d885-103">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="5d885-104">Указывает сертификат X.509, используемый для подписания и шифрования сообщений.</span><span class="sxs-lookup"><span data-stu-id="5d885-104">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5d885-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d885-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d885-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5d885-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5d885-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5d885-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d885-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5d885-108">Attributes</span></span>  
  
|<span data-ttu-id="5d885-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5d885-109">Attribute</span></span>|<span data-ttu-id="5d885-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5d885-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="5d885-111">Строка, содержащая значение для поиска в хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="5d885-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="5d885-112">Тип, указанный в атрибуте, должен отвечать требованиям заданного значения X509FindType.</span><span class="sxs-lookup"><span data-stu-id="5d885-112">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="5d885-113">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="5d885-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="5d885-114">Задает расположение хранилища сертификатов Х.509, которое клиент использует для проверки сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="5d885-114">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="5d885-115">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5d885-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d885-116">-LocalMachine — хранилище сертификатов, назначенное локальному компьютеру.</span><span class="sxs-lookup"><span data-stu-id="5d885-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="5d885-117">-CurrentUser: хранилище сертификатов, назначенное текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="5d885-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="5d885-118">По умолчанию используется значение LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5d885-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="5d885-119">Задает имя открываемого хранилища сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="5d885-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="5d885-120">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5d885-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d885-121">-AddressBook: хранилище сертификатов для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="5d885-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="5d885-122">-Аусрут: хранилище сертификатов для сторонних центров сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="5d885-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="5d885-123">-Цертификатионаусорити: хранилище сертификатов для промежуточных центров сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="5d885-123">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="5d885-124">— Запрещено: хранилище сертификатов для отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="5d885-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="5d885-125">-My: хранилище сертификатов для личных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="5d885-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="5d885-126">— Root: хранилище сертификатов для доверенных корневых центров сертификации (CAs).</span><span class="sxs-lookup"><span data-stu-id="5d885-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="5d885-127">-TrustedPeople: хранилище сертификатов для напрямую доверенных лиц и ресурсов.</span><span class="sxs-lookup"><span data-stu-id="5d885-127">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="5d885-128">-Трустедпублишер: хранилище сертификатов для напрямую доверенных издателей.</span><span class="sxs-lookup"><span data-stu-id="5d885-128">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="5d885-129">Значение по умолчанию - My.</span><span class="sxs-lookup"><span data-stu-id="5d885-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="5d885-130">Определяет тип поиска сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="5d885-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="5d885-131">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5d885-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d885-132">-(FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="5d885-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="5d885-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="5d885-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="5d885-134">-Финдбисубжектдистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="5d885-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="5d885-135">-Финдбиссуернаме</span><span class="sxs-lookup"><span data-stu-id="5d885-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="5d885-136">-Финдбиссуердистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="5d885-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="5d885-137">-Финдбисериалнумбер</span><span class="sxs-lookup"><span data-stu-id="5d885-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="5d885-138">-Финдбитимевалид</span><span class="sxs-lookup"><span data-stu-id="5d885-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="5d885-139">-Финдбитименотетвалид</span><span class="sxs-lookup"><span data-stu-id="5d885-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="5d885-140">-Финдбитемплатенаме</span><span class="sxs-lookup"><span data-stu-id="5d885-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="5d885-141">-Финдбяппликатионполици</span><span class="sxs-lookup"><span data-stu-id="5d885-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="5d885-142">-Финдбицертификатеполици</span><span class="sxs-lookup"><span data-stu-id="5d885-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="5d885-143">-Финдбекстенсион</span><span class="sxs-lookup"><span data-stu-id="5d885-143">-   FindByExtension</span></span><br /><span data-ttu-id="5d885-144">-Финдбикэйусаже</span><span class="sxs-lookup"><span data-stu-id="5d885-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="5d885-145">-Финдбисубжекткэйидентифиер</span><span class="sxs-lookup"><span data-stu-id="5d885-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="5d885-146">Тип, указанный в атрибуте `findValue`, должен отвечать требованиям заданного значения X509FindType.</span><span class="sxs-lookup"><span data-stu-id="5d885-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="5d885-147">Значение по умолчанию - FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="5d885-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d885-148">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5d885-148">Child Elements</span></span>  

 <span data-ttu-id="5d885-149">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5d885-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d885-150">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5d885-150">Parent Elements</span></span>  
  
|<span data-ttu-id="5d885-151">Элемент</span><span class="sxs-lookup"><span data-stu-id="5d885-151">Element</span></span>|<span data-ttu-id="5d885-152">Описание</span><span class="sxs-lookup"><span data-stu-id="5d885-152">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="5d885-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d885-153">Remarks</span></span>  

 <span data-ttu-id="5d885-154">Элемент `<certificate>` используется в случаях, когда служба должна заранее получить клиентский сертификат для безопасного обмена данными с клиентом.</span><span class="sxs-lookup"><span data-stu-id="5d885-154">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="5d885-155">Это характерно для дуплексного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="5d885-155">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="5d885-156">В более распространенном варианте «запрос/отклик» клиент включает сертификат в запрос, который используется службой для шифрования и подписания отклика.</span><span class="sxs-lookup"><span data-stu-id="5d885-156">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="5d885-157">Тем не менее при дуплексном обмене данными служба не получает запроса от клиента, и ей, таким образом, необходим сертификат клиента заранее, чтобы обеспечить защиту сообщения, отправляемого клиенту.</span><span class="sxs-lookup"><span data-stu-id="5d885-157">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="5d885-158">Следовательно, необходимо получить сертификат клиента при согласовании вне диапазона и указать сертификат с помощью этого элемента.</span><span class="sxs-lookup"><span data-stu-id="5d885-158">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="5d885-159">Дополнительные сведения о дуплексных службах см. [в разделе инструкции. Создание дуплексного контракта](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="5d885-159">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d885-160">Пример</span><span class="sxs-lookup"><span data-stu-id="5d885-160">Example</span></span>  

 <span data-ttu-id="5d885-161">В следующем примере кода демонстрируется поиск соответствующего сертификата X.509 и пользовательского типа проверки в элементе `<authentication>`.</span><span class="sxs-lookup"><span data-stu-id="5d885-161">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d885-162">См. также</span><span class="sxs-lookup"><span data-stu-id="5d885-162">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="5d885-163">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="5d885-163">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5d885-164">Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов</span><span class="sxs-lookup"><span data-stu-id="5d885-164">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="5d885-165">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="5d885-165">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
