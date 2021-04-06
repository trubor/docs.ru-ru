---
title: Установка .NET в Alpine — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Alpine.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6cd36fa6329d3c1a5835d4c202ac0024ffa41892
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079509"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>Установка пакета SDK для .NET или среды выполнения .NET в Alpine

В этой статье описано, как установить .NET в Alpine. Если поддержка какой-либо версии Alpine прекращается, то .NET также перестает поддерживать ее. Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a>Установить

Для Alpine Linux недоступны установщики. Устанавливать .NET необходимо одним из следующих способов:

- [Пакет Snap](linux-snap.md)
- [Установка с помощью скрипта _install-dotnet.sh_](linux-scripted-manual.md#scripted-install)
- [Ручное извлечение двоичных файлов](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a>Поддерживаемые дистрибутивы

В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Alpine, в которых они поддерживаются. Эти версии поддерживаются до окончания поддержки версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) либо до окончания жизненного цикла версии [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- Значок ✔️ означает, что версия Alpine или .NET поддерживается.
- Значок ❌ означает, что версия Alpine или версия .NET в таком выпуске Alpine не поддерживается.
- Если значок ✔️ стоит как напротив версии Alpine, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3.13 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.12 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.11 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.10 | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.9  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.8  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

Следующие версии .NET больше не поддерживаются. (но остаются доступными для скачивания):

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>Зависимости

Для .NET в Alpine Linux необходимо установить следующие зависимости:

- icu-libs
- krb5-libs
- libgcc
- libgdiplus (если для приложения .NET требуется сборка *System.Drawing.Common*)
- libintl
- libssl 1.1 (Alpine версии 3.9 или более поздней)
- libssl1.0 (Alpine версии 3.8 или более ранней)
- libstdc++
- zlib

Чтобы установить необходимые требования, выполните следующую команду:

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

Для установки **libgdiplus**, возможно, потребуется указать репозиторий:

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a>Следующие шаги

- [Включение заполнения клавишей TAB для .NET CLI](../tools/enable-tab-autocomplete.md)
- [Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code](../tutorials/with-visual-studio-code.md)
