---
title: Команда dotnet nuget push
description: Команда dotnet nuget push отправляет пакет на сервер и публикует его.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 71bc14fa729945b3d1e1508d014287cc5355f8cc
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637563"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="b3aec-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="b3aec-103">dotnet nuget push</span></span>

<span data-ttu-id="b3aec-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="b3aec-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b3aec-105">name</span><span class="sxs-lookup"><span data-stu-id="b3aec-105">Name</span></span>

<span data-ttu-id="b3aec-106">`dotnet nuget push` — отправляет пакет на сервер и публикует его.</span><span class="sxs-lookup"><span data-stu-id="b3aec-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b3aec-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="b3aec-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="b3aec-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b3aec-108">Description</span></span>

<span data-ttu-id="b3aec-109">Команда `dotnet nuget push` отправляет пакет на сервер и публикует его.</span><span class="sxs-lookup"><span data-stu-id="b3aec-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="b3aec-110">Команда push использует сервер и учетные данные, указанные в системном файле конфигурации NuGet или цепочке файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b3aec-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="b3aec-111">См. дополнительные сведения о файлах конфигурации в статье о [настройке поведения NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="b3aec-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="b3aec-112">Конфигурацию NuGet по умолчанию можно получить, загрузив файл *%AppData%\NuGet\NuGet.config* (Windows) или *$HOME/.local/share* (Linux и macOS). Затем нужно загрузить все файлы *nuget.config* или *.nuget\nuget.config*, начиная с корневого каталога диска и заканчивая текущим каталогом.</span><span class="sxs-lookup"><span data-stu-id="b3aec-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="b3aec-113">Команда отправляет существующий пакет.</span><span class="sxs-lookup"><span data-stu-id="b3aec-113">The command pushes an existing package.</span></span> <span data-ttu-id="b3aec-114">При этом пакет не создается.</span><span class="sxs-lookup"><span data-stu-id="b3aec-114">It doesn't create a package.</span></span> <span data-ttu-id="b3aec-115">Для создания пакета используйте [`dotnet pack`](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b3aec-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="b3aec-116">Аргументы</span><span class="sxs-lookup"><span data-stu-id="b3aec-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="b3aec-117">Указывает путь к файлу пакета для отправки.</span><span class="sxs-lookup"><span data-stu-id="b3aec-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="b3aec-118">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3aec-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="b3aec-119">Отключает буферизацию при передаче данных на сервер HTTP(S), чтобы снизить использование памяти.</span><span class="sxs-lookup"><span data-stu-id="b3aec-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="b3aec-120">Принудительно запускает приложение с использованием инвариантного английского языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="b3aec-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b3aec-121">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="b3aec-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="b3aec-122">Позволяет блокировать команду до выполнения действия пользователем, например аутентификации.</span><span class="sxs-lookup"><span data-stu-id="b3aec-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="b3aec-123">Параметр доступен, начиная с пакета SDK для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="b3aec-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="b3aec-124">Ключ API для сервера.</span><span class="sxs-lookup"><span data-stu-id="b3aec-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="b3aec-125">Не передает символы (даже если они присутствуют).</span><span class="sxs-lookup"><span data-stu-id="b3aec-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="b3aec-126">Не добавляет "api/v2/package" в исходный URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="b3aec-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="b3aec-127">Параметр доступен, начиная с пакета SDK для .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="b3aec-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="b3aec-128">Определяет URL-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="b3aec-128">Specifies the server URL.</span></span> <span data-ttu-id="b3aec-129">NuGet определяет источник в формате UNC или локальную папку и просто копирует файл вместо отправки через HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3aec-129">NuGet identifies a UNC or local folder source and simply copies the file there instead of pushing it using HTTP.</span></span>
  > [!IMPORTANT]
  > <span data-ttu-id="b3aec-130">Начиная с NuGet 3.4.2, этот параметр является обязательным, если в файле конфигурации NuGet не указано значение `DefaultPushSource`.</span><span class="sxs-lookup"><span data-stu-id="b3aec-130">Starting with NuGet 3.4.2, this is a mandatory parameter unless the NuGet config file specifies a `DefaultPushSource` value.</span></span> <span data-ttu-id="b3aec-131">Дополнительные сведения см. в статье [Configuring NuGet behavior](/nuget/consume-packages/configuring-nuget-behavior) (Настройка поведения NuGet).</span><span class="sxs-lookup"><span data-stu-id="b3aec-131">For more information, see [Configuring NuGet behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="b3aec-132">При принудительной отправке нескольких пакетов на сервер HTTP(S) обрабатывает любой ответ с кодом состояния 409 Conflict (конфликт) в виде предупреждения, чтобы можно было продолжить принудительную отправку.</span><span class="sxs-lookup"><span data-stu-id="b3aec-132">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="b3aec-133">Доступно, начиная с пакета SDK для .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="b3aec-133">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="b3aec-134">Ключ API для сервера символов.</span><span class="sxs-lookup"><span data-stu-id="b3aec-134">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="b3aec-135">Указывает URL-адрес сервера символов.</span><span class="sxs-lookup"><span data-stu-id="b3aec-135">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="b3aec-136">Указывает время ожидания для передачи на сервер в секундах.</span><span class="sxs-lookup"><span data-stu-id="b3aec-136">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="b3aec-137">Значение по умолчанию — 300 секунд (5 минут).</span><span class="sxs-lookup"><span data-stu-id="b3aec-137">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="b3aec-138">При указании 0 применяется значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b3aec-138">Specifying 0 applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="b3aec-139">Примеры</span><span class="sxs-lookup"><span data-stu-id="b3aec-139">Examples</span></span>

- <span data-ttu-id="b3aec-140">Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, используя ключ API:</span><span class="sxs-lookup"><span data-stu-id="b3aec-140">Push *foo.nupkg* to the default push source specified in the NuGet config file, using an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="b3aec-141">Отправляет *foo.nupkg* на официальный сервер NuGet, предоставляя ключ API:</span><span class="sxs-lookup"><span data-stu-id="b3aec-141">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="b3aec-142">Отправляет *foo.nupkg* в пользовательский источник push-уведомлений `https://customsource`, предоставляя ключ API:</span><span class="sxs-lookup"><span data-stu-id="b3aec-142">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="b3aec-143">Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet:</span><span class="sxs-lookup"><span data-stu-id="b3aec-143">Push *foo.nupkg* to the default push source specified in the NuGet config file:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="b3aec-144">Отправляет *foo.symbols.nupkg* в источник символов по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="b3aec-144">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="b3aec-145">Отправляет *foo.nupkg* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, с временем ожидания 360 с:</span><span class="sxs-lookup"><span data-stu-id="b3aec-145">Push *foo.nupkg* to the default push source specified in the NuGet config file, with a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="b3aec-146">Отправляет все файлы *NUPKG* из текущего каталога в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet:</span><span class="sxs-lookup"><span data-stu-id="b3aec-146">Push all *.nupkg* files in the current directory to the default push source specified in the NuGet config file:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > <span data-ttu-id="b3aec-147">Если эта команда не работает, возможно, это связано с ошибкой, которая существовала в более старых версиях пакета SDK (пакет SDK для .NET Core 2.1 и более ранних версий).</span><span class="sxs-lookup"><span data-stu-id="b3aec-147">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="b3aec-148">Чтобы устранить эту проблему, обновите версию пакета SDK или выполните следующую команду: `dotnet nuget push "**/*.nupkg"`</span><span class="sxs-lookup"><span data-stu-id="b3aec-148">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push "**/*.nupkg"`</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="b3aec-149">Закрывающие кавычки необходимы для оболочек, таких как bash, выполняющих файл глобализации.</span><span class="sxs-lookup"><span data-stu-id="b3aec-149">The enclosing quotes are required for shells such as bash that perform file globbing.</span></span> <span data-ttu-id="b3aec-150">Дополнительные сведения см. на странице [NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).</span><span class="sxs-lookup"><span data-stu-id="b3aec-150">For more information, see [NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).</span></span>

- <span data-ttu-id="b3aec-151">Отправляет все файлы *NUPKG* в источник push-уведомлений по умолчанию, указанный в файле конфигурации NuGet, даже если сервер HTTP (S) возвращает в ответе конфликт 409:</span><span class="sxs-lookup"><span data-stu-id="b3aec-151">Push all *.nupkg* files to the default push source specified in the NuGet config file, even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- <span data-ttu-id="b3aec-152">Отправляет все файлы *NUPKG* из текущего каталога в каталог локального веб-канала:</span><span class="sxs-lookup"><span data-stu-id="b3aec-152">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  <span data-ttu-id="b3aec-153">Эта команда не сохраняет пакеты в иерархическую структуру папок, что рекомендуется для оптимизации производительности.</span><span class="sxs-lookup"><span data-stu-id="b3aec-153">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="b3aec-154">Дополнительные сведения см. в разделе [Локальные веб-каналы](/nuget/hosting-packages/local-feeds).</span><span class="sxs-lookup"><span data-stu-id="b3aec-154">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
