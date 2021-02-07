---
description: 'Дополнительные сведения о: <dataContractSerializer> <System. Runtime. serialization>'
title: <dataContractSerializer> <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 3755005782ea773344326d211b9f8f115a97f2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754424"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="2df8c-103">\<dataContractSerializer> из \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2df8c-103">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="2df8c-104">Содержит данные конфигурации для <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2df8c-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="2df8c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2df8c-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2df8c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2df8c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2df8c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2df8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2df8c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2df8c-108">Attributes</span></span>  
  
|<span data-ttu-id="2df8c-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="2df8c-109">Element</span></span>|<span data-ttu-id="2df8c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2df8c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2df8c-111">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2df8c-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2df8c-112">Логическое значение, указывающее, пропускать ли данные, предоставленные конечной точкой при ее сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="2df8c-112">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="2df8c-113">Этот атрибут можно задать только в `<dataContractSerializer>` в элементе `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="2df8c-113">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="2df8c-114">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2df8c-114">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2df8c-115">Целое число, указывающее максимальное количество элементов для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="2df8c-115">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="2df8c-116">Этот атрибут имеет значение 65 536.</span><span class="sxs-lookup"><span data-stu-id="2df8c-116">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2df8c-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2df8c-117">Child Elements</span></span>  
  
|<span data-ttu-id="2df8c-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="2df8c-118">Element</span></span>|<span data-ttu-id="2df8c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="2df8c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="2df8c-120">Содержит известные типы, которые <xref:System.Runtime.Serialization.DataContractSerializer> использует при десериализации.</span><span class="sxs-lookup"><span data-stu-id="2df8c-120">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="2df8c-121">Дополнительные сведения о контрактах данных и известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2df8c-121">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2df8c-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2df8c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2df8c-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="2df8c-123">Element</span></span>|<span data-ttu-id="2df8c-124">Описание</span><span class="sxs-lookup"><span data-stu-id="2df8c-124">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="2df8c-125">Представляет корневой элемент для раздела пространства имен <xref:System.Runtime.Serialization> и содержит элементы для установки параметров <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2df8c-125">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2df8c-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="2df8c-126">Remarks</span></span>  

 <span data-ttu-id="2df8c-127">Дополнительные сведения об известных типах см. в разделе <xref:System.Runtime.Serialization.DataContractSerializer> и [известные типы контракта данных](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2df8c-127">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df8c-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2df8c-128">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="2df8c-129">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="2df8c-129">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
