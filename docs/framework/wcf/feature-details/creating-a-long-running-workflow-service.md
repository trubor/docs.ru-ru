---
description: Дополнительные сведения о создании длительно выполняемой службы рабочих процессов
title: Создание службы долго выполняющегося рабочего процесса
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 9d26e763e2515f9e9ec2b61201512f02eeaeb1bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756907"
---
# <a name="create-a-long-running-workflow-service"></a><span data-ttu-id="d8924-103">Создание длительно выполняющейся службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="d8924-103">Create a Long-running Workflow Service</span></span>

<span data-ttu-id="d8924-104">В данном разделе описывается, как создать службу длительных рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="d8924-104">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="d8924-105">Службы длительных рабочих процессов могут работать в течение долгого времени.</span><span class="sxs-lookup"><span data-stu-id="d8924-105">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="d8924-106">В определенные моменты рабочий процесс может переходить в состояние бездействия в ожидании дополнительных данных.</span><span class="sxs-lookup"><span data-stu-id="d8924-106">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="d8924-107">В этом случае рабочий процесс сохраняется в базе данных SQL и удаляется из памяти.</span><span class="sxs-lookup"><span data-stu-id="d8924-107">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="d8924-108">При поступлении дополнительных данных экземпляр рабочего процесса снова загружается в память и его выполнение продолжается.</span><span class="sxs-lookup"><span data-stu-id="d8924-108">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="d8924-109">В этом сценарии реализуется очень упрощенная система обработки заказов.</span><span class="sxs-lookup"><span data-stu-id="d8924-109">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="d8924-110">Клиент отправляет первоначальное сообщение службе рабочего процесса с указанием начать заказ.</span><span class="sxs-lookup"><span data-stu-id="d8924-110">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="d8924-111">Служба возвращает клиенту идентификатор заказа.</span><span class="sxs-lookup"><span data-stu-id="d8924-111">It returns an order ID to the client.</span></span> <span data-ttu-id="d8924-112">С этого момента в ожидании нового сообщения от клиента служба рабочего процесса переходит в состояние бездействия и сохраняется в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8924-112">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="d8924-113">Когда клиент отправит следующее сообщение, чтобы заказать товар, служба рабочего процесса будет снова загружена в память, после чего она завершит обработку заказа.</span><span class="sxs-lookup"><span data-stu-id="d8924-113">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="d8924-114">В приведенном образце кода служба возвращает строку, указывающую на то, что товар добавлен в заказ.</span><span class="sxs-lookup"><span data-stu-id="d8924-114">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="d8924-115">Этот образец кода не предполагает реализацию такого приложения в реальности, скорее это простой образец, иллюстрирующий работу служб длительных рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="d8924-115">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="d8924-116">В этом разделе предполагается, что вы умеете создавать проекты и решения Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d8924-116">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8924-117">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d8924-117">Prerequisites</span></span>

<span data-ttu-id="d8924-118">Чтобы воспользоваться этим пошаговым руководством, необходимо установить следующее программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="d8924-118">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="d8924-119">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="d8924-119">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="d8924-120">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="d8924-120">Visual Studio 2012</span></span>

3. <span data-ttu-id="d8924-121">Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8924-121">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="d8924-122">Вы знакомы с WCF и Visual Studio 2012 и знаете, как создавать проекты и решения.</span><span class="sxs-lookup"><span data-stu-id="d8924-122">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

## <a name="set-up-the-sql-database"></a><span data-ttu-id="d8924-123">Настройка базы данных SQL</span><span class="sxs-lookup"><span data-stu-id="d8924-123">Set up the SQL Database</span></span>

1. <span data-ttu-id="d8924-124">Для сохранения экземпляров служб рабочих процессов требуется установленный Microsoft SQL Server, на котором необходимо настроить базу данных для хранения выгруженных из памяти экземпляров рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="d8924-124">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="d8924-125">Запустите Microsoft SQL Management Studio, нажав кнопку **Пуск** , выбрав **все программы**, **Microsoft SQL Server 2008** и **Microsoft SQL Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="d8924-125">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="d8924-126">Чтобы войти в SQL Server экземпляр, нажмите кнопку " **Подключиться** "</span><span class="sxs-lookup"><span data-stu-id="d8924-126">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="d8924-127">Щелкните правой кнопкой мыши **базы данных** в представлении в виде дерева и выберите пункт **создать базу данных.**</span><span class="sxs-lookup"><span data-stu-id="d8924-127">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="d8924-128">для создания новой базы данных с именем `SQLPersistenceStore` .</span><span class="sxs-lookup"><span data-stu-id="d8924-128">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="d8924-129">Выполните в базе данных SQLPersistenceStore файл скрипта SqlWorkflowInstanceStoreSchema.sql, расположенный в каталоге C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en, чтобы настроить требуемые схемы базы данных.</span><span class="sxs-lookup"><span data-stu-id="d8924-129">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="d8924-130">Выполните в базе данных SQLPersistenceStore файл скрипта SqlWorkflowInstanceStoreLogic.sql, расположенный в каталоге C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en, чтобы настроить требуемую логику базы данных.</span><span class="sxs-lookup"><span data-stu-id="d8924-130">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

## <a name="create-the-web-hosted-workflow-service"></a><span data-ttu-id="d8924-131">Создание службы веб-размещения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="d8924-131">Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="d8924-132">Создайте пустое решение Visual Studio 2012, присвойте ему имя `OrderProcessing` .</span><span class="sxs-lookup"><span data-stu-id="d8924-132">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="d8924-133">Добавьте в него новый проект служебного приложения рабочего процесса WCF под названием `OrderService`.</span><span class="sxs-lookup"><span data-stu-id="d8924-133">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="d8924-134">В диалоговом окне Свойства проекта перейдите на вкладку **веб** .</span><span class="sxs-lookup"><span data-stu-id="d8924-134">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="d8924-135">В разделе **действие при запуске** выберите **определенная страница** и укажите `Service1.xamlx` .</span><span class="sxs-lookup"><span data-stu-id="d8924-135">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="d8924-136">![Веб-свойства проекта службы рабочего процесса](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Создание веб-страницы, размещенной в службе рабочего процесса, для конкретной службы")</span><span class="sxs-lookup"><span data-stu-id="d8924-136">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="d8924-137">В разделе **серверы** выберите **использовать локальный веб-сервер IIS**.</span><span class="sxs-lookup"><span data-stu-id="d8924-137">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="d8924-138">![Параметры локального веб-сервера](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Создание службы веб-размещения рабочих процессов — использование локального веб-сервера IIS")</span><span class="sxs-lookup"><span data-stu-id="d8924-138">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="d8924-139">Чтобы использовать этот параметр, необходимо запустить Visual Studio 2012 в режиме администратора.</span><span class="sxs-lookup"><span data-stu-id="d8924-139">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="d8924-140">Эти шаги необходимы, чтобы настроить размещение проекта службы рабочего процесса в IIS.</span><span class="sxs-lookup"><span data-stu-id="d8924-140">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="d8924-141">Откройте, `Service1.xamlx` если он еще не открыт, и удалите существующие действия **действия ReceiveRequest** и **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="d8924-141">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="d8924-142">Выберите действие **Последовательная служба** и щелкните ссылку **переменные** и добавьте переменные, показанные на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-142">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="d8924-143">Эти переменные будут в дальнейшем использоваться в службе рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d8924-143">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d8924-144">Если Коррелатионхандле не находится в раскрывающемся списке Тип переменной, выберите в раскрывающемся списке пункт **Обзор типов** .</span><span class="sxs-lookup"><span data-stu-id="d8924-144">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="d8924-145">Введите Коррелатионхандле в поле **имя типа** , выберите коррелатионхандле в списке и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d8924-145">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="d8924-146">![Добавить переменные](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Добавьте переменные в действие последовательной службы.")</span><span class="sxs-lookup"><span data-stu-id="d8924-146">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="d8924-147">Перетащите шаблон действия **ReceiveAndSendReply** в действие **последовательной службы** .</span><span class="sxs-lookup"><span data-stu-id="d8924-147">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="d8924-148">Этот набор действий будет получать сообщение от клиента и возвращать ему ответ.</span><span class="sxs-lookup"><span data-stu-id="d8924-148">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="d8924-149">Выберите действие **получить** и задайте свойства, выделенные на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-149">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="d8924-150">![Задание свойств действия Receive](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Задайте свойства действия получения.")</span><span class="sxs-lookup"><span data-stu-id="d8924-150">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="d8924-151">Свойство DisplayName задает имя, отображаемое для действия «Receive» в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="d8924-151">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="d8924-152">Свойства ServiceContractName и OperationName задают имя контракта службы и операции, которые реализуются действием Receive.</span><span class="sxs-lookup"><span data-stu-id="d8924-152">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="d8924-153">Дополнительные сведения об использовании контрактов в службах рабочих процессов см. в статье [использование контрактов в рабочем процессе](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d8924-153">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="d8924-154">Щелкните ссылку **define...** в действии **рецеивестартордер** и задайте свойства, показанные на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-154">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="d8924-155">Обратите внимание, что выбран переключатель **Параметры** , параметр с именем `p_customerName` привязан к `customerName` переменной.</span><span class="sxs-lookup"><span data-stu-id="d8924-155">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="d8924-156">Это настраивает действие **Receive** для получения данных и привязывает эти данные к локальным переменным.</span><span class="sxs-lookup"><span data-stu-id="d8924-156">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="d8924-157">![Задание данных, получаемых действием Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Задайте свойства для данных, полученных действием Receive.")</span><span class="sxs-lookup"><span data-stu-id="d8924-157">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="d8924-158">Выберите действие **SendReplyToReceive** и задайте выделенное свойство, показанное на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-158">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="d8924-159">![Задание свойств действия SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "сетреплипропертиес")</span><span class="sxs-lookup"><span data-stu-id="d8924-159">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="d8924-160">Щелкните ссылку **define...** в действии **сендреплитостартордер** и задайте свойства, показанные на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-160">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="d8924-161">Обратите внимание, что выбран переключатель **Параметры** ; параметр с именем `p_orderId` привязан к `orderId` переменной.</span><span class="sxs-lookup"><span data-stu-id="d8924-161">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="d8924-162">Этот параметр указывает, что действие SendReplyToStartOrder возвратит вызывающему объекту значение типа String.</span><span class="sxs-lookup"><span data-stu-id="d8924-162">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="d8924-163">![Настройка данных для содержимого действия SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Настройка параметра для действия Сетреплитостартордер.")</span><span class="sxs-lookup"><span data-stu-id="d8924-163">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="d8924-164">Перетащите действие Assign (назначение) между действиями **Receive** и **SendReply** и задайте свойства, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-164">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="d8924-165">![Добавление действия Assign](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Добавьте действие Assign.")</span><span class="sxs-lookup"><span data-stu-id="d8924-165">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="d8924-166">При этом будет создан новый идентификатор заказа, а его значение будет помещено в переменную orderId.</span><span class="sxs-lookup"><span data-stu-id="d8924-166">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="d8924-167">Выберите действие **реплитостартордер** .</span><span class="sxs-lookup"><span data-stu-id="d8924-167">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="d8924-168">В окне Свойства нажмите кнопку с многоточием для **CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="d8924-168">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="d8924-169">Выберите ссылку **Добавить инициализатор** , введите `orderIdHandle` в текстовом поле инициализатор, выберите инициализатор корреляции запросов для типа корреляции и выберите p_orderId в раскрывающемся списке запросы XPath.</span><span class="sxs-lookup"><span data-stu-id="d8924-169">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="d8924-170">Эти параметры показаны на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-170">These settings are shown in the following illustration.</span></span> <span data-ttu-id="d8924-171">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8924-171">Click **OK**.</span></span>  <span data-ttu-id="d8924-172">При этом будет инициализирована новая корреляция между клиентом и этим экземпляром службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d8924-172">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="d8924-173">При получении сообщения с этим идентификатором заказа оно будет направлено этому экземпляру службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d8924-173">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="d8924-174">![Добавление инициализатора корреляции](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Добавьте инициализатор корреляции.")</span><span class="sxs-lookup"><span data-stu-id="d8924-174">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="d8924-175">Перетащите еще одно действие **ReceiveAndSendReply** в конец рабочего процесса (за пределами **последовательности** , содержащей первые действия **Receive** и **SendReply** ).</span><span class="sxs-lookup"><span data-stu-id="d8924-175">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="d8924-176">Оно получит второе сообщение от клиента и ответит на него.</span><span class="sxs-lookup"><span data-stu-id="d8924-176">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="d8924-177">Выберите **последовательность** , содержащую только что добавленные действия **Receive** и **SendReply** , и нажмите кнопку **переменные** .</span><span class="sxs-lookup"><span data-stu-id="d8924-177">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="d8924-178">Добавьте переменную, отмеченную на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-178">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="d8924-179">![Добавление новых переменных](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Добавьте переменную ItemId.")</span><span class="sxs-lookup"><span data-stu-id="d8924-179">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="d8924-180">Также добавьте `orderResult` в область в качестве **строки** `Sequence` .</span><span class="sxs-lookup"><span data-stu-id="d8924-180">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="d8924-181">Выберите действие **получить** и задайте свойства, показанные на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="d8924-181">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="d8924-182">![Задание свойств действия получения](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Задайте свойства действий получения.")</span><span class="sxs-lookup"><span data-stu-id="d8924-182">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="d8924-183">Не забудьте изменить поле **одинаковыми servicecontractname** на `../IAddItem` .</span><span class="sxs-lookup"><span data-stu-id="d8924-183">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="d8924-184">Щелкните ссылку **define...** в действии **рецеивеаддитем** и добавьте параметры, показанные на следующем рисунке: настраивает действие Receive для принятия двух параметров, идентификатор заказа и идентификатор упорядоченного элемента.</span><span class="sxs-lookup"><span data-stu-id="d8924-184">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="d8924-185">![Указание параметров для второго получения](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Настройте действие Receive для получения двух параметров.")</span><span class="sxs-lookup"><span data-stu-id="d8924-185">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="d8924-186">Нажмите кнопку с многоточием **коррелатеон** и введите `orderIdHandle` .</span><span class="sxs-lookup"><span data-stu-id="d8924-186">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="d8924-187">В разделе **запросы XPath** щелкните стрелку раскрывающегося списка и выберите `p_orderId` .</span><span class="sxs-lookup"><span data-stu-id="d8924-187">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="d8924-188">При этом будет настроена корреляция второго действия Receive.</span><span class="sxs-lookup"><span data-stu-id="d8924-188">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="d8924-189">Дополнительные сведения о корреляции см. в разделе [корреляция](correlation.md).</span><span class="sxs-lookup"><span data-stu-id="d8924-189">For more information about correlation see [Correlation](correlation.md).</span></span>

        <span data-ttu-id="d8924-190">![Задание свойства CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Задайте свойство CorrelatesOn.")</span><span class="sxs-lookup"><span data-stu-id="d8924-190">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="d8924-191">Перетаскивание действия **If** сразу после действия **рецеивеаддитем** .</span><span class="sxs-lookup"><span data-stu-id="d8924-191">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="d8924-192">Это действие работает аналогично инструкции IF.</span><span class="sxs-lookup"><span data-stu-id="d8924-192">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="d8924-193">Присвойте свойству **Condition** значение. `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="d8924-193">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="d8924-194">Перетащите действие Assign ( **назначение** ) в раздел Then, а другой **—** в раздел **else** , чтобы установить свойства действий **назначения** , как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-194">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="d8924-195">![Задание результата вызова службы](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Назначьте результат вызова службы.")</span><span class="sxs-lookup"><span data-stu-id="d8924-195">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="d8924-196">Если условием является `true` , будет выполнен раздел **then** .</span><span class="sxs-lookup"><span data-stu-id="d8924-196">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="d8924-197">Значение, если условие выполняется `false` в разделе **else** .</span><span class="sxs-lookup"><span data-stu-id="d8924-197">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="d8924-198">Выберите действие **SendReplyToReceive** и задайте свойство **DisplayName** , как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-198">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="d8924-199">![Задание свойств действия SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Задайте свойство действия SendReply.")</span><span class="sxs-lookup"><span data-stu-id="d8924-199">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="d8924-200">Щелкните ссылку **define...** в действии **сетреплитоаддитем** и настройте его, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="d8924-200">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="d8924-201">Это настраивает действие **сендреплитоаддитем** для возврата значения в `orderResult` переменной.</span><span class="sxs-lookup"><span data-stu-id="d8924-201">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="d8924-202">![Настройка привязки данных для действия SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Задание свойства для действия Сендреплитоаддитем.")</span><span class="sxs-lookup"><span data-stu-id="d8924-202">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="d8924-203">Откройте файл web.config и добавьте в раздел следующие элементы, \<behavior> чтобы включить сохранение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d8924-203">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="d8924-204">В приведенном выше фрагменте кода необходимо заменить имя узла и экземпляра SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8924-204">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="d8924-205">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="d8924-205">Build the solution.</span></span>

## <a name="create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="d8924-206">Создание клиентского приложения для вызова службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="d8924-206">Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="d8924-207">Добавьте в решение новый проект консольного приложения с именем `OrderClient`.</span><span class="sxs-lookup"><span data-stu-id="d8924-207">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="d8924-208">Добавьте в проект `OrderClient` ссылки на следующие сборки:</span><span class="sxs-lookup"><span data-stu-id="d8924-208">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="d8924-209">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="d8924-209">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="d8924-210">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d8924-210">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="d8924-211">Добавьте ссылку на службу рабочего процесса и укажите `OrderService` в качестве пространства имен.</span><span class="sxs-lookup"><span data-stu-id="d8924-211">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="d8924-212">В метод `Main()` клиентского проекта добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="d8924-212">In the `Main()` method of the client project add the following code:</span></span>

    ```csharp
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. <span data-ttu-id="d8924-213">Выполните построение решения и запустите приложение `OrderClient`.</span><span class="sxs-lookup"><span data-stu-id="d8924-213">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="d8924-214">Клиент выведет на экран следующий текст.</span><span class="sxs-lookup"><span data-stu-id="d8924-214">The client will display the following text:</span></span>

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="d8924-215">Чтобы убедиться, что служба рабочего процесса сохранена, запустите SQL Server Management Studio, перейдя в меню " **Пуск** ", выбрав " **все программы**", **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="d8924-215">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="d8924-216">В области слева разверните, **базы данных**, **склперсистенцесторе**, **представления** и щелкните правой кнопкой мыши элемент **System. activitys. DurableInstancing. instances** и выберите **пункт выбрать первые 1000 строк**.</span><span class="sxs-lookup"><span data-stu-id="d8924-216">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="d8924-217">Убедитесь, что в области **результатов** отображается хотя бы один экземпляр.</span><span class="sxs-lookup"><span data-stu-id="d8924-217">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="d8924-218">Если во время работы возникнет исключение, в этой области могут быть указаны и другие экземпляры, оставшиеся от прошлых запусков.</span><span class="sxs-lookup"><span data-stu-id="d8924-218">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="d8924-219">Можно удалить существующие строки, щелкнув правой кнопкой мыши **System. activitys. DurableInstancing. Instances** и выбрав пункт **изменить первые 200 строк**, нажав кнопку **выполнить** , выбрав все строки на панели результатов и выбрав пункт **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="d8924-219">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="d8924-220">Чтобы проверить, что в базе данных отображается экземпляр, созданный учебным приложением, перед запуском клиента удалите все записи из представления экземпляров.</span><span class="sxs-lookup"><span data-stu-id="d8924-220">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="d8924-221">После запуска клиента выполните этот запрос («Выделить 1000 верхних строк») еще раз и удостоверьтесь, что новый экземпляр добавлен.</span><span class="sxs-lookup"><span data-stu-id="d8924-221">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="d8924-222">Нажмите клавишу ВВОД, чтобы отправить сообщение о добавлении товара службе рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d8924-222">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="d8924-223">Клиент выведет на экран следующий текст.</span><span class="sxs-lookup"><span data-stu-id="d8924-223">The client will display the following text:</span></span>

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="d8924-224">См. также</span><span class="sxs-lookup"><span data-stu-id="d8924-224">See also</span></span>

- [<span data-ttu-id="d8924-225">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="d8924-225">Workflow Services</span></span>](workflow-services.md)
