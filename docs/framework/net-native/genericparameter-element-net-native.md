---
description: 'Дополнительные сведения об <GenericParameter> элементе: Element (.NET Native)'
title: <GenericParameter> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: 57cbb3418289d7da4f25577188299acd55ce6c94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747833"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="de151-103">\<GenericParameter> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="de151-103">\<GenericParameter> Element (.NET Native)</span></span>

<span data-ttu-id="de151-104">Применяет политику к параметру типа универсального типа или метода.</span><span class="sxs-lookup"><span data-stu-id="de151-104">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de151-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de151-105">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de151-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="de151-106">Attributes and Elements</span></span>  

 <span data-ttu-id="de151-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="de151-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de151-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="de151-108">Attributes</span></span>  
  
|<span data-ttu-id="de151-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="de151-109">Attribute</span></span>|<span data-ttu-id="de151-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="de151-110">Attribute type</span></span>|<span data-ttu-id="de151-111">Описание</span><span class="sxs-lookup"><span data-stu-id="de151-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="de151-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="de151-112">General</span></span>|<span data-ttu-id="de151-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-113">Required attribute.</span></span> <span data-ttu-id="de151-114">Имя универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="de151-114">The name of the generic parameter.</span></span> <span data-ttu-id="de151-115">Например, для универсального делегата <xref:System.Func%603>, значение атрибута `Name` равно «TResult» для применения политики среды выполнения к возвращаемому значению делегата.</span><span class="sxs-lookup"><span data-stu-id="de151-115">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="de151-116">Отражение</span><span class="sxs-lookup"><span data-stu-id="de151-116">Reflection</span></span>|<span data-ttu-id="de151-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-117">Optional attribute.</span></span> <span data-ttu-id="de151-118">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="de151-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="de151-119">Отражение</span><span class="sxs-lookup"><span data-stu-id="de151-119">Reflection</span></span>|<span data-ttu-id="de151-120">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-120">Optional attribute.</span></span> <span data-ttu-id="de151-121">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="de151-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="de151-122">Отражение</span><span class="sxs-lookup"><span data-stu-id="de151-122">Reflection</span></span>|<span data-ttu-id="de151-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-123">Optional attribute.</span></span> <span data-ttu-id="de151-124">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="de151-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="de151-125">Сериализация</span><span class="sxs-lookup"><span data-stu-id="de151-125">Serialization</span></span>|<span data-ttu-id="de151-126">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-126">Optional attribute.</span></span> <span data-ttu-id="de151-127">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="de151-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="de151-128">Сериализация</span><span class="sxs-lookup"><span data-stu-id="de151-128">Serialization</span></span>|<span data-ttu-id="de151-129">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-129">Optional attribute.</span></span> <span data-ttu-id="de151-130">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de151-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="de151-131">Сериализация</span><span class="sxs-lookup"><span data-stu-id="de151-131">Serialization</span></span>|<span data-ttu-id="de151-132">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-132">Optional attribute.</span></span> <span data-ttu-id="de151-133">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de151-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="de151-134">Сериализация</span><span class="sxs-lookup"><span data-stu-id="de151-134">Serialization</span></span>|<span data-ttu-id="de151-135">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-135">Optional attribute.</span></span> <span data-ttu-id="de151-136">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de151-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="de151-137">Interop</span><span class="sxs-lookup"><span data-stu-id="de151-137">Interop</span></span>|<span data-ttu-id="de151-138">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-138">Optional attribute.</span></span> <span data-ttu-id="de151-139">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="de151-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="de151-140">Interop</span><span class="sxs-lookup"><span data-stu-id="de151-140">Interop</span></span>|<span data-ttu-id="de151-141">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-141">Optional attribute.</span></span> <span data-ttu-id="de151-142">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="de151-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="de151-143">Interop</span><span class="sxs-lookup"><span data-stu-id="de151-143">Interop</span></span>|<span data-ttu-id="de151-144">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-144">Optional attribute.</span></span> <span data-ttu-id="de151-145">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="de151-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="de151-146">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="de151-146">Name attribute</span></span>  
  
|<span data-ttu-id="de151-147">Значение</span><span class="sxs-lookup"><span data-stu-id="de151-147">Value</span></span>|<span data-ttu-id="de151-148">Описание</span><span class="sxs-lookup"><span data-stu-id="de151-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de151-149">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="de151-149">*generic_parameter_name*</span></span>|<span data-ttu-id="de151-150">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="de151-150">Required attribute.</span></span> <span data-ttu-id="de151-151">Имя универсального параметра типа.</span><span class="sxs-lookup"><span data-stu-id="de151-151">The name of the generic type parameter.</span></span> <span data-ttu-id="de151-152">Например, для универсального делегата <xref:System.Func%603> значение *generic_parameter_name*, равное "TResult", применяет политику среды выполнения к возвращаемому значению делегата.</span><span class="sxs-lookup"><span data-stu-id="de151-152">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="de151-153">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="de151-153">All other attributes</span></span>  
  
|<span data-ttu-id="de151-154">Значение</span><span class="sxs-lookup"><span data-stu-id="de151-154">Value</span></span>|<span data-ttu-id="de151-155">Описание</span><span class="sxs-lookup"><span data-stu-id="de151-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de151-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="de151-156">*policy_setting*</span></span>|<span data-ttu-id="de151-157">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="de151-157">The setting to apply to this policy type.</span></span> <span data-ttu-id="de151-158">Допустимые значения: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="de151-158">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="de151-159">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="de151-159">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de151-160">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="de151-160">Child Elements</span></span>  

 <span data-ttu-id="de151-161">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="de151-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de151-162">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="de151-162">Parent Elements</span></span>  
  
|<span data-ttu-id="de151-163">Элемент</span><span class="sxs-lookup"><span data-stu-id="de151-163">Element</span></span>|<span data-ttu-id="de151-164">Описание</span><span class="sxs-lookup"><span data-stu-id="de151-164">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="de151-165">Применяет политику отражения среды выполнения к конструктору или методу.</span><span class="sxs-lookup"><span data-stu-id="de151-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="de151-166">Применяет политику отражения среды выполнения для конкретного типа, например, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="de151-166">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de151-167">Remarks</span><span class="sxs-lookup"><span data-stu-id="de151-167">Remarks</span></span>  

 <span data-ttu-id="de151-168">`<GenericParameter>`Элемент является дочерним по отношению к [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) элементу или и используется для применения политики к конкретному параметру универсального типа, который задается его именем в сигнатуре универсального типа или метода.</span><span class="sxs-lookup"><span data-stu-id="de151-168">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="de151-169">Элемент `<GenericParameter>` особенно полезен при использовании сериализаторов.</span><span class="sxs-lookup"><span data-stu-id="de151-169">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="de151-170">В следующем примере элемент используется `<GenericParameter>` для применения политики к типу `T` при вызове перегрузок метода JsonConvert. методов DeserializeObject сериализатора JSON NewtonSoft [ \<T> (String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) .</span><span class="sxs-lookup"><span data-stu-id="de151-170">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de151-171">См. также</span><span class="sxs-lookup"><span data-stu-id="de151-171">See also</span></span>

- [<span data-ttu-id="de151-172">\<Method> Элемент</span><span class="sxs-lookup"><span data-stu-id="de151-172">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="de151-173">\<Type> Элемент</span><span class="sxs-lookup"><span data-stu-id="de151-173">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="de151-174">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="de151-174">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="de151-175">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="de151-175">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="de151-176">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="de151-176">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
