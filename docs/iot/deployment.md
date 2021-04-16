---
title: Развертывание приложений .NET в Raspberry Pi
description: Узнайте, как развертывать приложения .NET на Raspberry Pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594128"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a>Развертывание приложений .NET в Raspberry Pi

Развертывание приложений .NET в Raspberry Pi идентично развертыванию на любой другой платформе. Приложение может использовать *автономный* или *зависимый от платформы* режим развертывания. У каждой стратегии есть свои преимущества. Дополнительные сведения см. в статье [Обзор публикации приложений .NET](../core/deploying/index.md).

## <a name="deploying-a-framework-dependent-app"></a>Развертывание приложения, зависящего от платформы

Чтобы развернуть приложение как приложение, зависящее от платформы, выполните следующие действия.

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. Установите .NET на Raspberry Pi с помощью [скриптов dotnet-install](../core/tools/dotnet-install-script.md). В командной строке Bash в Raspberry Pi (локальной или SSH) выполните следующие действия.
    1. Выполните следующую команду, чтобы установить .NET:

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > При этом устанавливается последняя версия. Если требуется определенная версия, добавьте `--version <VERSION>` в конец, где `<VERSION>` — это конкретная версия сборки.

    1. Чтобы упростить разрешение пути, добавьте переменную среды `DOTNET_ROOT` и добавьте каталог *.dotnet* к `$PATH` с помощью следующих команд:

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. Проверьте установку .NET, выполнив следующую команду:

        ```dotnetcli
        dotnet --version
        ```

        Убедитесь, что отображаемая версия соответствует установленной версии.

1. Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.
    - [Разверните приложение в локальную папку](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019), если используется **Visual Studio**. Перед публикацией выберите **Изменить** в сводке профиля публикации и перейдите на вкладку **Параметры**. Убедитесь, что для **Режима развертывания** задано значение *Зависимый от платформы*, а **Целевая среда выполнения** — *Портативные*.
    - При использовании **интерфейса командной строки .NET** используйте команду [dotnet publish](../core/tools/dotnet-publish.md). Дополнительных аргументов не требуется.

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Запустите приложение из командной строки Bash на Raspberry Pi (локальном или SSH). Для этого задайте папку развертывания в качестве текущего каталога и выполните следующую команду (где *HelloWorld.dll* является точкой входа приложения):

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>Развертывание автономного приложения

Чтобы развернуть приложение как автономное приложение, выполните следующие действия.

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.
    - [Разверните приложение в локальную папку](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019), если используется **Visual Studio**. Перед публикацией выберите **Изменить** в сводке профиля публикации и перейдите на вкладку **Параметры**. Убедитесь, что для **Режима развертывания** задано значение *Автономный*, а **Целевая среда выполнения** — *linux-arm*.
    - При использовании **интерфейса командной строки .NET** используйте команду [dotnet publish](../core/tools/dotnet-publish.md) с аргументом `-r linux-arm`:

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Запустите приложение из командной строки Bash на Raspberry Pi (локальном или SSH). Для этого задайте в качестве текущего каталога расположение развертывания и выполните следующие действия:
    1. Предоставьте исполняемому файлу разрешение *execute* (где `HelloWorld` — имя исполняемого файла).

        ```bash
        chmod +x HelloWorld
        ```

    1. Запустите исполняемый файл.

        ```bash
        ./HelloWorld
        ```
