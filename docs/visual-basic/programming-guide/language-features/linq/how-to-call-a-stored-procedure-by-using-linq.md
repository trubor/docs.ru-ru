---
description: Дополнительные сведения о том, как вызвать хранимую процедуру с помощью LINQ (Visual Basic).
title: Практическое руководство. Вызов хранимой процедуры с помощью LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f6fca7ac008e5f0d5f68fdf9c192eaadae9412ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466332"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="20469-103">Практическое руководство. Вызов хранимой процедуры с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20469-103">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="20469-104">Запрос Language-Integrated (LINQ) упрощает доступ к информации базы данных, включая такие объекты базы данных, как хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="20469-104">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="20469-105">В следующем примере показано, как создать приложение, вызывающее хранимую процедуру в SQL Server базе данных.</span><span class="sxs-lookup"><span data-stu-id="20469-105">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="20469-106">В этом примере показано, как вызвать две различные хранимые процедуры в базе данных.</span><span class="sxs-lookup"><span data-stu-id="20469-106">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="20469-107">Каждая процедура возвращает результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="20469-107">Each procedure returns the results of a query.</span></span> <span data-ttu-id="20469-108">Одна процедура принимает входные параметры, а другая процедура не принимает параметры.</span><span class="sxs-lookup"><span data-stu-id="20469-108">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="20469-109">В примерах этого раздела используется учебная база данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="20469-109">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="20469-110">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="20469-110">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="20469-111">Инструкции см. в разделе [Загрузка образцов баз данных](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="20469-111">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="20469-112">Создание соединения с базой данных</span><span class="sxs-lookup"><span data-stu-id="20469-112">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="20469-113">В Visual Studio откройте **Обозреватель сервера** / **Обозреватель базы данных** , выбрав в  / меню **вид** пункт Обозреватель сервера **Обозреватель базы данных** .</span><span class="sxs-lookup"><span data-stu-id="20469-113">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="20469-114">Щелкните правой кнопкой мыши элемент **подключения к данным** в **Обозреватель сервера** / **Обозреватель базы данных** а затем выберите команду **Добавить подключение**.</span><span class="sxs-lookup"><span data-stu-id="20469-114">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="20469-115">Укажите допустимое соединение с образцом базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="20469-115">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="20469-116">Добавление проекта, содержащего файл LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="20469-116">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="20469-117">В меню **Файл** окна Visual Studio наведите указатель мыши на пункт **Создать** и щелкните **Проект**.</span><span class="sxs-lookup"><span data-stu-id="20469-117">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="20469-118">Выберите Visual Basic **Windows Forms приложение** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="20469-118">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="20469-119">В меню **Проект** выберите **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="20469-119">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="20469-120">Выберите шаблон элемента **LINQ to SQL классы** .</span><span class="sxs-lookup"><span data-stu-id="20469-120">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="20469-121">Задайте файлу имя `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="20469-121">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="20469-122">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="20469-122">Click **Add**.</span></span> <span data-ttu-id="20469-123">Для файла Northwind. dbml открыт реляционный конструктор объектов (реляционный конструктор R).</span><span class="sxs-lookup"><span data-stu-id="20469-123">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="20469-124">Добавление хранимых процедур в реляционный конструктор O/R</span><span class="sxs-lookup"><span data-stu-id="20469-124">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="20469-125">В **Обозреватель сервера** / **Обозреватель базы данных** разверните подключение к базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="20469-125">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="20469-126">Разверните папку **Хранимые процедуры** .</span><span class="sxs-lookup"><span data-stu-id="20469-126">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="20469-127">Если вы закрыли конструктор O/R, его можно открыть повторно, дважды щелкнув файл Northwind. dbml, который вы добавили ранее.</span><span class="sxs-lookup"><span data-stu-id="20469-127">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="20469-128">Щелкните хранимую процедуру **продажи по году** и перетащите ее на правую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="20469-128">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="20469-129">Щелкните **десять самых дорогих** хранимых процедур продуктов, перетащите ее на правую панель конструктора.</span><span class="sxs-lookup"><span data-stu-id="20469-129">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="20469-130">Сохраните изменения и закройте конструктор.</span><span class="sxs-lookup"><span data-stu-id="20469-130">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="20469-131">Сохраните проект.</span><span class="sxs-lookup"><span data-stu-id="20469-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="20469-132">Добавление кода для вывода результатов хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="20469-132">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="20469-133">Перетащите элемент управления из **области элементов** в <xref:System.Windows.Forms.DataGridView> форму Windows по умолчанию для проекта, Form1.</span><span class="sxs-lookup"><span data-stu-id="20469-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="20469-134">Дважды щелкните Form1, чтобы добавить код к `Load` событию.</span><span class="sxs-lookup"><span data-stu-id="20469-134">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="20469-135">При добавлении хранимых процедур в реляционный конструктор объектов конструктор добавил <xref:System.Data.Linq.DataContext> объект для проекта.</span><span class="sxs-lookup"><span data-stu-id="20469-135">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="20469-136">Этот объект содержит код, который необходим для доступа к этим процедурам.</span><span class="sxs-lookup"><span data-stu-id="20469-136">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="20469-137">Имя <xref:System.Data.Linq.DataContext> объекта для проекта определяется на основе имени DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="20469-137">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="20469-138">Для этого проекта объект называется <xref:System.Data.Linq.DataContext> `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="20469-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="20469-139">В коде можно создать экземпляр класса <xref:System.Data.Linq.DataContext> и вызвать методы хранимой процедуры, заданные в конструкторе O/R.</span><span class="sxs-lookup"><span data-stu-id="20469-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="20469-140">Чтобы выполнить привязку к <xref:System.Windows.Forms.DataGridView> объекту, может потребоваться принудительно выполнить запрос, вызвав <xref:System.Linq.Enumerable.ToList%2A> метод для результатов хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="20469-140">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="20469-141">Добавьте следующий код в `Load` событие для вызова любой из хранимых процедур, предоставляемых как методы для контекста данных.</span><span class="sxs-lookup"><span data-stu-id="20469-141">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="20469-142">Нажмите клавишу F5, чтобы запустить проект и просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="20469-142">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20469-143">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="20469-143">See also</span></span>

- [<span data-ttu-id="20469-144">LINQ</span><span class="sxs-lookup"><span data-stu-id="20469-144">LINQ</span></span>](index.md)
- [<span data-ttu-id="20469-145">Запросы</span><span class="sxs-lookup"><span data-stu-id="20469-145">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="20469-146">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="20469-146">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="20469-147">Методы DataContext (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="20469-147">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="20469-148">Практическое руководство. Назначение хранимых процедур для выполнения обновления, вставки и удаления (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="20469-148">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
