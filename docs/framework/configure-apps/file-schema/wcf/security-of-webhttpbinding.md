---
description: 'Дополнительные сведения <security> о: <webHttpBinding>'
title: <security> из <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: a80a919ef877f01503e5ceaeb4fe7432e46f288c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683051"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="2fbff-103">\<security> из \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2fbff-103">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="2fbff-104">Указывает требования к безопасности для конечной точки, настроенной с помощью [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2fbff-104">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="2fbff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2fbff-105">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fbff-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2fbff-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2fbff-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2fbff-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fbff-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2fbff-108">Attributes</span></span>  
  
|<span data-ttu-id="2fbff-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2fbff-109">Attribute</span></span>|<span data-ttu-id="2fbff-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2fbff-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fbff-111">mode</span><span class="sxs-lookup"><span data-stu-id="2fbff-111">mode</span></span>|<span data-ttu-id="2fbff-112">Указывает, использует ли конечная точка безопасность на уровне транспорта, или же режим обеспечения безопасности не используется.</span><span class="sxs-lookup"><span data-stu-id="2fbff-112">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="2fbff-113">Значение по умолчанию — `None`.</span><span class="sxs-lookup"><span data-stu-id="2fbff-113">The default is `None`.</span></span> <span data-ttu-id="2fbff-114">Это атрибут типа <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2fbff-114">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2fbff-115">Атрибут Mode</span><span class="sxs-lookup"><span data-stu-id="2fbff-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="2fbff-116">Значение</span><span class="sxs-lookup"><span data-stu-id="2fbff-116">Value</span></span>|<span data-ttu-id="2fbff-117">Описание</span><span class="sxs-lookup"><span data-stu-id="2fbff-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2fbff-118">None</span><span class="sxs-lookup"><span data-stu-id="2fbff-118">None</span></span>|<span data-ttu-id="2fbff-119">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="2fbff-119">Security is disabled.</span></span>|  
|<span data-ttu-id="2fbff-120">Транспорт</span><span class="sxs-lookup"><span data-stu-id="2fbff-120">Transport</span></span>|<span data-ttu-id="2fbff-121">Безопасность обеспечивается с помощью протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2fbff-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="2fbff-122">Необходимо настроить службу с использованием SSL-сертификата.</span><span class="sxs-lookup"><span data-stu-id="2fbff-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="2fbff-123">Сообщение полностью защищено с помощью HTTPS, а проверка подлинности службы выполняется клиентом с помощью SSL-сертификата службы.</span><span class="sxs-lookup"><span data-stu-id="2fbff-123">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="2fbff-124">Проверка подлинности клиента контролируется с помощью `ClientCredentialType` атрибута [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2fbff-124">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="2fbff-125">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="2fbff-125">TransportCredentialOnly</span></span>|<span data-ttu-id="2fbff-126">Данный режим не обеспечивает целостности и конфиденциальности сообщений.</span><span class="sxs-lookup"><span data-stu-id="2fbff-126">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="2fbff-127">Он обеспечивает проверку подлинности клиента на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="2fbff-127">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="2fbff-128">Этот режим следует использовать с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="2fbff-128">This mode should be used with caution.</span></span> <span data-ttu-id="2fbff-129">Он должен использоваться в средах, где безопасность транспорта предоставляется другими средствами (например, IPSec), а инфраструктура WCF предоставляет только проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="2fbff-129">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fbff-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2fbff-130">Child Elements</span></span>  
  
|<span data-ttu-id="2fbff-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="2fbff-131">Element</span></span>|<span data-ttu-id="2fbff-132">Описание</span><span class="sxs-lookup"><span data-stu-id="2fbff-132">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="2fbff-133">Определяет параметры безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="2fbff-133">Defines the transport security settings.</span></span> <span data-ttu-id="2fbff-134">Этот элемент соответствует типу <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2fbff-134">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fbff-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2fbff-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2fbff-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="2fbff-136">Element</span></span>|<span data-ttu-id="2fbff-137">Описание</span><span class="sxs-lookup"><span data-stu-id="2fbff-137">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="2fbff-138">Элемент Binding, который используется для настройки конечных точек для веб-служб Windows Communication Foundation (WCF), которые реагируют на запросы HTTP, а не сообщения SOAP.</span><span class="sxs-lookup"><span data-stu-id="2fbff-138">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fbff-139">См. также</span><span class="sxs-lookup"><span data-stu-id="2fbff-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="2fbff-140">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2fbff-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2fbff-141">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="2fbff-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2fbff-142">Привязки</span><span class="sxs-lookup"><span data-stu-id="2fbff-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2fbff-143">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="2fbff-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2fbff-144">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2fbff-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="2fbff-145">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="2fbff-145">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
