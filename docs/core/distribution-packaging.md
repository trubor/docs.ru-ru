---
title: Упаковка дистрибутивов .NET
description: Сведения о создании пакетов .NET, присвоении им имен и управлении их версиями для распространения.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 93d040064eb739b3bd045fdb16b356732353ddc8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216308"
---
# <a name="net-distribution-packaging"></a><span data-ttu-id="c6c02-103">Упаковка дистрибутивов .NET</span><span class="sxs-lookup"><span data-stu-id="c6c02-103">.NET distribution packaging</span></span>

<span data-ttu-id="c6c02-104">Поскольку .NET 5 (и .NET Core) и более поздних версий становится доступным на все большем количестве платформ, полезно знать, как создавать пакеты, присваивать им имена и управлять их версиями.</span><span class="sxs-lookup"><span data-stu-id="c6c02-104">As .NET 5 (and .NET Core) and later versions become available on more and more platforms, it's useful to learn how to package, name, and version apps and libraries that use it.</span></span> <span data-ttu-id="c6c02-105">Таким образом издатели пакетов смогут обеспечить согласованную работу независимо от платформы, выбранной пользователями для запуска .NET.</span><span class="sxs-lookup"><span data-stu-id="c6c02-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="c6c02-106">Эта статья пригодится пользователям, которые:</span><span class="sxs-lookup"><span data-stu-id="c6c02-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="c6c02-107">выполняют сборку .NET из исходного кода;</span><span class="sxs-lookup"><span data-stu-id="c6c02-107">Attempting to build .NET from source.</span></span>
- <span data-ttu-id="c6c02-108">хотят внести в .NET CLI изменения, способные повлиять на итоговый макет или создаваемые пакеты.</span><span class="sxs-lookup"><span data-stu-id="c6c02-108">Wanting to make changes to the .NET CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="c6c02-109">Структура диска</span><span class="sxs-lookup"><span data-stu-id="c6c02-109">Disk layout</span></span>

<span data-ttu-id="c6c02-110">Установка .NET включает несколько компонентов, которые располагаются в файловой системе следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c6c02-110">When installed, .NET consists of several components that are laid out as follows in the file system:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="c6c02-111">(1) **dotnet**: основное приложение (также называется "мультиплексором") выполняет две функции: активирует среду выполнения для запуска приложения и активирует пакет SDK для отправки в него команд.</span><span class="sxs-lookup"><span data-stu-id="c6c02-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="c6c02-112">Основное приложение представляет собой исполняемый файл в машинном коде (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="c6c02-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="c6c02-113">Хотя основное приложение одно, большинство остальных компонентов хранятся в каталогах версий (2, 3, 5, 6).</span><span class="sxs-lookup"><span data-stu-id="c6c02-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="c6c02-114">Это значит, что в системе могут быть представлены сразу несколько версий, поскольку разные версии компонентов устанавливаются параллельно.</span><span class="sxs-lookup"><span data-stu-id="c6c02-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="c6c02-115">(2) **host/fxr/\<fxr version>** содержит логику разрешений платформы, используемую основным приложением.</span><span class="sxs-lookup"><span data-stu-id="c6c02-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="c6c02-116">Основное приложение использует новейшую установленную версию hostfxr.</span><span class="sxs-lookup"><span data-stu-id="c6c02-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="c6c02-117">Hostfxr отвечает за выбор необходимой среды выполнения при запуске приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="c6c02-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET application.</span></span> <span data-ttu-id="c6c02-118">Например, приложение, созданное для среды выполнения .NET Core 2.0.0, использует версию 2.0.5, если версия 2.0.0 недоступна.</span><span class="sxs-lookup"><span data-stu-id="c6c02-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="c6c02-119">Аналогично hostfxr выбирает соответствующую версию SDK во время разработки.</span><span class="sxs-lookup"><span data-stu-id="c6c02-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="c6c02-120">(3) **sdk/\<sdk version>** пакет SDK (также называется инструментарием) — это набор управляемых средств, которые используются для написания кода и сборки библиотек и приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="c6c02-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET libraries and applications.</span></span> <span data-ttu-id="c6c02-121">Пакет SDK содержит .NET CLI, компиляторы языков с управляемым кодом, MSBuild, а также соответствующие задачи и целевые объекты сборки, NuGet, новые шаблоны проектов и т. д.</span><span class="sxs-lookup"><span data-stu-id="c6c02-121">The SDK includes the .NET CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="c6c02-122">(4) **sdk/NuGetFallbackFolder** содержит кэш пакетов NuGet, которые пакет SDK использует во время операции восстановления, например при выполнении `dotnet restore` или `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="c6c02-123">Эта папка используется только в версиях, предшествующих .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6c02-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="c6c02-124">Ее невозможно создать из источника, так как она содержит предварительно созданные двоичные ресурсы из `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="c6c02-125">Папка **shared** содержит платформы.</span><span class="sxs-lookup"><span data-stu-id="c6c02-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="c6c02-126">Общая платформа предоставляет набор библиотек в центральном расположении таким образом, что они могут использоваться другими приложениями.</span><span class="sxs-lookup"><span data-stu-id="c6c02-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="c6c02-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** эта платформа содержит среду выполнения .NET и вспомогательные управляемые библиотеки.</span><span class="sxs-lookup"><span data-stu-id="c6c02-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="c6c02-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** содержит библиотеки ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6c02-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="c6c02-129">Библиотеки в каталоге `Microsoft.AspNetCore.App` разрабатываются и поддерживаются как часть проекта .NET.</span><span class="sxs-lookup"><span data-stu-id="c6c02-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET project.</span></span> <span data-ttu-id="c6c02-130">Библиотеки в каталоге `Microsoft.AspNetCore.All` представляют собой подмножество, которое также содержит сторонние библиотеки.</span><span class="sxs-lookup"><span data-stu-id="c6c02-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="c6c02-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** содержит библиотеки для классических приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="c6c02-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="c6c02-132">Не используется на платформах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="c6c02-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="c6c02-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** — тексты лицензий .NET и лицензий библиотек сторонних производителей, используемых в .NET, соответственно.</span><span class="sxs-lookup"><span data-stu-id="c6c02-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET license and licenses of third-party libraries used in .NET, respectively.</span></span>

- <span data-ttu-id="c6c02-134">(9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` — это страница руководства по dotnet.</span><span class="sxs-lookup"><span data-stu-id="c6c02-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="c6c02-135">`dotnet` представляет собой символическую ссылку на основное приложение dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="c6c02-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="c6c02-136">Эти файлы устанавливаются в типичные расположения для системной интеграции.</span><span class="sxs-lookup"><span data-stu-id="c6c02-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="c6c02-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** описывают API версии `x.y` .NET и ASP.NET соответственно.</span><span class="sxs-lookup"><span data-stu-id="c6c02-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET and ASP.NET Core respectively.</span></span> <span data-ttu-id="c6c02-138">Эти пакеты используются при компиляции для этих целевых версий.</span><span class="sxs-lookup"><span data-stu-id="c6c02-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="c6c02-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span><span class="sxs-lookup"><span data-stu-id="c6c02-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="c6c02-140">содержит собственный двоичный файл для платформы `rid`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="c6c02-141">Этот двоичный файл представляет собой шаблон, используемый при компиляции приложения .NET в собственный двоичный файл для этой платформы.</span><span class="sxs-lookup"><span data-stu-id="c6c02-141">This binary is a template when compiling a .NET application into a native binary for that platform.</span></span>

- <span data-ttu-id="c6c02-142">(14) **Microsoft.WindowsDesktop.App.Ref** описывает API версии `x.y` для классических приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="c6c02-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="c6c02-143">Эти файлы используются при компиляции для этого целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="c6c02-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="c6c02-144">Не используется на платформах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="c6c02-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="c6c02-145">(15) **NETStandard.Library.Ref** описывает API `x.y` netstandard.</span><span class="sxs-lookup"><span data-stu-id="c6c02-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="c6c02-146">Эти файлы используются при компиляции для этого целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="c6c02-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="c6c02-147">(16) **/etc/dotnet/install_location** — это файл, содержащий полный путь для `{dotnet_root}`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="c6c02-148">Путь может заканчиваться новой строкой.</span><span class="sxs-lookup"><span data-stu-id="c6c02-148">The path may end with a newline.</span></span> <span data-ttu-id="c6c02-149">Если корневым элементом является `/usr/share/dotnet`, добавлять этот файл не нужно.</span><span class="sxs-lookup"><span data-stu-id="c6c02-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="c6c02-150">(17) **templates** содержат шаблоны, используемые пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="c6c02-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="c6c02-151">Например, `dotnet new` находит шаблоны проектов.</span><span class="sxs-lookup"><span data-stu-id="c6c02-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="c6c02-152">Папки, помеченные `(*)`, используются несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="c6c02-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="c6c02-153">Для некоторых форматов пакетов (например, `rpm`) требуется специальная обработка таких папок.</span><span class="sxs-lookup"><span data-stu-id="c6c02-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="c6c02-154">Этим должен заниматься специалист по обслуживанию пакетов.</span><span class="sxs-lookup"><span data-stu-id="c6c02-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="c6c02-155">Рекомендуемые пакеты</span><span class="sxs-lookup"><span data-stu-id="c6c02-155">Recommended packages</span></span>

<span data-ttu-id="c6c02-156">Управление версиями .NET основано на номерах версий компонентов среды выполнения вида `[major].[minor]`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-156">.NET versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="c6c02-157">Версия пакета SDK использует тот же `[major].[minor]` и имеет независимый номер `[patch]`, отражающий функцию и номер исправления для пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="c6c02-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="c6c02-158">Пример: Пакет SDK версии 2.2.302 — это второй выпуск исправления для третьей функции пакета SDK, который поддерживает среду выполнения версии 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6c02-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="c6c02-159">Дополнительные сведения о принципах управления версиями см. в разделе [Общие сведения об управлении версиями .NET](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="c6c02-159">For more information about how versioning works, see [.NET versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="c6c02-160">Некоторые пакеты содержат часть номера версии в своем имени.</span><span class="sxs-lookup"><span data-stu-id="c6c02-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="c6c02-161">Это позволяет устанавливать определенную версию.</span><span class="sxs-lookup"><span data-stu-id="c6c02-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="c6c02-162">Остальная часть версии в имя версии не включается.</span><span class="sxs-lookup"><span data-stu-id="c6c02-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="c6c02-163">Это позволяет диспетчеру пакетов операционной системы обновлять пакеты (например, автоматически устанавливать исправления безопасности).</span><span class="sxs-lookup"><span data-stu-id="c6c02-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="c6c02-164">Поддерживаемые диспетчеры пакетов рассчитаны на Linux.</span><span class="sxs-lookup"><span data-stu-id="c6c02-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="c6c02-165">Далее перечислены рекомендуемые пакеты.</span><span class="sxs-lookup"><span data-stu-id="c6c02-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="c6c02-166">`dotnet-sdk-[major].[minor]` — устанавливает новейшую версию пакета SDK для конкретной среды выполнения</span><span class="sxs-lookup"><span data-stu-id="c6c02-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="c6c02-167">**Версия:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="c6c02-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="c6c02-168">**Пример:** dotnet-sdk-2.1</span><span class="sxs-lookup"><span data-stu-id="c6c02-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="c6c02-169">**Содержит:** (3),(4)</span><span class="sxs-lookup"><span data-stu-id="c6c02-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="c6c02-170">**Зависимости:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="c6c02-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="c6c02-171">`aspnetcore-runtime-[major].[minor]` — устанавливает конкретную среду выполнения ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6c02-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="c6c02-172">**Версия:** \<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="c6c02-173">**Пример:** aspnetcore-runtime-2.1</span><span class="sxs-lookup"><span data-stu-id="c6c02-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="c6c02-174">**Содержит:** (6)</span><span class="sxs-lookup"><span data-stu-id="c6c02-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="c6c02-175">**Зависимости:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="c6c02-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="c6c02-176">`dotnet-runtime-deps-[major].[minor]` _(Необязательно)_  — устанавливает зависимости для запуска автономных приложений</span><span class="sxs-lookup"><span data-stu-id="c6c02-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="c6c02-177">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-178">**Пример:** dotnet-runtime-deps-2.1</span><span class="sxs-lookup"><span data-stu-id="c6c02-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="c6c02-179">**Зависимости:** _зависимости, зависящие от распределения_</span><span class="sxs-lookup"><span data-stu-id="c6c02-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="c6c02-180">`dotnet-runtime-[major].[minor]` — устанавливает конкретную среду выполнения</span><span class="sxs-lookup"><span data-stu-id="c6c02-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="c6c02-181">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-182">**Пример:** dotnet-runtime-2.1</span><span class="sxs-lookup"><span data-stu-id="c6c02-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="c6c02-183">**Содержит:** (5)</span><span class="sxs-lookup"><span data-stu-id="c6c02-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="c6c02-184">**Зависимости:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="c6c02-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="c6c02-185">`dotnet-hostfxr-[major].[minor]` — зависимость</span><span class="sxs-lookup"><span data-stu-id="c6c02-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="c6c02-186">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-187">**Пример:** dotnet-hostfxr-3.0</span><span class="sxs-lookup"><span data-stu-id="c6c02-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="c6c02-188">**Содержит:** (2)</span><span class="sxs-lookup"><span data-stu-id="c6c02-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="c6c02-189">**Зависимости:** `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="c6c02-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="c6c02-190">`dotnet-host` — зависимость</span><span class="sxs-lookup"><span data-stu-id="c6c02-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="c6c02-191">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-192">**Пример:** dotnet-host</span><span class="sxs-lookup"><span data-stu-id="c6c02-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="c6c02-193">**Содержит:** (1),(8),(9),(10),(16)</span><span class="sxs-lookup"><span data-stu-id="c6c02-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="c6c02-194">`dotnet-apphost-pack-[major].[minor]` — зависимость</span><span class="sxs-lookup"><span data-stu-id="c6c02-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="c6c02-195">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-196">**Содержит:** (13)</span><span class="sxs-lookup"><span data-stu-id="c6c02-196">**Contains:** (13)</span></span>

- <span data-ttu-id="c6c02-197">`dotnet-targeting-pack-[major].[minor]` — нацеливание на непоследнюю среду выполнения</span><span class="sxs-lookup"><span data-stu-id="c6c02-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="c6c02-198">**Версия:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="c6c02-199">**Содержит:** (12)</span><span class="sxs-lookup"><span data-stu-id="c6c02-199">**Contains:** (12)</span></span>

- <span data-ttu-id="c6c02-200">`aspnetcore-targeting-pack-[major].[minor]` — нацеливание на непоследнюю среду выполнения</span><span class="sxs-lookup"><span data-stu-id="c6c02-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="c6c02-201">**Версия:** \<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="c6c02-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="c6c02-202">**Содержит:** (11)</span><span class="sxs-lookup"><span data-stu-id="c6c02-202">**Contains:** (11)</span></span>

- <span data-ttu-id="c6c02-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` — нацеливание на версию netstandard</span><span class="sxs-lookup"><span data-stu-id="c6c02-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="c6c02-204">**Версия:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="c6c02-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="c6c02-205">**Содержит:** (15)</span><span class="sxs-lookup"><span data-stu-id="c6c02-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="c6c02-206">**Версия:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="c6c02-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="c6c02-207">**Содержит:** (15)</span><span class="sxs-lookup"><span data-stu-id="c6c02-207">**Contains:** (15)</span></span>

<span data-ttu-id="c6c02-208">Для использования `dotnet-runtime-deps-[major].[minor]` необходимо понимать _зависимости для конкретных дистрибутивов_.</span><span class="sxs-lookup"><span data-stu-id="c6c02-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="c6c02-209">Так как система сборки дистрибутива может наследовать этот пакет автоматически, он является необязательным. В этом случае эти зависимости добавляются прямо в пакет `dotnet-runtime-[major].[minor]`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="c6c02-210">Если содержимое пакета находится в папке, которой присвоена версия, имя пакета `[major].[minor]` совпадает с именем этой папки.</span><span class="sxs-lookup"><span data-stu-id="c6c02-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="c6c02-211">Для всех пакетов, кроме `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, также обязательно совпадение версий .NET.</span><span class="sxs-lookup"><span data-stu-id="c6c02-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET version.</span></span>

<span data-ttu-id="c6c02-212">Для зависимостей между пакетами должно действовать следующее применимое к версиям правило: _больше или равно_.</span><span class="sxs-lookup"><span data-stu-id="c6c02-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="c6c02-213">Например, для `dotnet-sdk-2.2:2.2.401` требуется `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="c6c02-214">В этом случае пользователь может обновить свою установку с помощью корневого пакета (например, `dnf update dotnet-sdk-2.2`).</span><span class="sxs-lookup"><span data-stu-id="c6c02-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="c6c02-215">Большинство дистрибутивов требуют построения из источника всех артефактов.</span><span class="sxs-lookup"><span data-stu-id="c6c02-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="c6c02-216">Это определенным образом влияет на пакеты:</span><span class="sxs-lookup"><span data-stu-id="c6c02-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="c6c02-217">Сторонние библиотеки в каталоге `shared/Microsoft.AspNetCore.All` нельзя собрать из исходного хода.</span><span class="sxs-lookup"><span data-stu-id="c6c02-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="c6c02-218">Поэтому эта папка исключена из пакета `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="c6c02-219">Папка `NuGetFallbackFolder` заполняется двоичными артефактами с сайта `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="c6c02-220">Она должна оставаться пустой.</span><span class="sxs-lookup"><span data-stu-id="c6c02-220">It should remain empty.</span></span>

<span data-ttu-id="c6c02-221">Несколько пакетов `dotnet-sdk` могут предоставлять одни и те же файлы для каталога `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="c6c02-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="c6c02-222">Чтобы не возникали проблемы с диспетчером пакетов, эти файлы (контрольная сумма, дата изменения и т. д.) должны быть идентичны.</span><span class="sxs-lookup"><span data-stu-id="c6c02-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="c6c02-223">Построение пакетов</span><span class="sxs-lookup"><span data-stu-id="c6c02-223">Building packages</span></span>

<span data-ttu-id="c6c02-224">Репозиторий [dotnet/source-build](https://github.com/dotnet/source-build) содержит инструкции по созданию архива TAR с исходным кодом пакета SDK для .NET и всех его компонентов.</span><span class="sxs-lookup"><span data-stu-id="c6c02-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET SDK and all its components.</span></span> <span data-ttu-id="c6c02-225">Выход репозитория, построенного из источника, соответствует виду, описанному в первом разделе этой статьи.</span><span class="sxs-lookup"><span data-stu-id="c6c02-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
