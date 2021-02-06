---
description: 'Дополнительные сведения о: <certificate> element'
title: Элемент <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 3f67435d86f19f81c1f6fe1fe2a9a8afbef69e53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639137"
---
# <a name="certificate-element"></a><span data-ttu-id="5c651-103">Элемент \<certificate></span><span class="sxs-lookup"><span data-stu-id="5c651-103">\<certificate> Element</span></span>

<span data-ttu-id="5c651-104">Задает сертификат X.509, используемый для подписи и шифрования сообщений для клиентов одноранговых сетей.</span><span class="sxs-lookup"><span data-stu-id="5c651-104">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5c651-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c651-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c651-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5c651-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5c651-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5c651-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c651-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5c651-108">Attributes</span></span>  
  
|<span data-ttu-id="5c651-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5c651-109">Attribute</span></span>|<span data-ttu-id="5c651-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5c651-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="5c651-111">Строка, содержащая значение для поиска в хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="5c651-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="5c651-112">Тип, указанный в этом атрибуте, должен отвечать требованиям заданного значения `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="5c651-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="5c651-113">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="5c651-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="5c651-114">Задает расположение хранилища сертификатов Х.509, которое клиент может использовать для проверки сертификата однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="5c651-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="5c651-115">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5c651-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5c651-116">-LocalMachine — хранилище сертификатов, назначенное локальному компьютеру.</span><span class="sxs-lookup"><span data-stu-id="5c651-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="5c651-117">-CurrentUser: хранилище сертификатов, назначенное текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="5c651-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="5c651-118">По умолчанию используется значение LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5c651-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="5c651-119">Задает имя открываемого хранилища сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="5c651-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="5c651-120">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5c651-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5c651-121">-AddressBook: хранилище сертификатов для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="5c651-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="5c651-122">-Аусрут: хранилище сертификатов для сторонних центров сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="5c651-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="5c651-123">-CertificateAuthority: хранилище сертификатов для промежуточных центров сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="5c651-123">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="5c651-124">— Запрещено: хранилище сертификатов для отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="5c651-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="5c651-125">-My: хранилище сертификатов для личных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="5c651-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="5c651-126">— Root: хранилище сертификатов для доверенных корневых центров сертификации (CAs).</span><span class="sxs-lookup"><span data-stu-id="5c651-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="5c651-127">-TrustedPeople: хранилище сертификатов для непосредственно доверенных лиц и ресурсов.</span><span class="sxs-lookup"><span data-stu-id="5c651-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="5c651-128">-Трустедпублишер: хранилище сертификатов для непосредственно доверенных издателей.</span><span class="sxs-lookup"><span data-stu-id="5c651-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="5c651-129">Значение по умолчанию - My.</span><span class="sxs-lookup"><span data-stu-id="5c651-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="5c651-130">Определяет тип поиска сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="5c651-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="5c651-131">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="5c651-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5c651-132">-(FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="5c651-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="5c651-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="5c651-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="5c651-134">-Финдбисубжектдистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="5c651-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="5c651-135">-Финдбиссуернаме</span><span class="sxs-lookup"><span data-stu-id="5c651-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="5c651-136">-Финдбиссуердистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="5c651-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="5c651-137">-Финдбисериалнумбер</span><span class="sxs-lookup"><span data-stu-id="5c651-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="5c651-138">-Финдбитимевалид</span><span class="sxs-lookup"><span data-stu-id="5c651-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="5c651-139">-Финдбитименотетвалид</span><span class="sxs-lookup"><span data-stu-id="5c651-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="5c651-140">-Финдбитемплатенаме</span><span class="sxs-lookup"><span data-stu-id="5c651-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="5c651-141">-Финдбяппликатионполици</span><span class="sxs-lookup"><span data-stu-id="5c651-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="5c651-142">-Финдбицертификатеполици</span><span class="sxs-lookup"><span data-stu-id="5c651-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="5c651-143">-Финдбекстенсион</span><span class="sxs-lookup"><span data-stu-id="5c651-143">-   FindByExtension</span></span><br /><span data-ttu-id="5c651-144">-Финдбикэйусаже</span><span class="sxs-lookup"><span data-stu-id="5c651-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="5c651-145">-Финдбисубжекткэйидентифиер</span><span class="sxs-lookup"><span data-stu-id="5c651-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="5c651-146">Тип, указанный в атрибуте `findValue`, должен отвечать требованиям заданного значения `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="5c651-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="5c651-147">Значение по умолчанию - FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="5c651-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c651-148">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5c651-148">Child Elements</span></span>  

 <span data-ttu-id="5c651-149">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5c651-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c651-150">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5c651-150">Parent Elements</span></span>  
  
|<span data-ttu-id="5c651-151">Элемент</span><span class="sxs-lookup"><span data-stu-id="5c651-151">Element</span></span>|<span data-ttu-id="5c651-152">Описание</span><span class="sxs-lookup"><span data-stu-id="5c651-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="5c651-153">Задает учетные данные, используемые при проверке подлинности одноранговых клиентов.</span><span class="sxs-lookup"><span data-stu-id="5c651-153">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c651-154">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c651-154">Remarks</span></span>  

 <span data-ttu-id="5c651-155">Этот элемент конфигурации содержит экземпляр X509Certificate2, используемый при проверке подлинности соседей в сетке узлов.</span><span class="sxs-lookup"><span data-stu-id="5c651-155">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="5c651-156">Дополнительные сведения о одноранговых программах см. в разделе одноранговая [сеть](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5c651-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c651-157">Пример</span><span class="sxs-lookup"><span data-stu-id="5c651-157">Example</span></span>  

 <span data-ttu-id="5c651-158">В следующем примере кода показывается, как найти сертификат, используемый в сценарии с одноранговой сетью.</span><span class="sxs-lookup"><span data-stu-id="5c651-158">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="5c651-159">См. также</span><span class="sxs-lookup"><span data-stu-id="5c651-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="5c651-160">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="5c651-160">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5c651-161">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="5c651-161">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="5c651-162">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5c651-162">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="5c651-163">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5c651-163">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="5c651-164">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="5c651-164">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
