---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Написание запросов в Visual Basic
title: Написание запросов
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 55a1b3382d587b7982b79448334c4688895fa6e6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466813"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="99d64-103">Пошаговое руководство. Написание запросов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99d64-103">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="99d64-104">В этом пошаговом руководстве показано, как можно использовать функции языка Visual Basic для написания выражений запросов Language-Integrated запросов (LINQ).</span><span class="sxs-lookup"><span data-stu-id="99d64-104">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="99d64-105">В этом пошаговом руководстве показано, как создавать запросы к списку объектов Student, выполнять запросы и изменять их.</span><span class="sxs-lookup"><span data-stu-id="99d64-105">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="99d64-106">Запросы включают в себя несколько функций, включая инициализаторы объектов, определение локального типа и анонимные типы.</span><span class="sxs-lookup"><span data-stu-id="99d64-106">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="99d64-107">После завершения этого пошагового руководства вы будете готовы перейти к образцам и документации для конкретного интересующего поставщика LINQ.</span><span class="sxs-lookup"><span data-stu-id="99d64-107">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="99d64-108">Поставщики LINQ включают [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99d64-108">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="99d64-109">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="99d64-109">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="99d64-110">Создание проекта консольного приложения</span><span class="sxs-lookup"><span data-stu-id="99d64-110">To create a console application project</span></span>

1. <span data-ttu-id="99d64-111">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99d64-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="99d64-112">В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.</span><span class="sxs-lookup"><span data-stu-id="99d64-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="99d64-113">В списке **Установленные шаблоны** щелкните **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="99d64-113">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="99d64-114">В списке типов проектов щелкните **консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="99d64-114">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="99d64-115">В поле **имя** введите имя проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="99d64-115">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="99d64-116">Создается проект.</span><span class="sxs-lookup"><span data-stu-id="99d64-116">A project is created.</span></span> <span data-ttu-id="99d64-117">По умолчанию он содержит ссылку на System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="99d64-117">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="99d64-118">Кроме того, в списке **Импортированные пространства имен** на [странице ссылки в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) содержится <xref:System.Linq?displayProperty=nameWithType> пространство имен.</span><span class="sxs-lookup"><span data-stu-id="99d64-118">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="99d64-119">На [странице Компиляция в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)убедитесь, что **параметр Infer** имеет значение **On**.</span><span class="sxs-lookup"><span data-stu-id="99d64-119">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="99d64-120">Добавление источника данных In-Memory</span><span class="sxs-lookup"><span data-stu-id="99d64-120">Add an In-Memory Data Source</span></span>

<span data-ttu-id="99d64-121">Источником данных для запросов в этом пошаговом руководстве является список `Student` объектов.</span><span class="sxs-lookup"><span data-stu-id="99d64-121">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="99d64-122">Каждый `Student` объект содержит имя, фамилию, класс year и академический рейтинг в тексте учащегося.</span><span class="sxs-lookup"><span data-stu-id="99d64-122">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="99d64-123">Добавление источника данных</span><span class="sxs-lookup"><span data-stu-id="99d64-123">To add the data source</span></span>

- <span data-ttu-id="99d64-124">Определите `Student` класс и создайте список экземпляров класса.</span><span class="sxs-lookup"><span data-stu-id="99d64-124">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="99d64-125">Код, необходимый для определения `Student` класса и создания списка, используемого в примерах пошагового руководства, приведен в разделе [Практическое руководство. Создание списка элементов](how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="99d64-125">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="99d64-126">Вы можете скопировать его из него и вставить в проект.</span><span class="sxs-lookup"><span data-stu-id="99d64-126">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="99d64-127">Новый код заменяет код, который отображался при создании проекта.</span><span class="sxs-lookup"><span data-stu-id="99d64-127">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="99d64-128">Добавление нового учащегося в список учащихся</span><span class="sxs-lookup"><span data-stu-id="99d64-128">To add a new student to the students list</span></span>

- <span data-ttu-id="99d64-129">Следуйте шаблону в `getStudents` методе, чтобы добавить в список другой экземпляр `Student` класса.</span><span class="sxs-lookup"><span data-stu-id="99d64-129">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="99d64-130">При добавлении учащегося будут представлены инициализаторы объектов.</span><span class="sxs-lookup"><span data-stu-id="99d64-130">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="99d64-131">Дополнительные сведения см. в разделе [инициализаторы объектов: именованные и анонимные типы](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="99d64-131">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="99d64-132">Создание запроса</span><span class="sxs-lookup"><span data-stu-id="99d64-132">Create a Query</span></span>

<span data-ttu-id="99d64-133">При выполнении запроса, добавленного в этом разделе, создается список учащихся, чьи учебные заведения помещают в десять первых.</span><span class="sxs-lookup"><span data-stu-id="99d64-133">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="99d64-134">Поскольку запрос выбирает полный `Student` объект каждый раз, тип результата запроса — `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="99d64-134">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="99d64-135">Однако тип запроса обычно не указывается в определениях запросов.</span><span class="sxs-lookup"><span data-stu-id="99d64-135">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="99d64-136">Вместо этого компилятор использует определение локального типа для определения типа.</span><span class="sxs-lookup"><span data-stu-id="99d64-136">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="99d64-137">Дополнительные сведения см. в разделе [определение локального типа](../../language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="99d64-137">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="99d64-138">Переменная диапазона запроса, выступает в `currentStudent` качестве ссылки на каждый `Student` экземпляр в источнике, `students` предоставляя доступ к свойствам каждого объекта в `students` .</span><span class="sxs-lookup"><span data-stu-id="99d64-138">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="99d64-139">Создание простого запроса</span><span class="sxs-lookup"><span data-stu-id="99d64-139">To create a simple query</span></span>

1. <span data-ttu-id="99d64-140">Найдите место в `Main` методе проекта, который помечен следующим образом:</span><span class="sxs-lookup"><span data-stu-id="99d64-140">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="99d64-141">Скопируйте приведенный ниже код и вставьте его в.</span><span class="sxs-lookup"><span data-stu-id="99d64-141">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="99d64-142">Наведите указатель мыши на `studentQuery` код, чтобы убедиться, что назначенный компилятором тип имеет значение `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="99d64-142">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="99d64-143">Выполнение запроса</span><span class="sxs-lookup"><span data-stu-id="99d64-143">Run the Query</span></span>

<span data-ttu-id="99d64-144">Переменная `studentQuery` содержит определение запроса, а не результаты выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="99d64-144">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="99d64-145">Типичный механизм выполнения запроса — `For Each` цикл.</span><span class="sxs-lookup"><span data-stu-id="99d64-145">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="99d64-146">Доступ к каждому элементу в возвращаемой последовательности осуществляется через переменную итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="99d64-146">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="99d64-147">Дополнительные сведения о выполнении запросов см. [в разделе Написание первого запроса LINQ](writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="99d64-147">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="99d64-148">Выполнение запроса</span><span class="sxs-lookup"><span data-stu-id="99d64-148">To run the query</span></span>

1. <span data-ttu-id="99d64-149">Добавьте следующий `For Each` цикл под запросом в проекте.</span><span class="sxs-lookup"><span data-stu-id="99d64-149">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="99d64-150">Наведите указатель мыши на переменную управления циклом, `studentRecord` чтобы увидеть ее тип данных.</span><span class="sxs-lookup"><span data-stu-id="99d64-150">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="99d64-151">Тип `studentRecord` выводится `Student` как, так как `studentQuery` возвращает коллекцию `Student` экземпляров.</span><span class="sxs-lookup"><span data-stu-id="99d64-151">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="99d64-152">Выполните сборку и запустите приложение, нажав клавиши CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="99d64-152">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="99d64-153">Обратите внимание на результаты в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="99d64-153">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="99d64-154">Изменение запроса</span><span class="sxs-lookup"><span data-stu-id="99d64-154">Modify the Query</span></span>

<span data-ttu-id="99d64-155">Проще проверять результаты запроса, если они находятся в указанном порядке.</span><span class="sxs-lookup"><span data-stu-id="99d64-155">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="99d64-156">Возвращаемую последовательность можно отсортировать на основе любого доступного поля.</span><span class="sxs-lookup"><span data-stu-id="99d64-156">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="99d64-157">Упорядочение результатов</span><span class="sxs-lookup"><span data-stu-id="99d64-157">To order the results</span></span>

1. <span data-ttu-id="99d64-158">Добавьте следующее `Order By` предложение между `Where` оператором и `Select` инструкцией запроса.</span><span class="sxs-lookup"><span data-stu-id="99d64-158">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="99d64-159">`Order By`Предложение упорядочивает результаты в алфавитном порядке от A до Z в соответствии с фамилией каждого учащегося.</span><span class="sxs-lookup"><span data-stu-id="99d64-159">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="99d64-160">Чтобы упорядочить по фамилии, а затем по имени, добавьте в запрос оба поля:</span><span class="sxs-lookup"><span data-stu-id="99d64-160">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="99d64-161">Можно также указать `Descending` Порядок от я до а.</span><span class="sxs-lookup"><span data-stu-id="99d64-161">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="99d64-162">Выполните сборку и запустите приложение, нажав клавиши CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="99d64-162">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="99d64-163">Обратите внимание на результаты в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="99d64-163">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="99d64-164">Введение локального идентификатора</span><span class="sxs-lookup"><span data-stu-id="99d64-164">To introduce a local identifier</span></span>

1. <span data-ttu-id="99d64-165">Добавьте код в этом разделе, чтобы ввести локальный идентификатор в выражение запроса.</span><span class="sxs-lookup"><span data-stu-id="99d64-165">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="99d64-166">Локальный идентификатор будет содержать промежуточный результат.</span><span class="sxs-lookup"><span data-stu-id="99d64-166">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="99d64-167">В следующем примере `name` — это идентификатор, содержащий объединение имени и фамилии учащегося.</span><span class="sxs-lookup"><span data-stu-id="99d64-167">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="99d64-168">Локальный идентификатор можно использовать для удобства или повысить производительность, сохранив результаты выражения, которые в противном случае будут вычисляться несколько раз.</span><span class="sxs-lookup"><span data-stu-id="99d64-168">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="99d64-169">Выполните сборку и запустите приложение, нажав клавиши CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="99d64-169">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="99d64-170">Обратите внимание на результаты в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="99d64-170">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="99d64-171">Проецирование одного поля в предложении SELECT</span><span class="sxs-lookup"><span data-stu-id="99d64-171">To project one field in the Select clause</span></span>

1. <span data-ttu-id="99d64-172">Добавьте запрос и `For Each` цикл из этого раздела, чтобы создать запрос, который создает последовательность, элементы которой отличаются от элементов в источнике.</span><span class="sxs-lookup"><span data-stu-id="99d64-172">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="99d64-173">В следующем примере источником является коллекция `Student` объектов, но возвращается только один элемент каждого объекта: имена учащихся, чье фамилия — Гарсиа.</span><span class="sxs-lookup"><span data-stu-id="99d64-173">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="99d64-174">Так как `currentStudent.First` является строкой, тип данных последовательности, возвращаемой `studentQuery3` , — это `IEnumerable(Of String)` последовательность строк.</span><span class="sxs-lookup"><span data-stu-id="99d64-174">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="99d64-175">Как и в предыдущих примерах, для определения типа данных для `studentQuery3` компилятора необходимо определить, используя вывод локального типа.</span><span class="sxs-lookup"><span data-stu-id="99d64-175">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="99d64-176">Наведите указатель мыши на `studentQuery3` код, чтобы убедиться, что назначенный тип имеет значение `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="99d64-176">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="99d64-177">Выполните сборку и запустите приложение, нажав клавиши CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="99d64-177">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="99d64-178">Обратите внимание на результаты в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="99d64-178">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="99d64-179">Создание анонимного типа в предложении SELECT</span><span class="sxs-lookup"><span data-stu-id="99d64-179">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="99d64-180">Добавьте код из этого раздела, чтобы увидеть, как анонимные типы используются в запросах.</span><span class="sxs-lookup"><span data-stu-id="99d64-180">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="99d64-181">Они используются в запросах, если требуется вернуть несколько полей из источника данных, а не полные записи ( `currentStudent` записи в предыдущих примерах) или отдельные поля ( `First` в предыдущем разделе).</span><span class="sxs-lookup"><span data-stu-id="99d64-181">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="99d64-182">Вместо определения нового именованного типа, содержащего поля, которые необходимо включить в результат, необходимо указать поля в `Select` предложении, и компилятор создаст анонимный тип с этими полями в качестве свойств.</span><span class="sxs-lookup"><span data-stu-id="99d64-182">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="99d64-183">Дополнительные сведения см. в статье [Анонимные типы](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="99d64-183">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="99d64-184">В следующем примере создается запрос, который возвращает имя и звание старших званий, чьи учебные заведения находятся в диапазоне от 1 до 10 в порядке академических званий.</span><span class="sxs-lookup"><span data-stu-id="99d64-184">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="99d64-185">В этом примере тип `studentQuery4` должен быть определен, поскольку `Select` предложение возвращает экземпляр анонимного типа, а анонимный тип не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="99d64-185">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="99d64-186">Выполните сборку и запустите приложение, нажав клавиши CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="99d64-186">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="99d64-187">Обратите внимание на результаты в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="99d64-187">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="99d64-188">Дополнительные примеры</span><span class="sxs-lookup"><span data-stu-id="99d64-188">Additional Examples</span></span>

<span data-ttu-id="99d64-189">Теперь, когда вы понимаете основы, ниже приведен список дополнительных примеров для демонстрации гибкости и возможностей запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="99d64-189">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="99d64-190">Каждому примеру предшествует краткое описание того, что он делает.</span><span class="sxs-lookup"><span data-stu-id="99d64-190">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="99d64-191">Наведите указатель мыши на переменную результата запроса для каждого запроса, чтобы увидеть выведенный тип.</span><span class="sxs-lookup"><span data-stu-id="99d64-191">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="99d64-192">`For Each`Для получения результатов используйте цикл.</span><span class="sxs-lookup"><span data-stu-id="99d64-192">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="99d64-193">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="99d64-193">Additional Information</span></span>

<span data-ttu-id="99d64-194">После ознакомления с основными понятиями работы с запросами вы можете ознакомиться с документацией и примерами для конкретного типа поставщика LINQ, который вас интересует:</span><span class="sxs-lookup"><span data-stu-id="99d64-194">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="99d64-195">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="99d64-195">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="99d64-196">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="99d64-196">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="99d64-197">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="99d64-197">LINQ to XML</span></span>](../../../../standard/linq/linq-xml-overview.md)

- [<span data-ttu-id="99d64-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="99d64-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="99d64-199">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="99d64-199">See also</span></span>

- [<span data-ttu-id="99d64-200">LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d64-200">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="99d64-201">Приступая к работе с LINQ в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99d64-201">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="99d64-202">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="99d64-202">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="99d64-203">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="99d64-203">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="99d64-204">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="99d64-204">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- <span data-ttu-id="99d64-205">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d64-205">[Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="99d64-206">LINQ</span><span class="sxs-lookup"><span data-stu-id="99d64-206">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="99d64-207">Запросы</span><span class="sxs-lookup"><span data-stu-id="99d64-207">Queries</span></span>](../../../language-reference/queries/index.md)
