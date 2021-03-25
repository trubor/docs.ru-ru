---
title: Средство диагностики dotnet-symbol — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-symbol для загрузки файлов, необходимых для отладки дампов и минидампов .NET.
ms.date: 11/17/2020
ms.openlocfilehash: 4543bd965c889d93d7dc0b89ff2d6f62c4343e5f
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189908"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="284a6-103">Загрузчик символов (dotnet-symbol)</span><span class="sxs-lookup"><span data-stu-id="284a6-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="284a6-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="284a6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="284a6-105">Установка</span><span class="sxs-lookup"><span data-stu-id="284a6-105">Install</span></span>

<span data-ttu-id="284a6-106">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-symbol) `dotnet-symbol`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="284a6-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="284a6-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="284a6-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="284a6-108">Описание</span><span class="sxs-lookup"><span data-stu-id="284a6-108">Description</span></span>

<span data-ttu-id="284a6-109">Глобальный инструмент `dotnet-symbol` скачивает файлы (символы, приложения уровня данных, модули и т. д.), необходимые для отладки основных дампов и минидампов.</span><span class="sxs-lookup"><span data-stu-id="284a6-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="284a6-110">Это может быть полезно при отладке дампов, записанных на другой компьютер.</span><span class="sxs-lookup"><span data-stu-id="284a6-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="284a6-111">`dotnet-symbol` может скачивать модули и символы, необходимые для анализа дампа.</span><span class="sxs-lookup"><span data-stu-id="284a6-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="284a6-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="284a6-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="284a6-113">Добавление пути к серверу символов "http://msdl.microsoft.com/download/symbols" (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="284a6-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="284a6-114">Добавление сервера символов в путь к серверу.</span><span class="sxs-lookup"><span data-stu-id="284a6-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="284a6-115">Добавление сервера символов, прошедшего проверку подлинности, в путь к серверу с помощью личного маркера доступа (PAT).</span><span class="sxs-lookup"><span data-stu-id="284a6-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="284a6-116">Добавление каталога кэша.</span><span class="sxs-lookup"><span data-stu-id="284a6-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="284a6-117">Обработка входных файлов во всех подкаталогах.</span><span class="sxs-lookup"><span data-stu-id="284a6-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="284a6-118">Загрузка только основной программы (то есть dotnet), которая требуется lldb для загрузки основных дампов.</span><span class="sxs-lookup"><span data-stu-id="284a6-118">Download only the host program (that is, dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="284a6-119">Загрузка файлов символов (PDB, DBG, DWARF).</span><span class="sxs-lookup"><span data-stu-id="284a6-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="284a6-120">Загрузка файлов модулей (DLL, SO, DYLIB).</span><span class="sxs-lookup"><span data-stu-id="284a6-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="284a6-121">Загрузка специальных модулей отладки (DAC, DBI, SOS).</span><span class="sxs-lookup"><span data-stu-id="284a6-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="284a6-122">Принудительная загрузка файлов PDB Windows при наличии переносимых PDB.</span><span class="sxs-lookup"><span data-stu-id="284a6-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="284a6-123">Указание выходного каталога.</span><span class="sxs-lookup"><span data-stu-id="284a6-123">Set the output directory.</span></span> <span data-ttu-id="284a6-124">В противном случае запись рядом с входным файлом (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="284a6-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="284a6-125">Включение выходных данных диагностики.</span><span class="sxs-lookup"><span data-stu-id="284a6-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="284a6-126">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="284a6-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="284a6-127">Скачать символы</span><span class="sxs-lookup"><span data-stu-id="284a6-127">Download symbols</span></span>

<span data-ttu-id="284a6-128">Выполнение `dotnet-symbol` для файла дампа по умолчанию загружает все модули, символы и файлы DAC/DBI, необходимые для отладки дампа, включая управляемые сборки.</span><span class="sxs-lookup"><span data-stu-id="284a6-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="284a6-129">Поскольку SOS теперь может скачивать символы при необходимости, большинство основных дампов Linux можно анализировать с помощью lldb, используя только модули host (dotnet) и модули отладки.</span><span class="sxs-lookup"><span data-stu-id="284a6-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="284a6-130">Чтобы получить эти файлы, необходимые для диагностики основного дампа с помощью lldb, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="284a6-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="284a6-131">Диагностика</span><span class="sxs-lookup"><span data-stu-id="284a6-131">Troubleshoot</span></span>

- <span data-ttu-id="284a6-132">Ошибка 404 (объект не найден) при скачивании символов.</span><span class="sxs-lookup"><span data-stu-id="284a6-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="284a6-133">Загрузка символов поддерживается только для официальных версий среды выполнения .NET Core, полученных по официальным каналам, таким как [официальный веб-сайт](https://dotnet.microsoft.com/download/dotnet) и [источники по умолчанию в сценариях установки dotnet](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="284a6-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet) and the [default sources in the dotnet installation scripts](../tools/dotnet-install-script.md).</span></span> <span data-ttu-id="284a6-134">Ошибка 404 при скачивании файлов отладки может указывать на то, что дамп был создан с помощью среды выполнения .NET Core из другого источника, например из исходного кода, созданного локально или для конкретного дистрибутива Linux, либо с сайтов сообщества, таких как archlinux.</span><span class="sxs-lookup"><span data-stu-id="284a6-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="284a6-135">В таких случаях файл, необходимый для отладки (dotnet, libcoreclr.so и libmscordaccore.so), должен быть скопирован из этих источников или из среды, в которой был создан файл дампа.</span><span class="sxs-lookup"><span data-stu-id="284a6-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>

## <a name="see-also"></a><span data-ttu-id="284a6-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="284a6-136">See also</span></span>

* [<span data-ttu-id="284a6-137">Отладка с помощью символов</span><span class="sxs-lookup"><span data-stu-id="284a6-137">Debugging with symbols</span></span>](/windows/win32/dxtecharts/debugging-with-symbols)
* [<span data-ttu-id="284a6-138">Символы и переносимые PDB</span><span class="sxs-lookup"><span data-stu-id="284a6-138">Symbols and Portable PDBs</span></span>](./symbols.md)
