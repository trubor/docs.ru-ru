---
title: Установка .NET в Linux с использованием пакета Snap — .NET
description: В этом разделе описывается установка пакета SDK для .NET или среды выполнения .NET в Linux с использованием пакета Snap.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 0d91f5049c92df240e2c3e26bc67952abe17fedc
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190103"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a>Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap

Для установки пакета SDK для .NET или среды выполнения .NET можно использовать пакет Snap. Пакеты Snap — это отличная альтернатива диспетчеру пакетов, встроенному в дистрибутив Linux. В этой статье описано, как установить .NET с использованием пакета [Snap](https://snapcraft.io/dotnet-sdk).

Snap-пакет — это пакет приложения и его зависимостей, которые работают без изменений во многих разных дистрибутивах Linux. Snap-пакеты можно найти и установить с помощью Snap Store. Дополнительные сведения о Snap см. в [этой статье](https://snapcraft.io/docs/getting-started).

> [!CAUTION]
> Пакеты Snap не поддерживаются в WSL2 в Windows 10. В качестве альтернативы можно использовать [скрипт `dotnet-install`](linux-scripted-manual.md#scripted-install) или диспетчер пакетов для соответствующего дистрибутива WSL2. Такой способ не рекомендуется, но вы можете попытаться включить пакет Snap с помощью [неподдерживаемого возможного решения, описываемого на форумах snapcraft](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).

## <a name="net-releases"></a>Выпуски .NET

В пакете Snap доступны только поддерживаемые (✔️) версии пакета SDK для .NET. Все версии среды выполнения .NET доступны в пакете Snap, начиная с версии 2.1. В следующей таблице перечислены выпуски .NET (и .NET Core):

| ✔️ Поддерживается | ❌ Не поддерживается |
|-------------|---------------|
| 5,0         | 3.0           |
| 3.1 (LTS)   | 2.2           |
| 2.1 (LTS)   | 2,0           |
|             | 1,1           |
|             | 1.0           |

Дополнительные сведения о жизненном цикле выпусков .NET см. в разделе [Политика поддержки .NET Core и .NET 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="sdk-or-runtime"></a>Пакет SDK или среда выполнения

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a>Установка пакета SDK

Пакеты Snap для пакета SDK для .NET публикуются с одним и тем же идентификатором: `dotnet-sdk`. Конкретную версию пакета SDK можно установить, указав канал. Пакет SDK содержит соответствующую среду выполнения. В следующей таблице перечислены каналы.

| Версия .NET | Пакет Snap или канал  |
|--------------|--------------------------|
| 5,0          | `5.0` или `latest/stable` |
| 3.1 (LTS)    | `3.1` или `lts/stable`    |
| 2.1 (LTS)    | `2.1`                    |

Выполните команду `snap install`, чтобы установить Snap-пакет пакета SDK для .NET. Используйте параметр `--channel`, чтобы указать, какую версию следует установить. Если этот параметр отсутствует, используйте `latest/stable`. В этом примере указан `5.0`:

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`. Вы можете выбрать любое имя `{alias}`. Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-sdk.dotnet dotnet50`. При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET. Выбор другого псевдонима несовместим с инструкциями из большинства учебников и примеров, так как в них требуется использовать команду `dotnet`.

## <a name="install-the-runtime"></a>Установка среды выполнения

Пакеты Snap для среды выполнения .NET публикуются с собственными идентификаторами пакета. В следующей таблице перечислены идентификаторы пакетов:

| Версия .NET      | Snap-пакет        |
|-------------------|---------------------|
| 5,0               | `dotnet-runtime-50` |
| 3.1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2.1 (LTS)         | `dotnet-runtime-21` |

Выполните команду `snap install`, чтобы установить Snap-пакет среды выполнения .NET. В этом примере устанавливается .NET 5.0:

```bash
sudo snap install dotnet-runtime-50 --classic
```

Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`. Вы можете выбрать любое имя `{alias}`. Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`. При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET. Выбор другого псевдонима несовместим с инструкциями из большинства учебников и примеров, так как в них требуется команда `dotnet`.

## <a name="export-the-install-location"></a>Экспорт расположения установки

Переменная среды `DOTNET_ROOT` часто используется различными средствами для определения места установки .NET. При установке .NET с помощью snap-пакета эта переменная среды не настраивается. Вам нужно настроить переменную среды *DOTNET_ROOT* в своем профиле. Путь к snap-пакету использует следующий формат: `/snap/{package}/current`. Например, если вы установили snap-пакет `dotnet-sdk`, используйте следующую команду, чтобы задать для переменной среды место расположения .NET:

```bash
export DOTNET_ROOT=/snap/dotnet-sdk/current
```

> [!TIP]
> Предыдущая команда `export` задает переменную среды только для сеанса терминала, в котором она была запущена.
>
> Вы можете изменить профиль оболочки, чтобы добавить команды окончательно. Существует несколько различных оболочек, доступных для Linux, и каждая из них имеет свой профиль. Пример:
>
> - **Оболочка Bash**: *~/.bash_profile*, *~/.bashrc*
> - **Оболочка Korn**: *~/.kshrc* или *.profile*
> - **Оболочка Z**: *~/.zshrc* или *.zprofile*
>
> Измените соответствующий исходный файл для своей оболочки и добавьте `export DOTNET_ROOT=/snap/dotnet-sdk/current`.

## <a name="tlsssl-certificate-errors"></a>Ошибки сертификатов TLS/SSL

При установке .NET с помощью пакета Snap возможно, что на некоторых дистрибутивах нельзя найти сертификаты TLS/SSL .NET, а во время выполнения `restore` может отобразиться сообщение об ошибке:

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Чтобы устранить эту проблему, задайте несколько переменных среды:

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

Расположение сертификата зависит от дистрибутива. Ниже приведены расположения для дистрибутивов, в которых возникла проблема.

| Distribution | Расположение                                            |
|--------------|-----------------------------------------------------|
| **Fedora**   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| **OpenSUSE** | `/etc/ssl/ca-bundle.pem`                            |
| **Solus**    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a>Дальнейшие действия

- [Включение заполнения клавишей TAB для .NET CLI](../tools/enable-tab-autocomplete.md)
- [Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code](../tutorials/with-visual-studio-code.md)
