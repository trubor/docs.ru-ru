---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Управление данными (C#)
title: Пошаговое руководство. Обработка данных (C#)
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 6176709a2e02d8c06ec54b70cc6e0e4c302509c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729592"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="e0895-103">Пошаговое руководство. Обработка данных (C#)</span><span class="sxs-lookup"><span data-stu-id="e0895-103">Walkthrough: Manipulating Data (C#)</span></span>

<span data-ttu-id="e0895-104">В данном руководстве представлен основной и полный сценарий [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] по добавлению, изменению и удалению данных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="e0895-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="e0895-105">Для добавления клиента, изменения его имени и удаления заказа следует использовать копию учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="e0895-105">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e0895-106">Это пошаговое руководство было написано с использованием параметров разработки Visual C#.</span><span class="sxs-lookup"><span data-stu-id="e0895-106">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e0895-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="e0895-107">Prerequisites</span></span>  

 <span data-ttu-id="e0895-108">Необходимо выполнить следующие требования.</span><span class="sxs-lookup"><span data-stu-id="e0895-108">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="e0895-109">Для хранения файлов используется выделенная папка ("c:\linqtest6").</span><span class="sxs-lookup"><span data-stu-id="e0895-109">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="e0895-110">Прежде чем приступить к выполнению задач, создайте такую папку.</span><span class="sxs-lookup"><span data-stu-id="e0895-110">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="e0895-111">Наличие учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="e0895-111">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e0895-112">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e0895-112">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e0895-113">Инструкции см. в разделе [Загрузка образцов баз данных](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e0895-113">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="e0895-114">После загрузки базы данных скопируйте файл northwnd.mdf в папку c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="e0895-114">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="e0895-115">Наличие файла кода C#, созданного из базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="e0895-115">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e0895-116">Этот файл можно создать с помощью реляционный конструктор объектов или средства SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e0895-116">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="e0895-117">Данное пошаговое руководство было написано с использованием средства SQLMetal со следующей командной строкой:</span><span class="sxs-lookup"><span data-stu-id="e0895-117">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e0895-118">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="e0895-118">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="e0895-119">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e0895-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e0895-120">Обзор</span><span class="sxs-lookup"><span data-stu-id="e0895-120">Overview</span></span>  

 <span data-ttu-id="e0895-121">Данное пошаговое руководство состоит из шести основных задач.</span><span class="sxs-lookup"><span data-stu-id="e0895-121">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="e0895-122">Создание [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0895-122">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="e0895-123">Добавление файла кода базы данных в проект.</span><span class="sxs-lookup"><span data-stu-id="e0895-123">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="e0895-124">Создание нового объекта клиента.</span><span class="sxs-lookup"><span data-stu-id="e0895-124">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="e0895-125">Изменение контактного имени клиента.</span><span class="sxs-lookup"><span data-stu-id="e0895-125">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="e0895-126">Удаление заказа.</span><span class="sxs-lookup"><span data-stu-id="e0895-126">Deleting an order.</span></span>  
  
- <span data-ttu-id="e0895-127">Отправка внесенных изменений в базу данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="e0895-127">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e0895-128">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e0895-128">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="e0895-129">В этой первой задаче вы создадите решение Visual Studio, содержащее необходимые ссылки для сборки и запуска [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта.</span><span class="sxs-lookup"><span data-stu-id="e0895-129">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e0895-130">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e0895-130">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="e0895-131">В меню **файл** Visual Studio наведите указатель на пункт **создать** и выберите пункт **проект**.</span><span class="sxs-lookup"><span data-stu-id="e0895-131">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="e0895-132">В области **типы проектов** диалогового окна **Новый проект** щелкните **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="e0895-132">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="e0895-133">В области **Шаблоны** щелкните **Консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="e0895-133">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="e0895-134">В поле **имя** введите **линкдатаманипулатионапп**.</span><span class="sxs-lookup"><span data-stu-id="e0895-134">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="e0895-135">В поле **Расположение** проверьте, где вы хотите сохранить файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="e0895-135">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="e0895-136">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="e0895-136">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="e0895-137">Добавление ссылок и директив LINQ</span><span class="sxs-lookup"><span data-stu-id="e0895-137">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="e0895-138">В этом пошаговом руководстве используются сборки, которые могут быть не установлены по умолчанию в проект.</span><span class="sxs-lookup"><span data-stu-id="e0895-138">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="e0895-139">Если System.Data.Linq не входит в список ссылок проекта, добавьте ее, как описано в следующих действиях.</span><span class="sxs-lookup"><span data-stu-id="e0895-139">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="e0895-140">Добавление сборки System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="e0895-140">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="e0895-141">В **Обозреватель решений** щелкните правой кнопкой мыши элемент **ссылки** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="e0895-141">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="e0895-142">В диалоговом окне **Добавление ссылки** щелкните **.NET**, выберите сборку System. Data. LINQ и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="e0895-142">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e0895-143">Сборка будет добавлена в проект.</span><span class="sxs-lookup"><span data-stu-id="e0895-143">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="e0895-144">Добавьте следующие директивы в начало Program.cs.</span><span class="sxs-lookup"><span data-stu-id="e0895-144">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e0895-145">Добавление файла кода Northwind в проект</span><span class="sxs-lookup"><span data-stu-id="e0895-145">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="e0895-146">При выполнении этих действий подразумевается, что для создания файла кода из учебной базы данных Northwind использовалось средство SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e0895-146">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e0895-147">Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="e0895-147">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e0895-148">Добавление файла кода northwind в проект</span><span class="sxs-lookup"><span data-stu-id="e0895-148">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="e0895-149">В меню **Проект** выберите пункт **Добавить существующий элемент**.</span><span class="sxs-lookup"><span data-stu-id="e0895-149">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="e0895-150">В диалоговом окне **Добавление существующего элемента** перейдите к c:\linqtest6\northwind.cs и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="e0895-150">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e0895-151">Файл northwind.cs будет добавлен в проект.</span><span class="sxs-lookup"><span data-stu-id="e0895-151">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="e0895-152">Настройка подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="e0895-152">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="e0895-153">Сначала проверьте подключение к базе данных.</span><span class="sxs-lookup"><span data-stu-id="e0895-153">First, test your connection to the database.</span></span> <span data-ttu-id="e0895-154">Обратите особое внимание, что в имени базы данных - Northwnd - отсутствует буква "i".</span><span class="sxs-lookup"><span data-stu-id="e0895-154">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="e0895-155">Если при выполнении следующих действий возникают ошибки, просмотрите файл northwind.cs, чтобы определить написание разделяемого класса Northwind.</span><span class="sxs-lookup"><span data-stu-id="e0895-155">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="e0895-156">Настройка и проверка подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="e0895-156">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="e0895-157">Введите или вставьте следующий код в метод `Main` в классе Program.</span><span class="sxs-lookup"><span data-stu-id="e0895-157">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="e0895-158">Чтобы проверить приложение на этом этапе, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="e0895-158">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="e0895-159">Откроется окно **консоли** .</span><span class="sxs-lookup"><span data-stu-id="e0895-159">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="e0895-160">Приложение можно закрыть, нажав клавишу ВВОД в окне **консоли** или выбрав пункт **прерывать отладку** в меню **Отладка** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0895-160">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="e0895-161">Создание новой сущности</span><span class="sxs-lookup"><span data-stu-id="e0895-161">Creating a New Entity</span></span>  

 <span data-ttu-id="e0895-162">Создание новой сущности не представляет особых проблем.</span><span class="sxs-lookup"><span data-stu-id="e0895-162">Creating a new entity is straightforward.</span></span> <span data-ttu-id="e0895-163">Для создания объектов (например, `Customer`) можно использовать ключевое слово `new`.</span><span class="sxs-lookup"><span data-stu-id="e0895-163">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="e0895-164">В этом и следующих разделах выполняются изменения только локального кэша.</span><span class="sxs-lookup"><span data-stu-id="e0895-164">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="e0895-165">Изменения не будут отправлены в базу данных до тех пор, пока ближе к концу данного руководства не будет вызван <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0895-165">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="e0895-166">Добавление нового объекта сущностей Customer</span><span class="sxs-lookup"><span data-stu-id="e0895-166">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="e0895-167">Создайте новый `Customer`, добавив перед `Console.ReadLine();`в методе `Main` следующий код.</span><span class="sxs-lookup"><span data-stu-id="e0895-167">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="e0895-168">Нажмите клавишу F5 для отладки решения.</span><span class="sxs-lookup"><span data-stu-id="e0895-168">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="e0895-169">Нажмите клавишу ВВОД в окне **консоли** , чтобы прекратить отладку и продолжить выполнение пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="e0895-169">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="e0895-170">Обновление объекта</span><span class="sxs-lookup"><span data-stu-id="e0895-170">Updating an Entity</span></span>  

 <span data-ttu-id="e0895-171">При выполнении следующих действий будет извлечен объект `Customer` и изменено одно из его свойств.</span><span class="sxs-lookup"><span data-stu-id="e0895-171">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="e0895-172">Изменение имени клиента</span><span class="sxs-lookup"><span data-stu-id="e0895-172">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="e0895-173">Добавьте следующий код перед `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="e0895-173">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="e0895-174">Удаление объекта</span><span class="sxs-lookup"><span data-stu-id="e0895-174">Deleting an Entity</span></span>  

 <span data-ttu-id="e0895-175">Используя тот же самый объект клиента, можно удалить первый заказ.</span><span class="sxs-lookup"><span data-stu-id="e0895-175">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="e0895-176">В следующем коде показано, как разорвать связь между строками и удалить строку из базы данных.</span><span class="sxs-lookup"><span data-stu-id="e0895-176">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="e0895-177">Чтобы удаление объектов, добавьте следующий код перед `Console.ReadLine`.</span><span class="sxs-lookup"><span data-stu-id="e0895-177">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="e0895-178">Удаление строки</span><span class="sxs-lookup"><span data-stu-id="e0895-178">To delete a row</span></span>  
  
- <span data-ttu-id="e0895-179">Добавьте следующий код перед `Console.ReadLine();`.</span><span class="sxs-lookup"><span data-stu-id="e0895-179">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="e0895-180">Отправка изменений в базу данных</span><span class="sxs-lookup"><span data-stu-id="e0895-180">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="e0895-181">Последнее действие, необходимое для создания, обновления и удаления объектов, заключается в фактической отправке изменений в базу данных.</span><span class="sxs-lookup"><span data-stu-id="e0895-181">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="e0895-182">Без него изменения останутся на локальном уровне и не появятся в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="e0895-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="e0895-183">Отправка изменений в базу данных</span><span class="sxs-lookup"><span data-stu-id="e0895-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="e0895-184">Вставьте следующий код перед `Console.ReadLine`.</span><span class="sxs-lookup"><span data-stu-id="e0895-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="e0895-185">Вставьте следующий код (после `SubmitChanges`), чтобы показать результаты до и после отправки изменений.</span><span class="sxs-lookup"><span data-stu-id="e0895-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="e0895-186">Нажмите клавишу F5 для отладки решения.</span><span class="sxs-lookup"><span data-stu-id="e0895-186">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="e0895-187">Нажмите клавишу ВВОД в окне **консоли** , чтобы закрыть приложение.</span><span class="sxs-lookup"><span data-stu-id="e0895-187">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0895-188">После добавления нового клиента путем отправки изменений это решение нельзя повторно выполнить в исходном виде.</span><span class="sxs-lookup"><span data-stu-id="e0895-188">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="e0895-189">Для повторного выполнения решения измените имя клиента и значение идентификатора добавляемого клиента.</span><span class="sxs-lookup"><span data-stu-id="e0895-189">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0895-190">См. также</span><span class="sxs-lookup"><span data-stu-id="e0895-190">See also</span></span>

- [<span data-ttu-id="e0895-191">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="e0895-191">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
