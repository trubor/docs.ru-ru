---
title: Телеметрия пакета SDK для .NET
description: Сведения о функциях телеметрии пакета SDK для .NET, позволяющих собирать сведения об использовании для анализа, а также о собираемых данных и способе отключения этих функций.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 137b703dc9369f09fb535af40edf057e4e02117a
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757841"
---
# <a name="net-sdk-telemetry"></a><span data-ttu-id="ac593-103">Телеметрия пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="ac593-103">.NET SDK telemetry</span></span>

<span data-ttu-id="ac593-104">[Пакет SDK для .NET](index.md) включает функцию телеметрии, которая собирает данные об использовании и сведения об исключениях при сбоях .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="ac593-104">The [.NET SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET CLI crashes.</span></span> <span data-ttu-id="ac593-105">.NET CLI поставляется с пакетом SDK для .NET и представляет собой набор команд, позволяющих создавать, тестировать и публиковать приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="ac593-105">The .NET CLI comes with the .NET SDK and is the set of verbs that enable you to build, test, and publish your .NET apps.</span></span> <span data-ttu-id="ac593-106">Команде разработчиков .NET важно знать, как используются эти средства, чтобы их можно было улучшить.</span><span class="sxs-lookup"><span data-stu-id="ac593-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="ac593-107">Сведения об ошибках помогают команде решать проблемы и устранять ошибки.</span><span class="sxs-lookup"><span data-stu-id="ac593-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="ac593-108">Данные публикуются в сводной форме по [лицензии Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="ac593-108">The collected data is published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="ac593-109">Область</span><span class="sxs-lookup"><span data-stu-id="ac593-109">Scope</span></span>

<span data-ttu-id="ac593-110">`dotnet` имеет две функции: для запуска приложений и для выполнения команд CLI.</span><span class="sxs-lookup"><span data-stu-id="ac593-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="ac593-111">Данные телеметрии *не собираются* при использовании `dotnet` для запуска приложения в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="ac593-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="ac593-112">Данные телеметрии *собираются* при использовании [команд CLI .NET](index.md), например:</span><span class="sxs-lookup"><span data-stu-id="ac593-112">Telemetry *is collected* when using any of the [.NET CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="ac593-113">Как отключить функцию</span><span class="sxs-lookup"><span data-stu-id="ac593-113">How to opt out</span></span>

<span data-ttu-id="ac593-114">Функция телеметрии пакета SDK для .NET по умолчанию включена.</span><span class="sxs-lookup"><span data-stu-id="ac593-114">The .NET SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="ac593-115">Чтобы отключить ее, присвойте переменной среды `DOTNET_CLI_TELEMETRY_OPTOUT` значение `1` или `true`.</span><span class="sxs-lookup"><span data-stu-id="ac593-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="ac593-116">При успешной установке программа установки пакета SDK для .NET отправляет единую запись телеметрии.</span><span class="sxs-lookup"><span data-stu-id="ac593-116">A single telemetry entry is also sent by the .NET SDK installer when a successful installation happens.</span></span> <span data-ttu-id="ac593-117">Чтобы отказаться от этого, задайте переменную среды `DOTNET_CLI_TELEMETRY_OPTOUT` перед установкой пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="ac593-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET SDK.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac593-118">Чтобы отказаться от отправки данных телеметрии после запуска установщика, закройте установщик, задайте переменную среды, а затем снова запустите установщик с заданной переменной среды.</span><span class="sxs-lookup"><span data-stu-id="ac593-118">To opt out after you started the installer: close the installer, set the environment variable, and then run the installer again with that value set.</span></span>

## <a name="disclosure"></a><span data-ttu-id="ac593-119">Раскрытие информации</span><span class="sxs-lookup"><span data-stu-id="ac593-119">Disclosure</span></span>

<span data-ttu-id="ac593-120">При первом выполнении одной из [команд .NET CLI](index.md) (например, `dotnet build`) пакет SDK для .NET выводит следующий текст.</span><span class="sxs-lookup"><span data-stu-id="ac593-120">The .NET SDK displays text similar to the following when you first run one of the [.NET CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="ac593-121">Он может немного отличаться в зависимости от используемой версии пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="ac593-121">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="ac593-122">Именно таким образом корпорация Майкрософт уведомляет вас о сборе данных.</span><span class="sxs-lookup"><span data-stu-id="ac593-122">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="ac593-123">Чтобы отключить отображение этого сообщения и приветственного сообщения .NET, задайте для переменной среды `DOTNET_NOLOGO` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="ac593-123">To disable this message and the .NET welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="ac593-124">Обратите внимание, что эта переменная не влияет на отказ от отправки данных телеметрии.</span><span class="sxs-lookup"><span data-stu-id="ac593-124">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="ac593-125">Точки данных</span><span class="sxs-lookup"><span data-stu-id="ac593-125">Data points</span></span>

<span data-ttu-id="ac593-126">Функция телеметрии не собирает персональные данные, например имена пользователей и их адреса электронной почты.</span><span class="sxs-lookup"><span data-stu-id="ac593-126">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="ac593-127">Она не проверяет код и не извлекает данные уровня проекта, например имя, репозиторий или автора.</span><span class="sxs-lookup"><span data-stu-id="ac593-127">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="ac593-128">Данные отправляются по защищенному протоколу на серверы Майкрософт с помощью технологии [Azure Monitor](https://azure.microsoft.com/services/monitor/), хранятся в режиме ограниченного доступа и используются в защищенных системах [хранилища Azure](https://azure.microsoft.com/services/storage/) с соблюдением строгих мер безопасности.</span><span class="sxs-lookup"><span data-stu-id="ac593-128">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="ac593-129">Мы заботимся о вашей конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="ac593-129">Protecting your privacy is important to us.</span></span> <span data-ttu-id="ac593-130">Если у вас есть подозрения, что функция телеметрии собирает конфиденциальные данные или что мы обрабатываем данные небезопасным либо неподобающим образом, отправьте сообщение о проблеме в репозитории [dotnet/sdk](https://github.com/dotnet/sdk/issues) или по адресу [dotnet@microsoft.com](mailto:dotnet@microsoft.com) для изучения.</span><span class="sxs-lookup"><span data-stu-id="ac593-130">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="ac593-131">Функция телеметрии собирает следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ac593-131">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="ac593-132">Версии пакета SDK</span><span class="sxs-lookup"><span data-stu-id="ac593-132">SDK versions</span></span> | <span data-ttu-id="ac593-133">Данные</span><span class="sxs-lookup"><span data-stu-id="ac593-133">Data</span></span> |
|--------------|------|
| <span data-ttu-id="ac593-134">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-134">All</span></span>          | <span data-ttu-id="ac593-135">Метка времени вызова.</span><span class="sxs-lookup"><span data-stu-id="ac593-135">Timestamp of invocation.</span></span> |
| <span data-ttu-id="ac593-136">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-136">All</span></span>          | <span data-ttu-id="ac593-137">Вызываемая команда (например, build), хэшируется с версии 2.1.</span><span class="sxs-lookup"><span data-stu-id="ac593-137">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="ac593-138">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-138">All</span></span>          | <span data-ttu-id="ac593-139">Состоящий из трех октетов IP-адрес, используемый для определения географического местоположения.</span><span class="sxs-lookup"><span data-stu-id="ac593-139">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="ac593-140">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-140">All</span></span>          | <span data-ttu-id="ac593-141">Операционная система и ее версия.</span><span class="sxs-lookup"><span data-stu-id="ac593-141">Operating system and version.</span></span> |
| <span data-ttu-id="ac593-142">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-142">All</span></span>          | <span data-ttu-id="ac593-143">Идентификатор среды выполнения (RID), в которой работает пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="ac593-143">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="ac593-144">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-144">All</span></span>          | <span data-ttu-id="ac593-145">Версия пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="ac593-145">.NET SDK version.</span></span> |
| <span data-ttu-id="ac593-146">Все</span><span class="sxs-lookup"><span data-stu-id="ac593-146">All</span></span>          | <span data-ttu-id="ac593-147">Профиль телеметрии: необязательное значение используется только при явном включении пользователем и внутри корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="ac593-147">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="ac593-148">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-148">>=2.0</span></span>        | <span data-ttu-id="ac593-149">Аргументы и параметры команды: собираются только известные аргументы и параметры (но не произвольные строки).</span><span class="sxs-lookup"><span data-stu-id="ac593-149">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="ac593-150">См. раздел о [собираемых параметрах](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="ac593-150">See [collected options](#collected-options).</span></span> <span data-ttu-id="ac593-151">Хэшируется после версии 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ac593-151">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="ac593-152">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-152">>=2.0</span></span>         | <span data-ttu-id="ac593-153">выполняется ли пакет SDK в контейнере;</span><span class="sxs-lookup"><span data-stu-id="ac593-153">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="ac593-154">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-154">>=2.0</span></span>         | <span data-ttu-id="ac593-155">Целевые платформы (из события `TargetFramework`), хэшируются начиная с версии 2.1.</span><span class="sxs-lookup"><span data-stu-id="ac593-155">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="ac593-156">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-156">>=2.0</span></span>         | <span data-ttu-id="ac593-157">Адрес управления доступом к среде передачи данных (MAC-адрес) с хэшированием (SHA256).</span><span class="sxs-lookup"><span data-stu-id="ac593-157">Hashed Media Access Control (MAC) address (SHA256).</span></span> |
| <span data-ttu-id="ac593-158">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-158">>=2.0</span></span>         | <span data-ttu-id="ac593-159">хэшированный текущий рабочий каталог.</span><span class="sxs-lookup"><span data-stu-id="ac593-159">Hashed current working directory.</span></span> |
| <span data-ttu-id="ac593-160">>= 2.0</span><span class="sxs-lookup"><span data-stu-id="ac593-160">>=2.0</span></span>         | <span data-ttu-id="ac593-161">Отчет об успешном выполнении установки с хэшированным именем EXE-файла установщика.</span><span class="sxs-lookup"><span data-stu-id="ac593-161">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="ac593-162">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="ac593-162">>=2.1.300</span></span>     | <span data-ttu-id="ac593-163">Версия ядра.</span><span class="sxs-lookup"><span data-stu-id="ac593-163">Kernel version.</span></span> |
| <span data-ttu-id="ac593-164">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="ac593-164">>=2.1.300</span></span>     | <span data-ttu-id="ac593-165">Выпуск или версия libc.</span><span class="sxs-lookup"><span data-stu-id="ac593-165">Libc release/version.</span></span> |
| <span data-ttu-id="ac593-166">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="ac593-166">>=3.0.100</span></span>     | <span data-ttu-id="ac593-167">Были ли перенаправлены выходные данные (true или false).</span><span class="sxs-lookup"><span data-stu-id="ac593-167">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="ac593-168">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="ac593-168">>=3.0.100</span></span>     | <span data-ttu-id="ac593-169">При сбое интерфейса командной строки или пакета SDK тип исключения и его трассировка стека (в отправляемую трассировку стека включается только код CLI или SDK).</span><span class="sxs-lookup"><span data-stu-id="ac593-169">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="ac593-170">Дополнительные сведения см. в разделе [Сбор данных телеметрии об исключениях при сбоях .NET CLI и SDK](#net-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="ac593-170">For more information, see [.NET CLI/SDK crash exception telemetry collected](#net-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="ac593-171">Собираемые параметры</span><span class="sxs-lookup"><span data-stu-id="ac593-171">Collected options</span></span>

<span data-ttu-id="ac593-172">Некоторые команды отправляют дополнительные данные.</span><span class="sxs-lookup"><span data-stu-id="ac593-172">Certain commands send additional data.</span></span> <span data-ttu-id="ac593-173">Подмножество команд отправляет первый аргумент:</span><span class="sxs-lookup"><span data-stu-id="ac593-173">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="ac593-174">Команда</span><span class="sxs-lookup"><span data-stu-id="ac593-174">Command</span></span>               | <span data-ttu-id="ac593-175">Данные первого аргумента отправлены</span><span class="sxs-lookup"><span data-stu-id="ac593-175">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="ac593-176">Запрашивается справка по командам.</span><span class="sxs-lookup"><span data-stu-id="ac593-176">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="ac593-177">Имя шаблона (хэшированное).</span><span class="sxs-lookup"><span data-stu-id="ac593-177">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="ac593-178">Слово `package` или `reference`.</span><span class="sxs-lookup"><span data-stu-id="ac593-178">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="ac593-179">Слово `package` или `reference`.</span><span class="sxs-lookup"><span data-stu-id="ac593-179">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="ac593-180">Слово `package` или `reference`.</span><span class="sxs-lookup"><span data-stu-id="ac593-180">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="ac593-181">Слово `add`, `list` или `remove`.</span><span class="sxs-lookup"><span data-stu-id="ac593-181">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="ac593-182">Слово `delete`, `locals` или `push`.</span><span class="sxs-lookup"><span data-stu-id="ac593-182">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="ac593-183">Подмножество команд отправляет выбранные параметры, если они используются, а также их значения:</span><span class="sxs-lookup"><span data-stu-id="ac593-183">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="ac593-184">Параметр</span><span class="sxs-lookup"><span data-stu-id="ac593-184">Option</span></span>                  | <span data-ttu-id="ac593-185">Команды</span><span class="sxs-lookup"><span data-stu-id="ac593-185">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="ac593-186">Все команды</span><span class="sxs-lookup"><span data-stu-id="ac593-186">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="ac593-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="ac593-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="ac593-188">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="ac593-188">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="ac593-189">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="ac593-189">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="ac593-190">За исключением `--verbosity` и `--sdk-package-version` все остальные значения хэшируются, начиная с пакета SDK для .NET Core 2.1.100.</span><span class="sxs-lookup"><span data-stu-id="ac593-190">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="ac593-191">Сбор данных телеметрии об исключениях при сбоях .NET CLI и SDK</span><span class="sxs-lookup"><span data-stu-id="ac593-191">.NET CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="ac593-192">В случае сбоя .NET CLI или пакета SDK он собирает имя исключения и трассировку стека кода CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="ac593-192">If the .NET CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="ac593-193">Эти сведения собираются для оценки проблем и улучшения качества пакета SDK для .NET и интерфейса командной строки.</span><span class="sxs-lookup"><span data-stu-id="ac593-193">This information is collected to assess problems and improve the quality of the .NET SDK and CLI.</span></span> <span data-ttu-id="ac593-194">В этой статье приводятся сведения о данных, которые мы собираем.</span><span class="sxs-lookup"><span data-stu-id="ac593-194">This article provides information about the data we collect.</span></span> <span data-ttu-id="ac593-195">Кроме того, она содержит советы, помогающие пользователям, создающим собственную версию пакета SDK для .NET, избежать случайного раскрытия персональных или конфиденциальных сведений.</span><span class="sxs-lookup"><span data-stu-id="ac593-195">It also provides tips on how users building their own version of the .NET SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="ac593-196">Типы собираемых данных</span><span class="sxs-lookup"><span data-stu-id="ac593-196">Types of collected data</span></span>

<span data-ttu-id="ac593-197">.NET CLI собирает сведения только об исключениях CLI/SDK, а не об исключениях в приложении.</span><span class="sxs-lookup"><span data-stu-id="ac593-197">.NET CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="ac593-198">Собранные данные содержат имя исключения и трассировку стека.</span><span class="sxs-lookup"><span data-stu-id="ac593-198">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="ac593-199">Эта трассировка стека относится к коду CLI или пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="ac593-199">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="ac593-200">В следующем примере показан тип собираемых данных:</span><span class="sxs-lookup"><span data-stu-id="ac593-200">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="ac593-201">Избегайте случайного разглашения информации</span><span class="sxs-lookup"><span data-stu-id="ac593-201">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="ac593-202">Участники .NET и все остальные, кто использует версию пакета SDK для .NET, которую они создали сами, должны учитывать путь к исходному коду пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="ac593-202">.NET contributors and anyone else running a version of the .NET SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="ac593-203">Если сбой происходит при использовании пакета SDK для .NET, который является пользовательской сборкой отладки или настроен с помощью файлов пользовательских символов сборки, путь к исходному файлу пакета SDK с компьютера сборки собирается как часть трассировки стека и не хэшируется.</span><span class="sxs-lookup"><span data-stu-id="ac593-203">If a crash occurs while using a .NET SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="ac593-204">По этой причине пользовательские сборки пакета SDK для .NET не должны размещаться в каталогах, имена путей которых раскрывают персональные или конфиденциальные сведения.</span><span class="sxs-lookup"><span data-stu-id="ac593-204">Because of this, custom builds of the .NET SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac593-205">См. также</span><span class="sxs-lookup"><span data-stu-id="ac593-205">See also</span></span>

- [<span data-ttu-id="ac593-206">Данные телеметрии .NET CLI</span><span class="sxs-lookup"><span data-stu-id="ac593-206">.NET CLI Telemetry Data</span></span>](https://dotnet.microsoft.com/platform/telemetry)
- [<span data-ttu-id="ac593-207">Справочные материалы по телеметрии (репозиторий dotnet/sdk)</span><span class="sxs-lookup"><span data-stu-id="ac593-207">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
