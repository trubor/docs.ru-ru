---
description: Дополнительные сведения см. в статье как определить класс, который может предоставлять одинаковые функциональные возможности для разных типов данных (Visual Basic)
title: Практическое руководство. Определение класса, реализующего одинаковую функциональность для разных типов данных
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 14be6c748ccb311c6a2974e8947b01a1c55a90b6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469751"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="dad2e-103">Практическое руководство. Определение класса, реализующего одинаковую функциональность для различных типов данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dad2e-103">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>

<span data-ttu-id="dad2e-104">Можно определить класс, из которого можно создавать объекты, обеспечивающие одинаковые функциональные возможности для различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="dad2e-104">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="dad2e-105">Для этого укажите в определении один или несколько *параметров типа* .</span><span class="sxs-lookup"><span data-stu-id="dad2e-105">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="dad2e-106">После этого класс может служить шаблоном для объектов, которые используют различные типы данных.</span><span class="sxs-lookup"><span data-stu-id="dad2e-106">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="dad2e-107">Класс, определенный таким образом, называется *универсальным классом*.</span><span class="sxs-lookup"><span data-stu-id="dad2e-107">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="dad2e-108">Преимущество определения универсального класса состоит в том, он определяется только один раз, и код может использовать его для создания многих объектов, использующих разнообразные типы данных.</span><span class="sxs-lookup"><span data-stu-id="dad2e-108">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="dad2e-109">Это дает более высокую производительность, чем при определении класса с помощью типа `Object` .</span><span class="sxs-lookup"><span data-stu-id="dad2e-109">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="dad2e-110">Помимо классов, можно определять и использовать универсальные структуры, интерфейсы, процедуры и делегаты.</span><span class="sxs-lookup"><span data-stu-id="dad2e-110">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="dad2e-111">Определение класса с помощью параметра типа</span><span class="sxs-lookup"><span data-stu-id="dad2e-111">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="dad2e-112">Определите класс обычным способом.</span><span class="sxs-lookup"><span data-stu-id="dad2e-112">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="dad2e-113">Добавьте `(Of` *typeparameter находится вне* `)` сразу после имени класса, чтобы указать параметр типа.</span><span class="sxs-lookup"><span data-stu-id="dad2e-113">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="dad2e-114">Если имеется более одного параметра типа, создайте разделенный запятыми список, заключенный в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="dad2e-114">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="dad2e-115">Не следует повторять ключевое слово `Of` .</span><span class="sxs-lookup"><span data-stu-id="dad2e-115">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="dad2e-116">Если код выполняет с параметром типа какие-либо операции, отличные от простого присваивания, следует записать данный параметр типа с условием `As` для добавления одного или нескольких *ограничений*.</span><span class="sxs-lookup"><span data-stu-id="dad2e-116">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="dad2e-117">Ограничение гарантирует, что тип, указанный для данного параметра типа, удовлетворяет определенным требованиям:</span><span class="sxs-lookup"><span data-stu-id="dad2e-117">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="dad2e-118">Поддерживает операции, например `>`, которые выполняются кодом.</span><span class="sxs-lookup"><span data-stu-id="dad2e-118">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="dad2e-119">Поддерживает элементы, например методы, к которым обращается код.</span><span class="sxs-lookup"><span data-stu-id="dad2e-119">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="dad2e-120">Предоставляет конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="dad2e-120">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="dad2e-121">Если не указаны никакие ограничения, код сможет использовать только операции и элементы, поддерживаемые [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="dad2e-121">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="dad2e-122">Дополнительные сведения см. в разделе [Type List](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="dad2e-122">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="dad2e-123">Определите каждый член класса, который должен быть объявлен с указанным типом, и объявите его `As` `typeparameter` .</span><span class="sxs-lookup"><span data-stu-id="dad2e-123">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="dad2e-124">Это относится к внутреннему хранилищу, параметрам процедур и возвращаемым значениям.</span><span class="sxs-lookup"><span data-stu-id="dad2e-124">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="dad2e-125">Убедитесь, что код использует только операции и методы, поддерживаемые типом данных, который может быть предоставлен для `itemType`.</span><span class="sxs-lookup"><span data-stu-id="dad2e-125">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="dad2e-126">В следующем примере определяется класс, управляющий простым списком.</span><span class="sxs-lookup"><span data-stu-id="dad2e-126">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="dad2e-127">Он хранит список во внутреннем массиве `items`, и использующий код может объявить тип данных элементов списка.</span><span class="sxs-lookup"><span data-stu-id="dad2e-127">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="dad2e-128">Параметризованный конструктор позволяет использовать код для установки верхней границы элемента `items` , а конструктор без параметров задает значение 9 (для всего 10 элементов).</span><span class="sxs-lookup"><span data-stu-id="dad2e-128">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="dad2e-129">Можно объявить один класс из `simpleList` для хранения списка значений `Integer` , другой класс — для хранения списка значений `String` и еще один — для хранения значений `Date` .</span><span class="sxs-lookup"><span data-stu-id="dad2e-129">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="dad2e-130">Кроме типа данных элементов списка, объекты, созданные из всех этих классов, ведут себя одинаково.</span><span class="sxs-lookup"><span data-stu-id="dad2e-130">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="dad2e-131">Аргумент типа, который использующий код указывает для `itemType` , может быть встроенным типом, например `Boolean` или `Double`, структурой, перечислением или любым типом класса, включая определяемый приложением.</span><span class="sxs-lookup"><span data-stu-id="dad2e-131">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="dad2e-132">Можно протестировать класс `simpleList` с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="dad2e-132">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="dad2e-133">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dad2e-133">See also</span></span>

- [<span data-ttu-id="dad2e-134">Типы данных</span><span class="sxs-lookup"><span data-stu-id="dad2e-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="dad2e-135">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dad2e-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="dad2e-136">Независимость от языка и независимые от языка компоненты</span><span class="sxs-lookup"><span data-stu-id="dad2e-136">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="dad2e-137">Окна</span><span class="sxs-lookup"><span data-stu-id="dad2e-137">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="dad2e-138">Type List</span><span class="sxs-lookup"><span data-stu-id="dad2e-138">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="dad2e-139">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="dad2e-139">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="dad2e-140">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="dad2e-140">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
