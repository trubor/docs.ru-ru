---
title: Установка средства ML.NET CLI
description: Узнайте, как установить, обновить, удалить средство ML.NET CLI, или вернутся к его предыдущей версии.
ms.date: 06/08/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: a2fdaa06c1602a2c3986b2f034cd1840e39d16a3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876777"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="66498-103">Установка средства ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66498-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="66498-104">Узнайте, как установить ML.NET CLI (интерфейс командной строки) в Windows, Mac или Linux.</span><span class="sxs-lookup"><span data-stu-id="66498-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="66498-105">ML.NET CLI создает качественные модели ML.NET и исходный код с помощью автоматизированного машинного обучения (AutoML) и набора данных для обучения.</span><span class="sxs-lookup"><span data-stu-id="66498-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="66498-106">Этот раздел относится к ML.NET CLI и ML.NET AutoML, находящимся в данный момент в предварительной версии; материалы могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="66498-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="66498-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="66498-107">Pre-requisites</span></span>

- [<span data-ttu-id="66498-108">Пакет SDK для .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="66498-108">.NET Core 3.1 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/3.1)

- <span data-ttu-id="66498-109">(Необязательно) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="66498-109">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="66498-110">Вы можете запускать проекты, написанные на C#, из Visual Studio по нажатию кнопки `F5` или с помощью `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="66498-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="66498-111">Примечание. Если после установки пакета SDK для .NET Core команда `dotnet tool` не работает, выйдите из Windows и снова войдите в систему.</span><span class="sxs-lookup"><span data-stu-id="66498-111">Note: If after installing .NET Core SDK the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="66498-112">Установка</span><span class="sxs-lookup"><span data-stu-id="66498-112">Install</span></span>

<span data-ttu-id="66498-113">Средство ML.NET CLI устанавливается так же, как и любое другое глобальное средство .NET.</span><span class="sxs-lookup"><span data-stu-id="66498-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="66498-114">Для этого используйте команду `dotnet tool install` .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="66498-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="66498-115">В примере ниже показано, как установить ML.NET CLI в расположении веб-канала NuGet по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="66498-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="66498-116">Если не удается установить средство (то есть оно недоступно в режиме по умолчанию веб-канала NuGet), отображаются сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="66498-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="66498-117">Убедитесь, что установлены флажки для нужных веб-каналов.</span><span class="sxs-lookup"><span data-stu-id="66498-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="66498-118">Если установка выполнена успешно, отображается сообщение с командой, используемой для вызова средства, и установленной версией, аналогичное приведенному ниже:</span><span class="sxs-lookup"><span data-stu-id="66498-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="66498-119">Можно проверить успешность установки, введя следующую команду:</span><span class="sxs-lookup"><span data-stu-id="66498-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="66498-120">Вы увидите справку для команд, доступных для средства mlnet, например для команды classification.</span><span class="sxs-lookup"><span data-stu-id="66498-120">You should see the help for available commands for the mlnet tool such as the 'classification' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="66498-121">Установка конкретного выпуска</span><span class="sxs-lookup"><span data-stu-id="66498-121">Install a specific release version</span></span>

<span data-ttu-id="66498-122">Если вам необходимо установить предварительную или конкретную версию средства, можно указать [платформу](../../standard/frameworks.md), используя следующий формат:</span><span class="sxs-lookup"><span data-stu-id="66498-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="66498-123">Вы также можете проверить, был ли пакет установлен правильно, введя следующую команду:</span><span class="sxs-lookup"><span data-stu-id="66498-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="66498-124">Удаление пакета интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="66498-124">Uninstall the CLI package</span></span>

<span data-ttu-id="66498-125">Введите следующую команду, чтобы удалить пакет с локального компьютера:</span><span class="sxs-lookup"><span data-stu-id="66498-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="66498-126">Обновление пакета интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="66498-126">Update the CLI package</span></span>

<span data-ttu-id="66498-127">Введите следующую команду, чтобы обновить пакет на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="66498-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="66498-128">Настройка предложений CLI (автозавершение по нажатию TAB)</span><span class="sxs-lookup"><span data-stu-id="66498-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="66498-129">Так как средство ML.NET CLI основано на `System.CommandLine`, оно имеет встроенную поддержку нажатия клавиши TAB.</span><span class="sxs-lookup"><span data-stu-id="66498-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="66498-130">Пример того, как работает автоматическое завершение по нажатию клавиши TAB, см в следующей анимации:</span><span class="sxs-lookup"><span data-stu-id="66498-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![изображение](./media/cli-tab-completion.gif)

<span data-ttu-id="66498-132">Автозавершение клавишей TAB (варианты параметров) работает в *Windows PowerShell* и *bash для macOS и Linux*, но не будет работать в *командной строке Windows*.</span><span class="sxs-lookup"><span data-stu-id="66498-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="66498-133">Чтобы включить его в текущей предварительной версии, конечный пользователь должен выполнить в каждой оболочке ряд однократных действий, описанных ниже.</span><span class="sxs-lookup"><span data-stu-id="66498-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="66498-134">После этого варианты завершения будут работать для всех приложений, написанных с помощью `System.CommandLine`, например ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="66498-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="66498-135">На компьютере, где вы хотите включить завершение, необходимо сделать две вещи.</span><span class="sxs-lookup"><span data-stu-id="66498-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="66498-136">Установите глобальное средство `dotnet-suggest`, запустив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="66498-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="66498-137">Добавьте соответствующую оболочку совместимости к профилю оболочки.</span><span class="sxs-lookup"><span data-stu-id="66498-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="66498-138">Может потребоваться создать файл профиля оболочки.</span><span class="sxs-lookup"><span data-stu-id="66498-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="66498-139">Скрипт оболочки совместимости перенаправит запрос завершения из оболочки в средство `dotnet-suggest`, которое делегирует его в соответствующее `System.CommandLine`-приложение.</span><span class="sxs-lookup"><span data-stu-id="66498-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="66498-140">Для bash следует добавить содержимое [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) в `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="66498-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="66498-141">Для PowerShell следует добавить содержимое [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) в свой профиль PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66498-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/main/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="66498-142">Ожидаемый путь к профилю PowerShell можно получить, выполнив следующую команду в консоли:</span><span class="sxs-lookup"><span data-stu-id="66498-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="66498-143">(В других оболочках [найдите](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) или откройте [соответствующее обращение](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="66498-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="66498-144">Каталог установки</span><span class="sxs-lookup"><span data-stu-id="66498-144">Installation directory</span></span>

<span data-ttu-id="66498-145">ML.NET CLI можно установить в каталоге по умолчанию или в выбранном вами расположении.</span><span class="sxs-lookup"><span data-stu-id="66498-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="66498-146">Каталоги по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="66498-146">The default directories are:</span></span>

| <span data-ttu-id="66498-147">Операционная система</span><span class="sxs-lookup"><span data-stu-id="66498-147">OS</span></span>          | <span data-ttu-id="66498-148">Path</span><span class="sxs-lookup"><span data-stu-id="66498-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="66498-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="66498-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="66498-150">Windows</span><span class="sxs-lookup"><span data-stu-id="66498-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="66498-151">Эти расположения добавляются в путь пользователя при первом запуске пакета SDK, поэтому установленные в них глобальные средства можно вызывать напрямую.</span><span class="sxs-lookup"><span data-stu-id="66498-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="66498-152">Обратите внимание, что глобальные средства входят в область конкретного пользователя, а не глобальную область компьютера.</span><span class="sxs-lookup"><span data-stu-id="66498-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="66498-153">Таким образом, нельзя установить глобальное средство, которое будет доступно для всех пользователей компьютера.</span><span class="sxs-lookup"><span data-stu-id="66498-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="66498-154">Средство доступно только для тех профилей пользователей, в которых оно установлено.</span><span class="sxs-lookup"><span data-stu-id="66498-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="66498-155">Глобальные средства также можно установить в конкретном каталоге.</span><span class="sxs-lookup"><span data-stu-id="66498-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="66498-156">При установке в конкретном каталоге необходимо убедиться, что команда доступна, включив этот каталог в путь, вызвав команду с указанным каталогом или вызвав средство из указанного каталога.</span><span class="sxs-lookup"><span data-stu-id="66498-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="66498-157">В этом случае .NET Core CLI не добавляет это расположение автоматически в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="66498-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="66498-158">См. также</span><span class="sxs-lookup"><span data-stu-id="66498-158">See also</span></span>

- [<span data-ttu-id="66498-159">Обзор ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66498-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="66498-160">Учебник. Проанализируйте тональность с помощью ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66498-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="66498-161">Справочное руководство по команде auto-train в ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66498-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="66498-162">Данные телеметрии в интерфейсе командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="66498-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
