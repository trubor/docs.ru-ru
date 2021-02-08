---
description: 'Дополнительные сведения <transport> о: <ws2007HttpBinding>'
title: <transport> из <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 8c6890bc291458ba0849ab7a206487431b279576
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773437"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="4dcb6-103">\<transport> из \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="4dcb6-103">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="4dcb6-104">Определяет параметры проверки подлинности для HTTP-транспорта.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-104">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="4dcb6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4dcb6-105">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="4dcb6-106">Тип</span><span class="sxs-lookup"><span data-stu-id="4dcb6-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dcb6-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4dcb6-107">Attributes and Elements</span></span>  

 <span data-ttu-id="4dcb6-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dcb6-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4dcb6-109">Attributes</span></span>  
  
|<span data-ttu-id="4dcb6-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4dcb6-110">Attribute</span></span>|<span data-ttu-id="4dcb6-111">Описание</span><span class="sxs-lookup"><span data-stu-id="4dcb6-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="4dcb6-112">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4dcb6-113">Это атрибут типа <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="4dcb6-114">Задает учетные данные, используемые для проверки подлинности клиента при подключении к прокси-серверу домена.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4dcb6-115">Это атрибут типа <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="4dcb6-116">Область проверки подлинности, используемая для дайджест-проверки подлинности или базовой проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-116">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4dcb6-117">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4dcb6-118">Область проверки подлинности задает по крайней мере имя основного узла, выполняющего проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4dcb6-119">Она также может указывать коллекцию пользователей, которым разрешен доступ.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-119">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="4dcb6-120">Пользователь может направить запрос к области проверки подлинности, чтобы определить, какие конкретно имя и пароль из нескольких возможных можно использовать.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-120">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4dcb6-121">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="4dcb6-121">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4dcb6-122">Значение</span><span class="sxs-lookup"><span data-stu-id="4dcb6-122">Value</span></span>|<span data-ttu-id="4dcb6-123">Описание</span><span class="sxs-lookup"><span data-stu-id="4dcb6-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4dcb6-124">None</span><span class="sxs-lookup"><span data-stu-id="4dcb6-124">None</span></span>|<span data-ttu-id="4dcb6-125">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-125">Security is disabled.</span></span>|  
|<span data-ttu-id="4dcb6-126">Basic</span><span class="sxs-lookup"><span data-stu-id="4dcb6-126">Basic</span></span>|<span data-ttu-id="4dcb6-127">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-127">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4dcb6-128">Digest (дайджест)</span><span class="sxs-lookup"><span data-stu-id="4dcb6-128">Digest</span></span>|<span data-ttu-id="4dcb6-129">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-129">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4dcb6-130">Ntlm</span><span class="sxs-lookup"><span data-stu-id="4dcb6-130">Ntlm</span></span>|<span data-ttu-id="4dcb6-131">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4dcb6-132">Windows</span><span class="sxs-lookup"><span data-stu-id="4dcb6-132">Windows</span></span>|<span data-ttu-id="4dcb6-133">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-133">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4dcb6-134">Certificate</span><span class="sxs-lookup"><span data-stu-id="4dcb6-134">Certificate</span></span>|<span data-ttu-id="4dcb6-135">Для проверки подлинности клиента используются сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-135">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4dcb6-136">Атрибут proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="4dcb6-136">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4dcb6-137">Значение</span><span class="sxs-lookup"><span data-stu-id="4dcb6-137">Value</span></span>|<span data-ttu-id="4dcb6-138">Описание</span><span class="sxs-lookup"><span data-stu-id="4dcb6-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4dcb6-139">None</span><span class="sxs-lookup"><span data-stu-id="4dcb6-139">None</span></span>|<span data-ttu-id="4dcb6-140">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-140">Security is disabled.</span></span>|  
|<span data-ttu-id="4dcb6-141">Basic</span><span class="sxs-lookup"><span data-stu-id="4dcb6-141">Basic</span></span>|<span data-ttu-id="4dcb6-142">Используется обычная проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-142">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4dcb6-143">Digest (дайджест)</span><span class="sxs-lookup"><span data-stu-id="4dcb6-143">Digest</span></span>|<span data-ttu-id="4dcb6-144">Используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-144">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4dcb6-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="4dcb6-145">Ntlm</span></span>|<span data-ttu-id="4dcb6-146">Используется проверка подлинности NTLM в качестве резервной в домене Windows.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4dcb6-147">Windows</span><span class="sxs-lookup"><span data-stu-id="4dcb6-147">Windows</span></span>|<span data-ttu-id="4dcb6-148">Используется встроенная проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-148">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4dcb6-149">Certificate</span><span class="sxs-lookup"><span data-stu-id="4dcb6-149">Certificate</span></span>|<span data-ttu-id="4dcb6-150">Для проверки подлинности клиента используются сертификаты X.509.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-150">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dcb6-151">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4dcb6-151">Child Elements</span></span>  

 <span data-ttu-id="4dcb6-152">None</span><span class="sxs-lookup"><span data-stu-id="4dcb6-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dcb6-153">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4dcb6-153">Parent Elements</span></span>  
  
|<span data-ttu-id="4dcb6-154">Элемент</span><span class="sxs-lookup"><span data-stu-id="4dcb6-154">Element</span></span>|<span data-ttu-id="4dcb6-155">Описание</span><span class="sxs-lookup"><span data-stu-id="4dcb6-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="4dcb6-156">Представляет возможности безопасности [\<ws2007HttpBinding>](ws2007httpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="4dcb6-156">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dcb6-157">См. также</span><span class="sxs-lookup"><span data-stu-id="4dcb6-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="4dcb6-158">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="4dcb6-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4dcb6-159">Привязки</span><span class="sxs-lookup"><span data-stu-id="4dcb6-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4dcb6-160">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="4dcb6-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4dcb6-161">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="4dcb6-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
