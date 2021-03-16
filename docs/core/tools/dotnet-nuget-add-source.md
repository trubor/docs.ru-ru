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
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.1.200 и более поздних версий

## <a name="name"></a>name

`dotnet nuget add source` — добавляет источник NuGet.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet nuget add source` добавляет новый источник пакета в файлы конфигурации NuGet.

> [!WARNING]
> При добавлении нескольких источников пакетов следите за тем, чтобы не ввести [уязвимость зависимостей](https://aka.ms/pkg-sec-wp).

## <a name="arguments"></a>Аргументы

- **`PACKAGE_SOURCE_PATH`**

  Путь к источнику пакета.

## <a name="options"></a>Параметры

- **`--configfile <FILE>`**

  Файл конфигурации NuGet. Если этот параметр указан, будут использоваться только параметры из этого файла. Если не указано, будет использоваться иерархия файлов конфигурации из текущего каталога. Дополнительные сведения см. в статье [Распространенные конфигурации NuGet](/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Имя источника.

- **`-p|--password <PASSWORD>`**

  Пароль, используемый при подключении к источнику, прошедшему проверку подлинности.

- **`--store-password-in-clear-text`**

  Включает сохранение учетных данных переносимого источника пакетов путем отключения шифрования паролей.

- **`-u|--username <USER>`**

  Имя пользователя, используемое при подключении к источнику, прошедшему проверку подлинности.

- **`--valid-authentication-types <TYPES>`**

  Разделенный запятыми список допустимых типов проверки подлинности для этого источника. Задайте значение `basic`, если сервер объявляет NTLM или Negotiate. Ваши учетные данные следует отправлять с помощью базового механизма, например, при использовании PAT с локальным Azure DevOps Server. К другим допустимым значениям относятся `negotiate`, `kerberos`, `ntlm` и `digest`, но они вряд ли будут полезны.

## <a name="examples"></a>Примеры

- Добавьте `nuget.org` в качестве источника:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Добавьте `c:\packages` в качестве локального источника:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Добавьте источник, требующий проверки подлинности:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Добавьте источник, требующий проверки подлинности (затем установите поставщик учетных данных):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>См. также

- [Разделы источников пакетов в файлах NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [Команда sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
