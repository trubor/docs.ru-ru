---
title: Практическое руководство. Изучение универсальных типов и создание их экземпляров при помощи отражения
description: Изучите универсальные типы и создайте их экземпляры при помощи отражения. Используйте свойства IsGenericType, IsGenericParameter и GenericParameterPosition.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: 34efca4a26b0ab3739d19b793237532ec9f4f15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263442"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="c5b12-104">Практическое руководство. Изучение универсальных типов и создание их экземпляров при помощи отражения</span><span class="sxs-lookup"><span data-stu-id="c5b12-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>

<span data-ttu-id="c5b12-105">Сведения об универсальных типах получаются аналогично сведениям о других типах: путем изучения объекта <xref:System.Type>, который представляет универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="c5b12-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="c5b12-106">Принципиальная разница заключается в том, что универсальный тип имеет список объектов <xref:System.Type>, представляющих его параметры универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="c5b12-107">В первой процедуре данного раздела изучаются универсальные типы.</span><span class="sxs-lookup"><span data-stu-id="c5b12-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="c5b12-108">Можно создать объект <xref:System.Type>, представляющий сконструированный тип, путем привязки аргументов типа к параметрам типа определения универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="c5b12-109">Это демонстрируется во второй процедуре.</span><span class="sxs-lookup"><span data-stu-id="c5b12-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="c5b12-110">Изучение универсального типа и его параметров типа</span><span class="sxs-lookup"><span data-stu-id="c5b12-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="c5b12-111">Получите экземпляр класса <xref:System.Type>, который представляет этот универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="c5b12-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="c5b12-112">В следующем коде этот тип получается с помощью оператора C# `typeof` (`GetType` в Visual Basic, `typeid` в Visual C++).</span><span class="sxs-lookup"><span data-stu-id="c5b12-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="c5b12-113">Другие способы получения объекта <xref:System.Type> см. в теме, посвященной объекту <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="c5b12-114">Обратите внимание, что в оставшейся части этой процедуры этот тип содержится в параметре метода с именем `t`.</span><span class="sxs-lookup"><span data-stu-id="c5b12-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="c5b12-115">Для определения того, является ли тип универсальным, используется свойство <xref:System.Type.IsGenericType%2A>, а для определения того, является ли тип определением универсального типа, свойство <xref:System.Type.IsGenericTypeDefinition%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="c5b12-116">Получите массив, содержащий аргументы универсального типа, с использованием метода <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="c5b12-117">Для каждого аргумента типа следует определить, является ли он параметром типа (например, в определении универсального типа) или типом, который был задан для параметра типа (например, в сконструированном типе) с использованием свойства <xref:System.Type.IsGenericParameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="c5b12-118">В системе типов параметр универсального типа представлен экземпляром класса <xref:System.Type>, как обычные типы.</span><span class="sxs-lookup"><span data-stu-id="c5b12-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="c5b12-119">В следующем примере показано имя и расположение параметра для объекта <xref:System.Type>, который представляет параметр универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="c5b12-120">В этом примере определить положение параметра не представляет труда; эти сведения более важны при изучении параметра типа, который используется в качестве аргумента типа для другого универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="c5b12-121">Определите ограничение базового типа и ограничения интерфейса параметра универсального типа с использованием метода <xref:System.Type.GetGenericParameterConstraints%2A>, чтобы получить все ограничения в одном массиве.</span><span class="sxs-lookup"><span data-stu-id="c5b12-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="c5b12-122">Расположение ограничений в конкретном порядке не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="c5b12-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="c5b12-123">При помощи свойства <xref:System.Type.GenericParameterAttributes%2A> выявите особые ограничения для параметра типа, например требования, чтобы он являлся ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="c5b12-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="c5b12-124">Это свойство содержит значения, представляющие расхождение, которое можно замаскировать, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="c5b12-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="c5b12-125">Атрибуты особого ограничения являются флагами, флаг (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), который не представляет особые ограничения, также не представляет ковариацию или контрвариацию.</span><span class="sxs-lookup"><span data-stu-id="c5b12-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="c5b12-126">Таким образом, для проверки любого из этих условий необходимо использовать подходящую маску.</span><span class="sxs-lookup"><span data-stu-id="c5b12-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="c5b12-127">В этом случае следует использовать свойство <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> для изоляции флагов особых ограничений.</span><span class="sxs-lookup"><span data-stu-id="c5b12-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="c5b12-128">Конструирование экземпляра универсального типа</span><span class="sxs-lookup"><span data-stu-id="c5b12-128">Constructing an Instance of a Generic Type</span></span>  

 <span data-ttu-id="c5b12-129">Универсальный тип напоминает шаблон.</span><span class="sxs-lookup"><span data-stu-id="c5b12-129">A generic type is like a template.</span></span> <span data-ttu-id="c5b12-130">Нельзя создать его экземпляры, если не указаны фактические типы для его параметров универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="c5b12-131">Чтобы сделать это во время выполнения с использованием отражения, необходимо использовать метод <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="c5b12-132">Конструирование экземпляра универсального типа</span><span class="sxs-lookup"><span data-stu-id="c5b12-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="c5b12-133">Получите объект <xref:System.Type>, который представляет универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="c5b12-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="c5b12-134">В следующем примере получается универсальный тип <xref:System.Collections.Generic.Dictionary%602> двумя разными способами: с использованием перегруженной версии метода <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> со строкой, описывающей этот тип, а также путем вызова метода <xref:System.Type.GetGenericTypeDefinition%2A> для сконструированного типа `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c5b12-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="c5b12-135">Для метода <xref:System.Type.MakeGenericType%2A> требуется определение универсального типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="c5b12-136">Создайте массив аргументов типа, на который будут заменены параметры типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="c5b12-137">Этот массив должен содержать правильное количество объектов <xref:System.Type> в том же порядке, в котором они отображаются в списке параметров типа.</span><span class="sxs-lookup"><span data-stu-id="c5b12-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="c5b12-138">В этом случае ключ (первый параметр типа) имеет тип <xref:System.String>, а значения в словаре являются экземплярами класса с именем `Example`.</span><span class="sxs-lookup"><span data-stu-id="c5b12-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="c5b12-139">Вызовите метод <xref:System.Type.MakeGenericType%2A>, чтобы привязать аргументы типа к параметрам типа и сконструировать тип.</span><span class="sxs-lookup"><span data-stu-id="c5b12-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="c5b12-140">Для создания объекта сконструированного типа используется перегруженная версия метода <xref:System.Activator.CreateInstance%28System.Type%29>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="c5b12-141">В следующем примере кода два экземпляра класса `Example` сохраняются в итоговом объекте `Dictionary<String, Example>`.</span><span class="sxs-lookup"><span data-stu-id="c5b12-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="c5b12-142">Пример</span><span class="sxs-lookup"><span data-stu-id="c5b12-142">Example</span></span>  

 <span data-ttu-id="c5b12-143">В следующем примере кода определяется метод `DisplayGenericType` для изучения определений универсальных типов и сконструированных типов, используемых в коде, и вывода сведений о них.</span><span class="sxs-lookup"><span data-stu-id="c5b12-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="c5b12-144">Метод `DisplayGenericType` показывает, как использовать свойства <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> и <xref:System.Type.GenericParameterPosition%2A>, а также метод <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="c5b12-145">В этом примере также определяется метод `DisplayGenericParameter` для изучения параметра универсального типа и вывода его ограничений.</span><span class="sxs-lookup"><span data-stu-id="c5b12-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="c5b12-146">В этом примере кода определяется набор тестовых типов, включая универсальный тип, который иллюстрирует ограничения параметра типа, и демонстрируется, как вывести сведения об этих типах.</span><span class="sxs-lookup"><span data-stu-id="c5b12-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="c5b12-147">В примере создается тип на основе класса <xref:System.Collections.Generic.Dictionary%602> путем создания массива аргументов типа и вызова метода <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="c5b12-148">Программа сравнивает объект <xref:System.Type>, сконструированный с использованием метода <xref:System.Type.MakeGenericType%2A>, с объектом <xref:System.Type>, полученным с использованием оператора `typeof` (`GetType` в Visual Basic), показывая, что эти объекты одинаковы.</span><span class="sxs-lookup"><span data-stu-id="c5b12-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="c5b12-149">Аналогичным образом программа получает определение универсального типа для сконструированного типа при помощи метода <xref:System.Type.GetGenericTypeDefinition%2A> и сравнивает его с объектом <xref:System.Type>, представляющим класс <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="c5b12-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b12-150">См. также</span><span class="sxs-lookup"><span data-stu-id="c5b12-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="c5b12-151">Отражение и универсальные типы</span><span class="sxs-lookup"><span data-stu-id="c5b12-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="c5b12-152">Просмотр сведений о типах</span><span class="sxs-lookup"><span data-stu-id="c5b12-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="c5b12-153">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="c5b12-153">Generics</span></span>](../../standard/generics/index.md)
