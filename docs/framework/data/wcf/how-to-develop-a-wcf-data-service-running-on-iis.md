---
description: Дополнительные сведения см. в статье как разработать службу данных WCF, работающую на IIS.
title: Практическое руководство. Разработка службы данных WCF Data Service, работающей на IIS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: b4d7b322a00e3c9c43005a416c608e1b98f1ce51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765481"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="177df-103">Руководство. Разработка службы данных WCF, работающей на сервере IIS</span><span class="sxs-lookup"><span data-stu-id="177df-103">How to: Develop a WCF data service running on IIS</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="177df-104">В этой статье показано, как использовать службы данных WCF для создания службы данных на основе образца базы данных Northwind, размещенного в веб-приложении ASP.NET, работающем на службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="177df-104">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="177df-105">Пример создания одной и той же службы данных Northwind как веб-приложения ASP.NET, выполняемого на ASP.NET Development Server, см. в [кратком руководстве по службы данных WCF](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="177df-105">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="177df-106">Чтобы создать службу данных Northwind, сначала установите образец базы данных Northwind на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="177df-106">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="177df-107">Чтобы установить базу данных, выполните скрипт Transact-SQL из [баз данных Northwind и Pubs для Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="177df-107">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="177df-108">В этой статье показано, как создать службу данных с помощью поставщика Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="177df-108">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="177df-109">Доступны другие поставщики служб данных.</span><span class="sxs-lookup"><span data-stu-id="177df-109">Other data services providers are available.</span></span> <span data-ttu-id="177df-110">Дополнительные сведения см. в разделе [поставщики служб данных](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="177df-110">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="177df-111">После создания службы требуется явно предоставить доступ к ресурсам службы данных.</span><span class="sxs-lookup"><span data-stu-id="177df-111">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="177df-112">Дополнительные сведения см. [в разделе инструкции. Включение доступа к службе данных](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="177df-112">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="177df-113">Создание веб-приложения ASP.NET, которое выполняется в службах IIS</span><span class="sxs-lookup"><span data-stu-id="177df-113">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="177df-114">В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.</span><span class="sxs-lookup"><span data-stu-id="177df-114">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="177df-115">В диалоговом окне **Новый проект** выберите **установленный** > [**Visual C#** или **Visual Basic**] > **веб-** категорию.</span><span class="sxs-lookup"><span data-stu-id="177df-115">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="177df-116">Выберите шаблон **Веб-приложение ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="177df-116">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="177df-117">Введите в `NorthwindService` качестве имени проекта.</span><span class="sxs-lookup"><span data-stu-id="177df-117">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="177df-118">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="177df-118">Click **OK**.</span></span>

6. <span data-ttu-id="177df-119">В меню **проект** выберите **Свойства норсвиндсервице**.</span><span class="sxs-lookup"><span data-stu-id="177df-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="177df-120">Перейдите на вкладку **веб** , а затем выберите **использовать локальный веб-сервер IIS**.</span><span class="sxs-lookup"><span data-stu-id="177df-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="177df-121">Щелкните **создать виртуальный каталог** , а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="177df-121">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="177df-122">С помощью командной строки с правами администратора выполните одну из следующих команд (в зависимости от операционной системы).</span><span class="sxs-lookup"><span data-stu-id="177df-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="177df-123">32-разрядные системы:</span><span class="sxs-lookup"><span data-stu-id="177df-123">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="177df-124">64-разрядные системы:</span><span class="sxs-lookup"><span data-stu-id="177df-124">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="177df-125">Она регистрирует Windows Communication Foundation (WCF) на компьютере.</span><span class="sxs-lookup"><span data-stu-id="177df-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="177df-126">С помощью командной строки с правами администратора выполните одну из следующих команд (в зависимости от операционной системы).</span><span class="sxs-lookup"><span data-stu-id="177df-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="177df-127">32-разрядные системы:</span><span class="sxs-lookup"><span data-stu-id="177df-127">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="177df-128">64-разрядные системы:</span><span class="sxs-lookup"><span data-stu-id="177df-128">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="177df-129">Это необходимо для того, чтобы проверить правильность работы служб IIS после установки WCF на компьютере.</span><span class="sxs-lookup"><span data-stu-id="177df-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="177df-130">Возможно, потребуется перезапустить службы IIS.</span><span class="sxs-lookup"><span data-stu-id="177df-130">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="177df-131">Если приложение ASP.NET запущено в службах IIS7, нужно также выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="177df-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="177df-132">Откройте диспетчер IIS и перейдите к приложению службы приложений на **веб-сайте по умолчанию**.</span><span class="sxs-lookup"><span data-stu-id="177df-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="177df-133">В окне **Просмотр возможностей** дважды щелкните элемент **Проверка подлинности**.</span><span class="sxs-lookup"><span data-stu-id="177df-133">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="177df-134">На странице **Проверка подлинности** выберите **Анонимная проверка подлинности**.</span><span class="sxs-lookup"><span data-stu-id="177df-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="177df-135">На панели **действия** нажмите кнопку **изменить** , чтобы задать субъект безопасности, в котором анонимные пользователи будут подключаться к сайту.</span><span class="sxs-lookup"><span data-stu-id="177df-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="177df-136">В диалоговом окне **изменение учетных данных анонимной проверки подлинности** выберите **удостоверение пула приложений**.</span><span class="sxs-lookup"><span data-stu-id="177df-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="177df-137">При использовании учетной записи сетевой службы анонимным пользователям предоставляется доступ к внутренней сети, связанной с этой учетной записью.</span><span class="sxs-lookup"><span data-stu-id="177df-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="177df-138">С помощью среды SQL Server Management Studio, программы sqlcmd.exe или редактора Transact-SQL в Visual Studio выполните следующую команду Transact-SQL для экземпляра SQL Server с прикрепленной базой данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="177df-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="177df-139">Она создает имя входа в экземпляр SQL Server для учетной записи Windows, используемой для запуска служб IIS.</span><span class="sxs-lookup"><span data-stu-id="177df-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="177df-140">Это позволит службам IIS подключиться к экземпляру SQL Server.</span><span class="sxs-lookup"><span data-stu-id="177df-140">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="177df-141">После присоединения базы данных Northwind выполните следующие команды Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="177df-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    <span data-ttu-id="177df-142">Они предоставляют право на новое имя входа, позволяющее службам IIS читать данные из базы данных Northwind и записывать данные в эту базу данных.</span><span class="sxs-lookup"><span data-stu-id="177df-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="177df-143">Определение модели данных</span><span class="sxs-lookup"><span data-stu-id="177df-143">Define the data model</span></span>

1. <span data-ttu-id="177df-144">В **Обозреватель решений** щелкните правой кнопкой мыши имя проекта ASP.NET и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="177df-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="177df-145">В диалоговом окне **Добавление нового элемента** выберите **ADO.NET EDM**.</span><span class="sxs-lookup"><span data-stu-id="177df-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="177df-146">В качестве имени модели данных введите `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="177df-146">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="177df-147">В мастере EDM выберите **создать из базы данных**, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="177df-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="177df-148">Подключите модель данных к базе данных, выполнив одно из следующих действий, а затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="177df-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="177df-149">Если подключение к базе данных уже не настроено, щелкните **создать соединение** и создайте новое соединение.</span><span class="sxs-lookup"><span data-stu-id="177df-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="177df-150">Дополнительные сведения см. в разделе [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="177df-150">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="177df-151">Этот экземпляр SQL Server должен содержать присоединенный образец базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="177df-151">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="177df-152">\- или -</span><span class="sxs-lookup"><span data-stu-id="177df-152">\- or -</span></span>

    - <span data-ttu-id="177df-153">Если имеется уже настроенное подключение к базе данных Northwind, выберите это подключение из списка.</span><span class="sxs-lookup"><span data-stu-id="177df-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="177df-154">На завершающей странице мастера установите флажки для всех таблиц базы данных и снимите флажки для представлений и хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="177df-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="177df-155">Нажмите кнопку **Готово** , чтобы закрыть мастер.</span><span class="sxs-lookup"><span data-stu-id="177df-155">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="177df-156">Создание службы данных</span><span class="sxs-lookup"><span data-stu-id="177df-156">Create the data service</span></span>

1. <span data-ttu-id="177df-157">В **Обозреватель решений** щелкните правой кнопкой мыши имя проекта ASP.NET и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="177df-157">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="177df-158">В диалоговом окне **Добавление нового элемента** выберите **WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="177df-158">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Шаблон элемента службы данных WCF в Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="177df-160">Шаблон **службы данных WCF** доступен в visual Studio 2015, но не в visual Studio 2017 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="177df-160">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="177df-161">В качестве имени службы введите `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="177df-161">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="177df-162">В Visual Studio для новой службы создаются файлы разметки и кодов XML.</span><span class="sxs-lookup"><span data-stu-id="177df-162">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="177df-163">По умолчанию открывается окно редактора кода.</span><span class="sxs-lookup"><span data-stu-id="177df-163">By default, the code-editor window opens.</span></span> <span data-ttu-id="177df-164">В **Обозреватель решений** служба имеет имя, Northwind и расширение. svc.cs или. svc. vb.</span><span class="sxs-lookup"><span data-stu-id="177df-164">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="177df-165">В коде службы данных замените комментарий `/* TODO: put your data source class name here */` в определении класса, задающего службу данных, типом контейнера сущностей модели данных, который в данном случае равен `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="177df-165">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="177df-166">Определение класса должно выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="177df-166">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="177df-167">См. также</span><span class="sxs-lookup"><span data-stu-id="177df-167">See also</span></span>

- [<span data-ttu-id="177df-168">Предоставление данных как службы</span><span class="sxs-lookup"><span data-stu-id="177df-168">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
