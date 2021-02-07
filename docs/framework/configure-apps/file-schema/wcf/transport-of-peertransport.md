---
description: 'Дополнительные сведения <transport> о: <peerTransport>'
title: <transport> из <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: ba3405c5dfadb513f92ebd537409a3f7b12fa291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664513"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="af2fb-103">\<transport> из \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="af2fb-103">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="af2fb-104">Задает тип транспорта для безопасных сообщений, отправленных одноранговыми узлами, настроенными с помощью этой привязки.</span><span class="sxs-lookup"><span data-stu-id="af2fb-104">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="af2fb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af2fb-105">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af2fb-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="af2fb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="af2fb-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="af2fb-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af2fb-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="af2fb-108">Attributes</span></span>  
  
|<span data-ttu-id="af2fb-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="af2fb-109">Attribute</span></span>|<span data-ttu-id="af2fb-110">Описание</span><span class="sxs-lookup"><span data-stu-id="af2fb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af2fb-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="af2fb-111">credentialType</span></span>|<span data-ttu-id="af2fb-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="af2fb-112">Optional.</span></span> <span data-ttu-id="af2fb-113">Задает тип учетных данных, используемых для проверки сообщений, отправляемых с помощью однорангового транспорта.</span><span class="sxs-lookup"><span data-stu-id="af2fb-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="af2fb-114">Это атрибут типа <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="af2fb-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="af2fb-115">Атрибут credentialType</span><span class="sxs-lookup"><span data-stu-id="af2fb-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="af2fb-116">Значение</span><span class="sxs-lookup"><span data-stu-id="af2fb-116">Value</span></span>|<span data-ttu-id="af2fb-117">Описание</span><span class="sxs-lookup"><span data-stu-id="af2fb-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af2fb-118">Certificate</span><span class="sxs-lookup"><span data-stu-id="af2fb-118">Certificate</span></span>|<span data-ttu-id="af2fb-119">Для проверки подлинности однорангового транспорта канала необходим сертификат X.509.</span><span class="sxs-lookup"><span data-stu-id="af2fb-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="af2fb-120">Пароль</span><span class="sxs-lookup"><span data-stu-id="af2fb-120">Password</span></span>|<span data-ttu-id="af2fb-121">Для проверки подлинности однорангового транспорта канала необходим правильный пароль.</span><span class="sxs-lookup"><span data-stu-id="af2fb-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af2fb-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="af2fb-122">Child Elements</span></span>  

 <span data-ttu-id="af2fb-123">None</span><span class="sxs-lookup"><span data-stu-id="af2fb-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af2fb-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="af2fb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="af2fb-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="af2fb-125">Element</span></span>|<span data-ttu-id="af2fb-126">Описание</span><span class="sxs-lookup"><span data-stu-id="af2fb-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="af2fb-127">Определяет параметры безопасности для однорангового транспорта.</span><span class="sxs-lookup"><span data-stu-id="af2fb-127">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af2fb-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="af2fb-128">Remarks</span></span>  

 <span data-ttu-id="af2fb-129">Этот элемент задается только в том случае, если атрибут mode [\<security>](security-of-peertransport.md) имеет значение `Transport` или `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="af2fb-129">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2fb-130">См. также</span><span class="sxs-lookup"><span data-stu-id="af2fb-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="af2fb-131">Безопасность транспорта</span><span class="sxs-lookup"><span data-stu-id="af2fb-131">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="af2fb-132">Транспорты</span><span class="sxs-lookup"><span data-stu-id="af2fb-132">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="af2fb-133">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="af2fb-133">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="af2fb-134">Привязки</span><span class="sxs-lookup"><span data-stu-id="af2fb-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="af2fb-135">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="af2fb-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="af2fb-136">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="af2fb-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
