---
title: Практическое руководство. Создание служб Windows
description: Используйте шаблон проекта "Служба Windows" для создания службы. Задайте свойство ServiceName, создайте установщики и переопределите методы OnStart и OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
ms.openlocfilehash: 9b171fa54cf65a482625c276c26185b12075c753
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270710"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="ad2a6-104">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="ad2a6-104">How to: Create Windows Services</span></span>

<span data-ttu-id="ad2a6-105">При создании службы можно использовать шаблон проекта Visual Studio, который называется **Служба Windows**.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="ad2a6-106">Этот шаблон автоматически выполняет основную часть работы, ссылаясь на необходимые классы и пространства имен, устанавливая наследование от базового класса для служб и переопределяя некоторые методы, которые вы обычно хотите переопределять.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ad2a6-107">Шаблон проекта "Службы Windows" в экспресс-выпуске Visual Studio отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="ad2a6-108">Для создания функциональной службы необходимо выполнить, как минимум, следующее:</span><span class="sxs-lookup"><span data-stu-id="ad2a6-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="ad2a6-109">Задайте свойство <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="ad2a6-110">Создайте установщики, необходимые для приложения службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="ad2a6-111">Переопределите и задайте код для методов <xref:System.ServiceProcess.ServiceBase.OnStart%2A> и <xref:System.ServiceProcess.ServiceBase.OnStop%2A> для настройки режимов поведения службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="ad2a6-112">Создание приложения службы Windows</span><span class="sxs-lookup"><span data-stu-id="ad2a6-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="ad2a6-113">Создайте проект **Служба Windows**.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ad2a6-114">Инструкции по созданию службы без использования шаблона см. в разделе [Практический пример. Создание служб программным способом](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="ad2a6-115">В окне **Свойства** задайте для своей службы свойство <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="ad2a6-116">![Задание свойства ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="ad2a6-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ad2a6-117">Значение <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> свойства всегда должно соответствовать имени, указанному в классах установщика.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="ad2a6-118">При изменении этого свойства необходимо также обновить свойство <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> классов установщика.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="ad2a6-119">Установите любые из следующих свойств для определения режима работы службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="ad2a6-120">Свойство.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-120">Property</span></span>|<span data-ttu-id="ad2a6-121">Параметр</span><span class="sxs-lookup"><span data-stu-id="ad2a6-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="ad2a6-122">`True`, чтобы указать, что служба может принимать запросы на останов работы; `false` для предотвращения останова службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="ad2a6-123">`True`, чтобы указать, что служба хочет принимать уведомления о выключении компьютера, на котором она работает, позволяя ему вызывать процедуру <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="ad2a6-124">`True`, чтобы указать, что служба может принимать запросы на приостановку или возобновление выполнения; `false` для предотвращения приостановки и возобновления работы службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="ad2a6-125">`True`, чтобы указать, что служба может обрабатывать уведомления об изменениях состояния питания компьютера; `false`, чтобы не сообщать службе об этих изменениях.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="ad2a6-126">`True` для внесения информационных записей в журнал событий приложения, когда служба выполняет некоторое действие; `false` для отключения этой функции.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="ad2a6-127">Дополнительные сведения см. в разделе [Практическое руководство. Запись сведений о службах в журнал](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="ad2a6-128">**Примечание.**  По умолчанию свойство <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="ad2a6-129">Когда <xref:System.ServiceProcess.ServiceBase.CanStop%2A> или <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> имеют значение `false`, **диспетчер служб** будет отключать пункты меню, отвечающие за остановку, приостановку или возобновление работы службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="ad2a6-130">Откройте редактор кода и введите данные для выполнения операций для процедур <xref:System.ServiceProcess.ServiceBase.OnStart%2A> и <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="ad2a6-131">Переопределите все прочие методы, для которых необходимо определить функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="ad2a6-132">Добавить установщики, необходимые для приложения службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="ad2a6-133">Дополнительные сведения см. в разделе [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="ad2a6-134">Скомпилируйте проект, выбрав в меню **Сборка** пункт **Собрать решение**.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ad2a6-135">Не нажимайте клавишу F5 для запуска проекта — таким способом нельзя запустить проект службы.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="ad2a6-136">Установите службу.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-136">Install the service.</span></span> <span data-ttu-id="ad2a6-137">Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2a6-138">См. также</span><span class="sxs-lookup"><span data-stu-id="ad2a6-138">See also</span></span>

- [<span data-ttu-id="ad2a6-139">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="ad2a6-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ad2a6-140">Практическое руководство. Создание служб программным способом</span><span class="sxs-lookup"><span data-stu-id="ad2a6-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="ad2a6-141">Практическое руководство. Добавление установщиков в приложение-службу</span><span class="sxs-lookup"><span data-stu-id="ad2a6-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="ad2a6-142">Практическое руководство. Запись сведений о службах в журнал</span><span class="sxs-lookup"><span data-stu-id="ad2a6-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="ad2a6-143">Практическое руководство. Запуск служб</span><span class="sxs-lookup"><span data-stu-id="ad2a6-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="ad2a6-144">Практическое руководство. Назначение службам контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="ad2a6-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="ad2a6-145">Практическое руководство. Установка и удаление служб</span><span class="sxs-lookup"><span data-stu-id="ad2a6-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="ad2a6-146">Пошаговое руководство: Создание приложения служб Windows в конструкторе компонентов</span><span class="sxs-lookup"><span data-stu-id="ad2a6-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
