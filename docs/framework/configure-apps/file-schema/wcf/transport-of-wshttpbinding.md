---
description: 'Дополнительные сведения <transport> о: <wsHttpBinding>'
title: <transport> из <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 7801148d76aaa9c074eeb7a83c1dd2fa152d871c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749302"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="9862b-103">\<transport> из \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9862b-103">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="9862b-104">Определяет параметры проверки подлинности для HTTP-транспорта.</span><span class="sxs-lookup"><span data-stu-id="9862b-104">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="9862b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9862b-105">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="9862b-106">Тип</span><span class="sxs-lookup"><span data-stu-id="9862b-106">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="9862b-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9862b-107">Attributes and Elements</span></span>

<span data-ttu-id="9862b-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9862b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9862b-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9862b-109">Attributes</span></span>

|<span data-ttu-id="9862b-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9862b-110">Attribute</span></span>|<span data-ttu-id="9862b-111">Описание</span><span class="sxs-lookup"><span data-stu-id="9862b-111">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="9862b-112">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="9862b-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="9862b-113">Это атрибут типа <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9862b-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="9862b-114">Задает учетные данные, используемые для проверки подлинности клиента при подключении к прокси-серверу домена.</span><span class="sxs-lookup"><span data-stu-id="9862b-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="9862b-115">Это атрибут типа <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9862b-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="9862b-116">Строка, указывающая область проверки подлинности для обычной проверки подлинности или дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="9862b-117">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="9862b-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9862b-118">Область проверки подлинности задает по крайней мере имя основного узла, выполняющего проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="9862b-119">Она также может указывать коллекцию пользователей, которым разрешен доступ.</span><span class="sxs-lookup"><span data-stu-id="9862b-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="9862b-120">Пользователь может запросить область проверки подлинности, чтобы выяснить, какое из нескольких возможных сочетаний имен пользователей и паролей можно использовать.</span><span class="sxs-lookup"><span data-stu-id="9862b-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="9862b-121">Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="9862b-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9862b-122">1. Never — политика никогда не применяется (Расширенная защита отключена).</span><span class="sxs-lookup"><span data-stu-id="9862b-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9862b-123">2. WhenSupported — политика применяется, только если клиент поддерживает расширенную защиту.</span><span class="sxs-lookup"><span data-stu-id="9862b-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9862b-124">3. всегда — политика всегда применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="9862b-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9862b-125">Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9862b-126">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="9862b-126">clientCredentialType Attribute</span></span>

|<span data-ttu-id="9862b-127">Значение</span><span class="sxs-lookup"><span data-stu-id="9862b-127">Value</span></span>|<span data-ttu-id="9862b-128">Описание</span><span class="sxs-lookup"><span data-stu-id="9862b-128">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="9862b-129">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="9862b-129">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="9862b-130">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-130">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="9862b-131">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-131">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="9862b-132">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="9862b-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="9862b-133">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="9862b-133">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="9862b-134">Для проверки подлинности клиента используются сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="9862b-134">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9862b-135">Атрибут proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="9862b-135">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="9862b-136">Значение</span><span class="sxs-lookup"><span data-stu-id="9862b-136">Value</span></span>|<span data-ttu-id="9862b-137">Описание</span><span class="sxs-lookup"><span data-stu-id="9862b-137">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="9862b-138">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="9862b-138">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="9862b-139">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-139">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="9862b-140">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="9862b-140">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="9862b-141">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="9862b-141">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="9862b-142">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="9862b-142">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="9862b-143">Для проверки подлинности клиента используются сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="9862b-143">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9862b-144">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9862b-144">Child Elements</span></span>

<span data-ttu-id="9862b-145">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9862b-145">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9862b-146">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9862b-146">Parent Elements</span></span>

|<span data-ttu-id="9862b-147">Элемент</span><span class="sxs-lookup"><span data-stu-id="9862b-147">Element</span></span>|<span data-ttu-id="9862b-148">Описание</span><span class="sxs-lookup"><span data-stu-id="9862b-148">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="9862b-149">Представляет возможности безопасности [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9862b-149">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="9862b-150">См. также</span><span class="sxs-lookup"><span data-stu-id="9862b-150">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="9862b-151">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9862b-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9862b-152">Привязки</span><span class="sxs-lookup"><span data-stu-id="9862b-152">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9862b-153">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="9862b-153">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9862b-154">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9862b-154">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
