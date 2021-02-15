---
description: 'Дополнительные сведения: отношения типов в операциях запроса (Visual Basic)'
title: Связи типов в операциях запроса
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: b6a59308e76afdcf1aaf7084904b9925cd5bef14
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428224"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="9fc79-103">Отношения типов в операциях запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fc79-103">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="9fc79-104">Переменные, используемые в операциях запросов Language-Integrated запросов (LINQ), строго типизированы и должны быть совместимы друг с другом.</span><span class="sxs-lookup"><span data-stu-id="9fc79-104">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="9fc79-105">Строгая типизация используется в источнике данных, в самом запросе и в выполнении запроса.</span><span class="sxs-lookup"><span data-stu-id="9fc79-105">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="9fc79-106">На следующем рисунке показаны термины, используемые для описания запроса LINQ.</span><span class="sxs-lookup"><span data-stu-id="9fc79-106">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="9fc79-107">Дополнительные сведения о частях запроса см. в разделе [основные операции запроса (Visual Basic)](basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9fc79-107">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![Снимок экрана, показывающий запрос на псевдокод с выделенными элементами.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="9fc79-109">Тип переменной диапазона в запросе должен быть совместим с типом элементов в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="9fc79-110">Тип переменной запроса должен быть совместим с элементом последовательности, определенным в `Select` предложении.</span><span class="sxs-lookup"><span data-stu-id="9fc79-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="9fc79-111">Наконец, тип элементов последовательности также должен быть совместим с типом управляющей переменной цикла, которая используется в `For Each` инструкции, выполняющей запрос.</span><span class="sxs-lookup"><span data-stu-id="9fc79-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="9fc79-112">Эта строгая типизация облегчает идентификацию ошибок типа во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="9fc79-112">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="9fc79-113">Visual Basic обеспечивает строгую типизацию, реализуя вывод локального типа, также называемую *неявной типизацией*.</span><span class="sxs-lookup"><span data-stu-id="9fc79-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="9fc79-114">Эта функция используется в предыдущем примере, и вы увидите, что она используется во всех примерах и документации по LINQ.</span><span class="sxs-lookup"><span data-stu-id="9fc79-114">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="9fc79-115">В Visual Basic вывод локального типа выполняется просто с помощью `Dim` оператора без `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="9fc79-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="9fc79-116">В следующем примере `city` строго типизирован как строка.</span><span class="sxs-lookup"><span data-stu-id="9fc79-116">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="9fc79-117">Локальное определение типа работает только в том случае, если параметр `Option Infer` имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="9fc79-118">Дополнительные сведения см. в разделе [оператор Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9fc79-118">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="9fc79-119">Однако даже если в запросе используется определение локального типа, то одни и те же связи типов существуют между переменными в источнике данных, переменной запроса и циклом выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="9fc79-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="9fc79-120">При написании запросов LINQ и использовании примеров и примеров кода в документации полезно иметь базовое понимание этих отношений типов.</span><span class="sxs-lookup"><span data-stu-id="9fc79-120">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="9fc79-121">Может потребоваться указать явный тип для переменной диапазона, которая не соответствует типу, возвращаемому источником данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="9fc79-122">Тип переменной диапазона можно указать с помощью `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="9fc79-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="9fc79-123">Однако это приводит к ошибке, если преобразование является [узким преобразованием](../../language-features/data-types/widening-and-narrowing-conversions.md) и `Option Strict` имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-123">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="9fc79-124">Поэтому рекомендуется выполнить преобразование для значений, полученных из источника данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="9fc79-125">Можно преобразовать значения из источника данных в явный тип переменной диапазона с помощью <xref:System.Linq.Enumerable.Cast%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="9fc79-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="9fc79-126">Можно также привести значения, выбранные в `Select` предложении, к явному типу, отличному от типа переменной диапазона.</span><span class="sxs-lookup"><span data-stu-id="9fc79-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="9fc79-127">Эти моменты показаны в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="9fc79-127">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="9fc79-128">Запросы, возвращающие все элементы исходных данных</span><span class="sxs-lookup"><span data-stu-id="9fc79-128">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="9fc79-129">В следующем примере показана операция запроса LINQ, возвращающая последовательность элементов, выбранных из исходных данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-129">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="9fc79-130">Источник, `names` , содержит массив строк, а выходные данные запроса представляют собой последовательность, содержащую строки, начинающиеся с буквы M.</span><span class="sxs-lookup"><span data-stu-id="9fc79-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="9fc79-131">Это эквивалентно следующему коду, но гораздо короче и проще в написании.</span><span class="sxs-lookup"><span data-stu-id="9fc79-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="9fc79-132">Использовать определение локального типа в запросах является предпочтительным стилем в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9fc79-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="9fc79-133">В обоих приведенных выше примерах кода существуют следующие связи, независимо от того, определены типы как неявно или явно.</span><span class="sxs-lookup"><span data-stu-id="9fc79-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="9fc79-134">Тип элементов в источнике данных, `names` , — это тип переменной диапазона `name` в запросе.</span><span class="sxs-lookup"><span data-stu-id="9fc79-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="9fc79-135">Тип объекта, который выбран, `name` определяет тип переменной запроса `mNames` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="9fc79-136">Ниже приведена `name` строка, поэтому переменная запроса имеет значение IEnumerable (Of String) в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9fc79-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="9fc79-137">Запрос, определенный в `mNames` , выполняется в `For Each` цикле.</span><span class="sxs-lookup"><span data-stu-id="9fc79-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="9fc79-138">Цикл выполняет итерацию результата выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="9fc79-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="9fc79-139">Поскольку `mNames` при выполнении будет возвращена последовательность строк, переменная итерации цикла, `nm` также является строкой.</span><span class="sxs-lookup"><span data-stu-id="9fc79-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="9fc79-140">Запросы, возвращающие одно поле из выбранных элементов</span><span class="sxs-lookup"><span data-stu-id="9fc79-140">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="9fc79-141">В следующем примере показана [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] операция запроса, возвращающая последовательность, содержащую только одну часть каждого элемента, выбранного из источника данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="9fc79-142">Запрос принимает коллекцию `Customer` объектов в качестве источника данных и проецирует только `Name` свойство в результате.</span><span class="sxs-lookup"><span data-stu-id="9fc79-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="9fc79-143">Поскольку имя клиента является строкой, запрос создает последовательность строк в качестве выходных данных.</span><span class="sxs-lookup"><span data-stu-id="9fc79-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="9fc79-144">Связи между переменными, как и в более простом примере.</span><span class="sxs-lookup"><span data-stu-id="9fc79-144">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="9fc79-145">Тип элементов в источнике данных, `customers` , — это тип переменной диапазона `cust` в запросе.</span><span class="sxs-lookup"><span data-stu-id="9fc79-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="9fc79-146">В этом примере это тип `Customer` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-146">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="9fc79-147">`Select`Оператор возвращает `Name` свойство каждого `Customer` объекта, а не весь объект.</span><span class="sxs-lookup"><span data-stu-id="9fc79-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="9fc79-148">Поскольку `Name` — это строка, переменная запроса, `custNames` , опять же, будет IEnumerable (Of String), а не `Customer` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="9fc79-149">Поскольку `custNames` представляет последовательность строк, `For Each` переменная итерации цикла `custName` должна быть строкой.</span><span class="sxs-lookup"><span data-stu-id="9fc79-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="9fc79-150">Без локального определения типа предыдущий пример был бы более громоздким для написания и понимания, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9fc79-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="9fc79-151">Запросы, для которых требуются анонимные типы</span><span class="sxs-lookup"><span data-stu-id="9fc79-151">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="9fc79-152">В следующем примере показана более сложная ситуация.</span><span class="sxs-lookup"><span data-stu-id="9fc79-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="9fc79-153">В предыдущем примере было неудобно указывать типы для всех переменных явным образом.</span><span class="sxs-lookup"><span data-stu-id="9fc79-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="9fc79-154">В этом примере это невозможно.</span><span class="sxs-lookup"><span data-stu-id="9fc79-154">In this example, it is impossible.</span></span> <span data-ttu-id="9fc79-155">Вместо выбора целых `Customer` элементов из источника данных или одного поля из каждого элемента `Select` предложение в этом запросе возвращает два свойства исходного `Customer` объекта: `Name` и `City` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="9fc79-156">В ответ на `Select` предложение компилятор определяет анонимный тип, содержащий эти два свойства.</span><span class="sxs-lookup"><span data-stu-id="9fc79-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="9fc79-157">Результатом выполнения `nameCityQuery` в `For Each` цикле является коллекция экземпляров нового анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="9fc79-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="9fc79-158">Так как анонимный тип не имеет имени, его нельзя указать `nameCityQuery` `custInfo` явным образом.</span><span class="sxs-lookup"><span data-stu-id="9fc79-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="9fc79-159">То есть с анонимным типом у вас нет имени типа для использования вместо `String` в `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="9fc79-160">Дополнительные сведения см. в статье [Анонимные типы](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9fc79-160">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="9fc79-161">Хотя невозможно указать типы для всех переменных в предыдущем примере, связи остаются неизменными.</span><span class="sxs-lookup"><span data-stu-id="9fc79-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="9fc79-162">Тип элементов в источнике данных опять является типом переменной диапазона в запросе.</span><span class="sxs-lookup"><span data-stu-id="9fc79-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="9fc79-163">В этом примере `cust` — это экземпляр `Customer` .</span><span class="sxs-lookup"><span data-stu-id="9fc79-163">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="9fc79-164">Так как `Select` инструкция создает анонимный тип, переменная запроса, `nameCityQuery` должна быть неявно типизирована как анонимный тип.</span><span class="sxs-lookup"><span data-stu-id="9fc79-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="9fc79-165">Анонимный тип не имеет имени и поэтому не может быть указан явным образом.</span><span class="sxs-lookup"><span data-stu-id="9fc79-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="9fc79-166">Тип переменной итерации в `For Each` цикле — это анонимный тип, созданный на шаге 2.</span><span class="sxs-lookup"><span data-stu-id="9fc79-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="9fc79-167">Поскольку тип не имеет пригодного для использования имени, тип переменной итерации цикла должен быть определен неявно.</span><span class="sxs-lookup"><span data-stu-id="9fc79-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fc79-168">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9fc79-168">See also</span></span>

- [<span data-ttu-id="9fc79-169">Приступая к работе с LINQ в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fc79-169">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="9fc79-170">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="9fc79-170">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="9fc79-171">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="9fc79-171">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- <span data-ttu-id="9fc79-172">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fc79-172">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="9fc79-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="9fc79-173">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="9fc79-174">Запросы</span><span class="sxs-lookup"><span data-stu-id="9fc79-174">Queries</span></span>](../../../language-reference/queries/index.md)
