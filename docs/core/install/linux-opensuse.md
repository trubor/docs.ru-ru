---
title: Установка .NET в openSUSE — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d238054a217a7295594db856d5497982572af377
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873956"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a>Установка пакета SDK для .NET или среды выполнения .NET в openSUSE

.NET поддерживается в openSUSE. В этой статье описано, как установить .NET в openSUSE.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Поддерживаемые дистрибутивы

В следующей таблице приведен список выпусков .NET, которые сейчас поддерживаются в openSUSE 15. Эти версии поддерживаются до тех пор, пока для версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или версии openSUSE не будет прекращена поддержка.

- Значок ✔️ означает, что версия openSUSE или .NET поддерживается.
- Значок ❌ означает, что версия openSUSE или версия .NET в таком выпуске openSUSE не поддерживается.
- Если значок ✔️ стоит как напротив версии openSUSE, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

Следующие версии .NET больше не поддерживаются. (но остаются доступными для скачивания):

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Удалите предварительные версии

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a>Установка других версий

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Устранение неполадок диспетчера пакетов

В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET.

### <a name="unable-to-find-package"></a>Не удалось найти пакет

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Ошибка получения

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>Зависимости

Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически. Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:

- krb5
- libicu
- libopenssl1_0_0

Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.

Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).

Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:

- [libgdiplus (версии 6.0.1 или выше)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono. Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.

## <a name="next-steps"></a>Следующие шаги

- [Включение заполнения клавишей TAB для .NET CLI](../tools/enable-tab-autocomplete.md)
- [Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code](../tutorials/with-visual-studio-code.md)
