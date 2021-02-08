---
description: 'Дополнительные сведения <transport> о: <msmqIntegrationBinding>'
title: <transport> из <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: bcca714320f333a16d518248531efe8039ff566e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773528"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="6f121-103">\<transport> из \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="6f121-103">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="6f121-104">Определяет параметры безопасности для транспорта интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="6f121-104">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="6f121-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6f121-105">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f121-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6f121-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6f121-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6f121-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f121-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6f121-108">Attributes</span></span>  
  
|<span data-ttu-id="6f121-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="6f121-109">Attribute</span></span>|<span data-ttu-id="6f121-110">Описание</span><span class="sxs-lookup"><span data-stu-id="6f121-110">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="6f121-111">Задает способ проверки подлинности сообщения транспортом MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6f121-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="6f121-112">Если задано значение `None`, атрибуту `msmqProtectionLevel` также должно быть присвоено значение `None`.</span><span class="sxs-lookup"><span data-stu-id="6f121-112">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="6f121-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="6f121-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6f121-114">-None — без проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="6f121-114">-   None: No authentication.</span></span><br /><span data-ttu-id="6f121-115">-WindowsDomain. механизм проверки подлинности использует Active Directory для получения сертификата X. 509 для идентификатора безопасности, связанного с сообщением.</span><span class="sxs-lookup"><span data-stu-id="6f121-115">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="6f121-116">Затем это используется для проверки ACL очереди, чтобы убедиться в наличии у пользователя разрешений для записи в очередь.</span><span class="sxs-lookup"><span data-stu-id="6f121-116">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="6f121-117">-Certificate: канал получает сертификат из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="6f121-117">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="6f121-118">Значение по умолчанию - WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="6f121-118">The default value is WindowsDomain.</span></span> <span data-ttu-id="6f121-119">Это атрибут типа <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="6f121-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="6f121-120">Задает алгоритм, который будет использоваться для шифрования сообщений при их передаче между диспетчерами очередей сообщений.</span><span class="sxs-lookup"><span data-stu-id="6f121-120">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="6f121-121">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="6f121-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6f121-122">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="6f121-122">-   RC4Stream</span></span><br /><span data-ttu-id="6f121-123">— AES</span><span class="sxs-lookup"><span data-stu-id="6f121-123">-   AES</span></span><br /><br /> <span data-ttu-id="6f121-124">Значение по умолчанию - RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="6f121-124">The default value is RC4Stream.</span></span> <span data-ttu-id="6f121-125">Это атрибут типа <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="6f121-125">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="6f121-126">Задает способ обеспечения безопасности сообщения на уровне транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6f121-126">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="6f121-127">Шифрование гарантирует целостность сообщений, а EncryptAndSign обеспечивает как целостность сообщений, так и неподдельность. то есть сообщение действительно поступает от отправителя, а отправитель — от того, кто говорят.</span><span class="sxs-lookup"><span data-stu-id="6f121-127">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="6f121-128">Допустимые значения включают следующие:</span><span class="sxs-lookup"><span data-stu-id="6f121-128">-   Valid values include the following:</span></span><br /><span data-ttu-id="6f121-129">-None: защита отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6f121-129">-   None: No protection.</span></span><br /><span data-ttu-id="6f121-130">-Sign: сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="6f121-130">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="6f121-131">-EncryptAndSign: сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="6f121-131">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="6f121-132">Значение по умолчанию - Sign.</span><span class="sxs-lookup"><span data-stu-id="6f121-132">The default value is Sign.</span></span> <span data-ttu-id="6f121-133">Это атрибут типа ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="6f121-133">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="6f121-134">— Указывает алгоритм, используемый при вычислении дайджеста как части сигнатур.</span><span class="sxs-lookup"><span data-stu-id="6f121-134">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="6f121-135">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="6f121-135">Valid values include the following:</span></span><br /><span data-ttu-id="6f121-136">-MD5</span><span class="sxs-lookup"><span data-stu-id="6f121-136">-   MD5</span></span><br /><span data-ttu-id="6f121-137">-SHA1</span><span class="sxs-lookup"><span data-stu-id="6f121-137">-   SHA1</span></span><br /><span data-ttu-id="6f121-138">-SHA256</span><span class="sxs-lookup"><span data-stu-id="6f121-138">-   SHA256</span></span><br /><span data-ttu-id="6f121-139">-SHA512</span><span class="sxs-lookup"><span data-stu-id="6f121-139">-   SHA512</span></span><br /><br /> <span data-ttu-id="6f121-140">Значение по умолчанию - SHA1.</span><span class="sxs-lookup"><span data-stu-id="6f121-140">The default value is SHA1.</span></span> <span data-ttu-id="6f121-141">Это атрибут типа <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="6f121-141">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="6f121-142">Из-за проблем с MD5 и SHA1 Корпорация Майкрософт рекомендует использовать SHA256 или более высокий уровень.</span><span class="sxs-lookup"><span data-stu-id="6f121-142">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f121-143">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6f121-143">Child Elements</span></span>  

 <span data-ttu-id="6f121-144">None</span><span class="sxs-lookup"><span data-stu-id="6f121-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f121-145">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6f121-145">Parent Elements</span></span>  
  
|<span data-ttu-id="6f121-146">Элемент</span><span class="sxs-lookup"><span data-stu-id="6f121-146">Element</span></span>|<span data-ttu-id="6f121-147">Описание</span><span class="sxs-lookup"><span data-stu-id="6f121-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="6f121-148">Определяет параметры безопасности для привязки MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6f121-148">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f121-149">Remarks</span><span class="sxs-lookup"><span data-stu-id="6f121-149">Remarks</span></span>  

 <span data-ttu-id="6f121-150">Данный элемент инкапсулирует параметры безопасности для транспорта интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="6f121-150">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="6f121-151">Данные параметры одинаковы для интеграции очереди сообщений и использующих очереди транспортов.</span><span class="sxs-lookup"><span data-stu-id="6f121-151">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="6f121-152">Это позволяет задать режим проверки подлинности, алгоритм шифрования, алгоритм SHA и уровень защиты.</span><span class="sxs-lookup"><span data-stu-id="6f121-152">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f121-153">См. также</span><span class="sxs-lookup"><span data-stu-id="6f121-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="6f121-154">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="6f121-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6f121-155">Привязки</span><span class="sxs-lookup"><span data-stu-id="6f121-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6f121-156">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="6f121-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6f121-157">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="6f121-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
