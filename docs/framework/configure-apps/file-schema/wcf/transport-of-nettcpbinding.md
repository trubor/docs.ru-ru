---
description: 'Дополнительные сведения <transport> о: <netTcpBinding>'
title: <transport> из <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 9005de300b41c9f53c62875ee185d0f8a3ee8d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664552"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="04eb6-103">\<transport> из \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="04eb6-103">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="04eb6-104">Определяет тип требований безопасности на уровне сообщений для конечной точки, настроенной с помощью [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="04eb6-104">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="04eb6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04eb6-105">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04eb6-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="04eb6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="04eb6-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="04eb6-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04eb6-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="04eb6-108">Attributes</span></span>  
  
|<span data-ttu-id="04eb6-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="04eb6-109">Attribute</span></span>|<span data-ttu-id="04eb6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="04eb6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04eb6-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="04eb6-111">clientCredentialType</span></span>|<span data-ttu-id="04eb6-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="04eb6-112">Optional.</span></span> <span data-ttu-id="04eb6-113">Задает тип учетных данных, используемых при проверке подлинности клиента с помощью безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="04eb6-113">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="04eb6-114">— Значение по умолчанию — `Windows` .</span><span class="sxs-lookup"><span data-stu-id="04eb6-114">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="04eb6-115">— Этот атрибут имеет тип <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="04eb6-115">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="04eb6-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="04eb6-116">protectionLevel</span></span>|<span data-ttu-id="04eb6-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="04eb6-117">Optional.</span></span> <span data-ttu-id="04eb6-118">Определяет безопасность на уровне транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="04eb6-118">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="04eb6-119">Подпись сообщений уменьшает риск подделки сообщения сторонними лицами при его передаче.</span><span class="sxs-lookup"><span data-stu-id="04eb6-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="04eb6-120">Шифрование обеспечивает конфиденциальность на уровне данных во время транспортировки.</span><span class="sxs-lookup"><span data-stu-id="04eb6-120">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="04eb6-121">Значение по умолчанию — `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="04eb6-121">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="04eb6-122">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="04eb6-122">sslProtocols</span></span>|<span data-ttu-id="04eb6-123">Значение флага перечисления SslProtocols, указывающее, какие протоколы SslProtocols поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="04eb6-123">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="04eb6-124">Значение по умолчанию — TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="04eb6-124">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="04eb6-125">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="04eb6-125">policyEnforcement</span></span>|<span data-ttu-id="04eb6-126">Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="04eb6-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="04eb6-127">1. Never — политика никогда не применяется (Расширенная защита отключена).</span><span class="sxs-lookup"><span data-stu-id="04eb6-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="04eb6-128">2. WhenSupported — политика применяется, только если клиент поддерживает расширенную защиту.</span><span class="sxs-lookup"><span data-stu-id="04eb6-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="04eb6-129">3. всегда — политика всегда применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="04eb6-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="04eb6-130">Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="04eb6-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="04eb6-131">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="04eb6-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="04eb6-132">Значение</span><span class="sxs-lookup"><span data-stu-id="04eb6-132">Value</span></span>|<span data-ttu-id="04eb6-133">Описание</span><span class="sxs-lookup"><span data-stu-id="04eb6-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04eb6-134">None</span><span class="sxs-lookup"><span data-stu-id="04eb6-134">None</span></span>|<span data-ttu-id="04eb6-135">Анонимный клиент.</span><span class="sxs-lookup"><span data-stu-id="04eb6-135">The client is anonymous.</span></span> <span data-ttu-id="04eb6-136">Это требует сертификата для службы.</span><span class="sxs-lookup"><span data-stu-id="04eb6-136">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="04eb6-137">Windows</span><span class="sxs-lookup"><span data-stu-id="04eb6-137">Windows</span></span>|<span data-ttu-id="04eb6-138">Задает проверку подлинности Windows для клиента с использованием согласования SP (согласование Kerberos).</span><span class="sxs-lookup"><span data-stu-id="04eb6-138">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="04eb6-139">Certificate</span><span class="sxs-lookup"><span data-stu-id="04eb6-139">Certificate</span></span>|<span data-ttu-id="04eb6-140">Проверка подлинности клиента выполняется с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="04eb6-140">The client is authenticated using a certificate.</span></span> <span data-ttu-id="04eb6-141">Это требует согласования SSL и сертификата для службы.</span><span class="sxs-lookup"><span data-stu-id="04eb6-141">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="04eb6-142">Атрибут protectionLevel</span><span class="sxs-lookup"><span data-stu-id="04eb6-142">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="04eb6-143">Значение</span><span class="sxs-lookup"><span data-stu-id="04eb6-143">Value</span></span>|<span data-ttu-id="04eb6-144">Описание</span><span class="sxs-lookup"><span data-stu-id="04eb6-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04eb6-145">None</span><span class="sxs-lookup"><span data-stu-id="04eb6-145">None</span></span>|<span data-ttu-id="04eb6-146">Нет защиты.</span><span class="sxs-lookup"><span data-stu-id="04eb6-146">No protection.</span></span>|  
|<span data-ttu-id="04eb6-147">Sign</span><span class="sxs-lookup"><span data-stu-id="04eb6-147">Sign</span></span>|<span data-ttu-id="04eb6-148">Сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="04eb6-148">Messages are signed.</span></span>|  
|<span data-ttu-id="04eb6-149">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="04eb6-149">EncryptAndSign</span></span>|<span data-ttu-id="04eb6-150">— Сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="04eb6-150">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04eb6-151">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="04eb6-151">Child Elements</span></span>  

 <span data-ttu-id="04eb6-152">None</span><span class="sxs-lookup"><span data-stu-id="04eb6-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04eb6-153">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="04eb6-153">Parent Elements</span></span>  
  
|<span data-ttu-id="04eb6-154">Элемент</span><span class="sxs-lookup"><span data-stu-id="04eb6-154">Element</span></span>|<span data-ttu-id="04eb6-155">Описание</span><span class="sxs-lookup"><span data-stu-id="04eb6-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="04eb6-156">Указывает возможности безопасности для [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="04eb6-156">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04eb6-157">Remarks</span><span class="sxs-lookup"><span data-stu-id="04eb6-157">Remarks</span></span>  

 <span data-ttu-id="04eb6-158">Безопасность транспорта используется для обеспечения целостности и конфиденциальности сообщений SOAP и для взаимной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="04eb6-158">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="04eb6-159">Если этот режим безопасности выбран для какой-либо привязки, стек каналов настраивается с использованием безопасного транспорта, а сообщения SOAP защищаются с использованием безопасности транспорта, например Windows (Negotiate) или SSL по TCP.</span><span class="sxs-lookup"><span data-stu-id="04eb6-159">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04eb6-160">См. также</span><span class="sxs-lookup"><span data-stu-id="04eb6-160">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="04eb6-161">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="04eb6-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="04eb6-162">Привязки</span><span class="sxs-lookup"><span data-stu-id="04eb6-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="04eb6-163">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="04eb6-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="04eb6-164">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="04eb6-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
