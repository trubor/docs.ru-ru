---
title: Практическое руководство. Запуск служб
description: Ознакомьтесь с несколькими способами запуска служб. Установленную службу необходимо запустить. Процедура запуска вызывает метод OnStart в классе службы.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: bf1a4f676c3c7789036cc3650169e04892c2a191
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494549"
---
# <a name="how-to-start-services"></a><span data-ttu-id="211c5-105">Практическое руководство. Запуск служб</span><span class="sxs-lookup"><span data-stu-id="211c5-105">How to: Start Services</span></span>

<span data-ttu-id="211c5-106">Установленную службу необходимо запустить.</span><span class="sxs-lookup"><span data-stu-id="211c5-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="211c5-107">Процедура запуска вызывает метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A> в классе службы.</span><span class="sxs-lookup"><span data-stu-id="211c5-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="211c5-108">Как правило, метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A> определяет полезные действия, которые будет выполнять служба.</span><span class="sxs-lookup"><span data-stu-id="211c5-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="211c5-109">Запущенная служба остается активной, пока не будет приостановлена или остановлена вручную.</span><span class="sxs-lookup"><span data-stu-id="211c5-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="211c5-110">Службы можно настроить на запуск автоматически или вручную.</span><span class="sxs-lookup"><span data-stu-id="211c5-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="211c5-111">Служба, которая запускается автоматически, будет запущена при первом включении или перезагрузке компьютера, на котором она установлена.</span><span class="sxs-lookup"><span data-stu-id="211c5-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="211c5-112">Службу, которая запускается вручную, должен запустить пользователь.</span><span class="sxs-lookup"><span data-stu-id="211c5-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="211c5-113">По умолчанию службы, созданные с помощью Visual Studio, настроены на запуск вручную.</span><span class="sxs-lookup"><span data-stu-id="211c5-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="211c5-114">Есть несколько способов запуска службы вручную: из **диспетчера служб** или **обозревателя сервера** либо из кода, используя компонент, который называется <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="211c5-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="211c5-115">Вы можете задать свойство <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> в классе <xref:System.ServiceProcess.ServiceInstaller>, чтобы определить способ запуска службы — вручную или автоматически.</span><span class="sxs-lookup"><span data-stu-id="211c5-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

## <a name="specify-how-a-service-should-start"></a><span data-ttu-id="211c5-116">Указание способа запуска службы</span><span class="sxs-lookup"><span data-stu-id="211c5-116">Specify how a service should start</span></span>

1. <span data-ttu-id="211c5-117">Создав службу, добавьте для нее необходимые установщики.</span><span class="sxs-lookup"><span data-stu-id="211c5-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="211c5-118">Дополнительные сведения см. в разделе [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="211c5-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="211c5-119">В конструкторе щелкните установщик процессов службы, с которой вы работаете.</span><span class="sxs-lookup"><span data-stu-id="211c5-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="211c5-120">В **окне свойств** задайте свойству <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="211c5-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="211c5-121">Чтобы установить службу</span><span class="sxs-lookup"><span data-stu-id="211c5-121">To have your service install</span></span>|<span data-ttu-id="211c5-122">Задайте это значение</span><span class="sxs-lookup"><span data-stu-id="211c5-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="211c5-123">При перезапуске компьютера</span><span class="sxs-lookup"><span data-stu-id="211c5-123">When the computer is restarted</span></span>|<span data-ttu-id="211c5-124">**Автоматический**</span><span class="sxs-lookup"><span data-stu-id="211c5-124">**Automatic**</span></span>|
    |<span data-ttu-id="211c5-125">При запуске службы с помощью явного действия пользователя</span><span class="sxs-lookup"><span data-stu-id="211c5-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="211c5-126">**Manual** (Вручную)</span><span class="sxs-lookup"><span data-stu-id="211c5-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="211c5-127">Чтобы полностью запретить запуск службы, можно задать свойству <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> значение **Disabled** (Отключено).</span><span class="sxs-lookup"><span data-stu-id="211c5-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="211c5-128">Это можно сделать, если вы собираетесь перезагружать сервер несколько раз и хотите сэкономить время, запретив запуск служб, которые обычно запускаются одновременно.</span><span class="sxs-lookup"><span data-stu-id="211c5-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="211c5-129">Эти и другие свойства можно изменить после установки службы.</span><span class="sxs-lookup"><span data-stu-id="211c5-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="211c5-130">Есть несколько способов запуска службы, для процесса <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> которой настроено значение **Manual** (Вручную): из **диспетчера служб** или **обозревателя серверов** либо из кода.</span><span class="sxs-lookup"><span data-stu-id="211c5-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="211c5-131">Важно отметить, что в действительности не все эти методы приводят к запуску службы в контексте **диспетчера служб**. При использовании **обозревателя сервера** и программных способов применяется контроллер.</span><span class="sxs-lookup"><span data-stu-id="211c5-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

## <a name="start-a-service-from-server-explorer"></a><span data-ttu-id="211c5-132">Запуск службы из обозревателя сервера</span><span class="sxs-lookup"><span data-stu-id="211c5-132">Start a service from Server Explorer</span></span>

1. <span data-ttu-id="211c5-133">В **обозревателе сервера** добавьте нужный сервер, если его нет в списке.</span><span class="sxs-lookup"><span data-stu-id="211c5-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="211c5-134">Дополнительные сведения см. в разделах "Практическое руководство. Подключение и инициализация обозревателя серверов или обозревателя баз данных".</span><span class="sxs-lookup"><span data-stu-id="211c5-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="211c5-135">Разверните узел **Службы** и выберите службу, которую нужно запустить.</span><span class="sxs-lookup"><span data-stu-id="211c5-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="211c5-136">Щелкните имя службы правой кнопкой мыши и выберите **Запуск**.</span><span class="sxs-lookup"><span data-stu-id="211c5-136">Right-click the name of the service, and then select **Start**.</span></span>

### <a name="start-a-service-from-services"></a><span data-ttu-id="211c5-137">Запуск службы из приложения "Службы"</span><span class="sxs-lookup"><span data-stu-id="211c5-137">Start a service from Services</span></span>

1. <span data-ttu-id="211c5-138">Откройте приложение **Службы**.</span><span class="sxs-lookup"><span data-stu-id="211c5-138">Open the **Services** app.</span></span>

2. <span data-ttu-id="211c5-139">Выберите службу в списке, щелкните ее правой кнопкой мыши и выберите **Запуск**.</span><span class="sxs-lookup"><span data-stu-id="211c5-139">Select your service in the list, right-click it, and then select **Start**.</span></span>

## <a name="start-a-service-from-code"></a><span data-ttu-id="211c5-140">Запуск службы из кода</span><span class="sxs-lookup"><span data-stu-id="211c5-140">Start a service from code</span></span>

1. <span data-ttu-id="211c5-141">Создайте экземпляр класса <xref:System.ServiceProcess.ServiceController> и настройте его для взаимодействия со службой, которой нужно управлять.</span><span class="sxs-lookup"><span data-stu-id="211c5-141">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="211c5-142">Чтобы запустить службу, вызовите метод <xref:System.ServiceProcess.ServiceController.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="211c5-142">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="211c5-143">См. также</span><span class="sxs-lookup"><span data-stu-id="211c5-143">See also</span></span>

- [<span data-ttu-id="211c5-144">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="211c5-144">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="211c5-145">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="211c5-145">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="211c5-146">Практическое руководство. Добавление установщиков в приложение-службу</span><span class="sxs-lookup"><span data-stu-id="211c5-146">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
