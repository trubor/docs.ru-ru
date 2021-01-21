---
title: Обзор развертывания ReadyToRun
description: Узнайте, что собой представляют развертывания ReadyToRun и зачем их использовать при публикации приложения с помощью .NET 5 и .NET Core 3.0, а также более поздних версий.
author: davidwrighton
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: 2d4aaac2534bbb1279eb88d8e24e1f5f022afe7d
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536103"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="932ca-103">Компиляция ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="932ca-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="932ca-104">Вы можете уменьшить время запуска и задержку приложения .NET, скомпилировав все сборки приложения в формат ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="932ca-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="932ca-105">R2R является разновидностью компиляции AOT.</span><span class="sxs-lookup"><span data-stu-id="932ca-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="932ca-106">Бинарные файлы R2R повышают производительность при запуске, снижая объем работы, выполняемой на этом этапе компилятором JIT.</span><span class="sxs-lookup"><span data-stu-id="932ca-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="932ca-107">Бинарные файлы содержат такой же машинный код, который создается компилятором JIT.</span><span class="sxs-lookup"><span data-stu-id="932ca-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="932ca-108">Но бинарные файлы R2R имеют больший размер, так как содержат не только код на промежуточном языке (IL), который по-прежнему необходим для некоторых сценариев, но и версию того же кода на машинном языке.</span><span class="sxs-lookup"><span data-stu-id="932ca-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="932ca-109">Функция R2R доступна только при публикации приложения, предназначенного для конкретной среды выполнения (RID), например для Windows x64 или Linux x64.</span><span class="sxs-lookup"><span data-stu-id="932ca-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="932ca-110">Чтобы скомпилировать проект в формат ReadyToRun, нужно опубликовать приложение, задав свойство PublishReadyToRun со значением `true`.</span><span class="sxs-lookup"><span data-stu-id="932ca-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to `true`.</span></span>

<span data-ttu-id="932ca-111">Опубликовать приложение в формате ReadyToRun можно двумя способами:</span><span class="sxs-lookup"><span data-stu-id="932ca-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="932ca-112">Укажите флаг PublishReadyToRun непосредственно для команды dotnet publish.</span><span class="sxs-lookup"><span data-stu-id="932ca-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="932ca-113">Дополнительные сведения см. в статье [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="932ca-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="932ca-114">Укажите свойство в проекте.</span><span class="sxs-lookup"><span data-stu-id="932ca-114">Specify the property in the project.</span></span>

    - <span data-ttu-id="932ca-115">Добавьте параметр `<PublishReadyToRun>` в проект.</span><span class="sxs-lookup"><span data-stu-id="932ca-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="932ca-116">Опубликуйте приложение без особых параметров.</span><span class="sxs-lookup"><span data-stu-id="932ca-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="932ca-117">Влияние использования функции ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="932ca-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="932ca-118">Компиляция Ahead Of Time оказывает существенное влияние на производительность приложения, которую может быть трудно спрогнозировать.</span><span class="sxs-lookup"><span data-stu-id="932ca-118">Ahead-of-time compilation has complex performance impact on application performance, which can be difficult to predict.</span></span> <span data-ttu-id="932ca-119">Как правило, размер сборки увеличивается в два или три раза.</span><span class="sxs-lookup"><span data-stu-id="932ca-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="932ca-120">Увеличение физического размера файла может привести к снижению производительности при загрузке сборки с диска и увеличить рабочий набор процесса.</span><span class="sxs-lookup"><span data-stu-id="932ca-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="932ca-121">Но при этом число методов, компилируемых во время выполнения, обычно значительно сокращается.</span><span class="sxs-lookup"><span data-stu-id="932ca-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="932ca-122">В результате большинство приложений с большим объемом кода получают значительные преимущества в отношении производительности, если включена функция ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="932ca-122">The result is that most applications that have large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="932ca-123">Для приложений с небольшим объемом кода, скорее всего, будет трудно заметить значительное улучшение работы, когда функция ReadyToRun включена, так как библиотеки среды выполнения .NET были предварительно скомпилированы с помощью ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="932ca-123">Applications that have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="932ca-124">Такое улучшение относится не только к запуску приложений, но и к первому использованию любого кода в приложении.</span><span class="sxs-lookup"><span data-stu-id="932ca-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="932ca-125">Например, с помощью ReadyToRun можно уменьшить задержку ответа при первом использовании веб-API в приложении ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="932ca-125">For instance, ReadyToRun can be used to reduce the response latency of the first use of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="932ca-126">Взаимодействие с многоуровневой компиляцией</span><span class="sxs-lookup"><span data-stu-id="932ca-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="932ca-127">Код, созданный при компиляции Ahead Of Time, не так хорошо оптимизирован как код, созданный JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="932ca-127">Ahead-of-time generated code is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="932ca-128">Для решения этой проблемы в многоуровневой компиляция часто используемые методы ReadyToRun заменяются методами, созданными JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="932ca-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="932ca-129">Как выбирается набор предварительно скомпилированных сборок</span><span class="sxs-lookup"><span data-stu-id="932ca-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="932ca-130">Пакет SDK реализует предварительную компиляцию сборок, распространяемых вместе с приложением.</span><span class="sxs-lookup"><span data-stu-id="932ca-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="932ca-131">Для автономных приложений в такой набор сборок будет включена платформа.</span><span class="sxs-lookup"><span data-stu-id="932ca-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="932ca-132">Двоичные файлы C++/CLI не подходят для компиляции ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="932ca-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="932ca-133">Как выбирается набор методов для предварительной компиляции</span><span class="sxs-lookup"><span data-stu-id="932ca-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="932ca-134">Компилятор попытается предварительно скомпилировать как можно больше методов.</span><span class="sxs-lookup"><span data-stu-id="932ca-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="932ca-135">Но по ряду причин использование функции ReadyToRun вряд ли помешает JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="932ca-135">However, for various reasons, it's not expected that using the ReadyToRun feature will prevent the JIT from executing.</span></span> <span data-ttu-id="932ca-136">Помимо прочего, к таким причинам могут относиться:</span><span class="sxs-lookup"><span data-stu-id="932ca-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="932ca-137">использование универсальных типов, определенных в отдельных сборках;</span><span class="sxs-lookup"><span data-stu-id="932ca-137">Use of generic types defined in separate assemblies.</span></span>
- <span data-ttu-id="932ca-138">взаимодействие с машинным кодом;</span><span class="sxs-lookup"><span data-stu-id="932ca-138">Interop with native code.</span></span>
- <span data-ttu-id="932ca-139">использование встроенных аппаратных средств, безопасность которых компилятор не может гарантировать для целевого компьютера;</span><span class="sxs-lookup"><span data-stu-id="932ca-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine.</span></span>
- <span data-ttu-id="932ca-140">некоторые нестандартные шаблоны IL;</span><span class="sxs-lookup"><span data-stu-id="932ca-140">Certain unusual IL patterns.</span></span>
- <span data-ttu-id="932ca-141">динамическое создание методов с использованием отражения или LINQ.</span><span class="sxs-lookup"><span data-stu-id="932ca-141">Dynamic method creation via reflection or LINQ.</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="932ca-142">Ограничения при работе с несколькими платформами и архитектурами</span><span class="sxs-lookup"><span data-stu-id="932ca-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="932ca-143">На некоторых платформах SDK компилятор ReadyToRun может выполнять перекрестную компиляцию для других целевых платформ.</span><span class="sxs-lookup"><span data-stu-id="932ca-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="932ca-144">Поддерживаемые целевые платформы для компиляции указаны в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="932ca-144">Supported compilation targets are described in the following table.</span></span>

| <span data-ttu-id="932ca-145">SDK платформы</span><span class="sxs-lookup"><span data-stu-id="932ca-145">SDK platform</span></span> | <span data-ttu-id="932ca-146">Поддерживаемые целевые платформы</span><span class="sxs-lookup"><span data-stu-id="932ca-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="932ca-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="932ca-147">Windows X64</span></span>  | <span data-ttu-id="932ca-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="932ca-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="932ca-149">Windows X86</span><span class="sxs-lookup"><span data-stu-id="932ca-149">Windows X86</span></span>  | <span data-ttu-id="932ca-150">Windows X86, Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="932ca-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="932ca-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="932ca-151">Linux X64</span></span>    | <span data-ttu-id="932ca-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="932ca-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="932ca-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="932ca-153">Linux ARM32</span></span>  | <span data-ttu-id="932ca-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="932ca-154">Linux ARM32</span></span> |
| <span data-ttu-id="932ca-155">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="932ca-155">Linux ARM64</span></span>  | <span data-ttu-id="932ca-156">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="932ca-156">Linux ARM64</span></span> |
| <span data-ttu-id="932ca-157">macOS X64</span><span class="sxs-lookup"><span data-stu-id="932ca-157">macOS X64</span></span>    | <span data-ttu-id="932ca-158">macOS X64</span><span class="sxs-lookup"><span data-stu-id="932ca-158">macOS X64</span></span> |
