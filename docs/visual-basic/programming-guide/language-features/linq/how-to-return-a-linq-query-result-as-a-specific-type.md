---
description: Дополнительные сведения см. в статье как вернуть результат запроса LINQ в виде определенного типа (Visual Basic)
title: Практическое руководство. Возвращение результата запроса LINQ в виде определенного типа
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 8abeb3b5f174b1671415cbb55f35952e3bc77e7d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425663"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="68513-103">Практическое руководство. Возвращение результата запроса LINQ в виде определенного типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68513-103">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>

<span data-ttu-id="68513-104">Language-Integrated query (LINQ) упрощает доступ к сведениям о базе данных и выполнение запросов.</span><span class="sxs-lookup"><span data-stu-id="68513-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="68513-105">По умолчанию запросы LINQ возвращают список объектов в виде анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="68513-105">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="68513-106">Можно также указать, что запрос возвращает список определенного типа с помощью `Select` предложения.</span><span class="sxs-lookup"><span data-stu-id="68513-106">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="68513-107">В следующем примере показано, как создать новое приложение, которое выполняет запросы к базе данных SQL Server и проецирует результаты в виде определенного именованного типа.</span><span class="sxs-lookup"><span data-stu-id="68513-107">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="68513-108">Дополнительные сведения см. в разделе [анонимные типы](../objects-and-classes/anonymous-types.md) и [предложение SELECT](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="68513-108">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="68513-109">В примерах этого раздела используется учебная база данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="68513-109">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="68513-110">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="68513-110">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="68513-111">Инструкции см. в разделе [Загрузка образцов баз данных](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="68513-111">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="68513-112">Создание соединения с базой данных</span><span class="sxs-lookup"><span data-stu-id="68513-112">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="68513-113">В Visual Studio откройте **Обозреватель сервера** / **Обозреватель базы данных** , выбрав в  / меню **вид** пункт Обозреватель сервера **Обозреватель базы данных** .</span><span class="sxs-lookup"><span data-stu-id="68513-113">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="68513-114">Щелкните правой кнопкой мыши элемент **подключения к данным** в **Обозреватель сервера** / **Обозреватель базы данных** а затем выберите команду **Добавить подключение**.</span><span class="sxs-lookup"><span data-stu-id="68513-114">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="68513-115">Укажите допустимое соединение с образцом базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="68513-115">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="68513-116">Добавление проекта, содержащего файл LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="68513-116">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="68513-117">В меню **Файл** окна Visual Studio наведите указатель мыши на пункт **Создать** и щелкните **Проект**.</span><span class="sxs-lookup"><span data-stu-id="68513-117">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="68513-118">Выберите Visual Basic **Windows Forms приложение** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="68513-118">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="68513-119">В меню **Проект** выберите **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="68513-119">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="68513-120">Выберите шаблон элемента **LINQ to SQL классы** .</span><span class="sxs-lookup"><span data-stu-id="68513-120">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="68513-121">Задайте файлу имя `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="68513-121">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="68513-122">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="68513-122">Click **Add**.</span></span> <span data-ttu-id="68513-123">Для файла Northwind. dbml открыт реляционный конструктор объектов (реляционный конструктор R).</span><span class="sxs-lookup"><span data-stu-id="68513-123">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="68513-124">Добавление таблиц в запрос в реляционный конструктор O/R</span><span class="sxs-lookup"><span data-stu-id="68513-124">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="68513-125">В **Обозреватель сервера** / **Обозреватель базы данных** разверните подключение к базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="68513-125">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="68513-126">Разверните папку **Таблицы**.</span><span class="sxs-lookup"><span data-stu-id="68513-126">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="68513-127">Если вы закрыли конструктор O/R, его можно открыть повторно, дважды щелкнув файл Northwind. dbml, который вы добавили ранее.</span><span class="sxs-lookup"><span data-stu-id="68513-127">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="68513-128">Щелкните таблицу Customers (клиенты) и перетащите ее на левую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="68513-128">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="68513-129">Конструктор создает новый `Customer` объект для проекта.</span><span class="sxs-lookup"><span data-stu-id="68513-129">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="68513-130">Результат запроса можно проецировать в виде `Customer` типа или в виде создаваемого типа.</span><span class="sxs-lookup"><span data-stu-id="68513-130">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="68513-131">Этот пример создаст новый тип в следующей процедуре и запишет результат запроса в качестве этого типа.</span><span class="sxs-lookup"><span data-stu-id="68513-131">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="68513-132">Сохраните изменения и закройте конструктор.</span><span class="sxs-lookup"><span data-stu-id="68513-132">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="68513-133">Сохраните проект.</span><span class="sxs-lookup"><span data-stu-id="68513-133">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="68513-134">Добавление кода для запроса к базе данных и вывода результатов</span><span class="sxs-lookup"><span data-stu-id="68513-134">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="68513-135">Перетащите элемент управления из **области элементов** в <xref:System.Windows.Forms.DataGridView> форму Windows по умолчанию для проекта, Form1.</span><span class="sxs-lookup"><span data-stu-id="68513-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="68513-136">Дважды щелкните Form1, чтобы изменить класс Form1.</span><span class="sxs-lookup"><span data-stu-id="68513-136">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="68513-137">После `End Class` оператора класса Form1 добавьте следующий код, чтобы создать `CustomerInfo` тип для хранения результатов запроса для этого примера.</span><span class="sxs-lookup"><span data-stu-id="68513-137">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="68513-138">При добавлении таблиц в реляционный конструктор объектов конструктор добавил в <xref:System.Data.Linq.DataContext> проект объект.</span><span class="sxs-lookup"><span data-stu-id="68513-138">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="68513-139">Этот объект содержит код, который необходим для доступа к этим таблицам и для доступа к отдельным объектам и коллекциям для каждой таблицы.</span><span class="sxs-lookup"><span data-stu-id="68513-139">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="68513-140">Имя <xref:System.Data.Linq.DataContext> объекта для проекта определяется на основе имени DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="68513-140">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="68513-141">Для этого проекта объект называется <xref:System.Data.Linq.DataContext> `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="68513-141">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="68513-142">В коде можно создать экземпляр класса <xref:System.Data.Linq.DataContext> и запросить таблицы, заданные конструктором O/R.</span><span class="sxs-lookup"><span data-stu-id="68513-142">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="68513-143">В `Load` событии класса Form1 добавьте следующий код для запроса таблиц, предоставляемых как свойства контекста данных.</span><span class="sxs-lookup"><span data-stu-id="68513-143">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="68513-144">`Select`Предложение запроса создаст новый `CustomerInfo` тип, а не анонимный тип для каждого элемента результата запроса.</span><span class="sxs-lookup"><span data-stu-id="68513-144">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="68513-145">Нажмите клавишу F5, чтобы запустить проект и просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="68513-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68513-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="68513-146">See also</span></span>

- [<span data-ttu-id="68513-147">LINQ</span><span class="sxs-lookup"><span data-stu-id="68513-147">LINQ</span></span>](index.md)
- [<span data-ttu-id="68513-148">Запросы</span><span class="sxs-lookup"><span data-stu-id="68513-148">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="68513-149">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="68513-149">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="68513-150">Методы DataContext (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="68513-150">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
