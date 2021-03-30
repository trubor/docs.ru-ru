---
ms.openlocfilehash: e3f6d2d4af55e831a262a2211bf495e2f2bd772e
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879605"
---

Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически. Но если вы устанавливаете .NET Core вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:

- krb5-libs
- libicu
- openssl-libs
- zlib

Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.

Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).

Для приложений .NET Core, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:

- [libgdiplus (версии 6.0.1 или выше)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono. Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.
