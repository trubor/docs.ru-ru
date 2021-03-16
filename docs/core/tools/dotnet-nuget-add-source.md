---
title: Команда dotnet nuget add source
description: Команда dotnet nuget add source добавляет новый источник пакета в файлы конфигурации NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: df31a2eaba997d0e9fe4f4c2666052fd7c7c2f03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105055"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="1c826-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="1c826-103">dotnet nuget add source</span></span>

<span data-ttu-id="1c826-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.1.200 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="1c826-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1c826-105">name</span><span class="sxs-lookup"><span data-stu-id="1c826-105">Name</span></span>

<span data-ttu-id="1c826-106">`dotnet nuget add source` — добавляет источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="1c826-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1c826-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="1c826-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="1c826-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1c826-108">Description</span></span>

<span data-ttu-id="1c826-109">Команда `dotnet nuget add source` добавляет новый источник пакета в файлы конфигурации NuGet.</span><span class="sxs-lookup"><span data-stu-id="1c826-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

> [!WARNING]
> <span data-ttu-id="1c826-110">При добавлении нескольких источников пакетов следите за тем, чтобы не ввести [уязвимость зависимостей](https://aka.ms/pkg-sec-wp).</span><span class="sxs-lookup"><span data-stu-id="1c826-110">When adding multiple package sources, be careful not to introduce a [dependency confusion vulnerability](https://aka.ms/pkg-sec-wp).</span></span>

## <a name="arguments"></a><span data-ttu-id="1c826-111">Аргументы</span><span class="sxs-lookup"><span data-stu-id="1c826-111">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="1c826-112">Путь к источнику пакета.</span><span class="sxs-lookup"><span data-stu-id="1c826-112">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="1c826-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c826-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="1c826-114">Файл конфигурации NuGet.</span><span class="sxs-lookup"><span data-stu-id="1c826-114">The NuGet configuration file.</span></span> <span data-ttu-id="1c826-115">Если этот параметр указан, будут использоваться только параметры из этого файла.</span><span class="sxs-lookup"><span data-stu-id="1c826-115">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="1c826-116">Если не указано, будет использоваться иерархия файлов конфигурации из текущего каталога.</span><span class="sxs-lookup"><span data-stu-id="1c826-116">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="1c826-117">Дополнительные сведения см. в статье [Распространенные конфигурации NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="1c826-117">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="1c826-118">Имя источника.</span><span class="sxs-lookup"><span data-stu-id="1c826-118">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="1c826-119">Пароль, используемый при подключении к источнику, прошедшему проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="1c826-119">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="1c826-120">Включает сохранение учетных данных переносимого источника пакетов путем отключения шифрования паролей.</span><span class="sxs-lookup"><span data-stu-id="1c826-120">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="1c826-121">Имя пользователя, используемое при подключении к источнику, прошедшему проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="1c826-121">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="1c826-122">Разделенный запятыми список допустимых типов проверки подлинности для этого источника.</span><span class="sxs-lookup"><span data-stu-id="1c826-122">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="1c826-123">Задайте значение `basic`, если сервер объявляет NTLM или Negotiate. Ваши учетные данные следует отправлять с помощью базового механизма, например, при использовании PAT с локальным Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="1c826-123">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="1c826-124">К другим допустимым значениям относятся `negotiate`, `kerberos`, `ntlm` и `digest`, но они вряд ли будут полезны.</span><span class="sxs-lookup"><span data-stu-id="1c826-124">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="1c826-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="1c826-125">Examples</span></span>

- <span data-ttu-id="1c826-126">Добавьте `nuget.org` в качестве источника:</span><span class="sxs-lookup"><span data-stu-id="1c826-126">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="1c826-127">Добавьте `c:\packages` в качестве локального источника:</span><span class="sxs-lookup"><span data-stu-id="1c826-127">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="1c826-128">Добавьте источник, требующий проверки подлинности:</span><span class="sxs-lookup"><span data-stu-id="1c826-128">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="1c826-129">Добавьте источник, требующий проверки подлинности (затем установите поставщик учетных данных):</span><span class="sxs-lookup"><span data-stu-id="1c826-129">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="1c826-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1c826-130">See also</span></span>

- [<span data-ttu-id="1c826-131">Разделы источников пакетов в файлах NuGet.config</span><span class="sxs-lookup"><span data-stu-id="1c826-131">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="1c826-132">Команда sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="1c826-132">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
