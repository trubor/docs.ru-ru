---
description: 'Дополнительные сведения о: <peer> <clientCredentials> element'
title: <peer> элемента <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 1ff9386ba51dcf6bab6df71bd345cdaa59f18e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683792"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="855fd-103">\<peer> элемента \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="855fd-103">\<peer> of \<clientCredentials> Element</span></span>

<span data-ttu-id="855fd-104">Задает учетные данные, используемые при проверке подлинности одноранговых клиентов.</span><span class="sxs-lookup"><span data-stu-id="855fd-104">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="855fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="855fd-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="855fd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="855fd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="855fd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="855fd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="855fd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="855fd-108">Attributes</span></span>  

 <span data-ttu-id="855fd-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="855fd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="855fd-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="855fd-110">Child Elements</span></span>  
  
|<span data-ttu-id="855fd-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="855fd-111">Element</span></span>|<span data-ttu-id="855fd-112">Описание</span><span class="sxs-lookup"><span data-stu-id="855fd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="855fd-113">Задает сертификат X.509, используемый для подписи и шифрования сообщений для клиентов одноранговых сетей.</span><span class="sxs-lookup"><span data-stu-id="855fd-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="855fd-114">.</span><span class="sxs-lookup"><span data-stu-id="855fd-114">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="855fd-115">Задает параметры проверки подлинности для одноранговых клиентов.</span><span class="sxs-lookup"><span data-stu-id="855fd-115">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="855fd-116">Задает параметры проверки подлинности для отправителей сообщений.</span><span class="sxs-lookup"><span data-stu-id="855fd-116">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="855fd-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="855fd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="855fd-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="855fd-118">Element</span></span>|<span data-ttu-id="855fd-119">Описание</span><span class="sxs-lookup"><span data-stu-id="855fd-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="855fd-120">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="855fd-120">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="855fd-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="855fd-121">Remarks</span></span>  

 <span data-ttu-id="855fd-122">Этот элемент конфигурации задает учетные данные, используемые одноранговым узлом для подтверждения своей подлинности для других узлов в сетке, а также параметры, используемые одноранговым узлом для проверки подлинности других одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="855fd-122">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="855fd-123">Дополнительные сведения см. в статье [Проверка подлинности сообщений одноранговых каналов](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) и [Защита приложений одноранговых каналов](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="855fd-123">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855fd-124">См. также</span><span class="sxs-lookup"><span data-stu-id="855fd-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="855fd-125">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="855fd-125">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="855fd-126">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="855fd-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="855fd-127">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="855fd-127">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="855fd-128">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="855fd-128">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="855fd-129">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="855fd-129">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="855fd-130">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="855fd-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
