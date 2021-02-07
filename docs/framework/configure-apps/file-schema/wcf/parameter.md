---
description: 'Дополнительные сведения: <parameter>'
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: fb04cfb5bf451cdb99c23ae41ea8fafeb13f0d11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683818"
---
# \<parameter>

<span data-ttu-id="b137c-102">Указывает общий параметр, если объявленный тип является общим типом.</span><span class="sxs-lookup"><span data-stu-id="b137c-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="b137c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b137c-103">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b137c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b137c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b137c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b137c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b137c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b137c-106">Attributes</span></span>  
  
|<span data-ttu-id="b137c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b137c-107">Attribute</span></span>|<span data-ttu-id="b137c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b137c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b137c-109">index</span><span class="sxs-lookup"><span data-stu-id="b137c-109">index</span></span>|<span data-ttu-id="b137c-110">Если объявленный тип является общим типом, указывает общий параметр, который возвращает известный тип.</span><span class="sxs-lookup"><span data-stu-id="b137c-110">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="b137c-111">тип</span><span class="sxs-lookup"><span data-stu-id="b137c-111">type</span></span>|<span data-ttu-id="b137c-112">Строка, которая описывает известный тип, используемый для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="b137c-112">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="b137c-113">Атрибут index</span><span class="sxs-lookup"><span data-stu-id="b137c-113">index Attribute</span></span>  
  
|<span data-ttu-id="b137c-114">Значение</span><span class="sxs-lookup"><span data-stu-id="b137c-114">Value</span></span>|<span data-ttu-id="b137c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b137c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b137c-116">"0"</span><span class="sxs-lookup"><span data-stu-id="b137c-116">"0"</span></span>|<span data-ttu-id="b137c-117">Первый параметр в общем типе.</span><span class="sxs-lookup"><span data-stu-id="b137c-117">The first parameter in the generic type.</span></span> <span data-ttu-id="b137c-118">Например, у <xref:System.Collections.Generic.List%601> есть только один параметр.</span><span class="sxs-lookup"><span data-stu-id="b137c-118">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="b137c-119">Если он используется как объявленный тип, индексу присваивается значение 0.</span><span class="sxs-lookup"><span data-stu-id="b137c-119">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="b137c-120">"1"</span><span class="sxs-lookup"><span data-stu-id="b137c-120">"1"</span></span>|<span data-ttu-id="b137c-121">Второй параметр в общем типе.</span><span class="sxs-lookup"><span data-stu-id="b137c-121">The second parameter in a generic type.</span></span> <span data-ttu-id="b137c-122">Например, у <xref:System.Collections.Generic.Dictionary%602> есть два параметра.</span><span class="sxs-lookup"><span data-stu-id="b137c-122">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="b137c-123">Если известный тип возвращается вторым параметром, атрибуту index присваивается значение 1.</span><span class="sxs-lookup"><span data-stu-id="b137c-123">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b137c-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b137c-124">Child Elements</span></span>  

 <span data-ttu-id="b137c-125">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b137c-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b137c-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b137c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b137c-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="b137c-127">Element</span></span>|<span data-ttu-id="b137c-128">Описание</span><span class="sxs-lookup"><span data-stu-id="b137c-128">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="b137c-129">Указывает известный тип, который может возвращаться полем или свойством объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="b137c-129">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b137c-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="b137c-130">Remarks</span></span>  

 <span data-ttu-id="b137c-131">Дополнительные сведения об известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md) и <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b137c-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b137c-132">[\<dataContractSerializer>](datacontractserializer-element.md)Пример использования этого элемента см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="b137c-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="b137c-133">У данного элемента конфигурации не может одновременно быть оба атрибута.</span><span class="sxs-lookup"><span data-stu-id="b137c-133">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="b137c-134">Если заданы оба атрибута, возникает исключение <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="b137c-134">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b137c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="b137c-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="b137c-136">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="b137c-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
