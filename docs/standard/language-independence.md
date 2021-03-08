---
title: Независимость от языка и независимые от языка компоненты
description: Сведения о том, как можно вести разработку на одном из множества языков, поддерживаемых в .NET, например C#, C++/CLI, F#, IronPython, VB, Visual COBOL и PowerShell.
dev_langs:
- csharp
- vb
ms.date: 07/22/2016
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 0cd8179de929ea55212d600844e658d6946861ab
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103079"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="1f2e3-103">Независимость от языка и независимые от языка компоненты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-103">Language independence and language-independent components</span></span>

<span data-ttu-id="1f2e3-104">.NET является независимой от языка.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-104">.NET is language independent.</span></span> <span data-ttu-id="1f2e3-105">Это означает, что вести разработку можно на одном из множества языков, предназначенных для реализаций .NET, например C#, F# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="1f2e3-106">Чтобы использовать типы и члены библиотек классов, разработанных для реализаций .NET, не требуется знать их исходный язык и следовать его правилам.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="1f2e3-107">Если вы разрабатываете компоненты, они будут доступны всем приложениям .NET вне зависимости от используемого вами языка.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-107">If you're a component developer, your component can be accessed by any .NET app, regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e3-108">В первой части этой статьи рассматривается, как создать компоненты, независимые от языка, чтобы использовать их в приложениях, написанных на любом языке.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-108">This first part of this article discusses creating language-independent components, that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="1f2e3-109">Кроме того, компонент и приложение могут состоять из фрагментов кода на разных языках. См. раздел [Взаимная совместимость кодов на разных языках](#cross-language-interoperability) во второй части этой статьи.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="1f2e3-110">Чтобы обеспечить полное взаимодействие между объектами вне зависимости от их языка, объекты должны предоставлять вызывающим объектам возможности, общие для всех языков.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="1f2e3-111">Этот общий набор компонентов определяется общеязыковой спецификацией (спецификацией CLS) — рядом правил, который применяется к создаваемым сборкам.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="1f2e3-112">Спецификация CLS определяется в разделе I, пп. 7–11, [стандарт ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span></span>

<span data-ttu-id="1f2e3-113">Если компонент соответствует спецификации CLS, к нему можно обращаться из кода сборок, написанных на любом языке программирования, поддерживающем CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="1f2e3-114">Чтобы проверить, является ли компонент CLS-совместимым, примените к исходному коду атрибут [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="1f2e3-115">Дополнительные сведения см. в разделе [Атрибут CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-115">For more information, see [The CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

## <a name="cls-compliance-rules"></a><span data-ttu-id="1f2e3-116">Правила CLS-совместимости</span><span class="sxs-lookup"><span data-stu-id="1f2e3-116">CLS compliance rules</span></span>

<span data-ttu-id="1f2e3-117">В этом разделе рассматриваются правила создания CLS-совместимого компонента.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-117">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="1f2e3-118">Полный список правил см. в разделе I, п. 11, [стандарта ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-118">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e3-119">Каждое правило CLS-совместимости спецификации CLS определяет требования к потребителям (разработчикам, которые программным образом обращаются к CLS-совместимому компоненту), платформам (разработчикам, которые используют компилятор языка для создания CLS-совместимых библиотек) и расширителям (разработчикам инструментов — например, компиляторов языка или синтаксических анализаторов кода, создающих CLS-совместимые компоненты).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-119">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="1f2e3-120">В этой статье описываются требования к платформам.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-120">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="1f2e3-121">Однако следует принимать во внимание, что некоторые правила в отношении расширителей могут также применяться к сборкам, создаваемым с помощью [Reflection.Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-121">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="1f2e3-122">Чтобы создать компонент, независимый от языка, достаточно применить правила CLS-совместимости к открытому интерфейсу компонента.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-122">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="1f2e3-123">Закрытая реализация может не соответствовать спецификации.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-123">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f2e3-124">Правила CLS-совместимости применяются только к открытому интерфейсу компонента и не применяются к закрытой реализации.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-124">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="1f2e3-125">Например, за исключением чисел типа [Byte](xref:System.Byte) целые числа без знака не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-125">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-126">В следующем примере класс `Person` предоставляет свойство `Age`, имеющее тип [UInt16](xref:System.UInt16), поэтому в коде отображается предупреждение компилятора.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-126">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="1f2e3-127">Чтобы класс Person удовлетворял требованиям CLS, можно изменить тип свойства `Age` с `UInt16` на [Int16](xref:System.Int16) — 16-битное целое число со знаком, которое является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-127">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="1f2e3-128">Тип закрытого поля `personAge` изменять не требуется.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-128">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="1f2e3-129">Публичный интерфейс библиотеки состоит из:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-129">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="1f2e3-130">определений открытых классов;</span><span class="sxs-lookup"><span data-stu-id="1f2e3-130">Definitions of public classes.</span></span>

* <span data-ttu-id="1f2e3-131">определений открытых членов открытых классов и определений членов, доступных производным классам (т. е. защищенных членов);</span><span class="sxs-lookup"><span data-stu-id="1f2e3-131">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="1f2e3-132">параметров и возвращаемых типов открытых методов открытых классов, а также параметров и возвращаемых типов методов, доступных производным классам.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-132">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="1f2e3-133">В следующей таблице представлены правила CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-133">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="1f2e3-134">Текст правил взят дословно из [стандарт ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/), авторские права: Ecma International, 2012.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-134">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="1f2e3-135">Дополнительные сведения об этих правилах вы найдете в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-135">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="1f2e3-136">Категория</span><span class="sxs-lookup"><span data-stu-id="1f2e3-136">Category</span></span> | <span data-ttu-id="1f2e3-137">См.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-137">See</span></span> | <span data-ttu-id="1f2e3-138">Правило</span><span class="sxs-lookup"><span data-stu-id="1f2e3-138">Rule</span></span> | <span data-ttu-id="1f2e3-139">Номер правила</span><span class="sxs-lookup"><span data-stu-id="1f2e3-139">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="1f2e3-140">Специальные возможности</span><span class="sxs-lookup"><span data-stu-id="1f2e3-140">Accessibility</span></span> | [<span data-ttu-id="1f2e3-141">Доступность членов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-141">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="1f2e3-142">При переопределении унаследованных методов не должна изменяться доступность. Исключение составляют методы, унаследованные из другой сборки с доступностью `family-or-assembly`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-142">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="1f2e3-143">В таких случаях переопределенный метод должен иметь доступность `family`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-143">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="1f2e3-144">10</span><span class="sxs-lookup"><span data-stu-id="1f2e3-144">10</span></span>
<span data-ttu-id="1f2e3-145">Специальные возможности</span><span class="sxs-lookup"><span data-stu-id="1f2e3-145">Accessibility</span></span> | [<span data-ttu-id="1f2e3-146">Доступность членов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-146">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="1f2e3-147">Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-147">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="1f2e3-148">Например, открытый метод, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-148">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="1f2e3-149">Видимость и доступность типов, составляющих экземпляры универсального типа, используемого в сигнатуре любого члена, должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-149">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="1f2e3-150">Например, экземпляр универсального типа в сигнатуре члена, видимого вне его сборки, не должен иметь универсальных аргументов, тип которых видимы только в пределах сборки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-150">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="1f2e3-151">12</span><span class="sxs-lookup"><span data-stu-id="1f2e3-151">12</span></span>
<span data-ttu-id="1f2e3-152">Массивы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-152">Arrays</span></span> | [<span data-ttu-id="1f2e3-153">Массивы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-153">Arrays</span></span>](#arrays) | <span data-ttu-id="1f2e3-154">Элементы массива должны быть CLS-совместимого типа, а измерения массива — иметь нижнюю границу, равную нулю.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-154">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="1f2e3-155">Для различения перегрузок достаточно, чтобы элемент был массивом и у него был задан тип элементов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-155">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="1f2e3-156">Если перегрузка основана на нескольких типах массивов, типы элементов должны быть именованными.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-156">When overloading is based on two or more array types, the element types shall be named types.</span></span> | <span data-ttu-id="1f2e3-157">16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-157">16</span></span>
<span data-ttu-id="1f2e3-158">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-158">Attributes</span></span> | [<span data-ttu-id="1f2e3-159">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-159">Attributes</span></span>](#attributes) | <span data-ttu-id="1f2e3-160">Атрибуты должны иметь тип [System.Attribute](xref:System.Attribute) или унаследованный от него.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-160">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="1f2e3-161">41</span><span class="sxs-lookup"><span data-stu-id="1f2e3-161">41</span></span>
<span data-ttu-id="1f2e3-162">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-162">Attributes</span></span> | [<span data-ttu-id="1f2e3-163">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-163">Attributes</span></span>](#attributes) | <span data-ttu-id="1f2e3-164">В спецификации CLS разрешено только подмножество кодировок настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-164">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="1f2e3-165">Единственными типами, которые должны иметь эти кодировки (см. раздел IV), являются: [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double) и любой тип перечисления на основе CLS-совместимого базового целочисленного типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-165">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="1f2e3-166">34</span><span class="sxs-lookup"><span data-stu-id="1f2e3-166">34</span></span>
<span data-ttu-id="1f2e3-167">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-167">Attributes</span></span> | [<span data-ttu-id="1f2e3-168">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-168">Attributes</span></span>](#attributes) | <span data-ttu-id="1f2e3-169">В спецификации CLS запрещены публично видимые обязательные модификаторы (`modreq`, см. раздел II), но разрешены необязательные модификаторы (`modopt`, см. раздел II), которые не распознаются.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-169">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="1f2e3-170">35</span><span class="sxs-lookup"><span data-stu-id="1f2e3-170">35</span></span>
<span data-ttu-id="1f2e3-171">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-171">Constructors</span></span> | [<span data-ttu-id="1f2e3-172">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-172">Constructors</span></span>](#constructors) | <span data-ttu-id="1f2e3-173">Доступ к данным унаследованного экземпляра возможен после того, как конструктор объекта вызвал какой-либо конструктор экземпляра базового класса.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-173">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="1f2e3-174">(Правило не относится к типам значений, которым не требуются конструкторы).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-174">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="1f2e3-175">21</span><span class="sxs-lookup"><span data-stu-id="1f2e3-175">21</span></span>
<span data-ttu-id="1f2e3-176">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-176">Constructors</span></span> | [<span data-ttu-id="1f2e3-177">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-177">Constructors</span></span>](#constructors) | <span data-ttu-id="1f2e3-178">Конструктор объекта должен вызываться только в ходе создания объекта и объекты не должны инициализироваться дважды.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-178">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="1f2e3-179">22</span><span class="sxs-lookup"><span data-stu-id="1f2e3-179">22</span></span>
<span data-ttu-id="1f2e3-180">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-180">Enumerations</span></span> | [<span data-ttu-id="1f2e3-181">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-181">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f2e3-182">Базовый тип перечисления должен быть встроенным целочисленным типом CLS, имя поля должно быть"value__" и это поле должно быть отмечено атрибутом `RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-182">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="1f2e3-183">7</span><span class="sxs-lookup"><span data-stu-id="1f2e3-183">7</span></span>
<span data-ttu-id="1f2e3-184">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-184">Enumerations</span></span> | [<span data-ttu-id="1f2e3-185">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-185">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f2e3-186">Существует два вида перечислений, которые различаются наличием/отсутствием настраиваемого атрибута [System.FlagsAttribute](xref:System.FlagsAttribute) (см. раздел IV библиотеки).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-186">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="1f2e3-187">Одно представляет именованные целочисленные значения, другое — именованные битовые флаги, сочетая которые, можно создавать значения без имени.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-187">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="1f2e3-188">Перечисление `enum` может принимать и другие значения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-188">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="1f2e3-189">8</span><span class="sxs-lookup"><span data-stu-id="1f2e3-189">8</span></span>
<span data-ttu-id="1f2e3-190">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-190">Enumerations</span></span> | [<span data-ttu-id="1f2e3-191">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-191">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f2e3-192">Статические поля литералов перечисления должны иметь тип перечисления.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-192">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="1f2e3-193">9</span><span class="sxs-lookup"><span data-stu-id="1f2e3-193">9</span></span>
<span data-ttu-id="1f2e3-194">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-194">Events</span></span> | [<span data-ttu-id="1f2e3-195">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-195">Events</span></span>](#events) | <span data-ttu-id="1f2e3-196">Реализующие событие методы должны быть отмечены в метаданных атрибутом `SpecialName`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-196">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="1f2e3-197">29</span><span class="sxs-lookup"><span data-stu-id="1f2e3-197">29</span></span>
<span data-ttu-id="1f2e3-198">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-198">Events</span></span> | [<span data-ttu-id="1f2e3-199">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-199">Events</span></span>](#events) | <span data-ttu-id="1f2e3-200">Событие и его методы доступа должны иметь одинаковую доступность.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-200">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="1f2e3-201">30</span><span class="sxs-lookup"><span data-stu-id="1f2e3-201">30</span></span>
<span data-ttu-id="1f2e3-202">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-202">Events</span></span> | [<span data-ttu-id="1f2e3-203">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-203">Events</span></span>](#events) | <span data-ttu-id="1f2e3-204">У события должны либо присутствовать, либо отсутствовать оба метода `add` и `remove`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-204">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="1f2e3-205">31</span><span class="sxs-lookup"><span data-stu-id="1f2e3-205">31</span></span>
<span data-ttu-id="1f2e3-206">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-206">Events</span></span> | [<span data-ttu-id="1f2e3-207">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-207">Events</span></span>](#events) | <span data-ttu-id="1f2e3-208">Методы `add` и `remove` для события должны иметь один параметр, тип которого определяет тип события. Тип параметра должен быть производным от [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-208">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="1f2e3-209">32</span><span class="sxs-lookup"><span data-stu-id="1f2e3-209">32</span></span>
<span data-ttu-id="1f2e3-210">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-210">Events</span></span> | [<span data-ttu-id="1f2e3-211">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-211">Events</span></span>](#events) | <span data-ttu-id="1f2e3-212">События должны следовать определенному шаблону именования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-212">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="1f2e3-213">Атрибут SpecialName, упоминаемый в правиле 29 спецификации CLS, должен игнорироваться в конкретных сравнениях имен и соответствовать правилам в отношении идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-213">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="1f2e3-214">33</span><span class="sxs-lookup"><span data-stu-id="1f2e3-214">33</span></span>
<span data-ttu-id="1f2e3-215">Исключения</span><span class="sxs-lookup"><span data-stu-id="1f2e3-215">Exceptions</span></span> | [<span data-ttu-id="1f2e3-216">Исключения</span><span class="sxs-lookup"><span data-stu-id="1f2e3-216">Exceptions</span></span>](#exceptions) | <span data-ttu-id="1f2e3-217">Объекты исключений должны иметь тип [System.Exception](xref:System.Exception) или унаследованный от него тип.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-217">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="1f2e3-218">Однако не требуется, чтобы CLS-совместимые методы блокировали распространение других типов исключений.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-218">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="1f2e3-219">40</span><span class="sxs-lookup"><span data-stu-id="1f2e3-219">40</span></span>
<span data-ttu-id="1f2e3-220">Общее</span><span class="sxs-lookup"><span data-stu-id="1f2e3-220">General</span></span> | [<span data-ttu-id="1f2e3-221">Правила CLS-совместимости</span><span class="sxs-lookup"><span data-stu-id="1f2e3-221">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="1f2e3-222">Правила CLS-совместимости применяются только к тем составляющим типа, которые доступны или видны за пределами определяющей сборки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-222">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="1f2e3-223">1</span><span class="sxs-lookup"><span data-stu-id="1f2e3-223">1</span></span>
<span data-ttu-id="1f2e3-224">Общее</span><span class="sxs-lookup"><span data-stu-id="1f2e3-224">General</span></span> | [<span data-ttu-id="1f2e3-225">Правила CLS-совместимости</span><span class="sxs-lookup"><span data-stu-id="1f2e3-225">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="1f2e3-226">Члены типов, не соответствующих правилам CLS-совместимости, не должны быть отмечены как CLS-совместимые.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-226">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-227">2</span><span class="sxs-lookup"><span data-stu-id="1f2e3-227">2</span></span>
<span data-ttu-id="1f2e3-228">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-228">Generics</span></span> | [<span data-ttu-id="1f2e3-229">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-229">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-230">У вложенного типа должно не меньше универсальных параметров, чем у включающего его типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-230">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="1f2e3-231">Универсальные параметры вложенного типа соответствуют по позиции универсальным параметрам включающего типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-231">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="1f2e3-232">42</span><span class="sxs-lookup"><span data-stu-id="1f2e3-232">42</span></span>
<span data-ttu-id="1f2e3-233">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-233">Generics</span></span> | [<span data-ttu-id="1f2e3-234">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-234">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-235">В имени универсального типа должны кодироваться все параметры типа, объявленные в невложенном типе или введенные во вложенном типе, в соответствии с определенными выше правилами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-235">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="1f2e3-236">43</span><span class="sxs-lookup"><span data-stu-id="1f2e3-236">43</span></span>
<span data-ttu-id="1f2e3-237">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-237">Generics</span></span> | [<span data-ttu-id="1f2e3-238">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-238">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-239">В универсальном типе должны повторно объявляться ограничения, обеспечивающие соответствие всем ограничениям базового типа и интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-239">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="1f2e3-240">44</span><span class="sxs-lookup"><span data-stu-id="1f2e3-240">44</span></span>
<span data-ttu-id="1f2e3-241">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-241">Generics</span></span> | [<span data-ttu-id="1f2e3-242">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-242">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-243">Типы, используемые в качестве ограничений универсальных параметров, должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-243">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-244">45</span><span class="sxs-lookup"><span data-stu-id="1f2e3-244">45</span></span>
<span data-ttu-id="1f2e3-245">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-245">Generics</span></span> | [<span data-ttu-id="1f2e3-246">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-246">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-247">Реализация видимости и доступности членов (включая вложенные типы) в экземплярах универсального типа должна ограничиваться областью конкретного экземпляра, а не объявлением универсального типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-247">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="1f2e3-248">С учетом этого также применяется правило 12 CLS-совместимости, касающееся видимости и доступности.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-248">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="1f2e3-249">46</span><span class="sxs-lookup"><span data-stu-id="1f2e3-249">46</span></span>
<span data-ttu-id="1f2e3-250">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="1f2e3-250">Generics</span></span> | [<span data-ttu-id="1f2e3-251">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-251">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f2e3-252">Каждый абстрактный или виртуальный универсальный метод должен иметь конкретную (не абстрактную) реализацию по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-252">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="1f2e3-253">47</span><span class="sxs-lookup"><span data-stu-id="1f2e3-253">47</span></span>
<span data-ttu-id="1f2e3-254">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-254">Interfaces</span></span> | [<span data-ttu-id="1f2e3-255">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-255">Interfaces</span></span>](#interfaces) | <span data-ttu-id="1f2e3-256">CLS-совместимые интерфейсы должны реализовываться без методов, не соответствующих правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-256">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="1f2e3-257">18</span><span class="sxs-lookup"><span data-stu-id="1f2e3-257">18</span></span>
<span data-ttu-id="1f2e3-258">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-258">Interfaces</span></span> | [<span data-ttu-id="1f2e3-259">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-259">Interfaces</span></span>](#interfaces) | <span data-ttu-id="1f2e3-260">CLS-совместимые интерфейсы не могут определять статические методы и поля.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-260">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="1f2e3-261">19</span><span class="sxs-lookup"><span data-stu-id="1f2e3-261">19</span></span>
<span data-ttu-id="1f2e3-262">Участники</span><span class="sxs-lookup"><span data-stu-id="1f2e3-262">Members</span></span> | [<span data-ttu-id="1f2e3-263">Обзор членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-263">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="1f2e3-264">Глобальные статические (static) поля и методы не совместимы с CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-264">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-265">36</span><span class="sxs-lookup"><span data-stu-id="1f2e3-265">36</span></span>
<span data-ttu-id="1f2e3-266">Участники</span><span class="sxs-lookup"><span data-stu-id="1f2e3-266">Members</span></span> | -- | <span data-ttu-id="1f2e3-267">Значение статического поля литерала задается с помощью метаданных инициализации поля.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-267">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="1f2e3-268">У CLS-совместимого литерала тип значения должен совпадать с типом литерала (или базовым типом, если литерал — перечисление `enum`).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-268">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="1f2e3-269">13</span><span class="sxs-lookup"><span data-stu-id="1f2e3-269">13</span></span>
<span data-ttu-id="1f2e3-270">Участники</span><span class="sxs-lookup"><span data-stu-id="1f2e3-270">Members</span></span> | [<span data-ttu-id="1f2e3-271">Обзор членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-271">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="1f2e3-272">Ограничение vararg не входит в спецификацию CLS. В спецификации поддерживается только стандартное соглашение об управляемых вызовах.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-272">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="1f2e3-273">15</span><span class="sxs-lookup"><span data-stu-id="1f2e3-273">15</span></span>
<span data-ttu-id="1f2e3-274">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="1f2e3-274">Naming conventions</span></span> | [<span data-ttu-id="1f2e3-275">Соглашения об именовании</span><span class="sxs-lookup"><span data-stu-id="1f2e3-275">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f2e3-276">Допустимые в сборках открывающие и внутренние символы идентификаторов указаны в приложении 7 технического отчета 15 стандарта Юникода версии 3.0. См. [формы нормализации Юникода](https://unicode.org/reports/tr15/).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-276">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="1f2e3-277">Идентификаторы должны иметь канонический формат, описанный в форме нормализации Юникода C. В рамках спецификации CLS два идентификатора считаются одинаковыми, если их записи в нижнем регистре совпадают (т. е. при взаимно-однозначном сопоставлении символов Юникода нижнего регистра без учета языкового стандарта).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-277">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="1f2e3-278">Таким образом, в рамках спецификации CLS отличия регистра недостаточно для различения идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-278">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="1f2e3-279">Однако чтобы переопределить наследуемое определение, требуется использовать точную кодировку исходного объявления.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-279">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="1f2e3-280">4</span><span class="sxs-lookup"><span data-stu-id="1f2e3-280">4</span></span>
<span data-ttu-id="1f2e3-281">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1f2e3-281">Overloading</span></span> | [<span data-ttu-id="1f2e3-282">Соглашения об именовании</span><span class="sxs-lookup"><span data-stu-id="1f2e3-282">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f2e3-283">Все имена, которые вводятся в CLS-совместимой области, должны быть различными независимо от типа, кроме случаев, когда имена одинаковы и разрешаются посредством перегрузки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-283">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="1f2e3-284">Другими словами, в системе общих типов CTS разрешено давать одинаковое имя методу и полю, а в спецификации CLS — нет.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-284">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="1f2e3-285">5</span><span class="sxs-lookup"><span data-stu-id="1f2e3-285">5</span></span>
<span data-ttu-id="1f2e3-286">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1f2e3-286">Overloading</span></span> | [<span data-ttu-id="1f2e3-287">Соглашения об именовании</span><span class="sxs-lookup"><span data-stu-id="1f2e3-287">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f2e3-288">Поля и вложенные типы должны отличаться только идентификаторами, хотя в системе общих типов CTS могут отличаться сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-288">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="1f2e3-289">Методы, свойства и события с одинаковыми именами (при сравнении идентификаторов) должны отличаться не только типом возвращаемого значения, за исключением случаев из правила 39 спецификации CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-289">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type, except as specified in CLS Rule 39</span></span> | <span data-ttu-id="1f2e3-290">6</span><span class="sxs-lookup"><span data-stu-id="1f2e3-290">6</span></span>
<span data-ttu-id="1f2e3-291">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1f2e3-291">Overloading</span></span> | [<span data-ttu-id="1f2e3-292">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="1f2e3-292">Overloads</span></span>](#overloads) | <span data-ttu-id="1f2e3-293">Перегружать можно только свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-293">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="1f2e3-294">37</span><span class="sxs-lookup"><span data-stu-id="1f2e3-294">37</span></span>
<span data-ttu-id="1f2e3-295">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1f2e3-295">Overloading</span></span> | [<span data-ttu-id="1f2e3-296">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="1f2e3-296">Overloads</span></span>](#overloads) |<span data-ttu-id="1f2e3-297">Свойства и методы могут перегружаться только на основе количества и типов их параметров, за исключением операторов преобразования `op_Implicit` и `op_Explicit`, которые также могут перегружаться на основе возвращаемого типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-297">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="1f2e3-298">38</span><span class="sxs-lookup"><span data-stu-id="1f2e3-298">38</span></span>
<span data-ttu-id="1f2e3-299">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1f2e3-299">Overloading</span></span> | -- | <span data-ttu-id="1f2e3-300">Если в типе объявлены несколько CLS-совместимых методов с одним и тем же именем и они создают набор экземпляров типа с одинаковыми параметрами и возвращаемыми типами, эти методы должны быть семантически эквивалентны в экземплярах типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-300">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="1f2e3-301">48</span><span class="sxs-lookup"><span data-stu-id="1f2e3-301">48</span></span>
<span data-ttu-id="1f2e3-302">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-302">Properties</span></span> | [<span data-ttu-id="1f2e3-303">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-303">Properties</span></span>](#properties) | <span data-ttu-id="1f2e3-304">Методы, которые реализуют получение и задание значения, должны быть отмечены в метаданных атрибутом `SpecialName`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-304">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="1f2e3-305">24</span><span class="sxs-lookup"><span data-stu-id="1f2e3-305">24</span></span>
<span data-ttu-id="1f2e3-306">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-306">Properties</span></span> | [<span data-ttu-id="1f2e3-307">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-307">Properties</span></span>](#properties) | <span data-ttu-id="1f2e3-308">Все методы доступа свойства должны быть либо одновременно статическими, виртуальными или экземплярами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-308">A property's accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="1f2e3-309">26</span><span class="sxs-lookup"><span data-stu-id="1f2e3-309">26</span></span>
<span data-ttu-id="1f2e3-310">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-310">Properties</span></span> | [<span data-ttu-id="1f2e3-311">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-311">Properties</span></span>](#properties) | <span data-ttu-id="1f2e3-312">Тип свойства, тип возвращаемого значения метода получения значения и тип последнего аргумента метода задания значения должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-312">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="1f2e3-313">Типы параметров свойства, типы параметров метода получения значения и типы параметров метода задания значения (за исключением его последнего параметра) должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-313">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="1f2e3-314">Все типы должны быть CLS-совместимыми и не могут быть управляемыми указателями (т. е. не могут передаваться по ссылке).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-314">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="1f2e3-315">27</span><span class="sxs-lookup"><span data-stu-id="1f2e3-315">27</span></span>
<span data-ttu-id="1f2e3-316">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-316">Properties</span></span> | [<span data-ttu-id="1f2e3-317">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-317">Properties</span></span>](#properties) | <span data-ttu-id="1f2e3-318">Свойства должны следовать определенному шаблону именования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-318">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="1f2e3-319">Атрибут `SpecialName`, упоминаемый в правиле 24 спецификации CLS, должен игнорироваться в соответствующих сравнениях имен и соответствовать правилам в отношении идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-319">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="1f2e3-320">Свойство должно иметь метод получения и/или задания значения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-320">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="1f2e3-321">28</span><span class="sxs-lookup"><span data-stu-id="1f2e3-321">28</span></span>
<span data-ttu-id="1f2e3-322">Преобразование типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-322">Type conversion</span></span> | [<span data-ttu-id="1f2e3-323">Преобразование типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-323">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="1f2e3-324">При наличии оператора преобразования op_Implicit или op_Explicit необходимо предоставить альтернативный способ приведения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-324">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="1f2e3-325">39</span><span class="sxs-lookup"><span data-stu-id="1f2e3-325">39</span></span>
<span data-ttu-id="1f2e3-326">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-326">Types</span></span> | [<span data-ttu-id="1f2e3-327">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-327">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-328">Упакованные типы значений не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-328">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-329">3</span><span class="sxs-lookup"><span data-stu-id="1f2e3-329">3</span></span>
<span data-ttu-id="1f2e3-330">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-330">Types</span></span> | [<span data-ttu-id="1f2e3-331">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-331">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-332">Все типы сигнатуры должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-332">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="1f2e3-333">Все типы, составляющие экземпляры универсального типа, должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-333">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-334">11</span><span class="sxs-lookup"><span data-stu-id="1f2e3-334">11</span></span>
<span data-ttu-id="1f2e3-335">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-335">Types</span></span> | [<span data-ttu-id="1f2e3-336">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-336">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-337">Типизированные ссылки несовместимы с CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-337">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-338">14</span><span class="sxs-lookup"><span data-stu-id="1f2e3-338">14</span></span>
<span data-ttu-id="1f2e3-339">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-339">Types</span></span> | [<span data-ttu-id="1f2e3-340">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-340">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-341">Типы неуправляемых указателей не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-341">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="1f2e3-342">17</span><span class="sxs-lookup"><span data-stu-id="1f2e3-342">17</span></span>
<span data-ttu-id="1f2e3-343">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-343">Types</span></span> | [<span data-ttu-id="1f2e3-344">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-344">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-345">CLS-совместимые классы, типы значений и интерфейсы должны реализовываться без членов, не соответствующих правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-345">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="1f2e3-346">20</span><span class="sxs-lookup"><span data-stu-id="1f2e3-346">20</span></span>
<span data-ttu-id="1f2e3-347">Типы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-347">Types</span></span> | [<span data-ttu-id="1f2e3-348">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-348">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f2e3-349">[System.Object](xref:System.Object) является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-349">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="1f2e3-350">Все другие CLS-совместимые классы должны наследоваться от CLS-совместимого класса.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-350">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="1f2e3-351">23</span><span class="sxs-lookup"><span data-stu-id="1f2e3-351">23</span></span>

<span data-ttu-id="1f2e3-352">Индекс подразделов:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-352">Index to subsections:</span></span>

* [<span data-ttu-id="1f2e3-353">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-353">Types and type member signatures</span></span>](#types-and-type-member-signatures)
* [<span data-ttu-id="1f2e3-354">Соглашения об именовании</span><span class="sxs-lookup"><span data-stu-id="1f2e3-354">Naming conventions</span></span>](#naming-conventions)
* [<span data-ttu-id="1f2e3-355">Преобразование типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-355">Type conversion</span></span>](#type-conversion)
* [<span data-ttu-id="1f2e3-356">Массивы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-356">Arrays</span></span>](#arrays)
* [<span data-ttu-id="1f2e3-357">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-357">Interfaces</span></span>](#interfaces)
* [<span data-ttu-id="1f2e3-358">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-358">Enumerations</span></span>](#enumerations)
* [<span data-ttu-id="1f2e3-359">Обзор членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-359">Type members in general</span></span>](#type-members-in-general)
* [<span data-ttu-id="1f2e3-360">Доступность членов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-360">Member accessibility</span></span>](#member-accessibility)
* [<span data-ttu-id="1f2e3-361">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-361">Generic types and members</span></span>](#generic-types-and-members)
* [<span data-ttu-id="1f2e3-362">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-362">Constructors</span></span>](#constructors)
* [<span data-ttu-id="1f2e3-363">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-363">Properties</span></span>](#properties)
* [<span data-ttu-id="1f2e3-364">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-364">Events</span></span>](#events)
* [<span data-ttu-id="1f2e3-365">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="1f2e3-365">Overloads</span></span>](#overloads)
* [<span data-ttu-id="1f2e3-366">Исключения</span><span class="sxs-lookup"><span data-stu-id="1f2e3-366">Exceptions</span></span>](#exceptions)
* [<span data-ttu-id="1f2e3-367">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-367">Attributes</span></span>](#attributes)

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="1f2e3-368">Сигнатуры типов и членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-368">Types and type member signatures</span></span>

<span data-ttu-id="1f2e3-369">Тип [System.Object](xref:System.Object) является CLS-совместимым. Это базовый тип всех типов объектов в системе типов .NET.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-369">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET type system.</span></span> <span data-ttu-id="1f2e3-370">В платформе .NET существует два вида наследования: неявное (например, класс [String](xref:System.String) неявно наследуется от класса `Object`) или явное (например, класс [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) явно наследуется от класса [ArgumentException](xref:System.ArgumentException), который явно наследуется от класса [Exception](xref:System.Exception)).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-370">Inheritance in .NET is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="1f2e3-371">Чтобы производный тип был CLS-совместимым, его базовый тип должен быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-371">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-372">В следующем примере рассматривается производный тип, базовый тип которого не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-372">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-373">Базовый класс `Counter` использует 32-битное целое число без знака в качестве счетчика.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-373">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="1f2e3-374">Поскольку этот класс реализует функцию счетчика с помощью переноса целого числа без знака, он помечается как не соответствующий правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-374">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="1f2e3-375">Поэтому производный класс `NonZeroCounter` также не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-375">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="1f2e3-376">Все типы в сигнатурах членов, в том числе тип свойства и тип возвращаемого значения метода, должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-376">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="1f2e3-377">Кроме того, в отношении универсальных типов применяются следующие правила:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-377">In addition, for generic types:</span></span>

* <span data-ttu-id="1f2e3-378">все типы, составляющие экземпляры универсального типа, должны быть CLS-совместимыми;</span><span class="sxs-lookup"><span data-stu-id="1f2e3-378">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="1f2e3-379">все типы, используемые в качестве ограничений универсальных параметров, должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-379">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-380">[Система общих типов CTS](common-type-system.md) платформы .NET имеет ряд встроенных типов, которые поддерживаются непосредственно средой CLR и особым образом кодируются в метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-380">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="1f2e3-381">В следующей таблице приводятся встроенные типы, которые являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-381">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-382">CLS-совместимый тип</span><span class="sxs-lookup"><span data-stu-id="1f2e3-382">CLS-compliant type</span></span> | <span data-ttu-id="1f2e3-383">Описание</span><span class="sxs-lookup"><span data-stu-id="1f2e3-383">Description</span></span>
------------------ | -----------
[<span data-ttu-id="1f2e3-384">Byte</span><span class="sxs-lookup"><span data-stu-id="1f2e3-384">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="1f2e3-385">8-битное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="1f2e3-385">8-bit unsigned integer</span></span>
[<span data-ttu-id="1f2e3-386">Int16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-386">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="1f2e3-387">16-битное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="1f2e3-387">16-bit signed integer</span></span>
[<span data-ttu-id="1f2e3-388">Int32</span><span class="sxs-lookup"><span data-stu-id="1f2e3-388">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="1f2e3-389">32-битное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="1f2e3-389">32-bit signed integer</span></span>
[<span data-ttu-id="1f2e3-390">Int64</span><span class="sxs-lookup"><span data-stu-id="1f2e3-390">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="1f2e3-391">64-битное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="1f2e3-391">64-bit signed integer</span></span>
[<span data-ttu-id="1f2e3-392">Single</span><span class="sxs-lookup"><span data-stu-id="1f2e3-392">Single</span></span>](xref:System.Single) | <span data-ttu-id="1f2e3-393">Число одинарной точности с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="1f2e3-393">Single-precision floating-point value</span></span>
[<span data-ttu-id="1f2e3-394">Double</span><span class="sxs-lookup"><span data-stu-id="1f2e3-394">Double</span></span>](xref:System.Double) | <span data-ttu-id="1f2e3-395">Число двойной точности с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="1f2e3-395">Double-precision floating-point value</span></span>
[<span data-ttu-id="1f2e3-396">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f2e3-396">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="1f2e3-397">Тип значения true или false</span><span class="sxs-lookup"><span data-stu-id="1f2e3-397">true or false value type</span></span>
[<span data-ttu-id="1f2e3-398">Char</span><span class="sxs-lookup"><span data-stu-id="1f2e3-398">Char</span></span>](xref:System.Char) | <span data-ttu-id="1f2e3-399">Единица кода в кодировке UTF-16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-399">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="1f2e3-400">Decimal</span><span class="sxs-lookup"><span data-stu-id="1f2e3-400">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="1f2e3-401">Десятичное число без плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="1f2e3-401">Non-floating-point decimal number</span></span>
[<span data-ttu-id="1f2e3-402">IntPtr</span><span class="sxs-lookup"><span data-stu-id="1f2e3-402">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="1f2e3-403">Указатель или дескриптор определяемого платформой размера</span><span class="sxs-lookup"><span data-stu-id="1f2e3-403">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="1f2e3-404">String</span><span class="sxs-lookup"><span data-stu-id="1f2e3-404">String</span></span>](xref:System.String) | <span data-ttu-id="1f2e3-405">Коллекция любого, в том числе нулевого, числа объектов Char</span><span class="sxs-lookup"><span data-stu-id="1f2e3-405">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="1f2e3-406">В следующей таблице приводятся встроенные типы, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-406">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="1f2e3-407">Тип, не являющийся CLS-совместимым</span><span class="sxs-lookup"><span data-stu-id="1f2e3-407">Non-compliant type</span></span> | <span data-ttu-id="1f2e3-408">Описание</span><span class="sxs-lookup"><span data-stu-id="1f2e3-408">Description</span></span> | <span data-ttu-id="1f2e3-409">Альтернативный CLS-совместимый тип</span><span class="sxs-lookup"><span data-stu-id="1f2e3-409">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="1f2e3-410">SByte</span><span class="sxs-lookup"><span data-stu-id="1f2e3-410">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="1f2e3-411">Тип данных — 8-битное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="1f2e3-411">8-bit signed integer data type</span></span> | [<span data-ttu-id="1f2e3-412">Int16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-412">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="1f2e3-413">UInt16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-413">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="1f2e3-414">16-битное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="1f2e3-414">16-bit unsigned integer</span></span> | [<span data-ttu-id="1f2e3-415">Int32</span><span class="sxs-lookup"><span data-stu-id="1f2e3-415">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="1f2e3-416">UInt32</span><span class="sxs-lookup"><span data-stu-id="1f2e3-416">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="1f2e3-417">32-битное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="1f2e3-417">32-bit unsigned integer</span></span> | [<span data-ttu-id="1f2e3-418">Int64</span><span class="sxs-lookup"><span data-stu-id="1f2e3-418">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="1f2e3-419">UInt64</span><span class="sxs-lookup"><span data-stu-id="1f2e3-419">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="1f2e3-420">64-битное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="1f2e3-420">64-bit unsigned integer</span></span> | <span data-ttu-id="1f2e3-421">[Int64](xref:System.Int64) (возможно переполнение), [BigInteger](xref:System.Numerics.BigInteger) или [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="1f2e3-421">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="1f2e3-422">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="1f2e3-422">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="1f2e3-423">Дескриптор или указатель без знака</span><span class="sxs-lookup"><span data-stu-id="1f2e3-423">Unsigned pointer or handle</span></span> | [<span data-ttu-id="1f2e3-424">IntPtr</span><span class="sxs-lookup"><span data-stu-id="1f2e3-424">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="1f2e3-425">В библиотеке классов .NET и других библиотеках классов могут встречаться другие типы, не являющиеся CLS-совместимыми. Например:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-425">The .NET Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="1f2e3-426">Упакованные типы значений.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-426">Boxed value types.</span></span> <span data-ttu-id="1f2e3-427">Следующий пример кода на C# создает класс с открытым свойством `int*` типа `Value`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-427">The following C# example creates a class that has a public property of type `int*` named `Value`.</span></span> <span data-ttu-id="1f2e3-428">Поскольку `int*` — это упакованный тип значений, компилятор помечает, что он не соответствует правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-428">Because an `int*` is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="1f2e3-429">Типизированные ссылки — особые конструкции, содержащие ссылку на объект и ссылку на тип.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-429">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="1f2e3-430">Если тип не является CLS-совместимым, необходимо применить к нему атрибут [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) с параметром *isCompliant*, имеющим значение `false`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-430">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="1f2e3-431">Дополнительные сведения см. в разделе [Атрибут CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-431">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="1f2e3-432">В следующем примере сигнатура метода и экземпляр универсального типа не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-432">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="1f2e3-433">Мы определяем класс `InvoiceItem`, имеющий свойство типа [UInt32](xref:System.UInt32), свойство типа [Nullable(Of UInt32)](xref:System.Nullable%601) и конструктор с параметрами типа `UInt32` и `Nullable(Of UInt32)`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-433">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="1f2e3-434">При компиляции появляются четыре предупреждения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-434">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="1f2e3-435">Они не будут отображаться, если заменить в открытом интерфейсе `InvoiceItem` типы, не соответствующие правилам CLS-совместимости, CLS-совместимыми типами:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-435">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="1f2e3-436">Помимо перечисленных типов существуют и другие категории типов, не являющихся CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-436">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="1f2e3-437">К ним относятся типы неуправляемых указателей и типы указателей функций.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-437">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="1f2e3-438">В следующем примере предупреждение компилятора отображается потому, что для создания массива целых чисел используется указатель на целое число.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-438">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="1f2e3-439">Все члены CLS-совместимых абстрактных классов (т. е. классов, отмеченных атрибутом `abstract` в C#) также должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-439">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="1f2e3-440">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="1f2e3-440">Naming conventions</span></span>

<span data-ttu-id="1f2e3-441">В некоторых языках программирования не учитывается регистр, поэтому идентификаторы (имена пространств имен, типов и членов) должны отличаться не только регистром.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-441">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="1f2e3-442">Два идентификатора считаются одинаковыми, если их записи в нижнем регистре совпадают.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-442">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="1f2e3-443">В следующем примере C# определяются два публичных класса: `Person` и `person`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-443">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="1f2e3-444">Они отличаются только регистром, поэтому компилятор C# помечает, что они не соответствуют правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-444">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="1f2e3-445">Идентификаторы языка программирования — имена пространств имен, типов и членов — должны соответствовать [стандарту Юникода](https://unicode.org/reports/tr15/).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-445">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="1f2e3-446">Это означает следующее.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-446">This means that:</span></span>

* <span data-ttu-id="1f2e3-447">В качестве первого символа идентификатора можно использовать любой символ верхнего или нижнего регистра, символ заголовка, модификатора, букву или цифру Юникода.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-447">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="1f2e3-448">Категории символов Юникода приводятся в описании перечисления [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-448">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="1f2e3-449">Допустимые последующие символы — символы тех же категорий, что и первый, а также несамостоятельные знаки, комбинированные самостоятельные знаки, десятичные числа, соединительные знаки пунктуации и коды форматирования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-449">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuation, and formatting codes.</span></span>

<span data-ttu-id="1f2e3-450">Перед сравнением идентификаторов необходимо отфильтровать коды форматирования и преобразовать идентификаторы в форму нормализации Юникода C, поскольку один символ может быть представлен несколькими единицами кода в кодировке UTF-16.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-450">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="1f2e3-451">Последовательности символов, соответствующие одним и тем же единицам кода в форме нормализации Юникода C, не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-451">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-452">В примере ниже определяется свойство с именем `Å`, представляющим собой символ ангстрема (U+212B), и свойство с именем `Å`, представляющим собой заглавную латинскую букву А с надстрочным кружком (U+00C5).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-452">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å`, which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="1f2e3-453">Компилятор C# помечает, что исходный код не соответствует правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-453">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="1f2e3-454">Имена членов в определенной области (например, имена пространств имен в сборке, типов в пространстве имен или членов типа) должны быть уникальными, за исключением имен, разрешаемых через перегрузку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-454">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="1f2e3-455">Это правило более строгое, чем требования системы общих типов CTS, где члены разных типов (например, метод и поле) могут иметь одинаковые имена в области.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-455">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="1f2e3-456">В частности у членов типов:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-456">In particular, for type members:</span></span>

* <span data-ttu-id="1f2e3-457">поля и вложенные типы различаются только по имени;</span><span class="sxs-lookup"><span data-stu-id="1f2e3-457">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="1f2e3-458">методы, свойства и события с одинаковым именем должны отличаться не только возвращаемым типом.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-458">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="1f2e3-459">Следующий пример иллюстрирует это правило.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-459">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="1f2e3-460">В нем определяется класс `Converter`, содержащий 4 члена с именем `Conversion`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-460">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="1f2e3-461">Три из них — методы, один — свойство.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-461">Three are methods, and one is a property.</span></span> <span data-ttu-id="1f2e3-462">Метод с параметром `Int64` имеет уникальное имя, а два метода с параметром `Int32` — нет, потому что возвращаемое значение не рассматривается как часть сигнатуры члена.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-462">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="1f2e3-463">Свойство `Conversion` также нарушает правило, поскольку имеет то же имя, что и перегруженные методы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-463">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="1f2e3-464">В некоторых языках есть уникальные ключевые слова. В языках, поддерживаемых средой CLR, должен существовать механизм обозначения идентификаторов (например, имен типов), совпадающих с ключевыми словами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-464">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="1f2e3-465">Например, `case` — ключевое слово как в C#, так и в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-465">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="1f2e3-466">В примере кода на Visual Basic неоднозначность между классом с именем `case` и ключевым словом `case` устраняется с помощью парных фигурных скобок.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-466">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="1f2e3-467">Иначе бы код не скомпилировался и появилось бы сообщение об ошибке "Ключевое слово не может использоваться как идентификатор".</span><span class="sxs-lookup"><span data-stu-id="1f2e3-467">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="1f2e3-468">В примере кода на C#, где создается экземпляр класса `case`, неоднозначность между ключевым словом и идентификатором разрешается с помощью символа @.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-468">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="1f2e3-469">Без этого символа компилятор C# выдал бы два сообщения об ошибке: "Требуется тип" и "Недопустимый элемент case".</span><span class="sxs-lookup"><span data-stu-id="1f2e3-469">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="1f2e3-470">Преобразование типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-470">Type conversion</span></span>

<span data-ttu-id="1f2e3-471">В спецификации CLS определены два оператора преобразования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-471">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="1f2e3-472">Для расширяющих преобразований, которые не приводят к потере данных или потере точности, используется оператор `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-472">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="1f2e3-473">Например, структура [Decimal](xref:System.Decimal) включает перегруженный оператор `op_Implicit`, который преобразует значения целочисленных типов и значения [Char](xref:System.Char) в значения `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-473">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="1f2e3-474">Для сужающих преобразований, которые могут привести к потере порядка (преобразование в значение с меньшим диапазоном) или потере точности, используется оператор `op_Explicit`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-474">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="1f2e3-475">Например, структура `Decimal` включает перегруженный оператор `op_Explicit`, который преобразует значения [Double](xref:System.Double) и [Single](xref:System.Single) в значения `Decimal`, а также значения `Decimal` в целочисленные значения и значения `Double`, `Single` и `Char`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-475">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="1f2e3-476">Однако перегружать операторы и определять пользовательские операторы можно не во всех языках.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-476">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="1f2e3-477">При реализации этих операторов преобразования необходимо предоставить альтернативный способ преобразования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-477">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="1f2e3-478">Рекомендуется использовать методы `From`Xxx и `To`Xxx.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-478">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="1f2e3-479">Следующий пример иллюстрирует неявное и явное преобразования, которые являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-479">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="1f2e3-480">В нем создается класс `UDouble`, который представляет число двойной точности с плавающей запятой со знаком.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-480">It creates a `UDouble` class that represents a signed double-precision, floating-point number.</span></span> <span data-ttu-id="1f2e3-481">В нем предусмотрены неявные преобразования `UDouble` в `Double` и явные преобразования `UDouble` в `Single`, `Double` в `UDouble` и `Single` в `UDouble`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-481">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="1f2e3-482">В нем также определен метод `ToDouble` — альтернативный вариант неявного преобразования и методы `ToSingle`, `FromDouble` и `FromSingle` — альтернативные варианты явного преобразования.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-482">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="1f2e3-483">Массивы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-483">Arrays</span></span>

<span data-ttu-id="1f2e3-484">Правила CLS-совместимости для массивов:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-484">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="1f2e3-485">Нижняя граница всех измерений массива должна быть равна нулю.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-485">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="1f2e3-486">В следующем примере создается массив с нижней границей равной единице, т. е. он не соответствует правилам CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-486">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="1f2e3-487">Несмотря на наличие атрибута [CLSCompliantAttribute](xref:System.CLSCompliantAttribute), компилятор не обнаруживает, что возвращаемый методом `Numbers.GetTenPrimes` массив не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-487">Despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="1f2e3-488">Все элементы массива должны состоять из CLS-совместимых типов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-488">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="1f2e3-489">В следующем примере определяются два метода, которые возвращают массивы, не являющиеся CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-489">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="1f2e3-490">Первый возвращает массив значений [UInt32](xref:System.UInt32).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-490">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="1f2e3-491">Второй возвращает массив [Object](xref:System.Object), содержащий значения [Int32](xref:System.Int32) и `UInt32`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-491">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="1f2e3-492">Поскольку тип первого массива — `UInt32`, компилятор сообщает, что он не является CLS-совместимым. Однако он не распознает, что элементы второго массива не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-492">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="1f2e3-493">Перегрузка методов, параметры которых являются массивами, разрешается исходя из предпосылки, что это массивы, и с учетом типа их элементов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-493">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="1f2e3-494">Поэтому следующий перегруженный метод `GetSquares` является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-494">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="1f2e3-495">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-495">Interfaces</span></span>

<span data-ttu-id="1f2e3-496">CLS-совместимый интерфейс может определять свойства, события и виртуальные методы (методы без реализации).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-496">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="1f2e3-497">Он не может содержать:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-497">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="1f2e3-498">Статические методы или статические поля.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-498">Static methods or static fields.</span></span> <span data-ttu-id="1f2e3-499">Компилятор C# выдает ошибки, если вы определили в интерфейсе статический член.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-499">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="1f2e3-500">Поля.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-500">Fields.</span></span> <span data-ttu-id="1f2e3-501">Компилятор C# выдает ошибки, если вы определили в интерфейсе поле.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-501">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="1f2e3-502">Методы, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-502">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-503">Например, в следующем определении интерфейса есть метод `INumber.GetUnsigned`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-503">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="1f2e3-504">Компилятор выдает предупреждение о том, что он не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-504">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="1f2e3-505">Вследствие этого правила не требуется, чтобы CLS-совместимые типы реализовывали члены, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-505">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="1f2e3-506">Если CLS-совместимая платформа предоставляет класс, реализующий интерфейс, который не является CLS-совместимым, в ней должны быть определены конкретные реализации всех членов, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-506">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="1f2e3-507">Кроме того, CLS-совместимые языковые компиляторы должны разрешать классам иметь отдельные реализации членов с одинаковыми именами и сигнатурами в нескольких интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-507">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="1f2e3-508">Язык C# поддерживает явные реализации интерфейса, с помощью которых можно определить разные реализации методов с одинаковыми именами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-508">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="1f2e3-509">Этот сценарий представлен в следующем примере, где определяется класс `Temperature`, который явно реализует интерфейсы `ICelsius` и `IFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-509">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="1f2e3-510">Перечисления</span><span class="sxs-lookup"><span data-stu-id="1f2e3-510">Enumerations</span></span>

<span data-ttu-id="1f2e3-511">Правила CLS-совместимости для перечислений:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-511">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="1f2e3-512">Базовый тип перечисления должен быть CLS-совместимым встроенным целочисленным типом ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32) или [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-512">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="1f2e3-513">Например, при определении перечисления с базовым типом [UInt32](xref:System.UInt32) компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-513">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="1f2e3-514">Тип перечисления должен иметь поле `Value__` с одним экземпляром, отмеченное атрибутом `FieldAttributes.RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-514">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="1f2e3-515">Это позволяет неявно ссылаться на значение поля.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-515">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="1f2e3-516">Статические поля литералов перечисления должны иметь тот же тип, что и перечисление.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-516">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="1f2e3-517">Например, если определить перечисление `State` со значениями `State.On` и `State.Off`, `State.On` и `State.Off` будут статическими полями литералов типа `State`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-517">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="1f2e3-518">Существует два вида перечислений:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-518">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="1f2e3-519">Первый вид представляет набор взаимно исключающих именованных целочисленных значений</span><span class="sxs-lookup"><span data-stu-id="1f2e3-519">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="1f2e3-520">и не имеет настраиваемого атрибута [System.FlagsAttribute](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-520">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="1f2e3-521">Второй вид представляет набор битовых флагов, сочетая которые, можно создавать значения без имени.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-521">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="1f2e3-522">Такие перечисления имеют настраиваемый атрибут [System.FlagsAttribute](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-522">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="1f2e3-523">Дополнительные сведения см. в документации по структуре [Enum](xref:System.Enum).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-523">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="1f2e3-524">Значение перечисления не ограничивается диапазоном указанных значений.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-524">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="1f2e3-525">Другими словами, диапазон значений в перечислении — это диапазон базового значения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-525">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="1f2e3-526">Метод `Enum.IsDefined` позволяет определить, является ли указанное значение членом перечисления.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-526">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="1f2e3-527">Обзор членов типов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-527">Type members in general</span></span>

<span data-ttu-id="1f2e3-528">В соответствии со спецификацией CLS доступ ко всем полям и методам должен осуществляться как к членам определенного класса.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-528">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="1f2e3-529">Поэтому глобальные статические поля и методы (статические поля и методы, определенные отдельно от типа) не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-529">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-530">Если такие поля или методы присутствуют в коде, компилятор C# выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-530">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="1f2e3-531">В спецификации CLS поддерживается только стандартное соглашение об управляемых вызовах.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-531">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="1f2e3-532">Соглашения о неуправляемых вызовах и методы со списками аргументов переменной длины, отмеченные ключевым словом `varargs`, не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-532">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="1f2e3-533">Для переменных списков аргументов, совместимых со стандартным соглашением об управляемых вызовах, следует использовать атрибут [ParamArrayAttribute](xref:System.ParamArrayAttribute) или индивидуальную реализацию языка, например ключевое слово `params` в C# или ключевое слово `ParamArray` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-533">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="1f2e3-534">Доступность членов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-534">Member accessibility</span></span>

<span data-ttu-id="1f2e3-535">Переопределение наследуемого члена не влияет на его доступность.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-535">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="1f2e3-536">Например, открытый метод базового класса невозможно переопределить с помощью закрытого метода производного класса.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-536">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="1f2e3-537">Существует одно исключение: член `protected internal` (в C#) или член `Protected Friend` (в Visual Basic) в одной сборке может переопределяться типом в другой сборке.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-537">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="1f2e3-538">Тогда переопределенный член будет иметь доступность `Protected`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-538">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="1f2e3-539">Рассмотрим следующий пример. Атрибут [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) имеет значение `true`. Когда класс `Person`, производный от класса `Animal`, изменяет доступность свойства `Species` с открытой на закрытую, компилятор выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-539">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="1f2e3-540">Однако если доступность меняется на открытую, ошибки не возникает.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-540">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="1f2e3-541">Типы в сигнатуре члена должны быть доступны всегда, когда доступен член.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-541">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="1f2e3-542">В частности, открытый член не может иметь параметр закрытого, защищенного или внутреннего типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-542">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="1f2e3-543">В следующем примере, когда конструктор класса `StringWrapper` предоставляет внутреннее значение перечисления `StringOperationType`, которое определяет, как переносится строка, компилятор выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-543">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="1f2e3-544">Универсальные типы и члены</span><span class="sxs-lookup"><span data-stu-id="1f2e3-544">Generic types and members</span></span>

<span data-ttu-id="1f2e3-545">У вложенного типа должно быть не меньше универсальных параметров, чем у включающего типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-545">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="1f2e3-546">Они соответствуют по позиции универсальным параметрам включающего типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-546">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="1f2e3-547">Универсальный тип может также содержать новые универсальные параметры.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-547">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="1f2e3-548">Связь между параметрами универсального типа содержащего типа и вложенных типов может скрываться синтаксисом отдельных языков.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-548">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="1f2e3-549">В следующем примере универсальный тип `Outer<T>` содержит два вложенных класса — `Inner1A` и `Inner1B<U>`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-549">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="1f2e3-550">При вызове метода `ToString`, наследуемого от класса `Object.ToString`, видно, что каждый вложенный класс включает параметры типа содержащего его класса.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-550">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="1f2e3-551">Имена универсальных типов кодируются в виде *имя*'*n*, где *имя* — имя типа, *\`*  — символьный литерал, а *n* — количество параметров, объявленных в типе (у вложенных универсальных типов — количество новых параметров типа).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-551">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="1f2e3-552">Эта запись имен универсальных типов в первую очередь пригодится разработчикам, использующим отражение для доступа к универсальным CLS-совместимым типам в библиотеке.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-552">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="1f2e3-553">Если к универсальному типу применяются ограничения, то типы, используемые в качестве ограничений, должны быть CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-553">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="1f2e3-554">В следующем примере определяется класс `BaseClass`, который не является CLS-совместимым, и универсальный класс `BaseCollection`, у которого параметр типа должен быть производным от класса `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-554">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="1f2e3-555">Поскольку `BaseClass` не является CLS-совместимым, компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-555">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="1f2e3-556">В универсальном типе, производном от универсального базового типа, должны повторно объявляться ограничения, обеспечивающие соответствие всем ограничениям базового типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-556">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="1f2e3-557">В следующем примере определяется `Number<T>`, который может представлять любой числовой тип.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-557">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="1f2e3-558">В нем также определяется класс `FloatingPoint<T>`, представляющий значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-558">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="1f2e3-559">Однако поскольку ограничения `Number<T>` (T должен быть типом значения) не применяются к `FloatingPoint<T>`, код не компилируется.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-559">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="1f2e3-560">Если в класс `FloatingPoint<T>` добавить ограничение, код компилируется.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-560">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="1f2e3-561">Спецификация CLS предполагает консервативную модель создания экземпляров вложенных типов и защищенных членов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-561">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="1f2e3-562">Открытые универсальные типы не могут предоставлять поля и члены с сигнатурами, содержащими определенный экземпляр вложенного защищенного универсального типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-562">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="1f2e3-563">Неуниверсальные типы, расширяющие определенный экземпляр универсального базового класса или интерфейса, не могут предоставлять поля и члены с сигнатурами, содержащими другой экземпляр вложенного защищенного универсального типа.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-563">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="1f2e3-564">В следующем примере определяется универсальный тип `C1<T>` и защищенный класс `C1<T>.N`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-564">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="1f2e3-565">Объект `C1<T>` имеет два метода: `M1` и `M2`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-565">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="1f2e3-566">Однако `M1` не является CLS-совместимым, поскольку он возвращает объект `C1<int>.N` из `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-566">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="1f2e3-567">Второй класс `C2` является производным от `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-567">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="1f2e3-568">Он имеет два метода: `M3` и `M4`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-568">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="1f2e3-569">`M3` не является CLS-совместимым, поскольку он возвращает объект `C1<int>.N` из подкласса `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-569">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="1f2e3-570">Языковые компиляторы могут накладывать даже более строгие ограничения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-570">Language compilers can be even more restrictive.</span></span> <span data-ttu-id="1f2e3-571">В этом примере на языке Visual Basic при компиляции `M4` возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-571">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="1f2e3-572">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="1f2e3-572">Constructors</span></span>

<span data-ttu-id="1f2e3-573">Правила для конструкторов CLS-совместимых классов и структур:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-573">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="1f2e3-574">Перед обращением к данным унаследованного экземпляра конструктор производного класса должен вызвать конструктор экземпляра базового класса,</span><span class="sxs-lookup"><span data-stu-id="1f2e3-574">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="1f2e3-575">поскольку конструкторы базовых классов не наследуются производными классами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-575">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="1f2e3-576">Это правило не применяется к структурам, не поддерживающим прямое наследование.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-576">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="1f2e3-577">Обычно компиляторы применяют это правило вне зависимости от требований CLS-совместимости. Это иллюстрирует следующий пример.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-577">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="1f2e3-578">Класс `Doctor` является производным от класса `Person`, однако класс `Doctor` не может вызывать конструктор класса `Person` для инициализации наследуемых полей экземпляра.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-578">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="1f2e3-579">Конструктор объекта можно вызывать только для создания объекта.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-579">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="1f2e3-580">Объект невозможно инициализировать дважды.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-580">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="1f2e3-581">В частности, это означает, что метод `Object.MemberwiseClone` не должен вызывать конструкторы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-581">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="1f2e3-582">Свойства</span><span class="sxs-lookup"><span data-stu-id="1f2e3-582">Properties</span></span>

<span data-ttu-id="1f2e3-583">Правила для свойств CLS-совместимых типов:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-583">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="1f2e3-584">Свойство должно иметь метод задания значения, метод получения значения или оба эти метода.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-584">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="1f2e3-585">В сборке они реализованы в виде специальных методов, т. е. отображаются как отдельные методы (метод получения значения имеет имя `get`\_*propertyname*, метод задания значения — `set`\_*propertyname*) и помечаются атрибутом `SpecialName` в метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-585">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="1f2e3-586">Компилятор C# обеспечивает соблюдение этого правила, поэтому применять атрибут <xref:System.CLSCompliantAttribute> не требуется.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-586">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="1f2e3-587">Тип свойства, тип возвращаемого значения метода получения значения свойства и тип последнего аргумента метода задания значения должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-587">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="1f2e3-588">Все эти типы должны быть CLS-совместимыми, и аргументы не могут присваиваться свойству по ссылке (т. е. не могут быть управляемыми указателями).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-588">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="1f2e3-589">Если свойство имеет и метод получения, и метод задания значения, оба эти метода должны быть либо виртуальными, либо статическими, либо экземплярами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-589">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="1f2e3-590">Компилятор C# обеспечивает соблюдение этого правила с помощью синтаксиса определения свойств.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-590">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="1f2e3-591">События</span><span class="sxs-lookup"><span data-stu-id="1f2e3-591">Events</span></span>

<span data-ttu-id="1f2e3-592">Событие определяется именем и типом.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-592">An event is defined by its name and its type.</span></span> <span data-ttu-id="1f2e3-593">Тип события является делегатом, который используется для обозначения события.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-593">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="1f2e3-594">Например, событие `DbConnection.StateChange` имеет тип `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-594">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="1f2e3-595">Помимо события также определяются три метода с именами, производными от имени события, которые обеспечивают реализацию события и имеют в метаданных сборки атрибут `SpecialName`:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-595">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="1f2e3-596">Метод добавления обработчика событий с именем `add`_ *EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-596">A method for adding an event handler, named `add`_ *EventName*.</span></span> <span data-ttu-id="1f2e3-597">Например, метод подписки для события `DbConnection.StateChange` называется `add_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-597">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="1f2e3-598">Метод удаления обработчика событий с именем `remove`_ *EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-598">A method for removing an event handler, named `remove`_ *EventName*.</span></span> <span data-ttu-id="1f2e3-599">Например, метод удаления для события `DbConnection.StateChange` называется `remove_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-599">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="1f2e3-600">Метод, который указывает, что возникло событие, с именем `raise`\_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-600">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e3-601">Большинство правил спецификации CLS, связанных с событиями, реализуется языковыми компиляторами и являются прозрачными для разработчиков компонентов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-601">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="1f2e3-602">Методы добавления, удаления и вызова события должны иметь одинаковую доступность</span><span class="sxs-lookup"><span data-stu-id="1f2e3-602">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="1f2e3-603">и быть либо одновременно статическими, либо виртуальными, либо экземплярами.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-603">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="1f2e3-604">Методы добавления и удаления события имеют один параметр, тип которого является типом делегата события.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-604">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="1f2e3-605">Методы добавления и удаления должны либо оба присутствовать, либо оба отсутствовать.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-605">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="1f2e3-606">В следующем примере определяется CLS-совместимый класс `Temperature`, который создает событие `TemperatureChanged`, если перепад температуры между двумя показаниями равен пороговому значению или превышает его.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-606">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="1f2e3-607">Класс `Temperature` явно определяет метод `raise_TemperatureChanged`, чтобы он мог выборочно выполнять обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-607">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="1f2e3-608">Overloads</span><span class="sxs-lookup"><span data-stu-id="1f2e3-608">Overloads</span></span>

<span data-ttu-id="1f2e3-609">Спецификация CLS налагает следующие требования на перегруженные члены:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-609">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="1f2e3-610">Члены могут перегружаться на основе количества и типов параметров.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-610">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="1f2e3-611">Соглашение о вызовах, тип возвращаемого значения, пользовательские модификаторы, применяемые к методу или его параметру, и способ передачи параметров (по значению или по ссылке) не учитываются при различении перегрузок.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-611">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="1f2e3-612">См. пример, иллюстрирующий требование уникальности имен в пределах области в разделе [Соглашения об именовании](#naming-conventions).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-612">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="1f2e3-613">Перегружать можно только свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-613">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="1f2e3-614">Поля и события невозможно перегружать.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-614">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="1f2e3-615">Универсальные методы могут перегружаться на основе количества универсальных параметров.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-615">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e3-616">Правило о том, что возвращаемое значение не считается частью сигнатуры метода для разрешения перегрузки не распространяется на операторы `op_Explicit` и `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-616">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="1f2e3-617">Их можно перегружать и на основе параметров, и на основе возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-617">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="1f2e3-618">Исключения</span><span class="sxs-lookup"><span data-stu-id="1f2e3-618">Exceptions</span></span>

<span data-ttu-id="1f2e3-619">Объекты исключений должны наследоваться от [System.Exception](xref:System.Exception) или типа, производного от `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-619">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="1f2e3-620">В следующем примере, когда пользовательский класс `ErrorClass` используется для обработки исключения, компилятор выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-620">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="1f2e3-621">Чтобы она не возникала, класс `ErrorClass` должен наследоваться от `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-621">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="1f2e3-622">Кроме того, необходимо переопределить свойство Message.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-622">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="1f2e3-623">Эти ошибки устранены в следующем примере, где определяется CLS-совместимый класс `ErrorClass`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-623">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="1f2e3-624">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f2e3-624">Attributes</span></span>

<span data-ttu-id="1f2e3-625">В сборках .NET настраиваемые атрибуты предоставляют расширяемый механизм хранения настраиваемых атрибутов и извлечения метаданных об объектах программирования (например, о сборках, типах, членах и параметрах методов).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-625">In .NET assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="1f2e3-626">Настраиваемые атрибуты должны наследоваться от [System.Attribute](xref:System.Attribute) или типа, производного от `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-626">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="1f2e3-627">Это правило не выполняется в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-627">The following example violates this rule.</span></span> <span data-ttu-id="1f2e3-628">В нем определяется класс `NumericAttribute`, который не является производным от `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-628">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="1f2e3-629">Компилятор выдает ошибку не при определении класса, а когда используется атрибут, который не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-629">A compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="1f2e3-630">Конструктор и свойства CLS-совместимого атрибута могут предоставлять только следующие типы:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-630">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="1f2e3-631">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f2e3-631">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="1f2e3-632">Byte</span><span class="sxs-lookup"><span data-stu-id="1f2e3-632">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="1f2e3-633">Char</span><span class="sxs-lookup"><span data-stu-id="1f2e3-633">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="1f2e3-634">Double</span><span class="sxs-lookup"><span data-stu-id="1f2e3-634">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="1f2e3-635">Int16</span><span class="sxs-lookup"><span data-stu-id="1f2e3-635">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="1f2e3-636">Int32</span><span class="sxs-lookup"><span data-stu-id="1f2e3-636">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="1f2e3-637">Int64</span><span class="sxs-lookup"><span data-stu-id="1f2e3-637">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="1f2e3-638">Single</span><span class="sxs-lookup"><span data-stu-id="1f2e3-638">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="1f2e3-639">String</span><span class="sxs-lookup"><span data-stu-id="1f2e3-639">String</span></span>](xref:System.String)

* [<span data-ttu-id="1f2e3-640">Type</span><span class="sxs-lookup"><span data-stu-id="1f2e3-640">Type</span></span>](xref:System.Type)

* <span data-ttu-id="1f2e3-641">Любой тип перечисления с базовым типом `Byte`, `Int16`, `Int32` или `Int64`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-641">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="1f2e3-642">В следующем примере определяется класс `DescriptionAttribute`, производный от [Attribute](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-642">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="1f2e3-643">Конструктор класса имеет параметр типа `Descriptor`, поэтому класс не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-643">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-644">Компилятор C# выдает предупреждение, но при этом успешно завершает компиляцию.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-644">The C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="1f2e3-645">Атрибут CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="1f2e3-645">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="1f2e3-646">Атрибут [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) указывает, соответствует ли элемент правилам спецификации CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-646">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="1f2e3-647">Конструктор `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` имеет один обязательный параметр *isCompliant*, определяющий, является ли элемент программы CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-647">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-648">Компилятор определяет элементы, которые предположительно являются CLS-совместимыми, однако не соответствуют правилам спецификации CLS, и выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-648">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="1f2e3-649">Он пропускает типы и члены, которые явно объявлены как не соответствующие правилам спецификации CLS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-649">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="1f2e3-650">Разработчики компонентов могут использовать атрибут `CLSCompliantAttribute` двумя способами:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-650">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="1f2e3-651">Определять части открытого интерфейса, предоставляемые компонентом, которые являются или не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-651">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="1f2e3-652">Если с помощью этого атрибута пометить определенные элементы программы как CLS-совместимые, они будут доступны во всех языках и инструментах, ориентированных на .NET.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-652">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target .NET.</span></span>

* <span data-ttu-id="1f2e3-653">С его помощью обеспечить, чтобы открытый интерфейс библиотеки компонентов предоставлял только CLS-совместимые элементы программы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-653">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="1f2e3-654">Если элементы не являются CLS-совместимыми, компиляторы обычно выдают предупреждение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-654">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="1f2e3-655">В некоторых случаях языковые компиляторы применяют правила CLS-совместимости вне зависимости от того, используется ли атрибут `CLSCompliantAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-655">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="1f2e3-656">Например, когда в интерфейсе определяется член `*static`, нарушается правило CLS-совместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-656">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="1f2e3-657">Однако если определить в интерфейсе член `*static`, компилятор C# выдает сообщение об ошибке и не компилирует приложение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-657">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="1f2e3-658">Атрибут `CLSCompliantAttribute` отмечен атрибутом [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) со значением `AttributeTargets.All`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-658">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="1f2e3-659">Это значение позволяет применять атрибут `CLSCompliantAttribute` к любым элементам программы: сборкам, модулям, типам (классам, структурам, перечислениям, интерфейсам и делегатам), членам типов (конструкторам, методам, свойствам, полям и событиям), параметрам, универсальным параметрам и возвращаемым значениям.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-659">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="1f2e3-660">Однако на практике атрибут рекомендуется применять только к сборкам, типам и членам типов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-660">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="1f2e3-661">В противном случае компиляторы игнорируют атрибут и создают предупреждения для всех параметров, универсальных параметров и возвращаемых значений открытого интерфейса библиотеки, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-661">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="1f2e3-662">Значение атрибута `CLSCompliantAttribute` наследуется вложенными элементами программы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-662">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="1f2e3-663">Например, если сборка отмечена как CLS-совместимая, ее типы также являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-663">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="1f2e3-664">Если тип отмечен как CLS-совместимый, его вложенные типы и члены также являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-664">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-665">Можно явно переопределить наследуемую совместимость, применив к вложенному элементу программы атрибут `CLSCompliantAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-665">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="1f2e3-666">Например, вы можете использовать атрибут `CLSCompliantAttribute`, указав для *isCompliant* значение `false`, чтобы определить в совместимой сборке несовместимый тип, а также использовать атрибут, указав для *isCompliant* значение `true`, чтобы определить в несовместимой сборке совместимый тип.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-666">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="1f2e3-667">Кроме того, можно определять несовместимые члены в совместимом типе.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-667">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="1f2e3-668">Однако несовместимый тип не может иметь совместимые члены, поэтому наследование от несовместимого типа невозможно переопределить с помощью параметра `true` со значением *isCompliant*.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-668">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="1f2e3-669">При разработке компонентов следует всегда указывать, что сборка, ее типы и члены являются CLS-совместимыми с помощью атрибута `CLSCompliantAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-669">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="1f2e3-670">Создание CLS-совместимых компонентов</span><span class="sxs-lookup"><span data-stu-id="1f2e3-670">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="1f2e3-671">Пометьте сборку как CLS-совместимую с помощью атрибута `CLSCompliantAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-671">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="1f2e3-672">Пометьте все открытые типы в сборке, которые не являются CLS-совместимыми, как несовместимые.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-672">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="1f2e3-673">Пометьте все открытые члены в CLS-совместимых типах как несовместимые.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-673">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="1f2e3-674">Предоставьте CLS-совместимую альтернативу членам, которые не являются CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-674">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="1f2e3-675">Если все несовместимые типы и члены отмечены, компилятор не выдает предупреждений о несовместимости.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-675">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="1f2e3-676">Однако следует указать, какие члены не являются CLS-совместимым, и определить CLS-совместимые альтернативы в документации продукта.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-676">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="1f2e3-677">В следующем примере с помощью атрибута `CLSCompliantAttribute` определяется CLS-совместимая сборка и тип `CharacterUtilities`, который имеет два члена, не являющихся CLS-совместимыми.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-677">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="1f2e3-678">Поскольку оба члена отмечены атрибутом `CLSCompliant(false)`, компилятор не выдает предупреждения.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-678">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="1f2e3-679">Класс также предоставляет CLS-совместимую альтернативу для обоих методов.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-679">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="1f2e3-680">В обычном случае мы бы добавили две перегрузки для метода `ToUTF16`, чтобы предоставить CLS-совместимые альтернативы.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-680">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="1f2e3-681">Однако методы не перегружаются на основе возвращаемого значения, поэтому CLS-совместимые и несовместимые методы имеют разные имена.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-681">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="1f2e3-682">При разработке приложений (а не библиотек, где предоставляются типы и члены, которые могут использоваться другими разработчиками) вы столкнетесь с вопросами CLS-совместимости программных элементов, которые использует приложение, только если их не поддерживает язык, на котором вы работаете.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-682">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="1f2e3-683">И если вы попытаетесь использовать элементы, которые не являются CLS-совместимыми, языковой компилятор выдаст предупреждение.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-683">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="1f2e3-684">Взаимная совместимость кодов на разных языках</span><span class="sxs-lookup"><span data-stu-id="1f2e3-684">Cross-language interoperability</span></span>

<span data-ttu-id="1f2e3-685">Независимость от языка имеет несколько возможных значений.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-685">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="1f2e3-686">Первое значение подразумевает беспроблемное использование типов, созданных на одном языке, приложением, написанным на другом языке.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-686">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="1f2e3-687">Второе значение, которое рассматривается в этой статье, — это объединение кода, написанного на нескольких языках, в единую сборку .NET.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-687">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET assembly.</span></span>

<span data-ttu-id="1f2e3-688">В следующем примере показана организация межъязыкового взаимодействия путем создания библиотеки классов с именем "Utilities.dll", которая содержит два класса: `NumericLib` и `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-688">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="1f2e3-689">Класс `NumericLib` написан на C#, а класс `StringLib` — на Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-689">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="1f2e3-690">Ниже приведен исходный код для `StringUtil.vb`, который содержит один член — `ToTitleCase` — в своем классе `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-690">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="1f2e3-691">Ниже приведен исходный код для "NumberUtil.cs", определяющий класс `NumericLib` с двумя членами: `IsEven` и `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-691">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="1f2e3-692">Чтобы упаковать оба класса в одну сборку, необходимо скомпилировать их в модули.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-692">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="1f2e3-693">Чтобы скомпилировать файл исходного кода на Visual Basic в модуль, используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-693">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="1f2e3-694">Чтобы скомпилировать файл исходного кода на C# в модуль, используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-694">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="1f2e3-695">Затем вызовите компоновщик (Link.exe), чтобы скомпилировать оба модуля в сборку.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-695">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="1f2e3-696">В следующем примере показаны вызовы методов `NumericLib.NearZero` и `StringLib.ToTitleCase`.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-696">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="1f2e3-697">И код Visual Basic, и код C# могут обращаться к методам в обоих классах.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-697">Both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="1f2e3-698">Чтобы скомпилировать код Visual Basic, используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-698">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="1f2e3-699">Чтобы скомпилировать C#, измените имя компилятора с vbc на csc и расширение файла на с VB на CS.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-699">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
