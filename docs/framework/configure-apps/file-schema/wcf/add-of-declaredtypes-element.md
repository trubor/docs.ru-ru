---
description: 'Дополнительные сведения о: <add> <declaredTypes> element'
title: <add> элемента <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 8e2be6e553ee5dc5c96bcae81d1c1c6bf609afed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803988"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="b4f46-103">\<add> элемента \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="b4f46-103">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="b4f46-104">Добавляет тип, используемый <xref:System.Runtime.Serialization.DataContractSerializer> во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="b4f46-104">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="b4f46-105">В каждый объявленный тип включены известные типы, которые будут возвращены как поле или свойство объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="b4f46-105">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b4f46-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4f46-106">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4f46-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b4f46-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b4f46-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b4f46-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4f46-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b4f46-109">Attributes</span></span>  
  
|<span data-ttu-id="b4f46-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b4f46-110">Attribute</span></span>|<span data-ttu-id="b4f46-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b4f46-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4f46-112">type</span><span class="sxs-lookup"><span data-stu-id="b4f46-112">type</span></span>|<span data-ttu-id="b4f46-113">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="b4f46-113">Required string attribute.</span></span><br /><br /> <span data-ttu-id="b4f46-114">Задает имя типа (в том числе пространство имен), имя сборки, номер версии, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="b4f46-114">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4f46-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b4f46-115">Child Elements</span></span>  
  
|<span data-ttu-id="b4f46-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4f46-116">Element</span></span>|<span data-ttu-id="b4f46-117">Описание</span><span class="sxs-lookup"><span data-stu-id="b4f46-117">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="b4f46-118">Задает известный тип для добавляемого объявленного типа.</span><span class="sxs-lookup"><span data-stu-id="b4f46-118">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="b4f46-119">Если объявленный тип является универсальным типом, необходимо также добавить элемент параметра к элементу `<knownType>`, чтобы указать, какой универсальный параметр будет использоваться для возвращения известного типа.</span><span class="sxs-lookup"><span data-stu-id="b4f46-119">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4f46-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b4f46-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4f46-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4f46-121">Element</span></span>|<span data-ttu-id="b4f46-122">Описание</span><span class="sxs-lookup"><span data-stu-id="b4f46-122">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="b4f46-123">Содержит типы, для которых необходимы известные типы во время десериализации с помощью <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b4f46-123">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4f46-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4f46-124">Remarks</span></span>  

 <span data-ttu-id="b4f46-125">Дополнительные сведения об известных типах см. в статье о [известных типах контрактов данных](../../../wcf/feature-details/data-contract-known-types.md) и <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b4f46-125">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b4f46-126">[\<dataContractSerializer>](datacontractserializer-element.md)Пример использования этого элемента см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="b4f46-126">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4f46-127">При добавлении типа <xref:System.Object> как `<declaredType>` возникает <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="b4f46-127">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="b4f46-128">Это обусловлено тем, что тип <xref:System.Object> нельзя использовать как объявленный тип в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b4f46-128">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f46-129">Пример</span><span class="sxs-lookup"><span data-stu-id="b4f46-129">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="b4f46-130">См. также</span><span class="sxs-lookup"><span data-stu-id="b4f46-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="b4f46-131">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="b4f46-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="b4f46-132">\<add> из \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="b4f46-132">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
