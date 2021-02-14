---
description: Дополнительные сведения см. в статье как изменить данные в базе данных с помощью LINQ (Visual Basic).
title: Практическое руководство. Изменение данных в базе данных с помощью LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: b58ca542fbc6f4d63705e45b53edc8ded83ab88b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422774"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="8d35e-103">Практическое руководство. Изменение данных в базе данных с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d35e-103">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="8d35e-104">Запросы Language-Integrated запросов (LINQ) упрощают доступ к сведениям о базе данных и изменяют значения в базе данных.</span><span class="sxs-lookup"><span data-stu-id="8d35e-104">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="8d35e-105">В следующем примере показано, как создать новое приложение, которое извлекает и обновляет сведения в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8d35e-105">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="8d35e-106">В примерах этого раздела используется учебная база данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8d35e-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8d35e-107">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8d35e-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="8d35e-108">Инструкции см. в разделе [Загрузка образцов баз данных](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8d35e-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="8d35e-109">Создание соединения с базой данных</span><span class="sxs-lookup"><span data-stu-id="8d35e-109">To create a connection to a database</span></span>

1. <span data-ttu-id="8d35e-110">В Visual Studio откройте **Обозреватель сервера** / **Обозреватель базы данных** , выбрав в меню **вид** пункт **Обозреватель сервера** / **Обозреватель базы данных**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="8d35e-111">Щелкните правой кнопкой мыши элемент **подключения к данным** в **Обозреватель сервера** / **Обозреватель базы данных** и выберите команду **Добавить подключение**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="8d35e-112">Укажите допустимое соединение с образцом базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8d35e-112">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="8d35e-113">Добавление проекта с файлом LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8d35e-113">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="8d35e-114">В меню **Файл** окна Visual Studio наведите указатель мыши на пункт **Создать** и щелкните **Проект**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8d35e-115">Выберите Visual Basic **Windows Forms приложение** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="8d35e-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="8d35e-116">В меню **Проект** выберите **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8d35e-117">Выберите шаблон элемента **LINQ to SQL классы** .</span><span class="sxs-lookup"><span data-stu-id="8d35e-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="8d35e-118">Задайте файлу имя `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="8d35e-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8d35e-119">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-119">Click **Add**.</span></span> <span data-ttu-id="8d35e-120">Для файла открывается реляционный конструктор объектов (реляционный конструктор R) `northwind.dbml` .</span><span class="sxs-lookup"><span data-stu-id="8d35e-120">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="8d35e-121">Добавление таблиц к запросам и их изменение в конструкторе</span><span class="sxs-lookup"><span data-stu-id="8d35e-121">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="8d35e-122">В **Обозреватель сервера** / **Обозреватель базы данных** разверните подключение к базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8d35e-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8d35e-123">Разверните папку **Таблицы**.</span><span class="sxs-lookup"><span data-stu-id="8d35e-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="8d35e-124">Если вы закрыли конструктор O/R, его можно открыть повторно, дважды щелкнув `northwind.dbml` файл, добавленный ранее.</span><span class="sxs-lookup"><span data-stu-id="8d35e-124">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="8d35e-125">Щелкните таблицу Customers (клиенты) и перетащите ее на левую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="8d35e-125">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="8d35e-126">Конструктор создает новый объект Customer для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="8d35e-126">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="8d35e-127">Сохраните изменения и закройте конструктор.</span><span class="sxs-lookup"><span data-stu-id="8d35e-127">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="8d35e-128">Сохраните проект.</span><span class="sxs-lookup"><span data-stu-id="8d35e-128">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="8d35e-129">Добавление кода для изменения базы данных и вывода результатов</span><span class="sxs-lookup"><span data-stu-id="8d35e-129">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="8d35e-130">Перетащите элемент управления из **области элементов** в <xref:System.Windows.Forms.DataGridView> форму Windows по умолчанию для проекта, Form1.</span><span class="sxs-lookup"><span data-stu-id="8d35e-130">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="8d35e-131">При добавлении таблиц в реляционный конструктор объектов конструктор добавил в <xref:System.Data.Linq.DataContext> проект объект.</span><span class="sxs-lookup"><span data-stu-id="8d35e-131">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="8d35e-132">Этот объект содержит код, который можно использовать для доступа к таблице Customers.</span><span class="sxs-lookup"><span data-stu-id="8d35e-132">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="8d35e-133">Он также содержит код, который определяет локальный объект Customer и коллекцию Customers для таблицы.</span><span class="sxs-lookup"><span data-stu-id="8d35e-133">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="8d35e-134">Имя <xref:System.Data.Linq.DataContext> объекта для проекта определяется на основе имени DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="8d35e-134">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8d35e-135">Для этого проекта объект называется <xref:System.Data.Linq.DataContext> `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="8d35e-135">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="8d35e-136">Можно создать экземпляр <xref:System.Data.Linq.DataContext> объекта в коде и запросить и изменить коллекцию Customers, указанную в конструкторе O/R.</span><span class="sxs-lookup"><span data-stu-id="8d35e-136">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="8d35e-137">Изменения, вносимые в коллекцию Customers, не отражаются в базе данных до их отправки путем вызова <xref:System.Data.Linq.DataContext.SubmitChanges%2A> метода <xref:System.Data.Linq.DataContext> объекта.</span><span class="sxs-lookup"><span data-stu-id="8d35e-137">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="8d35e-138">Дважды щелкните форму Windows Forms, форму Form1, чтобы добавить код в <xref:System.Windows.Forms.Form.Load> событие, чтобы запросить таблицу Customers, доступную в качестве свойства <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="8d35e-138">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="8d35e-139">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8d35e-139">Add the following code:</span></span>

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. <span data-ttu-id="8d35e-140">Перетащите на форму три элемента управления из **панели элементов** <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="8d35e-140">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="8d35e-141">Выберите первый `Button` элемент управления.</span><span class="sxs-lookup"><span data-stu-id="8d35e-141">Select the first `Button` control.</span></span> <span data-ttu-id="8d35e-142">В окне **Свойства** присвойте свойству `Name` `Button` элемента управления значение `AddButton` и значение `Text` `Add` .</span><span class="sxs-lookup"><span data-stu-id="8d35e-142">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="8d35e-143">Нажмите вторую кнопку и задайте `Name` свойству значение `UpdateButton` , а `Text` свойству — значение `Update` .</span><span class="sxs-lookup"><span data-stu-id="8d35e-143">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="8d35e-144">Нажмите третью кнопку и задайте `Name` свойству значение `DeleteButton` , а `Text` свойству — значение `Delete` .</span><span class="sxs-lookup"><span data-stu-id="8d35e-144">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="8d35e-145">Дважды щелкните кнопку **Добавить** , чтобы добавить код к `Click` событию.</span><span class="sxs-lookup"><span data-stu-id="8d35e-145">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="8d35e-146">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8d35e-146">Add the following code:</span></span>

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. <span data-ttu-id="8d35e-147">Дважды щелкните кнопку " **Обновить** ", чтобы добавить код в `Click` событие.</span><span class="sxs-lookup"><span data-stu-id="8d35e-147">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="8d35e-148">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8d35e-148">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="8d35e-149">Дважды щелкните кнопку **Удалить** , чтобы добавить код в `Click` событие.</span><span class="sxs-lookup"><span data-stu-id="8d35e-149">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="8d35e-150">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8d35e-150">Add the following code:</span></span>

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. <span data-ttu-id="8d35e-151">Нажмите клавишу F5 для запуска проекта.</span><span class="sxs-lookup"><span data-stu-id="8d35e-151">Press F5 to run your project.</span></span> <span data-ttu-id="8d35e-152">Нажмите кнопку **Добавить** , чтобы добавить новую запись.</span><span class="sxs-lookup"><span data-stu-id="8d35e-152">Click **Add** to add a new record.</span></span> <span data-ttu-id="8d35e-153">Нажмите кнопку **Обновить** , чтобы изменить новую запись.</span><span class="sxs-lookup"><span data-stu-id="8d35e-153">Click **Update** to modify the new record.</span></span> <span data-ttu-id="8d35e-154">Нажмите кнопку **Удалить** , чтобы удалить новую запись.</span><span class="sxs-lookup"><span data-stu-id="8d35e-154">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d35e-155">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8d35e-155">See also</span></span>

- [<span data-ttu-id="8d35e-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="8d35e-156">LINQ</span></span>](index.md)
- [<span data-ttu-id="8d35e-157">Запросы</span><span class="sxs-lookup"><span data-stu-id="8d35e-157">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="8d35e-158">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8d35e-158">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="8d35e-159">Методы DataContext (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="8d35e-159">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="8d35e-160">Практическое руководство. Назначение хранимых процедур для выполнения обновления, вставки и удаления (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="8d35e-160">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
