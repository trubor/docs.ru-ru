---
description: Дополнительные сведения см. в статье как определить имена и типы свойств в объявлениях анонимного типа (Visual Basic)
title: Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: e4bff8cd8dd879b97618a3bc69e1eaf1c7c269b7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483902"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="8f50a-103">Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f50a-103">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="8f50a-104">Анонимные типы не предоставляют механизм для прямого указания типов данных для свойств.</span><span class="sxs-lookup"><span data-stu-id="8f50a-104">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="8f50a-105">Типы всех свойств определяются посредством вывода.</span><span class="sxs-lookup"><span data-stu-id="8f50a-105">Types of all properties are inferred.</span></span> <span data-ttu-id="8f50a-106">В следующем примере типы `Name` и `Price` выводятся напрямую из значений, которые используются для их инициализации.</span><span class="sxs-lookup"><span data-stu-id="8f50a-106">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="8f50a-107">Анонимные типы также могут выводить имена и типы свойств из других источников.</span><span class="sxs-lookup"><span data-stu-id="8f50a-107">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="8f50a-108">В последующих разделах представлен список ситуаций, где вывод возможен, и примеры обратных ситуаций.</span><span class="sxs-lookup"><span data-stu-id="8f50a-108">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="8f50a-109">Успешный вывод</span><span class="sxs-lookup"><span data-stu-id="8f50a-109">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="8f50a-110">Анонимные типы могут выводить имена и типы свойств из следующих источников.</span><span class="sxs-lookup"><span data-stu-id="8f50a-110">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="8f50a-111">Из имен переменных.</span><span class="sxs-lookup"><span data-stu-id="8f50a-111">From variable names.</span></span> <span data-ttu-id="8f50a-112">Анонимный тип `anonProduct` будет иметь два свойства: `productName` и `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="8f50a-112">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="8f50a-113">Их типами данных будут типы исходных переменных, `String` и `Double`соответственно.</span><span class="sxs-lookup"><span data-stu-id="8f50a-113">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="8f50a-114">Из имен свойств или полей других объектов.</span><span class="sxs-lookup"><span data-stu-id="8f50a-114">From property or field names of other objects.</span></span> <span data-ttu-id="8f50a-115">Например, рассмотрим объект `car` типа `CarClass` , включающий свойства `Name` и `ID` .</span><span class="sxs-lookup"><span data-stu-id="8f50a-115">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="8f50a-116">Чтобы создать новый экземпляр анонимного типа `car1`со свойствами `Name` и `ID` , которые инициализируются значениями из объекта `car` , можно написать следующее.</span><span class="sxs-lookup"><span data-stu-id="8f50a-116">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="8f50a-117">Предыдущее объявление эквивалентно большей строке кода, определяющей анонимный тип `car2`.</span><span class="sxs-lookup"><span data-stu-id="8f50a-117">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="8f50a-118">Из имен элементов XML</span><span class="sxs-lookup"><span data-stu-id="8f50a-118">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="8f50a-119">Результирующий тип для `anon` будет иметь одно свойство `Book`c типом <xref:System.Collections.IEnumerable>(XElement).</span><span class="sxs-lookup"><span data-stu-id="8f50a-119">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="8f50a-120">Из функции, которая не имеет параметров, например `SomeFunction` в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8f50a-120">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="8f50a-121">Переменная `anon2` в следующем коде является анонимным типом, который имеет одно свойство: знак с именем `First`.</span><span class="sxs-lookup"><span data-stu-id="8f50a-121">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="8f50a-122">Этот код будет отображать букву E — букву, которая возвращена функцией <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f50a-122">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="8f50a-123">Неудачный вывод</span><span class="sxs-lookup"><span data-stu-id="8f50a-123">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="8f50a-124">Вывод имени завершится сбоем во многих случаях, в том числе в следующих.</span><span class="sxs-lookup"><span data-stu-id="8f50a-124">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="8f50a-125">Вывод является производным от вызова метода, конструктора или параметризованного свойства, для которого требуются аргументы.</span><span class="sxs-lookup"><span data-stu-id="8f50a-125">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="8f50a-126">Предыдущее объявление `anon1` завершается сбоем, если `someFunction` имеет один или несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="8f50a-126">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="8f50a-127">Проблема решается путем назначения новому имени свойства.</span><span class="sxs-lookup"><span data-stu-id="8f50a-127">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="8f50a-128">Вывод является производным от сложного выражения.</span><span class="sxs-lookup"><span data-stu-id="8f50a-128">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="8f50a-129">Ошибку можно устранить, назначив результат выражения для имени свойства.</span><span class="sxs-lookup"><span data-stu-id="8f50a-129">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="8f50a-130">Вывод нескольких свойств создает два или более свойств с одинаковым именем.</span><span class="sxs-lookup"><span data-stu-id="8f50a-130">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="8f50a-131">Возвращаясь к объявлениям в предыдущих примерах, невозможно указывать `product.Name` и `car1.Name` в качестве свойств для одного анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="8f50a-131">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="8f50a-132">Это связано с тем, что выводимый идентификатор для каждого из них будет `Name`.</span><span class="sxs-lookup"><span data-stu-id="8f50a-132">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="8f50a-133">Проблему можно решить, назначив значения уникальным именам свойств.</span><span class="sxs-lookup"><span data-stu-id="8f50a-133">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="8f50a-134">Обратите внимание, что изменение регистра (изменение прописных букв на строчные и наоборот) не делает имя уникальным.</span><span class="sxs-lookup"><span data-stu-id="8f50a-134">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="8f50a-135">Исходные тип и значение одного свойства зависят от другого свойства, которое еще не установлено.</span><span class="sxs-lookup"><span data-stu-id="8f50a-135">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="8f50a-136">Например, `.IDName = .LastName` не является допустимым в объявлении анонимного типа, если только `.LastName` уже не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="8f50a-136">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="8f50a-137">В этом примере проблему можно устранить, изменив порядок, в котором объявлены свойства, на обратный.</span><span class="sxs-lookup"><span data-stu-id="8f50a-137">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="8f50a-138">Имя свойства анонимного типа совпадает с именем элемента <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8f50a-138">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="8f50a-139">Например, следующее объявление завершится сбоем, так как `Equals` — это метод <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8f50a-139">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="8f50a-140">Проблему можно устранить, изменив имя свойства:</span><span class="sxs-lookup"><span data-stu-id="8f50a-140">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="8f50a-141">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8f50a-141">See also</span></span>

- [<span data-ttu-id="8f50a-142">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="8f50a-142">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="8f50a-143">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="8f50a-143">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="8f50a-144">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="8f50a-144">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="8f50a-145">Ключ</span><span class="sxs-lookup"><span data-stu-id="8f50a-145">Key</span></span>](../../../language-reference/modifiers/key.md)
