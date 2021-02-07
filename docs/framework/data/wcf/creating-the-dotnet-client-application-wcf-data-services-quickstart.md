---
description: 'Дополнительные сведения: Создание клиентского приложения платформа .NET Framework (краткое руководство по службы данных WCF)'
title: Создание клиентского приложения .NET Framework (краткое руководство по службам данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 6a397726b0680d4091f7cefd8928e43c74dc08bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766229"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="12746-103">Создание клиентского приложения .NET Framework (краткое руководство по службам данных WCF)</span><span class="sxs-lookup"><span data-stu-id="12746-103">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="12746-104">Это последняя задача краткого руководства по службы данных WCF.</span><span class="sxs-lookup"><span data-stu-id="12746-104">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="12746-105">В этой задаче вы добавите в решение консольное приложение, добавите ссылку на веб-канал Open Data Protocol (OData) в это новое клиентское приложение и получите доступ к каналу OData из клиентского приложения, используя созданные классы клиентской службы данных и клиентские библиотеки.</span><span class="sxs-lookup"><span data-stu-id="12746-105">In this task, you will add a console application to the solution, add a reference to the Open Data Protocol (OData) feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="12746-106">Для доступа к каналу данных наличие клиентского приложения на основе .NET Framework необязательно.</span><span class="sxs-lookup"><span data-stu-id="12746-106">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="12746-107">Доступ к службе данных может осуществляться любым компонентом приложения, использующим канал OData.</span><span class="sxs-lookup"><span data-stu-id="12746-107">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="12746-108">Дополнительные сведения см. [в разделе Использование службы данных в клиентском приложении](using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="12746-108">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="12746-109">Создание клиентского приложения в среде Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12746-109">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="12746-110">В **Обозреватель решений** щелкните решение правой кнопкой мыши, выберите **Добавить**, а затем — **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="12746-110">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="12746-111">В левой области выберите **установленные** > [**Visual C#** или **Visual Basic**] > **Рабочий стол Windows**, а затем выберите шаблон **приложения WPF** .</span><span class="sxs-lookup"><span data-stu-id="12746-111">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="12746-112">Введите `NorthwindClient` в качестве имени проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="12746-112">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="12746-113">Откройте файл MainWindow.xaml и замените XAML-код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="12746-113">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="12746-114">Добавление в проект ссылки на службу данных</span><span class="sxs-lookup"><span data-stu-id="12746-114">To add a data service reference to the project</span></span>

1. <span data-ttu-id="12746-115">В **Обозреватель решений** щелкните правой кнопкой мыши проект узлом NorthwindClient, выберите команду **Добавить**  >  **ссылку на службу**, а затем нажмите кнопку **обнаружить**.</span><span class="sxs-lookup"><span data-stu-id="12746-115">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="12746-116">При этом отображается служба данных Northwind, созданная в первой задаче.</span><span class="sxs-lookup"><span data-stu-id="12746-116">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="12746-117">В текстовом поле **пространство имен** введите `Northwind` , а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="12746-117">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="12746-118">При этом в проект добавляется новый файл кода, содержащий классы данных, которые используются для обращения и взаимодействия с ресурсами службы данных как с объектами.</span><span class="sxs-lookup"><span data-stu-id="12746-118">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="12746-119">Классы данных создаются в пространстве имен `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="12746-119">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="12746-120">Обращение к данным службы данных в приложении WPF</span><span class="sxs-lookup"><span data-stu-id="12746-120">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="12746-121">В **Обозреватель решений** в разделе **узлом NorthwindClient** щелкните правой кнопкой мыши проект и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="12746-121">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="12746-122">В диалоговом окне **Добавление ссылки** перейдите на вкладку **.net** , выберите System.Data.Services.Client.dll сборку и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="12746-122">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="12746-123">В **Обозреватель решений** в разделе **узлом NorthwindClient** откройте кодовую страницу файла MainWindow. XAML и добавьте следующую `using` инструкцию ( `Imports` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="12746-123">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="12746-124">Вставьте следующий код, запрашивающий службу данных и привязывающий результат к коллекции <xref:System.Data.Services.Client.DataServiceCollection%601> класса `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="12746-124">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="12746-125">Имя узла `localhost:12345` нужно заменить на сервер и порт, на котором размещен экземпляр службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="12746-125">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="12746-126">Вставьте следующий код, сохраняющий изменения, в класс `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="12746-126">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="12746-127">Сборка и запуск приложения NothwindClient</span><span class="sxs-lookup"><span data-stu-id="12746-127">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="12746-128">В **Обозреватель решений** щелкните правой кнопкой мыши проект узлом NorthwindClient и выберите **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="12746-128">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="12746-129">Чтобы запустить приложение, нажмите клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="12746-129">Press **F5** to start the application.</span></span>

     <span data-ttu-id="12746-130">При этом выполняется сборка решения и запуск клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="12746-130">This builds the solution and starts the client application.</span></span> <span data-ttu-id="12746-131">Данные извлекаются из службы данных и отображаются в консоли.</span><span class="sxs-lookup"><span data-stu-id="12746-131">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="12746-132">Измените значение в столбце **количество** сетки данных и нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="12746-132">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="12746-133">Изменения будут сохранены в службе данных.</span><span class="sxs-lookup"><span data-stu-id="12746-133">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="12746-134">Эта версия приложения NorthwindClient не поддерживает добавление и удаление сущностей.</span><span class="sxs-lookup"><span data-stu-id="12746-134">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="12746-135">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="12746-135">Next Steps</span></span>

<span data-ttu-id="12746-136">Вы успешно создали клиентское приложение, которое обращается к примеру веб-канала OData Northwind.</span><span class="sxs-lookup"><span data-stu-id="12746-136">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="12746-137">Вы также выполнили службы данных WCF быстрый запуск.</span><span class="sxs-lookup"><span data-stu-id="12746-137">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="12746-138">Дополнительные сведения о доступе к каналу OData из платформа .NET Framework приложения см. в разделе [службы данных WCF Client Library](wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="12746-138">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12746-139">См. также</span><span class="sxs-lookup"><span data-stu-id="12746-139">See also</span></span>

- [<span data-ttu-id="12746-140">Начало работы</span><span class="sxs-lookup"><span data-stu-id="12746-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="12746-141">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="12746-141">Resources</span></span>](wcf-data-services-resources.md)
