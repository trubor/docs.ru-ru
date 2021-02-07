---
description: 'Дополнительные сведения об <Parameter> элементе: Element (.NET Native)'
title: <Parameter> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 53b84027e8393e0a799d9652767d173c2787cd27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662797"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="dbc0f-103">\<Parameter> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="dbc0f-103">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="dbc0f-104">Применяет политику отражения к типу аргумента, переданного методу.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-104">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc0f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbc0f-105">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbc0f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="dbc0f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dbc0f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbc0f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="dbc0f-108">Attributes</span></span>  
  
|<span data-ttu-id="dbc0f-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dbc0f-109">Attribute</span></span>|<span data-ttu-id="dbc0f-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="dbc0f-110">Attribute type</span></span>|<span data-ttu-id="dbc0f-111">Описание</span><span class="sxs-lookup"><span data-stu-id="dbc0f-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="dbc0f-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="dbc0f-112">General</span></span>|<span data-ttu-id="dbc0f-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-113">Required attribute.</span></span> <span data-ttu-id="dbc0f-114">Имя параметра.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-114">The parameter name.</span></span> <span data-ttu-id="dbc0f-115">Например, сигнатура метода `String.CompareTo(Object value)`, значение `Name` — атрибут «value».</span><span class="sxs-lookup"><span data-stu-id="dbc0f-115">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="dbc0f-116">Отражение</span><span class="sxs-lookup"><span data-stu-id="dbc0f-116">Reflection</span></span>|<span data-ttu-id="dbc0f-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-117">Optional attribute.</span></span> <span data-ttu-id="dbc0f-118">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="dbc0f-119">Отражение</span><span class="sxs-lookup"><span data-stu-id="dbc0f-119">Reflection</span></span>|<span data-ttu-id="dbc0f-120">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-120">Optional attribute.</span></span> <span data-ttu-id="dbc0f-121">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="dbc0f-122">Отражение</span><span class="sxs-lookup"><span data-stu-id="dbc0f-122">Reflection</span></span>|<span data-ttu-id="dbc0f-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-123">Optional attribute.</span></span> <span data-ttu-id="dbc0f-124">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="dbc0f-125">Сериализация</span><span class="sxs-lookup"><span data-stu-id="dbc0f-125">Serialization</span></span>|<span data-ttu-id="dbc0f-126">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-126">Optional attribute.</span></span> <span data-ttu-id="dbc0f-127">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="dbc0f-128">Сериализация</span><span class="sxs-lookup"><span data-stu-id="dbc0f-128">Serialization</span></span>|<span data-ttu-id="dbc0f-129">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-129">Optional attribute.</span></span> <span data-ttu-id="dbc0f-130">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="dbc0f-131">Сериализация</span><span class="sxs-lookup"><span data-stu-id="dbc0f-131">Serialization</span></span>|<span data-ttu-id="dbc0f-132">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-132">Optional attribute.</span></span> <span data-ttu-id="dbc0f-133">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="dbc0f-134">Сериализация</span><span class="sxs-lookup"><span data-stu-id="dbc0f-134">Serialization</span></span>|<span data-ttu-id="dbc0f-135">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-135">Optional attribute.</span></span> <span data-ttu-id="dbc0f-136">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="dbc0f-137">Interop</span><span class="sxs-lookup"><span data-stu-id="dbc0f-137">Interop</span></span>|<span data-ttu-id="dbc0f-138">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-138">Optional attribute.</span></span> <span data-ttu-id="dbc0f-139">Определяет политику для маршалинга ссылочных типов в WinRT и COM.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-139">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="dbc0f-140">Interop</span><span class="sxs-lookup"><span data-stu-id="dbc0f-140">Interop</span></span>|<span data-ttu-id="dbc0f-141">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-141">Optional attribute.</span></span> <span data-ttu-id="dbc0f-142">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="dbc0f-143">Interop</span><span class="sxs-lookup"><span data-stu-id="dbc0f-143">Interop</span></span>|<span data-ttu-id="dbc0f-144">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-144">Optional attribute.</span></span> <span data-ttu-id="dbc0f-145">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="dbc0f-146">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="dbc0f-146">Name attribute</span></span>  
  
|<span data-ttu-id="dbc0f-147">Значение</span><span class="sxs-lookup"><span data-stu-id="dbc0f-147">Value</span></span>|<span data-ttu-id="dbc0f-148">Описание</span><span class="sxs-lookup"><span data-stu-id="dbc0f-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbc0f-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="dbc0f-149">*parameter_name*</span></span>|<span data-ttu-id="dbc0f-150">Имя параметра метода, к которому применяется политика.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-150">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="dbc0f-151">Например, сигнатура метода `String.CompareTo(Object value)`, значение `Name` — атрибут «value».</span><span class="sxs-lookup"><span data-stu-id="dbc0f-151">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="dbc0f-152">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="dbc0f-152">All other attributes</span></span>  
  
|<span data-ttu-id="dbc0f-153">Значение</span><span class="sxs-lookup"><span data-stu-id="dbc0f-153">Value</span></span>|<span data-ttu-id="dbc0f-154">Описание</span><span class="sxs-lookup"><span data-stu-id="dbc0f-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbc0f-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="dbc0f-155">*policy_setting*</span></span>|<span data-ttu-id="dbc0f-156">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="dbc0f-157">Допустимые значения: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="dbc0f-158">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="dbc0f-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbc0f-159">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="dbc0f-159">Child Elements</span></span>  

 <span data-ttu-id="dbc0f-160">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbc0f-161">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="dbc0f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="dbc0f-162">Элемент</span><span class="sxs-lookup"><span data-stu-id="dbc0f-162">Element</span></span>|<span data-ttu-id="dbc0f-163">Описание</span><span class="sxs-lookup"><span data-stu-id="dbc0f-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="dbc0f-164">Применяет политику отражения среды выполнения к конструктору или методу.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc0f-165">Remarks</span><span class="sxs-lookup"><span data-stu-id="dbc0f-165">Remarks</span></span>  

 <span data-ttu-id="dbc0f-166">`<Parameter>`Элемент является дочерним по отношению к [\<Method>](method-element-net-native.md) элементу и используется для применения политики к конкретному параметру метода.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="dbc0f-167">Конкретный параметр метода указывается по имени, а не по типу.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="dbc0f-168">По крайней мере один атрибут, который представляет тип политики, такие как `Activate` или `Dynamic`, должен присутствовать.</span><span class="sxs-lookup"><span data-stu-id="dbc0f-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc0f-169">См. также</span><span class="sxs-lookup"><span data-stu-id="dbc0f-169">See also</span></span>

- [<span data-ttu-id="dbc0f-170">\<Method> Элемент</span><span class="sxs-lookup"><span data-stu-id="dbc0f-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="dbc0f-171">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="dbc0f-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="dbc0f-172">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="dbc0f-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="dbc0f-173">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="dbc0f-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
