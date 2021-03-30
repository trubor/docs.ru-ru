---
title: Скрипты dotnet-install
description: Сведения о скриптах dotnet-install, которые служат для установки пакета SDK для .NET и общей среды выполнения.
ms.date: 09/22/2020
ms.openlocfilehash: 45b5a15bdbaa3f3167dd434e2600e33b69dc9b85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875165"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="7cb4a-103">Справка по скриптам dotnet-install</span><span class="sxs-lookup"><span data-stu-id="7cb4a-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="7cb4a-104">name</span><span class="sxs-lookup"><span data-stu-id="7cb4a-104">Name</span></span>

<span data-ttu-id="7cb4a-105">`dotnet-install.ps1` | `dotnet-install.sh` — скрипт, используемый для установки общей среды выполнения и пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7cb4a-106">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="7cb4a-106">Synopsis</span></span>

<span data-ttu-id="7cb4a-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="7cb4a-108">Linux или MacOS:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="7cb4a-109">Так как bash-скрипт также считывает параметры PowerShell, их можно использовать с этим скриптом в системах Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="7cb4a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="7cb4a-110">Description</span></span>

<span data-ttu-id="7cb4a-111">Скрипты `dotnet-install` выполняют установку пакета SDK для .NET без прав администратора. Этот пакет включает общую среду выполнения и .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-111">The `dotnet-install` scripts perform a non-admin installation of the .NET SDK, which includes the .NET CLI and the shared runtime.</span></span> <span data-ttu-id="7cb4a-112">Существует два скрипта:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-112">There are two scripts:</span></span>

* <span data-ttu-id="7cb4a-113">Скрипт PowerShell, который используется в Windows.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="7cb4a-114">Скрипт bash, который выполняется в Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-114">A bash script that works on Linux/macOS.</span></span>

> [!NOTE]
> <span data-ttu-id="7cb4a-115">.NET собирает данные телеметрии.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-115">.NET collects telemetry data.</span></span> <span data-ttu-id="7cb4a-116">Дополнительные сведения и о том, как отказаться от этого, см. в разделе [Телеметрия пакета SDK для .NET](telemetry.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-116">To learn more and how to opt out, see [.NET SDK telemetry](telemetry.md).</span></span>

### <a name="purpose"></a><span data-ttu-id="7cb4a-117">Цель</span><span class="sxs-lookup"><span data-stu-id="7cb4a-117">Purpose</span></span>

 <span data-ttu-id="7cb4a-118">Скрипты предназначены для использования в сценариях непрерывной интеграции (CI), если:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-118">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="7cb4a-119">Пакет SDK должен быть установлен без участия пользователя и без использования прав администратора.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-119">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="7cb4a-120">Установка пакета SDK не обязательно должна выполняться в ходе нескольких выполнений непрерывной интеграции.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-120">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="7cb4a-121">Типичная последовательность событий:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-121">The typical sequence of events:</span></span>
  * <span data-ttu-id="7cb4a-122">запускается непрерывная интеграция;</span><span class="sxs-lookup"><span data-stu-id="7cb4a-122">CI is triggered.</span></span>
  * <span data-ttu-id="7cb4a-123">в ходе непрерывной интеграции устанавливается пакет SDK с помощью одного из этих скриптов;</span><span class="sxs-lookup"><span data-stu-id="7cb4a-123">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="7cb4a-124">непрерывная интеграция завершается, временные данные, включая установку пакета SDK, удаляются.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-124">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="7cb4a-125">Чтобы настроить среду разработки или запустить приложения, используйте установщики вместо этих скриптов.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-125">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="7cb4a-126">Рекомендуемая версия</span><span class="sxs-lookup"><span data-stu-id="7cb4a-126">Recommended version</span></span>

<span data-ttu-id="7cb4a-127">Мы рекомендуем использовать стабильную версию скриптов.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-127">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="7cb4a-128">Bash (Linux или macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="7cb4a-128">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="7cb4a-129">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="7cb4a-129">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="7cb4a-130">Поведение скрипта</span><span class="sxs-lookup"><span data-stu-id="7cb4a-130">Script behavior</span></span>

<span data-ttu-id="7cb4a-131">Оба скрипта выполняют одни и те же функции.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-131">Both scripts have the same behavior.</span></span> <span data-ttu-id="7cb4a-132">Они скачивают файл ZIP или TAR из места сборки CLI, а затем осуществляют установку в расположении по умолчанию или расположении, заданном параметром `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-132">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="7cb4a-133">По умолчанию скрипты установки скачивают и устанавливают пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-133">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="7cb4a-134">Если вы хотите получить только общую среду выполнения, укажите аргумент `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-134">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="7cb4a-135">По умолчанию скрипт добавляет место установки в переменную $PATH для текущего сеанса.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-135">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="7cb4a-136">Переопределите это поведение по умолчанию, указав аргумент `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-136">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="7cb4a-137">Скрипт не задает переменную среды `DOTNET_ROOT`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-137">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="7cb4a-138">Перед запуском скрипта установите все необходимые [зависимости](../install/windows.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-138">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="7cb4a-139">Вы можете установить конкретную версию с помощью аргумента `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-139">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="7cb4a-140">Версию следует указывать в виде номера из трех частей, например `2.1.0`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-140">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="7cb4a-141">Если версия не указана, скрипт устанавливает версию `latest`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-141">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="7cb4a-142">Скрипты установки не обновляют реестр в Windows.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-142">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="7cb4a-143">Они просто скачивают двоичные ZIP-файлы и копируют их в папку.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-143">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="7cb4a-144">Чтобы значения разделов реестра обновлялись, используйте установщики .NET.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-144">If you want registry key values to be updated, use the .NET installers.</span></span>

## <a name="options"></a><span data-ttu-id="7cb4a-145">Параметры</span><span class="sxs-lookup"><span data-stu-id="7cb4a-145">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="7cb4a-146">Архитектура устанавливаемых двоичных файлов .NET.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-146">Architecture of the .NET binaries to install.</span></span> <span data-ttu-id="7cb4a-147">Допустимые значения: `<auto>`, `amd64`, `x64`, `x86`, `arm64` и `arm`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-147">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="7cb4a-148">Значение по умолчанию — `<auto>`, представляющее текущую используемую архитектуру ОС.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-148">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="7cb4a-149">Указывает URL-адрес для веб-канала Azure этого установщика.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-149">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="7cb4a-150">Изменять это значение не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-150">We recommended that you don't change this value.</span></span> <span data-ttu-id="7cb4a-151">Значение по умолчанию — `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-151">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="7cb4a-152">Указывает исходный канал для установки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-152">Specifies the source channel for the installation.</span></span> <span data-ttu-id="7cb4a-153">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-153">The possible values are:</span></span>

  - <span data-ttu-id="7cb4a-154">`Current` — самый последний выпуск.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-154">`Current` - Most current release.</span></span>
  - <span data-ttu-id="7cb4a-155">`LTS` — канал долгосрочной поддержки (самый последний поддерживаемый выпуск).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-155">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="7cb4a-156">Версия из двух частей в формате X.Y, который представляет конкретный выпуск (например, `2.1` или `3.0`).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-156">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="7cb4a-157">Имя ветви, например `release/3.1.1xx` или `master` (для ночных выпусков).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-157">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="7cb4a-158">Используйте этот параметр для установки версии из канала предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-158">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="7cb4a-159">Используйте имя канала, указанное в разделе [Установщики и двоичные файлы](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-159">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="7cb4a-160">Значение по умолчанию — `LTS`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-160">The default value is `LTS`.</span></span> <span data-ttu-id="7cb4a-161">Дополнительные сведения о каналах поддержки .NET см. на странице о [политике поддержки .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-161">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="7cb4a-162">Если задано, скрипт не будет выполнять установку.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-162">If set, the script won't perform the installation.</span></span> <span data-ttu-id="7cb4a-163">Вместо этого отобразится командная строка для согласованной установки запрошенной в настоящее время версии .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-163">Instead, it displays what command line to use to consistently install the currently requested version of the .NET CLI.</span></span> <span data-ttu-id="7cb4a-164">Например, если указать версию `latest`, он отображает ссылку для определенной версии, чтобы эту команду можно было детерминировано использовать в скрипте сборки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-164">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="7cb4a-165">Кроме того, он отображает расположение двоичного файла, если вы хотите выполнить скачивание или установку самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-165">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="7cb4a-166">Используется в качестве строки запроса для добавления в веб-канал Azure.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-166">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="7cb4a-167">Позволяет изменять URL-адрес для использования учетных записей хранилища BLOB-объектов, не являющихся общедоступными.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-167">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="7cb4a-168">Выводит справку для скрипта.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-168">Prints out help for the script.</span></span> <span data-ttu-id="7cb4a-169">Применяется только к скрипту bash.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-169">Applies only to bash script.</span></span> <span data-ttu-id="7cb4a-170">Для PowerShell используется `Get-Help ./dotnet-install.ps1`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-170">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="7cb4a-171">Указывает путь установки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-171">Specifies the installation path.</span></span> <span data-ttu-id="7cb4a-172">Если такого пути нет, создается каталог.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-172">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="7cb4a-173">Значение по умолчанию — *%LocalAppData%\Microsoft\dotnet* в Windows и */usr/share/dotnet* в Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-173">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="7cb4a-174">Двоичные файлы помещаются непосредственно в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-174">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="7cb4a-175">Указывает путь к файлу [global.json](global-json.md), который будет использоваться для определения версии пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-175">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="7cb4a-176">В файле *global.json* должно быть значение для `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-176">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="7cb4a-177">Отключает загрузку из [сети доставки содержимого Microsoft Azure (CDN)](/azure/cdn/cdn-overview) и напрямую использует некэшированный веб-канал.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-177">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="7cb4a-178">Если значение задано, папка установки не экспортируется в путь текущего сеанса.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-178">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="7cb4a-179">По умолчанию скрипт изменит значение PATH, благодаря чему .NET CLI становится доступным сразу после установки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-179">By default, the script modifies the PATH, which makes the .NET CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="7cb4a-180">Если значение задано, установщик использует прокси-сервер для выполнения веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-180">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="7cb4a-181">(Допустимо только для Windows.)</span><span class="sxs-lookup"><span data-stu-id="7cb4a-181">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="7cb4a-182">Если задано значение `ProxyAddress`, предоставляется список URL-адресов, разделенных запятыми, которые будут обходить прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-182">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="7cb4a-183">(Допустимо только для Windows.)</span><span class="sxs-lookup"><span data-stu-id="7cb4a-183">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="7cb4a-184">Если задано, установщик использует учетные данные текущего пользователя при использовании адреса прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-184">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="7cb4a-185">(Допустимо только для Windows.)</span><span class="sxs-lookup"><span data-stu-id="7cb4a-185">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="7cb4a-186">Устанавливается только общая среда выполнения, а не весь пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-186">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="7cb4a-187">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-187">The possible values are:</span></span>

  - <span data-ttu-id="7cb4a-188">`dotnet` — общая среда выполнения `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-188">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="7cb4a-189">`aspnetcore` — общая среда выполнения `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-189">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="7cb4a-190">`windowsdesktop` — общая среда выполнения `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-190">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- <span data-ttu-id="7cb4a-191">**`--runtime-id <RID>` [Не рекомендуется]**</span><span class="sxs-lookup"><span data-stu-id="7cb4a-191">**`--runtime-id <RID>` [Deprecated]**</span></span>

  <span data-ttu-id="7cb4a-192">Указывает [идентификатор среды выполнения](../rid-catalog.md), для которого устанавливаются средства.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-192">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="7cb4a-193">Используйте значение `linux-x64` для переносимых файлов Linux.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-193">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="7cb4a-194">(Допустимо только для Linux и macOS и для версий более ранних, чем .NET Core 2.1.)</span><span class="sxs-lookup"><span data-stu-id="7cb4a-194">(Only valid for Linux/macOS and for versions earlier than .NET Core 2.1.)</span></span>

  **`--os <OPERATING_SYSTEM>`**

  <span data-ttu-id="7cb4a-195">Указывает операционную систему, для которой устанавливаются средства.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-195">Specifies the operating system for which the tools are being installed.</span></span> <span data-ttu-id="7cb4a-196">Возможные значения: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-196">Possible values are: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`.</span></span> <span data-ttu-id="7cb4a-197">(Допустимо для .NET Core 2.1 и более поздних версий.)</span><span class="sxs-lookup"><span data-stu-id="7cb4a-197">(Valid for .NET Core 2.1 and later.)</span></span>

  <span data-ttu-id="7cb4a-198">Параметр является необязательным и должен использоваться только в том случае, если требуется переопределить операционную систему, обнаруженную сценарием.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-198">The parameter is optional and should only be used when it's required to override the operating system that is detected by the script.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="7cb4a-199">Этот параметр является устаревшим и может быть удален в будущей версии скрипта.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-199">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="7cb4a-200">Вместо этого рекомендуется использовать параметр `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-200">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="7cb4a-201">Устанавливаются только двоичные файлы общей среды выполнения; в противном случае устанавливается весь пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-201">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="7cb4a-202">Этот параметр эквивалентен указанию `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-202">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="7cb4a-203">Пропускает установку файлов без версии, таких как *dotnet.exe*, если они уже существуют.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-203">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="7cb4a-204">Позволяет изменять URL-адрес некэшированного веб-канала, используемого этим установщиком.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-204">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="7cb4a-205">Изменять это значение не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-205">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="7cb4a-206">Отображает сведения о диагностике.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-206">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="7cb4a-207">Представляет определенную версию сборки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-207">Represents a specific build version.</span></span> <span data-ttu-id="7cb4a-208">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-208">The possible values are:</span></span>

  - <span data-ttu-id="7cb4a-209">`latest` — последняя сборка в канале (используется с параметром `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-209">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="7cb4a-210">Версия из трех частей в формате X.Y.Z, который представляет определенную версию сборки. Заменяет параметр `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-210">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="7cb4a-211">Например, `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-211">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="7cb4a-212">Если не указано, `-Version` по умолчанию принимает значение `latest`.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-212">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="7cb4a-213">Примеры</span><span class="sxs-lookup"><span data-stu-id="7cb4a-213">Examples</span></span>

- <span data-ttu-id="7cb4a-214">Установка последней версии с долгосрочной поддержкой (LTS) в расположение по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-214">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="7cb4a-215">Windows:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-215">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="7cb4a-216">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-216">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="7cb4a-217">Установка последней версии из канала версии 3.1 в указанное расположение</span><span class="sxs-lookup"><span data-stu-id="7cb4a-217">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="7cb4a-218">Windows:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-218">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="7cb4a-219">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-219">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="7cb4a-220">Установка общей среды выполнения версии 3.0.0</span><span class="sxs-lookup"><span data-stu-id="7cb4a-220">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="7cb4a-221">Windows:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-221">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="7cb4a-222">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-222">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="7cb4a-223">Получите и установите скрипт версии 2.1.2 за корпоративным прокси-сервером (только для Windows):</span><span class="sxs-lookup"><span data-stu-id="7cb4a-223">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="7cb4a-224">Получите скрипт и установите однострочные примеры для интерфейса командной строки .NET:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-224">Obtain script and install .NET CLI one-liner examples:</span></span>

  <span data-ttu-id="7cb4a-225">Windows:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-225">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="7cb4a-226">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-226">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="7cb4a-227">См. также</span><span class="sxs-lookup"><span data-stu-id="7cb4a-227">See also</span></span>

- [<span data-ttu-id="7cb4a-228">Выпуски .NET</span><span class="sxs-lookup"><span data-stu-id="7cb4a-228">.NET releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="7cb4a-229">Архив загрузок пакета SDK и среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="7cb4a-229">.NET Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/main/release-notes/download-archive.md)
