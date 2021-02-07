---
description: 'Дополнительные сведения: <baseAddresses>'
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: a32afc23d4332bad149765a318c3ecdc73f99be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749692"
---
# \<baseAddresses>

<span data-ttu-id="05964-102">Представляет коллекцию элементов `baseAddress`, которые являются базовыми адресам для узла службы в резидентной среде.</span><span class="sxs-lookup"><span data-stu-id="05964-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="05964-103">Если указан базовый адрес, конечные точки можно настроить, используя относительные (по отношению к базовому адресу) адреса.</span><span class="sxs-lookup"><span data-stu-id="05964-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="05964-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="05964-104">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="05964-105">Тип</span><span class="sxs-lookup"><span data-stu-id="05964-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05964-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="05964-106">Attributes and Elements</span></span>  

 <span data-ttu-id="05964-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="05964-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05964-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="05964-108">Attributes</span></span>  

 <span data-ttu-id="05964-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="05964-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05964-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="05964-110">Child Elements</span></span>  
  
|<span data-ttu-id="05964-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="05964-111">Element</span></span>|<span data-ttu-id="05964-112">Описание</span><span class="sxs-lookup"><span data-stu-id="05964-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="05964-113">Элемент конфигурации, который задает базовые адреса, используемые узлом службы.</span><span class="sxs-lookup"><span data-stu-id="05964-113">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05964-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="05964-114">Parent Elements</span></span>  
  
|<span data-ttu-id="05964-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="05964-115">Element</span></span>|<span data-ttu-id="05964-116">Описание</span><span class="sxs-lookup"><span data-stu-id="05964-116">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="05964-117">Элемент конфигурации, который задает параметры узла службы.</span><span class="sxs-lookup"><span data-stu-id="05964-117">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05964-118">См. также</span><span class="sxs-lookup"><span data-stu-id="05964-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="05964-119">Размещение</span><span class="sxs-lookup"><span data-stu-id="05964-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
