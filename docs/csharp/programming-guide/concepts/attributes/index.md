---
title: Атрибуты (C#)
description: Узнайте, как использовать атрибуты для связывания метаданных или декларативных сведений с кодом в C#. Атрибут можно запрашивать во время выполнения с помощью отражения.
ms.date: 04/26/2018
ms.openlocfilehash: 4c85e36a36cbaa16ab8d1344237e5d685ffd60d9
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740375"
---
# <a name="attributes-c"></a><span data-ttu-id="dac34-104">Атрибуты (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-104">Attributes (C#)</span></span>

<span data-ttu-id="dac34-105">Атрибуты предоставляют мощное средство для связывания метаданных или декларативной информации с кодом (сборки, типы, методы, свойства и т. д.).</span><span class="sxs-lookup"><span data-stu-id="dac34-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="dac34-106">Связав атрибут связан с сущностью программы, вы можете проверять этот атрибут во время выполнения, используя технику *отражения*.</span><span class="sxs-lookup"><span data-stu-id="dac34-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="dac34-107">Подробнее см. в разделе [Отражение (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="dac34-108">Атрибуты имеют следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="dac34-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="dac34-109">Атрибуты добавляют в программу метаданные.</span><span class="sxs-lookup"><span data-stu-id="dac34-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="dac34-110">*Метаданные* — это сведения о типах, определенных в программе.</span><span class="sxs-lookup"><span data-stu-id="dac34-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="dac34-111">Все сборки .NET содержат некоторый набор метаданных, описывающих типы и члены типов, определенные в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="dac34-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="dac34-112">Вы можете добавить пользовательские атрибуты, чтобы указать любую дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="dac34-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="dac34-113">Подробнее см. в разделе [Создание настраиваемых атрибутов (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="dac34-114">Вы можете применить один или несколько атрибутов ко всей сборке, к модулю или к более мелким элементам программы, например к классам и свойствам.</span><span class="sxs-lookup"><span data-stu-id="dac34-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="dac34-115">Атрибуты могут принимать аргументы, так же как методы и свойства.</span><span class="sxs-lookup"><span data-stu-id="dac34-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="dac34-116">Программа может проверить собственные метаданные или метаданные в других программах, используя отражение.</span><span class="sxs-lookup"><span data-stu-id="dac34-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="dac34-117">Дополнительные сведения см. в разделе [Обращение к атрибутам с помощью отражения (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="dac34-118">Использование атрибутов</span><span class="sxs-lookup"><span data-stu-id="dac34-118">Using attributes</span></span>

<span data-ttu-id="dac34-119">Атрибуты можно использовать почти в любых объявлениях, но для каждого атрибута можно ограничить типы объявлений, в которых он является допустимым.</span><span class="sxs-lookup"><span data-stu-id="dac34-119">Attributes can be placed on almost any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="dac34-120">Чтобы указать атрибут на C#, поместите имя атрибута в квадратных скобках ([]) над объявлением сущности, к которой он применяется.</span><span class="sxs-lookup"><span data-stu-id="dac34-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="dac34-121">В этом примере атрибут <xref:System.SerializableAttribute> используется для применения определенной характеристики к классу:</span><span class="sxs-lookup"><span data-stu-id="dac34-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="dac34-122">Метод с атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute> объявляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dac34-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="dac34-123">В объявлении можно разместить несколько атрибутов, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="dac34-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="dac34-124">Некоторые атрибуты можно указать для одной сущности более одного раза.</span><span class="sxs-lookup"><span data-stu-id="dac34-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="dac34-125">Пример такого многократно используемого атрибута — <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="dac34-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="dac34-126">По соглашению все имена атрибутов заканчиваются словом Attribute, чтобы отличать их от других элементов библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="dac34-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="dac34-127">Но при использовании атрибута в коде этот суффикс можно не указывать.</span><span class="sxs-lookup"><span data-stu-id="dac34-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="dac34-128">Например, обращение `[DllImport]` эквивалентно `[DllImportAttribute]`, хотя в библиотеке классов .NET этот атрибут имеет имя `DllImportAttribute`.</span><span class="sxs-lookup"><span data-stu-id="dac34-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="dac34-129">Параметры атрибутов</span><span class="sxs-lookup"><span data-stu-id="dac34-129">Attribute parameters</span></span>

<span data-ttu-id="dac34-130">Многие атрибуты имеют параметры, которые могут быть позиционными, неименованными или именованными.</span><span class="sxs-lookup"><span data-stu-id="dac34-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="dac34-131">Позиционные параметры должны указываться в определенном порядке и не могут опускаться.</span><span class="sxs-lookup"><span data-stu-id="dac34-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="dac34-132">Именованные параметры являются необязательными и могут указываться в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="dac34-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="dac34-133">Сначала указываются позиционные параметры.</span><span class="sxs-lookup"><span data-stu-id="dac34-133">Positional parameters are specified first.</span></span> <span data-ttu-id="dac34-134">Например, эти три атрибута являются эквивалентными:</span><span class="sxs-lookup"><span data-stu-id="dac34-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="dac34-135">Первый параметр (имя библиотеки DLL) является позиционным и всегда располагается первым, остальные параметры являются именованными.</span><span class="sxs-lookup"><span data-stu-id="dac34-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="dac34-136">В этом примере оба именованных параметра имеют значение по умолчанию (false), и мы можем их опустить.</span><span class="sxs-lookup"><span data-stu-id="dac34-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="dac34-137">Позиционные параметры соответствуют параметрам конструктора атрибутов.</span><span class="sxs-lookup"><span data-stu-id="dac34-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="dac34-138">Именованные (или необязательные) параметры соответствуют свойствам или полям атрибута.</span><span class="sxs-lookup"><span data-stu-id="dac34-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="dac34-139">Сведения о значениях параметров по умолчанию указываются в документации по каждому отдельному атрибуту.</span><span class="sxs-lookup"><span data-stu-id="dac34-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

<span data-ttu-id="dac34-140">Дополнительные сведения о разрешенных типах параметров см. в разделе [Атрибуты](~/_csharplang/spec/attributes.md#attribute-parameter-types) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-140">For more information on allowed parameter types, see the [Attributes](~/_csharplang/spec/attributes.md#attribute-parameter-types) section of the [C# language specification](~/_csharplang/spec/introduction.md)</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="dac34-141">Целевые объекты атрибутов</span><span class="sxs-lookup"><span data-stu-id="dac34-141">Attribute targets</span></span>

<span data-ttu-id="dac34-142">*Целевой объект* атрибута — это сущность, к которой применяется атрибут.</span><span class="sxs-lookup"><span data-stu-id="dac34-142">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="dac34-143">Например, атрибут можно применить к классу, отдельному методу или ко всей сборке.</span><span class="sxs-lookup"><span data-stu-id="dac34-143">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="dac34-144">По умолчанию атрибут применяется к тому элементу, который следует за ним.</span><span class="sxs-lookup"><span data-stu-id="dac34-144">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="dac34-145">Но у вас есть возможность явным образом указать, например, что атрибут применяется к методу, параметру или возвращаемому значению.</span><span class="sxs-lookup"><span data-stu-id="dac34-145">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="dac34-146">Чтобы явным образом определить целевой объект атрибута, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="dac34-146">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="dac34-147">Возможные значения `target` перечислены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="dac34-147">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="dac34-148">Целевое значение</span><span class="sxs-lookup"><span data-stu-id="dac34-148">Target value</span></span>|<span data-ttu-id="dac34-149">Применение</span><span class="sxs-lookup"><span data-stu-id="dac34-149">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="dac34-150">Вся сборка</span><span class="sxs-lookup"><span data-stu-id="dac34-150">Entire assembly</span></span>|
|`module`|<span data-ttu-id="dac34-151">Модуль текущей сборки</span><span class="sxs-lookup"><span data-stu-id="dac34-151">Current assembly module</span></span>|
|`field`|<span data-ttu-id="dac34-152">Поле в классе или структуре</span><span class="sxs-lookup"><span data-stu-id="dac34-152">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="dac34-153">событие</span><span class="sxs-lookup"><span data-stu-id="dac34-153">Event</span></span>|
|`method`|<span data-ttu-id="dac34-154">Метод либо методы доступа к свойствам `get` и `set`</span><span class="sxs-lookup"><span data-stu-id="dac34-154">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="dac34-155">Параметры метода или параметры метода доступа `set`</span><span class="sxs-lookup"><span data-stu-id="dac34-155">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="dac34-156">Свойство.</span><span class="sxs-lookup"><span data-stu-id="dac34-156">Property</span></span>|
|`return`|<span data-ttu-id="dac34-157">Возвращаемое значение метода, индексатора свойства или метода доступа к свойствам `get`</span><span class="sxs-lookup"><span data-stu-id="dac34-157">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="dac34-158">Структура, класс, интерфейс, перечисление или делегат</span><span class="sxs-lookup"><span data-stu-id="dac34-158">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="dac34-159">Следует указать целевое значение `field`, чтобы применить атрибут к резервной переменной, созданной для [автоматически реализуемого свойства](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-159">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="dac34-160">Следующий пример демонстрирует, как применить атрибуты к сборкам и модулям.</span><span class="sxs-lookup"><span data-stu-id="dac34-160">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="dac34-161">Дополнительные сведения см. в разделе [Общие атрибуты (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-161">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="dac34-162">В следующем примере показано, как применять атрибуты к методам, параметрам и возвращаемым значениям методов в C#.</span><span class="sxs-lookup"><span data-stu-id="dac34-162">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="dac34-163">Вне зависимости от целевых объектов, для которых действует атрибут `ValidatedContract`, необходимо задать целевой объект для `return`, даже если атрибут `ValidatedContract` назначен только возвращаемым значениям.</span><span class="sxs-lookup"><span data-stu-id="dac34-163">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="dac34-164">Другими словами, компилятор не будет использовать сведения `AttributeUsage` для разрешения конфликтов между неоднозначными целевыми объектами атрибута.</span><span class="sxs-lookup"><span data-stu-id="dac34-164">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="dac34-165">Подробнее см. в разделе [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="dac34-165">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="dac34-166">Популярные методы применения атрибутов</span><span class="sxs-lookup"><span data-stu-id="dac34-166">Common uses for attributes</span></span>

<span data-ttu-id="dac34-167">В следующем списке перечислены несколько распространенных применений для атрибутов.</span><span class="sxs-lookup"><span data-stu-id="dac34-167">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="dac34-168">Указание для методов в веб-службах атрибута `WebMethod`, который обозначает, что метод должен вызываться по протоколу SOAP.</span><span class="sxs-lookup"><span data-stu-id="dac34-168">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="dac34-169">Для получения дополнительной информации см. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dac34-169">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="dac34-170">Описание способов упаковки параметров методов при взаимодействии с машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="dac34-170">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="dac34-171">Для получения дополнительной информации см. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dac34-171">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="dac34-172">Описание свойств COM для классов, методов и интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="dac34-172">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="dac34-173">Вызов неуправляемого кода с помощью класса <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dac34-173">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="dac34-174">Указание для сборки таких параметров, как заголовок, версия, описание или товарный знак.</span><span class="sxs-lookup"><span data-stu-id="dac34-174">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="dac34-175">Указание членов класса, которые будут сериализованы при сохранении класса.</span><span class="sxs-lookup"><span data-stu-id="dac34-175">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="dac34-176">Описание правил сопоставления членов класса с XML-узлами при XML-сериализации.</span><span class="sxs-lookup"><span data-stu-id="dac34-176">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="dac34-177">Описание требований безопасности для методов.</span><span class="sxs-lookup"><span data-stu-id="dac34-177">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="dac34-178">Указание характеристик, используемых для обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="dac34-178">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="dac34-179">Управление оптимизацией для JIT-компилятора, сохраняя при этом простоту отладки кода.</span><span class="sxs-lookup"><span data-stu-id="dac34-179">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="dac34-180">Получение сведений об объекте, вызывающем метод.</span><span class="sxs-lookup"><span data-stu-id="dac34-180">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="dac34-181">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="dac34-181">Related sections</span></span>

<span data-ttu-id="dac34-182">Дополнительные сведения можно найти в разделе</span><span class="sxs-lookup"><span data-stu-id="dac34-182">For more information, see:</span></span>

- [<span data-ttu-id="dac34-183">Создание настраиваемых атрибутов (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-183">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="dac34-184">Обращение к атрибутам с помощью отражения (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-184">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="dac34-185">Практическое руководство. Создание объединения C/C++ с помощью атрибутов (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-185">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="dac34-186">Общие атрибуты (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-186">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="dac34-187">Сведения о вызывающем объекте (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-187">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="dac34-188">См. также</span><span class="sxs-lookup"><span data-stu-id="dac34-188">See also</span></span>

- [<span data-ttu-id="dac34-189">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="dac34-189">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="dac34-190">Отражение (C#)</span><span class="sxs-lookup"><span data-stu-id="dac34-190">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="dac34-191">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="dac34-191">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="dac34-192">Использование атрибутов в C#</span><span class="sxs-lookup"><span data-stu-id="dac34-192">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
