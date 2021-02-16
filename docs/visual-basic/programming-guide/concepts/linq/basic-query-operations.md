---
description: 'Дополнительные сведения: основные операции запросов (Visual Basic)'
title: Основные операции запроса
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 1f8fbda83c21fe9032415d96ff2d7e184083a839
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428692"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="927a5-103">Основные операции запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="927a5-103">Basic Query Operations (Visual Basic)</span></span>

<span data-ttu-id="927a5-104">В этом разделе приведены краткие сведения о выражениях Language-Integrated запросов (LINQ) в Visual Basic и некоторых типичных операциях, выполняемых в запросе.</span><span class="sxs-lookup"><span data-stu-id="927a5-104">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="927a5-105">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="927a5-105">For more information, see the following topics:</span></span>  
  
 <span data-ttu-id="927a5-106">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="927a5-106">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md)</span></span>  
  
 [<span data-ttu-id="927a5-107">Запросы</span><span class="sxs-lookup"><span data-stu-id="927a5-107">Queries</span></span>](../../../language-reference/queries/index.md)  
  
 [<span data-ttu-id="927a5-108">Пошаговое руководство. Написание запросов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="927a5-108">Walkthrough: Writing Queries in Visual Basic</span></span>](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="927a5-109">Указание источника данных (из)</span><span class="sxs-lookup"><span data-stu-id="927a5-109">Specifying the Data Source (From)</span></span>  

 <span data-ttu-id="927a5-110">В запросе LINQ первым шагом является указание источника данных, к которому необходимо выполнить запрос.</span><span class="sxs-lookup"><span data-stu-id="927a5-110">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="927a5-111">Таким образом, `From` предложение в запросе всегда происходит первым.</span><span class="sxs-lookup"><span data-stu-id="927a5-111">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="927a5-112">Операторы запросов выбирают и формируют результат на основе типа источника.</span><span class="sxs-lookup"><span data-stu-id="927a5-112">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="927a5-113">`From`Предложение задает источник данных, `customers` и *переменную диапазона* `cust` .</span><span class="sxs-lookup"><span data-stu-id="927a5-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="927a5-114">Переменная диапазона похожа на переменную итерации цикла, за исключением того, что в выражении запроса фактическая итерация не выполняется.</span><span class="sxs-lookup"><span data-stu-id="927a5-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="927a5-115">При выполнении запроса, часто с помощью `For Each` цикла, переменная диапазона выступает в качестве ссылки на каждый последовательный элемент в `customers` .</span><span class="sxs-lookup"><span data-stu-id="927a5-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="927a5-116">Так как компилятор может определить тип `cust`, нет необходимости указывать его в явном виде.</span><span class="sxs-lookup"><span data-stu-id="927a5-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="927a5-117">Примеры запросов, написанных с неявной типизацией и без них, см. [в разделе связи типов в операциях запроса (Visual Basic)](type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="927a5-118">Дополнительные сведения об использовании `From` предложения в Visual Basic см. в разделе [предложение from](../../../language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="927a5-119">Фильтрация данных (где)</span><span class="sxs-lookup"><span data-stu-id="927a5-119">Filtering Data (Where)</span></span>  

 <span data-ttu-id="927a5-120">Возможно, наиболее распространенной операцией запроса является применение фильтра в виде логического выражения.</span><span class="sxs-lookup"><span data-stu-id="927a5-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="927a5-121">Затем запрос возвращает только те элементы, для которых выражение имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="927a5-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="927a5-122">`Where`Для выполнения фильтрации используется предложение.</span><span class="sxs-lookup"><span data-stu-id="927a5-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="927a5-123">Фильтр указывает, какие элементы в источнике данных включить в результирующую последовательность.</span><span class="sxs-lookup"><span data-stu-id="927a5-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="927a5-124">В следующем примере включаются только клиенты, имеющие адрес в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="927a5-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="927a5-125">`And` `Or` Для объединения выражений фильтра в предложении можно использовать логические операторы, такие как и `Where` .</span><span class="sxs-lookup"><span data-stu-id="927a5-125">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="927a5-126">Например, чтобы возвратить только тех клиентов из Лондона, имя которых — Девон, используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="927a5-126">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="927a5-127">Чтобы вернуть клиентов из Лондона или Париж, используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="927a5-127">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="927a5-128">Дополнительные сведения об использовании `Where` предложения в Visual Basic см. в разделе [предложение WHERE](../../../language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-128">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="927a5-129">Упорядочение данных (ORDER BY)</span><span class="sxs-lookup"><span data-stu-id="927a5-129">Ordering Data (Order By)</span></span>  

 <span data-ttu-id="927a5-130">Часто бывает удобно сортировать возвращаемые данные в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="927a5-130">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="927a5-131">`Order By`Предложение приведет к сортировке элементов в возвращаемой последовательности по указанному полю или полям.</span><span class="sxs-lookup"><span data-stu-id="927a5-131">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="927a5-132">Например, следующий запрос сортирует результаты на основе `Name` Свойства.</span><span class="sxs-lookup"><span data-stu-id="927a5-132">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="927a5-133">Поскольку `Name` является строкой, возвращаемые данные будут отсортированы в алфавитном порядке от а до я.</span><span class="sxs-lookup"><span data-stu-id="927a5-133">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="927a5-134">Для упорядочения результатов в обратном порядке от Я до А используется предложение `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="927a5-134">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="927a5-135">Значение по умолчанию —, `Ascending` если не задан ни параметр, `Ascending` ни `Descending` значение.</span><span class="sxs-lookup"><span data-stu-id="927a5-135">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="927a5-136">Дополнительные сведения об использовании `Order By` предложения в Visual Basic см. в разделе [ORDER BY](../../../language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-136">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="927a5-137">Выбор данных (выбор)</span><span class="sxs-lookup"><span data-stu-id="927a5-137">Selecting Data (Select)</span></span>  

 <span data-ttu-id="927a5-138">`Select`Предложение задает форму и содержимое возвращаемых элементов.</span><span class="sxs-lookup"><span data-stu-id="927a5-138">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="927a5-139">Например, можно указать, будут ли результаты состоять из полных `Customer` объектов, всего одного `Customer` свойства, подмножества свойств, сочетания свойств из различных источников данных или какого-либо нового типа результата на основе вычислений.</span><span class="sxs-lookup"><span data-stu-id="927a5-139">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="927a5-140">Когда предложение `Select` создает что-либо отличное от копии исходного элемента, операция называется *проекцией*.</span><span class="sxs-lookup"><span data-stu-id="927a5-140">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="927a5-141">Чтобы получить коллекцию, состоящую из полных `Customer` объектов, выберите саму переменную диапазона:</span><span class="sxs-lookup"><span data-stu-id="927a5-141">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="927a5-142">Если `Customer` экземпляр является большим объектом, который содержит много полей, и все, что требуется получить, — это имя, можно выбрать `cust.Name` , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="927a5-142">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="927a5-143">Определение локального типа распознает, что это изменяет тип результата из коллекции `Customer` объектов на коллекцию строк.</span><span class="sxs-lookup"><span data-stu-id="927a5-143">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="927a5-144">Чтобы выбрать несколько полей из источника данных, доступны два варианта:</span><span class="sxs-lookup"><span data-stu-id="927a5-144">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="927a5-145">В `Select` предложении укажите поля, которые необходимо включить в результат.</span><span class="sxs-lookup"><span data-stu-id="927a5-145">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="927a5-146">Компилятор определит анонимный тип, в котором эти поля являются свойствами.</span><span class="sxs-lookup"><span data-stu-id="927a5-146">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="927a5-147">Дополнительные сведения см. в статье [Анонимные типы](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-147">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="927a5-148">Поскольку возвращаемые элементы в следующем примере являются экземплярами анонимного типа, нельзя ссылаться на тип по имени в любом расположении в коде.</span><span class="sxs-lookup"><span data-stu-id="927a5-148">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="927a5-149">Имя типа, назначенное компилятором, содержит символы, недопустимые в стандартном коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="927a5-149">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="927a5-150">В следующем примере элементы в коллекции, возвращаемые запросом в `londonCusts4` , являются экземплярами анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="927a5-150">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="927a5-151">-или-</span><span class="sxs-lookup"><span data-stu-id="927a5-151">-or-</span></span>  
  
- <span data-ttu-id="927a5-152">Определите именованный тип, содержащий определенные поля, которые необходимо включить в результат, и создайте и инициализируйте экземпляры типа в `Select` предложении.</span><span class="sxs-lookup"><span data-stu-id="927a5-152">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="927a5-153">Используйте этот параметр только в том случае, если необходимо использовать отдельные результаты вне коллекции, в которой они возвращаются, или если необходимо передать их в качестве параметров в вызовы метода.</span><span class="sxs-lookup"><span data-stu-id="927a5-153">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="927a5-154">`londonCusts5`В следующем примере в качестве типа используется IEnumerable (Of намефоне).</span><span class="sxs-lookup"><span data-stu-id="927a5-154">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="927a5-155">Дополнительные сведения об использовании `Select` предложения в Visual Basic см. в разделе [предложение SELECT](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-155">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="927a5-156">Соединение данных (присоединение и объединение групп)</span><span class="sxs-lookup"><span data-stu-id="927a5-156">Joining Data (Join and Group Join)</span></span>  

 <span data-ttu-id="927a5-157">В предложении можно объединить более одного источника данных `From` несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="927a5-157">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="927a5-158">Например, следующий код использует два источника данных и неявно объединяет свойства обоих из них в результате.</span><span class="sxs-lookup"><span data-stu-id="927a5-158">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="927a5-159">Запрос выбирает учащихся, чьи фамилии начинаются с гласной.</span><span class="sxs-lookup"><span data-stu-id="927a5-159">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="927a5-160">Этот код можно запустить со списком учащихся, созданных в ходе [создания списка элементов](how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-160">You can run this code with the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="927a5-161">`Join`Ключевое слово эквивалентно значению `INNER JOIN` в SQL.</span><span class="sxs-lookup"><span data-stu-id="927a5-161">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="927a5-162">Он объединяет две коллекции на основе совпадающих значений ключей между элементами в двух коллекциях.</span><span class="sxs-lookup"><span data-stu-id="927a5-162">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="927a5-163">Запрос возвращает все элементы коллекции, имеющие совпадающие значения ключей, или часть ее элементов.</span><span class="sxs-lookup"><span data-stu-id="927a5-163">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="927a5-164">Например, следующий код дублирует действие предыдущего неявного объединения.</span><span class="sxs-lookup"><span data-stu-id="927a5-164">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="927a5-165">`Group Join` объединяет коллекции в одну иерархическую коллекцию, как `LEFT JOIN` в SQL.</span><span class="sxs-lookup"><span data-stu-id="927a5-165">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="927a5-166">Дополнительные сведения см. в разделе [предложение Join](../../../language-reference/queries/join-clause.md) и [предложение Group Join](../../../language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-166">For more information, see [Join Clause](../../../language-reference/queries/join-clause.md) and [Group Join Clause](../../../language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="927a5-167">Группирование данных (Group By)</span><span class="sxs-lookup"><span data-stu-id="927a5-167">Grouping Data (Group By)</span></span>  

 <span data-ttu-id="927a5-168">Можно добавить `Group By` предложение для группирования элементов в результатах запроса в соответствии с одним или несколькими полями элементов.</span><span class="sxs-lookup"><span data-stu-id="927a5-168">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="927a5-169">Например, следующий код группирует учащихся по классу year.</span><span class="sxs-lookup"><span data-stu-id="927a5-169">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="927a5-170">Если запустить этот код с помощью списка учащихся, созданных в [инструкции по созданию списка элементов](how-to-create-a-list-of-items.md), выходные данные `For Each` инструкции будут:</span><span class="sxs-lookup"><span data-stu-id="927a5-170">If you run this code using the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="927a5-171">Год: младшие</span><span class="sxs-lookup"><span data-stu-id="927a5-171">Year: Junior</span></span>  
  
 <span data-ttu-id="927a5-172">Туккер, Майкл</span><span class="sxs-lookup"><span data-stu-id="927a5-172">Tucker, Michael</span></span>  
  
 <span data-ttu-id="927a5-173">Гарсиа, Хьюго</span><span class="sxs-lookup"><span data-stu-id="927a5-173">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="927a5-174">Гарсиа, Дебра</span><span class="sxs-lookup"><span data-stu-id="927a5-174">Garcia, Debra</span></span>  
  
 <span data-ttu-id="927a5-175">Туккер, Лэнс</span><span class="sxs-lookup"><span data-stu-id="927a5-175">Tucker, Lance</span></span>  
  
 <span data-ttu-id="927a5-176">Год: старший</span><span class="sxs-lookup"><span data-stu-id="927a5-176">Year: Senior</span></span>  
  
 <span data-ttu-id="927a5-177">Омелченко, Светлана</span><span class="sxs-lookup"><span data-stu-id="927a5-177">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="927a5-178">Осада, Мичико</span><span class="sxs-lookup"><span data-stu-id="927a5-178">Osada, Michiko</span></span>  
  
 <span data-ttu-id="927a5-179">Фахури, Фэди</span><span class="sxs-lookup"><span data-stu-id="927a5-179">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="927a5-180">Фенг, Ханинг</span><span class="sxs-lookup"><span data-stu-id="927a5-180">Feng, Hanying</span></span>  
  
 <span data-ttu-id="927a5-181">Адамс, Терри</span><span class="sxs-lookup"><span data-stu-id="927a5-181">Adams, Terry</span></span>  
  
 <span data-ttu-id="927a5-182">Year: свежая</span><span class="sxs-lookup"><span data-stu-id="927a5-182">Year: Freshman</span></span>  
  
 <span data-ttu-id="927a5-183">Мортенсен, Свен</span><span class="sxs-lookup"><span data-stu-id="927a5-183">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="927a5-184">Гарсиа, Сезар</span><span class="sxs-lookup"><span data-stu-id="927a5-184">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="927a5-185">Вариант, показанный в следующем коде, упорядочивает класс years, а затем упорядочивает учащихся в каждом году по фамилии.</span><span class="sxs-lookup"><span data-stu-id="927a5-185">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="927a5-186">Дополнительные сведения о см `Group By` . в разделе [предложение GROUP BY](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-186">For more information about `Group By`, see [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927a5-187">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="927a5-187">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="927a5-188">Приступая к работе с LINQ в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="927a5-188">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="927a5-189">Запросы</span><span class="sxs-lookup"><span data-stu-id="927a5-189">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="927a5-190">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="927a5-190">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="927a5-191">LINQ</span><span class="sxs-lookup"><span data-stu-id="927a5-191">LINQ</span></span>](../../language-features/linq/index.md)
