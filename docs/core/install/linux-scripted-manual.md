---
title: Установка .NET в Linux вручную — .NET
description: В этом разделе описывается установка пакета SDK для .NET и среды выполнения .NET в Linux без использования диспетчера пакетов. Для этого можно использовать скрипт установки или извлечь двоичные файлы вручную.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9176f7477cf80c26ef0b5b7c438c47afcb423799
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231301"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="db200-104">Установка пакета SDK для .NET или среды выполнения .NET вручную</span><span class="sxs-lookup"><span data-stu-id="db200-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="db200-105">Платформа .NET поддерживается в Linux. В этой статье описывается установка .NET в Linux с помощью скрипта установки или посредством извлечения двоичных файлов.</span><span class="sxs-lookup"><span data-stu-id="db200-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="db200-106">Список дистрибутивов, поддерживающих встроенный диспетчер пакетов, см. в разделе [Установка .NET в Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="db200-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="db200-107">Также можно установить .NET с помощью пакета Snap.</span><span class="sxs-lookup"><span data-stu-id="db200-107">You can also install .NET with snap.</span></span> <span data-ttu-id="db200-108">Дополнительные сведения см. в разделе [Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap](linux-snap.md).</span><span class="sxs-lookup"><span data-stu-id="db200-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="db200-109">Выпуски .NET</span><span class="sxs-lookup"><span data-stu-id="db200-109">.NET releases</span></span>

<span data-ttu-id="db200-110">В следующей таблице перечислены выпуски .NET (и .NET Core):</span><span class="sxs-lookup"><span data-stu-id="db200-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="db200-111">✔️ Поддерживается</span><span class="sxs-lookup"><span data-stu-id="db200-111">✔️ Supported</span></span> | <span data-ttu-id="db200-112">❌ Не поддерживается</span><span class="sxs-lookup"><span data-stu-id="db200-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="db200-113">5,0</span><span class="sxs-lookup"><span data-stu-id="db200-113">5.0</span></span>         | <span data-ttu-id="db200-114">3.0</span><span class="sxs-lookup"><span data-stu-id="db200-114">3.0</span></span>           |
| <span data-ttu-id="db200-115">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="db200-115">3.1 (LTS)</span></span>   | <span data-ttu-id="db200-116">2.2</span><span class="sxs-lookup"><span data-stu-id="db200-116">2.2</span></span>           |
| <span data-ttu-id="db200-117">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="db200-117">2.1 (LTS)</span></span>   | <span data-ttu-id="db200-118">2,0</span><span class="sxs-lookup"><span data-stu-id="db200-118">2.0</span></span>           |
|             | <span data-ttu-id="db200-119">1,1</span><span class="sxs-lookup"><span data-stu-id="db200-119">1.1</span></span>           |
|             | <span data-ttu-id="db200-120">1.0</span><span class="sxs-lookup"><span data-stu-id="db200-120">1.0</span></span>           |

<span data-ttu-id="db200-121">Дополнительные сведения о жизненном цикле выпусков .NET см. в разделе [Политика поддержки .NET Core и .NET 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="db200-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="db200-122">Зависимости</span><span class="sxs-lookup"><span data-stu-id="db200-122">Dependencies</span></span>

<span data-ttu-id="db200-123">В некоторых случаях, например при [установке .NET вручную](#manual-install), некоторые зависимости могут не устанавливаться.</span><span class="sxs-lookup"><span data-stu-id="db200-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="db200-124">Ниже перечислены дистрибутивы Linux, которые поддерживаются корпорацией Майкрософт и для которых может потребоваться установка зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db200-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="db200-125">Дополнительные сведения см. на странице, посвященной соответствующему дистрибутиву:</span><span class="sxs-lookup"><span data-stu-id="db200-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="db200-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="db200-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="db200-127">Debian</span><span class="sxs-lookup"><span data-stu-id="db200-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="db200-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="db200-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="db200-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="db200-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="db200-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="db200-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="db200-131">SLES</span><span class="sxs-lookup"><span data-stu-id="db200-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="db200-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="db200-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="db200-133">Общие сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="db200-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="db200-134">Зависимости RPM</span><span class="sxs-lookup"><span data-stu-id="db200-134">RPM dependencies</span></span>

<span data-ttu-id="db200-135">Если ваш дистрибутив не указан в приведенном выше списке и построен на основе RPM, могут потребоваться следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="db200-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="db200-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="db200-136">krb5-libs</span></span>
- <span data-ttu-id="db200-137">libicu</span><span class="sxs-lookup"><span data-stu-id="db200-137">libicu</span></span>
- <span data-ttu-id="db200-138">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="db200-138">openssl-libs</span></span>

<span data-ttu-id="db200-139">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="db200-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="db200-140">Зависимости DEB</span><span class="sxs-lookup"><span data-stu-id="db200-140">DEB dependencies</span></span>

<span data-ttu-id="db200-141">Если ваш дистрибутив не указан в приведенном выше списке и построен на основе Debian, могут потребоваться следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="db200-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="db200-142">libc6</span><span class="sxs-lookup"><span data-stu-id="db200-142">libc6</span></span>
- <span data-ttu-id="db200-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="db200-143">libgcc1</span></span>
- <span data-ttu-id="db200-144">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="db200-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="db200-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="db200-145">libicu67</span></span>
- <span data-ttu-id="db200-146">libssl1.1</span><span class="sxs-lookup"><span data-stu-id="db200-146">libssl1.1</span></span>
- <span data-ttu-id="db200-147">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="db200-147">libstdc++6</span></span>
- <span data-ttu-id="db200-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="db200-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="db200-149">Общие зависимости</span><span class="sxs-lookup"><span data-stu-id="db200-149">Common dependencies</span></span>

<span data-ttu-id="db200-150">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="db200-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="db200-151">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="db200-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="db200-152">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="db200-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="db200-153">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="db200-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="db200-154">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="db200-154">Scripted install</span></span>

<span data-ttu-id="db200-155">[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации установок **пакета SDK** и **среды выполнения** и осуществления таких установок без прав администратора.</span><span class="sxs-lookup"><span data-stu-id="db200-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="db200-156">Скрипт можно скачать на странице <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="db200-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

> <span data-ttu-id="db200-157">![ВАЖНО] Для выполнения скрипта требуется Bash.</span><span class="sxs-lookup"><span data-stu-id="db200-157">![IMPORTANT] Bash is required to run the script.</span></span>

<span data-ttu-id="db200-158">Этот сценарий по умолчанию устанавливает последнюю версию SDK [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="db200-158">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="db200-159">Чтобы установить текущий выпуск, который может не быть версией LTS, используйте параметр `-c Current`.</span><span class="sxs-lookup"><span data-stu-id="db200-159">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="db200-160">Чтобы вместо пакета SDK установить среду выполнения .NET, используйте параметр `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="db200-160">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="db200-161">Вы можете установить определенную версию, указав ее в параметре `-c`.</span><span class="sxs-lookup"><span data-stu-id="db200-161">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="db200-162">Следующая команда устанавливает пакет SDK для .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="db200-162">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="db200-163">Дополнительные сведения см. в статье [Справка по скриптам dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="db200-163">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="db200-164">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="db200-164">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="db200-165">В качестве альтернативы диспетчерам пакетов можно скачать и вручную установить пакет SDK и среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="db200-165">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="db200-166">Ручная установка как правило выполняется в рамках тестирования непрерывной интеграции или в неподдерживаемом дистрибутиве Linux.</span><span class="sxs-lookup"><span data-stu-id="db200-166">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="db200-167">В большинстве случаев разработчикам и пользователям рекомендуется использовать диспетчер пакетов.</span><span class="sxs-lookup"><span data-stu-id="db200-167">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="db200-168">При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="db200-168">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="db200-169">Сначала скачайте **двоичный** выпуск пакета SDK или среды выполнения с одного из следующих сайтов:</span><span class="sxs-lookup"><span data-stu-id="db200-169">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="db200-170">✔️ [Скачиваемые файлы для .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="db200-170">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="db200-171">✔️ [Скачиваемые файлы .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)</span><span class="sxs-lookup"><span data-stu-id="db200-171">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet/3.1)</span></span>
- <span data-ttu-id="db200-172">✔️ [Скачиваемые файлы .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet/2.1)</span><span class="sxs-lookup"><span data-stu-id="db200-172">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet/2.1)</span></span>
- [<span data-ttu-id="db200-173">Все скачиваемые файлы для .NET Core</span><span class="sxs-lookup"><span data-stu-id="db200-173">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="db200-174">Извлеките скачанный файл и используйте команду `export`, чтобы задать переменные, используемые .NET, а затем проверьте включение .NET в переменную PATH.</span><span class="sxs-lookup"><span data-stu-id="db200-174">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="db200-175">Чтобы извлечь среду выполнения и сделать команды .NET CLI доступными в терминале, сначала скачайте двоичный выпуск .NET.</span><span class="sxs-lookup"><span data-stu-id="db200-175">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="db200-176">Затем откройте терминал и выполните следующие команды в каталоге с сохраненным файлом.</span><span class="sxs-lookup"><span data-stu-id="db200-176">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="db200-177">Имя файла архива может отличаться в зависимости от скачанных файлов.</span><span class="sxs-lookup"><span data-stu-id="db200-177">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="db200-178">**Используйте следующие команды для извлечения скачанной среды выполнения или пакета SDK.**</span><span class="sxs-lookup"><span data-stu-id="db200-178">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="db200-179">Не забудьте заменить значение `DOTNET_FILE` на имя файла:</span><span class="sxs-lookup"><span data-stu-id="db200-179">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="db200-180">Приведенные выше команды `export` сделают команды .NET CLI доступными только для сеанса терминала, в котором производился запуск.</span><span class="sxs-lookup"><span data-stu-id="db200-180">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="db200-181">Вы можете изменить профиль оболочки, чтобы добавить команды окончательно.</span><span class="sxs-lookup"><span data-stu-id="db200-181">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="db200-182">Существует несколько различных оболочек, доступных для Linux, и каждая из них имеет свой профиль.</span><span class="sxs-lookup"><span data-stu-id="db200-182">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="db200-183">Пример:</span><span class="sxs-lookup"><span data-stu-id="db200-183">For example:</span></span>
>
> - <span data-ttu-id="db200-184">**Оболочка Bash**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="db200-184">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="db200-185">**Оболочка Korn**: *~/.kshrc* или *.profile*</span><span class="sxs-lookup"><span data-stu-id="db200-185">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="db200-186">**Оболочка Z**: *~/.zshrc* или *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="db200-186">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="db200-187">Измените соответствующий исходный файл оболочки и добавьте `:$HOME/dotnet` в конец существующего оператора `PATH`.</span><span class="sxs-lookup"><span data-stu-id="db200-187">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="db200-188">Если оператор `PATH` не указан, добавьте новую строку с `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="db200-188">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="db200-189">Кроме того, добавьте `export DOTNET_ROOT=$HOME/dotnet` в конец файла.</span><span class="sxs-lookup"><span data-stu-id="db200-189">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="db200-190">Такой подход позволяет устанавливать разные версии в отдельные расположения и выбирать, какие из них следует использовать для каждого приложения.</span><span class="sxs-lookup"><span data-stu-id="db200-190">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="db200-191">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="db200-191">Next steps</span></span>

- [<span data-ttu-id="db200-192">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="db200-192">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="db200-193">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="db200-193">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
