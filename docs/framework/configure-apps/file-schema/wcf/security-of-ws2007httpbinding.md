---
description: 'Дополнительные сведения <security> о: <ws2007HttpBinding>'
title: <security> из <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ef8b82d34b318db79db061b9c01b147e619d39c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786815"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="35291-103">\<security> из \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="35291-103">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="35291-104">Представляет параметры безопасности, используемые с [\<ws2007HttpBinding>](ws2007httpbinding.md) элементом.</span><span class="sxs-lookup"><span data-stu-id="35291-104">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="35291-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35291-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35291-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="35291-106">Attributes and Elements</span></span>  

 <span data-ttu-id="35291-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="35291-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35291-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="35291-108">Attributes</span></span>  
  
|<span data-ttu-id="35291-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="35291-109">Attribute</span></span>|<span data-ttu-id="35291-110">Описание</span><span class="sxs-lookup"><span data-stu-id="35291-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="35291-111">Используемых.</span><span class="sxs-lookup"><span data-stu-id="35291-111">-   Optional.</span></span> <span data-ttu-id="35291-112">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="35291-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="35291-113">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="35291-113">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="35291-114">Это атрибут типа <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="35291-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="35291-115">Атрибут Mode</span><span class="sxs-lookup"><span data-stu-id="35291-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="35291-116">Значение</span><span class="sxs-lookup"><span data-stu-id="35291-116">Value</span></span>|<span data-ttu-id="35291-117">Описание</span><span class="sxs-lookup"><span data-stu-id="35291-117">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="35291-118">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="35291-118">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="35291-119">Безопасность обеспечивается с помощью протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35291-119">Security is provided using HTTPS.</span></span> <span data-ttu-id="35291-120">Необходима настройка службы с помощью SSL-сертификатов.</span><span class="sxs-lookup"><span data-stu-id="35291-120">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="35291-121">Сообщение полностью защищено с помощью HTTPS, а проверка подлинности службы выполняется клиентом с помощью SSL-сертификата службы.</span><span class="sxs-lookup"><span data-stu-id="35291-121">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="35291-122">Проверка подлинности клиента контролируется с помощью `ClientCredentials` атрибута [\<transport>](transport-of-ws2007httpbinding.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="35291-122">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="35291-123">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="35291-123">Security is provided using SOAP message security.</span></span> <span data-ttu-id="35291-124">По умолчанию текст сообщений SOAP шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="35291-124">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="35291-125">Этот режим предоставляет множество возможностей, например доступ к учетным данным службы для клиентов за пределами диапазона, выбор используемого набора алгоритмов и уровня защиты, применяемого к тексту сообщения посредством <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="35291-125">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="35291-126">Проверка подлинности клиента выполняется один раз для каждого сеанса, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="35291-126">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="35291-127">В данном режиме HTTPS обеспечивает целостность, конфиденциальность и проверку подлинности сервера, а механизм безопасности сообщений SOAP обеспечивает проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="35291-127">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="35291-128">По умолчанию проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="35291-128">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35291-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="35291-129">Child Elements</span></span>  
  
|<span data-ttu-id="35291-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="35291-130">Element</span></span>|<span data-ttu-id="35291-131">Описание</span><span class="sxs-lookup"><span data-stu-id="35291-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="35291-132">Определяет параметры безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="35291-132">Defines the transport security settings.</span></span> <span data-ttu-id="35291-133">Этот элемент соответствует типу <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="35291-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="35291-134">Эти параметры применяются только в том случае, если режим имеет значение Transport.</span><span class="sxs-lookup"><span data-stu-id="35291-134">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="35291-135">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="35291-135">Defines the security settings for the message.</span></span> <span data-ttu-id="35291-136">Этот элемент соответствует типу <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="35291-136">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="35291-137">Эти параметры неприменимы, если режим имеет значение Transport.</span><span class="sxs-lookup"><span data-stu-id="35291-137">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35291-138">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="35291-138">Parent Elements</span></span>  
  
|<span data-ttu-id="35291-139">Элемент</span><span class="sxs-lookup"><span data-stu-id="35291-139">Element</span></span>|<span data-ttu-id="35291-140">Описание</span><span class="sxs-lookup"><span data-stu-id="35291-140">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="35291-141">Привязка безопасности для приложений транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="35291-141">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35291-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="35291-142">Remarks</span></span>  

 <span data-ttu-id="35291-143">Этот элемент предназначен для взаимодействия со службами, реализующими спецификации WS-\*.</span><span class="sxs-lookup"><span data-stu-id="35291-143">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="35291-144">Безопасность транспорта для этой привязки обеспечивается посредством протокола SSL по протоколам HTTP или HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35291-144">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35291-145">См. также</span><span class="sxs-lookup"><span data-stu-id="35291-145">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="35291-146">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="35291-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="35291-147">Привязки</span><span class="sxs-lookup"><span data-stu-id="35291-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="35291-148">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="35291-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="35291-149">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="35291-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
