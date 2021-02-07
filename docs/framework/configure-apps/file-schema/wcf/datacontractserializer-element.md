---
description: 'Дополнительные сведения: <dataContractSerializer>'
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 0705a40f55d76ef46a7debcd4ecfb5235c7c0d21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754437"
---
# \<dataContractSerializer>

<span data-ttu-id="52d85-102">Содержит данные конфигурации для <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52d85-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="52d85-103">Этот элемент присутствует в двух разных иерархиях.</span><span class="sxs-lookup"><span data-stu-id="52d85-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="52d85-104">Одна из них указана в следующем разделе «Иерархия схемы», а другая - в разделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="52d85-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="52d85-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52d85-105">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52d85-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="52d85-106">Attributes and Elements</span></span>  

 <span data-ttu-id="52d85-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="52d85-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52d85-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="52d85-108">Attributes</span></span>  
  
|<span data-ttu-id="52d85-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="52d85-109">Element</span></span>|<span data-ttu-id="52d85-110">Описание</span><span class="sxs-lookup"><span data-stu-id="52d85-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52d85-111">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="52d85-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="52d85-112">Логическое значение, указывающее, пропускать ли данные, предоставленные конечной точкой при ее сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="52d85-112">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="52d85-113">Этот атрибут можно задать только в `<dataContractSerializer>` в элементе `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="52d85-113">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="52d85-114">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="52d85-114">maxItemsInObjectGraph</span></span>|<span data-ttu-id="52d85-115">Целое число, указывающее максимальное количество элементов для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="52d85-115">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="52d85-116">Этот атрибут имеет значение 65 536.</span><span class="sxs-lookup"><span data-stu-id="52d85-116">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52d85-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="52d85-117">Child Elements</span></span>  

 <span data-ttu-id="52d85-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="52d85-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52d85-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="52d85-119">Parent Elements</span></span>  
  
|<span data-ttu-id="52d85-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="52d85-120">Element</span></span>|<span data-ttu-id="52d85-121">Описание</span><span class="sxs-lookup"><span data-stu-id="52d85-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="52d85-122">Коллекция параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="52d85-122">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="52d85-123">Представляет корневой элемент для раздела пространства имен <xref:System.Runtime.Serialization> и содержит элементы для установки параметров <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52d85-123">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d85-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="52d85-124">Remarks</span></span>  

 <span data-ttu-id="52d85-125">Как указано в статье Введение в этот раздел, это вторая иерархия, в которой \<X509Extension> происходит элемент.</span><span class="sxs-lookup"><span data-stu-id="52d85-125">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="52d85-126">Дополнительные сведения об известных типах см. в разделе <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52d85-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d85-127">См. также</span><span class="sxs-lookup"><span data-stu-id="52d85-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="52d85-128">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="52d85-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="52d85-129">Передача данных и сериализация</span><span class="sxs-lookup"><span data-stu-id="52d85-129">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
