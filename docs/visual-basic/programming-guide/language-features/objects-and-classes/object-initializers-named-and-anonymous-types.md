---
description: 'Дополнительные сведения: инициализаторы объектов: именованные и анонимные типы (Visual Basic)'
title: 'Инициализаторы объектов: именованные и анонимные типы'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 47182653e74b16b9911f4b727eb1595bf3eceba6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455253"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="1134b-103">Инициализаторы объектов: именованные и анонимные типы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1134b-103">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="1134b-104">Инициализаторы объектов позволяют задавать свойства для сложного объекта с помощью одного выражения.</span><span class="sxs-lookup"><span data-stu-id="1134b-104">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="1134b-105">Они могут использоваться для создания экземпляров именованных типов и анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="1134b-105">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="1134b-106">Объявления</span><span class="sxs-lookup"><span data-stu-id="1134b-106">Declarations</span></span>  

 <span data-ttu-id="1134b-107">Объявления экземпляров именованных и анонимных типов могут выглядеть почти одинаково, но их последствия не совпадают.</span><span class="sxs-lookup"><span data-stu-id="1134b-107">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="1134b-108">Каждая категория имеет свои возможности и ограничения.</span><span class="sxs-lookup"><span data-stu-id="1134b-108">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="1134b-109">В следующем примере показан удобный способ объявления и инициализации экземпляра именованного класса с `Customer` помощью списка инициализаторов объектов.</span><span class="sxs-lookup"><span data-stu-id="1134b-109">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="1134b-110">Обратите внимание, что имя класса указывается после ключевого слова `New` .</span><span class="sxs-lookup"><span data-stu-id="1134b-110">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="1134b-111">Анонимный тип не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="1134b-111">An anonymous type has no usable name.</span></span> <span data-ttu-id="1134b-112">Поэтому создание экземпляра анонимного типа не может включать имя класса.</span><span class="sxs-lookup"><span data-stu-id="1134b-112">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="1134b-113">Требования и результаты двух объявлений не совпадают.</span><span class="sxs-lookup"><span data-stu-id="1134b-113">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="1134b-114">Для `namedCust` класс, `Customer` имеющий свойство, `Name` должен уже существовать, а объявление создает экземпляр этого класса.</span><span class="sxs-lookup"><span data-stu-id="1134b-114">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="1134b-115">Для `anonymousCust` компилятор определяет новый класс, который имеет одно свойство, строку с именем `Name` и создает новый экземпляр этого класса.</span><span class="sxs-lookup"><span data-stu-id="1134b-115">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="1134b-116">Именованные типы</span><span class="sxs-lookup"><span data-stu-id="1134b-116">Named Types</span></span>  

 <span data-ttu-id="1134b-117">Инициализаторы объектов предоставляют простой способ вызова конструктора типа, а затем задают значения некоторых или всех свойств в одной инструкции.</span><span class="sxs-lookup"><span data-stu-id="1134b-117">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="1134b-118">Компилятор вызывает соответствующий конструктор для инструкции: конструктор без параметров, если аргументы не представлены, или параметризованный конструктор при отправке одного или нескольких аргументов.</span><span class="sxs-lookup"><span data-stu-id="1134b-118">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="1134b-119">После этого заданные свойства инициализируются в том порядке, в котором они представлены в списке инициализаторов.</span><span class="sxs-lookup"><span data-stu-id="1134b-119">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="1134b-120">Каждая инициализация в списке инициализаторов состоит из присваивания начального значения члену класса.</span><span class="sxs-lookup"><span data-stu-id="1134b-120">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="1134b-121">Имена и типы данных элементов определяются при определении класса.</span><span class="sxs-lookup"><span data-stu-id="1134b-121">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="1134b-122">В следующих примерах `Customer` класс должен существовать и должен иметь члены с именем `Name` и `City` , которые могут принимать строковые значения.</span><span class="sxs-lookup"><span data-stu-id="1134b-122">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1134b-123">Кроме того, можно получить тот же результат, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="1134b-123">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1134b-124">Каждое из этих объявлений эквивалентно следующему примеру, который создает `Customer` объект с помощью конструктора без параметров, а затем задает начальные значения для `Name` свойств и с `City` помощью `With` инструкции.</span><span class="sxs-lookup"><span data-stu-id="1134b-124">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1134b-125">Если `Customer` класс содержит параметризованный конструктор, который позволяет отправить значение для `Name` , например, можно также объявить и инициализировать `Customer` объект следующими способами.</span><span class="sxs-lookup"><span data-stu-id="1134b-125">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="1134b-126">Не нужно инициализировать все свойства, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="1134b-126">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="1134b-127">Однако список инициализации не может быть пустым.</span><span class="sxs-lookup"><span data-stu-id="1134b-127">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="1134b-128">Неинициализированные свойства сохраняют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1134b-128">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="1134b-129">Вывод типа с именованными типами</span><span class="sxs-lookup"><span data-stu-id="1134b-129">Type Inference with Named Types</span></span>  

 <span data-ttu-id="1134b-130">Код для объявления можно сократить `cust1` , объединив инициализаторы объектов и вывод локального типа.</span><span class="sxs-lookup"><span data-stu-id="1134b-130">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="1134b-131">Это позволяет опустить `As` предложение в объявлении переменной.</span><span class="sxs-lookup"><span data-stu-id="1134b-131">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="1134b-132">Тип данных переменной выводится из типа объекта, созданного назначением.</span><span class="sxs-lookup"><span data-stu-id="1134b-132">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="1134b-133">В следующем примере типом `cust6` является `Customer` .</span><span class="sxs-lookup"><span data-stu-id="1134b-133">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="1134b-134">Примечания об именованных типах</span><span class="sxs-lookup"><span data-stu-id="1134b-134">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="1134b-135">Член класса не может быть инициализирован более одного раза в списке инициализаторов объектов.</span><span class="sxs-lookup"><span data-stu-id="1134b-135">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="1134b-136">Объявление `cust7` вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="1134b-136">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="1134b-137">Элемент может использоваться для инициализации самого себя или другого поля.</span><span class="sxs-lookup"><span data-stu-id="1134b-137">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="1134b-138">Если доступ к элементу осуществляется до инициализации, как показано в следующем объявлении для `cust8` , будет использоваться значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1134b-138">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="1134b-139">Помните, что при обработке объявления, использующего инициализатор объекта, первое, что происходит, это то, что вызывается соответствующий конструктор.</span><span class="sxs-lookup"><span data-stu-id="1134b-139">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="1134b-140">После этого инициализируются отдельные поля в списке инициализаторов.</span><span class="sxs-lookup"><span data-stu-id="1134b-140">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="1134b-141">В следующих примерах значение по умолчанию для присваивается `Name` `cust8` , а инициализированное значение присваивается в `cust9` .</span><span class="sxs-lookup"><span data-stu-id="1134b-141">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="1134b-142">В следующем примере параметризованный конструктор используется из `cust3` и `cust4` для объявления и инициализации и `cust10` `cust11` .</span><span class="sxs-lookup"><span data-stu-id="1134b-142">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="1134b-143">Инициализаторы объектов могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="1134b-143">Object initializers can be nested.</span></span> <span data-ttu-id="1134b-144">В следующем примере класс имеет `AddressClass` два свойства: `City` и `State` , и `Customer` класс имеет `Address` свойство, которое является экземпляром `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="1134b-144">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="1134b-145">Список инициализации не может быть пустым.</span><span class="sxs-lookup"><span data-stu-id="1134b-145">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="1134b-146">Инициализируемый экземпляр не может иметь тип Object.</span><span class="sxs-lookup"><span data-stu-id="1134b-146">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="1134b-147">Инициализируемые члены класса не могут быть общими членами, членами только для чтения, константами или вызовами методов.</span><span class="sxs-lookup"><span data-stu-id="1134b-147">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="1134b-148">Инициализируемые члены класса не могут индексироваться или уточняться.</span><span class="sxs-lookup"><span data-stu-id="1134b-148">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="1134b-149">В следующих примерах вызываются ошибки компилятора:</span><span class="sxs-lookup"><span data-stu-id="1134b-149">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="1134b-150">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="1134b-150">Anonymous Types</span></span>  

 <span data-ttu-id="1134b-151">Анонимные типы используют инициализаторы объектов для создания экземпляров новых типов, которые явно не определены и не имеют имени.</span><span class="sxs-lookup"><span data-stu-id="1134b-151">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="1134b-152">Вместо этого компилятор создает тип в соответствии со свойствами, которые вы указываете в списке инициализатора объекта.</span><span class="sxs-lookup"><span data-stu-id="1134b-152">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="1134b-153">Так как имя типа не указано, оно называется *анонимным типом*.</span><span class="sxs-lookup"><span data-stu-id="1134b-153">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="1134b-154">Например, Сравните следующее объявление с предыдущим для `cust6` .</span><span class="sxs-lookup"><span data-stu-id="1134b-154">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="1134b-155">Единственное отличие состоит в том, что после `New` для типа данных не указано имя.</span><span class="sxs-lookup"><span data-stu-id="1134b-155">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="1134b-156">Тем не менее, что происходит совершенно иначе.</span><span class="sxs-lookup"><span data-stu-id="1134b-156">However, what happens is quite different.</span></span> <span data-ttu-id="1134b-157">Компилятор определяет новый анонимный тип, который имеет два свойства: `Name` и и `City` создает экземпляр с указанными значениями.</span><span class="sxs-lookup"><span data-stu-id="1134b-157">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="1134b-158">Определение типа определяет типы `Name` и `City` в примере как строки.</span><span class="sxs-lookup"><span data-stu-id="1134b-158">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1134b-159">Имя анонимного типа создается компилятором и может отличаться от компиляции к компиляции.</span><span class="sxs-lookup"><span data-stu-id="1134b-159">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="1134b-160">Код не должен использовать имя анонимного типа или полагаться на него.</span><span class="sxs-lookup"><span data-stu-id="1134b-160">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="1134b-161">Поскольку имя типа недоступно, нельзя использовать `As` предложение для объявления `cust13` .</span><span class="sxs-lookup"><span data-stu-id="1134b-161">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="1134b-162">Его тип должен быть определен.</span><span class="sxs-lookup"><span data-stu-id="1134b-162">Its type must be inferred.</span></span> <span data-ttu-id="1134b-163">Без использования позднего связывания это ограничивает использование анонимных типов локальными переменными.</span><span class="sxs-lookup"><span data-stu-id="1134b-163">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="1134b-164">Анонимные типы обеспечивают важную поддержку запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="1134b-164">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="1134b-165">Дополнительные сведения об использовании анонимных типов в запросах см. в разделе [анонимные типы](anonymous-types.md) и [Введение в LINQ в Visual Basic](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="1134b-165">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="1134b-166">Примечания о анонимных типах</span><span class="sxs-lookup"><span data-stu-id="1134b-166">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="1134b-167">Как правило, все или большинство свойств в объявлении анонимного типа будут ключевыми свойствами, которые указываются путем ввода ключевого слова `Key` перед именем свойства.</span><span class="sxs-lookup"><span data-stu-id="1134b-167">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="1134b-168">Дополнительные сведения о ключевых свойствах см. в разделе [Key](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="1134b-168">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="1134b-169">Как и именованные типы, списки инициализаторов для определений анонимных типов должны объявлять хотя бы одно свойство.</span><span class="sxs-lookup"><span data-stu-id="1134b-169">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="1134b-170">При объявлении экземпляра анонимного типа компилятор создает соответствующее определение анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="1134b-170">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="1134b-171">Имена и типы данных свойств берутся из объявления экземпляра и включаются компилятором в определение.</span><span class="sxs-lookup"><span data-stu-id="1134b-171">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="1134b-172">Свойства не именуются и не определяются заранее, так как они бы были для именованного типа.</span><span class="sxs-lookup"><span data-stu-id="1134b-172">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="1134b-173">Их типы выводятся.</span><span class="sxs-lookup"><span data-stu-id="1134b-173">Their types are inferred.</span></span> <span data-ttu-id="1134b-174">Нельзя указать типы данных свойств с помощью `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="1134b-174">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="1134b-175">Анонимные типы также могут устанавливать имена и значения их свойств несколькими другими способами.</span><span class="sxs-lookup"><span data-stu-id="1134b-175">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="1134b-176">Например, свойство анонимного типа может принимать как имя, так и значение переменной, а также имя и значение свойства другого объекта.</span><span class="sxs-lookup"><span data-stu-id="1134b-176">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="1134b-177">Дополнительные сведения о параметрах определения свойств в анонимных типах см. [в разделе как вывести имена и типы свойств в объявлениях анонимного типа](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="1134b-177">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1134b-178">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1134b-178">See also</span></span>

- [<span data-ttu-id="1134b-179">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="1134b-179">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="1134b-180">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="1134b-180">Anonymous Types</span></span>](anonymous-types.md)
- <span data-ttu-id="1134b-181">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1134b-181">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="1134b-182">Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов</span><span class="sxs-lookup"><span data-stu-id="1134b-182">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="1134b-183">Ключ</span><span class="sxs-lookup"><span data-stu-id="1134b-183">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="1134b-184">Практическое руководство. Объявление объекта с помощью инициализатора объектов</span><span class="sxs-lookup"><span data-stu-id="1134b-184">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
