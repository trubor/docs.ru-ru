---
description: 'Дополнительные сведения об <TypeParameter> элементе: Element (.NET Native)'
title: <TypeParameter> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: 182cd62dc0584991b8ef0f5757d6005173d6d7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803650"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="7f1a7-103">\<TypeParameter> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7f1a7-103">\<TypeParameter> Element (.NET Native)</span></span>

<span data-ttu-id="7f1a7-104">Применяет политику к типу, представленному аргументом типа , переданным методу.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-104">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1a7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f1a7-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f1a7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7f1a7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f1a7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f1a7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7f1a7-108">Attributes</span></span>  
  
|<span data-ttu-id="7f1a7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7f1a7-109">Attribute</span></span>|<span data-ttu-id="7f1a7-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="7f1a7-110">Attribute type</span></span>|<span data-ttu-id="7f1a7-111">Описание</span><span class="sxs-lookup"><span data-stu-id="7f1a7-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7f1a7-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="7f1a7-112">General</span></span>|<span data-ttu-id="7f1a7-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-113">Required attribute.</span></span> <span data-ttu-id="7f1a7-114">Имя типа параметра типа <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-114">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="7f1a7-115">Например, для сигнатуры метода `Type.GetInterfaceMap(Type interfaceType)`, значение атрибута `Name` — "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="7f1a7-115">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="7f1a7-116">Отражение</span><span class="sxs-lookup"><span data-stu-id="7f1a7-116">Reflection</span></span>|<span data-ttu-id="7f1a7-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-117">Optional attribute.</span></span> <span data-ttu-id="7f1a7-118">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7f1a7-119">Отражение</span><span class="sxs-lookup"><span data-stu-id="7f1a7-119">Reflection</span></span>|<span data-ttu-id="7f1a7-120">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-120">Optional attribute.</span></span> <span data-ttu-id="7f1a7-121">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7f1a7-122">Отражение</span><span class="sxs-lookup"><span data-stu-id="7f1a7-122">Reflection</span></span>|<span data-ttu-id="7f1a7-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-123">Optional attribute.</span></span> <span data-ttu-id="7f1a7-124">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7f1a7-125">Сериализация</span><span class="sxs-lookup"><span data-stu-id="7f1a7-125">Serialization</span></span>|<span data-ttu-id="7f1a7-126">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-126">Optional attribute.</span></span> <span data-ttu-id="7f1a7-127">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7f1a7-128">Сериализация</span><span class="sxs-lookup"><span data-stu-id="7f1a7-128">Serialization</span></span>|<span data-ttu-id="7f1a7-129">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-129">Optional attribute.</span></span> <span data-ttu-id="7f1a7-130">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7f1a7-131">Сериализация</span><span class="sxs-lookup"><span data-stu-id="7f1a7-131">Serialization</span></span>|<span data-ttu-id="7f1a7-132">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-132">Optional attribute.</span></span> <span data-ttu-id="7f1a7-133">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7f1a7-134">Сериализация</span><span class="sxs-lookup"><span data-stu-id="7f1a7-134">Serialization</span></span>|<span data-ttu-id="7f1a7-135">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-135">Optional attribute.</span></span> <span data-ttu-id="7f1a7-136">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7f1a7-137">Interop</span><span class="sxs-lookup"><span data-stu-id="7f1a7-137">Interop</span></span>|<span data-ttu-id="7f1a7-138">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-138">Optional attribute.</span></span> <span data-ttu-id="7f1a7-139">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7f1a7-140">Interop</span><span class="sxs-lookup"><span data-stu-id="7f1a7-140">Interop</span></span>|<span data-ttu-id="7f1a7-141">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-141">Optional attribute.</span></span> <span data-ttu-id="7f1a7-142">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7f1a7-143">Interop</span><span class="sxs-lookup"><span data-stu-id="7f1a7-143">Interop</span></span>|<span data-ttu-id="7f1a7-144">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-144">Optional attribute.</span></span> <span data-ttu-id="7f1a7-145">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7f1a7-146">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="7f1a7-146">Name attribute</span></span>  
  
|<span data-ttu-id="7f1a7-147">Значение</span><span class="sxs-lookup"><span data-stu-id="7f1a7-147">Value</span></span>|<span data-ttu-id="7f1a7-148">Описание</span><span class="sxs-lookup"><span data-stu-id="7f1a7-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f1a7-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="7f1a7-149">*parameter_name*</span></span>|<span data-ttu-id="7f1a7-150">Имя типа параметра типа <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-150">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="7f1a7-151">Например, для сигнатуры метода `Type.GetInterfaceMap(Type interfaceType)`, значение атрибута `Name` — "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="7f1a7-151">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7f1a7-152">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="7f1a7-152">All other attributes</span></span>  
  
|<span data-ttu-id="7f1a7-153">Значение</span><span class="sxs-lookup"><span data-stu-id="7f1a7-153">Value</span></span>|<span data-ttu-id="7f1a7-154">Описание</span><span class="sxs-lookup"><span data-stu-id="7f1a7-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f1a7-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7f1a7-155">*policy_setting*</span></span>|<span data-ttu-id="7f1a7-156">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="7f1a7-157">Допустимые значения: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7f1a7-158">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7f1a7-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f1a7-159">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7f1a7-159">Child Elements</span></span>  

 <span data-ttu-id="7f1a7-160">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f1a7-161">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7f1a7-161">Parent Elements</span></span>  
  
|<span data-ttu-id="7f1a7-162">Элемент</span><span class="sxs-lookup"><span data-stu-id="7f1a7-162">Element</span></span>|<span data-ttu-id="7f1a7-163">Описание</span><span class="sxs-lookup"><span data-stu-id="7f1a7-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="7f1a7-164">Применяет политику отражения среды выполнения к конструктору или методу.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f1a7-165">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f1a7-165">Remarks</span></span>  

 <span data-ttu-id="7f1a7-166">`<TypeParameter>`Элемент аналогичен [\<Parameter>](parameter-element-net-native.md) элементу, за исключением того, что он может применяться только к параметрам типа <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="7f1a7-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="7f1a7-167">Применяет политику, независимо от представленного типа во время выполнения по аргументу типа, указанному атрибутом `Name`.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="7f1a7-168">Например, сериализатор NewtonSoft JSON включает статический метод `JsonConvert.DeserializeObject(String value, Type type)`.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="7f1a7-169">Следующие директивы отражения:</span><span class="sxs-lookup"><span data-stu-id="7f1a7-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="7f1a7-170">определяют, что метаданные для типа среды выполнения, представленные аргументом `type`, должны быть доступны для сериализации.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="7f1a7-171">Если применить эти директивы среды выполнения к проекту, который включает следующий исходный код:</span><span class="sxs-lookup"><span data-stu-id="7f1a7-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="7f1a7-172">директивы отражения делают метаданные для типа `StockQuote` доступными для сериализатора NewtonSoft JSON во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="7f1a7-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1a7-173">См. также</span><span class="sxs-lookup"><span data-stu-id="7f1a7-173">See also</span></span>

- [<span data-ttu-id="7f1a7-174">\<Method> Элемент</span><span class="sxs-lookup"><span data-stu-id="7f1a7-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="7f1a7-175">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7f1a7-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7f1a7-176">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="7f1a7-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="7f1a7-177">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="7f1a7-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
