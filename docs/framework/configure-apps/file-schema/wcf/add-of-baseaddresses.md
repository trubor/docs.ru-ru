---
description: 'Дополнительные сведения <add> о: <baseAddresses>'
title: <add> из <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: b25a4b5551784ecd8e67569c82c1388a144a9c9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804066"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="abb5e-103">\<add> из \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="abb5e-103">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="abb5e-104">Представляет элемент конфигурации, который задает базовые адреса, используемые узлом службы.</span><span class="sxs-lookup"><span data-stu-id="abb5e-104">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="abb5e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="abb5e-105">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="abb5e-106">Тип</span><span class="sxs-lookup"><span data-stu-id="abb5e-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb5e-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="abb5e-107">Attributes and Elements</span></span>  

 <span data-ttu-id="abb5e-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="abb5e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abb5e-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="abb5e-109">Attributes</span></span>  
  
|<span data-ttu-id="abb5e-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="abb5e-110">Attribute</span></span>|<span data-ttu-id="abb5e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="abb5e-111">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="abb5e-112">Строка, которая задает базовый адрес, используемый узлом службы.</span><span class="sxs-lookup"><span data-stu-id="abb5e-112">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abb5e-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="abb5e-113">Child Elements</span></span>  

 <span data-ttu-id="abb5e-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="abb5e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abb5e-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="abb5e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="abb5e-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="abb5e-116">Element</span></span>|<span data-ttu-id="abb5e-117">Описание</span><span class="sxs-lookup"><span data-stu-id="abb5e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="abb5e-118">Коллекция элементов `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="abb5e-118">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abb5e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="abb5e-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="abb5e-120">Размещение</span><span class="sxs-lookup"><span data-stu-id="abb5e-120">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
