---
description: 'Дополнительные сведения об <ImpliesType> элементе: Element (.NET Native)'
title: <ImpliesType> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 6476876f335788a276907fd2aef02d5623382699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747690"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="62116-103">\<ImpliesType> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="62116-103">\<ImpliesType> Element (.NET Native)</span></span>

<span data-ttu-id="62116-104">Применяет политику к типу, если политика была применена к содержащему типу или методу.</span><span class="sxs-lookup"><span data-stu-id="62116-104">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62116-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62116-105">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62116-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="62116-106">Attributes and Elements</span></span>  

 <span data-ttu-id="62116-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="62116-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62116-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="62116-108">Attributes</span></span>  
  
|<span data-ttu-id="62116-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="62116-109">Attribute</span></span>|<span data-ttu-id="62116-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="62116-110">Attribute type</span></span>|<span data-ttu-id="62116-111">Описание</span><span class="sxs-lookup"><span data-stu-id="62116-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="62116-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="62116-112">General</span></span>|<span data-ttu-id="62116-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-113">Required attribute.</span></span> <span data-ttu-id="62116-114">Указывает имя типа.</span><span class="sxs-lookup"><span data-stu-id="62116-114">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="62116-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="62116-115">Reflection</span></span>|<span data-ttu-id="62116-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-116">Optional attribute.</span></span> <span data-ttu-id="62116-117">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="62116-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="62116-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="62116-118">Reflection</span></span>|<span data-ttu-id="62116-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-119">Optional attribute.</span></span> <span data-ttu-id="62116-120">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="62116-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="62116-121">Отражение</span><span class="sxs-lookup"><span data-stu-id="62116-121">Reflection</span></span>|<span data-ttu-id="62116-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-122">Optional attribute.</span></span> <span data-ttu-id="62116-123">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="62116-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="62116-124">Сериализация</span><span class="sxs-lookup"><span data-stu-id="62116-124">Serialization</span></span>|<span data-ttu-id="62116-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-125">Optional attribute.</span></span> <span data-ttu-id="62116-126">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="62116-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="62116-127">Сериализация</span><span class="sxs-lookup"><span data-stu-id="62116-127">Serialization</span></span>|<span data-ttu-id="62116-128">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-128">Optional attribute.</span></span> <span data-ttu-id="62116-129">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62116-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="62116-130">Сериализация</span><span class="sxs-lookup"><span data-stu-id="62116-130">Serialization</span></span>|<span data-ttu-id="62116-131">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-131">Optional attribute.</span></span> <span data-ttu-id="62116-132">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62116-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="62116-133">Сериализация</span><span class="sxs-lookup"><span data-stu-id="62116-133">Serialization</span></span>|<span data-ttu-id="62116-134">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-134">Optional attribute.</span></span> <span data-ttu-id="62116-135">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62116-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="62116-136">Interop</span><span class="sxs-lookup"><span data-stu-id="62116-136">Interop</span></span>|<span data-ttu-id="62116-137">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-137">Optional attribute.</span></span> <span data-ttu-id="62116-138">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="62116-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="62116-139">Interop</span><span class="sxs-lookup"><span data-stu-id="62116-139">Interop</span></span>|<span data-ttu-id="62116-140">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-140">Optional attribute.</span></span> <span data-ttu-id="62116-141">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="62116-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="62116-142">Interop</span><span class="sxs-lookup"><span data-stu-id="62116-142">Interop</span></span>|<span data-ttu-id="62116-143">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="62116-143">Optional attribute.</span></span> <span data-ttu-id="62116-144">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="62116-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="62116-145">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="62116-145">Name attribute</span></span>  
  
|<span data-ttu-id="62116-146">Значение</span><span class="sxs-lookup"><span data-stu-id="62116-146">Value</span></span>|<span data-ttu-id="62116-147">Описание</span><span class="sxs-lookup"><span data-stu-id="62116-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62116-148">*type_name*</span><span class="sxs-lookup"><span data-stu-id="62116-148">*type_name*</span></span>|<span data-ttu-id="62116-149">Имя типа.</span><span class="sxs-lookup"><span data-stu-id="62116-149">The type name.</span></span> <span data-ttu-id="62116-150">Если тип, представленный этим элементом `<ImpliesType>`, находится в том же пространстве имен, что и содержащий его элемент `<Type>`, атрибут *type_name* может содержать имя типа без пространства имен.</span><span class="sxs-lookup"><span data-stu-id="62116-150">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="62116-151">В противном случае атрибут *type_name* должен содержать полное имя типа.</span><span class="sxs-lookup"><span data-stu-id="62116-151">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="62116-152">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="62116-152">All other attributes</span></span>  
  
|<span data-ttu-id="62116-153">Значение</span><span class="sxs-lookup"><span data-stu-id="62116-153">Value</span></span>|<span data-ttu-id="62116-154">Описание</span><span class="sxs-lookup"><span data-stu-id="62116-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62116-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="62116-155">*policy_setting*</span></span>|<span data-ttu-id="62116-156">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="62116-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="62116-157">Допустимые значения `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="62116-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="62116-158">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="62116-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62116-159">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="62116-159">Child Elements</span></span>  

 <span data-ttu-id="62116-160">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="62116-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62116-161">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="62116-161">Parent Elements</span></span>  
  
|<span data-ttu-id="62116-162">Элемент</span><span class="sxs-lookup"><span data-stu-id="62116-162">Element</span></span>|<span data-ttu-id="62116-163">Описание</span><span class="sxs-lookup"><span data-stu-id="62116-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="62116-164">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="62116-164">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="62116-165">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="62116-165">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="62116-166">Применяет политику отражения к методу.</span><span class="sxs-lookup"><span data-stu-id="62116-166">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62116-167">Remarks</span><span class="sxs-lookup"><span data-stu-id="62116-167">Remarks</span></span>  

 <span data-ttu-id="62116-168">Элемент `<ImpliesType>` в основном предназначен для использования в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="62116-168">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="62116-169">Он используется в следующем сценарии:</span><span class="sxs-lookup"><span data-stu-id="62116-169">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="62116-170">Если процедура должна отражаться на одном типе, она обязательно должна отражаться на втором типе</span><span class="sxs-lookup"><span data-stu-id="62116-170">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="62116-171">В противном случае метаданные для корректной реализации второго типа недоступны, так как статический анализ не указывает, что это необходимо.</span><span class="sxs-lookup"><span data-stu-id="62116-171">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="62116-172">Чаще всего двумя типами являются универсальные экземпляры общих аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="62116-172">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="62116-173">Элемент `<ImpliesType>` был определен исходя из предположения, что необходимость отражения в тип, заданный родительским элементом, предполагает необходимость отражения в тип, заданный элементом `<ImpliesType>`.</span><span class="sxs-lookup"><span data-stu-id="62116-173">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="62116-174">Например, для двух типов применяются следующие директивы отражения `Explicit<T>` и `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="62116-174">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="62116-175">Эта директива не действует, пока экземпляр `Explicit` не определил параметр политики `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="62116-175">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="62116-176">Например, если это так, для `Explicit<Int32>`, `Implicit<Int32>` создается экземпляр с открытыми корневыми членами, а их метаданные становятся доступными для динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="62116-176">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="62116-177">Ниже приведен реальный пример, который применяется по крайней мере к одному сериализатору.</span><span class="sxs-lookup"><span data-stu-id="62116-177">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="62116-178">Директивы захватывают требование, отражающее что-либо, что, как и то и другое, `IList<`  `>` включает отражение для соответствующего `List<`  `>` типа, не требуя каких-либо заметок для каждого приложения.</span><span class="sxs-lookup"><span data-stu-id="62116-178">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="62116-179">Элемент `<ImpliesType>` может также отображаться в элементе `<Method>`, так как в некоторых случаях создание экземпляров универсального метода подразумевает отражение на экземпляре типа.</span><span class="sxs-lookup"><span data-stu-id="62116-179">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="62116-180">Например, представьте универсальный метод `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)`, к которому заданная библиотека будет обращаться динамически вместе со связанными типами <xref:System.Collections.Generic.List%601> и <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="62116-180">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="62116-181">Это можно выразить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="62116-181">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62116-182">См. также</span><span class="sxs-lookup"><span data-stu-id="62116-182">See also</span></span>

- [<span data-ttu-id="62116-183">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="62116-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="62116-184">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="62116-184">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="62116-185">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="62116-185">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
