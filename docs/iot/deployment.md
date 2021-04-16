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
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="1b01d-103">Развертывание приложений .NET в Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1b01d-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="1b01d-104">Развертывание приложений .NET в Raspberry Pi идентично развертыванию на любой другой платформе.</span><span class="sxs-lookup"><span data-stu-id="1b01d-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="1b01d-105">Приложение может использовать *автономный* или *зависимый от платформы* режим развертывания.</span><span class="sxs-lookup"><span data-stu-id="1b01d-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="1b01d-106">У каждой стратегии есть свои преимущества.</span><span class="sxs-lookup"><span data-stu-id="1b01d-106">There are advantages to each strategy.</span></span> <span data-ttu-id="1b01d-107">Дополнительные сведения см. в статье [Обзор публикации приложений .NET](../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="1b01d-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="1b01d-108">Развертывание приложения, зависящего от платформы</span><span class="sxs-lookup"><span data-stu-id="1b01d-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="1b01d-109">Чтобы развернуть приложение как приложение, зависящее от платформы, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1b01d-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="1b01d-110">Установите .NET на Raspberry Pi с помощью [скриптов dotnet-install](../core/tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1b01d-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="1b01d-111">В командной строке Bash в Raspberry Pi (локальной или SSH) выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1b01d-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="1b01d-112">Выполните следующую команду, чтобы установить .NET:</span><span class="sxs-lookup"><span data-stu-id="1b01d-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="1b01d-113">При этом устанавливается последняя версия.</span><span class="sxs-lookup"><span data-stu-id="1b01d-113">This installs the latest version.</span></span> <span data-ttu-id="1b01d-114">Если требуется определенная версия, добавьте `--version <VERSION>` в конец, где `<VERSION>` — это конкретная версия сборки.</span><span class="sxs-lookup"><span data-stu-id="1b01d-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="1b01d-115">Чтобы упростить разрешение пути, добавьте переменную среды `DOTNET_ROOT` и добавьте каталог *.dotnet* к `$PATH` с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="1b01d-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="1b01d-116">Проверьте установку .NET, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="1b01d-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="1b01d-117">Убедитесь, что отображаемая версия соответствует установленной версии.</span><span class="sxs-lookup"><span data-stu-id="1b01d-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="1b01d-118">Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.</span><span class="sxs-lookup"><span data-stu-id="1b01d-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="1b01d-119">[Разверните приложение в локальную папку](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019), если используется **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1b01d-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="1b01d-120">Перед публикацией выберите **Изменить** в сводке профиля публикации и перейдите на вкладку **Параметры**. Убедитесь, что для **Режима развертывания** задано значение *Зависимый от платформы*, а **Целевая среда выполнения** — *Портативные*.</span><span class="sxs-lookup"><span data-stu-id="1b01d-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="1b01d-121">При использовании **интерфейса командной строки .NET** используйте команду [dotnet publish](../core/tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="1b01d-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="1b01d-122">Дополнительных аргументов не требуется.</span><span class="sxs-lookup"><span data-stu-id="1b01d-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="1b01d-123">Запустите приложение из командной строки Bash на Raspberry Pi (локальном или SSH).</span><span class="sxs-lookup"><span data-stu-id="1b01d-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="1b01d-124">Для этого задайте папку развертывания в качестве текущего каталога и выполните следующую команду (где *HelloWorld.dll* является точкой входа приложения):</span><span class="sxs-lookup"><span data-stu-id="1b01d-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="1b01d-125">Развертывание автономного приложения</span><span class="sxs-lookup"><span data-stu-id="1b01d-125">Deploying a self-contained app</span></span>

<span data-ttu-id="1b01d-126">Чтобы развернуть приложение как автономное приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="1b01d-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="1b01d-127">Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.</span><span class="sxs-lookup"><span data-stu-id="1b01d-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="1b01d-128">[Разверните приложение в локальную папку](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019), если используется **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1b01d-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="1b01d-129">Перед публикацией выберите **Изменить** в сводке профиля публикации и перейдите на вкладку **Параметры**. Убедитесь, что для **Режима развертывания** задано значение *Автономный*, а **Целевая среда выполнения** — *linux-arm*.</span><span class="sxs-lookup"><span data-stu-id="1b01d-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="1b01d-130">При использовании **интерфейса командной строки .NET** используйте команду [dotnet publish](../core/tools/dotnet-publish.md) с аргументом `-r linux-arm`:</span><span class="sxs-lookup"><span data-stu-id="1b01d-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="1b01d-131">Запустите приложение из командной строки Bash на Raspberry Pi (локальном или SSH).</span><span class="sxs-lookup"><span data-stu-id="1b01d-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="1b01d-132">Для этого задайте в качестве текущего каталога расположение развертывания и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1b01d-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="1b01d-133">Предоставьте исполняемому файлу разрешение *execute* (где `HelloWorld` — имя исполняемого файла).</span><span class="sxs-lookup"><span data-stu-id="1b01d-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="1b01d-134">Запустите исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="1b01d-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```
