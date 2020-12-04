---
title: Установка .NET в RHEL — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 931cad51ff8e35ff16b67ff9b795feb36010a66b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031791"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="64504-103">Установка пакета SDK для .NET или среды выполнения .NET в RHEL</span><span class="sxs-lookup"><span data-stu-id="64504-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="64504-104">.NET поддерживается в RHEL.</span><span class="sxs-lookup"><span data-stu-id="64504-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="64504-105">В этой статье описано, как установить .NET в RHEL.</span><span class="sxs-lookup"><span data-stu-id="64504-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="64504-106">Регистрация подписки Red Hat</span><span class="sxs-lookup"><span data-stu-id="64504-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="64504-107">Чтобы установить .NET из Red Hat в RHEL, сначала нужно зарегистрироваться с помощью диспетчера подписки Red Hat.</span><span class="sxs-lookup"><span data-stu-id="64504-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="64504-108">Если это еще не сделано в вашей системе либо вы точно не уверены, ознакомьтесь с [документацией по продукту Red Hat для .NET](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="64504-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="64504-109">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="64504-109">Supported distributions</span></span>

<span data-ttu-id="64504-110">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET в RHEL 7 и RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="64504-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="64504-111">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или RHEL.</span><span class="sxs-lookup"><span data-stu-id="64504-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="64504-112">Значок ✔️ означает, что версия RHEL или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="64504-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="64504-113">Значок ❌ означает, что версия RHEL или версия .NET в таком выпуске RHEL не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="64504-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="64504-114">Если значок ✔️ стоит как напротив версии RHEL, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="64504-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="64504-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="64504-115">RHEL</span></span>                     | <span data-ttu-id="64504-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="64504-116">.NET Core 2.1</span></span> | <span data-ttu-id="64504-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="64504-117">.NET Core 3.1</span></span> | <span data-ttu-id="64504-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="64504-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="64504-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="64504-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="64504-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="64504-120">✔️ 2.1</span></span>        | <span data-ttu-id="64504-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="64504-121">✔️ 3.1</span></span>        | <span data-ttu-id="64504-122">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="64504-122">✔️ 5.0</span></span> |
| <span data-ttu-id="64504-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="64504-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="64504-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="64504-124">✔️ 2.1</span></span>        | <span data-ttu-id="64504-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="64504-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="64504-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="64504-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="64504-127">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="64504-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="64504-128">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="64504-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="64504-129">3.0</span><span class="sxs-lookup"><span data-stu-id="64504-129">3.0</span></span>
- <span data-ttu-id="64504-130">2.2</span><span class="sxs-lookup"><span data-stu-id="64504-130">2.2</span></span>
- <span data-ttu-id="64504-131">2.0</span><span class="sxs-lookup"><span data-stu-id="64504-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="64504-132">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="64504-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="64504-133">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="64504-133">How to install other versions</span></span>

<span data-ttu-id="64504-134">Сведения об установке других выпусков .NET см. в [документации по Red Hat для .NET](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="64504-134">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="64504-135">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="64504-135">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="64504-136">.NET 5.0 пока недоступна в репозиториях AppStream, однако .NET Core 3.1 доступна.</span><span class="sxs-lookup"><span data-stu-id="64504-136">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="64504-137">Чтобы установить .NET Core 3.1, используйте команду `dnf install` с соответствующим пакетом, например `aspnetcore-runtime-3.1` или `dotnet-sdk-3.1`.</span><span class="sxs-lookup"><span data-stu-id="64504-137">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="64504-138">Следующие действия приведены для .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="64504-138">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="64504-139">RHEL 7 ✔️ .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="64504-139">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="64504-140">RHEL 7 ✔️ .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="64504-140">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="64504-141">Следующая команда устанавливает пакет `scl-utils`:</span><span class="sxs-lookup"><span data-stu-id="64504-141">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="64504-142">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="64504-142">Install the SDK</span></span>

<span data-ttu-id="64504-143">Пакет SDK для .NET Core позволяет разрабатывать приложения с помощью .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64504-143">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="64504-144">При установке пакета SDK для .NET Core не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="64504-144">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="64504-145">Чтобы установить пакет SDK для .NET Core, выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="64504-145">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="64504-146">В Red Hat не рекомендуется активировать `rh-dotnet31` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="64504-146">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="64504-147">Например, `rh-dotnet31` включает версию `libcurl`, которая отличается от базовой версии RHEL.</span><span class="sxs-lookup"><span data-stu-id="64504-147">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="64504-148">Это может вызвать проблемы в программах, которые не ожидают другой версии `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="64504-148">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="64504-149">Если вы хотите активировать `rh-dotnet` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="64504-149">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="64504-150">Установка среды выполнения</span><span class="sxs-lookup"><span data-stu-id="64504-150">Install the runtime</span></span>

<span data-ttu-id="64504-151">Среда выполнения .NET Core позволяет запускать приложения, созданные с помощью версии .NET Core без поддержки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="64504-151">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="64504-152">Приведенные ниже команды позволяют установить среду выполнения ASP.NET Core, которая больше всего совместима с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64504-152">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="64504-153">В терминале выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="64504-153">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="64504-154">В Red Hat не рекомендуется активировать `rh-dotnet31-aspnetcore-runtime-3.1` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="64504-154">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="64504-155">Например, `rh-dotnet31-aspnetcore-runtime-3.1` включает версию `libcurl`, которая отличается от базовой версии RHEL.</span><span class="sxs-lookup"><span data-stu-id="64504-155">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="64504-156">Это может вызвать проблемы в программах, которые не ожидают другой версии `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="64504-156">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="64504-157">Если вы хотите активировать `rh-dotnet31-aspnetcore-runtime-3.1` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="64504-157">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="64504-158">В качестве альтернативы среде выполнения ASP.NET Core вы можете установить среду выполнения .NET Core без поддержки ASP.NET Core. Для этого в приведенной выше команде замените `rh-dotnet31-aspnetcore-runtime-3.1` на `rh-dotnet31-dotnet-runtime-3.1`.</span><span class="sxs-lookup"><span data-stu-id="64504-158">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="64504-159">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="64504-159">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="64504-160">Зависимости</span><span class="sxs-lookup"><span data-stu-id="64504-160">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="64504-161">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="64504-161">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="64504-162">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="64504-162">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="64504-163">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="64504-163">Next steps</span></span>

- [<span data-ttu-id="64504-164">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="64504-164">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
