---
description: 'Дополнительные сведения: Общие сведения об атрибутах (Visual Basic)'
title: Обзор атрибутов
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: f25e69452f0af1c89af667619e673f8906704d1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437726"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="5fe66-103">Общие сведения об атрибутах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fe66-103">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="5fe66-104">Атрибуты предоставляют мощное средство для связывания метаданных или декларативной информации с кодом (сборки, типы, методы, свойства и т. д.).</span><span class="sxs-lookup"><span data-stu-id="5fe66-104">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="5fe66-105">Связав атрибут связан с сущностью программы, вы можете проверять этот атрибут во время выполнения, используя технику *отражения*.</span><span class="sxs-lookup"><span data-stu-id="5fe66-105">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="5fe66-106">Дополнительные сведения см. в статье [Отражение (Visual Basic)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5fe66-106">For more information, see [Reflection (Visual Basic)](../reflection.md).</span></span>

<span data-ttu-id="5fe66-107">Атрибуты имеют следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="5fe66-107">Attributes have the following properties:</span></span>

- <span data-ttu-id="5fe66-108">Атрибуты добавляют в программу метаданные.</span><span class="sxs-lookup"><span data-stu-id="5fe66-108">Attributes add metadata to your program.</span></span> <span data-ttu-id="5fe66-109">*Метаданные* — это сведения о типах, определенных в программе.</span><span class="sxs-lookup"><span data-stu-id="5fe66-109">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="5fe66-110">Все сборки .NET содержат некоторый набор метаданных, описывающих типы и члены типов, определенные в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="5fe66-110">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="5fe66-111">Вы можете добавить пользовательские атрибуты, чтобы указать любую дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="5fe66-111">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="5fe66-112">Дополнительные сведения см. в статье [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание пользовательских атрибутов (Visual Basic)).</span><span class="sxs-lookup"><span data-stu-id="5fe66-112">For more information, see, [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md).</span></span>

- <span data-ttu-id="5fe66-113">Вы можете применить один или несколько атрибутов ко всей сборке, к модулю или к более мелким элементам программы, например к классам и свойствам.</span><span class="sxs-lookup"><span data-stu-id="5fe66-113">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="5fe66-114">Атрибуты могут принимать аргументы, так же как методы и свойства.</span><span class="sxs-lookup"><span data-stu-id="5fe66-114">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="5fe66-115">Программа может проверить собственные метаданные или метаданные в других программах, используя отражение.</span><span class="sxs-lookup"><span data-stu-id="5fe66-115">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="5fe66-116">Дополнительные сведения см. в статье [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic)).</span><span class="sxs-lookup"><span data-stu-id="5fe66-116">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="5fe66-117">Использование атрибутов</span><span class="sxs-lookup"><span data-stu-id="5fe66-117">Using Attributes</span></span>

<span data-ttu-id="5fe66-118">Атрибуты можно использовать почти в любых объявлениях, но для каждого атрибута можно ограничить типы объявлений, в которых он является допустимым.</span><span class="sxs-lookup"><span data-stu-id="5fe66-118">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="5fe66-119">В Visual Basic атрибут заключен в угловые скобки ( \< > ).</span><span class="sxs-lookup"><span data-stu-id="5fe66-119">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="5fe66-120">Они должны располагаться непосредственно перед тем элементом, к которому они применяются, и обязательно в той же строке.</span><span class="sxs-lookup"><span data-stu-id="5fe66-120">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="5fe66-121">В этом примере атрибут <xref:System.SerializableAttribute> используется для применения определенной характеристики к классу:</span><span class="sxs-lookup"><span data-stu-id="5fe66-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="5fe66-122">Метод с атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute> объявляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5fe66-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="5fe66-123">В объявлении можно разместить несколько атрибутов:</span><span class="sxs-lookup"><span data-stu-id="5fe66-123">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="5fe66-124">Некоторые атрибуты можно указать для одной сущности более одного раза.</span><span class="sxs-lookup"><span data-stu-id="5fe66-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="5fe66-125">Пример такого многократно используемого атрибута — <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="5fe66-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="5fe66-126">По соглашению все имена атрибутов заканчиваются словом "Attribute", чтобы отличать их от других элементов платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5fe66-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="5fe66-127">Но при использовании атрибута в коде этот суффикс можно не указывать.</span><span class="sxs-lookup"><span data-stu-id="5fe66-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="5fe66-128">Например, обращение `[DllImport]` эквивалентно `[DllImportAttribute]`, хотя в .NET Framework этот атрибут имеет имя `DllImportAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5fe66-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="5fe66-129">Параметры атрибутов</span><span class="sxs-lookup"><span data-stu-id="5fe66-129">Attribute Parameters</span></span>

<span data-ttu-id="5fe66-130">Многие атрибуты имеют параметры, которые могут быть позиционными, неименованными или именованными.</span><span class="sxs-lookup"><span data-stu-id="5fe66-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="5fe66-131">Позиционные параметры необходимо указывать в строгом порядке и их нельзя опускать. Именованные параметры являются необязательными и их можно указывать в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="5fe66-131">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="5fe66-132">Сначала указываются позиционные параметры.</span><span class="sxs-lookup"><span data-stu-id="5fe66-132">Positional parameters are specified first.</span></span> <span data-ttu-id="5fe66-133">Например, эти три атрибута являются эквивалентными:</span><span class="sxs-lookup"><span data-stu-id="5fe66-133">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="5fe66-134">Первый параметр (имя библиотеки DLL) является позиционным и всегда располагается первым, остальные параметры являются именованными.</span><span class="sxs-lookup"><span data-stu-id="5fe66-134">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="5fe66-135">В этом примере оба именованных параметра имеют значение по умолчанию (false), и мы можем их опустить.</span><span class="sxs-lookup"><span data-stu-id="5fe66-135">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="5fe66-136">Сведения о значениях параметров по умолчанию указываются в документации по каждому отдельному атрибуту.</span><span class="sxs-lookup"><span data-stu-id="5fe66-136">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="5fe66-137">Целевые объекты атрибутов</span><span class="sxs-lookup"><span data-stu-id="5fe66-137">Attribute Targets</span></span>

<span data-ttu-id="5fe66-138">*Целевой объект* атрибута — это сущность, к которой применяется атрибут.</span><span class="sxs-lookup"><span data-stu-id="5fe66-138">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="5fe66-139">Например, атрибут можно применить к классу, отдельному методу или ко всей сборке.</span><span class="sxs-lookup"><span data-stu-id="5fe66-139">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="5fe66-140">По умолчанию атрибут применяется к тому элементу, перед которым он указан.</span><span class="sxs-lookup"><span data-stu-id="5fe66-140">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="5fe66-141">Но у вас есть возможность явным образом указать, например, что атрибут применяется к методу, параметру или возвращаемому значению.</span><span class="sxs-lookup"><span data-stu-id="5fe66-141">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="5fe66-142">Чтобы явным образом определить целевой объект атрибута, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="5fe66-142">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="5fe66-143">Возможные значения `target` перечислены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="5fe66-143">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="5fe66-144">Целевое значение</span><span class="sxs-lookup"><span data-stu-id="5fe66-144">Target value</span></span>|<span data-ttu-id="5fe66-145">Применение</span><span class="sxs-lookup"><span data-stu-id="5fe66-145">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="5fe66-146">Вся сборка</span><span class="sxs-lookup"><span data-stu-id="5fe66-146">Entire assembly</span></span>|
|`module`|<span data-ttu-id="5fe66-147">Текущий модуль сборки (это не то же самое, что модуль Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fe66-147">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="5fe66-148">Следующий пример демонстрирует, как применить атрибуты к сборкам и модулям.</span><span class="sxs-lookup"><span data-stu-id="5fe66-148">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="5fe66-149">Дополнительные сведения см. в статье [Common Attributes (Visual Basic)](common-attributes.md) (Распространенные атрибуты (Visual Basic)).</span><span class="sxs-lookup"><span data-stu-id="5fe66-149">For more information, see [Common Attributes (Visual Basic)](common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="5fe66-150">Популярные методы применения атрибутов</span><span class="sxs-lookup"><span data-stu-id="5fe66-150">Common Uses for Attributes</span></span>

<span data-ttu-id="5fe66-151">В следующем списке перечислены несколько распространенных применений для атрибутов.</span><span class="sxs-lookup"><span data-stu-id="5fe66-151">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="5fe66-152">Указание для методов в веб-службах атрибута `WebMethod`, который обозначает, что метод должен вызываться по протоколу SOAP.</span><span class="sxs-lookup"><span data-stu-id="5fe66-152">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="5fe66-153">Для получения дополнительной информации см. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5fe66-153">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="5fe66-154">Описание способов упаковки параметров методов при взаимодействии с машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="5fe66-154">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="5fe66-155">Для получения дополнительной информации см. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5fe66-155">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="5fe66-156">Описание свойств COM для классов, методов и интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="5fe66-156">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="5fe66-157">Вызов неуправляемого кода с помощью класса <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5fe66-157">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="5fe66-158">Указание для сборки таких параметров, как заголовок, версия, описание или товарный знак.</span><span class="sxs-lookup"><span data-stu-id="5fe66-158">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="5fe66-159">Указание членов класса, которые будут сериализованы при сохранении класса.</span><span class="sxs-lookup"><span data-stu-id="5fe66-159">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="5fe66-160">Описание правил сопоставления членов класса с XML-узлами при XML-сериализации.</span><span class="sxs-lookup"><span data-stu-id="5fe66-160">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="5fe66-161">Описание требований безопасности для методов.</span><span class="sxs-lookup"><span data-stu-id="5fe66-161">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="5fe66-162">Указание характеристик, используемых для обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="5fe66-162">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="5fe66-163">Управление оптимизацией для JIT-компилятора, сохраняя при этом простоту отладки кода.</span><span class="sxs-lookup"><span data-stu-id="5fe66-163">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="5fe66-164">Получение сведений об объекте, вызывающем метод.</span><span class="sxs-lookup"><span data-stu-id="5fe66-164">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5fe66-165">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="5fe66-165">Related Sections</span></span>

<span data-ttu-id="5fe66-166">Дополнительные сведения можно найти в разделе</span><span class="sxs-lookup"><span data-stu-id="5fe66-166">For more information, see:</span></span>

- <span data-ttu-id="5fe66-167">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание настраиваемых атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-167">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md)</span></span>

- <span data-ttu-id="5fe66-168">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-168">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>

- <span data-ttu-id="5fe66-169">[How to: Create a C/C++ Union by Using Attributes (Visual Basic)](how-to-create-a-c-cpp-union-by-using-attributes.md) (Практическое руководство. Создание объединения C/C++ с помощью атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-169">[How to: Create a C/C++ Union by Using Attributes (Visual Basic)](how-to-create-a-c-cpp-union-by-using-attributes.md)</span></span>

- <span data-ttu-id="5fe66-170">[Common Attributes (Visual Basic)](common-attributes.md) (Распространенные атрибуты (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-170">[Common Attributes (Visual Basic)](common-attributes.md)</span></span>

- <span data-ttu-id="5fe66-171">[Caller Information (Visual Basic)](../caller-information.md) (Сведения о вызывающем (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-171">[Caller Information (Visual Basic)](../caller-information.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="5fe66-172">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5fe66-172">See also</span></span>

- [<span data-ttu-id="5fe66-173">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fe66-173">Visual Basic Programming Guide</span></span>](../../index.md)
- <span data-ttu-id="5fe66-174">[Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fe66-174">[Reflection (Visual Basic)](../reflection.md)</span></span>
- [<span data-ttu-id="5fe66-175">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5fe66-175">Attributes</span></span>](../../../../standard/attributes/index.md)
