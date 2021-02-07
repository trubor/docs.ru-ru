---
description: 'Дополнительные сведения об <Library> элементе: Element (.NET Native)'
title: <Library> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: 224b2b9cbce8123f4a15b9ec3e3793674633822a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747612"
---
# <a name="library-element-net-native"></a><span data-ttu-id="b28ae-103">\<Library> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b28ae-103">\<Library> Element (.NET Native)</span></span>

<span data-ttu-id="b28ae-104">Определяет сборку, содержащую типы и члены типов, метаданные которой доступны для отражения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b28ae-104">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="b28ae-105">Элемент \<Directives></span><span class="sxs-lookup"><span data-stu-id="b28ae-105">\<Directives> Element</span></span>  
<span data-ttu-id="b28ae-106">Элемент \<Library></span><span class="sxs-lookup"><span data-stu-id="b28ae-106">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28ae-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b28ae-107">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b28ae-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b28ae-108">Attributes and Elements</span></span>  

 <span data-ttu-id="b28ae-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b28ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b28ae-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b28ae-110">Attributes</span></span>  
  
|<span data-ttu-id="b28ae-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b28ae-111">Attribute</span></span>|<span data-ttu-id="b28ae-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b28ae-112">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="b28ae-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="b28ae-113">Required attribute.</span></span> <span data-ttu-id="b28ae-114">Задает имя сборки.</span><span class="sxs-lookup"><span data-stu-id="b28ae-114">Specifies the name of an assembly.</span></span> <span data-ttu-id="b28ae-115">Дочерние элементы данного элемента `<Library>` определяют политику отражения среды выполнения для типов и членов типов в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="b28ae-115">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b28ae-116">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="b28ae-116">Name attribute</span></span>  
  
|<span data-ttu-id="b28ae-117">Значение</span><span class="sxs-lookup"><span data-stu-id="b28ae-117">Value</span></span>|<span data-ttu-id="b28ae-118">Описание</span><span class="sxs-lookup"><span data-stu-id="b28ae-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b28ae-119">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="b28ae-119">*assembly_name*</span></span>|<span data-ttu-id="b28ae-120">Простое имя сборки без расширения файла.</span><span class="sxs-lookup"><span data-stu-id="b28ae-120">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="b28ae-121">Этот атрибут соответствует свойству <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b28ae-121">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b28ae-122">Например, имя сборки с именем Extensions.dll является «Extensions».</span><span class="sxs-lookup"><span data-stu-id="b28ae-122">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="b28ae-123">Сведения об особой форме имени сборки *assembly_name* с поддержкой условного включения метаданных сборки см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="b28ae-123">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b28ae-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b28ae-124">Child Elements</span></span>  
  
|<span data-ttu-id="b28ae-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="b28ae-125">Element</span></span>|<span data-ttu-id="b28ae-126">Описание</span><span class="sxs-lookup"><span data-stu-id="b28ae-126">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="b28ae-127">Применяет политику ко всем типам в определенной сборке.</span><span class="sxs-lookup"><span data-stu-id="b28ae-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="b28ae-128">Применяет политику ко всем типам в определенном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="b28ae-128">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="b28ae-129">Применяет политику для конкретного типа, например, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="b28ae-129">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b28ae-130">Применяет политику к сконструированному универсальному типу.</span><span class="sxs-lookup"><span data-stu-id="b28ae-130">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="b28ae-131">Например, [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элемент можно использовать для определения политики для `List<String>` типа.</span><span class="sxs-lookup"><span data-stu-id="b28ae-131">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b28ae-132">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b28ae-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b28ae-133">Элемент</span><span class="sxs-lookup"><span data-stu-id="b28ae-133">Element</span></span>|<span data-ttu-id="b28ae-134">Описание</span><span class="sxs-lookup"><span data-stu-id="b28ae-134">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="b28ae-135">Корневой элемент файла директив среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b28ae-135">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b28ae-136">Remarks</span><span class="sxs-lookup"><span data-stu-id="b28ae-136">Remarks</span></span>  

 <span data-ttu-id="b28ae-137">[\<Directives>](directives-element-net-native.md)Элемент может содержать ноль, один или несколько `<Library>` элементов.</span><span class="sxs-lookup"><span data-stu-id="b28ae-137">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="b28ae-138">Элемент `<Library>` используется как контейнер для определения программных элементов, метаданные которых требуются во время выполнения. Этот элемент не выражают политики.</span><span class="sxs-lookup"><span data-stu-id="b28ae-138">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="b28ae-139">Во время компиляции средства компилятора осуществляют поиск только в библиотеке, назначенной с помощью элемента `<Library>`, на наличие программных элементов, определенных его дочерними элементами.</span><span class="sxs-lookup"><span data-stu-id="b28ae-139">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="b28ae-140">В отличие от этого, средства компилятора выполняют поиск всех библиотек, including.NET Framework Core Library, для программных элементов, идентифицируемых дочерними элементами [\<Application>](application-element-net-native.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="b28ae-140">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="b28ae-141">Директивы `<Library>` могут использоваться условно.</span><span class="sxs-lookup"><span data-stu-id="b28ae-141">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="b28ae-142">Если имя `<Library>` элемента начинается и заканчивается звездочкой ( \* ), `<Library>` директива действует только в том случае, если приложение ссылается на сборку, указанную между звездочками.</span><span class="sxs-lookup"><span data-stu-id="b28ae-142">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="b28ae-143">Например, следующая директива среды выполнения применяется только в том случае, если приложение ссылается на Utilities.dll сборку.</span><span class="sxs-lookup"><span data-stu-id="b28ae-143">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b28ae-144">См. также</span><span class="sxs-lookup"><span data-stu-id="b28ae-144">See also</span></span>

- [<span data-ttu-id="b28ae-145">\<Application> Элемент</span><span class="sxs-lookup"><span data-stu-id="b28ae-145">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="b28ae-146">\<Directives> Элемент</span><span class="sxs-lookup"><span data-stu-id="b28ae-146">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="b28ae-147">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b28ae-147">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b28ae-148">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="b28ae-148">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
