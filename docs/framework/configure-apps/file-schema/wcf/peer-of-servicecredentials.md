---
description: 'Дополнительные сведения <peer> о: <serviceCredentials>'
title: <peer> из <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 4d959f5061bb8069623b277219576dbd77ea52c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683740"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="59534-103">\<peer> из \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="59534-103">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="59534-104">Задает текущие учетные данные для однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="59534-104">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="59534-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59534-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59534-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="59534-106">Attributes and Elements</span></span>  

 <span data-ttu-id="59534-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="59534-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59534-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="59534-108">Attributes</span></span>  

 <span data-ttu-id="59534-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="59534-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59534-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="59534-110">Child Elements</span></span>  
  
|<span data-ttu-id="59534-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="59534-111">Element</span></span>|<span data-ttu-id="59534-112">Описание</span><span class="sxs-lookup"><span data-stu-id="59534-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="59534-113">Задает сертификат X.509, используемый для подписи и шифрования сообщений для служб одноранговых сетей.</span><span class="sxs-lookup"><span data-stu-id="59534-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="59534-114">.</span><span class="sxs-lookup"><span data-stu-id="59534-114">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="59534-115">Задает параметры проверки подлинности для отправителей сообщений.</span><span class="sxs-lookup"><span data-stu-id="59534-115">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="59534-116">Задает параметры проверки подлинности для одноранговых служб.</span><span class="sxs-lookup"><span data-stu-id="59534-116">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59534-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="59534-117">Parent Elements</span></span>  
  
|<span data-ttu-id="59534-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="59534-118">Element</span></span>|<span data-ttu-id="59534-119">Описание</span><span class="sxs-lookup"><span data-stu-id="59534-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="59534-120">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="59534-120">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59534-121">См. также</span><span class="sxs-lookup"><span data-stu-id="59534-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="59534-122">Одноранговая сеть</span><span class="sxs-lookup"><span data-stu-id="59534-122">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="59534-123">[Проверка подлинности сообщений для однорангового канала](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="59534-123">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="59534-124">[Пользовательской проверка подлинности для однорангового канала](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="59534-124">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="59534-125">Защита приложений одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="59534-125">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="59534-126">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="59534-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
