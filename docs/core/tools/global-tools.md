---
title: Средства .NET
description: Установка, использование, обновление и удаление средств .NET. Содержит сведения о глобальных средствах, средствах пути к средству и локальных средствах.
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 8839fd4fba72c9f973d906eabb72919306a847dd
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633888"
---
# <a name="how-to-manage-net-tools"></a><span data-ttu-id="a0b29-104">Управление средствами .NET</span><span class="sxs-lookup"><span data-stu-id="a0b29-104">How to manage .NET tools</span></span>

<span data-ttu-id="a0b29-105">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="a0b29-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="a0b29-106">Средство .NET — это специальный пакет NuGet, который содержит консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="a0b29-106">A .NET tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="a0b29-107">Средство можно установить на компьютере следующими способами.</span><span class="sxs-lookup"><span data-stu-id="a0b29-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="a0b29-108">Как глобальное средство.</span><span class="sxs-lookup"><span data-stu-id="a0b29-108">As a global tool.</span></span>

  <span data-ttu-id="a0b29-109">Двоичные файлы инструментов устанавливаются в каталог по умолчанию, который добавляется в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="a0b29-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="a0b29-110">Это средство можно вызвать из любого каталога на компьютере, не указывая его расположение.</span><span class="sxs-lookup"><span data-stu-id="a0b29-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="a0b29-111">Для всех каталогов на компьютере используется одна версия средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="a0b29-112">В качестве глобального средства в пользовательском расположении (также известном как средство пути к средству).</span><span class="sxs-lookup"><span data-stu-id="a0b29-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="a0b29-113">Двоичные файлы средств устанавливаются в указанном расположении.</span><span class="sxs-lookup"><span data-stu-id="a0b29-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="a0b29-114">Вы можете вызвать средство из каталога установки, предоставив каталог с именем команды или добавив каталог в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="a0b29-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="a0b29-115">Для всех каталогов на компьютере используется одна версия средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="a0b29-116">В качестве локального средства (применяется к пакету SDK для .NET Core 3.0 и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="a0b29-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="a0b29-117">Двоичные файлы средств устанавливаются в каталог по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a0b29-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="a0b29-118">Средство вызывается из каталога установки или любого из его подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="a0b29-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="a0b29-119">Разные каталоги могут использовать разные версии одного и того же средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="a0b29-120">В .NET CLI для наблюдения за тем, какие средства устанавливаются для каталога в качестве локальных, используются файлы манифеста.</span><span class="sxs-lookup"><span data-stu-id="a0b29-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="a0b29-121">Когда файл манифеста сохраняется в корневом каталоге репозитория исходного кода, участник может клонировать репозиторий и вызвать одну команду CLI .NET, которая устанавливает все средства, перечисленные в файлах манифеста.</span><span class="sxs-lookup"><span data-stu-id="a0b29-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0b29-122">Средства .NET выполняются с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="a0b29-122">.NET tools run in full trust.</span></span> <span data-ttu-id="a0b29-123">Не устанавливайте средства .NET, если вы не доверяете автору.</span><span class="sxs-lookup"><span data-stu-id="a0b29-123">Do not install a .NET tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="a0b29-124">Поиск средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-124">Find a tool</span></span>

<span data-ttu-id="a0b29-125">Ниже приведены некоторые способы поиска средств.</span><span class="sxs-lookup"><span data-stu-id="a0b29-125">Here are some ways to find tools:</span></span>

* <span data-ttu-id="a0b29-126">Чтобы найти средство, опубликованное в NuGet.org, используйте команду [dotnet tool search](dotnet-tool-search.md).</span><span class="sxs-lookup"><span data-stu-id="a0b29-126">Use the [dotnet tool search](dotnet-tool-search.md) command to find a tool that is published to NuGet.org.</span></span>
* <span data-ttu-id="a0b29-127">Выполните поиск на веб-сайте [NuGet](https://www.nuget.org), используя фильтр .NET tool (Инструмент .NET) из категории Package type (Тип пакета).</span><span class="sxs-lookup"><span data-stu-id="a0b29-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="a0b29-128">Дополнительные сведения см. в разделе [Поиск и выбор пакетов](/nuget/consume-packages/finding-and-choosing-packages).</span><span class="sxs-lookup"><span data-stu-id="a0b29-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="a0b29-129">См. исходный код для средств, созданных командой разработчиков ASP.NET Core в [каталоге средств репозитория GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="a0b29-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="a0b29-130">Дополнительные сведения о средствах диагностики см. в разделе [Средства диагностики .NET](../diagnostics/index.md#net-core-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="a0b29-130">Learn about diagnostic tools at [.NET diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="a0b29-131">Проверка автора и статистики</span><span class="sxs-lookup"><span data-stu-id="a0b29-131">Check the author and statistics</span></span>

<span data-ttu-id="a0b29-132">Поскольку средства .NET работают в режиме полного доверия, а глобальные средства добавляются в переменную среды PATH, они могут быть очень мощными.</span><span class="sxs-lookup"><span data-stu-id="a0b29-132">Since .NET tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="a0b29-133">Не скачивайте средства авторов, которым вы не доверяете.</span><span class="sxs-lookup"><span data-stu-id="a0b29-133">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="a0b29-134">Если средство размещается в NuGet, вы можете проверить автора и статистику, выполнив поиск средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-134">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="a0b29-135">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-135">Install a global tool</span></span>

<span data-ttu-id="a0b29-136">Чтобы установить средство в качестве глобального средства, используйте `-g` или опцию `--global` [установки средства dotnet](dotnet-tool-install.md), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a0b29-136">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="a0b29-137">В выходных данных отображается команда, используемая для вызова средства и установленной версии, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a0b29-137">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="a0b29-138">Расположение двоичных файлов средства по умолчанию зависит от операционной системы.</span><span class="sxs-lookup"><span data-stu-id="a0b29-138">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="a0b29-139">Операционная система</span><span class="sxs-lookup"><span data-stu-id="a0b29-139">OS</span></span>          | <span data-ttu-id="a0b29-140">Path</span><span class="sxs-lookup"><span data-stu-id="a0b29-140">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="a0b29-141">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="a0b29-141">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="a0b29-142">Windows</span><span class="sxs-lookup"><span data-stu-id="a0b29-142">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="a0b29-143">Это расположение добавляется к пути пользователя при первом запуске пакета SDK, поэтому глобальные средства можно вызывать из любого каталога, не указывая расположение средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-143">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="a0b29-144">Доступ к средству зависит от конкретного пользователя, а не от глобального компьютера.</span><span class="sxs-lookup"><span data-stu-id="a0b29-144">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="a0b29-145">Глобальное средство доступно только для пользователя, установившего средство.</span><span class="sxs-lookup"><span data-stu-id="a0b29-145">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="a0b29-146">Установка глобального средства в пользовательском расположении</span><span class="sxs-lookup"><span data-stu-id="a0b29-146">Install a global tool in a custom location</span></span>

<span data-ttu-id="a0b29-147">Чтобы установить средство в качестве глобального средства в пользовательском расположении, используйте опцию `--tool-path` [установки средства dotnet](dotnet-tool-install.md), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a0b29-147">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="a0b29-148">Windows:</span><span class="sxs-lookup"><span data-stu-id="a0b29-148">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="a0b29-149">В Linux или macOS.</span><span class="sxs-lookup"><span data-stu-id="a0b29-149">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="a0b29-150">Пакет SDK для .NET не добавляет это расположение автоматически в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="a0b29-150">The .NET SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="a0b29-151">Чтобы [вызвать средство пути к средству](#invoke-a-tool-path-tool), необходимо убедиться, что команда доступна с помощью одного из следующих методов.</span><span class="sxs-lookup"><span data-stu-id="a0b29-151">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="a0b29-152">Добавьте каталог установки в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="a0b29-152">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="a0b29-153">При вызове средства следует указать полный путь к нему.</span><span class="sxs-lookup"><span data-stu-id="a0b29-153">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="a0b29-154">Вызовите средство из каталога установки.</span><span class="sxs-lookup"><span data-stu-id="a0b29-154">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="a0b29-155">Установка локального средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-155">Install a local tool</span></span>

<span data-ttu-id="a0b29-156">**Применимо к пакету SDK для .NET Core 3.0 и более поздних версий.**</span><span class="sxs-lookup"><span data-stu-id="a0b29-156">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="a0b29-157">Чтобы установить средство только для локального доступа (для текущего каталога и подкаталогов), его необходимо добавить в файл манифеста средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-157">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="a0b29-158">Чтобы создать файл манифеста средства, выполните команду `dotnet new tool-manifest`:</span><span class="sxs-lookup"><span data-stu-id="a0b29-158">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="a0b29-159">Эта команда создает файл манифеста с именем *dotnet-tools.json* в каталоге *.config*.</span><span class="sxs-lookup"><span data-stu-id="a0b29-159">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="a0b29-160">Для добавления локального средства в файл манифеста используйте команду [dotnet tool install](dotnet-tool-install.md) и **omit** опции `--global` и `--tool-path`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a0b29-160">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="a0b29-161">Вывод команды показывает, в каком файле манифеста находится только что установленное средство, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a0b29-161">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="a0b29-162">В следующем примере показан файл манифеста с двумя установленными локальными средствами.</span><span class="sxs-lookup"><span data-stu-id="a0b29-162">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="a0b29-163">Обычно вы добавляете локальное средство в корневой каталог репозитория.</span><span class="sxs-lookup"><span data-stu-id="a0b29-163">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="a0b29-164">После записи файла манифеста в репозиторий после изменения, разработчики, извлекающие код из репозитория, получают последний файл манифеста.</span><span class="sxs-lookup"><span data-stu-id="a0b29-164">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="a0b29-165">Чтобы установить все средства, перечисленные в файле манифеста, они запускают команду `dotnet tool restore`:</span><span class="sxs-lookup"><span data-stu-id="a0b29-165">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="a0b29-166">Вывод показывает, какие инструменты восстановлены:</span><span class="sxs-lookup"><span data-stu-id="a0b29-166">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="a0b29-167">Установка конкретной версии средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-167">Install a specific tool version</span></span>

<span data-ttu-id="a0b29-168">Чтобы установить предварительную или конкретную версию средства, укажите номер версии, используя параметр `--version`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="a0b29-168">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="a0b29-169">Использование средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-169">Use a tool</span></span>

<span data-ttu-id="a0b29-170">Команда, которую вы используете для вызова средства, может отличаться от названия пакета, который вы устанавливаете.</span><span class="sxs-lookup"><span data-stu-id="a0b29-170">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="a0b29-171">Чтобы отобразить все средства, установленные на компьютере для текущего пользователя, используйте команду [dotnet tool list](dotnet-tool-list.md):</span><span class="sxs-lookup"><span data-stu-id="a0b29-171">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="a0b29-172">На выходе показаны версия и команда каждого средства, аналогично следующему примеру.</span><span class="sxs-lookup"><span data-stu-id="a0b29-172">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="a0b29-173">Как показано в этом примере, список показывает локальные средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-173">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="a0b29-174">Для просмотра глобальных средств используйте параметр `--global`, а для просмотра средства пути к средствам — `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a0b29-174">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="a0b29-175">Вызов глобального инструмента</span><span class="sxs-lookup"><span data-stu-id="a0b29-175">Invoke a global tool</span></span>

<span data-ttu-id="a0b29-176">Для глобальных средств используйте команду средства самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a0b29-176">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="a0b29-177">Например, если команда `dotnetsay` или `dotnet-doc`, это то, что вы используете для вызова команды.</span><span class="sxs-lookup"><span data-stu-id="a0b29-177">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="a0b29-178">Если команда начинается с префикса `dotnet-`, альтернативный способ вызова средства — использование команды `dotnet` и опускание префикса команды средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-178">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="a0b29-179">Например, если команда `dotnet-doc`, то средство вызывает следующая команда.</span><span class="sxs-lookup"><span data-stu-id="a0b29-179">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="a0b29-180">Однако в следующем сценарии для вызова глобального средства нельзя использовать команду `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="a0b29-180">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="a0b29-181">Глобальное и локальное средство имеют одну и ту же команду с префиксом `dotnet-`.</span><span class="sxs-lookup"><span data-stu-id="a0b29-181">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="a0b29-182">Вы хотите вызвать глобальное средство из каталога, находящегося в области действия локального средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-182">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="a0b29-183">В этом сценарии локальное средство вызывают `dotnet doc` и `dotnet dotnet-doc`.</span><span class="sxs-lookup"><span data-stu-id="a0b29-183">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="a0b29-184">Чтобы вызвать глобальное средство, используйте команду самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a0b29-184">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="a0b29-185">Вызов средства пути к средству</span><span class="sxs-lookup"><span data-stu-id="a0b29-185">Invoke a tool-path tool</span></span>

<span data-ttu-id="a0b29-186">Для вызова глобального средства, которое устанавливается с помощью опции `tool-path`, убедитесь, что команда доступна, как объяснялось [ранее в этой статье](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="a0b29-186">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="a0b29-187">Вызов локального средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-187">Invoke a local tool</span></span>

<span data-ttu-id="a0b29-188">Для вызова локального средства необходимо использовать команду `dotnet` из каталога установки.</span><span class="sxs-lookup"><span data-stu-id="a0b29-188">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="a0b29-189">Вы можете использовать длинную (`dotnet tool run <COMMAND_NAME>`) или короткую (`dotnet <COMMAND_NAME>`) форму, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="a0b29-189">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="a0b29-190">Если команда имеет префикс `dotnet-`, вы можете включить или исключить префикс при вызове средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-190">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="a0b29-191">Например, если команда `dotnet-doc`, то локальное средство вызовет любой из следующих примеров.</span><span class="sxs-lookup"><span data-stu-id="a0b29-191">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="a0b29-192">Обновление средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-192">Update a tool</span></span>

<span data-ttu-id="a0b29-193">Обновление средства подразумевает его удаление и установку последней стабильной версии.</span><span class="sxs-lookup"><span data-stu-id="a0b29-193">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="a0b29-194">Для обновления средства используйте команду [dotnet tool update](dotnet-tool-update.md) с той же опцией, что и при установке средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-194">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="a0b29-195">Для локального средства пакет SDK находит первый файл манифеста, который содержит идентификатор пакета, выполнив поиск в текущем и родительском каталоге.</span><span class="sxs-lookup"><span data-stu-id="a0b29-195">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="a0b29-196">Если такой идентификатор пакета отсутствует в любом файле манифеста, пакет SDK добавляет новую запись в ближайший файл манифеста.</span><span class="sxs-lookup"><span data-stu-id="a0b29-196">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="a0b29-197">Удаление средства</span><span class="sxs-lookup"><span data-stu-id="a0b29-197">Uninstall a tool</span></span>

<span data-ttu-id="a0b29-198">Удалите инструмент с помощью команды [dotnet tool uninstall](dotnet-tool-uninstall.md) с той же опцией, которую вы использовали для установки средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-198">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="a0b29-199">Для локального средства пакет SDK находит первый файл манифеста, который содержит идентификатор пакета, выполнив поиск в текущем и родительском каталоге.</span><span class="sxs-lookup"><span data-stu-id="a0b29-199">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="a0b29-200">Получение справки и устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="a0b29-200">Get help and troubleshoot</span></span>

<span data-ttu-id="a0b29-201">Чтобы получить список доступных команд `dotnet tool`, введите следующую команду.</span><span class="sxs-lookup"><span data-stu-id="a0b29-201">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="a0b29-202">Чтобы получить инструкции по использованию средства, введите одну из следующих команд или посетите веб-сайт средства.</span><span class="sxs-lookup"><span data-stu-id="a0b29-202">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="a0b29-203">Если средство не удается установить или запустить, см. статью [Устранение неполадок при использовании средства .NET](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="a0b29-203">If a tool fails to install or run, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b29-204">См. также</span><span class="sxs-lookup"><span data-stu-id="a0b29-204">See also</span></span>

- [<span data-ttu-id="a0b29-205">Учебник. Создание средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="a0b29-205">Tutorial: Create a .NET tool using the .NET CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="a0b29-206">Учебник. Установка и использование глобального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="a0b29-206">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="a0b29-207">Учебник. Установка и использование локального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="a0b29-207">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
