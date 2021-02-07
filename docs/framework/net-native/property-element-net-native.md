---
description: 'Дополнительные сведения об <Property> элементе: Element (.NET Native)'
title: <Property> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: cd3c033fd2ce21b69ff0d8563f0782838f39b09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738472"
---
# <a name="property-element-net-native"></a><span data-ttu-id="0eebd-103">\<Property> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0eebd-103">\<Property> Element (.NET Native)</span></span>

<span data-ttu-id="0eebd-104">Применяет политику отражения среды выполнения к свойству.</span><span class="sxs-lookup"><span data-stu-id="0eebd-104">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eebd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0eebd-105">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eebd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0eebd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0eebd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0eebd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eebd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0eebd-108">Attributes</span></span>  
  
|<span data-ttu-id="0eebd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0eebd-109">Attribute</span></span>|<span data-ttu-id="0eebd-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="0eebd-110">Attribute type</span></span>|<span data-ttu-id="0eebd-111">Описание</span><span class="sxs-lookup"><span data-stu-id="0eebd-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0eebd-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0eebd-112">General</span></span>|<span data-ttu-id="0eebd-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0eebd-113">Required attribute.</span></span> <span data-ttu-id="0eebd-114">Задает имя свойства.</span><span class="sxs-lookup"><span data-stu-id="0eebd-114">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="0eebd-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="0eebd-115">Reflection</span></span>|<span data-ttu-id="0eebd-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0eebd-116">Optional attribute.</span></span> <span data-ttu-id="0eebd-117">Определяет запрос для получения сведений о свойстве или перечисляет свойство, но не включает динамический доступ во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0eebd-117">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0eebd-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="0eebd-118">Reflection</span></span>|<span data-ttu-id="0eebd-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0eebd-119">Optional attribute.</span></span> <span data-ttu-id="0eebd-120">Управляет доступом среды выполнения к свойству для включения динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="0eebd-120">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="0eebd-121">Эта политика гарантирует, что свойство можно задать или получить динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0eebd-121">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="0eebd-122">Сериализация</span><span class="sxs-lookup"><span data-stu-id="0eebd-122">Serialization</span></span>|<span data-ttu-id="0eebd-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0eebd-123">Optional attribute.</span></span> <span data-ttu-id="0eebd-124">Управляет доступом среды выполнения к свойству, чтобы включить экземпляры типов, предназначенных для сериализации в таких библиотеках, как сериализатор Newtonsoft JSON или для привязки данных.</span><span class="sxs-lookup"><span data-stu-id="0eebd-124">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0eebd-125">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="0eebd-125">Name attribute</span></span>  
  
|<span data-ttu-id="0eebd-126">Значение</span><span class="sxs-lookup"><span data-stu-id="0eebd-126">Value</span></span>|<span data-ttu-id="0eebd-127">Описание</span><span class="sxs-lookup"><span data-stu-id="0eebd-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0eebd-128">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0eebd-128">*method_name*</span></span>|<span data-ttu-id="0eebd-129">Имя свойства.</span><span class="sxs-lookup"><span data-stu-id="0eebd-129">The property name.</span></span> <span data-ttu-id="0eebd-130">Тип свойства определяется родительским [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элементом или.</span><span class="sxs-lookup"><span data-stu-id="0eebd-130">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0eebd-131">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="0eebd-131">All other attributes</span></span>  
  
|<span data-ttu-id="0eebd-132">Значение</span><span class="sxs-lookup"><span data-stu-id="0eebd-132">Value</span></span>|<span data-ttu-id="0eebd-133">Описание</span><span class="sxs-lookup"><span data-stu-id="0eebd-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0eebd-134">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0eebd-134">*policy_setting*</span></span>|<span data-ttu-id="0eebd-135">Параметр, применяемый к этому типу политики для свойства.</span><span class="sxs-lookup"><span data-stu-id="0eebd-135">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="0eebd-136">Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`.</span><span class="sxs-lookup"><span data-stu-id="0eebd-136">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0eebd-137">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0eebd-137">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eebd-138">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0eebd-138">Child Elements</span></span>  

 <span data-ttu-id="0eebd-139">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0eebd-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eebd-140">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0eebd-140">Parent Elements</span></span>  
  
|<span data-ttu-id="0eebd-141">Элемент</span><span class="sxs-lookup"><span data-stu-id="0eebd-141">Element</span></span>|<span data-ttu-id="0eebd-142">Описание</span><span class="sxs-lookup"><span data-stu-id="0eebd-142">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0eebd-143">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0eebd-143">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0eebd-144">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="0eebd-144">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eebd-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="0eebd-145">Remarks</span></span>  

 <span data-ttu-id="0eebd-146">Если политика свойства не определена явно, оно наследует политику среды выполнения своего родительского элемента.</span><span class="sxs-lookup"><span data-stu-id="0eebd-146">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eebd-147">Пример</span><span class="sxs-lookup"><span data-stu-id="0eebd-147">Example</span></span>  

 <span data-ttu-id="0eebd-148">В следующем примере используется отражение для создания экземпляров объекта `Book` и отображения значений его свойств.</span><span class="sxs-lookup"><span data-stu-id="0eebd-148">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="0eebd-149">Исходный файл default.rd.xml для проекта выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0eebd-149">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="0eebd-150">Файл применяет значение `All` к политике `Activate` для класса `Book`, который предоставляет доступ к конструкторам класса через отражение.</span><span class="sxs-lookup"><span data-stu-id="0eebd-150">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="0eebd-151">Политика `Browse` для класса `Book` наследуется от его родительского пространства имен.</span><span class="sxs-lookup"><span data-stu-id="0eebd-151">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="0eebd-152">Это свойство имеет значение `Required Public`, что делает метаданные доступными во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0eebd-152">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="0eebd-153">Ниже приведен исходный код для этого примера.</span><span class="sxs-lookup"><span data-stu-id="0eebd-153">The following is the source code for the example.</span></span> <span data-ttu-id="0eebd-154">`outputBlock`Переменная представляет <xref:Windows.UI.Xaml.Controls.TextBlock> элемент управления.</span><span class="sxs-lookup"><span data-stu-id="0eebd-154">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="0eebd-155">Тем не менее компиляция и выполнение этого примера создает исключение [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0eebd-155">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="0eebd-156">Несмотря на то, что мы уже сделали метаданные для типа `Book` доступными, нам не удалось обеспечить динамический доступ к реализациям свойств считывания.</span><span class="sxs-lookup"><span data-stu-id="0eebd-156">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="0eebd-157">Эту ошибку можно исправить одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="0eebd-157">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="0eebd-158">путем определения `Dynamic` политики для `Book` типа в его [\<Type>](type-element-net-native.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="0eebd-158">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="0eebd-159">Путем добавления вложенного [\<Property>](property-element-net-native.md) элемента для каждого свойства, для которого необходимо вызвать метод получения, как в следующем default.rd.xml файле.</span><span class="sxs-lookup"><span data-stu-id="0eebd-159">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0eebd-160">См. также</span><span class="sxs-lookup"><span data-stu-id="0eebd-160">See also</span></span>

- [<span data-ttu-id="0eebd-161">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0eebd-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0eebd-162">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0eebd-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0eebd-163">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="0eebd-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
