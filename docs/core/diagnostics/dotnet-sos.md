---
title: Средство диагностики dotnet-sos — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-sos для управления расширением отладчика SOS, которое используется с собственными отладчиками в Windows и Linux.
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765011"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="536e4-103">Установщик SOS (dotnet-sos)</span><span class="sxs-lookup"><span data-stu-id="536e4-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="536e4-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="536e4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="536e4-105">Установка</span><span class="sxs-lookup"><span data-stu-id="536e4-105">Install</span></span>

<span data-ttu-id="536e4-106">Есть два способа загрузки и установки `dotnet-sos`:</span><span class="sxs-lookup"><span data-stu-id="536e4-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="536e4-107">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="536e4-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="536e4-108">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-sos) `dotnet-sos`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="536e4-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="536e4-109">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="536e4-109">**Direct download:**</span></span>

  <span data-ttu-id="536e4-110">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="536e4-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="536e4-111">OS</span><span class="sxs-lookup"><span data-stu-id="536e4-111">OS</span></span>  | <span data-ttu-id="536e4-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="536e4-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="536e4-113">Windows</span><span class="sxs-lookup"><span data-stu-id="536e4-113">Windows</span></span> | <span data-ttu-id="536e4-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="536e4-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="536e4-115">macOS</span><span class="sxs-lookup"><span data-stu-id="536e4-115">macOS</span></span>   | [<span data-ttu-id="536e4-116">x64</span><span class="sxs-lookup"><span data-stu-id="536e4-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="536e4-117">Linux</span><span class="sxs-lookup"><span data-stu-id="536e4-117">Linux</span></span>   | <span data-ttu-id="536e4-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="536e4-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="536e4-119">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="536e4-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="536e4-120">Описание</span><span class="sxs-lookup"><span data-stu-id="536e4-120">Description</span></span>

<span data-ttu-id="536e4-121">Глобальное средство `dotnet-sos` устанавливает [расширение отладчика SOS](sos-debugging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="536e4-121">The `dotnet-sos` global tool installs the [SOS debugger extension](sos-debugging-extension.md).</span></span> <span data-ttu-id="536e4-122">Это расширение позволяет проверять управляемое состояние .NET Core из отладчиков машинного кода, таких как lldb и windbg.</span><span class="sxs-lookup"><span data-stu-id="536e4-122">This extension lets you inspect managed .NET Core state from native debuggers like lldb and windbg.</span></span>

> [!NOTE]
> <span data-ttu-id="536e4-123">Установка SOS с помощью средства `dotnet-sos` требуется только в Linux или macOS.</span><span class="sxs-lookup"><span data-stu-id="536e4-123">Installing SOS via the `dotnet-sos` tool is only needed on Linux or macOS.</span></span>  <span data-ttu-id="536e4-124">Это также может потребоваться в Windows, если вы используете старые средства отладки.</span><span class="sxs-lookup"><span data-stu-id="536e4-124">It may also be needed on Windows if you're using older debugging tools.</span></span> <span data-ttu-id="536e4-125">Последние версии [Отладчика Windows](/windows-hardware/drivers/debugger/debugger-download-tools) (версии WinDbg или CDB >= 10.0.18317.1001) автоматически загружают SOS из коллекции расширений Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="536e4-125">Recent versions of the [Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 of WinDbg or cdb) load SOS automatically from the Microsoft extension gallery.</span></span>  

## <a name="options"></a><span data-ttu-id="536e4-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="536e4-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="536e4-127">Отображение сведений о версии.</span><span class="sxs-lookup"><span data-stu-id="536e4-127">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="536e4-128">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="536e4-128">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="536e4-129">dotnet-sos install</span><span class="sxs-lookup"><span data-stu-id="536e4-129">dotnet-sos install</span></span>

<span data-ttu-id="536e4-130">Установка [расширения SOS](sos-debugging-extension.md) локально для отладки процессов .NET Core.</span><span class="sxs-lookup"><span data-stu-id="536e4-130">Installs the [SOS extension](sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="536e4-131">В macOS и Linux файл *LLDBINIT* будет обновлен таким образом, чтобы расширение загружалось автоматически при запуске lldb.</span><span class="sxs-lookup"><span data-stu-id="536e4-131">On macOS and Linux, the *.lldbinit* file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="536e4-132">При установке SOS в Windows с более старыми средствами отладки (ниже версии 10.0.18317.1001) необходимо вручную загрузить расширение в WinDbg или CDB, запустив `.load %USERPROFILE%\.dotnet\sos\sos.dll` в отладчике.</span><span class="sxs-lookup"><span data-stu-id="536e4-132">If you're installing SOS on Windows with older debugging tools (prior to version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="536e4-133">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="536e4-133">Synopsis</span></span>

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a><span data-ttu-id="536e4-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="536e4-134">Options</span></span>

- **`--architecture <arch>`**

  <span data-ttu-id="536e4-135">Задает архитектуру процессора для устанавливаемых двоичных файлов SOS.</span><span class="sxs-lookup"><span data-stu-id="536e4-135">Specifies the processor architecture of the SOS binaries to install.</span></span> <span data-ttu-id="536e4-136">По умолчанию средство `dotnet-sos` устанавливает архитектуру хост-компьютера.</span><span class="sxs-lookup"><span data-stu-id="536e4-136">By default, `dotnet-sos` installs the architecture of the host machine.</span></span> <span data-ttu-id="536e4-137">Используйте этот параметр, если необходимо установить SOS для архитектуры, отличной от архитектуры узла dotnet.</span><span class="sxs-lookup"><span data-stu-id="536e4-137">Use this option when you want to install SOS for an architecture that's different from the dotnet host architecture.</span></span> <span data-ttu-id="536e4-138">Например, если вы запускаете двоичные файлы Arm32 на узле Arm64, необходимо установить SOS командой `dotnet-sos install --architecture Arm`.</span><span class="sxs-lookup"><span data-stu-id="536e4-138">For example, if you're running Arm32 binaries from an Arm64 host, you will need to install SOS with `dotnet-sos install --architecture Arm`.</span></span>

  <span data-ttu-id="536e4-139">Доступны следующие архитектуры:</span><span class="sxs-lookup"><span data-stu-id="536e4-139">The following architectures are available:</span></span>

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="536e4-140">dotnet-sos uninstall</span><span class="sxs-lookup"><span data-stu-id="536e4-140">dotnet-sos uninstall</span></span>

<span data-ttu-id="536e4-141">Удаление [расширения SOS](sos-debugging-extension.md), а в Linux и macOS также удаление из конфигурации lldb.</span><span class="sxs-lookup"><span data-stu-id="536e4-141">Uninstalls the [SOS extension](sos-debugging-extension.md) and, on Linux and macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="536e4-142">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="536e4-142">Synopsis</span></span>

```console
dotnet-sos uninstall
```
