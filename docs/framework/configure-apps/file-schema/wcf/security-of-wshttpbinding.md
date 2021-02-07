---
description: 'Дополнительные сведения <security> о: <wsHttpBinding>'
title: <security> из <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 646d49bd67b2b544ae2616f206bfdeabf7806579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683064"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="fff14-103">\<security> из \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fff14-103">\<security> of \<wsHttpBinding></span></span>

<span data-ttu-id="fff14-104">Представляет возможности безопасности [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="fff14-104">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="fff14-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fff14-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fff14-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fff14-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fff14-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fff14-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fff14-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fff14-108">Attributes</span></span>  
  
|<span data-ttu-id="fff14-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fff14-109">Attribute</span></span>|<span data-ttu-id="fff14-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fff14-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fff14-111">mode</span><span class="sxs-lookup"><span data-stu-id="fff14-111">mode</span></span>|<span data-ttu-id="fff14-112">Используемых.</span><span class="sxs-lookup"><span data-stu-id="fff14-112">-   Optional.</span></span> <span data-ttu-id="fff14-113">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="fff14-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="fff14-114">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="fff14-114">The default is `Message`.</span></span><br /><span data-ttu-id="fff14-115">— Этот атрибут имеет тип <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="fff14-115">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fff14-116">Атрибут Mode</span><span class="sxs-lookup"><span data-stu-id="fff14-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="fff14-117">Значение</span><span class="sxs-lookup"><span data-stu-id="fff14-117">Value</span></span>|<span data-ttu-id="fff14-118">Описание</span><span class="sxs-lookup"><span data-stu-id="fff14-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fff14-119">None</span><span class="sxs-lookup"><span data-stu-id="fff14-119">None</span></span>|<span data-ttu-id="fff14-120">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="fff14-120">Security is disabled.</span></span>|  
|<span data-ttu-id="fff14-121">Транспорт</span><span class="sxs-lookup"><span data-stu-id="fff14-121">Transport</span></span>|<span data-ttu-id="fff14-122">Безопасность обеспечивается с помощью протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fff14-122">Security is provided using HTTPS.</span></span> <span data-ttu-id="fff14-123">Необходимо настроить службу с использованием SSL-сертификата.</span><span class="sxs-lookup"><span data-stu-id="fff14-123">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="fff14-124">Сообщение полностью защищено с помощью HTTPS, а проверка подлинности выполняется клиентом с помощью SSL-сертификата службы.</span><span class="sxs-lookup"><span data-stu-id="fff14-124">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="fff14-125">Проверка подлинности клиента контролируется посредством атрибута `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="fff14-125">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="fff14-126">объекта [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="fff14-126">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="fff14-127">Сообщение</span><span class="sxs-lookup"><span data-stu-id="fff14-127">Message</span></span>|<span data-ttu-id="fff14-128">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="fff14-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="fff14-129">По умолчанию текст сообщений SOAP шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="fff14-129">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="fff14-130">Этот режим предоставляет множество возможностей, например сведения о доступности учетных данных службы для клиентов на внештатных каналах, об используемом наборе алгоритмов и об уровне защиты, применяемом к тексту сообщения через свойство Security.Message.</span><span class="sxs-lookup"><span data-stu-id="fff14-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="fff14-131">Проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="fff14-131">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="fff14-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="fff14-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="fff14-133">В данном режиме HTTPS обеспечивает целостность, конфиденциальность и проверку подлинности сервера, а механизм безопасности сообщений SOAP обеспечивает проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="fff14-133">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="fff14-134">По умолчанию проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="fff14-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fff14-135">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fff14-135">Child Elements</span></span>  
  
|<span data-ttu-id="fff14-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="fff14-136">Element</span></span>|<span data-ttu-id="fff14-137">Описание</span><span class="sxs-lookup"><span data-stu-id="fff14-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="fff14-138">Определяет параметры безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="fff14-138">Defines the transport security settings.</span></span> <span data-ttu-id="fff14-139">Этот элемент соответствует типу <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fff14-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="fff14-140">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="fff14-140">Defines the security settings for the message.</span></span> <span data-ttu-id="fff14-141">Этот элемент соответствует типу <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="fff14-141">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fff14-142">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fff14-142">Parent Elements</span></span>  
  
|<span data-ttu-id="fff14-143">Элемент</span><span class="sxs-lookup"><span data-stu-id="fff14-143">Element</span></span>|<span data-ttu-id="fff14-144">Описание</span><span class="sxs-lookup"><span data-stu-id="fff14-144">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="fff14-145">Привязка безопасности для приложений транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="fff14-145">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fff14-146">Remarks</span><span class="sxs-lookup"><span data-stu-id="fff14-146">Remarks</span></span>  

 <span data-ttu-id="fff14-147">Класс WSHttpBinding предназначен для взаимодействия со службами, реализующими спецификации WS-\*.</span><span class="sxs-lookup"><span data-stu-id="fff14-147">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="fff14-148">Безопасность транспорта для этой привязки обеспечивается посредством протокола SSL по протоколам HTTP или HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fff14-148">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff14-149">См. также</span><span class="sxs-lookup"><span data-stu-id="fff14-149">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="fff14-150">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fff14-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fff14-151">Привязки</span><span class="sxs-lookup"><span data-stu-id="fff14-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fff14-152">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="fff14-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fff14-153">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fff14-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
