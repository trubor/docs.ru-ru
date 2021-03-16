---
title: Скрипты dotnet-install
description: Сведения о скриптах dotnet-install, которые служат для установки пакета SDK для .NET и общей среды выполнения.
ms.date: 09/22/2020
ms.openlocfilehash: 51482ca70d08d86e02a493f1da49b056fed8d11c
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206691"
---
# <a name="dotnet-install-scripts-reference"></a>Справка по скриптам dotnet-install

## <a name="name"></a>name

`dotnet-install.ps1` | `dotnet-install.sh` — скрипт, используемый для установки общей среды выполнения и пакета SDK для .NET.

## <a name="synopsis"></a>Краткий обзор

Windows:

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

Linux или MacOS:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

Так как bash-скрипт также считывает параметры PowerShell, их можно использовать с этим скриптом в системах Linux и macOS.

## <a name="description"></a>Описание

Скрипты `dotnet-install` выполняют установку пакета SDK для .NET без прав администратора. Этот пакет включает общую среду выполнения и .NET CLI. Существует два скрипта:

* Скрипт PowerShell, который используется в Windows.
* Скрипт bash, который выполняется в Linux и macOS.

> [!NOTE]
> .NET собирает данные телеметрии. Дополнительные сведения и о том, как отказаться от этого, см. в разделе [Телеметрия пакета SDK для .NET](telemetry.md).

### <a name="purpose"></a>Цель

 Скрипты предназначены для использования в сценариях непрерывной интеграции (CI), если:

* Пакет SDK должен быть установлен без участия пользователя и без использования прав администратора.
* Установка пакета SDK не обязательно должна выполняться в ходе нескольких выполнений непрерывной интеграции.

  Типичная последовательность событий:
  * запускается непрерывная интеграция;
  * в ходе непрерывной интеграции устанавливается пакет SDK с помощью одного из этих скриптов;
  * непрерывная интеграция завершается, временные данные, включая установку пакета SDK, удаляются.

Чтобы настроить среду разработки или запустить приложения, используйте установщики вместо этих скриптов.

### <a name="recommended-version"></a>Рекомендуемая версия

Мы рекомендуем использовать стабильную версию скриптов.

- Bash (Linux или macOS): <https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1>

### <a name="script-behavior"></a>Поведение скрипта

Оба скрипта выполняют одни и те же функции. Они скачивают файл ZIP или TAR из места сборки CLI, а затем осуществляют установку в расположении по умолчанию или расположении, заданном параметром `-InstallDir|--install-dir`.

По умолчанию скрипты установки скачивают и устанавливают пакет SDK. Если вы хотите получить только общую среду выполнения, укажите аргумент `-Runtime|--runtime`.

По умолчанию скрипт добавляет место установки в переменную $PATH для текущего сеанса. Переопределите это поведение по умолчанию, указав аргумент `-NoPath|--no-path`. Скрипт не задает переменную среды `DOTNET_ROOT`.

Перед запуском скрипта установите все необходимые [зависимости](../install/windows.md#dependencies).

Вы можете установить конкретную версию с помощью аргумента `-Version|--version`. Версию следует указывать в виде номера из трех частей, например `2.1.0`. Если версия не указана, скрипт устанавливает версию `latest`.

Скрипты установки не обновляют реестр в Windows. Они просто скачивают двоичные ZIP-файлы и копируют их в папку. Чтобы значения разделов реестра обновлялись, используйте установщики .NET.

## <a name="options"></a>Параметры

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Архитектура устанавливаемых двоичных файлов .NET. Допустимые значения: `<auto>`, `amd64`, `x64`, `x86`, `arm64` и `arm`. Значение по умолчанию — `<auto>`, представляющее текущую используемую архитектуру ОС.

- **`-AzureFeed|--azure-feed`**

  Указывает URL-адрес для веб-канала Azure этого установщика. Изменять это значение не рекомендуется. Значение по умолчанию — `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Указывает исходный канал для установки. Допустимые значения:

  - `Current` — самый последний выпуск.
  - `LTS` — канал долгосрочной поддержки (самый последний поддерживаемый выпуск).
  - Версия из двух частей в формате X.Y, который представляет конкретный выпуск (например, `2.1` или `3.0`).
  - Имя ветви, например `release/3.1.1xx` или `master` (для ночных выпусков). Используйте этот параметр для установки версии из канала предварительной версии. Используйте имя канала, указанное в разделе [Установщики и двоичные файлы](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Значение по умолчанию — `LTS`. Дополнительные сведения о каналах поддержки .NET см. на странице о [политике поддержки .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

- **`-DryRun|--dry-run`**

  Если задано, скрипт не будет выполнять установку. Вместо этого отобразится командная строка для согласованной установки запрошенной в настоящее время версии .NET CLI. Например, если указать версию `latest`, он отображает ссылку для определенной версии, чтобы эту команду можно было детерминировано использовать в скрипте сборки. Кроме того, он отображает расположение двоичного файла, если вы хотите выполнить скачивание или установку самостоятельно.

- **`-FeedCredential|--feed-credential`**

  Используется в качестве строки запроса для добавления в веб-канал Azure. Позволяет изменять URL-адрес для использования учетных записей хранилища BLOB-объектов, не являющихся общедоступными.

- **`--help`**

  Выводит справку для скрипта. Применяется только к скрипту bash. Для PowerShell используется `Get-Help ./dotnet-install.ps1`.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Указывает путь установки. Если такого пути нет, создается каталог. Значение по умолчанию — *%LocalAppData%\Microsoft\dotnet* в Windows и */usr/share/dotnet* в Linux и macOS. Двоичные файлы помещаются непосредственно в этот каталог.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Указывает путь к файлу [global.json](global-json.md), который будет использоваться для определения версии пакета SDK. В файле *global.json* должно быть значение для `sdk:version`.

- **`-NoCdn|--no-cdn`**

  Отключает загрузку из [сети доставки содержимого Microsoft Azure (CDN)](/azure/cdn/cdn-overview) и напрямую использует некэшированный веб-канал.

- **`-NoPath|--no-path`**

  Если значение задано, папка установки не экспортируется в путь текущего сеанса. По умолчанию скрипт изменит значение PATH, благодаря чему .NET CLI становится доступным сразу после установки.

- **`-ProxyAddress`**

  Если значение задано, установщик использует прокси-сервер для выполнения веб-запросов. (Допустимо только для Windows.)

- **`-ProxyBypassList <LIST_OF_URLS>`**

  Если задано значение `ProxyAddress`, предоставляется список URL-адресов, разделенных запятыми, которые будут обходить прокси-сервер. (Допустимо только для Windows.)

- **`ProxyUseDefaultCredentials`**

  Если задано, установщик использует учетные данные текущего пользователя при использовании адреса прокси-сервера. (Допустимо только для Windows.)

- **`-Runtime|--runtime <RUNTIME>`**

  Устанавливается только общая среда выполнения, а не весь пакет SDK. Допустимые значения:

  - `dotnet` — общая среда выполнения `Microsoft.NETCore.App`.
  - `aspnetcore` — общая среда выполнения `Microsoft.AspNetCore.App`.
  - `windowsdesktop` — общая среда выполнения `Microsoft.WindowsDesktop.App`.

- **`--runtime-id <RID>` [Не рекомендуется]**

  Указывает [идентификатор среды выполнения](../rid-catalog.md), для которого устанавливаются средства. Используйте значение `linux-x64` для переносимых файлов Linux. (Допустимо только для Linux и macOS и для версий более ранних, чем .NET Core 2.1.)

  **`--os <OPERATING_SYSTEM>`**

  Указывает операционную систему, для которой устанавливаются средства. Возможные значения: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`. (Допустимо для .NET Core 2.1 и более поздних версий.)

  Параметр является необязательным и должен использоваться только в том случае, если требуется переопределить операционную систему, обнаруженную сценарием.

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Этот параметр является устаревшим и может быть удален в будущей версии скрипта. Вместо этого рекомендуется использовать параметр `-Runtime|--runtime`.

  Устанавливаются только двоичные файлы общей среды выполнения; в противном случае устанавливается весь пакет SDK. Этот параметр эквивалентен указанию `-Runtime|--runtime dotnet`.

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Пропускает установку файлов без версии, таких как *dotnet.exe*, если они уже существуют.

- **`-UncachedFeed|--uncached-feed`**

  Позволяет изменять URL-адрес некэшированного веб-канала, используемого этим установщиком. Изменять это значение не рекомендуется.

- **`-Verbose|--verbose`**

  Отображает сведения о диагностике.

- **`-Version|--version <VERSION>`**

  Представляет определенную версию сборки. Допустимые значения:

  - `latest` — последняя сборка в канале (используется с параметром `-Channel`).
  - Версия из трех частей в формате X.Y.Z, который представляет определенную версию сборки. Заменяет параметр `-Channel`. Например, `2.0.0-preview2-006120`.

  Если не указано, `-Version` по умолчанию принимает значение `latest`.

## <a name="examples"></a>Примеры

- Установка последней версии с долгосрочной поддержкой (LTS) в расположение по умолчанию:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  Mac OS и Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Установка последней версии из канала версии 3.1 в указанное расположение

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  Mac OS и Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Установка общей среды выполнения версии 3.0.0

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  Mac OS и Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Получите и установите скрипт версии 2.1.2 за корпоративным прокси-сервером (только для Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Получите скрипт и установите однострочные примеры для интерфейса командной строки .NET:

  Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  Mac OS и Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>См. также

- [Выпуски .NET](https://github.com/dotnet/core/releases)
- [Архив загрузок пакета SDK и среды выполнения .NET](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
