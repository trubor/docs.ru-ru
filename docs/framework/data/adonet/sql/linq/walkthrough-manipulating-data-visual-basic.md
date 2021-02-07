---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Управление данными (Visual Basic)
title: Пошаговое руководство. Обработка данных (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 22bef61c294a92984446402063bf14b06f5b2b2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729527"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="a8070-103">Пошаговое руководство. Обработка данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8070-103">Walkthrough: Manipulating Data (Visual Basic)</span></span>

<span data-ttu-id="a8070-104">В данном руководстве представлен основной и полный сценарий [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] по добавлению, изменению и удалению данных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="a8070-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="a8070-105">Для добавления клиента, изменения его имени и удаления заказа следует использовать копию учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8070-105">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a8070-106">Это пошаговое руководство было написано с помощью параметров разработки Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8070-106">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8070-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="a8070-107">Prerequisites</span></span>  

 <span data-ttu-id="a8070-108">Необходимо выполнить следующие требования.</span><span class="sxs-lookup"><span data-stu-id="a8070-108">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="a8070-109">Для хранения файлов используется выделенная папка ("c:\linqtest2").</span><span class="sxs-lookup"><span data-stu-id="a8070-109">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="a8070-110">Прежде чем приступить к выполнению задач, создайте такую папку.</span><span class="sxs-lookup"><span data-stu-id="a8070-110">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="a8070-111">Наличие учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8070-111">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="a8070-112">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a8070-112">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="a8070-113">Инструкции см. в разделе [Загрузка образцов баз данных](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a8070-113">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="a8070-114">После загрузки базы данных скопируйте файл northwnd.mdf в папку c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="a8070-114">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="a8070-115">Наличие файла кода Visual Basic, созданного из базы данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="a8070-115">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="a8070-116">Этот файл можно создать с помощью реляционный конструктор объектов или средства SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a8070-116">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="a8070-117">Данное пошаговое руководство было написано с использованием средства SQLMetal со следующей командной строкой:</span><span class="sxs-lookup"><span data-stu-id="a8070-117">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="a8070-118">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="a8070-118">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="a8070-119">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a8070-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a8070-120">Обзор</span><span class="sxs-lookup"><span data-stu-id="a8070-120">Overview</span></span>  

 <span data-ttu-id="a8070-121">Данное пошаговое руководство состоит из шести основных задач.</span><span class="sxs-lookup"><span data-stu-id="a8070-121">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="a8070-122">Создание [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8070-122">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="a8070-123">Добавление файла кода базы данных в проект.</span><span class="sxs-lookup"><span data-stu-id="a8070-123">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="a8070-124">Создание нового объекта клиента.</span><span class="sxs-lookup"><span data-stu-id="a8070-124">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="a8070-125">Изменение контактного имени клиента.</span><span class="sxs-lookup"><span data-stu-id="a8070-125">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="a8070-126">Удаление заказа.</span><span class="sxs-lookup"><span data-stu-id="a8070-126">Deleting an order.</span></span>  
  
- <span data-ttu-id="a8070-127">Отправка внесенных изменений в базу данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8070-127">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="a8070-128">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a8070-128">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="a8070-129">В этой первой задаче вы создадите решение Visual Studio, содержащее необходимые ссылки для сборки и запуска [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта.</span><span class="sxs-lookup"><span data-stu-id="a8070-129">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="a8070-130">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a8070-130">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="a8070-131">В меню **Файл** Visual Studio выберите команду **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="a8070-131">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="a8070-132">В области **типы проектов** диалогового окна **Новый проект** нажмите кнопку **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="a8070-132">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="a8070-133">В области **Шаблоны** щелкните **Консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="a8070-133">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="a8070-134">В поле **имя** введите **линкдатаманипулатионапп**.</span><span class="sxs-lookup"><span data-stu-id="a8070-134">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="a8070-135">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8070-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="a8070-136">Добавление ссылок и директив LINQ</span><span class="sxs-lookup"><span data-stu-id="a8070-136">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="a8070-137">В этом пошаговом руководстве используются сборки, которые могут быть не установлены по умолчанию в проект.</span><span class="sxs-lookup"><span data-stu-id="a8070-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="a8070-138">Если `System.Data.Linq` в проекте нет списка (щелкните **Показывать все файлы** в **Обозреватель решений** и разверните узел **ссылки** ), добавьте его, как описано в следующих шагах.</span><span class="sxs-lookup"><span data-stu-id="a8070-138">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="a8070-139">Добавление сборки System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="a8070-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="a8070-140">В **Обозреватель решений** щелкните правой кнопкой мыши элемент **ссылки** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="a8070-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="a8070-141">В диалоговом окне **Добавление ссылки** щелкните **.NET**, выберите сборку System. Data. LINQ и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a8070-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a8070-142">Сборка будет добавлена в проект.</span><span class="sxs-lookup"><span data-stu-id="a8070-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="a8070-143">В редакторе кода добавьте следующие директивы над **Module1**:</span><span class="sxs-lookup"><span data-stu-id="a8070-143">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a8070-144">Добавление файла кода Northwind в проект</span><span class="sxs-lookup"><span data-stu-id="a8070-144">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="a8070-145">При выполнении этих действий подразумевается, что для создания файла кода из учебной базы данных Northwind использовалось средство SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a8070-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="a8070-146">Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="a8070-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a8070-147">Добавление файла кода northwind в проект</span><span class="sxs-lookup"><span data-stu-id="a8070-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="a8070-148">В меню **Проект** выберите пункт **Добавить существующий элемент**.</span><span class="sxs-lookup"><span data-stu-id="a8070-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="a8070-149">В диалоговом окне **Добавление существующего элемента** перейдите к c:\linqtest2\northwind.vb и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="a8070-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a8070-150">Файл northwind.vb будет добавлен в проект.</span><span class="sxs-lookup"><span data-stu-id="a8070-150">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="a8070-151">Настройка подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="a8070-151">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="a8070-152">Сначала проверьте подключение к базе данных.</span><span class="sxs-lookup"><span data-stu-id="a8070-152">First, test your connection to the database.</span></span> <span data-ttu-id="a8070-153">Обратите особое внимание, что в имени базы данных - Northwnd - отсутствует буква "i".</span><span class="sxs-lookup"><span data-stu-id="a8070-153">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="a8070-154">Если при выполнении следующих действий возникают ошибки, просмотрите файл northwind.vb, чтобы определить написание разделяемого класса Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8070-154">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="a8070-155">Настройка и проверка подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="a8070-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="a8070-156">Введите или вставьте следующий код в `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="a8070-156">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="a8070-157">Чтобы проверить приложение на этом этапе, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="a8070-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="a8070-158">Откроется окно **консоли** .</span><span class="sxs-lookup"><span data-stu-id="a8070-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="a8070-159">Закройте приложение, нажав клавишу ВВОД в окне **консоли** или выбрав пункт **прерывать отладку** в меню **Отладка** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8070-159">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="a8070-160">Создание новой сущности</span><span class="sxs-lookup"><span data-stu-id="a8070-160">Creating a New Entity</span></span>  

 <span data-ttu-id="a8070-161">Создание новой сущности не представляет особых проблем.</span><span class="sxs-lookup"><span data-stu-id="a8070-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="a8070-162">Для создания объектов (например, `Customer`) можно использовать ключевое слово `New`.</span><span class="sxs-lookup"><span data-stu-id="a8070-162">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="a8070-163">В этом и следующих разделах выполняются изменения только локального кэша.</span><span class="sxs-lookup"><span data-stu-id="a8070-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="a8070-164">Изменения не будут отправлены в базу данных до тех пор, пока ближе к концу данного руководства не будет вызван <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8070-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="a8070-165">Добавление нового объекта сущностей Customer</span><span class="sxs-lookup"><span data-stu-id="a8070-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="a8070-166">Создайте новый `Customer`, добавив перед `Console.ReadLine` в `Sub Main` следующий код.</span><span class="sxs-lookup"><span data-stu-id="a8070-166">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="a8070-167">Нажмите клавишу F5 для отладки решения.</span><span class="sxs-lookup"><span data-stu-id="a8070-167">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="a8070-168">В окне консоли отображаются следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="a8070-168">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="a8070-169">Обратите внимание, что в выходных данных новая строка не отображается.</span><span class="sxs-lookup"><span data-stu-id="a8070-169">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="a8070-170">Новые данные еще не были переданы в базу данных.</span><span class="sxs-lookup"><span data-stu-id="a8070-170">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="a8070-171">Нажмите клавишу ВВОД в окне **консоли** , чтобы отключить отладку.</span><span class="sxs-lookup"><span data-stu-id="a8070-171">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="a8070-172">Обновление объекта</span><span class="sxs-lookup"><span data-stu-id="a8070-172">Updating an Entity</span></span>  

 <span data-ttu-id="a8070-173">При выполнении следующих действий будет извлечен объект `Customer` и изменено одно из его свойств.</span><span class="sxs-lookup"><span data-stu-id="a8070-173">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="a8070-174">Изменение имени клиента</span><span class="sxs-lookup"><span data-stu-id="a8070-174">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="a8070-175">Добавьте следующий код перед `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="a8070-175">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="a8070-176">Удаление объекта</span><span class="sxs-lookup"><span data-stu-id="a8070-176">Deleting an Entity</span></span>  

 <span data-ttu-id="a8070-177">Используя тот же самый объект клиента, можно удалить первый заказ.</span><span class="sxs-lookup"><span data-stu-id="a8070-177">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="a8070-178">В следующем коде показано, как разорвать связь между строками и удалить строку из базы данных.</span><span class="sxs-lookup"><span data-stu-id="a8070-178">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="a8070-179">Удаление строки</span><span class="sxs-lookup"><span data-stu-id="a8070-179">To delete a row</span></span>  
  
- <span data-ttu-id="a8070-180">Добавьте следующий код перед `Console.ReadLine()`.</span><span class="sxs-lookup"><span data-stu-id="a8070-180">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="a8070-181">Отправка изменений в базу данных</span><span class="sxs-lookup"><span data-stu-id="a8070-181">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="a8070-182">Последнее действие, необходимое для создания, обновления и удаления объектов, заключается в фактической отправке изменений в базу данных.</span><span class="sxs-lookup"><span data-stu-id="a8070-182">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="a8070-183">Без него изменения останутся на локальном уровне и не появятся в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="a8070-183">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="a8070-184">Отправка изменений в базу данных</span><span class="sxs-lookup"><span data-stu-id="a8070-184">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="a8070-185">Вставьте следующий код перед `Console.ReadLine`.</span><span class="sxs-lookup"><span data-stu-id="a8070-185">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="a8070-186">Вставьте следующий код (после `SubmitChanges`), чтобы показать результаты до и после отправки изменений.</span><span class="sxs-lookup"><span data-stu-id="a8070-186">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="a8070-187">Нажмите клавишу F5 для отладки решения.</span><span class="sxs-lookup"><span data-stu-id="a8070-187">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="a8070-188">Появится окно консоли со следующими данными.</span><span class="sxs-lookup"><span data-stu-id="a8070-188">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="a8070-189">Нажмите клавишу ВВОД в окне **консоли** , чтобы отключить отладку.</span><span class="sxs-lookup"><span data-stu-id="a8070-189">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8070-190">После добавления нового клиента путем отправки изменений это решение нельзя повторно выполнить в исходном виде, поскольку этот же клиент не может быть добавлен без изменений.</span><span class="sxs-lookup"><span data-stu-id="a8070-190">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="a8070-191">Для повторного выполнения решения измените значение идентификатора добавляемого клиента.</span><span class="sxs-lookup"><span data-stu-id="a8070-191">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8070-192">См. также</span><span class="sxs-lookup"><span data-stu-id="a8070-192">See also</span></span>

- [<span data-ttu-id="a8070-193">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="a8070-193">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
