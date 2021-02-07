---
description: 'Дополнительные сведения о: <extensions> раздел'
title: Раздел <extensions>
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 65b1de76155b1e3fbd8e5f14a5f4a1cb8c180ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664695"
---
# <a name="extensions-section"></a><span data-ttu-id="61e44-103">Раздел \<extensions></span><span class="sxs-lookup"><span data-stu-id="61e44-103">\<extensions> section</span></span>

<span data-ttu-id="61e44-104">Данный раздел конфигурации содержит коллекцию расширений, которые позволяют пользователю создавать пользовательские привязки, поведения и другие возможности расширений.</span><span class="sxs-lookup"><span data-stu-id="61e44-104">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="61e44-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61e44-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61e44-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="61e44-106">Attributes and Elements</span></span>  

 <span data-ttu-id="61e44-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="61e44-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61e44-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="61e44-108">Attributes</span></span>  

 <span data-ttu-id="61e44-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="61e44-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61e44-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="61e44-110">Child Elements</span></span>  
  
|<span data-ttu-id="61e44-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="61e44-111">Element</span></span>|<span data-ttu-id="61e44-112">Описание</span><span class="sxs-lookup"><span data-stu-id="61e44-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="61e44-113">Этот раздел содержит дочерние элементы, которые задают расширения поведений, которые позволяют пользователю настроить поведения службы или конечной точки.</span><span class="sxs-lookup"><span data-stu-id="61e44-113">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="61e44-114">В этом разделе описывается, как обеспечивается использование пользовательского элемента привязки в файле конфигурации компьютера или приложения.</span><span class="sxs-lookup"><span data-stu-id="61e44-114">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="61e44-115">Этот раздел содержит дочерние элементы, которые задают расширения привязки, которые позволяют пользователю настроить привязки.</span><span class="sxs-lookup"><span data-stu-id="61e44-115">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="61e44-116">Этот раздел содержит дочерние элементы, которые регистрируют стандартные конечные точки.</span><span class="sxs-lookup"><span data-stu-id="61e44-116">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61e44-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="61e44-117">Parent Elements</span></span>  
  
|<span data-ttu-id="61e44-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="61e44-118">Element</span></span>|<span data-ttu-id="61e44-119">Описание</span><span class="sxs-lookup"><span data-stu-id="61e44-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61e44-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="61e44-120">system.ServiceModel</span></span>|<span data-ttu-id="61e44-121">Корневой элемент всех элементов конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="61e44-121">The root element of all WCF configuration elements.</span></span>|
