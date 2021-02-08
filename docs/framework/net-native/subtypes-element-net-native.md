---
description: 'Дополнительные сведения об <Subtypes> элементе: Element (.NET Native)'
title: <Subtypes> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: d30bb482e784d912d3f5d61f688ed2b824e45f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801960"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="e5666-103">\<Subtypes> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e5666-103">\<Subtypes> Element (.NET Native)</span></span>

<span data-ttu-id="e5666-104">Применяет политику среды выполнения для всех классов, унаследованных из содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="e5666-104">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5666-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5666-105">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5666-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e5666-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e5666-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e5666-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5666-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e5666-108">Attributes</span></span>  
  
|<span data-ttu-id="e5666-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e5666-109">Attribute</span></span>|<span data-ttu-id="e5666-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="e5666-110">Attribute type</span></span>|<span data-ttu-id="e5666-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e5666-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="e5666-112">Отражение</span><span class="sxs-lookup"><span data-stu-id="e5666-112">Reflection</span></span>|<span data-ttu-id="e5666-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-113">Optional attribute.</span></span> <span data-ttu-id="e5666-114">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="e5666-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e5666-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="e5666-115">Reflection</span></span>|<span data-ttu-id="e5666-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-116">Optional attribute.</span></span> <span data-ttu-id="e5666-117">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e5666-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="e5666-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="e5666-118">Reflection</span></span>|<span data-ttu-id="e5666-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-119">Optional attribute.</span></span> <span data-ttu-id="e5666-120">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="e5666-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e5666-121">Сериализация</span><span class="sxs-lookup"><span data-stu-id="e5666-121">Serialization</span></span>|<span data-ttu-id="e5666-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-122">Optional attribute.</span></span> <span data-ttu-id="e5666-123">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="e5666-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e5666-124">Сериализация</span><span class="sxs-lookup"><span data-stu-id="e5666-124">Serialization</span></span>|<span data-ttu-id="e5666-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-125">Optional attribute.</span></span> <span data-ttu-id="e5666-126">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5666-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e5666-127">Сериализация</span><span class="sxs-lookup"><span data-stu-id="e5666-127">Serialization</span></span>|<span data-ttu-id="e5666-128">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-128">Optional attribute.</span></span> <span data-ttu-id="e5666-129">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5666-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e5666-130">Сериализация</span><span class="sxs-lookup"><span data-stu-id="e5666-130">Serialization</span></span>|<span data-ttu-id="e5666-131">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-131">Optional attribute.</span></span> <span data-ttu-id="e5666-132">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5666-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e5666-133">Interop</span><span class="sxs-lookup"><span data-stu-id="e5666-133">Interop</span></span>|<span data-ttu-id="e5666-134">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-134">Optional attribute.</span></span> <span data-ttu-id="e5666-135">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="e5666-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e5666-136">Interop</span><span class="sxs-lookup"><span data-stu-id="e5666-136">Interop</span></span>|<span data-ttu-id="e5666-137">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-137">Optional attribute.</span></span> <span data-ttu-id="e5666-138">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="e5666-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e5666-139">Interop</span><span class="sxs-lookup"><span data-stu-id="e5666-139">Interop</span></span>|<span data-ttu-id="e5666-140">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e5666-140">Optional attribute.</span></span> <span data-ttu-id="e5666-141">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="e5666-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="e5666-142">Все атрибуты</span><span class="sxs-lookup"><span data-stu-id="e5666-142">All attributes</span></span>  
  
|<span data-ttu-id="e5666-143">Значение</span><span class="sxs-lookup"><span data-stu-id="e5666-143">Value</span></span>|<span data-ttu-id="e5666-144">Описание</span><span class="sxs-lookup"><span data-stu-id="e5666-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e5666-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e5666-145">*policy_setting*</span></span>|<span data-ttu-id="e5666-146">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="e5666-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="e5666-147">Допустимые значения `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e5666-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e5666-148">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e5666-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5666-149">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e5666-149">Child Elements</span></span>  

 <span data-ttu-id="e5666-150">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e5666-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5666-151">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e5666-151">Parent Elements</span></span>  
  
|<span data-ttu-id="e5666-152">Элемент</span><span class="sxs-lookup"><span data-stu-id="e5666-152">Element</span></span>|<span data-ttu-id="e5666-153">Описание</span><span class="sxs-lookup"><span data-stu-id="e5666-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="e5666-154">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="e5666-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5666-155">Remarks</span><span class="sxs-lookup"><span data-stu-id="e5666-155">Remarks</span></span>  

 <span data-ttu-id="e5666-156">Элемент `<Subtypes>` применяет политику ко всем подтипам его содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="e5666-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="e5666-157">Используется для применения различных политик для производных типов и их базовых классов.</span><span class="sxs-lookup"><span data-stu-id="e5666-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="e5666-158">Атрибуты отражения, сериализации и взаимодействия необязательны, несмотря на то, что по крайней мере один из них должен присутствовать.</span><span class="sxs-lookup"><span data-stu-id="e5666-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5666-159">Пример</span><span class="sxs-lookup"><span data-stu-id="e5666-159">Example</span></span>  

 <span data-ttu-id="e5666-160">В следующем примере определяется класс с именем `BaseClass` и подкласс с именем `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="e5666-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="e5666-161">Как показано в следующем коде, файл директив среды выполнения явно задает политики `Dynamic` и `Activate` для `BaseClass` в `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="e5666-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="e5666-162">Из-за этого, объекты типа `BaseClass` не могут использоваться для динамического создания экземпляров или создания путем вызовов конструктора класса `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="e5666-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="e5666-163">Тем не менее, элемент `<Subtypes>` допускает использование классов, производных от `BaseClass`, для динамического создания экземпляров, а также для создания с помощью вызовов их конструкторов класса.</span><span class="sxs-lookup"><span data-stu-id="e5666-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="e5666-164">Благодаря директиве `<Subtypes>`, следующий код, динамически создающий экземпляр `Derived1` экземпляр путем вызова метода <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType>, выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="e5666-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="e5666-165">Здесь переменная блока представляет объект <xref:System.Windows.Controls.TextBlock> в пустом приложении для магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="e5666-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e5666-166">См. также</span><span class="sxs-lookup"><span data-stu-id="e5666-166">See also</span></span>

- [<span data-ttu-id="e5666-167">\<Type> Элемент</span><span class="sxs-lookup"><span data-stu-id="e5666-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="e5666-168">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e5666-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e5666-169">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e5666-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e5666-170">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e5666-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
