---
description: 'Дополнительные сведения <security> о: <msmqIntegrationBinding>'
title: <security> из <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 4ad4cb89599198661d764cfeb985609be027c0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683207"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="9a0f7-103">\<security> из \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="9a0f7-103">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="9a0f7-104">Определяет параметры безопасности транспорта для канала интеграции очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="9a0f7-104">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="9a0f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a0f7-105">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a0f7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9a0f7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9a0f7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a0f7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9a0f7-108">Attributes</span></span>  
  
|<span data-ttu-id="9a0f7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9a0f7-109">Attribute</span></span>|<span data-ttu-id="9a0f7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="9a0f7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a0f7-111">mode</span><span class="sxs-lookup"><span data-stu-id="9a0f7-111">mode</span></span>|<span data-ttu-id="9a0f7-112">Задает тип системы безопасности, отвечающей за целостность, конфиденциальность и проверку подлинности при использовании канала интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-112">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="9a0f7-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9a0f7-114">-None: отключает безопасность.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-114">-   None: This disables security.</span></span><br /><span data-ttu-id="9a0f7-115">-Transport: защита и проверка подлинности предоставляются транспортом.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="9a0f7-116">Это значение связано с безопасностью сообщений между двумя диспетчерами очереди.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="9a0f7-117">Между приложением и диспетчером очереди безопасность сообщений не обеспечивается.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="9a0f7-118">Существующие Msmq-приложения функционально равноценны такому режиму безопасности.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="9a0f7-119">Значение по умолчанию — `Transport`.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-119">The default value is `Transport`.</span></span> <span data-ttu-id="9a0f7-120">Это атрибут типа <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-120">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a0f7-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9a0f7-121">Child Elements</span></span>  
  
|<span data-ttu-id="9a0f7-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="9a0f7-122">Element</span></span>|<span data-ttu-id="9a0f7-123">Описание</span><span class="sxs-lookup"><span data-stu-id="9a0f7-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="9a0f7-124">Определяет параметры безопасности для транспорта интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-124">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="9a0f7-125">Это элемент типа <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9a0f7-125">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a0f7-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9a0f7-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9a0f7-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="9a0f7-127">Element</span></span>|<span data-ttu-id="9a0f7-128">Описание</span><span class="sxs-lookup"><span data-stu-id="9a0f7-128">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9a0f7-129">Элемент Binding объекта [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9a0f7-129">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a0f7-130">См. также</span><span class="sxs-lookup"><span data-stu-id="9a0f7-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="9a0f7-131">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="9a0f7-131">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="9a0f7-132">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9a0f7-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9a0f7-133">Привязки</span><span class="sxs-lookup"><span data-stu-id="9a0f7-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a0f7-134">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="9a0f7-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9a0f7-135">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9a0f7-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
