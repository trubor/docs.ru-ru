---
title: Создание службы данных WCF в Visual Studio
description: Узнайте, как создать образец службы данных, который использует службы данных WCF для предоставления веб-канала OData на основе образца базы данных.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 04c91483587c8976e40584474ced2f5474ab89f4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805770"
---
# <a name="create-the-data-service"></a><span data-ttu-id="ce2bc-103">Создание службы данных</span><span class="sxs-lookup"><span data-stu-id="ce2bc-103">Create the data service</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="ce2bc-104">В этом разделе вы создадите образец службы данных, который использует службы данных WCF для предоставления веб-канала Open Data Protocol (OData), основанного на образце базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="ce2bc-105">Задача включает следующие основные шаги.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="ce2bc-106">создайте веб-приложение ASP.NET;</span><span class="sxs-lookup"><span data-stu-id="ce2bc-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="ce2bc-107">Определение модели данных с использованием средств для работы с моделью EDM.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="ce2bc-108">Добавление службы данных в веб-приложение.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="ce2bc-109">Включите доступ к службе данных.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="ce2bc-110">Создание веб-приложения ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce2bc-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="ce2bc-111">В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="ce2bc-112">В диалоговом окне **Новый проект** в разделе Visual Basic или Visual C# выберите категорию **веб-узел** , а затем выберите **ASP.NET Web Application (веб-приложение**).</span><span class="sxs-lookup"><span data-stu-id="ce2bc-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="ce2bc-113">Введите в `NorthwindService` качестве имени проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="ce2bc-114">В диалоговом окне **новое веб-приложение ASP.NET** выберите **пусто** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="ce2bc-115">(Необязательно) Укажите конкретный номер порта для веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="ce2bc-116">Примечание. номер порта `12345` используется в этой серии кратких руководств.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="ce2bc-117">В **Обозреватель решений** щелкните правой кнопкой мыши только что созданный проект ASP.NET, а затем выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="ce2bc-118">Перейдите на вкладку **веб** и задайте для параметра **конкретный порт** значение `12345` .</span><span class="sxs-lookup"><span data-stu-id="ce2bc-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="ce2bc-119">Определение модели данных</span><span class="sxs-lookup"><span data-stu-id="ce2bc-119">Define the data model</span></span>

1. <span data-ttu-id="ce2bc-120">В **Обозреватель решений** щелкните правой кнопкой мыши имя проекта ASP.NET и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="ce2bc-121">В диалоговом окне **Добавление нового элемента** выберите категорию **данные** , а затем выберите **ADO.NET EDM**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="ce2bc-122">В качестве имени модели данных введите `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="ce2bc-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="ce2bc-123">В **мастере EDM** выберите элемент **конструктор EF из базы данных**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="ce2bc-124">Подключите модель данных к базе данных, выполнив одно из следующих действий, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="ce2bc-125">Если подключение к базе данных уже не настроено, щелкните **создать подключение** и создайте новое подключение.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="ce2bc-126">Дополнительные сведения см. в разделе [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ce2bc-126">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="ce2bc-127">Этот экземпляр SQL Server должен содержать присоединенный образец базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="ce2bc-128">\- или -</span><span class="sxs-lookup"><span data-stu-id="ce2bc-128">\- or -</span></span>

    - <span data-ttu-id="ce2bc-129">Если имеется уже настроенное подключение к базе данных Northwind, выберите это подключение из списка.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="ce2bc-130">На завершающей странице мастера установите флажки для всех таблиц базы данных и снимите флажки для представлений и хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="ce2bc-131">Нажмите кнопку **Готово** , чтобы закрыть мастер.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="ce2bc-132">Создание службы данных WCF</span><span class="sxs-lookup"><span data-stu-id="ce2bc-132">Create the WCF data service</span></span>

1. <span data-ttu-id="ce2bc-133">В **Обозреватель решений** щелкните правой кнопкой мыши проект ASP.NET и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="ce2bc-134">В диалоговом окне **Добавление нового элемента** выберите шаблон элемента **службы данных WCF** из категории **веб** .</span><span class="sxs-lookup"><span data-stu-id="ce2bc-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Шаблон элемента службы данных WCF в Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="ce2bc-136">Шаблон **службы данных WCF** доступен в visual Studio 2015, но не в visual Studio 2017 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="ce2bc-137">В качестве имени службы введите `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="ce2bc-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="ce2bc-138">В Visual Studio для новой службы создаются файлы разметки и кодов XML.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="ce2bc-139">По умолчанию открывается окно редактора кода.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="ce2bc-140">В **Обозреватель решений** служба имеет имя Northwind с расширением *SVC. CS* или *. svc. vb*.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="ce2bc-141">В коде службы данных замените комментарий `/* TODO: put your data source class name here */` в определении класса, задающего службу данных, типом контейнера сущностей модели данных, который в данном случае равен `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="ce2bc-142">Определение класса должно выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="ce2bc-143">Разрешение доступа к ресурсам службы данных</span><span class="sxs-lookup"><span data-stu-id="ce2bc-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="ce2bc-144">В коде службы данных замените код местозаполнителя в функции `InitializeService` следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="ce2bc-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="ce2bc-145">Это обеспечивает авторизованным клиентам доступ для чтения и записи к ресурсам указанных наборов сущностей.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce2bc-146">Любой клиент, имеющий доступ к приложению ASP.NET, имеет также доступ к ресурсам, предоставляемым службой данных.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="ce2bc-147">Для предотвращения несанкционированного доступа к ресурсам производственной службы данных необходимо также установить защиту самого приложения.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="ce2bc-148">Дополнительные сведения см. в разделе [Securing WCF Data Services](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ce2bc-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce2bc-149">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="ce2bc-149">Next steps</span></span>

<span data-ttu-id="ce2bc-150">Вы успешно создали новую службу данных, которая предоставляет канал OData, основанный на образце базы данных Northwind, и вы включили доступ к каналу для клиентов, имеющих разрешения для веб-приложения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce2bc-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="ce2bc-151">Далее вы запустите службу данных из Visual Studio и получите доступ к каналу OData, отправив запросы HTTP GET через веб-браузер:</span><span class="sxs-lookup"><span data-stu-id="ce2bc-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce2bc-152">Доступ к службе из веб-браузера</span><span class="sxs-lookup"><span data-stu-id="ce2bc-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="ce2bc-153">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ce2bc-153">See also</span></span>

- <span data-ttu-id="ce2bc-154">[Средства EDM ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce2bc-154">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
