---
title: Проверка установленных версий .NET в Windows, Linux и macOS — .NET
description: Сведения о том, какие версии .NET установлены на компьютере. Сюда входит среда выполнения .NET и пакет SDK для .NET.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2fc12c8c398b1a74d623e53884df666f4d4b85f1
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851618"
---
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="6519c-104">Проверка того, установлена ли платформа .NET</span><span class="sxs-lookup"><span data-stu-id="6519c-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="6519c-105">Эта статья описывает, как проверить, какие версии среды выполнения .NET и пакета SDK установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="6519c-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="6519c-106">Если у вас есть интегрированная среда разработки, такая как Visual Studio или Visual Studio для Mac, то возможно, платформа .NET уже установлена.</span><span class="sxs-lookup"><span data-stu-id="6519c-106">If you have an integrated development environment, such as Visual Studio or Visual Studio for Mac, .NET may have already been installed.</span></span>

<span data-ttu-id="6519c-107">При установке пакета SDK устанавливается и соответствующая среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="6519c-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="6519c-108">Если любая команда из этой статьи завершается ошибкой, среда выполнения или пакет SDK не установлены.</span><span class="sxs-lookup"><span data-stu-id="6519c-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="6519c-109">Дополнительные сведения см. в статьях, посвященных установке в [Windows](windows.md), [macOS](macos.md) или [Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="6519c-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="6519c-110">Проверка версий пакета SDK</span><span class="sxs-lookup"><span data-stu-id="6519c-110">Check SDK versions</span></span>

<span data-ttu-id="6519c-111">Вы можете узнать, какие версии пакета SDK для .NET установлены, с помощью терминала.</span><span class="sxs-lookup"><span data-stu-id="6519c-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="6519c-112">Откройте терминал и выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="6519c-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="6519c-113">Вы получите результат, аналогичный приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="6519c-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="6519c-114">Проверка версий среды выполнения</span><span class="sxs-lookup"><span data-stu-id="6519c-114">Check runtime versions</span></span>

<span data-ttu-id="6519c-115">Вы можете узнать, какие версии среды выполнения .NET установлены, с помощью приведенной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="6519c-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="6519c-116">Вы получите результат, аналогичный приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="6519c-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="6519c-117">Проверка папок установки</span><span class="sxs-lookup"><span data-stu-id="6519c-117">Check for install folders</span></span>

<span data-ttu-id="6519c-118">Возможно, платформа .NET установлена, но не добавлена в переменную `PATH` для профиля операционной системы или пользователя.</span><span class="sxs-lookup"><span data-stu-id="6519c-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="6519c-119">В данном случае команды из предыдущих разделов могут не работать.</span><span class="sxs-lookup"><span data-stu-id="6519c-119">In this case, the commands from the previous sections may not work.</span></span> <span data-ttu-id="6519c-120">В качестве альтернативы можно проверить существование папок установки .NET.</span><span class="sxs-lookup"><span data-stu-id="6519c-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="6519c-121">При установке с помощью установщика или сценария .NET устанавливается в стандартную папку.</span><span class="sxs-lookup"><span data-stu-id="6519c-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="6519c-122">В большинстве случаев установщик или сценарий, который вы используете для установки .NET, предоставляет возможность установки в другую папку.</span><span class="sxs-lookup"><span data-stu-id="6519c-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="6519c-123">Если вы решили выполнить установить в другую папку, измените начало пути к папке.</span><span class="sxs-lookup"><span data-stu-id="6519c-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="6519c-124">**Исполняемый файл dotnet**</span><span class="sxs-lookup"><span data-stu-id="6519c-124">**dotnet executable**</span></span>\
<span data-ttu-id="6519c-125">_C:\\program files\\dotnet\\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="6519c-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="6519c-126">**Пакет SDK для .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-126">**.NET SDK**</span></span>\
<span data-ttu-id="6519c-127">_C:\\program files\\dotnet\\sdk\\{версия}\\_</span><span class="sxs-lookup"><span data-stu-id="6519c-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="6519c-128">**Среда выполнения .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-128">**.NET Runtime**</span></span>\
<span data-ttu-id="6519c-129">_C:\\program files\\dotnet\\shared\\{тип среды выполнения}\\{версия}\\_</span><span class="sxs-lookup"><span data-stu-id="6519c-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="6519c-130">**Исполняемый файл dotnet**</span><span class="sxs-lookup"><span data-stu-id="6519c-130">**dotnet executable**</span></span>\
<span data-ttu-id="6519c-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="6519c-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="6519c-132">**Пакет SDK для .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-132">**.NET SDK**</span></span>\
<span data-ttu-id="6519c-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="6519c-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="6519c-134">**Среда выполнения .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-134">**.NET Runtime**</span></span>\
<span data-ttu-id="6519c-135">_/home/user/share/dotnet/shared/{тип среды выполнения}/{версия}/_</span><span class="sxs-lookup"><span data-stu-id="6519c-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="6519c-136">**Исполняемый файл dotnet**</span><span class="sxs-lookup"><span data-stu-id="6519c-136">**dotnet executable**</span></span>\
<span data-ttu-id="6519c-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="6519c-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="6519c-138">**Пакет SDK для .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-138">**.NET SDK**</span></span>\
<span data-ttu-id="6519c-139">_/usr/local/share/dotnet/sdk/{версия}/_</span><span class="sxs-lookup"><span data-stu-id="6519c-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="6519c-140">**Среда выполнения .NET**</span><span class="sxs-lookup"><span data-stu-id="6519c-140">**.NET Runtime**</span></span>\
<span data-ttu-id="6519c-141">_/usr/local/share/dotnet/shared/{тип среды выполнения}/{версия}/_</span><span class="sxs-lookup"><span data-stu-id="6519c-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="6519c-142">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="6519c-142">More information</span></span>

<span data-ttu-id="6519c-143">Версии пакета SDK и среды выполнения можно просмотреть с помощью команды `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="6519c-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="6519c-144">Вы также получите другие сведения о среде, такие как версия операционной системы и идентификатор среды выполнения (RID).</span><span class="sxs-lookup"><span data-stu-id="6519c-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6519c-145">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="6519c-145">Next steps</span></span>

- <span data-ttu-id="6519c-146">[Установка среды выполнения .NET и пакета SDK для Windows](windows.md).</span><span class="sxs-lookup"><span data-stu-id="6519c-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="6519c-147">[Установка среды выполнения .NET и пакета SDK для macOS](macos.md).</span><span class="sxs-lookup"><span data-stu-id="6519c-147">[Install the .NET Runtime and SDK for macOS](macos.md).</span></span>
- <span data-ttu-id="6519c-148">[Установка среды выполнения .NET и пакета SDK для Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="6519c-148">[Install the .NET Runtime and SDK for Linux](linux.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6519c-149">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6519c-149">See also</span></span>

- [<span data-ttu-id="6519c-150">Определение установленных версий платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6519c-150">Determine which .NET Framework versions are installed</span></span>](../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)
