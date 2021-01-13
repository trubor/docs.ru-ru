---
title: Приложение с одним файлом
description: Узнайте, что такое приложение с одним файлом и зачем нужно использовать эту модель развертывания приложения.
author: lakshanf
ms.author: lakshanf
ms.date: 12/17/2020
ms.openlocfilehash: e2d2c9ed4c28d11a77e4f840602982a36cf1c80c
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678151"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="8fcbf-103">Развертывание и выполнение в виде отдельного файла</span><span class="sxs-lookup"><span data-stu-id="8fcbf-103">Single file deployment and executable</span></span>

<span data-ttu-id="8fcbf-104">Объединение всех зависящих от приложения файлов в один двоичный файл предоставляет разработчику приложения привлекательный вариант развертывания и распространения приложения в виде одного файла.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="8fcbf-105">Эта модель развертывания была доступна с момента выпуска .NET Core 3.0 и улучшена в .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="8fcbf-106">Ранее в .NET Core 3.0, когда пользователь запускал приложение с одним файлом, узел .NET Core перед запуском приложения сначала извлекал все файлы во временный каталог.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="8fcbf-107">В .NET 5.0 этот подход был улучшен, позволяя запускать код напрямую без необходимости извлекать файлы из приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="8fcbf-108">Развертывание в одном файле доступно как для [зависимой от платформы модели развертывания](index.md#publish-framework-dependent), так и для [автономных приложений](index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="8fcbf-109">Размер одного файла для автономного приложения будет большим, так как он будет включать в себя среду выполнения и библиотеки платформы.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="8fcbf-110">Вариант развертывания в виде одного файла можно сочетать с параметрами публикации [ReadyToRun](ready-to-run.md) и [Обрезка (экспериментальная функция в .NET 5.0)](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-110">The single file deployment option can be combined with [ReadyToRun](ready-to-run.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="8fcbf-111">Несовместимость API</span><span class="sxs-lookup"><span data-stu-id="8fcbf-111">API incompatibility</span></span>

<span data-ttu-id="8fcbf-112">Некоторые API несовместимы с моделью развертывания с одним файлом. Поэтому, возможно, потребуется изменить приложения, если они используют такие API.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="8fcbf-113">Если вы работаете со сторонними платформами или пакетами, возможно, они также используют один из таких API и требуют изменения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="8fcbf-114">Распространенная причина многих проблем — это зависимость от путей к файлам или библиотекам DLL, поставляемых с приложением.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="8fcbf-115">В таблице ниже приведены соответствующие сведения об API библиотеки среды выполнения для использования с одним файлом.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="8fcbf-116">API</span><span class="sxs-lookup"><span data-stu-id="8fcbf-116">API</span></span>                            | <span data-ttu-id="8fcbf-117">Примечание</span><span class="sxs-lookup"><span data-stu-id="8fcbf-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="8fcbf-118">Возвращает пустую строку.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="8fcbf-119">Возвращает строку со значением `<Unknown>` или вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="8fcbf-120">Возвращает строку со значением `<Unknown>`.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="8fcbf-121">Выдает исключение <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="8fcbf-122">Выдает исключение <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="8fcbf-123">Выдает исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="8fcbf-124">Выдает исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="8fcbf-125">Возвращает `null`.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="8fcbf-126">Возвращает `null`.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="8fcbf-127">Вот некоторые рекомендации по исправлению для распространенных сценариев:</span><span class="sxs-lookup"><span data-stu-id="8fcbf-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="8fcbf-128">Чтобы получить доступ к файлам, расположенным рядом с исполняемым файлом, используйте <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="8fcbf-129">Чтобы найти имя исполняемого файла, используйте первый элемент метода <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="8fcbf-130">Чтобы не допустить доставку свободных файлов в целом, используйте [внедренные ресурсы](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="attaching-a-debugger"></a><span data-ttu-id="8fcbf-131">Подключение отладчика</span><span class="sxs-lookup"><span data-stu-id="8fcbf-131">Attaching a debugger</span></span>

<span data-ttu-id="8fcbf-132">В Linux [SOS с LLDB](../diagnostics/dotnet-sos.md) — это единственный отладчик, который может подключаться к автономным процессам с одним файлом или выполнять отладку аварийных дампов.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-132">On Linux, the only debugger which can attach to self-contained single-file processes or debug crash dumps is [SOS with LLDB](../diagnostics/dotnet-sos.md).</span></span>

<span data-ttu-id="8fcbf-133">В Windows и Mac для отладки аварийных дампов можно использовать Visual Studio и VS Code.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-133">On Windows and Mac, Visual Studio and VS Code can be used to debug crash dumps.</span></span> <span data-ttu-id="8fcbf-134">Для подключения к исполняемому файлу выполняемого автономного приложения с одним файлом требуется дополнительный файл: _mscordbi.{dll,so}_ .</span><span class="sxs-lookup"><span data-stu-id="8fcbf-134">Attaching to a running self-contained single-file executable requires an extra file: _mscordbi.{dll,so}_.</span></span>

<span data-ttu-id="8fcbf-135">При отсутствии этого файла Visual Studio может выдать сообщение об ошибке, информирующее о том, что не удается присоединиться к процессу,</span><span class="sxs-lookup"><span data-stu-id="8fcbf-135">Without this file Visual Studio may produce the error "Unable to attach to the process.</span></span> <span data-ttu-id="8fcbf-136">так как установлен компонент отладки.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-136">A debug component is not installed."</span></span> <span data-ttu-id="8fcbf-137">VS Code выдать сообщение об ошибке, информирующее о том, что не удается присоединиться к процессу из-за неизвестной ошибки 0x80131c3c.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-137">and VS Code may produce the error "Failed to attach to process: Unknown Error: 0x80131c3c."</span></span>

<span data-ttu-id="8fcbf-138">Чтобы устранить эти ошибки, нужно скопировать _mscordbi_ и вставить рядом с исполняемым файлом.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-138">To fix these errors, _mscordbi_ needs to be copied next to the executable.</span></span> <span data-ttu-id="8fcbf-139">По умолчанию файл _mscordbi_ обработан с помощью `publish` в подкаталоге с идентификатором среды выполнения приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-139">_mscordbi_ is `publish`ed by default in the subdirectory with the application's runtime ID.</span></span> <span data-ttu-id="8fcbf-140">Например, если бы нужно было опубликовать исполняемый файл автономного приложения с одним файлом, используя CLI `dotnet` для Windows и параметры `-r win-x64`, файл следовало бы поместить в папку _bin/Debug/net5.0/win-x64/publish_.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-140">So, for example, if one were to publish a self-contained single-file executable using the `dotnet` CLI for Windows using the parameters `-r win-x64`, the executable would be placed in _bin/Debug/net5.0/win-x64/publish_.</span></span> <span data-ttu-id="8fcbf-141">Копия _mscordbi.dll_ будет находиться в папке _bin/debug/NET 5.0/Win-x64_.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-141">A copy of _mscordbi.dll_ would be present in _bin/Debug/net5.0/win-x64_.</span></span>

## <a name="other-considerations"></a><span data-ttu-id="8fcbf-142">Другие замечания</span><span class="sxs-lookup"><span data-stu-id="8fcbf-142">Other considerations</span></span>

<span data-ttu-id="8fcbf-143">По умолчанию один файл не включает собственные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-143">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="8fcbf-144">В Linux предварительно связывается среда выполнения с пакетом, а в каталоге, в котором размещается приложение с одним файлом, развертываются только собственные библиотеки приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-144">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="8fcbf-145">В Windows предварительно связывается только код размещения, а в каталоге, в котором размещается приложение с одним файлом, развертываются как библиотеки среды выполнения, так и собственные библиотеки приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-145">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="8fcbf-146">Это позволяет обеспечить эффективную отладку, для которой требуется, чтобы собственные файлы были исключены из одного файла.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-146">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="8fcbf-147">Можно задать флаг `IncludeNativeLibrariesForSelfExtract`, чтобы включить собственные библиотеки в один пакет, но эти файлы будут извлечены во временный каталог на клиентском компьютере при запуске приложения с одним файлом.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-147">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="8fcbf-148">Все связанные PDB-файлы будут храниться рядом с приложением с одним файлом, и они не будут упакованы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-148">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="8fcbf-149">Если нужно включить PDB-файлы в сборку для компилируемых проектов, задайте для `DebugType` значение `embedded`, как описано [ниже](#include-pdb-files-inside-the-bundle).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-149">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="8fcbf-150">Управляемые компоненты C++ не подходят для развертывания с одним файлом. Поэтому рекомендуется писать приложения на C# или другом неуправляемом языке на базе C++, если требуется совместимость с развертыванием в одном файле.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-150">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="8fcbf-151">Исключить файлы из внедрения</span><span class="sxs-lookup"><span data-stu-id="8fcbf-151">Exclude files from being embedded</span></span>

<span data-ttu-id="8fcbf-152">Некоторые файлы можно явно исключить из внедрения в один файл, установив следующие метаданные.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-152">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="8fcbf-153">Например, чтобы поместить некоторые файлы в каталог публикации, но не объединять их в один файл, укажите следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-153">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="8fcbf-154">Добавление PDB-файлов в пакет</span><span class="sxs-lookup"><span data-stu-id="8fcbf-154">Include PDB files inside the bundle</span></span>

<span data-ttu-id="8fcbf-155">PDB-файл для сборки можно внедрить в саму сборку (`.dll`), используя параметр, приведенный ниже.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-155">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="8fcbf-156">Так как символы являются частью сборки, они также будут частью приложения с одним файлом:</span><span class="sxs-lookup"><span data-stu-id="8fcbf-156">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="8fcbf-157">Например, добавьте следующее свойство в файл проекта сборки, чтобы внедрить PDB-файл в эту сборку:</span><span class="sxs-lookup"><span data-stu-id="8fcbf-157">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---sample-project-file"></a><span data-ttu-id="8fcbf-158">Публикация приложения с одним файлом — пример файла проекта</span><span class="sxs-lookup"><span data-stu-id="8fcbf-158">Publish a single file app - sample project file</span></span>

<span data-ttu-id="8fcbf-159">Ниже приведен пример файла проекта, в котором задана публикация одного файла:</span><span class="sxs-lookup"><span data-stu-id="8fcbf-159">Here's a sample project file that specifies single-file publishing:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="8fcbf-160">Эти свойства имеют следующие функции:</span><span class="sxs-lookup"><span data-stu-id="8fcbf-160">These properties have the following functions:</span></span>

* <span data-ttu-id="8fcbf-161">`PublishSingleFile` — включение однофайловой публикации.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-161">`PublishSingleFile` - Enables single-file publishing.</span></span>
* <span data-ttu-id="8fcbf-162">`SelfContained` — определение того, будет ли приложение автономным или зависимым от платформы.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-162">`SelfContained` - Determines whether the app will be self-contained or framework-dependent.</span></span>
* <span data-ttu-id="8fcbf-163">`RuntimeIdentifier` — указание [типа операционной системы и ЦП](../rid-catalog.md), для которых предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-163">`RuntimeIdentifier` - Specifies the [OS and CPU type](../rid-catalog.md) you are targeting.</span></span>
* <span data-ttu-id="8fcbf-164">`PublishTrimmed` — разрешение использования [усечения сборки](trim-self-contained.md), которое поддерживается только для автономных приложений.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-164">`PublishTrimmed` - Enables use of [assembly trimming](trim-self-contained.md), which is only supported for self-contained apps.</span></span>
* <span data-ttu-id="8fcbf-165">`PublishReadyToRun` — включение [компиляции AOT](ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-165">`PublishReadyToRun` - Enables [ahead-of-time (AOT) compilation](ready-to-run.md).</span></span>

<span data-ttu-id="8fcbf-166">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="8fcbf-166">**Notes:**</span></span>

* <span data-ttu-id="8fcbf-167">Приложения создаются для определенной ОС и архитектуры.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-167">Apps are OS and architecture-specific.</span></span> <span data-ttu-id="8fcbf-168">Необходимо опубликовать приложение для каждой конфигурации, например Linux x64, Linux ARM64, Windows x64 и т. д.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-168">You need to publish for each configuration, such as Linux x64, Linux ARM64, Windows x64, and so forth.</span></span>
* <span data-ttu-id="8fcbf-169">Файлы конфигурации, такие как *\*.runtimeconfig.json*, включаются в один файл.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-169">Configuration files, such as *\*.runtimeconfig.json*, are included in the single file.</span></span> <span data-ttu-id="8fcbf-170">Если требуется дополнительный файл конфигурации, его можно поместить вместе с одним файлом приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-170">If an additional configuration file is needed, you can place it beside the single file.</span></span>

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="8fcbf-171">Публикация приложения с одним файлом с помощью CLI</span><span class="sxs-lookup"><span data-stu-id="8fcbf-171">Publish a single file app - CLI</span></span>

<span data-ttu-id="8fcbf-172">Опубликуйте приложение с одним файлом с помощью команды [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-172">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="8fcbf-173">При публикации приложения задайте следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-173">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="8fcbf-174">Опубликовать для конкретной среды выполнения: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="8fcbf-174">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="8fcbf-175">Опубликовать в виде одного файла: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="8fcbf-175">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="8fcbf-176">В следующем примере приложение для Windows публикуется как автономное приложение с одним файлом.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-176">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="8fcbf-177">В следующем примере приложение для Linux публикуется как зависимое от платформы приложение с одним файлом.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-177">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="8fcbf-178">Дополнительные сведения см. в статье [Публикация приложений .NET Core с помощью .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-178">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="8fcbf-179">Публикация приложения с одним файлом с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fcbf-179">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="8fcbf-180">Visual Studio создает многократно используемые профили публикации, которые управляют процессом публикации приложения.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-180">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="8fcbf-181">В **обозревателе решений** щелкните правой кнопкой мыши проект, который нужно опубликовать.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-181">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="8fcbf-182">Нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-182">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Обозреватель решений с контекстным меню, где выделен пункт Опубликовать":::

    <span data-ttu-id="8fcbf-184">Если у вас еще нет профиля публикации, следуйте инструкциям по его созданию и выберите **Папка** в качестве типа целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-184">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="8fcbf-185">Нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-185">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Профиль публикации Visual Studio с кнопкой Изменить":::

01. <span data-ttu-id="8fcbf-187">В диалоговом окне **Параметры профиля** задайте следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-187">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="8fcbf-188">Параметру **Режим развертывания** задайте значение **Автономное**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-188">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="8fcbf-189">В качестве значения параметра **Целевая среда выполнения** укажите платформу, на которую будет выполнена публикация.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-189">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="8fcbf-190">Выберите **Создать отдельный файл**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-190">Select **Produce single file**.</span></span>

    <span data-ttu-id="8fcbf-191">Нажмите кнопку **Сохранить**, чтобы сохранить параметры и вернуться в диалоговое окно **Публикация**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-191">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Диалоговое окно параметров профиля с выделенными параметрами для режима развертывания, целевой среды выполнения и создания отдельного файла":::

01. <span data-ttu-id="8fcbf-193">Чтобы опубликовать приложение с одним файлом, нажмите кнопку **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-193">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="8fcbf-194">Дополнительные сведения см. в статье [Публикация приложений .NET Core с помощью Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-194">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="8fcbf-195">Публикация приложения с одним файлом с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="8fcbf-195">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="8fcbf-196">В Visual Studio для Mac отсутствует возможность публикации приложения в виде одного файла.</span><span class="sxs-lookup"><span data-stu-id="8fcbf-196">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="8fcbf-197">Вам потребуется опубликовать приложение вручную, выполнив инструкции из раздела [Публикация приложения с одним файлом с помощью CLI](#publish-a-single-file-app---cli).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-197">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="8fcbf-198">Дополнительные сведения см. в статье [Публикация приложений .NET Core с помощью .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-198">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fcbf-199">См. также</span><span class="sxs-lookup"><span data-stu-id="8fcbf-199">See also</span></span>

- <span data-ttu-id="8fcbf-200">[Развертывание приложений .NET Core](index.md)</span><span class="sxs-lookup"><span data-stu-id="8fcbf-200">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="8fcbf-201">[Публикация приложений .NET Core с помощью .NET Core CLI](deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="8fcbf-201">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="8fcbf-202">[Публикация приложений .NET Core с помощью Visual Studio](deploy-with-vs.md)</span><span class="sxs-lookup"><span data-stu-id="8fcbf-202">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="8fcbf-203">[Команда `dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="8fcbf-203">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
