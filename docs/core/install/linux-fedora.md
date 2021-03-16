---
title: Установка .NET в Fedora — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Fedora.
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255765"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>Установка пакета SDK для .NET или среды выполнения .NET в Fedora

Платформа .NET поддерживается в Fedora. В этой статье описано, как установить .NET в Fedora. Если поддержка какой-либо версии Fedora прекращается, то .NET также перестает поддерживать ее.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Дополнительные сведения об установке .NET без использования диспетчера пакетов см. в одной из следующих статей:

- [Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap.](linux-snap.md)
- [Установка пакета SDK для .NET или среды выполнения .NET с использованием скрипта.](linux-scripted-manual.md#scripted-install)
- [Установка пакета SDK для .NET или среды выполнения .NET вручную.](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a>Установка .NET 5.0

Последней версией .NET, которая представлена в репозиториях пакетов по умолчанию для Fedora 33, является .NET 5.0.

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a>Установка .NET Core 3.1

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a>Поддерживаемые дистрибутивы

В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Fedora, в которых они поддерживаются. Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Fedora](https://fedoraproject.org/wiki/End_of_life).

- Значок ✔️ означает, что версия Fedora или .NET поддерживается.
- Значок ❌ означает, что версия Fedora или версия .NET в таком выпуске Fedora не поддерживается.
- Если значок ✔️ стоит как напротив версии Fedora, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.

| Версия .NET  | Fedora 33 ✔️ | 32 ✔️ | 31 ❌ | 30 ❌ | 29 ❌ | 28 ❌ | 27 ❌ |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| .NET 5.0      | ✔️        | ✔️ | ❌|❌ |❌ |❌  |❌ |
| .NET Core 3.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |❌  |❌ |
| .NET Core 2.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |✔️  |✔️ |

Следующие версии .NET больше не поддерживаются. (но остаются доступными для скачивания):

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Удалите предварительные версии

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a>Зависимости

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a>Установка в других дистрибутивах

В репозиториях пакетов по умолчанию для более старых версий Fedora отсутствует .NET Core. Вы можете установить .NET с помощью пакета [snap](linux-snap.md), [скрипта _dotnet-install.sh_](linux-scripted-manual.md#scripted-install)или репозитория Майкрософт:

01. Сначала необходимо добавить ключ подписывания пакета Майкрософт в список доверенных ключей.

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. Далее добавьте репозиторий пакетов Майкрософт. Источник репозитория зависит от вашей версии Fedora.

    | Версия Fedora | Репозиторий пакетов |
    | -------------- | ------- |
    | 31             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | 30             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | 29             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | 28             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | 27             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a>Установка других версий

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Устранение неполадок диспетчера пакетов

В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET или .NET Core.

### <a name="unable-to-find-package"></a>Не удалось найти пакет

Дополнительные сведения об установке .NET без использования диспетчера пакетов см. в одной из следующих статей:

- [Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap.](linux-snap.md)
- [Установка пакета SDK для .NET или среды выполнения .NET с использованием скрипта.](linux-scripted-manual.md#scripted-install)
- [Установка пакета SDK для .NET или среды выполнения .NET вручную.](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a>Ошибка получения

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a>Дальнейшие действия

- [Включение заполнения клавишей TAB для .NET CLI](../tools/enable-tab-autocomplete.md)
- [Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code](../tutorials/with-visual-studio-code.md)
