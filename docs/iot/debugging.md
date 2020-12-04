---
title: Отладка приложений .NET на Raspberry Pi
description: Узнайте, как выполнять отладку приложений .NET на Raspberry Pi и аналогичных устройствах.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 7b9872304ee53071452772e3da02081a7def4d80
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594017"
---
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="1b775-103">Отладка приложений .NET на Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1b775-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="1b775-104">Отладка приложений .NET, работающих на устройствах IoT под управлением ARM, таких как Raspberry Pi, представляет собой уникальную задачу.</span><span class="sxs-lookup"><span data-stu-id="1b775-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="1b775-105">Приложения .NET можно разрабатывать на устройствах ARM.</span><span class="sxs-lookup"><span data-stu-id="1b775-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="1b775-106">Однако OmniSharp, необходимый для отладки приложений .NET вне Visual Studio, несовместим с устройствами ARM.</span><span class="sxs-lookup"><span data-stu-id="1b775-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="1b775-107">В результате приложения должны быть отлажены удаленно с совместимой платформы.</span><span class="sxs-lookup"><span data-stu-id="1b775-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="1b775-108">Отладка из Visual Studio Code (кросс-платформенные)</span><span class="sxs-lookup"><span data-stu-id="1b775-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="1b775-109">Для отладки .NET на платформе Raspberry Pi с Visual Studio Code требуется выполнить действия по настройке Raspberry Pi и файла проекта в *launch.js* .</span><span class="sxs-lookup"><span data-stu-id="1b775-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="1b775-110">Включение SSH в Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1b775-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="1b775-111">Для удаленной отладки требуется SSH.</span><span class="sxs-lookup"><span data-stu-id="1b775-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="1b775-112">Сведения о включении SSH см. в [разделе *Включение SSH* в документации по Raspberry Pi](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="1b775-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="1b775-113">Установка Удаленный отладчик Visual Studio на устройстве Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1b775-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="1b775-114">В консоли Bash в Raspberry Pi (локально или через SSH) выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1b775-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="1b775-115">Чтобы скачать и установить Удаленный отладчик Visual Studio на устройстве PI Raspberry, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1b775-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="1b775-116">Отладчику требуется запуск от имени `root` .</span><span class="sxs-lookup"><span data-stu-id="1b775-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="1b775-117">По умолчанию `root` не имеет пароля в Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="1b775-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="1b775-118">Задайте пароль для `root` , выполнив следующую команду и следуя инструкциям на экране.</span><span class="sxs-lookup"><span data-stu-id="1b775-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="1b775-119">Visual Studio Code использует протокол SSH для удаленной отладки.</span><span class="sxs-lookup"><span data-stu-id="1b775-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="1b775-120">В целях безопасности `root` не разрешается входить по протоколу SSH по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1b775-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="1b775-121">Чтобы включить `root` Вход через SSH, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1b775-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="1b775-122">Выполните следующую команду, чтобы открыть *каталог/etc/ssh/sshd_config* в [Nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="1b775-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="1b775-123">Нажмите клавиши <kbd>CTRL + W</kbd> и выполните поиск по запросу **пермитрутлогин**.</span><span class="sxs-lookup"><span data-stu-id="1b775-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="1b775-124">При необходимости раскомментируйте строку с помощью **пермитрутлогин** .</span><span class="sxs-lookup"><span data-stu-id="1b775-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="1b775-125">Измените строку для чтения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1b775-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="1b775-126">Если в *sshd_config каталог/etc/SSH/* нет строки **пермитрутлогин** , добавьте новую строку со значением, показанным выше.</span><span class="sxs-lookup"><span data-stu-id="1b775-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="1b775-127">Нажмите клавиши <kbd>CTRL + X</kbd> , чтобы выйти и сохранить шанс.</span><span class="sxs-lookup"><span data-stu-id="1b775-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="1b775-128">При появлении запроса **сохранить измененный буфер?** нажмите клавишу <kbd>Y</kbd> для подтверждения.</span><span class="sxs-lookup"><span data-stu-id="1b775-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="1b775-129">Нажмите клавишу <kbd>Ввод</kbd> , чтобы подтвердить перезапись исходного файла.</span><span class="sxs-lookup"><span data-stu-id="1b775-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="1b775-130">Перезагрузите Raspberry Pi, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1b775-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="1b775-131">launch.jsустановки в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b775-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="1b775-132">Добавьте конфигурацию запуска в *launch.js* проекта.</span><span class="sxs-lookup"><span data-stu-id="1b775-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="1b775-133">Если в проекте нет *launch.js* файла, добавьте его, перейдя на вкладку **выполнить** , выбрав **создать launch.jsв файле** и выбрав **.NET** или **.NET Core** в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="1b775-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="1b775-134">Новая конфигурация в *launch.jsв* должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1b775-134">The new configuration in *launch.json* should look similar to this:</span></span>

```json
"configurations": [
    {
        "name": ".NET Core Launch (remote console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "/home/pi/.dotnet/dotnet",
        "args": ["/home/pi/sample/Sample.dll"],
        "cwd": "/home/pi/sample",
        "stopAtEntry": false,
        "console": "internalConsole",
        "pipeTransport": {
            "pipeCwd": "${workspaceFolder}",
            "pipeProgram": "C:\\Program Files\\PuTTY\\PLINK.EXE",
            "pipeArgs": [
                "-pw",
                "P@ssw0rd",
                "root@raspberrypi"
            ],
            "debuggerPath": "/home/pi/vsdbg/vsdbg"
        }
    },
```

<span data-ttu-id="1b775-135">Обратите внимание на следующее.</span><span class="sxs-lookup"><span data-stu-id="1b775-135">Notice the following:</span></span>

- <span data-ttu-id="1b775-136">`program` — Это путь к среде выполнения .NET на устройстве PI.</span><span class="sxs-lookup"><span data-stu-id="1b775-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="1b775-137">`args` путь к сборке для отладки на устройстве PI.</span><span class="sxs-lookup"><span data-stu-id="1b775-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="1b775-138">`cwd` Рабочий каталог, используемый при запуске приложения на устройстве PI.</span><span class="sxs-lookup"><span data-stu-id="1b775-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="1b775-139">`pipeProgram` — Это путь к SSH-клиенту на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="1b775-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="1b775-140">`pipeArgs` параметры, передаваемые клиенту SSH.</span><span class="sxs-lookup"><span data-stu-id="1b775-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="1b775-141">Обязательно укажите параметр Password, а также `root` пользователя в формате `<user>@<hostname>` .</span><span class="sxs-lookup"><span data-stu-id="1b775-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b775-142">В приведенном выше примере используется *Плинк*, компонент клиента [PuTTY](https://www.ssh.com/ssh/putty/) вышеуказанного <span class="docon docon-navigate-external x-hidden-focus"></span> SSH.</span><span class="sxs-lookup"><span data-stu-id="1b775-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="1b775-143">[OpenSSH](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> Вместо этого можно использовать OpenSSH, который входит в последние версии Windows и Linux.</span><span class="sxs-lookup"><span data-stu-id="1b775-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="1b775-144">Однако OpenSSH не поддерживает отправку паролей в качестве параметра командной строки.</span><span class="sxs-lookup"><span data-stu-id="1b775-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="1b775-145">Чтобы использовать OpenSSH, [Настройте Raspberry Pi для доступа SSH, не имеющего пароля](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="1b775-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="1b775-146">Развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="1b775-146">Deploy the app</span></span>

<span data-ttu-id="1b775-147">Разверните приложение, как описано в разделе [развертывание приложений .NET для Raspberry Pi](deployment.md).</span><span class="sxs-lookup"><span data-stu-id="1b775-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="1b775-148">Убедитесь, что путь развертывания совпадает с путем, указанным в `cwd` параметре в *launch.js* конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b775-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="1b775-149">Запуск отладчика</span><span class="sxs-lookup"><span data-stu-id="1b775-149">Launch the debugger</span></span>

<span data-ttu-id="1b775-150">На вкладке **выполнить** выберите конфигурацию **запуска .NET Core (удаленная консоль)** и щелкните **начать отладку**.</span><span class="sxs-lookup"><span data-stu-id="1b775-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="1b775-151">Приложение запускается на устройстве Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="1b775-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="1b775-152">Отладчик можно использовать для установки точек останова, проверки локальных переменных и многого другого.</span><span class="sxs-lookup"><span data-stu-id="1b775-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="1b775-153">Ссылки</span><span class="sxs-lookup"><span data-stu-id="1b775-153">References</span></span>

<span data-ttu-id="1b775-154">[Удаленная отладка с VS Code в Windows до Raspberry Pi с помощью .NET Core на ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="1b775-154">[Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="1b775-155">Отладка из Visual Studio в Windows</span><span class="sxs-lookup"><span data-stu-id="1b775-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="1b775-156">Visual Studio может выполнять отладку приложений .NET на удаленных устройствах через SSH.</span><span class="sxs-lookup"><span data-stu-id="1b775-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="1b775-157">На устройстве не требуется специальной настройки.</span><span class="sxs-lookup"><span data-stu-id="1b775-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="1b775-158">Дополнительные сведения об использовании Visual Studio для удаленной отладки .NET см. в статье [Удаленная отладка .NET в Linux с помощью SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="1b775-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
