---
description: 'Дополнительные сведения <security> о: <basicHttpBinding>'
title: <security> из <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 92d938d062d56cbb066a1170a9d3b8f3f5ba0186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683260"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="f8c34-103">\<security> из \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f8c34-103">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="f8c34-104">Определяет возможности безопасности для [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f8c34-104">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f8c34-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8c34-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8c34-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f8c34-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f8c34-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f8c34-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8c34-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f8c34-108">Attributes</span></span>  
  
|<span data-ttu-id="f8c34-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f8c34-109">Attribute</span></span>|<span data-ttu-id="f8c34-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f8c34-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8c34-111">mode</span><span class="sxs-lookup"><span data-stu-id="f8c34-111">mode</span></span>|<span data-ttu-id="f8c34-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f8c34-112">Optional.</span></span> <span data-ttu-id="f8c34-113">Задает тип используемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="f8c34-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="f8c34-114">Значение по умолчанию — `None`.</span><span class="sxs-lookup"><span data-stu-id="f8c34-114">The default is `None`.</span></span> <span data-ttu-id="f8c34-115">Это атрибут типа <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f8c34-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f8c34-116">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="f8c34-116">mode Attribute</span></span>  
  
|<span data-ttu-id="f8c34-117">Значение</span><span class="sxs-lookup"><span data-stu-id="f8c34-117">Value</span></span>|<span data-ttu-id="f8c34-118">Описание</span><span class="sxs-lookup"><span data-stu-id="f8c34-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8c34-119">None</span><span class="sxs-lookup"><span data-stu-id="f8c34-119">None</span></span>|<span data-ttu-id="f8c34-120">— Сообщения не защищаются во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="f8c34-120">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f8c34-121">Транспорт</span><span class="sxs-lookup"><span data-stu-id="f8c34-121">Transport</span></span>|<span data-ttu-id="f8c34-122">Безопасность обеспечивается с помощью транспорта HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8c34-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="f8c34-123">Сообщения SOAP защищаются при помощи HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8c34-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="f8c34-124">Служба проходит проверку подлинности для клиента с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="f8c34-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="f8c34-125">Проверка подлинности клиента осуществляется с помощью предоставленного ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="f8c34-125">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="f8c34-126">См [\<transport>](transport-of-basichttpbinding.md) . раздел.</span><span class="sxs-lookup"><span data-stu-id="f8c34-126">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="f8c34-127">Сообщение</span><span class="sxs-lookup"><span data-stu-id="f8c34-127">Message</span></span>|<span data-ttu-id="f8c34-128">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="f8c34-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f8c34-129">По умолчанию текст сообщений шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="f8c34-129">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="f8c34-130">Для этой привязки система требует, чтобы клиенту был предоставлен сертификат сервера с использованием внештатного канала.</span><span class="sxs-lookup"><span data-stu-id="f8c34-130">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="f8c34-131">Единственным допустимым значением `ClientCredentialType` для данной привязки является `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="f8c34-131">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="f8c34-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f8c34-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="f8c34-133">Целостность, конфиденциальность и проверка подлинности сервера обеспечиваются с помощью средств безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="f8c34-133">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="f8c34-134">Проверка подлинности клиента осуществляется при помощи механизма безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="f8c34-134">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="f8c34-135">Данный режим может использоваться, когда проверка подлинности клиента осуществляется с помощью имени пользователя/пароля и существует развернутый канал HTTP с обеспечением безопасности при передаче сообщений.</span><span class="sxs-lookup"><span data-stu-id="f8c34-135">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="f8c34-136">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f8c34-136">TransportCredentialOnly</span></span>|<span data-ttu-id="f8c34-137">Данный режим не обеспечивает целостности и конфиденциальности сообщений.</span><span class="sxs-lookup"><span data-stu-id="f8c34-137">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f8c34-138">Он предоставляет проверку подлинности клиента на основе http.</span><span class="sxs-lookup"><span data-stu-id="f8c34-138">It provides http-based client authentication.</span></span> <span data-ttu-id="f8c34-139">Этот режим следует использовать с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="f8c34-139">This mode should be used with caution.</span></span> <span data-ttu-id="f8c34-140">Он должен использоваться в средах, где безопасность транспорта предоставляется другими средствами (например, IPSec), а инфраструктура WCF предоставляет только проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="f8c34-140">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8c34-141">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f8c34-141">Child Elements</span></span>  
  
|<span data-ttu-id="f8c34-142">Элемент</span><span class="sxs-lookup"><span data-stu-id="f8c34-142">Element</span></span>|<span data-ttu-id="f8c34-143">Описание</span><span class="sxs-lookup"><span data-stu-id="f8c34-143">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="f8c34-144">Определяет параметры безопасности транспорта для базовой службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="f8c34-144">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="f8c34-145">Данный элемент соответствует <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="f8c34-145">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="f8c34-146">Определяет параметры безопасности сообщений для базовой службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="f8c34-146">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="f8c34-147">Данный элемент соответствует <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="f8c34-147">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8c34-148">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f8c34-148">Parent Elements</span></span>  
  
|<span data-ttu-id="f8c34-149">Элемент</span><span class="sxs-lookup"><span data-stu-id="f8c34-149">Element</span></span>|<span data-ttu-id="f8c34-150">Описание</span><span class="sxs-lookup"><span data-stu-id="f8c34-150">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8c34-151">binding</span><span class="sxs-lookup"><span data-stu-id="f8c34-151">binding</span></span>|<span data-ttu-id="f8c34-152">Элемент Binding объекта [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f8c34-152">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8c34-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8c34-153">Remarks</span></span>  

 <span data-ttu-id="f8c34-154">По умолчанию сообщение SOAP не защищено и проверка подлинности клиента не выполняется.</span><span class="sxs-lookup"><span data-stu-id="f8c34-154">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="f8c34-155">Данный элемент позволяет настроить дополнительные параметры безопасности для элемента `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f8c34-155">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c34-156">См. также</span><span class="sxs-lookup"><span data-stu-id="f8c34-156">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="f8c34-157">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="f8c34-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f8c34-158">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="f8c34-158">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f8c34-159">Привязки</span><span class="sxs-lookup"><span data-stu-id="f8c34-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f8c34-160">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="f8c34-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f8c34-161">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="f8c34-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
