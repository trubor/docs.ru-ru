---
title: Разработка библиотек с помощью .NET CLI
description: Узнайте, как создавать библиотеки для .NET с помощью .NET CLI. Вы создадите библиотеку, которая поддерживает несколько платформ.
author: cartermp
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 76d08007e191fe9090f3f14c906a40e84e37bd19
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548413"
---
# <a name="develop-libraries-with-the-net-cli"></a><span data-ttu-id="da4e1-104">Разработка библиотек с помощью .NET CLI</span><span class="sxs-lookup"><span data-stu-id="da4e1-104">Develop libraries with the .NET CLI</span></span>

<span data-ttu-id="da4e1-105">В этой статье показано, как создавать библиотеки для .NET с помощью .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="da4e1-105">This article covers how to write libraries for .NET using the .NET CLI.</span></span> <span data-ttu-id="da4e1-106">CLI предоставляет эффективный и низкоуровневый интерфейс, работающий в любых поддерживаемых операционных системах.</span><span class="sxs-lookup"><span data-stu-id="da4e1-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="da4e1-107">Вы по-прежнему можете создавать библиотеки с помощью Visual Studio. Если вы предпочитаете такой способ, обратитесь к [руководству по Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="da4e1-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da4e1-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="da4e1-108">Prerequisites</span></span>

<span data-ttu-id="da4e1-109">На компьютере должен быть установлен [пакет SDK для .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="da4e1-109">You need the [.NET SDK](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="da4e1-110">При работе с разделами, в которых используются различные версии .NET Framework, на компьютере с ОС Windows должна быть установлена платформа [.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="da4e1-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com/download/dotnet-framework) installed on a Windows machine.</span></span>

<span data-ttu-id="da4e1-111">Кроме того, если необходимо поддерживать целевые платформы .NET Framework предыдущих версий, требуется установить целевые пакеты или пакеты разработчиков со [страницы с доступными для скачивания файлами для .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework)</span><span class="sxs-lookup"><span data-stu-id="da4e1-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET Framework downloads page](https://dotnet.microsoft.com/download/dotnet-framework).</span></span> <span data-ttu-id="da4e1-112">См. таблицу ниже.</span><span class="sxs-lookup"><span data-stu-id="da4e1-112">Refer to this table:</span></span>

| <span data-ttu-id="da4e1-113">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="da4e1-113">.NET Framework version</span></span> | <span data-ttu-id="da4e1-114">Скачиваемые компоненты</span><span class="sxs-lookup"><span data-stu-id="da4e1-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="da4e1-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="da4e1-115">4.6.1</span></span>                  | <span data-ttu-id="da4e1-116">.NET Framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="da4e1-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="da4e1-117">4.6</span><span class="sxs-lookup"><span data-stu-id="da4e1-117">4.6</span></span>                    | <span data-ttu-id="da4e1-118">.NET Framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="da4e1-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="da4e1-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="da4e1-119">4.5.2</span></span>                  | <span data-ttu-id="da4e1-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="da4e1-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="da4e1-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="da4e1-121">4.5.1</span></span>                  | <span data-ttu-id="da4e1-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="da4e1-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="da4e1-123">4.5</span><span class="sxs-lookup"><span data-stu-id="da4e1-123">4.5</span></span>                    | <span data-ttu-id="da4e1-124">Пакет средств разработки программного обеспечения Windows для Windows 8</span><span class="sxs-lookup"><span data-stu-id="da4e1-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="da4e1-125">4,0</span><span class="sxs-lookup"><span data-stu-id="da4e1-125">4.0</span></span>                    | <span data-ttu-id="da4e1-126">Пакет SDK для Windows 7 и .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="da4e1-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="da4e1-127">2.0, 3.0 и 3.5</span><span class="sxs-lookup"><span data-stu-id="da4e1-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="da4e1-128">Среда выполнения .NET Framework 3.5 с пакетом обновления 1 (SP1) (либо версия для Windows 8 или более поздняя)</span><span class="sxs-lookup"><span data-stu-id="da4e1-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-50-or-net-standard"></a><span data-ttu-id="da4e1-129">Нацеливание на .NET 5.0 или .NET Standard</span><span class="sxs-lookup"><span data-stu-id="da4e1-129">How to target .NET 5.0 or .NET Standard</span></span>

<span data-ttu-id="da4e1-130">Вы можете управлять целевой платформой проекта, добавив его в файл проекта (*CSPROJ* или *FSPROJ*).</span><span class="sxs-lookup"><span data-stu-id="da4e1-130">You control your project's target framework by adding it to your project file (*.csproj* or *.fsproj*).</span></span> <span data-ttu-id="da4e1-131">Инструкции по выбору между нацеливанием на .NET 5.0 и .NET Standard см. в разделе [.NET 5 и .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span><span class="sxs-lookup"><span data-stu-id="da4e1-131">For guidance on how to choose between targeting .NET 5.0 or .NET Standard see [.NET 5 and .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="da4e1-132">Если требуется нацеливание на .NET Framework версии 4.0 или более ранней или использование интерфейса API, доступного в .NET Framework, но не в .NET Standard (например, `System.Drawing`), прочитайте следующие подразделы, чтобы узнать, как осуществляется настройка для разных версий.</span><span class="sxs-lookup"><span data-stu-id="da4e1-132">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="da4e1-133">Нацеливание на .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-133">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="da4e1-134">В этих инструкциях предполагается, что на компьютере установлена платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-134">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="da4e1-135">Чтобы установить зависимости, обратитесь к разделу [Предварительные требования](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="da4e1-135">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="da4e1-136">Имейте в виду, что некоторые используемые здесь версии .NET Framework больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="da4e1-136">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="da4e1-137">Сведения о неподдерживаемых версиях см. в статье [Вопросы и ответы о политике по срокам поддержки Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us).</span><span class="sxs-lookup"><span data-stu-id="da4e1-137">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="da4e1-138">Чтобы охватить максимальное количество разработчиков и проектов, используйте .NET Framework 4.0 в качестве базовой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="da4e1-138">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="da4e1-139">Для нацеливания на .NET Framework начните использовать правильный моникер целевой платформы (TFM), соответствующий версии .NET Framework, которая должна поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="da4e1-139">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="da4e1-140">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="da4e1-140">.NET Framework version</span></span> | <span data-ttu-id="da4e1-141">TFM</span><span class="sxs-lookup"><span data-stu-id="da4e1-141">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="da4e1-142">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="da4e1-142">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="da4e1-143">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="da4e1-143">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="da4e1-144">.NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="da4e1-144">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="da4e1-145">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="da4e1-145">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="da4e1-146">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="da4e1-146">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="da4e1-147">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="da4e1-147">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="da4e1-148">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="da4e1-148">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="da4e1-149">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="da4e1-149">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="da4e1-150">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="da4e1-150">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="da4e1-151">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="da4e1-151">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="da4e1-152">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="da4e1-152">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="da4e1-153">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="da4e1-153">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="da4e1-154">Вставьте этот моникер целевой платформы в раздел `TargetFramework` файла проекта.</span><span class="sxs-lookup"><span data-stu-id="da4e1-154">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="da4e1-155">Например, вот как создать библиотеку, предназначенную для .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="da4e1-155">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="da4e1-156">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="da4e1-156">And that's it!</span></span> <span data-ttu-id="da4e1-157">Хотя эта библиотека компилируется только для .NET Framework 4, ее можно использовать в более поздних версиях .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-157">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="da4e1-158">Настройка для различных версий</span><span class="sxs-lookup"><span data-stu-id="da4e1-158">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="da4e1-159">В приведенных ниже инструкциях предполагается, что на компьютере установлена платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-159">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="da4e1-160">Сведения о зависимостях, которые необходимо установить, и о том, где их можно скачать, см. в разделе [Предварительные требования](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="da4e1-160">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="da4e1-161">Если проект поддерживает как .NET Framework, так и .NET, может потребоваться нацеливание на более старые версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-161">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET.</span></span> <span data-ttu-id="da4e1-162">В такой ситуации, если вам нужно применять более новые интерфейсы API и языковые конструкции для новых целевых платформ, используйте директивы `#if` в коде.</span><span class="sxs-lookup"><span data-stu-id="da4e1-162">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="da4e1-163">Кроме того, может потребоваться добавить разные пакеты и зависимости для каждой целевой платформы, чтобы включить различные интерфейсы API, необходимые в каждом случае.</span><span class="sxs-lookup"><span data-stu-id="da4e1-163">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="da4e1-164">Предположим, имеется библиотека, выполняющая сетевые операции по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="da4e1-164">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="da4e1-165">Для .NET Standard и .NET Framework версии 4.5 или более поздней можно использовать класс `HttpClient` из пространства имен `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-165">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="da4e1-166">Однако в более ранних версиях .NET Framework нет класса `HttpClient`, поэтому вместо него можно использовать класс `WebClient` из пространства имен `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-166">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="da4e1-167">Файл проекта может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="da4e1-167">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard2.0;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="da4e1-168">Вы заметите три основных изменения:</span><span class="sxs-lookup"><span data-stu-id="da4e1-168">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="da4e1-169">Узел `TargetFramework` был заменен на `TargetFrameworks`, внутри которого содержатся три моникера целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="da4e1-169">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="da4e1-170">Добавлен узел `<ItemGroup>` для целевой платформы `net40`, который извлекает одну ссылку на .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-170">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="da4e1-171">Добавлен узел `<ItemGroup>` для целевой платформы `net45`, который извлекает две ссылки на .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da4e1-171">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="da4e1-172">Система сборки распознает следующие символы препроцессора, используемые в директивах `#if`:</span><span class="sxs-lookup"><span data-stu-id="da4e1-172">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="da4e1-173">Ниже приведен пример использования условной компиляции для каждого целевого объекта:</span><span class="sxs-lookup"><span data-stu-id="da4e1-173">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET Framework 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="da4e1-174">При сборке этого проекта с `dotnet build` вы увидите, что в папке `bin/` появились три каталога:</span><span class="sxs-lookup"><span data-stu-id="da4e1-174">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard2.0/
```

<span data-ttu-id="da4e1-175">Каждый из них содержит файлы `.dll` для соответствующего целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="da4e1-175">Each of these contains the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net"></a><span data-ttu-id="da4e1-176">Тестирование библиотек в .NET</span><span class="sxs-lookup"><span data-stu-id="da4e1-176">How to test libraries on .NET</span></span>

<span data-ttu-id="da4e1-177">Необходимо иметь возможность тестирования проектов на различных платформах.</span><span class="sxs-lookup"><span data-stu-id="da4e1-177">It's important to be able to test across platforms.</span></span> <span data-ttu-id="da4e1-178">Вы можете использовать [xUnit](https://xunit.net/) или MSTest без дополнительной настройки.</span><span class="sxs-lookup"><span data-stu-id="da4e1-178">You can use either [xUnit](https://xunit.net/) or MSTest out of the box.</span></span> <span data-ttu-id="da4e1-179">Обе платформы тестирования идеально подходят для модульного тестирования библиотеки в .NET.</span><span class="sxs-lookup"><span data-stu-id="da4e1-179">Both are perfectly suitable for unit testing your library on .NET.</span></span> <span data-ttu-id="da4e1-180">Настройка тестовых проектов для решения зависит от [его структуры](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="da4e1-180">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="da4e1-181">В следующем примере предполагается, что каталог с тестами и каталог с исходным кодом находятся в одном и том же каталоге верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="da4e1-181">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="da4e1-182">В этом примере используются некоторые [команды интерфейса командной строки .NET](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="da4e1-182">This uses some [.NET CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="da4e1-183">Дополнительные сведения см. в разделах [dotnet new](../tools/dotnet-new.md) и [dotnet sln](../tools/dotnet-sln.md).</span><span class="sxs-lookup"><span data-stu-id="da4e1-183">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="da4e1-184">Настройте решение.</span><span class="sxs-lookup"><span data-stu-id="da4e1-184">Set up your solution.</span></span> <span data-ttu-id="da4e1-185">Это можно сделать с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="da4e1-185">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="da4e1-186">Эти команды создадут проекты и объединят их в решение.</span><span class="sxs-lookup"><span data-stu-id="da4e1-186">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="da4e1-187">Ваш каталог для `SolutionWithSrcAndTest` должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="da4e1-187">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="da4e1-188">Перейдите в каталог тестового проекта и добавьте ссылку на `MyProject.Test` из `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-188">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="da4e1-189">Восстановите пакеты и соберите проекты:</span><span class="sxs-lookup"><span data-stu-id="da4e1-189">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

1. <span data-ttu-id="da4e1-190">Убедитесь, что xUnit запущен, выполнив команду `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-190">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="da4e1-191">Если вы решили использовать MSTest, запустите средство запуска консоли MSTest вместо xUnit.</span><span class="sxs-lookup"><span data-stu-id="da4e1-191">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="da4e1-192">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="da4e1-192">And that's it!</span></span> <span data-ttu-id="da4e1-193">Теперь вы можете протестировать библиотеку для всех платформ с помощью средств командной строки.</span><span class="sxs-lookup"><span data-stu-id="da4e1-193">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="da4e1-194">Теперь, когда все настроено, протестировать библиотеку очень легко:</span><span class="sxs-lookup"><span data-stu-id="da4e1-194">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="da4e1-195">Внесите изменения в библиотеку.</span><span class="sxs-lookup"><span data-stu-id="da4e1-195">Make changes to your library.</span></span>
1. <span data-ttu-id="da4e1-196">Выполните тесты в тестовом каталоге из командной строки с помощью команды `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-196">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="da4e1-197">При вызове команды `dotnet test` будет автоматически выполнена повторная сборка кода.</span><span class="sxs-lookup"><span data-stu-id="da4e1-197">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="da4e1-198">Использование нескольких проектов</span><span class="sxs-lookup"><span data-stu-id="da4e1-198">How to use multiple projects</span></span>

<span data-ttu-id="da4e1-199">В случае с более крупными библиотеками, как правило, требуется реализовывать функциональность в разных проектах.</span><span class="sxs-lookup"><span data-stu-id="da4e1-199">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="da4e1-200">Представим, что необходимо создать библиотеку, которую можно использовать в идиоматичном коде на языках C# и F#.</span><span class="sxs-lookup"><span data-stu-id="da4e1-200">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="da4e1-201">Это означает, что библиотека будет использоваться способами, естественными для языков C# и F#.</span><span class="sxs-lookup"><span data-stu-id="da4e1-201">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="da4e1-202">Например, в C# можно использовать библиотеку следующим образом:</span><span class="sxs-lookup"><span data-stu-id="da4e1-202">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="da4e1-203">В F# это может выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="da4e1-203">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="da4e1-204">Подобные сценарии использования предполагают, что интерфейсы API, к которым осуществляется доступ, должны иметь разную структуру для C# и F#.</span><span class="sxs-lookup"><span data-stu-id="da4e1-204">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="da4e1-205">Стандартным подходом к решению этой задачи является факторинг всей логики библиотеки в базовом проекте и определение в проектах C# и F# уровней API, которые вызывают этот базовый проект.</span><span class="sxs-lookup"><span data-stu-id="da4e1-205">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="da4e1-206">Далее в этом разделе будут использоваться следующие имена:</span><span class="sxs-lookup"><span data-stu-id="da4e1-206">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="da4e1-207">**AwesomeLibrary.Core** — базовый проект, содержащий всю логику библиотеки;</span><span class="sxs-lookup"><span data-stu-id="da4e1-207">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="da4e1-208">**AwesomeLibrary.CSharp** — проект с открытыми интерфейсами API, предназначенными для использования в коде на языке C#</span><span class="sxs-lookup"><span data-stu-id="da4e1-208">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="da4e1-209">**AwesomeLibrary.FSharp** — проект с открытыми интерфейсами API, предназначенными для использования в коде на языке F#</span><span class="sxs-lookup"><span data-stu-id="da4e1-209">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="da4e1-210">Чтобы получить ту же структуру каталогов, что и в этом руководстве, выполните следующие команды в окне терминала:</span><span class="sxs-lookup"><span data-stu-id="da4e1-210">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="da4e1-211">Эти команды добавят три указанные выше проекта и файл решения, который их связывает.</span><span class="sxs-lookup"><span data-stu-id="da4e1-211">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="da4e1-212">Создание файла решения и связывание проектов позволит создавать и восстанавливать проекты из верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="da4e1-212">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="da4e1-213">Ссылки проектов на проекты</span><span class="sxs-lookup"><span data-stu-id="da4e1-213">Project-to-project referencing</span></span>

<span data-ttu-id="da4e1-214">Ссылку на проект лучше всего добавить с помощью интерфейса командной строки .NET.</span><span class="sxs-lookup"><span data-stu-id="da4e1-214">The best way to reference a project is to use the .NET CLI to add a project reference.</span></span> <span data-ttu-id="da4e1-215">Из каталогов проекта **AwesomeLibrary.CSharp** и **AwesomeLibrary.FSharp** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="da4e1-215">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="da4e1-216">Теперь файлы **AwesomeLibrary.CSharp** и **AwesomeLibrary.FSharp** будут ссылаться на **AwesomeLibrary.Core** в качестве целевого объекта `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="da4e1-216">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="da4e1-217">Чтобы это проверить, просмотрите файлы проектов, и вы увидите в них следующий код:</span><span class="sxs-lookup"><span data-stu-id="da4e1-217">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="da4e1-218">Если вы не хотите использовать интерфейс командной строки .NET, можете добавить этот код в каждый файл проекта вручную.</span><span class="sxs-lookup"><span data-stu-id="da4e1-218">You can add this section to each project file manually if you prefer not to use the .NET CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="da4e1-219">Структурирование решения</span><span class="sxs-lookup"><span data-stu-id="da4e1-219">Structuring a solution</span></span>

<span data-ttu-id="da4e1-220">Еще один важный аспект решений с несколькими проектами — правильное формирование общей структуры.</span><span class="sxs-lookup"><span data-stu-id="da4e1-220">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="da4e1-221">Код можно упорядочить так, как вам удобно. Если каждый проект связан с файлом решения с помощью `dotnet sln add`, вы сможете запускать команды `dotnet restore` и `dotnet build` на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="da4e1-221">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
