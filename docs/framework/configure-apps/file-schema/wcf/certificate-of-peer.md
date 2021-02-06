---
description: 'Дополнительные сведения <certificate> о: <peer>'
title: <certificate> из <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: e48a96a3f1fa486b19289584ae0c059eb5b7048d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639059"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="457e3-103">\<certificate> из \<peer></span><span class="sxs-lookup"><span data-stu-id="457e3-103">\<certificate> of \<peer></span></span>

<span data-ttu-id="457e3-104">Задает сертификат, используемый одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="457e3-104">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="457e3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="457e3-105">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="457e3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="457e3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="457e3-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="457e3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="457e3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="457e3-108">Attributes</span></span>  
  
|<span data-ttu-id="457e3-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="457e3-109">Attribute</span></span>|<span data-ttu-id="457e3-110">Описание</span><span class="sxs-lookup"><span data-stu-id="457e3-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="457e3-111">Строка, содержащая значение для поиска в хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="457e3-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="457e3-112">Тип, указанный в этом атрибуте, должен отвечать требованиям заданного значения `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="457e3-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="457e3-113">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="457e3-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="457e3-114">Задает расположение хранилища сертификатов Х.509, которое клиент может использовать для проверки сертификата однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="457e3-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="457e3-115">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="457e3-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="457e3-116">-LocalMachine — хранилище сертификатов, назначенное локальному компьютеру.</span><span class="sxs-lookup"><span data-stu-id="457e3-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="457e3-117">-CurrentUser: хранилище сертификатов, назначенное текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="457e3-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="457e3-118">По умолчанию используется значение LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="457e3-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="457e3-119">Задает имя открываемого хранилища сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="457e3-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="457e3-120">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="457e3-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="457e3-121">-AddressBook: хранилище сертификатов для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="457e3-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="457e3-122">-Аусрут: хранилище сертификатов для сторонних центров сертификации (CAs).</span><span class="sxs-lookup"><span data-stu-id="457e3-122">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="457e3-123">-CertificateAuthority: хранилище сертификатов для промежуточных центров сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="457e3-123">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="457e3-124">— Запрещено: хранилище сертификатов для отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="457e3-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="457e3-125">-My: хранилище сертификатов для личных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="457e3-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="457e3-126">— Root: хранилище сертификатов для доверенных корневых центров сертификации (CAs).</span><span class="sxs-lookup"><span data-stu-id="457e3-126">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="457e3-127">-TrustedPeople: хранилище сертификатов для непосредственно доверенных лиц и ресурсов.</span><span class="sxs-lookup"><span data-stu-id="457e3-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="457e3-128">-Трустедпублишер: хранилище сертификатов для непосредственно доверенных издателей.</span><span class="sxs-lookup"><span data-stu-id="457e3-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="457e3-129">Значение по умолчанию - My.</span><span class="sxs-lookup"><span data-stu-id="457e3-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="457e3-130">Определяет тип поиска сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="457e3-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="457e3-131">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="457e3-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="457e3-132">-(FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="457e3-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="457e3-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="457e3-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="457e3-134">-Финдбисубжектдистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="457e3-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="457e3-135">-Финдбиссуернаме</span><span class="sxs-lookup"><span data-stu-id="457e3-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="457e3-136">-Финдбиссуердистингуишеднаме</span><span class="sxs-lookup"><span data-stu-id="457e3-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="457e3-137">-Финдбисериалнумбер</span><span class="sxs-lookup"><span data-stu-id="457e3-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="457e3-138">-Финдбитимевалид</span><span class="sxs-lookup"><span data-stu-id="457e3-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="457e3-139">-Финдбитименотетвалид</span><span class="sxs-lookup"><span data-stu-id="457e3-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="457e3-140">-Финдбитемплатенаме</span><span class="sxs-lookup"><span data-stu-id="457e3-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="457e3-141">-Финдбяппликатионполици</span><span class="sxs-lookup"><span data-stu-id="457e3-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="457e3-142">-Финдбицертификатеполици</span><span class="sxs-lookup"><span data-stu-id="457e3-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="457e3-143">-Финдбекстенсион</span><span class="sxs-lookup"><span data-stu-id="457e3-143">-   FindByExtension</span></span><br /><span data-ttu-id="457e3-144">-Финдбикэйусаже</span><span class="sxs-lookup"><span data-stu-id="457e3-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="457e3-145">-Финдбисубжекткэйидентифиер</span><span class="sxs-lookup"><span data-stu-id="457e3-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="457e3-146">Тип, указанный в атрибуте `findValue`, должен отвечать требованиям заданного значения `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="457e3-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="457e3-147">Значение по умолчанию - FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="457e3-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="457e3-148">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="457e3-148">Child Elements</span></span>  

 <span data-ttu-id="457e3-149">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="457e3-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="457e3-150">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="457e3-150">Parent Elements</span></span>  
  
|<span data-ttu-id="457e3-151">Элемент</span><span class="sxs-lookup"><span data-stu-id="457e3-151">Element</span></span>|<span data-ttu-id="457e3-152">Описание</span><span class="sxs-lookup"><span data-stu-id="457e3-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="457e3-153">Задает текущие учетные данные для однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="457e3-153">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="457e3-154">Remarks</span><span class="sxs-lookup"><span data-stu-id="457e3-154">Remarks</span></span>  

 <span data-ttu-id="457e3-155">Этот элемент конфигурации содержит экземпляр `X509Certificate2`, используемый при проверке подлинности соседей в сетке узлов.</span><span class="sxs-lookup"><span data-stu-id="457e3-155">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="457e3-156">Дополнительные сведения о одноранговых программах см. в разделе одноранговая [сеть](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="457e3-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457e3-157">См. также</span><span class="sxs-lookup"><span data-stu-id="457e3-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="457e3-158">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="457e3-158">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="457e3-159">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="457e3-159">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="457e3-160">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="457e3-160">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="457e3-161">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="457e3-161">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="457e3-162">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="457e3-162">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="457e3-163">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="457e3-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
