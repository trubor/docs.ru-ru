---
description: Дополнительные сведения см. в разделе Пошаговое руководство. использование только хранимых процедур (C#)
title: Пошаговое руководство. Применение только хранимых процедур (C#)
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 89cb6da9ec4e8d144726b6e3575a32c04d6aeec0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791781"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="b95a2-103">Пошаговое руководство. Применение только хранимых процедур (C#)</span><span class="sxs-lookup"><span data-stu-id="b95a2-103">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="b95a2-104">В данном пошаговом руководстве представлен основной полный сценарий [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для получения доступа к данным, выполняя только хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="b95a2-104">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="b95a2-105">Этот метод часто используется администраторами баз данных для ограничения способов получения доступа к хранилищам данных.</span><span class="sxs-lookup"><span data-stu-id="b95a2-105">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="b95a2-106">Хранимые процедуры можно также использовать в приложениях [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для переопределения поведения по умолчанию, особенно для процессов `Create`, `Update` и `Delete`.</span><span class="sxs-lookup"><span data-stu-id="b95a2-106">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="b95a2-107">Дополнительные сведения см. в разделе [Настройка операций вставки, обновления и удаления](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b95a2-107">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="b95a2-108">Для целей данного пошагового руководства будут использованы два метода, которые были сопоставлены с хранимыми процедурами в образце базы данных Northwind: CustOrdersDetail и CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="b95a2-108">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="b95a2-109">Сопоставление осуществляется при запуске программы командной строки SQLMetal для создания файла C#.</span><span class="sxs-lookup"><span data-stu-id="b95a2-109">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="b95a2-110">Дополнительные сведения см. в разделе "Предварительные требования" далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b95a2-110">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="b95a2-111">Это пошаговое руководство не полагается на реляционный конструктор объектов.</span><span class="sxs-lookup"><span data-stu-id="b95a2-111">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="b95a2-112">Разработчики, использующие Visual Studio, также могут использовать конструктор O/R для реализации функциональных возможностей хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="b95a2-112">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="b95a2-113">См. раздел [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="b95a2-113">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="b95a2-114">Это пошаговое руководство было написано с использованием параметров разработки Visual C#.</span><span class="sxs-lookup"><span data-stu-id="b95a2-114">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b95a2-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b95a2-115">Prerequisites</span></span>

<span data-ttu-id="b95a2-116">Необходимо выполнить следующие требования.</span><span class="sxs-lookup"><span data-stu-id="b95a2-116">This walkthrough requires the following:</span></span>

- <span data-ttu-id="b95a2-117">Для хранения файлов используется выделенная папка ("c:\linqtest7").</span><span class="sxs-lookup"><span data-stu-id="b95a2-117">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="b95a2-118">Прежде чем приступить к выполнению задач, создайте такую папку.</span><span class="sxs-lookup"><span data-stu-id="b95a2-118">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="b95a2-119">Наличие учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="b95a2-119">The Northwind sample database.</span></span>

     <span data-ttu-id="b95a2-120">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="b95a2-120">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b95a2-121">Инструкции см. в разделе [Загрузка образцов баз данных](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b95a2-121">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="b95a2-122">После загрузки базы данных скопируйте файл northwnd.mdf в папку c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="b95a2-122">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="b95a2-123">Наличие файла кода C#, созданного из базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="b95a2-123">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="b95a2-124">Данное пошаговое руководство было написано с использованием средства SqlMetal со следующей командной строкой:</span><span class="sxs-lookup"><span data-stu-id="b95a2-124">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="b95a2-125">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="b95a2-125">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="b95a2-126">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b95a2-126">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="b95a2-127">Обзор</span><span class="sxs-lookup"><span data-stu-id="b95a2-127">Overview</span></span>

<span data-ttu-id="b95a2-128">Данное пошаговое руководство состоит из шести основных задач.</span><span class="sxs-lookup"><span data-stu-id="b95a2-128">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="b95a2-129">Настройка [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b95a2-129">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="b95a2-130">Добавление сборки System.Data.Linq в проект.</span><span class="sxs-lookup"><span data-stu-id="b95a2-130">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="b95a2-131">Добавление файла кода базы данных в проект.</span><span class="sxs-lookup"><span data-stu-id="b95a2-131">Adding the database code file to the project.</span></span>

- <span data-ttu-id="b95a2-132">Создание подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="b95a2-132">Creating a connection with the database.</span></span>

- <span data-ttu-id="b95a2-133">Настройка пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b95a2-133">Setting up the user interface.</span></span>

- <span data-ttu-id="b95a2-134">Запуск и тестирование приложения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-134">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b95a2-135">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b95a2-135">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="b95a2-136">В этой первой задаче вы создадите решение Visual Studio, содержащее необходимые ссылки для сборки и запуска [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта.</span><span class="sxs-lookup"><span data-stu-id="b95a2-136">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b95a2-137">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b95a2-137">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="b95a2-138">В меню **файл** Visual Studio наведите указатель на пункт **создать** и выберите пункт **проект**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-138">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="b95a2-139">В области **типы проектов** диалогового окна **Новый проект** щелкните **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-139">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="b95a2-140">Выберите **Приложение Windows Forms** в области **Шаблоны**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-140">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="b95a2-141">В поле **имя** введите **спроконляпп**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-141">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="b95a2-142">В поле **Расположение** проверьте, где вы хотите сохранить файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="b95a2-142">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="b95a2-143">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-143">Click **OK**.</span></span>

     <span data-ttu-id="b95a2-144">Откроется конструктор Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b95a2-144">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="b95a2-145">Добавление ссылки на сборку LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b95a2-145">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="b95a2-146">Сборка [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не включается в стандартный шаблон приложения Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b95a2-146">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="b95a2-147">Сборку необходимо добавить самостоятельно, выполнив приведенные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b95a2-147">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="b95a2-148">Добавление сборки System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="b95a2-148">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="b95a2-149">В **Обозреватель решений** щелкните правой кнопкой мыши элемент **ссылки** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-149">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="b95a2-150">В диалоговом окне **Добавление ссылки** щелкните **.NET**, выберите сборку System. Data. LINQ и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-150">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="b95a2-151">Сборка будет добавлена в проект.</span><span class="sxs-lookup"><span data-stu-id="b95a2-151">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b95a2-152">Добавление файла кода Northwind в проект</span><span class="sxs-lookup"><span data-stu-id="b95a2-152">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="b95a2-153">При выполнении действий этого шага предполагается, что для создания файла кода из учебной базы данных Northwind использовалась программа SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="b95a2-153">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b95a2-154">Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b95a2-154">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b95a2-155">Добавление файла кода northwind в проект</span><span class="sxs-lookup"><span data-stu-id="b95a2-155">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="b95a2-156">В меню **Проект** выберите пункт **Добавить существующий элемент**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-156">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="b95a2-157">В диалоговом окне **Добавление существующего элемента** перейдите в c:\linqtest7\northwind.cs и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-157">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="b95a2-158">Файл northwind.cs будет добавлен в проект.</span><span class="sxs-lookup"><span data-stu-id="b95a2-158">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="b95a2-159">Создание подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="b95a2-159">Creating a Database Connection</span></span>

<span data-ttu-id="b95a2-160">На этом этапе определяется подключение к учебной базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="b95a2-160">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="b95a2-161">В качестве пути используется "c:\linqtest7\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="b95a2-161">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="b95a2-162">Создание подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="b95a2-162">To create the database connection</span></span>

1. <span data-ttu-id="b95a2-163">В **Обозреватель решений** щелкните правой кнопкой мыши **Form1.CS** и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-163">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="b95a2-164">Введите следующий код в класс `Form1`:</span><span class="sxs-lookup"><span data-stu-id="b95a2-164">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="b95a2-165">Настройка пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="b95a2-165">Setting up the User Interface</span></span>

<span data-ttu-id="b95a2-166">В этой задаче настраивается интерфейс, с помощью которого пользователи могут выполнять хранимые процедуры для получения доступа к данным в базе данных.</span><span class="sxs-lookup"><span data-stu-id="b95a2-166">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="b95a2-167">В приложении, разрабатываемом с помощью настоящего пошагового руководства, пользователи могут получать доступ к данным в базе данных только с помощью хранимых процедур, внедренных в приложение.</span><span class="sxs-lookup"><span data-stu-id="b95a2-167">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="b95a2-168">Настройка пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="b95a2-168">To set up the user interface</span></span>

1. <span data-ttu-id="b95a2-169">Вернитесь к конструктор Windows Forms (**Form1. cs [Design]**).</span><span class="sxs-lookup"><span data-stu-id="b95a2-169">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="b95a2-170">В меню **Вид** выберите пункт **Область элементов**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-170">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="b95a2-171">Откроется панель элементов.</span><span class="sxs-lookup"><span data-stu-id="b95a2-171">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b95a2-172">Щелкните кнопку **Автоскрытие** , чтобы открыть панель элементов во время выполнения оставшихся действий в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="b95a2-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="b95a2-173">Перетащите две кнопки, два текстовых поля и две метки с панели элементов на **форму Form1**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="b95a2-174">Расположите элементы управления в соответствии с показанным здесь рисунком.</span><span class="sxs-lookup"><span data-stu-id="b95a2-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="b95a2-175">Разверните **форму Form1** , чтобы элементы управления были легко размещены.</span><span class="sxs-lookup"><span data-stu-id="b95a2-175">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="b95a2-176">Щелкните правой кнопкой мыши элемент **Label1** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-176">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="b95a2-177">Измените свойство **Text** с помощью **Label1** , чтобы **ввести OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-177">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="b95a2-178">Таким же образом для **ярлык2** измените свойство **Text** с **ярлык2** на **Ввод CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-178">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="b95a2-179">Аналогичным образом измените свойство **Text** для **Button1** на **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-179">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="b95a2-180">Измените свойство **Text** для свойства **Button2** на " **журнал заказов**".</span><span class="sxs-lookup"><span data-stu-id="b95a2-180">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="b95a2-181">Расширьте элементы управления "Кнопка", чтобы отображался весь текст.</span><span class="sxs-lookup"><span data-stu-id="b95a2-181">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="b95a2-182">Обработка нажатий кнопки</span><span class="sxs-lookup"><span data-stu-id="b95a2-182">To handle button clicks</span></span>

1. <span data-ttu-id="b95a2-183">Дважды щелкните элемент **сведения о заказе** в **Form1** , чтобы открыть обработчик событий button1 в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="b95a2-183">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="b95a2-184">Введите в обработчик кнопки `button1` следующий код:</span><span class="sxs-lookup"><span data-stu-id="b95a2-184">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="b95a2-185">Теперь дважды щелкните элемент " **Button2** " на **Form1** , чтобы открыть `button2` обработчик.</span><span class="sxs-lookup"><span data-stu-id="b95a2-185">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="b95a2-186">Введите в обработчик кнопки `button2` следующий код:</span><span class="sxs-lookup"><span data-stu-id="b95a2-186">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="b95a2-187">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="b95a2-187">Testing the Application</span></span>

<span data-ttu-id="b95a2-188">Теперь необходимо протестировать приложение.</span><span class="sxs-lookup"><span data-stu-id="b95a2-188">Now it is time to test your application.</span></span> <span data-ttu-id="b95a2-189">Обратите внимание, что все обращения к хранилищу данных ограничены теми действиями, которые могут выполняться двумя хранимыми процедурами.</span><span class="sxs-lookup"><span data-stu-id="b95a2-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="b95a2-190">Эти действия заключаются в возвращении продуктов, включенных в заказ с введенным кодом, или истории продуктов, заказанных клиентом с введенным кодом.</span><span class="sxs-lookup"><span data-stu-id="b95a2-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="b95a2-191">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="b95a2-191">To test the application</span></span>

1. <span data-ttu-id="b95a2-192">Нажмите клавишу F5, чтобы начать отладку.</span><span class="sxs-lookup"><span data-stu-id="b95a2-192">Press F5 to start debugging.</span></span>

     <span data-ttu-id="b95a2-193">Откроется форма "Form1".</span><span class="sxs-lookup"><span data-stu-id="b95a2-193">Form1 appears.</span></span>

2. <span data-ttu-id="b95a2-194">В поле **Enter OrderID (введите** код заказа) введите `10249` , а затем щелкните **Order Details (подробности заказа**).</span><span class="sxs-lookup"><span data-stu-id="b95a2-194">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="b95a2-195">В окне сообщения будет отображен список продуктов, включенных в заказ 10249.</span><span class="sxs-lookup"><span data-stu-id="b95a2-195">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="b95a2-196">Нажмите кнопку **OК** , чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-196">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="b95a2-197">В поле **введите CustomerID** введите `ALFKI` , а затем щелкните **Журнал заказа**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="b95a2-198">Откроется окно сообщения, в котором отображается история заказа для клиента ALFKI.</span><span class="sxs-lookup"><span data-stu-id="b95a2-198">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="b95a2-199">Нажмите кнопку **OК** , чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-199">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="b95a2-200">В поле **Enter OrderID (введите** код заказа) введите `123` , а затем щелкните **Order Details (подробности заказа**).</span><span class="sxs-lookup"><span data-stu-id="b95a2-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="b95a2-201">Откроется окно сообщения, в котором отображается текст "Нет результатов".</span><span class="sxs-lookup"><span data-stu-id="b95a2-201">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="b95a2-202">Нажмите кнопку **OК** , чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-202">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="b95a2-203">В меню **Отладка** выберите команду **прерывать отладку**.</span><span class="sxs-lookup"><span data-stu-id="b95a2-203">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="b95a2-204">Сеанс отладки закрывается.</span><span class="sxs-lookup"><span data-stu-id="b95a2-204">The debug session closes.</span></span>

6. <span data-ttu-id="b95a2-205">Если вы завершили эксперименты, можно нажать кнопку **Закрыть проект** в меню **файл** и сохранить проект при появлении соответствующего запроса.</span><span class="sxs-lookup"><span data-stu-id="b95a2-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b95a2-206">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="b95a2-206">Next Steps</span></span>

<span data-ttu-id="b95a2-207">Этот проект можно улучшить, выполнив некоторые изменения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="b95a2-208">Например, можно создать поле со списком доступных хранимых процедур и разрешить пользователю выбирать процедуру для выполнения.</span><span class="sxs-lookup"><span data-stu-id="b95a2-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="b95a2-209">Можно также записывать выходные данных отчетов в текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="b95a2-209">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="b95a2-210">См. также</span><span class="sxs-lookup"><span data-stu-id="b95a2-210">See also</span></span>

- [<span data-ttu-id="b95a2-211">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="b95a2-211">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="b95a2-212">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="b95a2-212">Stored Procedures</span></span>](stored-procedures.md)
