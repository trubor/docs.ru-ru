---
title: Средства .NET
description: Установка, использование, обновление и удаление средств .NET. Содержит сведения о глобальных средствах, средствах пути к средству и локальных средствах.
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: d4fca6b52b1444cf73efc49a6c50294cc5f6015b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874827"
---
# <a name="how-to-manage-net-tools"></a><span data-ttu-id="97c36-104">Управление средствами .NET</span><span class="sxs-lookup"><span data-stu-id="97c36-104">How to manage .NET tools</span></span>

<span data-ttu-id="97c36-105">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="97c36-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="97c36-106">Средство .NET — это специальный пакет NuGet, который содержит консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="97c36-106">A .NET tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="97c36-107">Средство можно установить на компьютере следующими способами.</span><span class="sxs-lookup"><span data-stu-id="97c36-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="97c36-108">Как глобальное средство.</span><span class="sxs-lookup"><span data-stu-id="97c36-108">As a global tool.</span></span>

  <span data-ttu-id="97c36-109">Двоичные файлы инструментов устанавливаются в каталог по умолчанию, который добавляется в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="97c36-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="97c36-110">Это средство можно вызвать из любого каталога на компьютере, не указывая его расположение.</span><span class="sxs-lookup"><span data-stu-id="97c36-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="97c36-111">Для всех каталогов на компьютере используется одна версия средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="97c36-112">В качестве глобального средства в пользовательском расположении (также известном как средство пути к средству).</span><span class="sxs-lookup"><span data-stu-id="97c36-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="97c36-113">Двоичные файлы средств устанавливаются в указанном расположении.</span><span class="sxs-lookup"><span data-stu-id="97c36-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="97c36-114">Вы можете вызвать средство из каталога установки, предоставив каталог с именем команды или добавив каталог в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="97c36-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="97c36-115">Для всех каталогов на компьютере используется одна версия средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="97c36-116">В качестве локального средства (применяется к пакету SDK для .NET Core 3.0 и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="97c36-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="97c36-117">Двоичные файлы средств устанавливаются в каталог по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="97c36-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="97c36-118">Средство вызывается из каталога установки или любого из его подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="97c36-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="97c36-119">Разные каталоги могут использовать разные версии одного и того же средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="97c36-120">В .NET CLI для наблюдения за тем, какие средства устанавливаются для каталога в качестве локальных, используются файлы манифеста.</span><span class="sxs-lookup"><span data-stu-id="97c36-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="97c36-121">Когда файл манифеста сохраняется в корневом каталоге репозитория исходного кода, участник может клонировать репозиторий и вызвать одну команду CLI .NET, которая устанавливает все средства, перечисленные в файлах манифеста.</span><span class="sxs-lookup"><span data-stu-id="97c36-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97c36-122">Средства .NET выполняются с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="97c36-122">.NET tools run in full trust.</span></span> <span data-ttu-id="97c36-123">Не устанавливайте средства .NET, если вы не доверяете автору.</span><span class="sxs-lookup"><span data-stu-id="97c36-123">Do not install a .NET tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="97c36-124">Поиск средства</span><span class="sxs-lookup"><span data-stu-id="97c36-124">Find a tool</span></span>

<span data-ttu-id="97c36-125">Ниже приведены некоторые способы поиска средств.</span><span class="sxs-lookup"><span data-stu-id="97c36-125">Here are some ways to find tools:</span></span>

* <span data-ttu-id="97c36-126">Чтобы найти средство, опубликованное в NuGet.org, используйте команду [dotnet tool search](dotnet-tool-search.md).</span><span class="sxs-lookup"><span data-stu-id="97c36-126">Use the [dotnet tool search](dotnet-tool-search.md) command to find a tool that is published to NuGet.org.</span></span>
* <span data-ttu-id="97c36-127">Выполните поиск на веб-сайте [NuGet](https://www.nuget.org), используя фильтр .NET tool (Инструмент .NET) из категории Package type (Тип пакета).</span><span class="sxs-lookup"><span data-stu-id="97c36-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="97c36-128">Дополнительные сведения см. в разделе [Поиск и выбор пакетов](/nuget/consume-packages/finding-and-choosing-packages).</span><span class="sxs-lookup"><span data-stu-id="97c36-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="97c36-129">См. исходный код для средств, созданных командой разработчиков ASP.NET Core в [каталоге средств репозитория GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/main/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="97c36-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/main/src/Tools).</span></span>
* <span data-ttu-id="97c36-130">Дополнительные сведения о средствах диагностики см. в разделе [Средства диагностики .NET](../diagnostics/index.md#net-core-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="97c36-130">Learn about diagnostic tools at [.NET diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="97c36-131">Проверка автора и статистики</span><span class="sxs-lookup"><span data-stu-id="97c36-131">Check the author and statistics</span></span>

<span data-ttu-id="97c36-132">Поскольку средства .NET работают в режиме полного доверия, а глобальные средства добавляются в переменную среды PATH, они могут быть очень мощными.</span><span class="sxs-lookup"><span data-stu-id="97c36-132">Since .NET tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="97c36-133">Не скачивайте средства авторов, которым вы не доверяете.</span><span class="sxs-lookup"><span data-stu-id="97c36-133">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="97c36-134">Если средство размещается в NuGet, вы можете проверить автора и статистику, выполнив поиск средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-134">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="97c36-135">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="97c36-135">Install a global tool</span></span>

<span data-ttu-id="97c36-136">Чтобы установить средство в качестве глобального средства, используйте `-g` или опцию `--global` [установки средства dotnet](dotnet-tool-install.md), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97c36-136">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="97c36-137">В выходных данных отображается команда, используемая для вызова средства и установленной версии, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97c36-137">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="97c36-138">Расположение двоичных файлов средства по умолчанию зависит от операционной системы.</span><span class="sxs-lookup"><span data-stu-id="97c36-138">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="97c36-139">Операционная система</span><span class="sxs-lookup"><span data-stu-id="97c36-139">OS</span></span>          | <span data-ttu-id="97c36-140">Path</span><span class="sxs-lookup"><span data-stu-id="97c36-140">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="97c36-141">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="97c36-141">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="97c36-142">Windows</span><span class="sxs-lookup"><span data-stu-id="97c36-142">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="97c36-143">Это расположение добавляется к пути пользователя при первом запуске пакета SDK, поэтому глобальные средства можно вызывать из любого каталога, не указывая расположение средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-143">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="97c36-144">Доступ к средству зависит от конкретного пользователя, а не от глобального компьютера.</span><span class="sxs-lookup"><span data-stu-id="97c36-144">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="97c36-145">Глобальное средство доступно только для пользователя, установившего средство.</span><span class="sxs-lookup"><span data-stu-id="97c36-145">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="97c36-146">Установка глобального средства в пользовательском расположении</span><span class="sxs-lookup"><span data-stu-id="97c36-146">Install a global tool in a custom location</span></span>

<span data-ttu-id="97c36-147">Чтобы установить средство в качестве глобального средства в пользовательском расположении, используйте опцию `--tool-path` [установки средства dotnet](dotnet-tool-install.md), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97c36-147">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="97c36-148">Windows:</span><span class="sxs-lookup"><span data-stu-id="97c36-148">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="97c36-149">В Linux или macOS.</span><span class="sxs-lookup"><span data-stu-id="97c36-149">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="97c36-150">Пакет SDK для .NET не добавляет это расположение автоматически в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="97c36-150">The .NET SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="97c36-151">Чтобы [вызвать средство пути к средству](#invoke-a-tool-path-tool), необходимо убедиться, что команда доступна с помощью одного из следующих методов.</span><span class="sxs-lookup"><span data-stu-id="97c36-151">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="97c36-152">Добавьте каталог установки в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="97c36-152">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="97c36-153">При вызове средства следует указать полный путь к нему.</span><span class="sxs-lookup"><span data-stu-id="97c36-153">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="97c36-154">Вызовите средство из каталога установки.</span><span class="sxs-lookup"><span data-stu-id="97c36-154">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="97c36-155">Установка локального средства</span><span class="sxs-lookup"><span data-stu-id="97c36-155">Install a local tool</span></span>

<span data-ttu-id="97c36-156">**Применимо к пакету SDK для .NET Core 3.0 и более поздних версий.**</span><span class="sxs-lookup"><span data-stu-id="97c36-156">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="97c36-157">Чтобы установить средство только для локального доступа (для текущего каталога и подкаталогов), его необходимо добавить в файл манифеста средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-157">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="97c36-158">Чтобы создать файл манифеста средства, выполните команду `dotnet new tool-manifest`:</span><span class="sxs-lookup"><span data-stu-id="97c36-158">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="97c36-159">Эта команда создает файл манифеста с именем *dotnet-tools.json* в каталоге *.config*.</span><span class="sxs-lookup"><span data-stu-id="97c36-159">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="97c36-160">Для добавления локального средства в файл манифеста используйте команду [dotnet tool install](dotnet-tool-install.md) и **omit** опции `--global` и `--tool-path`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97c36-160">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="97c36-161">Вывод команды показывает, в каком файле манифеста находится только что установленное средство, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97c36-161">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="97c36-162">В следующем примере показан файл манифеста с двумя установленными локальными средствами.</span><span class="sxs-lookup"><span data-stu-id="97c36-162">The following example shows a manifest file with two local tools installed:</span></span>

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

<span data-ttu-id="97c36-163">Обычно вы добавляете локальное средство в корневой каталог репозитория.</span><span class="sxs-lookup"><span data-stu-id="97c36-163">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="97c36-164">После записи файла манифеста в репозиторий после изменения, разработчики, извлекающие код из репозитория, получают последний файл манифеста.</span><span class="sxs-lookup"><span data-stu-id="97c36-164">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="97c36-165">Чтобы установить все средства, перечисленные в файле манифеста, они запускают команду `dotnet tool restore`:</span><span class="sxs-lookup"><span data-stu-id="97c36-165">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="97c36-166">Вывод показывает, какие инструменты восстановлены:</span><span class="sxs-lookup"><span data-stu-id="97c36-166">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="97c36-167">Установка конкретной версии средства</span><span class="sxs-lookup"><span data-stu-id="97c36-167">Install a specific tool version</span></span>

<span data-ttu-id="97c36-168">Чтобы установить предварительную или конкретную версию средства, укажите номер версии, используя параметр `--version`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="97c36-168">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="97c36-169">Использование средства</span><span class="sxs-lookup"><span data-stu-id="97c36-169">Use a tool</span></span>

<span data-ttu-id="97c36-170">Команда, которую вы используете для вызова средства, может отличаться от названия пакета, который вы устанавливаете.</span><span class="sxs-lookup"><span data-stu-id="97c36-170">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="97c36-171">Чтобы отобразить все средства, установленные на компьютере для текущего пользователя, используйте команду [dotnet tool list](dotnet-tool-list.md):</span><span class="sxs-lookup"><span data-stu-id="97c36-171">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="97c36-172">На выходе показаны версия и команда каждого средства, аналогично следующему примеру.</span><span class="sxs-lookup"><span data-stu-id="97c36-172">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="97c36-173">Как показано в этом примере, список показывает локальные средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-173">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="97c36-174">Для просмотра глобальных средств используйте параметр `--global`, а для просмотра средства пути к средствам — `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="97c36-174">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="97c36-175">Вызов глобального инструмента</span><span class="sxs-lookup"><span data-stu-id="97c36-175">Invoke a global tool</span></span>

<span data-ttu-id="97c36-176">Для глобальных средств используйте команду средства самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="97c36-176">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="97c36-177">Например, если команда `dotnetsay` или `dotnet-doc`, это то, что вы используете для вызова команды.</span><span class="sxs-lookup"><span data-stu-id="97c36-177">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="97c36-178">Если команда начинается с префикса `dotnet-`, альтернативный способ вызова средства — использование команды `dotnet` и опускание префикса команды средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-178">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="97c36-179">Например, если команда `dotnet-doc`, то средство вызывает следующая команда.</span><span class="sxs-lookup"><span data-stu-id="97c36-179">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="97c36-180">Однако в следующем сценарии для вызова глобального средства нельзя использовать команду `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="97c36-180">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="97c36-181">Глобальное и локальное средство имеют одну и ту же команду с префиксом `dotnet-`.</span><span class="sxs-lookup"><span data-stu-id="97c36-181">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="97c36-182">Вы хотите вызвать глобальное средство из каталога, находящегося в области действия локального средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-182">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="97c36-183">В этом сценарии локальное средство вызывают `dotnet doc` и `dotnet dotnet-doc`.</span><span class="sxs-lookup"><span data-stu-id="97c36-183">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="97c36-184">Чтобы вызвать глобальное средство, используйте команду самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="97c36-184">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="97c36-185">Вызов средства пути к средству</span><span class="sxs-lookup"><span data-stu-id="97c36-185">Invoke a tool-path tool</span></span>

<span data-ttu-id="97c36-186">Для вызова глобального средства, которое устанавливается с помощью опции `tool-path`, убедитесь, что команда доступна, как объяснялось [ранее в этой статье](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="97c36-186">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="97c36-187">Вызов локального средства</span><span class="sxs-lookup"><span data-stu-id="97c36-187">Invoke a local tool</span></span>

<span data-ttu-id="97c36-188">Для вызова локального средства необходимо использовать команду `dotnet` из каталога установки.</span><span class="sxs-lookup"><span data-stu-id="97c36-188">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="97c36-189">Вы можете использовать длинную (`dotnet tool run <COMMAND_NAME>`) или короткую (`dotnet <COMMAND_NAME>`) форму, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="97c36-189">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="97c36-190">Если команда имеет префикс `dotnet-`, вы можете включить или исключить префикс при вызове средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-190">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="97c36-191">Например, если команда `dotnet-doc`, то локальное средство вызовет любой из следующих примеров.</span><span class="sxs-lookup"><span data-stu-id="97c36-191">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="97c36-192">Обновление средства</span><span class="sxs-lookup"><span data-stu-id="97c36-192">Update a tool</span></span>

<span data-ttu-id="97c36-193">Обновление средства подразумевает его удаление и установку последней стабильной версии.</span><span class="sxs-lookup"><span data-stu-id="97c36-193">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="97c36-194">Для обновления средства используйте команду [dotnet tool update](dotnet-tool-update.md) с той же опцией, что и при установке средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-194">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="97c36-195">Для локального средства пакет SDK находит первый файл манифеста, который содержит идентификатор пакета, выполнив поиск в текущем и родительском каталоге.</span><span class="sxs-lookup"><span data-stu-id="97c36-195">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="97c36-196">Если такой идентификатор пакета отсутствует в любом файле манифеста, пакет SDK добавляет новую запись в ближайший файл манифеста.</span><span class="sxs-lookup"><span data-stu-id="97c36-196">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="97c36-197">Удаление средства</span><span class="sxs-lookup"><span data-stu-id="97c36-197">Uninstall a tool</span></span>

<span data-ttu-id="97c36-198">Удалите инструмент с помощью команды [dotnet tool uninstall](dotnet-tool-uninstall.md) с той же опцией, которую вы использовали для установки средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-198">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="97c36-199">Для локального средства пакет SDK находит первый файл манифеста, который содержит идентификатор пакета, выполнив поиск в текущем и родительском каталоге.</span><span class="sxs-lookup"><span data-stu-id="97c36-199">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="97c36-200">Получение справки и устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="97c36-200">Get help and troubleshoot</span></span>

<span data-ttu-id="97c36-201">Чтобы получить список доступных команд `dotnet tool`, введите следующую команду.</span><span class="sxs-lookup"><span data-stu-id="97c36-201">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="97c36-202">Чтобы получить инструкции по использованию средства, введите одну из следующих команд или посетите веб-сайт средства.</span><span class="sxs-lookup"><span data-stu-id="97c36-202">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="97c36-203">Если средство не удается установить или запустить, см. статью [Устранение неполадок при использовании средства .NET](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="97c36-203">If a tool fails to install or run, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97c36-204">См. также</span><span class="sxs-lookup"><span data-stu-id="97c36-204">See also</span></span>

- [<span data-ttu-id="97c36-205">Учебник. Создание средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="97c36-205">Tutorial: Create a .NET tool using the .NET CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="97c36-206">Учебник. Установка и использование глобального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="97c36-206">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="97c36-207">Учебник. Установка и использование локального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="97c36-207">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
