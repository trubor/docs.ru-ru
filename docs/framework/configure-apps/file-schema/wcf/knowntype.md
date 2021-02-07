---
description: 'Дополнительные сведения: <knownType>'
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 205f799c81263be3dd08aae9efefb975b06a0cc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725510"
---
# \<knownType>

<span data-ttu-id="04888-102">Задает тип, используемый <xref:System.Runtime.Serialization.DataContractSerializer> во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="04888-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="04888-103">Элемент задает «известный тип», возвращаемый полем или свойством «объявленного типа».</span><span class="sxs-lookup"><span data-stu-id="04888-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="04888-104">Дополнительные сведения см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="04888-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="04888-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04888-105">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="04888-106">Тип</span><span class="sxs-lookup"><span data-stu-id="04888-106">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04888-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="04888-107">Attributes and Elements</span></span>  

 <span data-ttu-id="04888-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="04888-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04888-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="04888-109">Attributes</span></span>  
  
|<span data-ttu-id="04888-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="04888-110">Attribute</span></span>|<span data-ttu-id="04888-111">Описание</span><span class="sxs-lookup"><span data-stu-id="04888-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04888-112">type</span><span class="sxs-lookup"><span data-stu-id="04888-112">type</span></span>|<span data-ttu-id="04888-113">Задает тип (в том числе пространство имен), имя сборки, версию, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="04888-113">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04888-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="04888-114">Child Elements</span></span>  
  
|<span data-ttu-id="04888-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="04888-115">Element</span></span>|<span data-ttu-id="04888-116">Описание</span><span class="sxs-lookup"><span data-stu-id="04888-116">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="04888-117">Задает индекс параметра в том случае, если объявленный тип является универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="04888-117">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04888-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="04888-118">Parent Elements</span></span>  
  
|<span data-ttu-id="04888-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="04888-119">Element</span></span>|<span data-ttu-id="04888-120">Описание</span><span class="sxs-lookup"><span data-stu-id="04888-120">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="04888-121">Добавляет объявленный тип в коллекцию объявленных типов.</span><span class="sxs-lookup"><span data-stu-id="04888-121">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04888-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="04888-122">Remarks</span></span>  

 <span data-ttu-id="04888-123">Дополнительные сведения об известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md) и <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="04888-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="04888-124">[\<dataContractSerializer>](datacontractserializer-element.md)Пример использования этого элемента см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="04888-124">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04888-125">Пример</span><span class="sxs-lookup"><span data-stu-id="04888-125">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="04888-126">См. также</span><span class="sxs-lookup"><span data-stu-id="04888-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="04888-127">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="04888-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
