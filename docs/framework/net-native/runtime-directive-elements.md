---
description: 'Дополнительные сведения: элементы директив среды выполнения'
title: Элементы директив среды выполнения
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: 74ff6c7d782f48106e37b99187770d8e82926be4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738433"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="b962a-103">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="b962a-103">Runtime Directive Elements</span></span>

<span data-ttu-id="b962a-104">Формат файла директив (rd.xml) среды выполнения поддерживает следующие элементы директивы среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b962a-104">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="b962a-105">Иерархическое представление см. в разделе [Справочник по конфигурационному файлу директив среды выполнения (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b962a-105">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="b962a-106">Применяется политика отражения среды выполнения для всех типов, используемых в приложении и служит в качестве контейнера для приложения типы и члены типов, метаданные которого доступны для отражения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b962a-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="b962a-107">Это дочерний [\<Directives>](directives-element-net-native.md) элемент элемента.</span><span class="sxs-lookup"><span data-stu-id="b962a-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="b962a-108">Применяет политику среды выполнения ко всем типам в сборке.</span><span class="sxs-lookup"><span data-stu-id="b962a-108">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="b962a-109">Это дочерний элемент [\<Application>](application-element-net-native.md) элементов и [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-109">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="b962a-110">Если содержащая его [\<Type>](type-element-net-native.md) директива является атрибутом, применяет политику среды выполнения к элементам кода, к которым применяется этот атрибут.</span><span class="sxs-lookup"><span data-stu-id="b962a-110">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="b962a-111">Корневой элемент в каждом файле директив среды выполнения для .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b962a-111">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="b962a-112">Его дочерними элементами являются [\<Application>](application-element-net-native.md) и [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-112">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="b962a-113">Применяет политику среды выполнения к событию.</span><span class="sxs-lookup"><span data-stu-id="b962a-113">Applies runtime policy to an event.</span></span> <span data-ttu-id="b962a-114">Это дочерний элемент [\<Type>](type-element-net-native.md) элементов и [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-114">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="b962a-115">Применяет политику среды выполнения к полю.</span><span class="sxs-lookup"><span data-stu-id="b962a-115">Applies runtime policy to a field.</span></span> <span data-ttu-id="b962a-116">Это дочерний элемент [\<Type>](type-element-net-native.md) элементов и [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-116">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="b962a-117">Применяет политику среды выполнения к параметру типа универсального типа или метода.</span><span class="sxs-lookup"><span data-stu-id="b962a-117">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="b962a-118">Применяет политику среды выполнения к типу, если политика была применена к содержащему типу или методу.</span><span class="sxs-lookup"><span data-stu-id="b962a-118">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="b962a-119">Применяет политику среды выполнения ко всем типам в сборке.</span><span class="sxs-lookup"><span data-stu-id="b962a-119">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="b962a-120">Это дочерний элемент [\<Application>](application-element-net-native.md) элементов и [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-120">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="b962a-121">Применяет политику среды выполнения к методу.</span><span class="sxs-lookup"><span data-stu-id="b962a-121">Applies runtime policy to a method.</span></span> <span data-ttu-id="b962a-122">Это дочерний элемент [\<Type>](type-element-net-native.md) элементов и [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-122">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="b962a-123">Применяет политику среды выполнения к сконструированному универсальному методу.</span><span class="sxs-lookup"><span data-stu-id="b962a-123">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="b962a-124">Это дочерний элемент [\<Type>](type-element-net-native.md) элементов и [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-124">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="b962a-125">Применяет политику среды выполнения ко всем типам в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="b962a-125">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="b962a-126">Применяет политику среды выполнения к типу аргумента, переданного методу.</span><span class="sxs-lookup"><span data-stu-id="b962a-126">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="b962a-127">Применяет политику среды выполнения к свойству.</span><span class="sxs-lookup"><span data-stu-id="b962a-127">Applies runtime policy to a property.</span></span> <span data-ttu-id="b962a-128">Это дочерний элемент [\<Type>](type-element-net-native.md) элементов и [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b962a-128">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="b962a-129">Применяет политику среды выполнения для всех классов, унаследованных из содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="b962a-129">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="b962a-130">Применяет политику среды выполнения к типу.</span><span class="sxs-lookup"><span data-stu-id="b962a-130">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="b962a-131">Применяет политику среды выполнения к сконструированному универсальному типу.</span><span class="sxs-lookup"><span data-stu-id="b962a-131">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="b962a-132">Применяет политику среды выполнения к типу, представленному аргументом <xref:System.Type>, переданным методу.</span><span class="sxs-lookup"><span data-stu-id="b962a-132">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b962a-133">См. также</span><span class="sxs-lookup"><span data-stu-id="b962a-133">See also</span></span>

- [<span data-ttu-id="b962a-134">Справочник по конфигурационному файлу rd.xml</span><span class="sxs-lookup"><span data-stu-id="b962a-134">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
