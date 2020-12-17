---
title: Установка .NET в RHEL — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851644"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="28126-103">Установка пакета SDK для .NET или среды выполнения .NET в RHEL</span><span class="sxs-lookup"><span data-stu-id="28126-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="28126-104">.NET поддерживается в RHEL.</span><span class="sxs-lookup"><span data-stu-id="28126-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="28126-105">В этой статье описано, как установить .NET в RHEL.</span><span class="sxs-lookup"><span data-stu-id="28126-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="28126-106">Регистрация подписки Red Hat</span><span class="sxs-lookup"><span data-stu-id="28126-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="28126-107">Чтобы установить .NET из Red Hat в RHEL, сначала нужно зарегистрироваться с помощью диспетчера подписки Red Hat.</span><span class="sxs-lookup"><span data-stu-id="28126-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="28126-108">Если это еще не сделано в вашей системе либо вы точно не уверены, ознакомьтесь с [документацией по продукту Red Hat для .NET](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="28126-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="28126-109">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="28126-109">Supported distributions</span></span>

<span data-ttu-id="28126-110">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET в RHEL 7 и RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="28126-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="28126-111">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или RHEL.</span><span class="sxs-lookup"><span data-stu-id="28126-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="28126-112">Значок ✔️ означает, что версия RHEL или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="28126-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="28126-113">Значок ❌ означает, что версия RHEL или версия .NET в таком выпуске RHEL не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="28126-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="28126-114">Если значок ✔️ стоит как напротив версии RHEL, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="28126-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="28126-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="28126-115">RHEL</span></span>                     | <span data-ttu-id="28126-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="28126-116">.NET Core 2.1</span></span> | <span data-ttu-id="28126-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="28126-117">.NET Core 3.1</span></span> | <span data-ttu-id="28126-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="28126-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="28126-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="28126-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="28126-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="28126-120">✔️ 2.1</span></span>        | <span data-ttu-id="28126-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="28126-121">✔️ 3.1</span></span>        | <span data-ttu-id="28126-122">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="28126-122">✔️ 5.0</span></span> |
| <span data-ttu-id="28126-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="28126-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="28126-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="28126-124">✔️ 2.1</span></span>        | <span data-ttu-id="28126-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="28126-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="28126-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="28126-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="28126-127">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="28126-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="28126-128">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="28126-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="28126-129">3.0</span><span class="sxs-lookup"><span data-stu-id="28126-129">3.0</span></span>
- <span data-ttu-id="28126-130">2.2</span><span class="sxs-lookup"><span data-stu-id="28126-130">2.2</span></span>
- <span data-ttu-id="28126-131">2.0</span><span class="sxs-lookup"><span data-stu-id="28126-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="28126-132">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="28126-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="28126-133">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="28126-133">How to install other versions</span></span>

<span data-ttu-id="28126-134">Сведения об установке других выпусков .NET см. в [документации по Red Hat для .NET](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="28126-134">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="28126-135">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="28126-135">RHEL 8 ✔️</span></span>

<span data-ttu-id="28126-136">Платформа .NET включена в репозитории AppStream для RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="28126-136">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="28126-137">RHEL 7 ✔️ .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="28126-137">RHEL 7 ✔️ .NET 5.0</span></span>

<span data-ttu-id="28126-138">Следующая команда устанавливает пакет `scl-utils`:</span><span class="sxs-lookup"><span data-stu-id="28126-138">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="28126-139">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="28126-139">Install the SDK</span></span>

<span data-ttu-id="28126-140">Пакет SDK для .NET позволяет разрабатывать приложения с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="28126-140">The .NET SDK allows you to develop apps with .NET .</span></span> <span data-ttu-id="28126-141">При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="28126-141">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="28126-142">Чтобы установить пакет SDK для .NET, выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="28126-142">To install .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="28126-143">В Red Hat не рекомендуется активировать `rh-dotnet50` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="28126-143">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="28126-144">Если вы хотите активировать `rh-dotnet` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="28126-144">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="28126-145">Установка среды выполнения</span><span class="sxs-lookup"><span data-stu-id="28126-145">Install the runtime</span></span>

<span data-ttu-id="28126-146">Среда выполнения .NET позволяет запускать приложения, созданные в версии .NET, не включающей среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="28126-146">The .NET Runtime allows you to run apps that were made with .NET that didn't include the runtime.</span></span> <span data-ttu-id="28126-147">Приведенные ниже команды позволяют установить среду выполнения ASP.NET Core, которая больше всего совместима с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28126-147">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="28126-148">В терминале выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="28126-148">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="28126-149">В Red Hat не рекомендуется активировать `rh-dotnet50` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="28126-149">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="28126-150">Если вы хотите активировать `rh-dotnet50` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="28126-150">If you want to enable `rh-dotnet50` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

<span data-ttu-id="28126-151">В качестве альтернативы среде выполнения ASP.NET Core вы можете установить среду выполнения .NET без поддержки ASP.NET Core. Для этого в приведенных выше командах замените `rh-dotnet50-aspnetcore-runtime-5.0` на `rh-dotnet50-dotnet-runtime-5.0`.</span><span class="sxs-lookup"><span data-stu-id="28126-151">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the commands above with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="28126-152">RHEL 7 ✔️ .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="28126-152">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="28126-153">Следующая команда устанавливает пакет `scl-utils`:</span><span class="sxs-lookup"><span data-stu-id="28126-153">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="28126-154">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="28126-154">Install the SDK</span></span>

<span data-ttu-id="28126-155">Пакет SDK для .NET Core позволяет разрабатывать приложения с помощью .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28126-155">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="28126-156">При установке пакета SDK для .NET Core не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="28126-156">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="28126-157">Чтобы установить пакет SDK для .NET Core, выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="28126-157">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="28126-158">В Red Hat не рекомендуется активировать `rh-dotnet31` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="28126-158">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="28126-159">Например, `rh-dotnet31` включает версию `libcurl`, которая отличается от базовой версии RHEL.</span><span class="sxs-lookup"><span data-stu-id="28126-159">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="28126-160">Это может вызвать проблемы в программах, которые не ожидают другой версии `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="28126-160">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="28126-161">Если вы хотите активировать `rh-dotnet` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="28126-161">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="28126-162">Установка среды выполнения</span><span class="sxs-lookup"><span data-stu-id="28126-162">Install the runtime</span></span>

<span data-ttu-id="28126-163">Среда выполнения .NET Core позволяет запускать приложения, созданные с помощью версии .NET Core без поддержки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="28126-163">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="28126-164">Приведенные ниже команды позволяют установить среду выполнения ASP.NET Core, которая больше всего совместима с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28126-164">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="28126-165">В терминале выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="28126-165">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="28126-166">В Red Hat не рекомендуется активировать `rh-dotnet31` на постоянной основе, так как это может повлиять на другие программы.</span><span class="sxs-lookup"><span data-stu-id="28126-166">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="28126-167">Например, `rh-dotnet31` включает версию `libcurl`, которая отличается от базовой версии RHEL.</span><span class="sxs-lookup"><span data-stu-id="28126-167">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="28126-168">Это может вызвать проблемы в программах, которые не ожидают другой версии `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="28126-168">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="28126-169">Если вы хотите активировать `rh-dotnet31` на постоянной основе, добавьте следующую строку в файл _~/.bashrc_.</span><span class="sxs-lookup"><span data-stu-id="28126-169">If you want to enable `rh-dotnet31` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

<span data-ttu-id="28126-170">В качестве альтернативы среде выполнения ASP.NET Core вы можете установить среду выполнения .NET Core без поддержки ASP.NET Core. Для этого в приведенной выше команде замените `rh-dotnet31-aspnetcore-runtime-3.1` на `rh-dotnet31-dotnet-runtime-3.1`.</span><span class="sxs-lookup"><span data-stu-id="28126-170">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="28126-171">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="28126-171">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="28126-172">Зависимости</span><span class="sxs-lookup"><span data-stu-id="28126-172">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="28126-173">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="28126-173">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="28126-174">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="28126-174">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="28126-175">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="28126-175">Next steps</span></span>

- [<span data-ttu-id="28126-176">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="28126-176">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
