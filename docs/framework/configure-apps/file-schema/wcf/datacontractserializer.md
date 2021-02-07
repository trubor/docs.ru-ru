---
description: 'Дополнительные сведения: dataContractSerializer'
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 5dee59ba97a1632c142179aee79058dd3ce8c349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754411"
---
# <a name="datacontractserializer"></a><span data-ttu-id="80dd0-103">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="80dd0-103">dataContractSerializer</span></span>

<span data-ttu-id="80dd0-104">Содержит данные конфигурации для <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="80dd0-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="80dd0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="80dd0-105">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80dd0-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="80dd0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="80dd0-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="80dd0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80dd0-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="80dd0-108">Attributes</span></span>  
  
|<span data-ttu-id="80dd0-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="80dd0-109">Element</span></span>|<span data-ttu-id="80dd0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="80dd0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80dd0-111">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="80dd0-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="80dd0-112">Логическое значение, указывающее, должны ли пропускаться данные, предоставляемые конечной точкой, при их сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="80dd0-112">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="80dd0-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="80dd0-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="80dd0-114">Целое число, указывающее максимальное количество элементов для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="80dd0-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80dd0-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="80dd0-115">Child Elements</span></span>  

 <span data-ttu-id="80dd0-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="80dd0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80dd0-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="80dd0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="80dd0-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="80dd0-118">Element</span></span>|<span data-ttu-id="80dd0-119">Описание</span><span class="sxs-lookup"><span data-stu-id="80dd0-119">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="80dd0-120">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="80dd0-120">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80dd0-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="80dd0-121">Remarks</span></span>  

 <span data-ttu-id="80dd0-122">Дополнительные сведения об известных типах см. в документации по <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="80dd0-122">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="80dd0-123">Элемент поведения `<dataContractSerializer>` (если он присутствует) должен всегда находиться в файле конфигурации перед элементом поведения `<enableWebScript>`.</span><span class="sxs-lookup"><span data-stu-id="80dd0-123">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="80dd0-124">В противном случае результирующее поведение является неопределенным.</span><span class="sxs-lookup"><span data-stu-id="80dd0-124">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80dd0-125">См. также</span><span class="sxs-lookup"><span data-stu-id="80dd0-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="80dd0-126">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="80dd0-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="80dd0-127">Передача данных и сериализация</span><span class="sxs-lookup"><span data-stu-id="80dd0-127">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
