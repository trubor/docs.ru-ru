---
title: Развертывание приложений .NET в Raspberry Pi
description: Узнайте, как развертывать приложения .NET на Raspberry Pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594128"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="e4143-103">Развертывание приложений .NET в Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="e4143-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="e4143-104">Развертывание приложений .NET в Raspberry Pi идентично тому, что и любая другая платформа.</span><span class="sxs-lookup"><span data-stu-id="e4143-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="e4143-105">Приложение может работать как *автономный* или *зависящий от платформы* режим развертывания.</span><span class="sxs-lookup"><span data-stu-id="e4143-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="e4143-106">Каждая стратегия имеет свои преимущества.</span><span class="sxs-lookup"><span data-stu-id="e4143-106">There are advantages to each strategy.</span></span> <span data-ttu-id="e4143-107">Дополнительные сведения см. в статье [Общие сведения о публикации приложений .NET](../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4143-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="e4143-108">Развертывание приложения, зависящего от платформы</span><span class="sxs-lookup"><span data-stu-id="e4143-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="e4143-109">Чтобы развернуть приложение как приложение, зависящее от платформы, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e4143-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="e4143-110">Установите .NET на Raspberry Pi с помощью [скриптов DotNet-Install](../core/tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e4143-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="e4143-111">Выполните следующие действия из командной строки bash на устройстве Raspberry Pi (локальная или SSH):</span><span class="sxs-lookup"><span data-stu-id="e4143-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="e4143-112">Выполните следующую команду, чтобы установить .NET:</span><span class="sxs-lookup"><span data-stu-id="e4143-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="e4143-113">При этом устанавливается последняя версия.</span><span class="sxs-lookup"><span data-stu-id="e4143-113">This installs the latest version.</span></span> <span data-ttu-id="e4143-114">Если требуется определенная версия, добавьте `--version <VERSION>` в конец, где `<VERSION>` — это конкретная версия сборки.</span><span class="sxs-lookup"><span data-stu-id="e4143-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="e4143-115">Чтобы упростить разрешение пути, добавьте `DOTNET_ROOT` переменную среды и добавьте к ней каталог *. DotNet* `$PATH` с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="e4143-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="e4143-116">Проверьте установку .NET, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="e4143-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="e4143-117">Убедитесь, что отображаемая версия соответствует установленной версии.</span><span class="sxs-lookup"><span data-stu-id="e4143-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="e4143-118">Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.</span><span class="sxs-lookup"><span data-stu-id="e4143-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="e4143-119">При использовании **Visual Studio** [разверните приложение в локальной папке](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="e4143-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="e4143-120">Перед публикацией выберите **изменить** в сводке профиля публикации и перейдите на вкладку **Параметры** . Убедитесь, что для **режима развертывания** задано значение " *зависимая от платформы* ", а **Целевая среда выполнения** — " *Переносимая*".</span><span class="sxs-lookup"><span data-stu-id="e4143-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="e4143-121">При использовании **интерфейса командной строки .NET** используйте команду [DotNet Publish](../core/tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="e4143-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="e4143-122">Дополнительные аргументы не требуются.</span><span class="sxs-lookup"><span data-stu-id="e4143-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="e4143-123">В командной строке Bash на Raspberry Pi (Local или SSH) запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="e4143-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="e4143-124">Для этого задайте папку развертывания в качестве текущего каталога и выполните следующую команду (где *HelloWorld.dll* является точкой входа приложения):</span><span class="sxs-lookup"><span data-stu-id="e4143-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="e4143-125">Развертывание автономного приложения</span><span class="sxs-lookup"><span data-stu-id="e4143-125">Deploying a self-contained app</span></span>

<span data-ttu-id="e4143-126">Чтобы развернуть приложение как автономное приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e4143-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="e4143-127">Опубликуйте приложение на компьютере разработки, как показано ниже, в зависимости от среды разработки.</span><span class="sxs-lookup"><span data-stu-id="e4143-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="e4143-128">При использовании **Visual Studio** [разверните приложение в локальной папке](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="e4143-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="e4143-129">Перед публикацией выберите **изменить** в сводке профиля публикации и перейдите на вкладку **Параметры** . Убедитесь, что для **режима развертывания** задано *автономное* и **Целевая среда выполнения** имеет значение *Linux-ARM*.</span><span class="sxs-lookup"><span data-stu-id="e4143-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="e4143-130">При использовании **интерфейса командной строки .NET** используйте команду [DotNet Publish](../core/tools/dotnet-publish.md) с `-r linux-arm` аргументом:</span><span class="sxs-lookup"><span data-stu-id="e4143-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="e4143-131">В командной строке Bash на Raspberry Pi (Local или SSH) запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="e4143-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="e4143-132">Для этого задайте в качестве текущего каталога расположение развертывания и выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e4143-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="e4143-133">Предоставьте исполняемому файлу разрешение *EXECUTE* (где `HelloWorld` — имя исполняемого файла).</span><span class="sxs-lookup"><span data-stu-id="e4143-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="e4143-134">Запустите исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="e4143-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```
