---
description: 'Дополнительные сведения: <mexEndpoint>'
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 1872b6104aaaaa2787ca3f359026552499bade9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684416"
---
# \<mexEndpoint>

<span data-ttu-id="e0ebb-102">Этот элемент конфигурации определяет стандартную конечную точку с фиксированным контрактом IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="e0ebb-103">Поскольку все конечные точки обмена метаданными указывают IMetadataExchange в качестве своего контракта, можно использовать эту стандартную точку вместо определения собственной точки.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="e0ebb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0ebb-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0ebb-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e0ebb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e0ebb-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0ebb-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e0ebb-107">Attributes</span></span>  
  
|<span data-ttu-id="e0ebb-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e0ebb-108">Attribute</span></span>|<span data-ttu-id="e0ebb-109">Описание</span><span class="sxs-lookup"><span data-stu-id="e0ebb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0ebb-110">name</span><span class="sxs-lookup"><span data-stu-id="e0ebb-110">name</span></span>|<span data-ttu-id="e0ebb-111">Строка, указывающая имя конфигурации стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-111">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e0ebb-112">Это имя используется в атрибуте `endpointConfiguration` конечной точки службы для связывания стандартной конечной точки с ее конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-112">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0ebb-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e0ebb-113">Child Elements</span></span>  

 <span data-ttu-id="e0ebb-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0ebb-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e0ebb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e0ebb-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ebb-116">Element</span></span>|<span data-ttu-id="e0ebb-117">Описание</span><span class="sxs-lookup"><span data-stu-id="e0ebb-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="e0ebb-118">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="e0ebb-118">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
