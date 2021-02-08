---
description: 'Дополнительные сведения: <host>'
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ff240c85af3aab7c1208a6a49b1943f3c6a8cd99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802285"
---
# \<host>

<span data-ttu-id="b660b-102">Задает параметры узла службы.</span><span class="sxs-lookup"><span data-stu-id="b660b-102">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="b660b-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b660b-103">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="b660b-104">Тип</span><span class="sxs-lookup"><span data-stu-id="b660b-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b660b-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b660b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b660b-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b660b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b660b-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b660b-107">Attributes</span></span>  

 <span data-ttu-id="b660b-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b660b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b660b-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b660b-109">Child Elements</span></span>  
  
|<span data-ttu-id="b660b-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="b660b-110">Element</span></span>|<span data-ttu-id="b660b-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b660b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="b660b-112">Коллекция элементов`baseAddress`, которая задает базовые адреса, используемые узлом службы.</span><span class="sxs-lookup"><span data-stu-id="b660b-112">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="b660b-113">Элемент конфигурации, задающий допустимый интервал времени для открытия или закрытия узла службы.</span><span class="sxs-lookup"><span data-stu-id="b660b-113">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b660b-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b660b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b660b-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="b660b-115">Element</span></span>|<span data-ttu-id="b660b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b660b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="b660b-117">Задает параметры для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b660b-117">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b660b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b660b-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="b660b-119">Размещение</span><span class="sxs-lookup"><span data-stu-id="b660b-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
