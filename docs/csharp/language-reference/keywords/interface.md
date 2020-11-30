---
description: ':::no-loc text=interface::: (справочник по C#)'
title: interface. Справочник по C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89134592"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="e2fed-103">:::no-loc text="interface"::: (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="e2fed-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="e2fed-104">Интерфейс определяет контракт.</span><span class="sxs-lookup"><span data-stu-id="e2fed-104">An interface defines a contract.</span></span> <span data-ttu-id="e2fed-105">Любой [`class`](class.md) или [`struct`](../builtin-types/struct.md), реализующий этот контракт, должен предоставлять реализацию для членов, определенных в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="e2fed-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="e2fed-106">Начиная с C# 8.0, интерфейс может определять реализацию по умолчанию для членов.</span><span class="sxs-lookup"><span data-stu-id="e2fed-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="e2fed-107">Он также может определять члены [`static`](static.md), чтобы обеспечить единую реализацию для общих функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="e2fed-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="e2fed-108">В следующем примере класс `ImplementationClass` должен реализовать метод с именем `SampleMethod`, не имеющий параметров и возвращающий значение `void`.</span><span class="sxs-lookup"><span data-stu-id="e2fed-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="e2fed-109">Дополнительные сведения и примеры см. в разделе [Интерфейсы](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2fed-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2fed-110">Пример</span><span class="sxs-lookup"><span data-stu-id="e2fed-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="e2fed-111">Интерфейс может быть членом пространства имен или класса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="e2fed-112">Объявление интерфейса может содержать объявления (сигнатуры без реализации) следующих членов.</span><span class="sxs-lookup"><span data-stu-id="e2fed-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="e2fed-113">Методы</span><span class="sxs-lookup"><span data-stu-id="e2fed-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="e2fed-114">Свойства</span><span class="sxs-lookup"><span data-stu-id="e2fed-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="e2fed-115">Индексаторы</span><span class="sxs-lookup"><span data-stu-id="e2fed-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="e2fed-116">События</span><span class="sxs-lookup"><span data-stu-id="e2fed-116">Events</span></span>](event.md)

<span data-ttu-id="e2fed-117">Эти предыдущие объявления членов обычно не содержат тело.</span><span class="sxs-lookup"><span data-stu-id="e2fed-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="e2fed-118">Начиная с C# 8.0, член интерфейса может объявлять тело.</span><span class="sxs-lookup"><span data-stu-id="e2fed-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="e2fed-119">Этот называется *реализацией по умолчанию*.</span><span class="sxs-lookup"><span data-stu-id="e2fed-119">This is called a *default implementation*.</span></span> <span data-ttu-id="e2fed-120">Члены с телом позволяют интерфейсу предоставлять реализацию по умолчанию для классов и структур, которые не предоставляют реализацию с переопределением.</span><span class="sxs-lookup"><span data-stu-id="e2fed-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="e2fed-121">Кроме того, начиная с C# 8.0, интерфейс может включать следующее.</span><span class="sxs-lookup"><span data-stu-id="e2fed-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="e2fed-122">Константы</span><span class="sxs-lookup"><span data-stu-id="e2fed-122">Constants</span></span>](const.md)
- [<span data-ttu-id="e2fed-123">Операторы</span><span class="sxs-lookup"><span data-stu-id="e2fed-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="e2fed-124">[Статический конструктор](../../programming-guide/classes-and-structs/constructors.md#static-constructors)</span><span class="sxs-lookup"><span data-stu-id="e2fed-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="e2fed-125">Вложенные типы</span><span class="sxs-lookup"><span data-stu-id="e2fed-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="e2fed-126">Статические поля, методы, свойства, индексаторы и события</span><span class="sxs-lookup"><span data-stu-id="e2fed-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="e2fed-127">Объявления членов с использованием синтаксиса явной реализации интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="e2fed-128">Явные модификаторы доступа (доступ по умолчанию — [`public`](access-modifiers.md)).</span><span class="sxs-lookup"><span data-stu-id="e2fed-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="e2fed-129">Интерфейсы не могут содержать состояние экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e2fed-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="e2fed-130">Хотя статические поля теперь разрешены, поля экземпляров в интерфейсах запрещены.</span><span class="sxs-lookup"><span data-stu-id="e2fed-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="e2fed-131">[Автосвойства экземпляра](../../programming-guide/classes-and-structs/auto-implemented-properties.md) не поддерживаются в интерфейсах, так как они неявно объявляют скрытое поле.</span><span class="sxs-lookup"><span data-stu-id="e2fed-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="e2fed-132">Это правило оказывает незначительное воздействие на объявления свойств.</span><span class="sxs-lookup"><span data-stu-id="e2fed-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="e2fed-133">В объявлении интерфейса следующий код не объявляет автоматически реализуемое свойство, как в `class` или `struct`.</span><span class="sxs-lookup"><span data-stu-id="e2fed-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="e2fed-134">Вместо этого он объявляет свойство, которое не имеет реализации по умолчанию, но должно быть реализовано в любом типе, реализующем интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e2fed-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="e2fed-135">Интерфейс может наследовать от одного или нескольких базовых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="e2fed-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="e2fed-136">Когда интерфейс [переопределяет метод](override.md), реализованный в базовом интерфейсе, он должен использовать синтаксис [явной реализации интерфейса](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="e2fed-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="e2fed-137">Если список базовых типов содержит базовый класс и интерфейсы, базовый класс должен стоять первым в списке.</span><span class="sxs-lookup"><span data-stu-id="e2fed-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="e2fed-138">Класс, реализующий интерфейс, может явно реализовывать члены этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="e2fed-139">При явной реализации члена к нему можно получить доступ только через экземпляр интерфейса, но не через экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="e2fed-140">Кроме того, обращение к членам интерфейса по умолчанию можно осуществлять только через экземпляр интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="e2fed-141">Дополнительные сведения о явной реализации интерфейса см. в статье [Явная реализация интерфейса](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="e2fed-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2fed-142">Пример</span><span class="sxs-lookup"><span data-stu-id="e2fed-142">Example</span></span>

<span data-ttu-id="e2fed-143">В следующем примере показана реализация интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e2fed-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="e2fed-144">В этом примере интерфейс содержит объявление свойства, а класс содержит реализацию.</span><span class="sxs-lookup"><span data-stu-id="e2fed-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="e2fed-145">Любой экземпляр класса, который реализует `IPoint`, имеет целочисленные свойства `x` и `y`.</span><span class="sxs-lookup"><span data-stu-id="e2fed-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="e2fed-146">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="e2fed-146">C# language specification</span></span>

<span data-ttu-id="e2fed-147">Дополнительные сведения см. в разделе [Интерфейсы](~/_csharplang/spec/interfaces.md) статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md), а также в спецификации функций для [элементов интерфейса по умолчанию — C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e2fed-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fed-148">См. также</span><span class="sxs-lookup"><span data-stu-id="e2fed-148">See also</span></span>

- [<span data-ttu-id="e2fed-149">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="e2fed-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2fed-150">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="e2fed-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2fed-151">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="e2fed-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e2fed-152">Ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="e2fed-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="e2fed-153">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e2fed-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="e2fed-154">Использование свойств</span><span class="sxs-lookup"><span data-stu-id="e2fed-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="e2fed-155">Использование индексаторов</span><span class="sxs-lookup"><span data-stu-id="e2fed-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
