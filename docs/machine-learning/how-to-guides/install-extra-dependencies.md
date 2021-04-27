---
title: Установка дополнительных зависимостей ML.NET
description: Сведения о том, как установить собственные библиотеки, от которых зависят пакеты ML.NET, но которые не устанавливаются вместе с пакетами NuGet.
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 2cff99cfa8a29ac87db69968025ea1081ddde81d
ms.sourcegitcommit: 02cc87f02c46e603ea5925de95af746b7ab46a35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2021
ms.locfileid: "107954709"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="98673-103">Установка дополнительных зависимостей ML.NET</span><span class="sxs-lookup"><span data-stu-id="98673-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="98673-104">В большинстве случаев во всех операционных системах установка ML.NET выполняется так же просто, как и ссылка на соответствующий пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="98673-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="98673-105">Однако в некоторых случаях применяются дополнительные требования к установке, особенно если требуются собственные компоненты.</span><span class="sxs-lookup"><span data-stu-id="98673-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="98673-106">В этом документе описаны требования к установке для этих случаев.</span><span class="sxs-lookup"><span data-stu-id="98673-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="98673-107">Разделы упорядочены по конкретным пакетам `Microsoft.ML.*` NuGet, имеющим дополнительную зависимость.</span><span class="sxs-lookup"><span data-stu-id="98673-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="98673-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="98673-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="98673-109">Оба этих пакета имеют зависимость от `Microsoft.ML.MKL.Redist`, который зависит от `libomp`.</span><span class="sxs-lookup"><span data-stu-id="98673-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="98673-110">Windows</span><span class="sxs-lookup"><span data-stu-id="98673-110">Windows</span></span>

<span data-ttu-id="98673-111">Дополнительные шаги установки не требуются.</span><span class="sxs-lookup"><span data-stu-id="98673-111">No extra installation steps required.</span></span> <span data-ttu-id="98673-112">Библиотека устанавливается при добавлении пакета NuGet в проект.</span><span class="sxs-lookup"><span data-stu-id="98673-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="98673-113">Linux</span><span class="sxs-lookup"><span data-stu-id="98673-113">Linux</span></span>

1. <span data-ttu-id="98673-114">Установка ключа GPG для репозитория</span><span class="sxs-lookup"><span data-stu-id="98673-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="98673-115">Добавление репозитория APT для MKL</span><span class="sxs-lookup"><span data-stu-id="98673-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="98673-116">Обновление пакетов</span><span class="sxs-lookup"><span data-stu-id="98673-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="98673-117">Установка MKL</span><span class="sxs-lookup"><span data-stu-id="98673-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="98673-118">Пример:</span><span class="sxs-lookup"><span data-stu-id="98673-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="98673-119">Определите расположение `libiomp.so`:</span><span class="sxs-lookup"><span data-stu-id="98673-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="98673-120">Пример:</span><span class="sxs-lookup"><span data-stu-id="98673-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="98673-121">Добавьте это расположение в путь к библиотеке загрузки:</span><span class="sxs-lookup"><span data-stu-id="98673-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="98673-122">Mac</span><span class="sxs-lookup"><span data-stu-id="98673-122">Mac</span></span>

1. <span data-ttu-id="98673-123">Установите библиотеку с помощью `Homebrew`:</span><span class="sxs-lookup"><span data-stu-id="98673-123">Install the library with `Homebrew`</span></span>

    ```bash
    wget https://raw.githubusercontent.com/Homebrew/homebrew-core/fb8323f2b170bd4ae97e1bac9bf3e2983af3fdb0/Formula/libomp.rb && brew install ./libomp.rb && brew link libomp --force
    ```
