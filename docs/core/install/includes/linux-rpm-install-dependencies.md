---
ms.openlocfilehash: 5a027054024d8429831d73525ab3748c51ae850e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255764"
---

<span data-ttu-id="a0253-101">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="a0253-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="a0253-102">Но если вы устанавливаете .NET Core вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="a0253-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="a0253-103">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="a0253-103">krb5-libs</span></span>
- <span data-ttu-id="a0253-104">libicu</span><span class="sxs-lookup"><span data-stu-id="a0253-104">libicu</span></span>
- <span data-ttu-id="a0253-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="a0253-105">openssl-libs</span></span>
- <span data-ttu-id="a0253-106">zlib</span><span class="sxs-lookup"><span data-stu-id="a0253-106">zlib</span></span>

<span data-ttu-id="a0253-107">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="a0253-107">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="a0253-108">Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="a0253-108">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="a0253-109">Для приложений .NET Core, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="a0253-109">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="a0253-110">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="a0253-110">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="a0253-111">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="a0253-111">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="a0253-112">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="a0253-112">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
