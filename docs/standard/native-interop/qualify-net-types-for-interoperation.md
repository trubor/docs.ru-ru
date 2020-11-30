---
title: Уточнение типов .NET для COM-взаимодействия
description: В этой статье приводятся рекомендации по предоставлению типов в сборке .NET приложениям COM для COM-взаимодействия.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 3f5fe0f168e0e520ce1985faf5a8228c1bfbdf20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734313"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="8d91d-103">Уточнение типов .NET для COM-взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8d91d-103">Qualifying .NET Types for COM Interoperation</span></span>

<span data-ttu-id="8d91d-104">Если вы планируете предоставлять типы в сборке COM-приложениям, во время разработки необходимо учитывать требования COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="8d91d-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="8d91d-105">Управляемые типы (класс, интерфейс, структура и перечисление) легко интегрируются с COM-типами, если следовать приведенным ниже рекомендациям:</span><span class="sxs-lookup"><span data-stu-id="8d91d-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="8d91d-106">Классы должны явным образом реализовывать интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="8d91d-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="8d91d-107">Несмотря на то, что COM-взаимодействие предоставляет механизм для автоматического создания интерфейса, содержащего все члены класса и члены его базового класса, гораздо эффективнее предоставлять явные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="8d91d-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="8d91d-108">Автоматически создаваемый интерфейс называется интерфейсом класса.</span><span class="sxs-lookup"><span data-stu-id="8d91d-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="8d91d-109">См. рекомендации в разделе [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса).</span><span class="sxs-lookup"><span data-stu-id="8d91d-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="8d91d-110">В Visual Basic, C# и C++ можно внедрять определения интерфейса в код вместо использования языка IDL или его эквивалента.</span><span class="sxs-lookup"><span data-stu-id="8d91d-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="8d91d-111">Дополнительные сведения о синтаксисе см. в документации по соответствующему языку.</span><span class="sxs-lookup"><span data-stu-id="8d91d-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="8d91d-112">Управляемые типы должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="8d91d-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="8d91d-113">Регистрация и экспорт в библиотеку типов поддерживаются только для открытых типов.</span><span class="sxs-lookup"><span data-stu-id="8d91d-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="8d91d-114">В результате видимыми для модели COM являются только открытые типы.</span><span class="sxs-lookup"><span data-stu-id="8d91d-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="8d91d-115">Управляемые типы предоставляют функциональные возможности другому управляемому коду, который может быть недоступен для модели COM.</span><span class="sxs-lookup"><span data-stu-id="8d91d-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="8d91d-116">Например, COM-клиентам не предоставляются параметризованные конструкторы, статические методы и поля констант.</span><span class="sxs-lookup"><span data-stu-id="8d91d-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="8d91d-117">Кроме того, поскольку среда выполнения выполняет маршалинг данных из типа и обратно, данные могут копироваться и преобразовываться.</span><span class="sxs-lookup"><span data-stu-id="8d91d-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="8d91d-118">Методы, свойства, поля и события должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="8d91d-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="8d91d-119">Члены открытых типов, которые должны быть видимыми для модели COM, также должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="8d91d-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="8d91d-120">Видимость сборки, открытого типа или открытых членов открытого типа можно ограничить с помощью атрибута <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d91d-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="8d91d-121">По умолчанию все открытые типы и члены являются видимыми.</span><span class="sxs-lookup"><span data-stu-id="8d91d-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="8d91d-122">Для активации из модели COM типы должны иметь открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="8d91d-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="8d91d-123">Таким образом, видимыми для модели COM являются только управляемые открытые типы.</span><span class="sxs-lookup"><span data-stu-id="8d91d-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="8d91d-124">При этом без открытого конструктора без параметров (конструктор без аргументов) COM-клиенты не смогут создавать этот тип.</span><span class="sxs-lookup"><span data-stu-id="8d91d-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="8d91d-125">COM-клиенты могут использовать такой тип, если он активирован другими способами.</span><span class="sxs-lookup"><span data-stu-id="8d91d-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="8d91d-126">Типы не могут быть абстрактными.</span><span class="sxs-lookup"><span data-stu-id="8d91d-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="8d91d-127">Ни COM-клиенты, ни клиенты .NET не могут создавать абстрактные типы.</span><span class="sxs-lookup"><span data-stu-id="8d91d-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="8d91d-128">При экспорте в модель COM иерархия наследования управляемого типа преобразуется в плоскую структуру.</span><span class="sxs-lookup"><span data-stu-id="8d91d-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="8d91d-129">Кроме того, в управляемой и неуправляемой средах существуют различия в управлении версиями.</span><span class="sxs-lookup"><span data-stu-id="8d91d-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="8d91d-130">Типы, предоставляемые модели COM, имеют характеристики управления версиями, отличные от других управляемых типов.</span><span class="sxs-lookup"><span data-stu-id="8d91d-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d91d-131">См. также</span><span class="sxs-lookup"><span data-stu-id="8d91d-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="8d91d-132">Предоставление компонентов .NET Framework клиентам COM</span><span class="sxs-lookup"><span data-stu-id="8d91d-132">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- <span data-ttu-id="8d91d-133">[Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса)</span><span class="sxs-lookup"><span data-stu-id="8d91d-133">[Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface)</span></span>
- [<span data-ttu-id="8d91d-134">Применение атрибутов взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8d91d-134">Applying Interop Attributes</span></span>](apply-interop-attributes.md)
- [<span data-ttu-id="8d91d-135">Упаковка сборки .NET Framework для COM</span><span class="sxs-lookup"><span data-stu-id="8d91d-135">Packaging a .NET Framework Assembly for COM</span></span>](../../framework/interop/packaging-an-assembly-for-com.md)
