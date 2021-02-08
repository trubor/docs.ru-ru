---
description: 'Дополнительные сведения: <declaredTypes>'
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: e5f60209dd556edc7cf47b01b1a58c1f17d74eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803936"
---
# \<declaredTypes>

<span data-ttu-id="cd14e-102">Содержит известные типы, которые <xref:System.Runtime.Serialization.DataContractSerializer> использует при десериализации.</span><span class="sxs-lookup"><span data-stu-id="cd14e-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="cd14e-103">Дополнительные сведения о контрактах данных и известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd14e-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="cd14e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd14e-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd14e-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="cd14e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cd14e-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="cd14e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd14e-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="cd14e-107">Attributes</span></span>  

 <span data-ttu-id="cd14e-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="cd14e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd14e-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="cd14e-109">Child Elements</span></span>  
  
|<span data-ttu-id="cd14e-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="cd14e-110">Element</span></span>|<span data-ttu-id="cd14e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="cd14e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="cd14e-112">Добавляет типы, для которых необходимы известные типы.</span><span class="sxs-lookup"><span data-stu-id="cd14e-112">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd14e-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="cd14e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="cd14e-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="cd14e-114">Element</span></span>|<span data-ttu-id="cd14e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="cd14e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="cd14e-116">Содержит данные конфигурации для <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cd14e-116">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd14e-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd14e-117">Remarks</span></span>  

 <span data-ttu-id="cd14e-118">Дополнительные сведения об известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md) и <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="cd14e-118">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd14e-119">Пример</span><span class="sxs-lookup"><span data-stu-id="cd14e-119">Example</span></span>  

 <span data-ttu-id="cd14e-120">В следующем коде XML показаны объявленные типы и известные типы, добавленные в `DataContractSerializer` элемент.</span><span class="sxs-lookup"><span data-stu-id="cd14e-120">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="cd14e-121">В этом примере показаны три добавляемых типа.</span><span class="sxs-lookup"><span data-stu-id="cd14e-121">The example shows three types being added.</span></span> <span data-ttu-id="cd14e-122">Первый тип - это пользовательский тип с именем «Orders», использующий известный тип с именем «Item».</span><span class="sxs-lookup"><span data-stu-id="cd14e-122">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="cd14e-123">Второй объявленный тип - это <xref:System.Collections.Generic.List%601>, использующий `Item` в качестве известного типа.</span><span class="sxs-lookup"><span data-stu-id="cd14e-123">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="cd14e-124">Наконец, третий объявленный тип - это <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="cd14e-124">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="cd14e-125">Тип класса <xref:System.Collections.Generic.Dictionary%602> является универсальным типом с двумя параметрами типов.</span><span class="sxs-lookup"><span data-stu-id="cd14e-125">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="cd14e-126">Первый представляет ключ, а второй представляет значение.</span><span class="sxs-lookup"><span data-stu-id="cd14e-126">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="cd14e-127">В следующем примере параметр второго типа <xref:System.Collections.Generic.List%601> (значение) добавляется к списку известных типов.</span><span class="sxs-lookup"><span data-stu-id="cd14e-127">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="cd14e-128">Чтобы задать параметр типа для использования в известном типе, необходимо использовать атрибут `index`.</span><span class="sxs-lookup"><span data-stu-id="cd14e-128">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="cd14e-129">В данном примере тип значения указан атрибутом индекса, для которого задано значение 1 (коллекция начинается с нуля).</span><span class="sxs-lookup"><span data-stu-id="cd14e-129">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="cd14e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="cd14e-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="cd14e-131">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="cd14e-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
