---
description: 'Дополнительные сведения <security> о: <wsDualHttpBinding>'
title: <security> из <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 6d2e87912aef6114d7dcb99b82e4a7804317b28a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683038"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="98693-103">\<security> из \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="98693-103">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="98693-104">Определяет возможности безопасности для [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="98693-104">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="98693-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98693-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98693-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="98693-106">Attributes and Elements</span></span>  

 <span data-ttu-id="98693-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="98693-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98693-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="98693-108">Attributes</span></span>  
  
|<span data-ttu-id="98693-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="98693-109">Attribute</span></span>|<span data-ttu-id="98693-110">Описание</span><span class="sxs-lookup"><span data-stu-id="98693-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98693-111">mode</span><span class="sxs-lookup"><span data-stu-id="98693-111">mode</span></span>|<span data-ttu-id="98693-112">Используемых.</span><span class="sxs-lookup"><span data-stu-id="98693-112">-   Optional.</span></span> <span data-ttu-id="98693-113">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="98693-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="98693-114">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="98693-114">The default value is `Message`.</span></span> <span data-ttu-id="98693-115">Это атрибут типа <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="98693-115">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="98693-116">Атрибут Mode</span><span class="sxs-lookup"><span data-stu-id="98693-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="98693-117">Значение</span><span class="sxs-lookup"><span data-stu-id="98693-117">Value</span></span>|<span data-ttu-id="98693-118">Описание</span><span class="sxs-lookup"><span data-stu-id="98693-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98693-119">None</span><span class="sxs-lookup"><span data-stu-id="98693-119">None</span></span>|<span data-ttu-id="98693-120">Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="98693-120">Security is disabled.</span></span>|  
|<span data-ttu-id="98693-121">Сообщение</span><span class="sxs-lookup"><span data-stu-id="98693-121">Message</span></span>|<span data-ttu-id="98693-122">Безопасность обеспечивается с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="98693-122">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98693-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="98693-123">Child Elements</span></span>  
  
|<span data-ttu-id="98693-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="98693-124">Element</span></span>|<span data-ttu-id="98693-125">Описание</span><span class="sxs-lookup"><span data-stu-id="98693-125">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="98693-126">Определяет параметры безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="98693-126">Defines the settings for the message-level security.</span></span> <span data-ttu-id="98693-127">Это элемент типа <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="98693-127">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98693-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="98693-128">Parent Elements</span></span>  
  
|<span data-ttu-id="98693-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="98693-129">Element</span></span>|<span data-ttu-id="98693-130">Описание</span><span class="sxs-lookup"><span data-stu-id="98693-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="98693-131">Определяет все возможности привязки [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="98693-131">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98693-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="98693-132">Remarks</span></span>  

 <span data-ttu-id="98693-133">Двойная привязка предоставляет службе IP-адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="98693-133">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="98693-134">Клиенту следует использовать механизм безопасности, чтобы гарантировать, что подключение выполняется только к доверенным службам.</span><span class="sxs-lookup"><span data-stu-id="98693-134">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98693-135">См. также</span><span class="sxs-lookup"><span data-stu-id="98693-135">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="98693-136">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="98693-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="98693-137">Привязки</span><span class="sxs-lookup"><span data-stu-id="98693-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="98693-138">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="98693-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="98693-139">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="98693-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
