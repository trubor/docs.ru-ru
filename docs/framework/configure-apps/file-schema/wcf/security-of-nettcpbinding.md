---
description: 'Дополнительные сведения <security> о: <netTcpBinding>'
title: <security> из <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: ad924f5a6ea9e003f6427ee76d3aef3afde9d083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683077"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="acf76-103">\<security> из \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="acf76-103">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="acf76-104">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="acf76-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="acf76-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="acf76-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acf76-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="acf76-106">Attributes and Elements</span></span>  

 <span data-ttu-id="acf76-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="acf76-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acf76-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="acf76-108">Attributes</span></span>  
  
|<span data-ttu-id="acf76-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="acf76-109">Attribute</span></span>|<span data-ttu-id="acf76-110">Описание</span><span class="sxs-lookup"><span data-stu-id="acf76-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acf76-111">mode</span><span class="sxs-lookup"><span data-stu-id="acf76-111">mode</span></span>|<span data-ttu-id="acf76-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="acf76-112">Optional.</span></span> <span data-ttu-id="acf76-113">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="acf76-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="acf76-114">Ниже приведены допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="acf76-114">Valid values are shown below.</span></span> <span data-ttu-id="acf76-115">Значение по умолчанию — `Transport`.</span><span class="sxs-lookup"><span data-stu-id="acf76-115">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="acf76-116">Это атрибут типа <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="acf76-116">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="acf76-117">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="acf76-117">mode Attribute</span></span>  
  
|<span data-ttu-id="acf76-118">Значение</span><span class="sxs-lookup"><span data-stu-id="acf76-118">Value</span></span>|<span data-ttu-id="acf76-119">Описание</span><span class="sxs-lookup"><span data-stu-id="acf76-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="acf76-120">None</span><span class="sxs-lookup"><span data-stu-id="acf76-120">None</span></span>|<span data-ttu-id="acf76-121">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="acf76-121">Security is disabled.</span></span>|  
|<span data-ttu-id="acf76-122">Транспорт</span><span class="sxs-lookup"><span data-stu-id="acf76-122">Transport</span></span>|<span data-ttu-id="acf76-123">Безопасность транспорта обеспечивается с помощью TLS через TCP или SPNego.</span><span class="sxs-lookup"><span data-stu-id="acf76-123">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="acf76-124">Может потребоваться настроить службу с использованием SSL-сертификатов.</span><span class="sxs-lookup"><span data-stu-id="acf76-124">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="acf76-125">Этот режим позволяет контролировать уровень защиты.</span><span class="sxs-lookup"><span data-stu-id="acf76-125">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="acf76-126">Сообщение</span><span class="sxs-lookup"><span data-stu-id="acf76-126">Message</span></span>|<span data-ttu-id="acf76-127">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="acf76-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="acf76-128">По умолчанию текст сообщений SOAP шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="acf76-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="acf76-129">Этот режим предоставляет множество функций, таких как сведения о доступности учетных данных службы для клиентов за пределами диапазона, об используемом наборе алгоритмов и об уровне защиты, применяемом к тексту сообщения.</span><span class="sxs-lookup"><span data-stu-id="acf76-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="acf76-130">Проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="acf76-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="acf76-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="acf76-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="acf76-132">Безопасность транспорта связана с безопасностью сообщения.</span><span class="sxs-lookup"><span data-stu-id="acf76-132">Transport security is coupled with message security.</span></span> <span data-ttu-id="acf76-133">Безопасность транспорта обеспечивается протоколом TLS через TCP, или SPNego, и гарантирует целостность, конфиденциальность и проверку подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="acf76-133">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="acf76-134">Безопасность сообщений SOAP представляет проверку подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="acf76-134">SOAP message security provides client authentication.</span></span> <span data-ttu-id="acf76-135">По умолчанию проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.</span><span class="sxs-lookup"><span data-stu-id="acf76-135">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acf76-136">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="acf76-136">Child Elements</span></span>  
  
|<span data-ttu-id="acf76-137">Элемент</span><span class="sxs-lookup"><span data-stu-id="acf76-137">Element</span></span>|<span data-ttu-id="acf76-138">Описание</span><span class="sxs-lookup"><span data-stu-id="acf76-138">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="acf76-139">Определяет параметры безопасности для данного транспорта.</span><span class="sxs-lookup"><span data-stu-id="acf76-139">Defines the security settings for the transport.</span></span> <span data-ttu-id="acf76-140">Это элемент типа <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="acf76-140">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="acf76-141">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="acf76-141">Defines the security settings for the message.</span></span> <span data-ttu-id="acf76-142">Это элемент типа <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="acf76-142">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acf76-143">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="acf76-143">Parent Elements</span></span>  
  
|<span data-ttu-id="acf76-144">Элемент</span><span class="sxs-lookup"><span data-stu-id="acf76-144">Element</span></span>|<span data-ttu-id="acf76-145">Описание</span><span class="sxs-lookup"><span data-stu-id="acf76-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acf76-146">binding</span><span class="sxs-lookup"><span data-stu-id="acf76-146">binding</span></span>|<span data-ttu-id="acf76-147">Элемент Binding объекта [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="acf76-147">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf76-148">Remarks</span><span class="sxs-lookup"><span data-stu-id="acf76-148">Remarks</span></span>  

 <span data-ttu-id="acf76-149">Каждая из стандартных привязок предоставляет параметры для управления требованиями безопасности перемещения.</span><span class="sxs-lookup"><span data-stu-id="acf76-149">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="acf76-150">Эти параметры, как правило, включают режим безопасности, определяющий, используется ли безопасность уровня сообщения или уровня транспорта, а также выбор типа учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="acf76-150">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="acf76-151">На основании предоставленного выбора параметров создается стек каналов с соответствующей безопасностью.</span><span class="sxs-lookup"><span data-stu-id="acf76-151">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="acf76-152">Предоставляемые системой привязки, поставляемые Windows Communication Foundation (WCF), представляют собой набор, отвечающий требованиям наиболее распространенных сценариев.</span><span class="sxs-lookup"><span data-stu-id="acf76-152">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="acf76-153">Каждая из этих привязок позволяет задавать требования безопасности для некоторых конкретных целевых сценариев.</span><span class="sxs-lookup"><span data-stu-id="acf76-153">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="acf76-154">Элемент конфигурации предоставляет спецификации безопасности для `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="acf76-154">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="acf76-155">Это безопасная, надежная и оптимизированная привязка, пригодная для обмена данными между компьютерами.</span><span class="sxs-lookup"><span data-stu-id="acf76-155">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="acf76-156">По умолчанию она создает стек связи среды выполнения, поддерживающий протокол TCP для доставки сообщений и безопасность Windows для безопасности сообщений и проверки подлинности, WS-ReliableMessaging для надежности, а также кодирование двоичных сообщений.</span><span class="sxs-lookup"><span data-stu-id="acf76-156">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf76-157">См. также</span><span class="sxs-lookup"><span data-stu-id="acf76-157">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="acf76-158">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="acf76-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="acf76-159">Привязки</span><span class="sxs-lookup"><span data-stu-id="acf76-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="acf76-160">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="acf76-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="acf76-161">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="acf76-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
