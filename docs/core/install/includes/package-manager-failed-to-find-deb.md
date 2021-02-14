---
ms.openlocfilehash: 3275865cf7f4669ba7deaacea320136d02f64dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804221"
---

<span data-ttu-id="83b3e-101">Если появляется сообщение об ошибке, похожее на **Не удалось найти пакет {dotnet-package}** или **Не удалось установить некоторые пакеты**, выполните проведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="83b3e-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="83b3e-102">В следующем наборе команд есть два заполнителя.</span><span class="sxs-lookup"><span data-stu-id="83b3e-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="83b3e-103">Этот заполнитель представляет собой устанавливаемый пакет .NET, например `aspnetcore-runtime-3.1`.</span><span class="sxs-lookup"><span data-stu-id="83b3e-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="83b3e-104">Это используется в следующей команде `sudo apt-get install`.</span><span class="sxs-lookup"><span data-stu-id="83b3e-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="83b3e-105">Этот заполнитель представляет собой версию дистрибутива, которую вы используете.</span><span class="sxs-lookup"><span data-stu-id="83b3e-105">This represents the distribution version you're on.</span></span> <span data-ttu-id="83b3e-106">Он используется в приведенной ниже команде `wget`.</span><span class="sxs-lookup"><span data-stu-id="83b3e-106">This is used in the `wget` command below.</span></span> <span data-ttu-id="83b3e-107">Версия дистрибутива — это числовое значение, например `20.04` в Ubuntu или `10` в Debian.</span><span class="sxs-lookup"><span data-stu-id="83b3e-107">The distribution version is the numerical value, such as `20.04` on Ubuntu or `10` on Debian.</span></span>

<span data-ttu-id="83b3e-108">Сначала попробуйте очистить список пакетов.</span><span class="sxs-lookup"><span data-stu-id="83b3e-108">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="83b3e-109">Затем попробуйте установить .NET еще раз.</span><span class="sxs-lookup"><span data-stu-id="83b3e-109">Then, try to install .NET again.</span></span> <span data-ttu-id="83b3e-110">Если проблема не решена, можно выполнить установку вручную с помощью приведенных ниже команд.</span><span class="sxs-lookup"><span data-stu-id="83b3e-110">If that doesn't work, you can run a manual install with the following commands:</span></span>
