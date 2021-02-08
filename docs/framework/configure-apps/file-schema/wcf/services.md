---
description: 'Дополнительные сведения: <services>'
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 6e8c0c5ad5390c097db7bf1be1f0d489e1c0d624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786711"
---
# \<services>

<span data-ttu-id="d7d5e-102">Службы задаются в разделе `services` файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d7d5e-103">Для каждой службы используется собственный раздел конфигурации `service`.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-103">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="d7d5e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7d5e-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7d5e-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d7d5e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d7d5e-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7d5e-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d7d5e-107">Attributes</span></span>  

 <span data-ttu-id="d7d5e-108">None</span><span class="sxs-lookup"><span data-stu-id="d7d5e-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7d5e-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d7d5e-109">Child Elements</span></span>  
  
|<span data-ttu-id="d7d5e-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="d7d5e-110">Element</span></span>|<span data-ttu-id="d7d5e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="d7d5e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="d7d5e-112">Определяет контракт службы, поведение и конечные точки конкретной службы.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-112">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7d5e-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d7d5e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d7d5e-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="d7d5e-114">Element</span></span>|<span data-ttu-id="d7d5e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="d7d5e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="d7d5e-116">Корневой элемент всех элементов конфигурации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d7d5e-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7d5e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d7d5e-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
