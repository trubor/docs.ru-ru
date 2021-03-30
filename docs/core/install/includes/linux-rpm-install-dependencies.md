---
ms.openlocfilehash: e3f6d2d4af55e831a262a2211bf495e2f2bd772e
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879605"
---

<span data-ttu-id="f8596-101">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="f8596-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="f8596-102">Но если вы устанавливаете .NET Core вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="f8596-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="f8596-103">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="f8596-103">krb5-libs</span></span>
- <span data-ttu-id="f8596-104">libicu</span><span class="sxs-lookup"><span data-stu-id="f8596-104">libicu</span></span>
- <span data-ttu-id="f8596-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="f8596-105">openssl-libs</span></span>
- <span data-ttu-id="f8596-106">zlib</span><span class="sxs-lookup"><span data-stu-id="f8596-106">zlib</span></span>

<span data-ttu-id="f8596-107">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="f8596-107">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="f8596-108">Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f8596-108">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="f8596-109">Для приложений .NET Core, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="f8596-109">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="f8596-110">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="f8596-110">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="f8596-111">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="f8596-111">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="f8596-112">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="f8596-112">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
