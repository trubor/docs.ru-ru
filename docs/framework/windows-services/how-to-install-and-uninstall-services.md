---
title: Практическое руководство. Установка и удаление служб Windows
description: Узнайте, как устанавливать и удалять службы Windows. Если вы разрабатываете службу Windows с помощью .NET, можно использовать программу InstallUtil.exe или PowerShell.
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
ms.openlocfilehash: 0803d9908a9b92df0d17537ee4db2d798a2a07cc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433425"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="c6ee5-104">Практическое руководство. Установка и удаление служб Windows</span><span class="sxs-lookup"><span data-stu-id="c6ee5-104">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="c6ee5-105">Если вы разрабатываете службу Windows с помощью .NET Framework, вы можете быстро установить приложение службы с помощью служебной программы командной строки [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) или [PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="c6ee5-105">If you're developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="c6ee5-106">Если вы являетесь разработчиком и хотите создать службу Windows, которую пользователи могут устанавливать и удалять, можно использовать [набор инструментов WiX](https://wixtoolset.org/) или коммерческие средства, такие как [Advanced Installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html) или другие.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-106">Developers who want to release a Windows service that users can install and uninstall can use the free [WiX Toolset](https://wixtoolset.org/) or commercial tools like [Advanced Installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html), or others.</span></span> <span data-ttu-id="c6ee5-107">См. сведения о [создании пакета установщика (классическое приложение Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="c6ee5-107">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="c6ee5-108">Если вы хотите удалить службу на своем компьютере, не выполняйте процедуру, описанную в этой статье.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-108">If you want to uninstall a service from your computer, don't follow the steps in this article.</span></span> <span data-ttu-id="c6ee5-109">Вместо этого определите, какая программа (или программный пакет) установила эту службу, а затем выберите **Приложения** в параметрах, чтобы удалить эту программу.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-109">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="c6ee5-110">Следует отметить, что многие службы являются составной частью ОС Windows. Если их удалить, это может привести к нестабильной работе системы.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-110">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="c6ee5-111">Чтобы использовать процедуру, описанную в этой статье, сначала необходимо добавить установщик службы в свою службу Windows.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-111">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="c6ee5-112">Дополнительные сведения см. в разделе [Пошаговое руководство: создание диспетчера служб Windows](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="c6ee5-112">For more information, see [Walkthrough: Creating a Windows service app](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="c6ee5-113">Проекты служб Windows нельзя запускать непосредственно из среды разработки Visual Studio путем нажатия клавиши F5.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-113">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="c6ee5-114">Перед запуском проекта необходимо установить службу в проекте.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-114">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="c6ee5-115">Запустите **обозреватель сервера** и убедитесь, что служба установлена или удалена.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-115">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span>

## <a name="install-using-installutilexe-utility"></a><span data-ttu-id="c6ee5-116">Установка с помощью программы InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="c6ee5-116">Install using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="c6ee5-117">В меню **Пуск** выберите каталог **Visual Studio \<*version*>** и затем **Командная строка разработчика для VS \<*version*>** .</span><span class="sxs-lookup"><span data-stu-id="c6ee5-117">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="c6ee5-118">Появится командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-118">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="c6ee5-119">Откройте каталог, где находится скомпилированный исполняемый файл вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-119">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="c6ee5-120">Запустите *InstallUtil.exe* из командной строки, указав исполняемый файл проекта в качестве параметра:</span><span class="sxs-lookup"><span data-stu-id="c6ee5-120">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="c6ee5-121">Если вы используете командную строку разработчика для Visual Studio, системный путь должен указывать на файл *InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-121">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="c6ee5-122">Если это не так, можно добавить его в путь или использовать полный путь для его вызова.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-122">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="c6ee5-123">Этот инструмент устанавливается вместе с платформой .NET Framework в папку *%WINDIR%\Microsoft.NET\Framework[64]\\<версия_платформы\>* .</span><span class="sxs-lookup"><span data-stu-id="c6ee5-123">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="c6ee5-124">Пример:</span><span class="sxs-lookup"><span data-stu-id="c6ee5-124">For example:</span></span>
     - <span data-ttu-id="c6ee5-125">Для 32-разрядной версии .NET Framework 4 или 4.5 и более поздних версий: если каталог установки Windows — *C:\Windows*, по умолчанию используется путь *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-125">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="c6ee5-126">Для 64-разрядной версии .NET Framework 4 или 4.5 и более поздних версий: по умолчанию используется путь *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-126">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

## <a name="uninstall-using-installutilexe-utility"></a><span data-ttu-id="c6ee5-127">Удаление с помощью служебной программы InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="c6ee5-127">Uninstall using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="c6ee5-128">В меню **Пуск** выберите каталог **Visual Studio \<*version*>** и затем **Командная строка разработчика для VS \<*version*>** .</span><span class="sxs-lookup"><span data-stu-id="c6ee5-128">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="c6ee5-129">Появится командная строка разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-129">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="c6ee5-130">Запустите *InstallUtil.exe* из командной строки, указав выходные данные проекта в качестве параметра:</span><span class="sxs-lookup"><span data-stu-id="c6ee5-130">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="c6ee5-131">После удаления исполняемого файла для службы сама служба может по-прежнему присутствовать в реестре.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-131">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="c6ee5-132">В этом случае удалить запись службы из реестра можно с помощью команды [sc delete](/windows-server/administration/windows-commands/sc-delete).</span><span class="sxs-lookup"><span data-stu-id="c6ee5-132">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

## <a name="install-using-powershell"></a><span data-ttu-id="c6ee5-133">Установка с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6ee5-133">Install using PowerShell</span></span>

1. <span data-ttu-id="c6ee5-134">В меню **Пуск** выберите **Каталог Windows PowerShell** и **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-134">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="c6ee5-135">Откройте каталог, где находится скомпилированный исполняемый файл вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-135">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="c6ee5-136">Выполните командлет [**New-Service**](/powershell/module/microsoft.powershell.management/new-service), указав в качестве параметров выходные данные проекта и имя службы.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-136">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

## <a name="uninstall-using-powershell"></a><span data-ttu-id="c6ee5-137">Удаление с помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6ee5-137">Uninstall using PowerShell</span></span>

1. <span data-ttu-id="c6ee5-138">В меню **Пуск** выберите **Каталог Windows PowerShell** и **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-138">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="c6ee5-139">Выполните командлет [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service), указав в качестве параметра имя службы.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-139">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="c6ee5-140">После удаления исполняемого файла для службы сама служба может по-прежнему присутствовать в реестре.</span><span class="sxs-lookup"><span data-stu-id="c6ee5-140">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="c6ee5-141">В этом случае удалить запись службы из реестра можно с помощью команды [sc delete](/windows-server/administration/windows-commands/sc-delete).</span><span class="sxs-lookup"><span data-stu-id="c6ee5-141">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="c6ee5-142">См. также</span><span class="sxs-lookup"><span data-stu-id="c6ee5-142">See also</span></span>

- [<span data-ttu-id="c6ee5-143">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="c6ee5-143">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="c6ee5-144">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="c6ee5-144">How to: Create Windows services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="c6ee5-145">Практическое руководство. Добавление установщиков в приложение-службу</span><span class="sxs-lookup"><span data-stu-id="c6ee5-145">How to: Add installers to your service application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="c6ee5-146">Installutil.exe (установщик)</span><span class="sxs-lookup"><span data-stu-id="c6ee5-146">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
