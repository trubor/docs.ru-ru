---
description: 'Дополнительные сведения: <sslStreamSecurity>'
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 77e08deb5263e330ead5df21ed1ef2dddbba28ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682700"
---
# \<sslStreamSecurity>

<span data-ttu-id="3feb5-102">Представляет пользовательский элемент привязки, который поддерживает безопасность канала с помощью потока SSL.</span><span class="sxs-lookup"><span data-stu-id="3feb5-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="3feb5-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3feb5-103">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3feb5-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3feb5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3feb5-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3feb5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3feb5-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3feb5-106">Attributes</span></span>  
  
|<span data-ttu-id="3feb5-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3feb5-107">Attribute</span></span>|<span data-ttu-id="3feb5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3feb5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3feb5-109">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="3feb5-109">requireClientCertificate</span></span>|<span data-ttu-id="3feb5-110">Логическое значение, указывающее, требуется ли для этой привязки сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="3feb5-110">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="3feb5-111">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="3feb5-111">The default is `false`.</span></span>|  
|<span data-ttu-id="3feb5-112">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3feb5-112">sslProtocols</span></span>|<span data-ttu-id="3feb5-113">Значение флага перечисления SslProtocols, указывающее, какие протоколы SslProtocols поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="3feb5-113">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3feb5-114">Значение по умолчанию — Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="3feb5-114">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3feb5-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3feb5-115">Child Elements</span></span>  

 <span data-ttu-id="3feb5-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3feb5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3feb5-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3feb5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3feb5-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="3feb5-118">Element</span></span>|<span data-ttu-id="3feb5-119">Описание</span><span class="sxs-lookup"><span data-stu-id="3feb5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3feb5-120">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="3feb5-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3feb5-121">См. также</span><span class="sxs-lookup"><span data-stu-id="3feb5-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="3feb5-122">Привязки</span><span class="sxs-lookup"><span data-stu-id="3feb5-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3feb5-123">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="3feb5-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3feb5-124">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="3feb5-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
