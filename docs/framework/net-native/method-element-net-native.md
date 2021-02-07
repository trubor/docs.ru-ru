---
description: 'Дополнительные сведения об <Method> элементе: Element (.NET Native)'
title: <Method> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 76c379ed81e721316e4293b20ba89acfbc9d174f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747529"
---
# <a name="method-element-net-native"></a><span data-ttu-id="0d813-103">\<Method> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0d813-103">\<Method> Element (.NET Native)</span></span>

<span data-ttu-id="0d813-104">Применяет политику отражения среды выполнения к конструктору или методу.</span><span class="sxs-lookup"><span data-stu-id="0d813-104">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d813-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d813-105">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d813-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0d813-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0d813-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0d813-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d813-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0d813-108">Attributes</span></span>  
  
|<span data-ttu-id="0d813-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0d813-109">Attribute</span></span>|<span data-ttu-id="0d813-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="0d813-110">Attribute type</span></span>|<span data-ttu-id="0d813-111">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0d813-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0d813-112">General</span></span>|<span data-ttu-id="0d813-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0d813-113">Required attribute.</span></span> <span data-ttu-id="0d813-114">Задает имя метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-114">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="0d813-115">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0d813-115">General</span></span>|<span data-ttu-id="0d813-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0d813-116">Optional attribute.</span></span> <span data-ttu-id="0d813-117">Задает подпись метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-117">Specifies the method signature.</span></span> <span data-ttu-id="0d813-118">При наличии нескольких параметров, они разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0d813-118">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="0d813-119">Например, следующий элемент `<Method>` определяет политику для метода <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.</span><span class="sxs-lookup"><span data-stu-id="0d813-119">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="0d813-120">Если атрибут отсутствует, директива среды выполнения применяется для всех перегруженных версий метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-120">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="0d813-121">Отражение</span><span class="sxs-lookup"><span data-stu-id="0d813-121">Reflection</span></span>|<span data-ttu-id="0d813-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0d813-122">Optional attribute.</span></span> <span data-ttu-id="0d813-123">Определяет запрос для получения сведений о методе или перечисляет методы, но не включает динамический вызов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d813-123">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0d813-124">Отражение</span><span class="sxs-lookup"><span data-stu-id="0d813-124">Reflection</span></span>|<span data-ttu-id="0d813-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0d813-125">Optional attribute.</span></span> <span data-ttu-id="0d813-126">Управляет доступом среды выполнения к конструктору или методу для включения динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="0d813-126">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="0d813-127">Эта политика гарантирует, что член может быть вызван динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d813-127">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0d813-128">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="0d813-128">Name attribute</span></span>  
  
|<span data-ttu-id="0d813-129">Значение</span><span class="sxs-lookup"><span data-stu-id="0d813-129">Value</span></span>|<span data-ttu-id="0d813-130">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0d813-131">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0d813-131">*method_name*</span></span>|<span data-ttu-id="0d813-132">Имя метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-132">The method name.</span></span> <span data-ttu-id="0d813-133">Тип метода определяется родительским [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элементом или.</span><span class="sxs-lookup"><span data-stu-id="0d813-133">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="0d813-134">Сигнатура атрибута</span><span class="sxs-lookup"><span data-stu-id="0d813-134">Signature attribute</span></span>  
  
|<span data-ttu-id="0d813-135">Значение</span><span class="sxs-lookup"><span data-stu-id="0d813-135">Value</span></span>|<span data-ttu-id="0d813-136">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0d813-137">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="0d813-137">*method_signature*</span></span>|<span data-ttu-id="0d813-138">Типы параметров, которые образуют сигнатуру метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-138">The parameter types that form the method signature.</span></span> <span data-ttu-id="0d813-139">Несколько параметров разделяются запятыми, например, `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="0d813-139">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="0d813-140">Имена параметров типа должно быть полными.</span><span class="sxs-lookup"><span data-stu-id="0d813-140">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0d813-141">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="0d813-141">All other attributes</span></span>  
  
|<span data-ttu-id="0d813-142">Значение</span><span class="sxs-lookup"><span data-stu-id="0d813-142">Value</span></span>|<span data-ttu-id="0d813-143">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0d813-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0d813-144">*policy_setting*</span></span>|<span data-ttu-id="0d813-145">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="0d813-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="0d813-146">Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`.</span><span class="sxs-lookup"><span data-stu-id="0d813-146">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0d813-147">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0d813-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d813-148">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0d813-148">Child Elements</span></span>  
  
|<span data-ttu-id="0d813-149">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d813-149">Element</span></span>|<span data-ttu-id="0d813-150">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-150">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="0d813-151">Применяет политику к типу аргумента, переданного методу.</span><span class="sxs-lookup"><span data-stu-id="0d813-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="0d813-152">Применяет политику к параметру типа универсального типа или метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-152">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="0d813-153">Применяет политику к типу, если политика была применена для метода, представленного содержащим элементом `<Method>`.</span><span class="sxs-lookup"><span data-stu-id="0d813-153">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="0d813-154">Применяет политику к типу, представленному аргументом <xref:System.Type>, переданным методу.</span><span class="sxs-lookup"><span data-stu-id="0d813-154">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d813-155">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0d813-155">Parent Elements</span></span>  
  
|<span data-ttu-id="0d813-156">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d813-156">Element</span></span>|<span data-ttu-id="0d813-157">Описание</span><span class="sxs-lookup"><span data-stu-id="0d813-157">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0d813-158">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0d813-158">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0d813-159">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0d813-159">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d813-160">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d813-160">Remarks</span></span>  

 <span data-ttu-id="0d813-161">Элемент `<Method>` универсального метода применяет свою политику для всех экземпляров, которые не имеют собственной политики.</span><span class="sxs-lookup"><span data-stu-id="0d813-161">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="0d813-162">Можно использовать атрибут `Signature`, чтобы задать политику для перегрузки определенного метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-162">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="0d813-163">В противном случае, если атрибут `Signature` отсутствует, директива среды выполнения применяется для всех перегруженных версий метода.</span><span class="sxs-lookup"><span data-stu-id="0d813-163">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="0d813-164">Нельзя определить политику отражения среды выполнения для конструктора, используя элемент `<Method>`.</span><span class="sxs-lookup"><span data-stu-id="0d813-164">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="0d813-165">Вместо этого используйте `Activate` атрибут  [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) элемента,, [\<Type>](type-element-net-native.md) или [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0d813-165">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d813-166">Пример</span><span class="sxs-lookup"><span data-stu-id="0d813-166">Example</span></span>  

 <span data-ttu-id="0d813-167">Метод `Stringify` в следующем примере – это универсальный метод форматирования, который использует отражение для преобразования объекта в строковое представление.</span><span class="sxs-lookup"><span data-stu-id="0d813-167">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="0d813-168">Помимо вызова метода  `ToString` по умолчанию объекта , метод может создать отформатированную результирующую строку путем передачи методу  `ToString` объекта строки формата, реализации <xref:System.IFormatProvider>, или и то и другое.</span><span class="sxs-lookup"><span data-stu-id="0d813-168">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="0d813-169">Он также может вызвать одну из перегрузок <xref:System.Convert.ToString%2A?displayProperty=nameWithType>, которая преобразует число в двоичное, шестнадцатеричное или восьмеричное представление.</span><span class="sxs-lookup"><span data-stu-id="0d813-169">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="0d813-170">Метод `Stringify` может быть вызван таким кодом, как указан ниже:</span><span class="sxs-lookup"><span data-stu-id="0d813-170">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="0d813-171">Тем не менее при компиляции с .NET Native пример может вызвать ряд исключений во время выполнения, включая исключения <xref:System.NullReferenceException> и [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). Это происходит потому, что метод `Stringify` предназначен главным образом для поддержки динамического форматирования простых типов в библиотеке классов платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d813-171">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="0d813-172">Однако их метаданные не становятся доступными в файле директив по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d813-172">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="0d813-173">Даже в том случае, если метаданные доступны, в примере возникают исключения [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), поскольку соответствующие реализации `ToString` не были включены в машинный код.</span><span class="sxs-lookup"><span data-stu-id="0d813-173">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="0d813-174">Эти исключения можно устранить с помощью [\<Type>](type-element-net-native.md) элемента, чтобы определить типы, метаданные которых должны присутствовать, и добавить `<Method>` элементы, чтобы гарантировать, что также имеется реализация перегрузок методов, которые могут вызываться динамически.</span><span class="sxs-lookup"><span data-stu-id="0d813-174">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="0d813-175">Ниже приведен файл default.rd.xml, который устраняет эти исключения и позволяет выполнить пример без ошибок.</span><span class="sxs-lookup"><span data-stu-id="0d813-175">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d813-176">См. также</span><span class="sxs-lookup"><span data-stu-id="0d813-176">See also</span></span>

- [<span data-ttu-id="0d813-177">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0d813-177">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0d813-178">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0d813-178">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0d813-179">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0d813-179">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="0d813-180">\<MethodInstantiation> Элемент</span><span class="sxs-lookup"><span data-stu-id="0d813-180">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
