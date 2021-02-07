---
description: 'Дополнительные сведения <security> о: <netHttpBinding>'
title: <security> из <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 70d6363c0ac7fa00d83880ddc8c873548b385a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683129"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="85611-103">\<security> из \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="85611-103">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="85611-104">Определяет возможности безопасности для [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="85611-104">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="85611-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85611-105">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85611-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="85611-106">Attributes and elements</span></span>

<span data-ttu-id="85611-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="85611-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="85611-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="85611-108">Attributes</span></span>

|<span data-ttu-id="85611-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="85611-109">Attribute</span></span>|<span data-ttu-id="85611-110">Описание</span><span class="sxs-lookup"><span data-stu-id="85611-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="85611-111">mode</span><span class="sxs-lookup"><span data-stu-id="85611-111">mode</span></span>|<span data-ttu-id="85611-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="85611-112">Optional.</span></span> <span data-ttu-id="85611-113">Задает тип используемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="85611-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="85611-114">Значение по умолчанию — `None`.</span><span class="sxs-lookup"><span data-stu-id="85611-114">The default is `None`.</span></span> <span data-ttu-id="85611-115">Это атрибут типа <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="85611-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="85611-116">атрибут mode</span><span class="sxs-lookup"><span data-stu-id="85611-116">mode attribute</span></span>

|<span data-ttu-id="85611-117">Значение</span><span class="sxs-lookup"><span data-stu-id="85611-117">Value</span></span>|<span data-ttu-id="85611-118">Описание</span><span class="sxs-lookup"><span data-stu-id="85611-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="85611-119">None</span><span class="sxs-lookup"><span data-stu-id="85611-119">None</span></span>|<span data-ttu-id="85611-120">— Сообщения не защищаются во время перемещения.</span><span class="sxs-lookup"><span data-stu-id="85611-120">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="85611-121">Транспорт</span><span class="sxs-lookup"><span data-stu-id="85611-121">Transport</span></span>|<span data-ttu-id="85611-122">Безопасность обеспечивается с помощью транспорта HTTPS.</span><span class="sxs-lookup"><span data-stu-id="85611-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="85611-123">Сообщения SOAP защищаются при помощи HTTPS.</span><span class="sxs-lookup"><span data-stu-id="85611-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="85611-124">Служба проходит проверку подлинности для клиента с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="85611-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="85611-125">Проверка подлинности клиента осуществляется с помощью предоставленного ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="85611-125">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="85611-126">Сообщение</span><span class="sxs-lookup"><span data-stu-id="85611-126">Message</span></span>|<span data-ttu-id="85611-127">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="85611-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="85611-128">По умолчанию текст сообщений шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="85611-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="85611-129">Для этой привязки система требует, чтобы клиенту был предоставлен сертификат сервера с использованием внештатного канала.</span><span class="sxs-lookup"><span data-stu-id="85611-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="85611-130">Единственным допустимым значением `ClientCredentialType` для данной привязки является `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="85611-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="85611-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="85611-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="85611-132">Целостность, конфиденциальность и проверка подлинности сервера обеспечиваются с помощью средств безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="85611-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="85611-133">Проверка подлинности клиента осуществляется при помощи механизма безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="85611-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="85611-134">Данный режим может использоваться, когда проверка подлинности клиента осуществляется с помощью имени пользователя/пароля и существует развернутый канал HTTP с обеспечением безопасности при передаче сообщений.</span><span class="sxs-lookup"><span data-stu-id="85611-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="85611-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="85611-135">TransportCredentialOnly</span></span>|<span data-ttu-id="85611-136">Данный режим не обеспечивает целостности и конфиденциальности сообщений.</span><span class="sxs-lookup"><span data-stu-id="85611-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="85611-137">Он предоставляет проверку подлинности клиента на основе http.</span><span class="sxs-lookup"><span data-stu-id="85611-137">It provides http-based client authentication.</span></span> <span data-ttu-id="85611-138">Этот режим следует использовать с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="85611-138">This mode should be used with caution.</span></span> <span data-ttu-id="85611-139">Он должен использоваться в средах, где безопасность транспорта предоставляется другими средствами (например, IPSec), а инфраструктура WCF предоставляет только проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="85611-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="85611-140">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="85611-140">Child elements</span></span>

|<span data-ttu-id="85611-141">Элемент</span><span class="sxs-lookup"><span data-stu-id="85611-141">Element</span></span>|<span data-ttu-id="85611-142">Описание</span><span class="sxs-lookup"><span data-stu-id="85611-142">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="85611-143">Определяет параметры безопасности транспорта для базовой службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="85611-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="85611-144">Данный элемент соответствует <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="85611-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="85611-145">Определяет параметры безопасности сообщений для базовой службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="85611-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="85611-146">Данный элемент соответствует <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="85611-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="85611-147">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="85611-147">Parent elements</span></span>

|<span data-ttu-id="85611-148">Элемент</span><span class="sxs-lookup"><span data-stu-id="85611-148">Element</span></span>|<span data-ttu-id="85611-149">Описание</span><span class="sxs-lookup"><span data-stu-id="85611-149">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="85611-150">binding</span><span class="sxs-lookup"><span data-stu-id="85611-150">binding</span></span>|<span data-ttu-id="85611-151">Элемент Binding объекта [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="85611-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="85611-152">Remarks</span><span class="sxs-lookup"><span data-stu-id="85611-152">Remarks</span></span>

 <span data-ttu-id="85611-153">По умолчанию сообщение SOAP не защищено и проверка подлинности клиента не выполняется.</span><span class="sxs-lookup"><span data-stu-id="85611-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="85611-154">Данный элемент позволяет настроить дополнительные параметры безопасности для элемента `netHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="85611-154">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="85611-155">См. также</span><span class="sxs-lookup"><span data-stu-id="85611-155">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="85611-156">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="85611-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="85611-157">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="85611-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="85611-158">Привязки</span><span class="sxs-lookup"><span data-stu-id="85611-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="85611-159">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="85611-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="85611-160">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="85611-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
