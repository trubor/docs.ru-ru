---
title: Создание и запуск долго выполняющегося рабочего процесса
description: В этой статье показано, как создать ведущее приложение Windows Forms, которое поддерживает запуск и возобновление нескольких экземпляров рабочего процесса и сохраняемости рабочих процессов.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 701788ac5575ad671afd56db3af4bd247efac8b1
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188469"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="884ea-103">Создание и запуск долго выполняющегося рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-103">How to create and run a long-running workflow</span></span>

<span data-ttu-id="884ea-104">Одной из основных функций Windows Workflow Foundation (WF) является способность среды выполнения сохранять и выгружать неактивные рабочие процессы в базу данных.</span><span class="sxs-lookup"><span data-stu-id="884ea-104">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="884ea-105">Инструкции по [выполнению рабочего процесса](how-to-run-a-workflow.md) демонстрируют основы размещения рабочих процессов с помощью консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="884ea-105">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="884ea-106">Приведены примеры запуска рабочих процессов, обработчиков жизненного цикла рабочего процесса и возобновления закладок.</span><span class="sxs-lookup"><span data-stu-id="884ea-106">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="884ea-107">Для эффективной демонстрации сохранения рабочего процесса требуется более сложный узел рабочих процессов, обеспечивающий запуск и возобновление нескольких экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-107">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="884ea-108">На этом шаге учебника показано, как создать ведущее приложение форм Windows Form, которое обеспечивает запуск и возобновление нескольких экземпляров рабочих процессов, сохранение рабочего процесса и основу для таких дополнительных возможностей, как отслеживание версий, которые показаны в последующих шагах учебника, и управление ими.</span><span class="sxs-lookup"><span data-stu-id="884ea-108">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="884ea-109">В этом шаге руководства и последующих шагах используются все три типа рабочих процессов из [руководства: создание рабочего процесса](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="884ea-109">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="to-create-the-persistence-database"></a><span data-ttu-id="884ea-110">Создание базы данных сохраняемости</span><span class="sxs-lookup"><span data-stu-id="884ea-110">To create the persistence database</span></span>

1. <span data-ttu-id="884ea-111">Откройте SQL Server Management Studio и подключитесь к локальному серверу, например **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="884ea-111">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="884ea-112">Щелкните правой кнопкой мыши узел **базы данных** на локальном сервере и выберите пункт **создать базу данных**.</span><span class="sxs-lookup"><span data-stu-id="884ea-112">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="884ea-113">Назовите новую базу данных **WF45GettingStartedTutorial**, примите все остальные значения и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="884ea-113">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="884ea-114">Перед созданием базы данных убедитесь, что у вас есть разрешение на **Создание базы данных** на локальном сервере.</span><span class="sxs-lookup"><span data-stu-id="884ea-114">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="884ea-115">Выберите **Открыть**, **файл** в меню **файл** .</span><span class="sxs-lookup"><span data-stu-id="884ea-115">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="884ea-116">Перейдите в следующую папку: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span><span class="sxs-lookup"><span data-stu-id="884ea-116">Browse to the following folder: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span></span>

    <span data-ttu-id="884ea-117">Выберите два следующих файла и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="884ea-117">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="884ea-118">*SqlWorkflowInstanceStoreLogic.sql*</span><span class="sxs-lookup"><span data-stu-id="884ea-118">*SqlWorkflowInstanceStoreLogic.sql*</span></span>

    - <span data-ttu-id="884ea-119">*SqlWorkflowInstanceStoreSchema.sql*</span><span class="sxs-lookup"><span data-stu-id="884ea-119">*SqlWorkflowInstanceStoreSchema.sql*</span></span>

3. <span data-ttu-id="884ea-120">В меню **окно** выберите **склворкфловинстанцесторесчема. SQL** .</span><span class="sxs-lookup"><span data-stu-id="884ea-120">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="884ea-121">Убедитесь, что в раскрывающемся списке **Доступные базы данных** выбрано **WF45GettingStartedTutorial** , и выберите команду **выполнить** в меню **запрос** .</span><span class="sxs-lookup"><span data-stu-id="884ea-121">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="884ea-122">В меню **окно** выберите **склворкфловинстанцесторелогик. SQL** .</span><span class="sxs-lookup"><span data-stu-id="884ea-122">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="884ea-123">Убедитесь, что в раскрывающемся списке **Доступные базы данных** выбрано **WF45GettingStartedTutorial** , и выберите команду **выполнить** в меню **запрос** .</span><span class="sxs-lookup"><span data-stu-id="884ea-123">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="884ea-124">Важно выполнить предыдущие два шага в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="884ea-124">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="884ea-125">Если выполнить запросы в неправильном порядке, произойдет ошибка и база данных сохраняемости не будет правильно настроена.</span><span class="sxs-lookup"><span data-stu-id="884ea-125">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a><span data-ttu-id="884ea-126">Добавление ссылки в сборки DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="884ea-126">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="884ea-127">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="884ea-127">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="884ea-128">Выберите **сборки** из списка **Добавить ссылку** и введите `DurableInstancing` в поле **Поиск сборок** .</span><span class="sxs-lookup"><span data-stu-id="884ea-128">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="884ea-129">Сборки отфильтруются, и будет легче выбрать необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="884ea-129">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="884ea-130">Установите флажок рядом с элементом **System. activitys. DurableInstancing** и **System. Runtime. DurableInstancing** в списке **результатов поиска** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="884ea-130">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

## <a name="to-create-the-workflow-host-form"></a><span data-ttu-id="884ea-131">Создание ведущей формы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-131">To create the workflow host form</span></span>

1. <span data-ttu-id="884ea-132">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите **добавить**, **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="884ea-132">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="884ea-133">В списке **установленные** шаблоны выберите **форма Windows**, введите `WorkflowHostForm` в поле **имя** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="884ea-133">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="884ea-134">Задайте следующие свойства формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-134">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="884ea-135">Свойство.</span><span class="sxs-lookup"><span data-stu-id="884ea-135">Property</span></span>|<span data-ttu-id="884ea-136">Значение</span><span class="sxs-lookup"><span data-stu-id="884ea-136">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="884ea-137">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="884ea-137">FormBorderStyle</span></span>|<span data-ttu-id="884ea-138">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="884ea-138">FixedSingle</span></span>|
    |<span data-ttu-id="884ea-139">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="884ea-139">MaximizeBox</span></span>|<span data-ttu-id="884ea-140">False</span><span class="sxs-lookup"><span data-stu-id="884ea-140">False</span></span>|
    |<span data-ttu-id="884ea-141">Размер</span><span class="sxs-lookup"><span data-stu-id="884ea-141">Size</span></span>|<span data-ttu-id="884ea-142">400, 420</span><span class="sxs-lookup"><span data-stu-id="884ea-142">400, 420</span></span>|

4. <span data-ttu-id="884ea-143">Добавьте в форму следующие элементы управления в указанном порядке и задайте значения свойств.</span><span class="sxs-lookup"><span data-stu-id="884ea-143">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="884ea-144">Control</span><span class="sxs-lookup"><span data-stu-id="884ea-144">Control</span></span>|<span data-ttu-id="884ea-145">Свойство: значение</span><span class="sxs-lookup"><span data-stu-id="884ea-145">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="884ea-146">**Button**</span><span class="sxs-lookup"><span data-stu-id="884ea-146">**Button**</span></span>|<span data-ttu-id="884ea-147">Имя: Невгаме</span><span class="sxs-lookup"><span data-stu-id="884ea-147">Name: NewGame</span></span><br /><br /> <span data-ttu-id="884ea-148">Расположение: 13, 13</span><span class="sxs-lookup"><span data-stu-id="884ea-148">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="884ea-149">Размер: 75, 23</span><span class="sxs-lookup"><span data-stu-id="884ea-149">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="884ea-150">Текст: Новая игра</span><span class="sxs-lookup"><span data-stu-id="884ea-150">Text: New Game</span></span>|
    |<span data-ttu-id="884ea-151">**Label**</span><span class="sxs-lookup"><span data-stu-id="884ea-151">**Label**</span></span>|<span data-ttu-id="884ea-152">Расположение: 94, 18</span><span class="sxs-lookup"><span data-stu-id="884ea-152">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="884ea-153">Текст: догадка числа от 1 до</span><span class="sxs-lookup"><span data-stu-id="884ea-153">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="884ea-154">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-154">**ComboBox**</span></span>|<span data-ttu-id="884ea-155">Имя: Нумберранже</span><span class="sxs-lookup"><span data-stu-id="884ea-155">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="884ea-156">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="884ea-156">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="884ea-157">Элементы: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="884ea-157">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="884ea-158">Расположение: 228, 12</span><span class="sxs-lookup"><span data-stu-id="884ea-158">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="884ea-159">Размер: 143, 21</span><span class="sxs-lookup"><span data-stu-id="884ea-159">Size: 143, 21</span></span>|
    |<span data-ttu-id="884ea-160">**Label**</span><span class="sxs-lookup"><span data-stu-id="884ea-160">**Label**</span></span>|<span data-ttu-id="884ea-161">Расположение: 13, 43</span><span class="sxs-lookup"><span data-stu-id="884ea-161">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="884ea-162">Текст: тип рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-162">Text: Workflow type</span></span>|
    |<span data-ttu-id="884ea-163">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-163">**ComboBox**</span></span>|<span data-ttu-id="884ea-164">Имя: Воркфловтипе</span><span class="sxs-lookup"><span data-stu-id="884ea-164">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="884ea-165">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="884ea-165">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="884ea-166">Элементы: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="884ea-166">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="884ea-167">Расположение: 94, 40</span><span class="sxs-lookup"><span data-stu-id="884ea-167">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="884ea-168">Размер: 277, 21</span><span class="sxs-lookup"><span data-stu-id="884ea-168">Size: 277, 21</span></span>|
    |<span data-ttu-id="884ea-169">**Label**</span><span class="sxs-lookup"><span data-stu-id="884ea-169">**Label**</span></span>|<span data-ttu-id="884ea-170">Имя: Воркфловверсион</span><span class="sxs-lookup"><span data-stu-id="884ea-170">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="884ea-171">Расположение: 13, 362</span><span class="sxs-lookup"><span data-stu-id="884ea-171">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="884ea-172">Текст: версия рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-172">Text: Workflow version</span></span>|
    |<span data-ttu-id="884ea-173">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-173">**GroupBox**</span></span>|<span data-ttu-id="884ea-174">Расположение: 13, 67</span><span class="sxs-lookup"><span data-stu-id="884ea-174">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="884ea-175">Размер: 358, 287</span><span class="sxs-lookup"><span data-stu-id="884ea-175">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="884ea-176">Текст: игра</span><span class="sxs-lookup"><span data-stu-id="884ea-176">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="884ea-177">При добавлении следующих элементов управления помещайте их в GroupBox.</span><span class="sxs-lookup"><span data-stu-id="884ea-177">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="884ea-178">Control</span><span class="sxs-lookup"><span data-stu-id="884ea-178">Control</span></span>|<span data-ttu-id="884ea-179">Свойство: значение</span><span class="sxs-lookup"><span data-stu-id="884ea-179">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="884ea-180">**Label**</span><span class="sxs-lookup"><span data-stu-id="884ea-180">**Label**</span></span>|<span data-ttu-id="884ea-181">Расположение: 7, 20</span><span class="sxs-lookup"><span data-stu-id="884ea-181">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="884ea-182">Текст: идентификатор экземпляра рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-182">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="884ea-183">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-183">**ComboBox**</span></span>|<span data-ttu-id="884ea-184">Имя: InstanceId.</span><span class="sxs-lookup"><span data-stu-id="884ea-184">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="884ea-185">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="884ea-185">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="884ea-186">Расположение: 121, 17</span><span class="sxs-lookup"><span data-stu-id="884ea-186">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="884ea-187">Размер: 227, 21</span><span class="sxs-lookup"><span data-stu-id="884ea-187">Size: 227, 21</span></span>|
    |<span data-ttu-id="884ea-188">**Label**</span><span class="sxs-lookup"><span data-stu-id="884ea-188">**Label**</span></span>|<span data-ttu-id="884ea-189">Расположение: 7, 47</span><span class="sxs-lookup"><span data-stu-id="884ea-189">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="884ea-190">Текст: предположение</span><span class="sxs-lookup"><span data-stu-id="884ea-190">Text: Guess</span></span>|
    |<span data-ttu-id="884ea-191">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-191">**TextBox**</span></span>|<span data-ttu-id="884ea-192">Имя: предположение</span><span class="sxs-lookup"><span data-stu-id="884ea-192">Name: Guess</span></span><br /><br /> <span data-ttu-id="884ea-193">Расположение: 50, 44</span><span class="sxs-lookup"><span data-stu-id="884ea-193">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="884ea-194">Размер: 65, 20</span><span class="sxs-lookup"><span data-stu-id="884ea-194">Size: 65, 20</span></span>|
    |<span data-ttu-id="884ea-195">**Button**</span><span class="sxs-lookup"><span data-stu-id="884ea-195">**Button**</span></span>|<span data-ttu-id="884ea-196">Имя: Ентергуесс</span><span class="sxs-lookup"><span data-stu-id="884ea-196">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="884ea-197">Расположение: 121, 42</span><span class="sxs-lookup"><span data-stu-id="884ea-197">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="884ea-198">Размер: 75, 23</span><span class="sxs-lookup"><span data-stu-id="884ea-198">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="884ea-199">Текст: введите предположение</span><span class="sxs-lookup"><span data-stu-id="884ea-199">Text: Enter Guess</span></span>|
    |<span data-ttu-id="884ea-200">**Button**</span><span class="sxs-lookup"><span data-stu-id="884ea-200">**Button**</span></span>|<span data-ttu-id="884ea-201">Имя: Куитгаме</span><span class="sxs-lookup"><span data-stu-id="884ea-201">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="884ea-202">Расположение: 274, 42</span><span class="sxs-lookup"><span data-stu-id="884ea-202">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="884ea-203">Размер: 75, 23</span><span class="sxs-lookup"><span data-stu-id="884ea-203">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="884ea-204">Текст: Quit</span><span class="sxs-lookup"><span data-stu-id="884ea-204">Text: Quit</span></span>|
    |<span data-ttu-id="884ea-205">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="884ea-205">**TextBox**</span></span>|<span data-ttu-id="884ea-206">Имя: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="884ea-206">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="884ea-207">Расположение: 10, 73</span><span class="sxs-lookup"><span data-stu-id="884ea-207">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="884ea-208">Многострочный: true</span><span class="sxs-lookup"><span data-stu-id="884ea-208">Multiline: True</span></span><br /><br /> <span data-ttu-id="884ea-209">ReadOnly: true</span><span class="sxs-lookup"><span data-stu-id="884ea-209">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="884ea-210">Полосы прокрутки: по вертикали</span><span class="sxs-lookup"><span data-stu-id="884ea-210">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="884ea-211">Размер: 338, 208</span><span class="sxs-lookup"><span data-stu-id="884ea-211">Size: 338, 208</span></span>|

5. <span data-ttu-id="884ea-212">Задайте для свойства **AcceptButton** формы значение **ентергуесс**.</span><span class="sxs-lookup"><span data-stu-id="884ea-212">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="884ea-213">В следующем примере показана заполненная форма.</span><span class="sxs-lookup"><span data-stu-id="884ea-213">The following example illustrates the completed form.</span></span>

 ![Снимок экрана формы узла рабочего процесса Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a><span data-ttu-id="884ea-215">Добавление свойств и вспомогательных методов формы</span><span class="sxs-lookup"><span data-stu-id="884ea-215">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="884ea-216">В этом разделе показано, как добавить в класс формы свойства и вспомогательные методы, которые настраивают пользовательский интерфейс формы для запуска и возобновления рабочих процессов угадывания числа.</span><span class="sxs-lookup"><span data-stu-id="884ea-216">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="884ea-217">Щелкните правой кнопкой мыши **воркфловхостформ** в **Обозреватель решений** и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="884ea-217">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="884ea-218">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="884ea-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="884ea-219">Добавьте следующие объявления членов в класс **воркфловхостформ** .</span><span class="sxs-lookup"><span data-stu-id="884ea-219">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="884ea-220">Если у вас другая строка подключения, обновите строку `connectionString` так, чтобы она указывала на вашу базу данных.</span><span class="sxs-lookup"><span data-stu-id="884ea-220">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="884ea-221">Добавьте свойство `WorkflowInstanceId` в класс `WorkflowFormHost`.</span><span class="sxs-lookup"><span data-stu-id="884ea-221">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

    ```vb
    Public ReadOnly Property WorkflowInstanceId() As Guid
        Get
            If InstanceId.SelectedIndex = -1 Then
                Return Guid.Empty
            Else
                Return New Guid(InstanceId.SelectedItem.ToString())
            End If
        End Get
    End Property
    ```

    ```csharp
    public Guid WorkflowInstanceId
    {
        get
        {
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;
        }
    }
    ```

    <span data-ttu-id="884ea-222">В `InstanceId` поле со списком отображается список сохраненных идентификаторов экземпляров рабочих процессов, а `WorkflowInstanceId` свойство возвращает текущий выбранный рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="884ea-222">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="884ea-223">Добавьте обработчик события `Load` формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-223">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="884ea-224">Чтобы добавить обработчик, переключитесь в **режим конструктора** для формы, щелкните значок **событий** в верхней части окна **Свойства** и дважды щелкните **Load (загрузить**).</span><span class="sxs-lookup"><span data-stu-id="884ea-224">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="884ea-225">Добавьте в раздел `WorkflowHostForm_Load` следующий код.</span><span class="sxs-lookup"><span data-stu-id="884ea-225">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
    NumberRange.SelectedIndex = 0
    WorkflowType.SelectedIndex = 0

    ListPersistedWorkflows()
    ```

    ```csharp
    // Initialize the store and configure it so that it can be used for
    // multiple WorkflowApplication instances.
    store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    // Set default ComboBox selections.
    NumberRange.SelectedIndex = 0;
    WorkflowType.SelectedIndex = 0;

    ListPersistedWorkflows();
    ```

    <span data-ttu-id="884ea-226">Когда форма загружена, настраивается класс `SqlWorkflowInstanceStore`, для полей со списком диапазонов и типов рабочего процесса устанавливаются значения по умолчанию, а сохраненные экземпляры рабочих процессов добавляются в поле `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="884ea-226">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="884ea-227">Добавьте обработчик событий `SelectedIndexChanged` для `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="884ea-227">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="884ea-228">Чтобы добавить обработчик, переключитесь в **режим конструктора** для формы, выберите `InstanceId` поле со списком, щелкните значок **события** в верхней части окна " **Свойства** " и дважды щелкните элемент "," .</span><span class="sxs-lookup"><span data-stu-id="884ea-228">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="884ea-229">Добавьте в раздел `InstanceId_SelectedIndexChanged` следующий код.</span><span class="sxs-lookup"><span data-stu-id="884ea-229">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="884ea-230">Каждый раз, когда пользователь выбирает рабочий процесс с помощью поля со списком, этот обработчик обновляет окно состояния.</span><span class="sxs-lookup"><span data-stu-id="884ea-230">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
        instance.Abandon()
    End If
    ```

    ```csharp
    if (InstanceId.SelectedIndex == -1)
    {
        return;
    }

    // Clear the status window.
    WorkflowStatus.Clear();

    // Get the workflow version and display it.
    // If the workflow is just starting then this info will not
    // be available in the persistence store so do not try and retrieve it.
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="884ea-231">Добавьте следующий метод `ListPersistedWorkflows` в класс формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-231">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="884ea-232">`ListPersistedWorkflows` запрашивает у хранилища экземпляров сохраненные экземпляры рабочих процессов и добавляет их идентификаторы в поле со списком `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="884ea-232">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="884ea-233">Добавьте следующий метод `UpdateStatus` и соответствующий делегат в класс формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-233">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="884ea-234">Этот метод обновляет окно состояния в форме с данными о состоянии рабочего процесса, выполняемого в данный момент.</span><span class="sxs-lookup"><span data-stu-id="884ea-234">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length
            WorkflowStatus.ScrollToCaret()
        End If
    End Sub
    ```

    ```csharp
    private delegate void UpdateStatusDelegate(string msg);
    public void UpdateStatus(string msg)
    {
        // We may be on a different thread so we need to
        // make this call using BeginInvoke.
        if (InvokeRequired)
        {
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);
        }
        else
        {
            if (!msg.EndsWith("\r\n"))
            {
                msg += "\r\n";
            }
            WorkflowStatus.AppendText(msg);

            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;
            WorkflowStatus.ScrollToCaret();
        }
    }
    ```

11. <span data-ttu-id="884ea-235">Добавьте следующий метод `GameOver` и соответствующий делегат в класс формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-235">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="884ea-236">После завершения рабочего процесса этот метод обновляет пользовательский интерфейс формы, удаляя идентификатор экземпляра завершенного рабочего процесса из поля со списком **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="884ea-236">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem)
            InstanceId.SelectedIndex = -1
        End If
    End Sub
    ```

    ```csharp
    private delegate void GameOverDelegate();
    private void GameOver()
    {
        if (InvokeRequired)
        {
            BeginInvoke(new GameOverDelegate(GameOver));
        }
        else
        {
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a><span data-ttu-id="884ea-237">Настройка хранилища экземпляров, обработчиков жизненного цикла рабочего процесса и расширений</span><span class="sxs-lookup"><span data-stu-id="884ea-237">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="884ea-238">Добавьте метод `ConfigureWorkflowApplication` в класс формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-238">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="884ea-239">Этот метод задает `WorkflowApplication`, добавляет необходимые расширения и обработчики событий жизненного цикла рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-239">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="884ea-240">В `ConfigureWorkflowApplication` укажите `SqlWorkflowInstanceStore` для `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-240">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="884ea-241">Затем создайте экземпляр класса `StringWriter` и добавьте его в коллекцию `Extensions` приложения `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-241">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="884ea-242">При `StringWriter` добавлении к расширениям он фиксирует все `WriteLine` выходные данные действия.</span><span class="sxs-lookup"><span data-stu-id="884ea-242">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="884ea-243">Когда рабочий процесс становится неактивным, выходные данные `WriteLine` можно извлечь из `StringWriter` и показать на форме.</span><span class="sxs-lookup"><span data-stu-id="884ea-243">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="884ea-244">Добавьте следующий обработчик события `Completed`.</span><span class="sxs-lookup"><span data-stu-id="884ea-244">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="884ea-245">После успешного завершения рабочего процесса число ходов, которое потребовалось для угадывания числа, отображается в окне состояния.</span><span class="sxs-lookup"><span data-stu-id="884ea-245">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="884ea-246">Если рабочий процесс завершается, выдаются сведения об исключении, которое явилось причиной.</span><span class="sxs-lookup"><span data-stu-id="884ea-246">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="884ea-247">В конце обработчика вызывается метод `GameOver`, который удаляет завершенный рабочий процесс из списка рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="884ea-247">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="884ea-248">Добавьте следующие обработчики `Aborted` и `OnUnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="884ea-248">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="884ea-249">Метод `GameOver` не вызывается из обработчика `Aborted`, поскольку в случае аварийного завершения выполнения экземпляра рабочего процесса работа экземпляра не прекращается окончательно, позже можно перезапустить экземпляр.</span><span class="sxs-lookup"><span data-stu-id="884ea-249">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="884ea-250">Добавьте следующий обработчик `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="884ea-250">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="884ea-251">Этот обработчик получает расширение `StringWriter`, которое было добавлено, извлекает данные из действий `WriteLine` и отображает их в окне состояния.</span><span class="sxs-lookup"><span data-stu-id="884ea-251">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()
            For Each writer In writers
                UpdateStatus(writer.ToString())
            Next
            Return PersistableIdleAction.Unload
        End Function
    ```

    ```csharp
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
    {
        // Send the current WriteLine outputs to the status window.
        var writers = e.GetInstanceExtensions<StringWriter>();
        foreach (var writer in writers)
        {
            UpdateStatus(writer.ToString());
        }
        return PersistableIdleAction.Unload;
    };
    ```

    <span data-ttu-id="884ea-252">Для перечисления <xref:System.Activities.PersistableIdleAction> существует три значения: <xref:System.Activities.PersistableIdleAction.None>,<xref:System.Activities.PersistableIdleAction.Persist> и <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="884ea-252">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="884ea-253">Значение <xref:System.Activities.PersistableIdleAction.Persist> вызывает сохранение рабочего процесса, но не его выгрузку.</span><span class="sxs-lookup"><span data-stu-id="884ea-253"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="884ea-254">Значение <xref:System.Activities.PersistableIdleAction.Unload> вызывает сохранение и выгрузку рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-254"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="884ea-255">Ниже приведен полный пример метода `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-255">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()
                For Each writer In writers
                    UpdateStatus(writer.ToString())
                Next
                Return PersistableIdleAction.Unload
            End Function
    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
        // Configure the persistence store.
        wfApp.InstanceStore = store;

        // Add a StringWriter to the extensions. This captures the output
        // from the WriteLine activities so we can display it in the form.
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
            GameOver();
            return UnhandledExceptionAction.Terminate;
        };

        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
        {
            // Send the current WriteLine outputs to the status window.
            var writers = e.GetInstanceExtensions<StringWriter>();
            foreach (var writer in writers)
            {
                UpdateStatus(writer.ToString());
            }
            return PersistableIdleAction.Unload;
        };
    }
    ```

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a><span data-ttu-id="884ea-256">Разрешение запуска и возобновления нескольких типов рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="884ea-256">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="884ea-257">Чтобы возобновить экземпляр рабочего процесса, ведущее приложение должно предоставить определение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-257">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="884ea-258">В этом учебнике описано 3 типа рабочих процессов и далее предоставлено несколько версий этих типов.</span><span class="sxs-lookup"><span data-stu-id="884ea-258">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="884ea-259">`WorkflowIdentity` позволяет ведущему приложению связать идентификационные данные с сохраненным экземпляром рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-259">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="884ea-260">В этом разделе показано, как создать служебный класс, который поможет сопоставить идентификационные данные из сохраненного экземпляра рабочего процесса с соответствующим определением рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-260">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="884ea-261">Дополнительные сведения о `WorkflowIdentity` и управлении версиями см. [в разделе Использование WorkflowIdentity и управление версиями](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="884ea-261">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="884ea-262">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите **добавить**, **класс**.</span><span class="sxs-lookup"><span data-stu-id="884ea-262">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="884ea-263">Введите `WorkflowVersionMap` в поле **имя** и нажмите кнопку **добавить**.</span><span class="sxs-lookup"><span data-stu-id="884ea-263">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="884ea-264">Добавьте следующие инструкции `using` или `Imports` в начало файла с другими инструкциями `using` или `Imports`.</span><span class="sxs-lookup"><span data-stu-id="884ea-264">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. <span data-ttu-id="884ea-265">Замените объявление класса `WorkflowVersionMap` следующим объявлением.</span><span class="sxs-lookup"><span data-stu-id="884ea-265">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
       }
    }
    ```

    <span data-ttu-id="884ea-266">`WorkflowVersionMap` содержит три удостоверения рабочего процесса, которые сопоставляются с тремя определениями рабочих процессов из этого учебника и используются в следующих разделах при запуске и возобновлении рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="884ea-266">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

## <a name="to-start-a-new-workflow"></a><span data-ttu-id="884ea-267">Запуск нового рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-267">To start a new workflow</span></span>

1. <span data-ttu-id="884ea-268">Добавьте обработчик событий `Click` для `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="884ea-268">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="884ea-269">Чтобы добавить обработчик, переключитесь в **режим конструктора** для формы и дважды щелкните `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="884ea-269">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="884ea-270">Добавляется обработчик `NewGame_Click`, и активируется представление кода формы.</span><span class="sxs-lookup"><span data-stu-id="884ea-270">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="884ea-271">Когда пользователь нажимает эту кнопку, запускается новый рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="884ea-271">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="884ea-272">Добавьте следующий код в обработчик события щелчка.</span><span class="sxs-lookup"><span data-stu-id="884ea-272">Add the following code to the click handler.</span></span> <span data-ttu-id="884ea-273">Этот код создает словарь входных аргументов для рабочего процесса, различаемых по имени аргумента.</span><span class="sxs-lookup"><span data-stu-id="884ea-273">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="884ea-274">Этот словарь содержит одну запись с диапазоном случайного созданных чисел, полученных из поля со списком диапазонов.</span><span class="sxs-lookup"><span data-stu-id="884ea-274">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="884ea-275">Затем добавьте следующий код, который запускает рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="884ea-275">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="884ea-276">`WorkflowIdentity` и определение рабочего процесса, соответствующие выбранному типу рабочего процесса, извлекаются с помощью вспомогательного класса `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="884ea-276">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="884ea-277">Затем создается новый экземпляр `WorkflowApplication` с помощью определения рабочего процесса, `WorkflowIdentity` и словаря входных аргументов.</span><span class="sxs-lookup"><span data-stu-id="884ea-277">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

    ```vb
    Dim identity As WorkflowIdentity = Nothing
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
    End Select

    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

    Dim wfApp = New WorkflowApplication(wf, inputs, identity)
    ```

    ```csharp
    WorkflowIdentity identity = null;
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;
    };

    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);
    ```

4. <span data-ttu-id="884ea-278">Затем необходимо добавить следующий код, который добавляет рабочий процесс в список рабочих процессов и отображает сведения о версии рабочего процесса на форме.</span><span class="sxs-lookup"><span data-stu-id="884ea-278">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. <span data-ttu-id="884ea-279">Вызовите `ConfigureWorkflowApplication` для настройки хранилища экземпляров, расширений и обработчиков жизненного цикла рабочего процесса для экземпляра `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-279">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="884ea-280">Теперь вызовите `Run`.</span><span class="sxs-lookup"><span data-stu-id="884ea-280">Finally, call `Run`.</span></span>

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="884ea-281">Ниже приведен полный пример обработчика `NewGame_Click`.</span><span class="sxs-lookup"><span data-stu-id="884ea-281">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
        Dim inputs As New Dictionary(Of String, Object)()
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))

        Dim identity As WorkflowIdentity = Nothing
        Select Case WorkflowType.SelectedItem.ToString()
            Case "SequentialNumberGuessWorkflow"
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity

            Case "StateMachineNumberGuessWorkflow"
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

            Case "FlowchartNumberGuessWorkflow"
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
        End Select

        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

        Dim wfApp = New WorkflowApplication(wf, inputs, identity)

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
        wfApp.Run()
    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {
        var inputs = new Dictionary<string, object>();
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));

        WorkflowIdentity identity = null;
        switch (WorkflowType.SelectedItem.ToString())
        {
            case "SequentialNumberGuessWorkflow":
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
                break;

            case "StateMachineNumberGuessWorkflow":
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
                break;

            case "FlowchartNumberGuessWorkflow":
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
                break;
        };

        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a><span data-ttu-id="884ea-282">Возобновление рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-282">To resume a workflow</span></span>

1. <span data-ttu-id="884ea-283">Добавьте обработчик событий `Click` для `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="884ea-283">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="884ea-284">Чтобы добавить обработчик, переключитесь в **режим конструктора** для формы и дважды щелкните `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="884ea-284">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="884ea-285">Когда пользователь нажимает эту кнопку, возобновляется рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="884ea-285">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="884ea-286">Добавьте следующий код, чтобы убедиться в том, что рабочий процесс выбран в списке рабочих процессов и догадка пользователя верна.</span><span class="sxs-lookup"><span data-stu-id="884ea-286">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim userGuess As Integer
    If Not Int32.TryParse(Guess.Text, userGuess) Then
        MessageBox.Show("Please enter an integer.")
        Guess.SelectAll()
        Guess.Focus()
        Return
    End If
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    int guess;
    if (!Int32.TryParse(Guess.Text, out guess))
    {
        MessageBox.Show("Please enter an integer.");
        Guess.SelectAll();
        Guess.Focus();
        return;
    }
    ```

3. <span data-ttu-id="884ea-287">Затем извлеките `WorkflowApplicationInstance` сохраненного экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-287">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="884ea-288">`WorkflowApplicationInstance` представляет экземпляр сохраненного рабочего процесса, который еще не был связан с определением рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-288">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="884ea-289">`DefinitionIdentity` экземпляра `WorkflowApplicationInstance` содержит `WorkflowIdentity` экземпляра сохраненного рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-289">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="884ea-290">В этом учебнике служебный класс `WorkflowVersionMap` используется для сопоставления `WorkflowIdentity` с соответствующим определением рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="884ea-290">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="884ea-291">Когда определение рабочего процесса получено, создается приложение `WorkflowApplication` на основе правильного определения.</span><span class="sxs-lookup"><span data-stu-id="884ea-291">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="884ea-292">После создания `WorkflowApplication` настройте хранилище экземпляров, обработчики жизненного цикла рабочего процесса и расширения, вызвав `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-292">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="884ea-293">Эти шаги требуются каждый раз, когда создается новое приложение `WorkflowApplication`, и должны быть выполнены до того, как экземпляр рабочего процесса будет загружен в `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-293">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="884ea-294">После загрузки рабочего процесса он возобновляется с догадкой пользователя.</span><span class="sxs-lookup"><span data-stu-id="884ea-294">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", userGuess)
    ```

    ```csharp
    // Configure the extensions and lifecycle handlers.
    // Do this before the instance is loaded. Once the instance is
    // loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", guess);
    ```

5. <span data-ttu-id="884ea-295">И наконец, очистите текстовое поле с догадкой и подготовьте форму для ввода другой догадки.</span><span class="sxs-lookup"><span data-stu-id="884ea-295">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="884ea-296">Ниже приведен полный пример обработчика `EnterGuess_Click`.</span><span class="sxs-lookup"><span data-stu-id="884ea-296">The following example is the completed `EnterGuess_Click` handler.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click
        If WorkflowInstanceId = Guid.Empty Then
            MessageBox.Show("Please select a workflow.")
            Return
        End If

        Dim userGuess As Integer
        If Not Int32.TryParse(Guess.Text, userGuess) Then
            MessageBox.Show("Please enter an integer.")
            Guess.SelectAll()
            Guess.Focus()
            Return
        End If

        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
        Guess.Clear()
        Guess.Focus()
    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {
        if (WorkflowInstanceId == Guid.Empty)
        {
            MessageBox.Show("Please select a workflow.");
            return;
        }

        int guess;
        if (!Int32.TryParse(Guess.Text, out guess))
        {
            MessageBox.Show("Please enter an integer.");
            Guess.SelectAll();
            Guess.Focus();
            return;
        }

        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);

        // Use the persisted WorkflowIdentity to retrieve the correct workflow
        // definition from the dictionary.
        Activity wf =
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

        // Associate the WorkflowApplication with the correct definition
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

        // Configure the extensions and lifecycle handlers.
        // Do this before the instance is loaded. Once the instance is
        // loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp);

        // Load the workflow.
        wfApp.Load(instance);

        // Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", guess);

        // Clear the Guess textbox.
        Guess.Clear();
        Guess.Focus();
    }
    ```

## <a name="to-terminate-a-workflow"></a><span data-ttu-id="884ea-297">Завершение рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="884ea-297">To terminate a workflow</span></span>

1. <span data-ttu-id="884ea-298">Добавьте обработчик событий `Click` для `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="884ea-298">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="884ea-299">Чтобы добавить обработчик, переключитесь в **режим конструктора** для формы и дважды щелкните `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="884ea-299">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="884ea-300">Когда пользователь нажимает эту кнопку, рабочий процесс, выбранный на данный момент, завершается.</span><span class="sxs-lookup"><span data-stu-id="884ea-300">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="884ea-301">Добавьте следующий код в обработчик `QuitGame_Click`:</span><span class="sxs-lookup"><span data-stu-id="884ea-301">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="884ea-302">Code First проверяет, что рабочий процесс выбран в списке рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="884ea-302">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="884ea-303">Затем он загружает сохраненный экземпляр в `WorkflowApplicationInstance`, использует `DefinitionIdentity` для получения правильного определения рабочего процесса и инициализирует `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-303">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="884ea-304">После этого настраиваются расширения и обработчики жизненного цикла рабочего процесса с помощью метода `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="884ea-304">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="884ea-305">После настройки `WorkflowApplication` приложение загружается и вызывается метод `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="884ea-305">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
    wfApp.Terminate("User resigns.")
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a><span data-ttu-id="884ea-306">Построение и запуск приложения</span><span class="sxs-lookup"><span data-stu-id="884ea-306">To build and run the application</span></span>

1. <span data-ttu-id="884ea-307">Дважды щелкните **Program.CS** (или **Module1. vb**) в **Обозреватель решений** , чтобы отобразить код.</span><span class="sxs-lookup"><span data-stu-id="884ea-307">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="884ea-308">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="884ea-308">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="884ea-309">Удалите или закомментируйте существующий код размещения рабочего процесса из [руководства: запуск рабочего процесса](how-to-run-a-workflow.md)и замените его следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="884ea-309">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

    ```vb
    Sub Main()
        Application.EnableVisualStyles()
        Application.Run(New WorkflowHostForm())
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        Application.EnableVisualStyles();
        Application.Run(new WorkflowHostForm());
    }
    ```

4. <span data-ttu-id="884ea-310">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="884ea-310">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="884ea-311">На вкладке **приложение** укажите **приложение Windows** для **типа выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="884ea-311">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="884ea-312">Этот шаг не обязателен, но, если его не выполнить, вместе с формой отображается окно консоли.</span><span class="sxs-lookup"><span data-stu-id="884ea-312">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="884ea-313">Нажмите клавиши Ctrl+Shift+B, чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="884ea-313">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="884ea-314">Убедитесь, что **NumberGuessWorkflowHost** установлен в качестве запускаемого приложения, и нажмите клавиши CTRL + F5, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="884ea-314">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="884ea-315">Выберите диапазон для игры подбора и тип рабочего процесса, который нужно запустить, и щелкните **Новая игра**.</span><span class="sxs-lookup"><span data-stu-id="884ea-315">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="884ea-316">Введите предположение в поле **предположение** и нажмите кнопку **Перейти** , чтобы отправить свое предположение.</span><span class="sxs-lookup"><span data-stu-id="884ea-316">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="884ea-317">Обратите внимание, что выходные данные действий `WriteLine` отображаются на форме.</span><span class="sxs-lookup"><span data-stu-id="884ea-317">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="884ea-318">Запустите несколько рабочих процессов, используя различные типы рабочих процессов и диапазоны номеров, введите некоторые предположения и переключайтесь между рабочими процессами, выбрав из списка **идентификатор экземпляра рабочего процесса** .</span><span class="sxs-lookup"><span data-stu-id="884ea-318">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="884ea-319">Обратите внимание, что, если перейти к новому рабочему процессу, предыдущие догадки и ход выполнения рабочего процесса не отображаются в окне состояния.</span><span class="sxs-lookup"><span data-stu-id="884ea-319">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="884ea-320">Состояние недоступно, так как оно не перехвачено и не сохранено.</span><span class="sxs-lookup"><span data-stu-id="884ea-320">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="884ea-321">На следующем шаге руководства [: как создать настраиваемый участник отслеживания](how-to-create-a-custom-tracking-participant.md)создайте настраиваемый участник отслеживания, сохраняющий эту информацию.</span><span class="sxs-lookup"><span data-stu-id="884ea-321">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
