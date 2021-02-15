---
description: Дополнительные сведения см. в статье как найти минимальное или максимальное значение в результатах запроса с помощью LINQ (Visual Basic).
title: Практическое руководство. Поиск минимального или максимального значения в результатах запроса с помощью LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: e6337b61b01d720bd37390f61e4e285aa150ec3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422811"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="8239e-103">Практическое руководство. Поиск минимального или максимального значения в результатах запроса с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8239e-103">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="8239e-104">Language-Integrated query (LINQ) упрощает доступ к сведениям о базе данных и выполнение запросов.</span><span class="sxs-lookup"><span data-stu-id="8239e-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="8239e-105">В следующем примере показано, как создать новое приложение, которое выполняет запросы к базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8239e-105">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="8239e-106">Образец определяет минимальное и максимальное значения для результатов с помощью `Aggregate` `Group By` предложений и.</span><span class="sxs-lookup"><span data-stu-id="8239e-106">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="8239e-107">Дополнительные сведения см. в разделе [предложение Aggregate](../../../language-reference/queries/aggregate-clause.md) и [предложение GROUP BY](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8239e-107">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="8239e-108">В примерах этого раздела используется учебная база данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8239e-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8239e-109">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8239e-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="8239e-110">Инструкции см. в разделе [Загрузка образцов баз данных](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8239e-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="8239e-111">Создание соединения с базой данных</span><span class="sxs-lookup"><span data-stu-id="8239e-111">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="8239e-112">В Visual Studio откройте **Обозреватель сервера** / **Обозреватель базы данных** , выбрав в  / меню **вид** пункт Обозреватель сервера **Обозреватель базы данных** .</span><span class="sxs-lookup"><span data-stu-id="8239e-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="8239e-113">Щелкните правой кнопкой мыши элемент **подключения к данным** в **Обозреватель сервера** / **Обозреватель базы данных** а затем выберите команду **Добавить подключение**.</span><span class="sxs-lookup"><span data-stu-id="8239e-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="8239e-114">Укажите допустимое соединение с образцом базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8239e-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="8239e-115">Добавление проекта, содержащего файл LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8239e-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="8239e-116">В меню **Файл** окна Visual Studio наведите указатель мыши на пункт **Создать** и щелкните **Проект**.</span><span class="sxs-lookup"><span data-stu-id="8239e-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8239e-117">Выберите Visual Basic **Windows Forms приложение** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="8239e-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="8239e-118">В меню **Проект** выберите **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="8239e-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8239e-119">Выберите шаблон элемента **LINQ to SQL классы** .</span><span class="sxs-lookup"><span data-stu-id="8239e-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="8239e-120">Задайте файлу имя `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="8239e-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8239e-121">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="8239e-121">Click **Add**.</span></span> <span data-ttu-id="8239e-122">Для файла Northwind. dbml открыт реляционный конструктор объектов (реляционный конструктор R).</span><span class="sxs-lookup"><span data-stu-id="8239e-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="8239e-123">Добавление таблиц в запрос в реляционный конструктор O/R</span><span class="sxs-lookup"><span data-stu-id="8239e-123">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="8239e-124">В **Обозреватель сервера** / **Обозреватель базы данных** разверните подключение к базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8239e-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8239e-125">Разверните папку **Таблицы**.</span><span class="sxs-lookup"><span data-stu-id="8239e-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="8239e-126">Если вы закрыли конструктор O/R, его можно открыть повторно, дважды щелкнув файл Northwind. dbml, который вы добавили ранее.</span><span class="sxs-lookup"><span data-stu-id="8239e-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="8239e-127">Щелкните таблицу Customers (клиенты) и перетащите ее на левую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="8239e-127">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="8239e-128">Щелкните таблицу Orders и перетащите ее на левую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="8239e-128">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="8239e-129">Конструктор создает `Customer` `Order` для проекта новые объекты и.</span><span class="sxs-lookup"><span data-stu-id="8239e-129">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="8239e-130">Обратите внимание, что конструктор автоматически обнаруживает связи между таблицами и создает дочерние свойства для связанных объектов.</span><span class="sxs-lookup"><span data-stu-id="8239e-130">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="8239e-131">Например, IntelliSense покажет, что `Customer` объект имеет `Orders` свойство для всех заказов, связанных с этим клиентом.</span><span class="sxs-lookup"><span data-stu-id="8239e-131">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="8239e-132">Сохраните изменения и закройте конструктор.</span><span class="sxs-lookup"><span data-stu-id="8239e-132">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="8239e-133">Сохраните проект.</span><span class="sxs-lookup"><span data-stu-id="8239e-133">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="8239e-134">Добавление кода для запроса к базе данных и отображение результатов</span><span class="sxs-lookup"><span data-stu-id="8239e-134">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="8239e-135">Перетащите элемент управления из **области элементов** в <xref:System.Windows.Forms.DataGridView> форму Windows по умолчанию для проекта, Form1.</span><span class="sxs-lookup"><span data-stu-id="8239e-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="8239e-136">Дважды щелкните Form1, чтобы добавить код в `Load` событие в форме.</span><span class="sxs-lookup"><span data-stu-id="8239e-136">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="8239e-137">При добавлении таблиц в реляционный конструктор объектов конструктор добавил <xref:System.Data.Linq.DataContext> объект для проекта.</span><span class="sxs-lookup"><span data-stu-id="8239e-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="8239e-138">Этот объект содержит код, который необходим для доступа к этим таблицам, в дополнение к отдельным объектам и коллекциям для каждой таблицы.</span><span class="sxs-lookup"><span data-stu-id="8239e-138">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="8239e-139">Имя <xref:System.Data.Linq.DataContext> объекта для проекта определяется на основе имени DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="8239e-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8239e-140">Для этого проекта объект называется <xref:System.Data.Linq.DataContext> `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="8239e-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="8239e-141">В коде можно создать экземпляр класса <xref:System.Data.Linq.DataContext> и запросить таблицы, заданные конструктором O/R.</span><span class="sxs-lookup"><span data-stu-id="8239e-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="8239e-142">Добавьте следующий код в `Load` событие.</span><span class="sxs-lookup"><span data-stu-id="8239e-142">Add the following code to the `Load` event.</span></span> <span data-ttu-id="8239e-143">Этот код запрашивает таблицы, предоставляемые как свойства контекста данных, и определяет минимальное и максимальное значения для результатов.</span><span class="sxs-lookup"><span data-stu-id="8239e-143">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="8239e-144">В примере предложение используется `Aggregate` для запроса одного результата, а предложение — для `Group By` отображения среднего для сгруппированных результатов.</span><span class="sxs-lookup"><span data-stu-id="8239e-144">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="8239e-145">Нажмите клавишу **F5** , чтобы запустить проект и просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="8239e-145">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8239e-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8239e-146">See also</span></span>

- [<span data-ttu-id="8239e-147">LINQ</span><span class="sxs-lookup"><span data-stu-id="8239e-147">LINQ</span></span>](index.md)
- [<span data-ttu-id="8239e-148">Запросы</span><span class="sxs-lookup"><span data-stu-id="8239e-148">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="8239e-149">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8239e-149">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="8239e-150">Методы DataContext (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="8239e-150">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
