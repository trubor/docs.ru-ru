---
title: Руководство по программированию на C#. Конструкторы экземпляров
description: Конструкторы экземпляров в C# используются для создания и инициализации переменных члена экземпляра, если создание объекта class осуществляется с помощью выражения new.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 0f9372c744a7bdfab44c8cd020a4378cff729c57
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899039"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="30454-103">Конструкторы экземпляров (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="30454-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="30454-104">Конструкторы экземпляров используются для создания и инициализации переменных члена экземпляра, если создание объекта [class](../../language-reference/keywords/class.md) осуществляется с помощью выражения [new](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="30454-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="30454-105">Для инициализации класса [static](../../language-reference/keywords/static.md) или статических переменных в нестатическом классе определяется статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="30454-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="30454-106">Дополнительные сведения см. в разделе [Статические конструкторы](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="30454-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="30454-107">В следующем примере показан конструктор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="30454-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[CoordsWithParameterlessConstructorOnly#1](snippets/instance-constructors/coords/Program.cs#1)]
  
> [!NOTE]
> <span data-ttu-id="30454-108">Для ясности этот класс содержит открытые поля.</span><span class="sxs-lookup"><span data-stu-id="30454-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="30454-109">Открытые поля не рекомендуется использовать на практике, поскольку в этом случае любой метод в любом месте программы получает неограниченный и неконтролируемый доступ к внутренней работе объекта.</span><span class="sxs-lookup"><span data-stu-id="30454-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="30454-110">Члены данных обычно должны быть закрытыми, а доступ к ним должен осуществляться только посредством методов и свойства класса.</span><span class="sxs-lookup"><span data-stu-id="30454-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="30454-111">Этот конструктор экземпляра вызывается каждый раз при создании объекта на базе класса `Coords`.</span><span class="sxs-lookup"><span data-stu-id="30454-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="30454-112">Такой конструктор без аргументов называется *конструктором без параметров*.</span><span class="sxs-lookup"><span data-stu-id="30454-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="30454-113">Зачастую такие конструкторы используются для предоставления дополнительных конструкторов.</span><span class="sxs-lookup"><span data-stu-id="30454-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="30454-114">Например, можно добавить конструктор в класс `Coords`, позволяющий указывать начальные значения для членов данных:</span><span class="sxs-lookup"><span data-stu-id="30454-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[TwoArgumentConstructor#2](snippets/instance-constructors/coords/Program.cs#2)]
  
 <span data-ttu-id="30454-115">Это позволяет создавать объекты `Coords` с начальными значениями по умолчанию или с другими начальными значениями:</span><span class="sxs-lookup"><span data-stu-id="30454-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[InstantiatingCoords#3](snippets/instance-constructors/coords/Program.cs#3)]
  
 <span data-ttu-id="30454-116">Если класс не имеет конструктора, автоматически создается конструктор без параметров и для инициализации полей объекта используются значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30454-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="30454-117">Например, [int](../../language-reference/builtin-types/integral-numeric-types.md) инициализируется значением 0.</span><span class="sxs-lookup"><span data-stu-id="30454-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="30454-118">Дополнительные сведения о значениях по умолчанию типов см. в разделе [Значения по умолчанию типов C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="30454-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="30454-119">Следовательно, поскольку конструктор без параметров класса `Coords` инициализирует все члены данных с нулевыми значениями, его можно удалить. При этом работа класса не изменится.</span><span class="sxs-lookup"><span data-stu-id="30454-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="30454-120">Полный пример использования нескольких конструкторов см. в данном разделе в примере 1; пример автоматически созданного конструктора см. в примере 2.</span><span class="sxs-lookup"><span data-stu-id="30454-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="30454-121">Конструкторы экземпляров также можно использовать для вызова конструкторов экземпляров базового класса.</span><span class="sxs-lookup"><span data-stu-id="30454-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="30454-122">Конструктор класса может вызвать конструктор базового класса с помощью инициализатора:</span><span class="sxs-lookup"><span data-stu-id="30454-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
```csharp
class Circle : Shape
{
    public Circle(double radius)
        : base(radius, 0)
    {
    }
}
```
  
 <span data-ttu-id="30454-123">В этом примере класс `Circle` передает значения радиуса и высоты конструктору, предоставленному классом `Shape`, для которого класс `Circle` является производным.</span><span class="sxs-lookup"><span data-stu-id="30454-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="30454-124">Полный текст кода с использованием классов `Shape` и `Circle` см. в данном разделе в примере 3.</span><span class="sxs-lookup"><span data-stu-id="30454-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="30454-125">Пример 1</span><span class="sxs-lookup"><span data-stu-id="30454-125">Example 1</span></span>  

 <span data-ttu-id="30454-126">В следующем примере демонстрируется класс с двумя конструкторами, один из которых не имеет аргументов, а второй имеет два аргумента.</span><span class="sxs-lookup"><span data-stu-id="30454-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[CoordsFullExample#4](snippets/instance-constructors/coords/Program.cs#4)]
  
## <a name="example-2"></a><span data-ttu-id="30454-127">Пример 2</span><span class="sxs-lookup"><span data-stu-id="30454-127">Example 2</span></span>  

 <span data-ttu-id="30454-128">В этом примере класс `Person` не имеет конструкторов, поэтому автоматически предоставляется конструктор без параметров, а все поля инициализируются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30454-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[Person](snippets/instance-constructors/person/Program.cs)]
  
 <span data-ttu-id="30454-129">Обратите внимание, что значение по умолчанию `age` равно `0`, а значение по умолчанию `name` равно `null`.</span><span class="sxs-lookup"><span data-stu-id="30454-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="30454-130">Пример 3</span><span class="sxs-lookup"><span data-stu-id="30454-130">Example 3</span></span>  

 <span data-ttu-id="30454-131">В следующем примере демонстрируется использование инициализатора базового класса.</span><span class="sxs-lookup"><span data-stu-id="30454-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="30454-132">Класс `Circle` является производным от основного класса `Shape`, а класс `Cylinder` является производным от класса `Circle`.</span><span class="sxs-lookup"><span data-stu-id="30454-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="30454-133">Конструктор каждого производного класса использует инициализатор своего базового класса.</span><span class="sxs-lookup"><span data-stu-id="30454-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[ShapesExample](snippets/instance-constructors/shapes/Program.cs)]
  
 <span data-ttu-id="30454-134">Дополнительные примеры вызова конструкторов базовых классов см. в разделах [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md) и [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="30454-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30454-135">См. также</span><span class="sxs-lookup"><span data-stu-id="30454-135">See also</span></span>

- [<span data-ttu-id="30454-136">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="30454-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="30454-137">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="30454-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="30454-138">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="30454-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="30454-139">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="30454-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="30454-140">static</span><span class="sxs-lookup"><span data-stu-id="30454-140">static</span></span>](../../language-reference/keywords/static.md)
