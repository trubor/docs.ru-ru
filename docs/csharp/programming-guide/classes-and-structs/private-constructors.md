---
title: Руководство по программированию на C#. Закрытые конструкторы
description: Закрытый конструктор — это особый конструктор экземпляров в C#, используемый для ограничения способа создания объекта. Он может использоваться с фабричными методами или другими идиомами конструирования.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899408"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="86e4f-104">Закрытые конструкторы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="86e4f-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="86e4f-105">Закрытый конструктор — это особый конструктор экземпляров.</span><span class="sxs-lookup"><span data-stu-id="86e4f-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="86e4f-106">Обычно он используется в классах, содержащих только статические элементы.</span><span class="sxs-lookup"><span data-stu-id="86e4f-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="86e4f-107">Если в классе один или несколько закрытых конструкторов и ни одного открытого конструктора, то прочие классы (за исключением вложенных классов) не смогут создавать экземпляры этого класса.</span><span class="sxs-lookup"><span data-stu-id="86e4f-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="86e4f-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="86e4f-108">For example:</span></span>  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 <span data-ttu-id="86e4f-109">Объявление пустого конструктора запрещает автоматическое создание конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="86e4f-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="86e4f-110">Обратите внимание, что если не использовать с конструктором модификатор доступа, то по умолчанию он все равно будет закрытым.</span><span class="sxs-lookup"><span data-stu-id="86e4f-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="86e4f-111">Однако обычно используется модификатор [private](../../language-reference/keywords/private.md), чтобы явно обозначить невозможность создания экземпляров этого класса.</span><span class="sxs-lookup"><span data-stu-id="86e4f-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="86e4f-112">Закрытые конструкторы используются, чтобы не допустить создания экземпляров класса при отсутствии полей или методов экземпляра, например для класса <xref:System.Math>, или когда осуществляется вызов метода для получения экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="86e4f-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="86e4f-113">Если все методы в классе являются статическими, имеет смысл сделать статическим весь класс.</span><span class="sxs-lookup"><span data-stu-id="86e4f-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="86e4f-114">Дополнительные сведения см. в разделе [Статические классы и члены статических классов](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="86e4f-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e4f-115">Пример</span><span class="sxs-lookup"><span data-stu-id="86e4f-115">Example</span></span>  

 <span data-ttu-id="86e4f-116">Ниже приведен пример класса с закрытым конструктором.</span><span class="sxs-lookup"><span data-stu-id="86e4f-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 <span data-ttu-id="86e4f-117">Обратите внимание, что если в примере раскомментировать следующий оператор, возникнет ошибка, так как конструктор недоступен из-за уровня защиты:</span><span class="sxs-lookup"><span data-stu-id="86e4f-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a><span data-ttu-id="86e4f-118">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="86e4f-118">C# Language Specification</span></span>  

<span data-ttu-id="86e4f-119">Дополнительные сведения см. в разделе [Закрытые конструкторы](~/_csharplang/spec/classes.md#private-constructors) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="86e4f-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="86e4f-120">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="86e4f-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="86e4f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="86e4f-121">See also</span></span>

- [<span data-ttu-id="86e4f-122">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="86e4f-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86e4f-123">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="86e4f-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="86e4f-124">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="86e4f-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="86e4f-125">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="86e4f-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="86e4f-126">private</span><span class="sxs-lookup"><span data-stu-id="86e4f-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="86e4f-127">public</span><span class="sxs-lookup"><span data-stu-id="86e4f-127">public</span></span>](../../language-reference/keywords/public.md)
