---
description: 'Дополнительные сведения <security> о: <netMsmqBinding>'
title: <security> из <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1b60d9e390e371555f4c3abf4988e79bb0f04fe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786854"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="0131a-103">\<security> из \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="0131a-103">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="0131a-104">Определяет параметры безопасности для привязки MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0131a-104">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="0131a-105">Он указывает, включена ли поддержка транспорта или безопасности SOAP и, если поддержка включена, указывает используемые уровни защиты и режим проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0131a-105">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="0131a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0131a-106">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0131a-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0131a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="0131a-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0131a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0131a-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0131a-109">Attributes</span></span>  
  
|<span data-ttu-id="0131a-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0131a-110">Attribute</span></span>|<span data-ttu-id="0131a-111">Описание</span><span class="sxs-lookup"><span data-stu-id="0131a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0131a-112">mode</span><span class="sxs-lookup"><span data-stu-id="0131a-112">mode</span></span>|<span data-ttu-id="0131a-113">Задает тип безопасности, который контролирует целостность, конфиденциальность и проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="0131a-113">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="0131a-114">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="0131a-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0131a-115">-None: отключает безопасность.</span><span class="sxs-lookup"><span data-stu-id="0131a-115">-   None: This disables security.</span></span><br /><span data-ttu-id="0131a-116">-Transport: защита и проверка подлинности предоставляются транспортом.</span><span class="sxs-lookup"><span data-stu-id="0131a-116">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="0131a-117">Это значение связано с безопасностью сообщений между двумя диспетчерами очереди.</span><span class="sxs-lookup"><span data-stu-id="0131a-117">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="0131a-118">Между приложением и диспетчером очереди безопасность сообщений не обеспечивается.</span><span class="sxs-lookup"><span data-stu-id="0131a-118">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="0131a-119">Существующие Msmq-приложения функционально равноценны такому режиму безопасности.</span><span class="sxs-lookup"><span data-stu-id="0131a-119">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="0131a-120">-Message: определяет безопасность конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="0131a-120">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="0131a-121">Безопасность на транспортном уровне не предоставляется.</span><span class="sxs-lookup"><span data-stu-id="0131a-121">There is no security offered at the transport layer.</span></span> <span data-ttu-id="0131a-122">Такие параметры аналогичны параметрам безопасности, предоставляемой другими стандартными привязками.</span><span class="sxs-lookup"><span data-stu-id="0131a-122">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="0131a-123">Оба: обеспечивают безопасность на уровне транспорта и сообщений протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="0131a-123">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="0131a-124">На обоих уровнях требуются одни и те же учетные данные.</span><span class="sxs-lookup"><span data-stu-id="0131a-124">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="0131a-125">Значение по умолчанию - Transport.</span><span class="sxs-lookup"><span data-stu-id="0131a-125">The default value is Transport.</span></span> <span data-ttu-id="0131a-126">Это атрибут типа <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0131a-126">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0131a-127">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0131a-127">Child Elements</span></span>  
  
|<span data-ttu-id="0131a-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="0131a-128">Element</span></span>|<span data-ttu-id="0131a-129">Описание</span><span class="sxs-lookup"><span data-stu-id="0131a-129">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="0131a-130">Определяет параметры безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="0131a-130">Defines the SOAP message security settings.</span></span> <span data-ttu-id="0131a-131">Это элемент типа <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="0131a-131">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="0131a-132">Определяет параметры безопасности для транспорта MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0131a-132">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="0131a-133">Это элемент типа <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0131a-133">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0131a-134">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0131a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="0131a-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="0131a-135">Element</span></span>|<span data-ttu-id="0131a-136">Описание</span><span class="sxs-lookup"><span data-stu-id="0131a-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0131a-137">binding</span><span class="sxs-lookup"><span data-stu-id="0131a-137">binding</span></span>|<span data-ttu-id="0131a-138">Элемент binding элемента [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0131a-138">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0131a-139">См. также</span><span class="sxs-lookup"><span data-stu-id="0131a-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="0131a-140">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="0131a-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0131a-141">Привязки</span><span class="sxs-lookup"><span data-stu-id="0131a-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0131a-142">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="0131a-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0131a-143">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="0131a-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="0131a-144">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="0131a-144">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
