---
description: Дополнительные сведения о универсальных типах в Visual Basic (Visual Basic)
title: Универсальные типы
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: 1164513825240b1e83fbce2aeb6478430b0bc250
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428549"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="c0fa6-103">Универсальные типы в Visual Basic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0fa6-103">Generic Types in Visual Basic (Visual Basic)</span></span>

<span data-ttu-id="c0fa6-104">*Универсальный тип* является одиночным элементом программирования, который используется для выполнения одинаковой функциональности для различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-104">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="c0fa6-105">При определении универсальных классов или процедур не нужно определять отдельную версию для каждого типа данных, для которых может потребоваться выполнение этой функциональности.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-105">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="c0fa6-106">В качестве аналогии можно привести отвертку со съемными головками.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-106">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="c0fa6-107">Вы смотрите на шуруп, который нужно завинтить, и выбираете подходящую головку (шлицевую, крестовую или звездообразную).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-107">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="c0fa6-108">Меняя головки, вы выполняете с помощью отвертки одну и ту же функцию: завинчиваете или вывинчиваете шуруп.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-108">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 ![Схема отвертки с различными заголовками.](./media/generic-types/generic-screwdriver-set.gif)  
  
 <span data-ttu-id="c0fa6-110">При определении универсального типа его можно параметризовать с помощью одного или нескольких типов данных.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-110">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="c0fa6-111">Это позволяет использовать код, чтобы адаптировать типы данных к его требованиям.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-111">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="c0fa6-112">В коде можно объявить несколько различных элементов программирования из универсального элемента, каждый из которых действует для разных наборов типов данных.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-112">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="c0fa6-113">Но все объявленные элементы подчиняются одинаковой логике, независимо от того, какие типы данных они используют.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-113">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="c0fa6-114">Допустим, вам нужно создать и использовать класс очереди, который работает с определенным типом данных, например `String`.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-114">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="c0fa6-115">Можно объявить такой класс из <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-115">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c0fa6-116">Теперь можно использовать `stringQ` для работы исключительно со значениями `String` .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-116">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="c0fa6-117">Так как `stringQ` предназначен конкретно для `String` , а не является универсальным для значений `Object` , вам не потребуется позднее связывание или преобразование типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-117">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="c0fa6-118">Это экономит время выполнения и сокращает число ошибок во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-118">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="c0fa6-119">Дополнительные сведения об использовании универсального типа см. в разделе [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-119">For more information on using a generic type, see [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="c0fa6-120">Пример универсального класса</span><span class="sxs-lookup"><span data-stu-id="c0fa6-120">Example of a Generic Class</span></span>  

 <span data-ttu-id="c0fa6-121">В следующем примере показано определение каркаса универсального класса.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-121">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c0fa6-122">В предыдущем каркасе `t` — это *параметр типа*, то есть заполнитель для типа данных, указанного при объявлении класса.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-122">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="c0fa6-123">В другом месте в коде можно объявлять различные версии `classHolder` , указав различные типы данных для `t`.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-123">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="c0fa6-124">Два таких объявления показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-124">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c0fa6-125">Предыдущие инструкции объявляют *сконструированные классы*, в которых указанный тип заменяет параметр типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-125">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="c0fa6-126">Эта замена распространяется по всему коду сконструированного класса.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-126">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="c0fa6-127">В следующем примере показано, как процедура `processNewItem` выглядит в `integerClass`.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-127">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c0fa6-128">Более полный пример см. в разделе [как определить класс, который может обеспечить идентичную функциональность для различных типов данных](how-to-define-a-class-that-can-provide-identical-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-128">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="c0fa6-129">Допустимые элементы программирования</span><span class="sxs-lookup"><span data-stu-id="c0fa6-129">Eligible Programming Elements</span></span>  

 <span data-ttu-id="c0fa6-130">Можно определять и использовать универсальные классы, структуры, интерфейсы, процедуры и делегаты.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-130">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="c0fa6-131">Обратите внимание, что платформа .NET Framework определяет несколько универсальных классов, структур и интерфейсов, представляющих часто используемые универсальные элементы.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-131">Note that the .NET Framework defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="c0fa6-132">Пространство имен <xref:System.Collections.Generic?displayProperty=nameWithType> предоставляет словари, списки, очереди и стеки.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-132">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="c0fa6-133">Перед определением собственного универсального элемента посмотрите, не существует ли он уже в <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-133">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c0fa6-134">Процедуры не являются типами, но можно определять и использовать универсальные процедуры.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-134">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="c0fa6-135">См. раздел [Generic Procedures in Visual Basic](generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-135">See [Generic Procedures in Visual Basic](generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="c0fa6-136">Преимущества универсальных типов</span><span class="sxs-lookup"><span data-stu-id="c0fa6-136">Advantages of Generic Types</span></span>  

 <span data-ttu-id="c0fa6-137">Универсальный тип служит в качестве основы для объявления нескольких различных программных элементов, каждый из которых работает с определенным типом данных.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-137">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="c0fa6-138">Альтернативы для универсального типа:</span><span class="sxs-lookup"><span data-stu-id="c0fa6-138">The alternatives to a generic type are:</span></span>  
  
1. <span data-ttu-id="c0fa6-139">одиночный тип, работающий с типом данных `Object` .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-139">A single type operating on the `Object` data type.</span></span>  
  
2. <span data-ttu-id="c0fa6-140">Набор версий типа, *зависящих от типа* , каждая версия по отдельности запрограммирована и работает на одном конкретном типе данных, таком как `String` , `Integer` или определяемом пользователем типе, например `customer` .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-140">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="c0fa6-141">Универсальный тип имеет следующие преимущества по сравнению с этими альтернативами.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-141">A generic type has the following advantages over these alternatives:</span></span>  
  
- <span data-ttu-id="c0fa6-142">**Безопасность типа.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-142">**Type Safety.**</span></span> <span data-ttu-id="c0fa6-143">Универсальные типы обеспечивают проверку типов во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-143">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="c0fa6-144">Типы на основе `Object` принимают любой тип данных, и необходимо написать код, чтобы проверить, является ли тип входных данных приемлемым.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-144">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="c0fa6-145">При использовании универсальных типов компилятор может перехватить несоответствие типов до выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-145">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
- <span data-ttu-id="c0fa6-146">**Производительность.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-146">**Performance.**</span></span> <span data-ttu-id="c0fa6-147">Универсальные типы не должны *упаковывать* и *unупаковывать* данные, так как каждый из них является специальным для одного типа данных.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-147">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="c0fa6-148">Операции, основанные на `Object` , должны упаковывать типы входных данных для их преобразования в `Object` и распаковать данные, предназначенные для вывода.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-148">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="c0fa6-149">Упаковка и распаковка снижают производительность.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-149">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="c0fa6-150">Типы на основе `Object` имеют позднее связывание, а значит, для доступа к их элементам требуется дополнительный код во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-150">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="c0fa6-151">Это также снижает производительность.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-151">This also reduces performance.</span></span>  
  
- <span data-ttu-id="c0fa6-152">**Консолидация кода.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-152">**Code Consolidation.**</span></span> <span data-ttu-id="c0fa6-153">Код в универсальном типе должен быть определен только один раз.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-153">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="c0fa6-154">Набор типозависимых версий типа должен реплицировать тот же код в каждой версии. Единственное отличие состоит в конкретном типе данных для этой версии.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-154">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="c0fa6-155">При использовании универсальных типов типозависимые версии формируются из исходного универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-155">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
- <span data-ttu-id="c0fa6-156">**Повторное использование кода.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-156">**Code Reuse.**</span></span> <span data-ttu-id="c0fa6-157">Код, который не зависит от определенного типа данных, можно повторно использовать с различными типами данных, если он является универсальным.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-157">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="c0fa6-158">Часто его можно повторно использовать даже с типом данных, который изначально не предусматривался.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-158">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
- <span data-ttu-id="c0fa6-159">**Поддержка IDE.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-159">**IDE Support.**</span></span> <span data-ttu-id="c0fa6-160">При использовании сконструированного типа, объявленного из универсального типа, интегрированная среда разработки (IDE) может предоставить дополнительную поддержку при разработке кода.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-160">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="c0fa6-161">Например, IntelliSense может показать типозависимые параметры аргумента для конструктора или метода.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-161">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
- <span data-ttu-id="c0fa6-162">**Универсальные алгоритмы.**</span><span class="sxs-lookup"><span data-stu-id="c0fa6-162">**Generic Algorithms.**</span></span> <span data-ttu-id="c0fa6-163">Абстрактные алгоритмы, которые не зависят от типов, хорошо подходят для универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-163">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="c0fa6-164">Например, универсальную процедуру, которая сортирует элементы с помощью интерфейса <xref:System.IComparable> , можно использовать с любым типом данных, который реализует <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-164">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="c0fa6-165">Ограничения</span><span class="sxs-lookup"><span data-stu-id="c0fa6-165">Constraints</span></span>  

 <span data-ttu-id="c0fa6-166">Несмотря на то, что код в определении универсального типа должен быть максимально независимым от типов, может потребоваться определенная возможность любого типа данных, указанного для универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-166">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="c0fa6-167">Например, если необходимо сравнить два элемента с целью сортировки или упорядочивания, их тип данных должен реализовывать интерфейс <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-167">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="c0fa6-168">Соблюдение этого требования можно обеспечить путем добавления *ограничения* к параметру типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-168">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="c0fa6-169">Пример ограничения</span><span class="sxs-lookup"><span data-stu-id="c0fa6-169">Example of a Constraint</span></span>  

 <span data-ttu-id="c0fa6-170">В следующем примере показано каркасное определение класса с ограничением, которое требует аргумент типа для реализации <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-170">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c0fa6-171">Если последующий код попытается создать класс из `itemManager` , используя тип, который не реализует <xref:System.IComparable>, компилятор сообщит об ошибке.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-171">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="c0fa6-172">Типы ограничений</span><span class="sxs-lookup"><span data-stu-id="c0fa6-172">Types of Constraints</span></span>  

 <span data-ttu-id="c0fa6-173">Ограничение может содержать приведенные ниже требования в любой комбинации.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-173">Your constraint can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="c0fa6-174">Аргумент типа должен реализовывать один или несколько интерфейсов</span><span class="sxs-lookup"><span data-stu-id="c0fa6-174">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="c0fa6-175">Аргумент типа должен наследовать только из одного класса или быть типом только одного класса.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-175">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
- <span data-ttu-id="c0fa6-176">Аргумент типа должен предоставлять конструктор без параметров, доступный коду, который создает объекты из него.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-176">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
- <span data-ttu-id="c0fa6-177">Аргумент типа должен быть *ссылочным типом* или иметь *тип значения*</span><span class="sxs-lookup"><span data-stu-id="c0fa6-177">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="c0fa6-178">Если нужно задать более одного требования, используйте разделенный запятыми *список ограничений* , заключенный в фигурные скобки (`{ }`).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-178">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="c0fa6-179">Чтобы запросить доступный конструктор, включите в список ключевое слово [New operator](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-179">To require an accessible constructor, you include the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="c0fa6-180">Чтобы требовать ссылочный тип, включите ключевое слово `Class` . Чтобы требовать тип значения, включите ключевое слово `Structure` .</span><span class="sxs-lookup"><span data-stu-id="c0fa6-180">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="c0fa6-181">Дополнительные сведения об ограничениях см. в разделе [Type List](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa6-181">For more information on constraints, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="c0fa6-182">Пример множественных ограничений</span><span class="sxs-lookup"><span data-stu-id="c0fa6-182">Example of Multiple Constraints</span></span>  

 <span data-ttu-id="c0fa6-183">В следующем примере показано каркасное определение универсального класса со списком ограничений в параметре типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-183">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="c0fa6-184">В коде, который создает экземпляр этого класса, аргумент типа должен реализовывать интерфейсы <xref:System.IComparable> и <xref:System.IDisposable> , быть ссылочным типом и предоставлять доступ к конструктору без параметров.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-184">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a><span data-ttu-id="c0fa6-185">Важные термины</span><span class="sxs-lookup"><span data-stu-id="c0fa6-185">Important Terms</span></span>  

 <span data-ttu-id="c0fa6-186">Универсальные типы вводят и используют следующие термины.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-186">Generic types introduce and use the following terms:</span></span>  
  
- <span data-ttu-id="c0fa6-187">*Универсальный тип*.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-187">*Generic Type*.</span></span> <span data-ttu-id="c0fa6-188">Определение класса, структуры, интерфейса, процедуры или делегата, для которого необходимо указать по крайней мере один тип данных при объявлении.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-188">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
- <span data-ttu-id="c0fa6-189">*Параметр типа*.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-189">*Type Parameter*.</span></span> <span data-ttu-id="c0fa6-190">В определении универсального типа это заполнитель для типа данных, указываемый при объявлении типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-190">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
- <span data-ttu-id="c0fa6-191">*Аргумент типа*.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-191">*Type Argument*.</span></span> <span data-ttu-id="c0fa6-192">Определенный тип данных, который заменяет параметр типа при объявлении сконструированного типа из универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-192">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
- <span data-ttu-id="c0fa6-193">*Ограничение*.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-193">*Constraint*.</span></span> <span data-ttu-id="c0fa6-194">Условие для параметра типа, ограничивающее аргумент типа, который можно указать для него.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-194">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="c0fa6-195">Ограничение может требовать, чтобы аргумент типа реализовывал определенный интерфейс, был определенным классом или наследовал от него, имел доступный конструктор без параметров или был ссылочным типом или типом значения.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-195">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="c0fa6-196">Можно объединять эти ограничения, но невозможно указывать более одного класса.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-196">You can combine these constraints, but you can specify at most one class.</span></span>  
  
- <span data-ttu-id="c0fa6-197">*Сконструированный тип*.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-197">*Constructed Type*.</span></span> <span data-ttu-id="c0fa6-198">Класс, структура, интерфейс, процедура или делегат, объявленный из универсального типа с помощью указания аргументов типа для параметров типа.</span><span class="sxs-lookup"><span data-stu-id="c0fa6-198">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fa6-199">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c0fa6-199">See also</span></span>

- [<span data-ttu-id="c0fa6-200">Типы данных</span><span class="sxs-lookup"><span data-stu-id="c0fa6-200">Data Types</span></span>](index.md)
- [<span data-ttu-id="c0fa6-201">Символы типов</span><span class="sxs-lookup"><span data-stu-id="c0fa6-201">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="c0fa6-202">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c0fa6-202">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="c0fa6-203">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0fa6-203">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="c0fa6-204">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="c0fa6-204">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="c0fa6-205">Типы данных</span><span class="sxs-lookup"><span data-stu-id="c0fa6-205">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="c0fa6-206">Окна</span><span class="sxs-lookup"><span data-stu-id="c0fa6-206">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="c0fa6-207">Тех</span><span class="sxs-lookup"><span data-stu-id="c0fa6-207">As</span></span>](../../../language-reference/statements/as-clause.md)
- [<span data-ttu-id="c0fa6-208">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="c0fa6-208">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="c0fa6-209">Ковариация и контрвариантность</span><span class="sxs-lookup"><span data-stu-id="c0fa6-209">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="c0fa6-210">Итераторы</span><span class="sxs-lookup"><span data-stu-id="c0fa6-210">Iterators</span></span>](../../concepts/iterators.md)
