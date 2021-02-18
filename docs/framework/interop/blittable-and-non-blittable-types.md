---
title: Преобразуемые и непреобразуемые типы
description: Узнайте, что представляют собой преобразуемые и непреобразуемые типы. Преобразуемые типы данных одинаково представлены в управляемой и неуправляемой памяти и не требуют специальной обработки.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: c9168bd245e10232a798b3e6f3b9448b24996a77
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436127"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="30038-104">Преобразуемые и непреобразуемые типы</span><span class="sxs-lookup"><span data-stu-id="30038-104">Blittable and Non-Blittable Types</span></span>

<span data-ttu-id="30038-105">Большинство типов данных имеют общее представление как в управляемой, так и в неуправляемой памяти и не требуют специальной обработки со стороны маршалера взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="30038-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="30038-106">Такие типы называются *непреобразуемыми*, поскольку при их передаче между управляемым и неуправляемым кодом не требуется преобразование.</span><span class="sxs-lookup"><span data-stu-id="30038-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="30038-107">Структуры, возвращаемые из вызовов неуправляемого кода, должны иметь непреобразуемый тип.</span><span class="sxs-lookup"><span data-stu-id="30038-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="30038-108">Вызовы неуправляемого кода не поддерживают преобразуемые структуры, такие как типы возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="30038-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="30038-109">Следующие типы из пространства имен <xref:System> относятся к непреобразуемым:</span><span class="sxs-lookup"><span data-stu-id="30038-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="30038-110">Также непреобразуемыми являются следующие сложные типы:</span><span class="sxs-lookup"><span data-stu-id="30038-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="30038-111">Одномерные массивы непреобразуемых примитивных типов, например массивы целых чисел.</span><span class="sxs-lookup"><span data-stu-id="30038-111">One-dimensional arrays of blittable primitive types, such as an array of integers.</span></span> <span data-ttu-id="30038-112">Тем не менее тип, содержащий переменный массив непреобразуемых типов, сам по себе не является непреобразуемым.</span><span class="sxs-lookup"><span data-stu-id="30038-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>
  
- <span data-ttu-id="30038-113">Форматированные типы значений, содержащие только непреобразуемые типы (и классы, если они маршалируются как непреобразуемые типы).</span><span class="sxs-lookup"><span data-stu-id="30038-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="30038-114">Дополнительные сведения о форматированных типах значений см. в разделе [Маршалинг по умолчанию для типов значений](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="30038-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="30038-115">Ссылки на объекты не относятся к непреобразуемым типам.</span><span class="sxs-lookup"><span data-stu-id="30038-115">Object references are not blittable.</span></span> <span data-ttu-id="30038-116">Это справедливо для массивов ссылок на объекты, которые сами по себе являются непреобразуемыми.</span><span class="sxs-lookup"><span data-stu-id="30038-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="30038-117">Например, можно определить непреобразуемую структуру, однако при этом нельзя определить непреобразуемый тип, который содержит массив ссылок на такие структуры.</span><span class="sxs-lookup"><span data-stu-id="30038-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="30038-118">В целях оптимизации массивы непреобразуемых примитивных типов и классов, которые содержат только непреобразуемые члены, при маршалинге [закрепляются](copying-and-pinning.md), а не копируются.</span><span class="sxs-lookup"><span data-stu-id="30038-118">As an optimization, arrays of blittable primitive types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="30038-119">Эти типы могут маршалироваться как параметры ввода-вывода, если вызывающий и вызываемый объект находятся в одном подразделении.</span><span class="sxs-lookup"><span data-stu-id="30038-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="30038-120">Тем не менее такие типы фактически маршалируются как параметры ввода. Чтобы маршалировать аргумент как параметр ввода-вывода, необходимо применить атрибуты <xref:System.Runtime.InteropServices.InAttribute> и <xref:System.Runtime.InteropServices.OutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30038-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>
  
 <span data-ttu-id="30038-121">Некоторые управляемые типы данных требуют отличающегося представления в неуправляемой среде.</span><span class="sxs-lookup"><span data-stu-id="30038-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="30038-122">Такие преобразуемые типы данных должны преобразовываться в форму, подходящую для маршалинга.</span><span class="sxs-lookup"><span data-stu-id="30038-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="30038-123">Например, управляемые строки относятся к преобразуемым типам, поскольку перед выполнением маршалинга их необходимо преобразовывать в строковые объекты.</span><span class="sxs-lookup"><span data-stu-id="30038-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="30038-124">В следующей таблице перечислены преобразуемые типы из пространства имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="30038-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="30038-125">[Делегаты](default-marshaling-behavior.md#default-marshaling-for-delegates), представляющие собой структуры данных, которые ссылаются на статический метод или экземпляр класса, также являются преобразуемыми.</span><span class="sxs-lookup"><span data-stu-id="30038-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="30038-126">Преобразуемые типы</span><span class="sxs-lookup"><span data-stu-id="30038-126">Non-blittable type</span></span>|<span data-ttu-id="30038-127">Описание</span><span class="sxs-lookup"><span data-stu-id="30038-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="30038-128">System.Array</span><span class="sxs-lookup"><span data-stu-id="30038-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="30038-129">Преобразует в массив в стиле C или `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="30038-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="30038-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30038-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="30038-131">Преобразует в одно-, двух- или четырехбайтовое значение, где `true` выражается как 1 или -1.</span><span class="sxs-lookup"><span data-stu-id="30038-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="30038-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30038-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="30038-133">Преобразует в символ Юникода или ANSI.</span><span class="sxs-lookup"><span data-stu-id="30038-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="30038-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30038-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="30038-135">Преобразует в интерфейс класса.</span><span class="sxs-lookup"><span data-stu-id="30038-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="30038-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="30038-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="30038-137">Преобразует в вариант или интерфейс.</span><span class="sxs-lookup"><span data-stu-id="30038-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="30038-138">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="30038-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="30038-139">Преобразует в массив в стиле C или `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="30038-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="30038-140">System.String</span><span class="sxs-lookup"><span data-stu-id="30038-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="30038-141">Преобразует в строку, завершающуюся ссылкой NULL, или в BSTR.</span><span class="sxs-lookup"><span data-stu-id="30038-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="30038-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30038-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="30038-143">Преобразует в структуру с фиксированным расположением в памяти.</span><span class="sxs-lookup"><span data-stu-id="30038-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="30038-144">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="30038-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="30038-145">Преобразует в массив в стиле C или `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="30038-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="30038-146">Типы классов и объектов поддерживаются только COM-взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="30038-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="30038-147">Для соответствующих типов в Visual Basic, C# и C++ см. раздел [Обзор библиотеки классов](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30038-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30038-148">См. также</span><span class="sxs-lookup"><span data-stu-id="30038-148">See also</span></span>

- [<span data-ttu-id="30038-149">Характеристики маршалинга по умолчанию</span><span class="sxs-lookup"><span data-stu-id="30038-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
