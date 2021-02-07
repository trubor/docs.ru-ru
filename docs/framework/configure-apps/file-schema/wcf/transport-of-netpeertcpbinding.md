---
description: 'Дополнительные сведения <transport> о: <netPeerTcpBinding>'
title: <transport> из <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: e93885234577e4f3c7a99be66e4798d33ffb5893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664578"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="2005d-103">\<transport> из \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2005d-103">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="2005d-104">Задает параметры безопасности на транспортном уровне при использовании [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2005d-104">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2005d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2005d-105">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2005d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2005d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2005d-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2005d-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2005d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2005d-108">Attributes</span></span>  
  
|<span data-ttu-id="2005d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2005d-109">Attribute</span></span>|<span data-ttu-id="2005d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2005d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2005d-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="2005d-111">credentialType</span></span>|<span data-ttu-id="2005d-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="2005d-112">Optional.</span></span> <span data-ttu-id="2005d-113">Задает тип учетных данных, используемых для проверки сообщений, отправляемых с помощью однорангового транспорта.</span><span class="sxs-lookup"><span data-stu-id="2005d-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="2005d-114">Это атрибут типа <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2005d-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="2005d-115">Атрибут credentialType</span><span class="sxs-lookup"><span data-stu-id="2005d-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="2005d-116">Значение</span><span class="sxs-lookup"><span data-stu-id="2005d-116">Value</span></span>|<span data-ttu-id="2005d-117">Описание</span><span class="sxs-lookup"><span data-stu-id="2005d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2005d-118">Certificate</span><span class="sxs-lookup"><span data-stu-id="2005d-118">Certificate</span></span>|<span data-ttu-id="2005d-119">Для проверки подлинности однорангового транспорта канала необходим сертификат X.509.</span><span class="sxs-lookup"><span data-stu-id="2005d-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="2005d-120">Пароль</span><span class="sxs-lookup"><span data-stu-id="2005d-120">Password</span></span>|<span data-ttu-id="2005d-121">Для проверки подлинности однорангового транспорта канала необходим правильный пароль.</span><span class="sxs-lookup"><span data-stu-id="2005d-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2005d-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2005d-122">Child Elements</span></span>  

 <span data-ttu-id="2005d-123">None</span><span class="sxs-lookup"><span data-stu-id="2005d-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2005d-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2005d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2005d-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="2005d-125">Element</span></span>|<span data-ttu-id="2005d-126">Описание</span><span class="sxs-lookup"><span data-stu-id="2005d-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="2005d-127">Определяет параметры безопасности для [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2005d-127">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2005d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2005d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="2005d-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2005d-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2005d-130">Привязки</span><span class="sxs-lookup"><span data-stu-id="2005d-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2005d-131">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="2005d-131">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2005d-132">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2005d-132">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
