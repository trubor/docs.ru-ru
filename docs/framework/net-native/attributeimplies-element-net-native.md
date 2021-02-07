---
description: 'Дополнительные сведения об <AttributeImplies> элементе: Element (.NET Native)'
title: <AttributeImplies> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 5af1f60f2c1e556281f2f1d392b1a046e52dd277
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747911"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="71d3e-103">\<AttributeImplies> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="71d3e-103">\<AttributeImplies> Element (.NET Native)</span></span>

<span data-ttu-id="71d3e-104">Определяет политики для элементов кода, к которым применяется содержащий атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-104">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d3e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71d3e-105">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71d3e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="71d3e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="71d3e-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="71d3e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71d3e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="71d3e-108">Attributes</span></span>  
  
|<span data-ttu-id="71d3e-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="71d3e-109">Attribute</span></span>|<span data-ttu-id="71d3e-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="71d3e-110">Attribute type</span></span>|<span data-ttu-id="71d3e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="71d3e-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="71d3e-112">Отражение</span><span class="sxs-lookup"><span data-stu-id="71d3e-112">Reflection</span></span>|<span data-ttu-id="71d3e-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-113">Optional attribute.</span></span> <span data-ttu-id="71d3e-114">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="71d3e-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="71d3e-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="71d3e-115">Reflection</span></span>|<span data-ttu-id="71d3e-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-116">Optional attribute.</span></span> <span data-ttu-id="71d3e-117">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="71d3e-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="71d3e-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="71d3e-118">Reflection</span></span>|<span data-ttu-id="71d3e-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-119">Optional attribute.</span></span> <span data-ttu-id="71d3e-120">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="71d3e-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="71d3e-121">Сериализация</span><span class="sxs-lookup"><span data-stu-id="71d3e-121">Serialization</span></span>|<span data-ttu-id="71d3e-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-122">Optional attribute.</span></span> <span data-ttu-id="71d3e-123">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="71d3e-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="71d3e-124">Сериализация</span><span class="sxs-lookup"><span data-stu-id="71d3e-124">Serialization</span></span>|<span data-ttu-id="71d3e-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-125">Optional attribute.</span></span> <span data-ttu-id="71d3e-126">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="71d3e-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="71d3e-127">Сериализация</span><span class="sxs-lookup"><span data-stu-id="71d3e-127">Serialization</span></span>|<span data-ttu-id="71d3e-128">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-128">Optional attribute.</span></span> <span data-ttu-id="71d3e-129">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="71d3e-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="71d3e-130">Сериализация</span><span class="sxs-lookup"><span data-stu-id="71d3e-130">Serialization</span></span>|<span data-ttu-id="71d3e-131">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-131">Optional attribute.</span></span> <span data-ttu-id="71d3e-132">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="71d3e-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="71d3e-133">Interop</span><span class="sxs-lookup"><span data-stu-id="71d3e-133">Interop</span></span>|<span data-ttu-id="71d3e-134">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-134">Optional attribute.</span></span> <span data-ttu-id="71d3e-135">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="71d3e-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="71d3e-136">Interop</span><span class="sxs-lookup"><span data-stu-id="71d3e-136">Interop</span></span>|<span data-ttu-id="71d3e-137">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-137">Optional attribute.</span></span> <span data-ttu-id="71d3e-138">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="71d3e-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="71d3e-139">Interop</span><span class="sxs-lookup"><span data-stu-id="71d3e-139">Interop</span></span>|<span data-ttu-id="71d3e-140">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="71d3e-140">Optional attribute.</span></span> <span data-ttu-id="71d3e-141">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="71d3e-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="71d3e-142">Все атрибуты</span><span class="sxs-lookup"><span data-stu-id="71d3e-142">All attributes</span></span>  
  
|<span data-ttu-id="71d3e-143">Значение</span><span class="sxs-lookup"><span data-stu-id="71d3e-143">Value</span></span>|<span data-ttu-id="71d3e-144">Описание</span><span class="sxs-lookup"><span data-stu-id="71d3e-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71d3e-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="71d3e-145">*policy_setting*</span></span>|<span data-ttu-id="71d3e-146">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="71d3e-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="71d3e-147">Допустимые значения `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="71d3e-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="71d3e-148">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="71d3e-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71d3e-149">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="71d3e-149">Child Elements</span></span>  

 <span data-ttu-id="71d3e-150">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="71d3e-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71d3e-151">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="71d3e-151">Parent Elements</span></span>  
  
|<span data-ttu-id="71d3e-152">Элемент</span><span class="sxs-lookup"><span data-stu-id="71d3e-152">Element</span></span>|<span data-ttu-id="71d3e-153">Описание</span><span class="sxs-lookup"><span data-stu-id="71d3e-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="71d3e-154">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="71d3e-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d3e-155">Remarks</span><span class="sxs-lookup"><span data-stu-id="71d3e-155">Remarks</span></span>  

 <span data-ttu-id="71d3e-156">Элемент `<AttributeImplies>` используется в том случае, если его содержащий тип является атрибутом (то есть классом, производным от <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="71d3e-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="71d3e-157">Если атрибут применяется к элементу определенной программы, политика, определенная элементом `<AttributeImplies>`, применяется к этому элементу программы.</span><span class="sxs-lookup"><span data-stu-id="71d3e-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="71d3e-158">Атрибуты отражения, сериализации и взаимодействия необязательны, несмотря на то, что по крайней мере один из них должен присутствовать.</span><span class="sxs-lookup"><span data-stu-id="71d3e-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d3e-159">См. также</span><span class="sxs-lookup"><span data-stu-id="71d3e-159">See also</span></span>

- [<span data-ttu-id="71d3e-160">\<Type> Элемент</span><span class="sxs-lookup"><span data-stu-id="71d3e-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="71d3e-161">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="71d3e-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="71d3e-162">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="71d3e-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="71d3e-163">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="71d3e-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
