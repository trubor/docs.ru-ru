---
description: 'Дополнительные сведения <transport> о: <netHttpBinding>'
title: <transport> из <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 1c2029fcbc57632b828fa180ba0ffbbf6b974775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773515"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="b433b-103">\<transport> из \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b433b-103">\<transport> of \<netHttpBinding></span></span>

<span data-ttu-id="b433b-104">Определяет свойства, которые управляют параметрами проверки подлинности для транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="b433b-104">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="b433b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b433b-105">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b433b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b433b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b433b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b433b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b433b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b433b-108">Attributes</span></span>  
  
|<span data-ttu-id="b433b-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b433b-109">Attribute</span></span>|<span data-ttu-id="b433b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b433b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b433b-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b433b-111">clientCredentialType</span></span>|<span data-ttu-id="b433b-112">— Указывает тип учетных данных, используемых при проверке подлинности клиента с помощью проверки подлинности HTTP.</span><span class="sxs-lookup"><span data-stu-id="b433b-112">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="b433b-113">Значение по умолчанию — `None`.</span><span class="sxs-lookup"><span data-stu-id="b433b-113">The default is `None`.</span></span> <span data-ttu-id="b433b-114">Это атрибут типа <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b433b-114">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b433b-115">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="b433b-115">proxyCredentialType</span></span>|<span data-ttu-id="b433b-116">— Указывает тип учетных данных, используемых при выполнении проверки подлинности клиента в домене с использованием прокси-сервера через HTTP.</span><span class="sxs-lookup"><span data-stu-id="b433b-116">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="b433b-117">Этот атрибут применим, только если атрибут `mode` родительского элемента `security` имеет значение `Transport` или `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="b433b-117">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="b433b-118">Это атрибут типа <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b433b-118">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="b433b-119">realm</span><span class="sxs-lookup"><span data-stu-id="b433b-119">realm</span></span>|<span data-ttu-id="b433b-120">Строка, указывающая область, используемую схемой проверки подлинности HTTP для обычной проверки подлинности или дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-120">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="b433b-121">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="b433b-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="b433b-122">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b433b-122">policyEnforcement</span></span>|<span data-ttu-id="b433b-123">Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="b433b-123">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b433b-124">1. Never — политика никогда не применяется (Расширенная защита отключена).</span><span class="sxs-lookup"><span data-stu-id="b433b-124">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b433b-125">2. WhenSupported — политика применяется, только если клиент поддерживает расширенную защиту.</span><span class="sxs-lookup"><span data-stu-id="b433b-125">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b433b-126">3. всегда — политика всегда применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="b433b-126">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b433b-127">Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-127">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="b433b-128">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="b433b-128">protectionScenario</span></span>|<span data-ttu-id="b433b-129">Это перечисление указывает сценарий защиты, регламентированный политикой.</span><span class="sxs-lookup"><span data-stu-id="b433b-129">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b433b-130">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b433b-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b433b-131">Значение</span><span class="sxs-lookup"><span data-stu-id="b433b-131">Value</span></span>|<span data-ttu-id="b433b-132">Описание</span><span class="sxs-lookup"><span data-stu-id="b433b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b433b-133">None</span><span class="sxs-lookup"><span data-stu-id="b433b-133">None</span></span>|<span data-ttu-id="b433b-134">Во время передачи сообщения не защищены.</span><span class="sxs-lookup"><span data-stu-id="b433b-134">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b433b-135">Basic</span><span class="sxs-lookup"><span data-stu-id="b433b-135">Basic</span></span>|<span data-ttu-id="b433b-136">Задает обычную проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-136">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="b433b-137">Digest (дайджест)</span><span class="sxs-lookup"><span data-stu-id="b433b-137">Digest</span></span>|<span data-ttu-id="b433b-138">Задает дайджест-проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-138">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="b433b-139">Ntlm</span><span class="sxs-lookup"><span data-stu-id="b433b-139">Ntlm</span></span>|<span data-ttu-id="b433b-140">Задает проверку подлинности NTLM, если это возможно и если не удается выполнить проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="b433b-140">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="b433b-141">Windows</span><span class="sxs-lookup"><span data-stu-id="b433b-141">Windows</span></span>|<span data-ttu-id="b433b-142">Задает встроенную проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="b433b-142">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b433b-143">Атрибут proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="b433b-143">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b433b-144">Значение</span><span class="sxs-lookup"><span data-stu-id="b433b-144">Value</span></span>|<span data-ttu-id="b433b-145">Описание</span><span class="sxs-lookup"><span data-stu-id="b433b-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b433b-146">None</span><span class="sxs-lookup"><span data-stu-id="b433b-146">None</span></span>|<span data-ttu-id="b433b-147">— Сообщения не защищаются во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="b433b-147">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b433b-148">Basic</span><span class="sxs-lookup"><span data-stu-id="b433b-148">Basic</span></span>|<span data-ttu-id="b433b-149">Задает обычную проверку подлинности, как определено документом RFC 2617, который посвящен проверке подлинности HTTP, обычной проверке и дайджест-проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-149">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="b433b-150">Digest (дайджест)</span><span class="sxs-lookup"><span data-stu-id="b433b-150">Digest</span></span>|<span data-ttu-id="b433b-151">Задает дайджест-проверку подлинности, как определено документом RFC 2617, который посвящен проверке подлинности HTTP, обычной проверке и дайджест-проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="b433b-151">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="b433b-152">Ntlm</span><span class="sxs-lookup"><span data-stu-id="b433b-152">Ntlm</span></span>|<span data-ttu-id="b433b-153">Задает проверку подлинности NTLM, если это возможно и если не удается выполнить проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="b433b-153">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="b433b-154">Windows</span><span class="sxs-lookup"><span data-stu-id="b433b-154">Windows</span></span>|<span data-ttu-id="b433b-155">Задает встроенную проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="b433b-155">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="b433b-156">Certificate</span><span class="sxs-lookup"><span data-stu-id="b433b-156">Certificate</span></span>|<span data-ttu-id="b433b-157">Выполняет проверку подлинности клиента с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="b433b-157">Performs client authentication using a certificate.</span></span> <span data-ttu-id="b433b-158">Такая возможность действует, только если атрибут `Mode` родительского элемента `security` имеет значение Transport, и не действует, если этот атрибут имеет значение TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="b433b-158">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b433b-159">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b433b-159">Child Elements</span></span>  

 <span data-ttu-id="b433b-160">None</span><span class="sxs-lookup"><span data-stu-id="b433b-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b433b-161">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b433b-161">Parent Elements</span></span>  
  
|<span data-ttu-id="b433b-162">Элемент</span><span class="sxs-lookup"><span data-stu-id="b433b-162">Element</span></span>|<span data-ttu-id="b433b-163">Описание</span><span class="sxs-lookup"><span data-stu-id="b433b-163">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="b433b-164">Определяет возможности безопасности для [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b433b-164">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b433b-165">Пример</span><span class="sxs-lookup"><span data-stu-id="b433b-165">Example</span></span>  

 <span data-ttu-id="b433b-166">В следующем примере демонстрируется использование безопасности транспорта SSL с использованием основной привязки.</span><span class="sxs-lookup"><span data-stu-id="b433b-166">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="b433b-167">По умолчанию основная привязка поддерживает взаимодействие по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="b433b-167">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="b433b-168">См. также</span><span class="sxs-lookup"><span data-stu-id="b433b-168">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="b433b-169">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="b433b-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b433b-170">Привязки</span><span class="sxs-lookup"><span data-stu-id="b433b-170">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b433b-171">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="b433b-171">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b433b-172">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="b433b-172">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
