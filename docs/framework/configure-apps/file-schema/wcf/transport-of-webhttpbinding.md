---
description: 'Дополнительные сведения <transport> о: <webHttpBinding>'
title: <transport> из <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: a845786f4e60a44dcb157201235d28d49ab8d40b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773450"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="2dec7-103">\<transport> из \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2dec7-103">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="2dec7-104">Определяет параметры безопасности уровня транспорта для конечной точки службы, настроенной для получения запросов HTTP.</span><span class="sxs-lookup"><span data-stu-id="2dec7-104">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2dec7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2dec7-105">Syntax</span></span>  
  
```xml  
<webHttpBinding>
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
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="2dec7-106">Тип</span><span class="sxs-lookup"><span data-stu-id="2dec7-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dec7-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2dec7-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2dec7-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2dec7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dec7-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2dec7-109">Attributes</span></span>  
  
|<span data-ttu-id="2dec7-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2dec7-110">Attribute</span></span>|<span data-ttu-id="2dec7-111">Описание</span><span class="sxs-lookup"><span data-stu-id="2dec7-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2dec7-112">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="2dec7-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2dec7-113">Это атрибут типа <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2dec7-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2dec7-114">Задает учетные данные, используемые для проверки подлинности клиента при подключении к прокси-серверу домена.</span><span class="sxs-lookup"><span data-stu-id="2dec7-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2dec7-115">Это атрибут типа <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2dec7-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2dec7-116">Строка, указывающая область проверки подлинности для обычной проверки подлинности или дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2dec7-117">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="2dec7-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2dec7-118">Область проверки подлинности задает по крайней мере имя основного узла, выполняющего проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2dec7-119">Она также может указывать коллекцию пользователей, которым разрешен доступ.</span><span class="sxs-lookup"><span data-stu-id="2dec7-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="2dec7-120">Пользователь может запросить область проверки подлинности, чтобы выяснить, какое из нескольких возможных сочетаний имен пользователей и паролей можно использовать.</span><span class="sxs-lookup"><span data-stu-id="2dec7-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="2dec7-121">Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="2dec7-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2dec7-122">1. Never — политика никогда не применяется (Расширенная защита отключена).</span><span class="sxs-lookup"><span data-stu-id="2dec7-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2dec7-123">2. WhenSupported — политика применяется, только если клиент поддерживает расширенную защиту.</span><span class="sxs-lookup"><span data-stu-id="2dec7-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2dec7-124">3. всегда — политика всегда применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="2dec7-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2dec7-125">Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2dec7-126">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="2dec7-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2dec7-127">Значение</span><span class="sxs-lookup"><span data-stu-id="2dec7-127">Value</span></span>|<span data-ttu-id="2dec7-128">Описание</span><span class="sxs-lookup"><span data-stu-id="2dec7-128">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2dec7-129">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="2dec7-129">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2dec7-130">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-130">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2dec7-131">Для проверки подлинности клиента используются сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="2dec7-131">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="2dec7-132">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-132">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2dec7-133">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="2dec7-133">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2dec7-134">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="2dec7-134">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2dec7-135">Атрибут proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="2dec7-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2dec7-136">Значение</span><span class="sxs-lookup"><span data-stu-id="2dec7-136">Value</span></span>|<span data-ttu-id="2dec7-137">Описание</span><span class="sxs-lookup"><span data-stu-id="2dec7-137">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2dec7-138">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="2dec7-138">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2dec7-139">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-139">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2dec7-140">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="2dec7-140">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2dec7-141">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="2dec7-141">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2dec7-142">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="2dec7-142">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2dec7-143">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2dec7-143">Child Elements</span></span>  

 <span data-ttu-id="2dec7-144">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2dec7-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2dec7-145">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2dec7-145">Parent Elements</span></span>  
  
|<span data-ttu-id="2dec7-146">Элемент</span><span class="sxs-lookup"><span data-stu-id="2dec7-146">Element</span></span>|<span data-ttu-id="2dec7-147">Описание</span><span class="sxs-lookup"><span data-stu-id="2dec7-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="2dec7-148">Представляет возможности безопасности [\<wsHttpBinding>](wshttpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="2dec7-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2dec7-149">См. также</span><span class="sxs-lookup"><span data-stu-id="2dec7-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="2dec7-150">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2dec7-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2dec7-151">Привязки</span><span class="sxs-lookup"><span data-stu-id="2dec7-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2dec7-152">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="2dec7-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2dec7-153">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2dec7-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="2dec7-154">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="2dec7-154">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
