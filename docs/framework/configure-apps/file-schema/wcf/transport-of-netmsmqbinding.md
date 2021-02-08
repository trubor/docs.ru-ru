---
description: 'Дополнительные сведения <transport> о: <netMsmqBinding>'
title: <transport> из <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 04768f259629277abd758d102f3873bb28f16514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773502"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="fd9e9-103">\<transport> из \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="fd9e9-103">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="fd9e9-104">Определяет параметры безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-104">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="fd9e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fd9e9-105">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd9e9-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fd9e9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fd9e9-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd9e9-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fd9e9-108">Attributes</span></span>  
  
|<span data-ttu-id="fd9e9-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fd9e9-109">Attribute</span></span>|<span data-ttu-id="fd9e9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fd9e9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd9e9-111">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="fd9e9-111">msmqAuthenticationMode</span></span>|<span data-ttu-id="fd9e9-112">Задает способ проверки подлинности сообщения транспортом MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-112">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="fd9e9-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd9e9-114">-None — без проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-114">-   None: No authentication.</span></span><br /><span data-ttu-id="fd9e9-115">-WindowsDomain. механизм проверки подлинности использует Active Directory для получения сертификата X. 509 для идентификатора безопасности, связанного с сообщением.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-115">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="fd9e9-116">Затем он используется для проверки списка управления доступом для очереди с целью удостовериться, что пользователь имеет разрешение на запись в очередь.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-116">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="fd9e9-117">-Certificate: канал получает сертификат из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-117">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="fd9e9-118">Значение по умолчанию — `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-118">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="fd9e9-119">Если данный атрибут имеет значение `None`, то атрибут `msmqProtectionLevel` также должен иметь значение `None`.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-119">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="fd9e9-120">Это атрибут типа <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-120">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="fd9e9-121">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd9e9-121">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="fd9e9-122">Задает алгоритм, который будет использоваться для шифрования сообщений при их передаче между диспетчерами очередей сообщений.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-122">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="fd9e9-123">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd9e9-124">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="fd9e9-124">-   RC4Stream</span></span><br /><span data-ttu-id="fd9e9-125">— AES</span><span class="sxs-lookup"><span data-stu-id="fd9e9-125">-   AES</span></span><br /><span data-ttu-id="fd9e9-126">— Значение по умолчанию — `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="fd9e9-126">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="fd9e9-127">Это атрибут типа <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-127">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="fd9e9-128">msmqprotectionLevel</span><span class="sxs-lookup"><span data-stu-id="fd9e9-128">msmqProtectionLevel</span></span>|<span data-ttu-id="fd9e9-129">Задает способ обеспечения безопасности сообщений на уровне транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-129">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="fd9e9-130">Шифрование обеспечивает целостность сообщения, тогда как подпись и шифрование обеспечивают как целостность сообщения, так и неподдельность.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-130">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="fd9e9-131">То есть сообщение действительно поступило от отправителя, а отправитель — от того, кто говорят.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-131">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="fd9e9-132">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd9e9-133">-None: защита отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-133">-   None: No protection.</span></span><br /><span data-ttu-id="fd9e9-134">-Sign: сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-134">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fd9e9-135">-EncryptAndSign: сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-135">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="fd9e9-136">— Значение по умолчанию — `Sign` .</span><span class="sxs-lookup"><span data-stu-id="fd9e9-136">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="fd9e9-137">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd9e9-137">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="fd9e9-138">Указывает алгоритм хэширования, который будет использоваться при вычислении хэш-кода сообщения.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-138">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="fd9e9-139">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd9e9-140">-MD5</span><span class="sxs-lookup"><span data-stu-id="fd9e9-140">-   MD5</span></span><br /><span data-ttu-id="fd9e9-141">-SHA1</span><span class="sxs-lookup"><span data-stu-id="fd9e9-141">-   SHA1</span></span><br /><span data-ttu-id="fd9e9-142">-SHA256</span><span class="sxs-lookup"><span data-stu-id="fd9e9-142">-   SHA256</span></span><br /><span data-ttu-id="fd9e9-143">-SHA512</span><span class="sxs-lookup"><span data-stu-id="fd9e9-143">-   SHA512</span></span><br /><br /> <span data-ttu-id="fd9e9-144">Значение по умолчанию — `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-144">The default is `SHA1`.</span></span> <span data-ttu-id="fd9e9-145">Это атрибут типа <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-145">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="fd9e9-146">Из-за проблем с MD5 и SHA1 Корпорация Майкрософт рекомендует использовать SHA256 или более высокий уровень.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-146">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd9e9-147">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fd9e9-147">Child Elements</span></span>  

 <span data-ttu-id="fd9e9-148">None</span><span class="sxs-lookup"><span data-stu-id="fd9e9-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd9e9-149">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fd9e9-149">Parent Elements</span></span>  
  
|<span data-ttu-id="fd9e9-150">Элемент</span><span class="sxs-lookup"><span data-stu-id="fd9e9-150">Element</span></span>|<span data-ttu-id="fd9e9-151">Описание</span><span class="sxs-lookup"><span data-stu-id="fd9e9-151">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="fd9e9-152">Определяет параметры безопасности для поставленного в очередь транспорта.</span><span class="sxs-lookup"><span data-stu-id="fd9e9-152">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd9e9-153">См. также</span><span class="sxs-lookup"><span data-stu-id="fd9e9-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="fd9e9-154">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="fd9e9-154">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fd9e9-155">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fd9e9-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fd9e9-156">Привязки</span><span class="sxs-lookup"><span data-stu-id="fd9e9-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fd9e9-157">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="fd9e9-157">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fd9e9-158">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fd9e9-158">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
