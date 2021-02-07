---
description: 'Дополнительные сведения об <MethodInstantiation> элементе: Element (.NET Native)'
title: <MethodInstantiation> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: 985d522a559dbbce936a2f29a9983c89ebd18a48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747495"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="0c6dd-103">\<MethodInstantiation> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0c6dd-103">\<MethodInstantiation> Element (.NET Native)</span></span>

<span data-ttu-id="0c6dd-104">Применяет политику отражения среды выполнения к сконструированному универсальному методу.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-104">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c6dd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c6dd-105">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c6dd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0c6dd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0c6dd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c6dd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0c6dd-108">Attributes</span></span>  
  
|<span data-ttu-id="0c6dd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0c6dd-109">Attribute</span></span>|<span data-ttu-id="0c6dd-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="0c6dd-110">Attribute type</span></span>|<span data-ttu-id="0c6dd-111">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0c6dd-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0c6dd-112">General</span></span>|<span data-ttu-id="0c6dd-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-113">Required attribute.</span></span> <span data-ttu-id="0c6dd-114">Задает имя метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-114">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="0c6dd-115">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0c6dd-115">General</span></span>|<span data-ttu-id="0c6dd-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-116">Optional attribute.</span></span> <span data-ttu-id="0c6dd-117">Определяет именованные параметры метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-117">Specifies named parameters of the method.</span></span> <span data-ttu-id="0c6dd-118">Несколько именованных параметров разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-118">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="0c6dd-119">Атрибут `Signature` позволяет различать перегруженные методы.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-119">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="0c6dd-120">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0c6dd-120">General</span></span>|<span data-ttu-id="0c6dd-121">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-121">Required attribute.</span></span> <span data-ttu-id="0c6dd-122">Задает аргументы универсального типа.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-122">Specifies the generic type arguments.</span></span> <span data-ttu-id="0c6dd-123">При наличии нескольких аргументов, они разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-123">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="0c6dd-124">Отражение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-124">Reflection</span></span>|<span data-ttu-id="0c6dd-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-125">Optional attribute.</span></span> <span data-ttu-id="0c6dd-126">Определяет запрос для получения сведений о методе или перечисляет методы, но не включает динамический вызов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-126">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0c6dd-127">Отражение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-127">Reflection</span></span>|<span data-ttu-id="0c6dd-128">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-128">Optional attribute.</span></span> <span data-ttu-id="0c6dd-129">Управляет доступом среды выполнения к конструктору или методу для включения динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-129">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="0c6dd-130">Эта политика гарантирует, что член может быть вызван динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-130">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0c6dd-131">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="0c6dd-131">Name attribute</span></span>  
  
|<span data-ttu-id="0c6dd-132">Значение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-132">Value</span></span>|<span data-ttu-id="0c6dd-133">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c6dd-134">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0c6dd-134">*method_name*</span></span>|<span data-ttu-id="0c6dd-135">Имя метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-135">The method name.</span></span> <span data-ttu-id="0c6dd-136">Тип метода определяется родительским [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элементом или.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-136">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="0c6dd-137">Сигнатура атрибута</span><span class="sxs-lookup"><span data-stu-id="0c6dd-137">Signature attribute</span></span>  
  
|<span data-ttu-id="0c6dd-138">Значение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-138">Value</span></span>|<span data-ttu-id="0c6dd-139">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c6dd-140">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="0c6dd-140">*method_signature*</span></span>|<span data-ttu-id="0c6dd-141">Определяет именованные параметры метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-141">Specifies the named parameters of the method.</span></span> <span data-ttu-id="0c6dd-142">При наличии нескольких параметров, они разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-142">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="0c6dd-143">Атрибут аргументов</span><span class="sxs-lookup"><span data-stu-id="0c6dd-143">Arguments attribute</span></span>  
  
|<span data-ttu-id="0c6dd-144">Значение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-144">Value</span></span>|<span data-ttu-id="0c6dd-145">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c6dd-146">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="0c6dd-146">*method_arguments*</span></span>|<span data-ttu-id="0c6dd-147">Задает аргументы универсального типа.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-147">Specifies the generic type arguments.</span></span> <span data-ttu-id="0c6dd-148">При наличии нескольких аргументов, они разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-148">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="0c6dd-149">Каждый аргумент должен содержать полное имя типа.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-149">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0c6dd-150">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="0c6dd-150">All other attributes</span></span>  
  
|<span data-ttu-id="0c6dd-151">Значение</span><span class="sxs-lookup"><span data-stu-id="0c6dd-151">Value</span></span>|<span data-ttu-id="0c6dd-152">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c6dd-153">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0c6dd-153">*policy_setting*</span></span>|<span data-ttu-id="0c6dd-154">Параметр, применяемый к этому типу политики для метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-154">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="0c6dd-155">Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-155">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0c6dd-156">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0c6dd-156">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c6dd-157">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0c6dd-157">Child Elements</span></span>  

 <span data-ttu-id="0c6dd-158">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c6dd-159">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0c6dd-159">Parent Elements</span></span>  
  
|<span data-ttu-id="0c6dd-160">Элемент</span><span class="sxs-lookup"><span data-stu-id="0c6dd-160">Element</span></span>|<span data-ttu-id="0c6dd-161">Описание</span><span class="sxs-lookup"><span data-stu-id="0c6dd-161">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0c6dd-162">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-162">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0c6dd-163">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-163">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c6dd-164">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c6dd-164">Remarks</span></span>  

 <span data-ttu-id="0c6dd-165">Элемент `<MethodInstantiation>`  переопределяет политику отражения среды выполнения его соответствующего открытого универсального метода.</span><span class="sxs-lookup"><span data-stu-id="0c6dd-165">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6dd-166">См. также</span><span class="sxs-lookup"><span data-stu-id="0c6dd-166">See also</span></span>

- [<span data-ttu-id="0c6dd-167">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0c6dd-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0c6dd-168">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0c6dd-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0c6dd-169">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0c6dd-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="0c6dd-170">\<Method> Элемент</span><span class="sxs-lookup"><span data-stu-id="0c6dd-170">\<Method> Element</span></span>](method-element-net-native.md)
