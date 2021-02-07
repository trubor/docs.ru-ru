---
description: 'Дополнительные сведения: <msmqTransportSecurity>'
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: d5a681c287749598c8c80470ea6d800f1687a80d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684169"
---
# \<msmqTransportSecurity>

<span data-ttu-id="4c7c8-102">Задает параметры безопасности транспорта MSMQ для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="4c7c8-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c7c8-103">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c7c8-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4c7c8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4c7c8-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c7c8-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4c7c8-106">Attributes</span></span>  
  
|<span data-ttu-id="4c7c8-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4c7c8-107">Attribute</span></span>|<span data-ttu-id="4c7c8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4c7c8-108">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="4c7c8-109">Задает способ проверки подлинности сообщения транспортом MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-109">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="4c7c8-110">Если задано значение `None`, атрибуту `msmqProtectionLevel` также должно быть присвоено значение `None`.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-110">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="4c7c8-111">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c7c8-112">-None — без проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-112">-   None: No authentication.</span></span><br /><span data-ttu-id="4c7c8-113">— Windows: механизм проверки подлинности использует Active Directory, чтобы получить сертификат X. 509 для идентификатора безопасности, связанного с сообщением.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-113">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="4c7c8-114">Затем это используется для проверки ACL очереди, чтобы убедиться в наличии у пользователя разрешений для записи в очередь.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-114">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="4c7c8-115">-Certificate: канал получает сертификат из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-115">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="4c7c8-116">Значение по умолчанию - Windows.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-116">The default value is Windows.</span></span> <span data-ttu-id="4c7c8-117">Это атрибут типа <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-117">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="4c7c8-118">Задает алгоритм, который будет использоваться для шифрования сообщений при их передаче между диспетчерами очередей сообщений.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-118">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="4c7c8-119">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c7c8-120">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="4c7c8-120">-   RC4Stream</span></span><br /><span data-ttu-id="4c7c8-121">— AES</span><span class="sxs-lookup"><span data-stu-id="4c7c8-121">-   AES</span></span><br /><br /> <span data-ttu-id="4c7c8-122">Значение по умолчанию - RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-122">The default value is RC4Stream.</span></span> <span data-ttu-id="4c7c8-123">Это атрибут типа <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-123">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="4c7c8-124">Задает способ обеспечения безопасности сообщения на уровне транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-124">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="4c7c8-125">Шифрование гарантирует целостность сообщений, а EncryptAndSign обеспечивает как целостность сообщений, так и неподдельность. то есть сообщение действительно поступает от отправителя, а отправитель — от того, кто говорят.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-125">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="4c7c8-126">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c7c8-127">-None: защита отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-127">-   None: No protection.</span></span><br /><span data-ttu-id="4c7c8-128">-Sign: сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-128">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="4c7c8-129">-EncryptAndSign: сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-129">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="4c7c8-130">Значение по умолчанию - Sign.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-130">The default value is Sign.</span></span> <span data-ttu-id="4c7c8-131">Это атрибут типа <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-131">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="4c7c8-132">Задает алгоритм, который должен использоваться при вычислении хэш-кода как части сигнатур.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-132">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="4c7c8-133">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c7c8-134">-MD5</span><span class="sxs-lookup"><span data-stu-id="4c7c8-134">-   MD5</span></span><br /><span data-ttu-id="4c7c8-135">-SHA1</span><span class="sxs-lookup"><span data-stu-id="4c7c8-135">-   SHA1</span></span><br /><span data-ttu-id="4c7c8-136">-SHA256</span><span class="sxs-lookup"><span data-stu-id="4c7c8-136">-   SHA256</span></span><br /><span data-ttu-id="4c7c8-137">-SHA512</span><span class="sxs-lookup"><span data-stu-id="4c7c8-137">-   SHA512</span></span><br /><br /> <span data-ttu-id="4c7c8-138">Значение по умолчанию - SHA1.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-138">The default value is SHA1.</span></span> <span data-ttu-id="4c7c8-139">Это атрибут типа <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-139">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="4c7c8-140">Из-за проблем с MD5 и SHA1 Корпорация Майкрософт рекомендует использовать SHA256 или более высокий уровень.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-140">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c7c8-141">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4c7c8-141">Child Elements</span></span>  

 <span data-ttu-id="4c7c8-142">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-142">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c7c8-143">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4c7c8-143">Parent Elements</span></span>  
  
|<span data-ttu-id="4c7c8-144">Элемент</span><span class="sxs-lookup"><span data-stu-id="4c7c8-144">Element</span></span>|<span data-ttu-id="4c7c8-145">Описание</span><span class="sxs-lookup"><span data-stu-id="4c7c8-145">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="4c7c8-146">Задает параметры, необходимые для взаимодействия с отправителем или получателем очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="4c7c8-146">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="4c7c8-147">Задает свойства обмена данными в очереди для службы Windows Communication Foundation (WCF), использующей собственный протокол MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-147">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c7c8-148">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c7c8-148">Remarks</span></span>  

 <span data-ttu-id="4c7c8-149">Дополнительные сведения о безопасности транспорта см. в разделе [Безопасность транспорта](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="4c7c8-149">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7c8-150">См. также</span><span class="sxs-lookup"><span data-stu-id="4c7c8-150">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4c7c8-151">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="4c7c8-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="4c7c8-152">Транспорты</span><span class="sxs-lookup"><span data-stu-id="4c7c8-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4c7c8-153">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="4c7c8-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4c7c8-154">Привязки</span><span class="sxs-lookup"><span data-stu-id="4c7c8-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4c7c8-155">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="4c7c8-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4c7c8-156">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="4c7c8-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="4c7c8-157">Безопасность транспорта</span><span class="sxs-lookup"><span data-stu-id="4c7c8-157">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
