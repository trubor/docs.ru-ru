---
title: Отладка приложений .NET на устройствах Raspberry Pi
description: Узнайте, как выполнять отладку приложений .NET на устройствах Raspberry Pi и аналогичных устройствах.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 58858384c49a296e0b33d663f3ef930caf9cace6
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102258069"
---
# <a name="debug-net-apps-on-raspberry-pi"></a>Отладка приложений .NET на устройствах Raspberry Pi

Отладка приложений .NET, работающих на устройствах Интернета вещей на основе ARM, таких как Raspberry Pi, является уникальной задачей. Приложения .NET можно разрабатывать на устройствах ARM. Однако решение OmniSharp, необходимое для отладки приложений .NET вне Visual Studio, несовместимо с устройствами ARM. Поэтому отладка приложений должна выполняться в удаленном режиме с совместимой платформы.

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>Отладка из Visual Studio Code (кроссплатформенная среда)

Для отладки приложения .NET на устройстве Raspberry Pi из Visual Studio Code требуется выполнить действия по настройке на устройстве Raspberry Pi и в файле *launch.js* проекта.

### <a name="enable-ssh-on-the-raspberry-pi"></a>Включение протокола SSH на устройстве Raspberry Pi

Для удаленной отладки требуется протокол SSH. Сведения о включении SSH см. в [статье о *включении SSH* в документации по Raspberry Pi](https://www.raspberrypi.org/documentation/remote-access/ssh/).

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>Установка Удаленного отладчика Visual Studio на устройстве Raspberry Pi

В консоли Bash на устройстве Raspberry Pi (локально или через SSH) выполните следующие действия.

1. Чтобы скачать и установить Удаленный отладчик Visual Studio на устройстве PI Raspberry, выполните следующую команду:

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. Отладчику требуется запуск с правами `root`. По умолчанию `root` не имеет пароля в Raspberry Pi. Задайте пароль для `root`, выполнив приведенную ниже команду и следуя инструкциям на экране.

    ```bash
    sudo passwd root
    ```

1. Для удаленной отладки в Visual Studio Code используется протокол SSH. В целях безопасности `root` запрещено выполнять вход по протоколу SSH по умолчанию. Чтобы разрешить для `root` вход через SSH, выполните следующие действия.

    1. Выполните приведенную ниже команду, чтобы открыть файл */etc/ssh/sshd_config* в [nano](https://www.nano-editor.org/docs.php).

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. Нажмите сочетание клавиш <kbd>CTRL+W</kbd> и выполните поиск по запросу **PermitRootLogin**.
    1. При необходимости раскомментируйте строку с **PermitRootLogin**.
    1. Измените строку так, чтобы она имела следующий вид:

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > Если в файле */etc/ssh/sshd_config* нет строки **PermitRootLogin**, добавьте новую строку со значением, показанным выше.

    1. Нажмите сочетание клавиш <kbd>CTRL+X</kbd>, чтобы выйти и сохранить изменения. При появлении запроса **Сохранить измененный буфер?** нажмите клавишу <kbd>Y</kbd> для подтверждения. Нажмите клавишу <kbd>ВВОД</kbd>, чтобы подтвердить перезапись исходного файла.
    1. Перезагрузите устройство Raspberry Pi, выполнив следующую команду:

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>Настройка файла launch.json в Visual Studio Code

Добавьте конфигурацию запуска в файл *launch.js* проекта. Если в проекте нет файла *launch.js*, добавьте его, перейдя на вкладку **Запуск**, щелкнув **Создать файл launch.js** и выбрав **.NET** или **.NET Core** в диалоговом окне.

Новая конфигурация в файле *launch.jsв* должна выглядеть следующим образом:

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

Обратите внимание на следующее.

- `program` — это путь к среде выполнения .NET на устройстве PI.
- `args` — это путь к отлаживаемой сборке на устройстве PI.
- `cwd` — это рабочий каталог, используемый при запуске приложения на устройстве PI.
- `pipeProgram` — это путь к SSH-клиенту на локальном компьютере.
- `pipeArgs` — это параметры, передаваемые SSH-клиенту. Обязательно укажите пароль, а также пользователя `root` в формате `<user>@<hostname>`.

> [!IMPORTANT]
> В приведенном выше примере используется *plink*, компонент SSH-клиента [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span>. Вместо него можно использовать [OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, входящий в последние версии Windows и Linux. Однако OpenSSH не поддерживает отправку паролей в качестве параметра командной строки. Чтобы использовать OpenSSH, [настройте устройство Raspberry Pi для беспарольного доступа через SSH](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).

### <a name="deploy-the-app"></a>Развертывание приложения

Разверните приложение, как описано в статье о [развертывании приложений .NET на устройстве Raspberry Pi](deployment.md). Убедитесь, что путь развертывания совпадает с путем, указанным в параметре `cwd` в конфигурации *launch.js*.

### <a name="launch-the-debugger"></a>Запуск отладчика

На вкладке **Запуск** выберите конфигурацию **Запуск .NET Core (удаленная консоль)** и щелкните **Начать отладку**. Приложение запускается на устройстве Raspberry Pi. Отладчик можно использовать для установки точек останова, проверки локальных переменных и многого другого.

## <a name="references"></a>Ссылки

[Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm) (Удаленная отладка из VS Code в Windows на устройстве Raspberry Pi с помощью .NET Core в ARM)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>Отладка из Visual Studio в Windows

Visual Studio может выполнять отладку приложений .NET на удаленных устройствах через SSH. Никаких дополнительных настроек на устройстве не требуется. Дополнительные сведения об использовании Visual Studio для удаленной отладки .NET см. в статье об [удаленной отладке .NET в Linux с помощью SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).

::: zone-end
