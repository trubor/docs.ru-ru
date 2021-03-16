---
title: Команда dotnet tool install
description: Команда dotnet tool install устанавливает указанное средство .NET на компьютер.
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206485"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий

## <a name="name"></a>name

`dotnet tool install` устанавливает указанное [средство .NET](global-tools.md) на компьютер.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet tool install` предоставляет способ установки средств .NET на компьютере. Чтобы использовать команду, укажите один из следующих параметров установки:

* Чтобы установить глобальный инструмент в расположение по умолчанию, используйте параметр `--global`.
* Чтобы установить глобальный инструмент в расположение, указанное пользователем, используйте параметр `--tool-path`.
* Чтобы установить локальный инструмент, пропустите параметры `--global` и `--tool-path`.

**Локальные средства доступны в пакете SDK для .NET Core, начиная с версии 3.0.**

Глобальные средства устанавливаются в следующие каталоги по умолчанию при выборе параметра `-g` или `--global`:

| Операционная система          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Локальные средства добавляются в файл *dotnet-tools.json* в каталоге *. config* в текущем каталоге. Если файл манифеста еще не существует, создайте его, выполнив следующую команду:

```dotnetcli
dotnet new tool-manifest
```

Дополнительные сведения см. в разделе [Установка глобального средства](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Аргументы

- **`PACKAGE_NAME`**

  Имя или идентификатор пакета NuGet, который содержит устанавливаемое средство .NET.

## <a name="options"></a>Параметры

- **`--add-source <SOURCE>`**

  Добавляет дополнительный источник пакета NuGet для использования во время установки. Доступ к каналам осуществляется параллельно, а не последовательно в некотором порядке приоритета. Если один и тот же пакет и версия находятся в нескольких каналах, используется самый быстрый канал. Дополнительные сведения см. в разделе [Процесс установки пакета NuGet](/nuget/concepts/package-installation-process).

- **`--configfile <FILE>`**

  Файл конфигурации NuGet (*nuget.config*), который будет использоваться.

- **`--framework <FRAMEWORK>`**

  Указывает [требуемую версию .NET Framework](../../standard/frameworks.md) для установки средства. По умолчанию пакет SDK для .NET пытается выбрать наиболее подходящую версию .NET Framework.

- **`-g|--global`**

  Указывает, что установка происходит на уровне пользователя. Не может использоваться вместе с параметром `--tool-path`. Пропуск параметров `--global` и `--tool-path` задает установку локального средства.

- **`-h|--help`**

  Выводит краткую справку по команде.

- **`--tool-path <PATH>`**

  Указывает место установки глобального средства. Путь может быть абсолютным или относительным. Если путь не существует, команда пытается создать его. Пропуск параметров `--global` и `--tool-path` задает установку локального средства.

- **`-v|--verbosity <LEVEL>`**

  Задает уровень детализации команды. Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Версия средства для установки. По умолчанию устанавливается последняя стабильная версия пакета. Используйте этот параметр для установки предварительной версии или предыдущей версии средства.

## <a name="examples"></a>Примеры

- **`dotnet tool install -g dotnetsay`**

  Устанавливает глобальное средство [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в расположении по умолчанию.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве глобального инструмента в определенном каталоге Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве глобального инструмента в определенном каталоге Linux/macOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Устанавливает версию 2.0.0 в качестве глобального средства [dotnetsay](https://www.nuget.org/packages/dotnetsay/):

- **`dotnet tool install dotnetsay`**

  Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве локального средства для текущего каталога.

## <a name="see-also"></a>См. также

- [Средства .NET](global-tools.md)
- [Учебник. Установка и использование глобального средства .NET с помощью интерфейса командной строки .NET](global-tools-how-to-use.md)
- [Учебник. Установка и использование локального средства .NET с помощью интерфейса командной строки .NET](local-tools-how-to-use.md)
