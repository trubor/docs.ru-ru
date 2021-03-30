---
title: Установка .NET в Linux вручную — .NET
description: В этом разделе описывается установка пакета SDK для .NET и среды выполнения .NET в Linux без использования диспетчера пакетов. Для этого можно использовать скрипт установки или извлечь двоичные файлы вручную.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6840814627be0124d7b3855f08a433eab76eac4a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873917"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a>Установка пакета SDK для .NET или среды выполнения .NET вручную

Платформа .NET поддерживается в Linux. В этой статье описывается установка .NET в Linux с помощью скрипта установки или посредством извлечения двоичных файлов. Список дистрибутивов, поддерживающих встроенный диспетчер пакетов, см. в разделе [Установка .NET в Linux](linux.md).

Также можно установить .NET с помощью пакета Snap. Дополнительные сведения см. в разделе [Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap](linux-snap.md).

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a>Выпуски .NET

В следующей таблице перечислены выпуски .NET (и .NET Core):

| ✔️ Поддерживается | ❌ Не поддерживается |
|-------------|---------------|
| 5,0         | 3.0           |
| 3.1 (LTS)   | 2.2           |
| 2.1 (LTS)   | 2,0           |
|             | 1,1           |
|             | 1.0           |

Дополнительные сведения о жизненном цикле выпусков .NET см. в разделе [Политика поддержки .NET Core и .NET 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="dependencies"></a>Зависимости

В некоторых случаях, например при [установке .NET вручную](#manual-install), некоторые зависимости могут не устанавливаться. Ниже перечислены дистрибутивы Linux, которые поддерживаются корпорацией Майкрософт и для которых может потребоваться установка зависимостей. Дополнительные сведения см. на странице, посвященной соответствующему дистрибутиву:

- [Alpine](linux-alpine.md#dependencies)
- [Debian](linux-debian.md#dependencies)
- [CentOS](linux-centos.md#dependencies)
- [Fedora](linux-fedora.md#dependencies)
- [RHEL](linux-rhel.md#dependencies)
- [SLES](linux-sles.md#dependencies)
- [Ubuntu](linux-ubuntu.md#dependencies)

Общие сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).

### <a name="rpm-dependencies"></a>Зависимости RPM

Если ваш дистрибутив не указан в приведенном выше списке и построен на основе RPM, могут потребоваться следующие зависимости:

- krb5-libs
- libicu
- openssl-libs

Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.

### <a name="deb-dependencies"></a>Зависимости DEB

Если ваш дистрибутив не указан в приведенном выше списке и построен на основе Debian, могут потребоваться следующие зависимости:

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu67
- libssl1.1
- libstdc++6
- zlib1g

### <a name="common-dependencies"></a>Общие зависимости

Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:

- [libgdiplus (версии 6.0.1 или выше)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono. Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Установка с помощью скрипта

[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации установок **пакета SDK** и **среды выполнения** и осуществления таких установок без прав администратора. Скрипт можно скачать на странице <https://dot.net/v1/dotnet-install.sh>.

Этот сценарий по умолчанию устанавливает последнюю версию SDK [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1. Чтобы установить текущий выпуск, который может не быть версией LTS, используйте параметр `-c Current`.

```bash
./dotnet-install.sh -c Current
```

Чтобы вместо пакета SDK установить среду выполнения .NET, используйте параметр `--runtime`.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Вы можете установить определенную версию, указав ее в параметре `-c`. Следующая команда устанавливает пакет SDK для .NET 5.0.

```bash
./dotnet-install.sh -c 5.0
```

Дополнительные сведения см. в статье [Справка по скриптам dotnet-install](../tools/dotnet-install-script.md).

## <a name="manual-install"></a>Установка вручную

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

В качестве альтернативы диспетчерам пакетов можно скачать и вручную установить пакет SDK и среду выполнения. Ручная установка как правило выполняется в рамках тестирования непрерывной интеграции или в неподдерживаемом дистрибутиве Linux. В большинстве случаев разработчикам и пользователям рекомендуется использовать диспетчер пакетов.

При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения. Сначала скачайте **двоичный** выпуск пакета SDK или среды выполнения с одного из следующих сайтов:

- ✔️ [Скачиваемые файлы для .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [Скачиваемые файлы .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)
- ✔️ [Скачиваемые файлы .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet/2.1)
- [Все скачиваемые файлы для .NET Core](https://dotnet.microsoft.com/download/dotnet)

Извлеките скачанный файл и используйте команду `export`, чтобы задать переменные, используемые .NET, а затем проверьте включение .NET в переменную PATH.

Чтобы извлечь среду выполнения и сделать команды .NET CLI доступными в терминале, сначала скачайте двоичный выпуск .NET. Затем откройте терминал и выполните следующие команды в каталоге с сохраненным файлом. Имя файла архива может отличаться в зависимости от скачанных файлов.

**Используйте следующие команды для извлечения скачанной среды выполнения или пакета SDK.** Не забудьте заменить значение `DOTNET_FILE` на имя файла:

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> Приведенные выше команды `export` сделают команды .NET CLI доступными только для сеанса терминала, в котором производился запуск.
>
> Вы можете изменить профиль оболочки, чтобы добавить команды окончательно. Существует несколько различных оболочек, доступных для Linux, и каждая из них имеет свой профиль. Пример:
>
> - **Оболочка Bash**: *~/.bash_profile*, *~/.bashrc*
> - **Оболочка Korn**: *~/.kshrc* или *.profile*
> - **Оболочка Z**: *~/.zshrc* или *.zprofile*
>
> Измените соответствующий исходный файл оболочки и добавьте `:$HOME/dotnet` в конец существующего оператора `PATH`. Если оператор `PATH` не указан, добавьте новую строку с `export PATH=$PATH:$HOME/dotnet`.
>
> Кроме того, добавьте `export DOTNET_ROOT=$HOME/dotnet` в конец файла.

Такой подход позволяет устанавливать разные версии в отдельные расположения и выбирать, какие из них следует использовать для каждого приложения.

## <a name="next-steps"></a>Дальнейшие действия

- [Включение заполнения клавишей TAB для .NET CLI](../tools/enable-tab-autocomplete.md)
- [Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code](../tutorials/with-visual-studio-code.md)
