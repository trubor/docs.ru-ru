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
# <a name="install-extra-mlnet-dependencies"></a>Установка дополнительных зависимостей ML.NET

В большинстве случаев во всех операционных системах установка ML.NET выполняется так же просто, как и ссылка на соответствующий пакет NuGet.

```dotnetcli
dotnet add package Microsoft.ML
```

Однако в некоторых случаях применяются дополнительные требования к установке, особенно если требуются собственные компоненты. В этом документе описаны требования к установке для этих случаев. Разделы упорядочены по конкретным пакетам `Microsoft.ML.*` NuGet, имеющим дополнительную зависимость.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries, Microsoft.ML.AutoML

Оба этих пакета имеют зависимость от `Microsoft.ML.MKL.Redist`, который зависит от `libomp`.

### <a name="windows"></a>Windows

Дополнительные шаги установки не требуются. Библиотека устанавливается при добавлении пакета NuGet в проект.

### <a name="linux"></a>Linux

1. Установка ключа GPG для репозитория

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

2. Добавление репозитория APT для MKL

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Обновление пакетов

    ```bash
    sudo apt-get update
    ```

4. Установка MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Пример:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Определите расположение `libiomp.so`:

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Пример:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Добавьте это расположение в путь к библиотеке загрузки:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Установите библиотеку с помощью `Homebrew`:

    ```bash
    wget https://raw.githubusercontent.com/Homebrew/homebrew-core/fb8323f2b170bd4ae97e1bac9bf3e2983af3fdb0/Formula/libomp.rb && brew install ./libomp.rb && brew link libomp --force
    ```
