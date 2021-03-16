---
title: 'NETSDK1045: текущий пакет SDK для .NET не поддерживает в качестве целевого объекта "более новую версию".'
description: Сведения об ошибке NETSDK1045 в пакете SDK для .NET, которая возникает, когда средствам сборки не удается найти запрашиваемую версию пакета SDK для .NET.
ms.topic: error-reference
ms.date: 02/12/2021
f1_keywords:
- NETSDK1045
ms.openlocfilehash: 7f21270fdc7c2db862a49302a302bf8121fc86a5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104106"
---
# <a name="netsdk1045-the-current-net-sdk-does-not-support-newer-version-as-a-target"></a><span data-ttu-id="96e5d-103">NETSDK1045: текущий пакет SDK для .NET не поддерживает в качестве целевого объекта "более новую версию".</span><span class="sxs-lookup"><span data-stu-id="96e5d-103">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span>

<span data-ttu-id="96e5d-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="96e5d-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="96e5d-105">Эта ошибка возникает, когда средствам сборки не удается найти пакет SDK для .NET, необходимый для построения проекта.</span><span class="sxs-lookup"><span data-stu-id="96e5d-105">This error occurs when the build tools can't find the version of the .NET SDK that's needed to build a project.</span></span> <span data-ttu-id="96e5d-106">Обычно это происходит из-за проблем с установкой или настройкой пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96e5d-106">This is typically due to a .NET Core SDK installation or configuration issue.</span></span> <span data-ttu-id="96e5d-107">Полный текст сообщения об ошибке подобен приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="96e5d-107">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="96e5d-108">NETSDK1045: текущий пакет SDK для .NET не поддерживает в качестве целевого объекта "более новую версию".</span><span class="sxs-lookup"><span data-stu-id="96e5d-108">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span> <span data-ttu-id="96e5d-109">Либо выполните нацеливание на "более старую версию" или более раннюю версию, либо используйте пакет SDK для .NET, поддерживающий "более новую версию".</span><span class="sxs-lookup"><span data-stu-id="96e5d-109">Either target 'older version' or lower, or use a .NET SDK version that supports 'newer version'.</span></span>

<span data-ttu-id="96e5d-110">В следующих разделах описаны некоторые из возможных причин этой ошибки.</span><span class="sxs-lookup"><span data-stu-id="96e5d-110">The following sections describe some of the possible reasons for this error.</span></span> <span data-ttu-id="96e5d-111">Проверьте каждую из них и посмотрите, какие из них применимы.</span><span class="sxs-lookup"><span data-stu-id="96e5d-111">Check each one and see which one applies to you.</span></span> <span data-ttu-id="96e5d-112">Помните, что при внесении изменений в среду или файлы конфигурации может потребоваться перезапустить окна командной строки, перезапустить Visual Studio или перезагрузить компьютер, чтобы изменения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="96e5d-112">Keep in mind that when making changes to the environment or the configuration files, you might have to restart command windows, restart Visual Studio, or reboot your machine, for your changes to take effect.</span></span>

## <a name="net-sdk-version"></a><span data-ttu-id="96e5d-113">Версия пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="96e5d-113">.NET SDK version</span></span>

<span data-ttu-id="96e5d-114">Откройте файл проекта (CSPROJ, VBPROJ или FSPROJ) и проверьте целевую платформу.</span><span class="sxs-lookup"><span data-stu-id="96e5d-114">Open the project file (.csproj, .vbproj, or .fsproj) and check the target framework.</span></span> <span data-ttu-id="96e5d-115">Это версия платформы, которую приложение пытается использовать.</span><span class="sxs-lookup"><span data-stu-id="96e5d-115">This is the version of the framework that your app is trying to use.</span></span>

```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

<span data-ttu-id="96e5d-116">Убедитесь, что на компьютере установлена указанная версия .NET.</span><span class="sxs-lookup"><span data-stu-id="96e5d-116">Make sure that the version of .NET listed is installed on the machine.</span></span> <span data-ttu-id="96e5d-117">Список установленных версий можно отобразить с помощью следующей команды (откройте окно командной строки разработчика и выполните следующую команду):</span><span class="sxs-lookup"><span data-stu-id="96e5d-117">You can list the installed versions by using the following command (open a Developer Command Prompt and run this command):</span></span>

```dotnetcli
dotnet --list-sdks
```

### <a name="x86-or-x64-architecture"></a><span data-ttu-id="96e5d-118">Архитектура x86 или x64</span><span class="sxs-lookup"><span data-stu-id="96e5d-118">x86 or x64 architecture</span></span>

<span data-ttu-id="96e5d-119">Каждая версия пакета SDK для .NET доступна как для архитектуры x86, так и для архитектуры x64.</span><span class="sxs-lookup"><span data-stu-id="96e5d-119">Each version of the .NET SDK is available in both x86 and x64 architecture.</span></span> <span data-ttu-id="96e5d-120">Возможно, проект пытается найти пакет SDK для .NET для неправильной архитектуры, либо пакет SDK для .NET для требуемой архитектуры, возможно, не установлен.</span><span class="sxs-lookup"><span data-stu-id="96e5d-120">The project might be trying to find the .NET SDK for the wrong architecture, or the .NET SDK for the architecture your project needs might not be installed.</span></span> <span data-ttu-id="96e5d-121">Проверьте папки установки требуемой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="96e5d-121">Check the installation folders for the architecture you need.</span></span> <span data-ttu-id="96e5d-122">Например, в Windows версия пакета SDK для .NET для архитектуры x86 устанавливается в папку *C:\Program Files (x86)\dotnet*, а для архитектуры x64 — в папку *C:\Program Files\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="96e5d-122">For example, on Windows, the x86 version of the .NET SDK is installed in *C:\Program Files (x86)\dotnet* and the x64 version is installed in *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="96e5d-123">Ознакомьтесь с разделом [Проверка того, установлена ли платформа .NET](../../install/how-to-detect-installed-versions.md) и выберите свою операционную систему, чтобы узнать, как определить, какие компоненты установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="96e5d-123">See [How to check that .NET is already installed](../../install/how-to-detect-installed-versions.md) and choose your operating system to find out how to detect what's installed on your machine.</span></span>

<span data-ttu-id="96e5d-124">Если нужная версия не установлена, найдите нужный вариант на странице [загрузки .NET](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="96e5d-124">If the version you need isn't installed, find the one you need at the [.NET Downloads](https://dotnet.microsoft.com/download/dotnet) page.</span></span>

## <a name="preview-not-enabled"></a><span data-ttu-id="96e5d-125">Не включена предварительная версия</span><span class="sxs-lookup"><span data-stu-id="96e5d-125">Preview not enabled</span></span>

<span data-ttu-id="96e5d-126">Если у вас установлена предварительная версия требуемой версии пакета SDK для .NET, необходимо также задать параметр включения предварительных версий в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96e5d-126">If you have a preview installed of the requested .NET SDK version, you also need to set the option to enable previews in Visual Studio.</span></span> <span data-ttu-id="96e5d-127">Выберите **Сервис** > **Параметры** > **Среда** > **Функции предварительной версии** и убедитесь, что установлен флажок **Использовать предварительные версии пакетов SDK для .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="96e5d-127">Go to **Tools** > **Options** > **Environment** > **Preview Features**, and make sure that **Use previews of the .NET Core SDK** is checked.</span></span>

## <a name="visual-studio-version"></a><span data-ttu-id="96e5d-128">Версия Visual Studio</span><span class="sxs-lookup"><span data-stu-id="96e5d-128">Visual Studio version</span></span>

<span data-ttu-id="96e5d-129">Например, для .NET Core 3.0 и более поздних версий требуется Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="96e5d-129">For example, .NET Core 3.0 and later require Visual Studio 2019.</span></span> <span data-ttu-id="96e5d-130">Выполните обновление до [Visual Studio 2019 версии 16.3](https://visualstudio.microsoft.com/downloads) или более поздней для сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="96e5d-130">Upgrade to [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads) or later to build your project.</span></span>

## <a name="path-environment-variable"></a><span data-ttu-id="96e5d-131">Переменная среды PATH</span><span class="sxs-lookup"><span data-stu-id="96e5d-131">PATH environment variable</span></span>

<span data-ttu-id="96e5d-132">Средства сборки используют переменную среды PATH для поиска правильной версии средств сборки .NET.</span><span class="sxs-lookup"><span data-stu-id="96e5d-132">The build tools use the PATH environment variable to find the right version of the .NET build tools.</span></span> <span data-ttu-id="96e5d-133">Если переменная среды PATH содержит прямые пути к старым средствам сборки, может появиться это сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="96e5d-133">If the PATH environment variable contains direct paths to older build tools, this error message could appear.</span></span> <span data-ttu-id="96e5d-134">Убедитесь, что единственный путь к средствам .NET в переменной среды PATH относится к папке верхнего уровня *dotnet*, например *C:\Program Files\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="96e5d-134">Make sure the only path to the .NET tools in the PATH environment variable is to the top-level *dotnet* folder, for example, *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="96e5d-135">Примером неверной переменной PATH будет нечто вроде *C:\Program Files\dotnet\2.1.0\sdks*.</span><span class="sxs-lookup"><span data-stu-id="96e5d-135">An example of an incorrect PATH would be something like *C:\Program Files\dotnet\2.1.0\sdks*.</span></span>

## <a name="msbuildsdkpath-environment-variable"></a><span data-ttu-id="96e5d-136">Переменная среды MSBuildSDKPath</span><span class="sxs-lookup"><span data-stu-id="96e5d-136">MSBuildSDKPath environment variable</span></span>

<span data-ttu-id="96e5d-137">Проверьте переменную среды MSBuildSDKPath.</span><span class="sxs-lookup"><span data-stu-id="96e5d-137">Check the MSBuildSDKPath environment variable.</span></span> <span data-ttu-id="96e5d-138">Эта необязательная переменная среды распознается MSBuild, и если она задана, она переопределяет значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="96e5d-138">This optional environment variable is recognized by MSBuild and if set, overrides the default value.</span></span> <span data-ttu-id="96e5d-139">Может быть задана определенная более ранняя версия пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="96e5d-139">It might be set to a specific older version of the .NET SDK.</span></span> <span data-ttu-id="96e5d-140">Если это так, попробуйте удалить ее и перестроить проект.</span><span class="sxs-lookup"><span data-stu-id="96e5d-140">If it's set, try deleting it and rebuilding your project.</span></span>

## <a name="globaljson-file"></a><span data-ttu-id="96e5d-141">Файл global.json</span><span class="sxs-lookup"><span data-stu-id="96e5d-141">global.json file</span></span>

<span data-ttu-id="96e5d-142">Проверьте файл *global.json* в корневой папке проекта и всю цепочку каталогов до корня тома, поскольку он может находиться в любом месте в структуре папок.</span><span class="sxs-lookup"><span data-stu-id="96e5d-142">Check for a *global.json* file in the root folder in your project and up the directory chain to the root of the volume, since it can be anywhere in the folder structure.</span></span> <span data-ttu-id="96e5d-143">Если он содержит версию пакета SDK, удалите узел `sdk` и все его дочерние элементы или обновите его до нужной более новой версии .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96e5d-143">If it contains an SDK version, delete the `sdk` node and all its children, or update it to the desired newer .NET Core version.</span></span>

```json
{
  "sdk": {
    "version": "2.1.0"
  }
}
```

<span data-ttu-id="96e5d-144">Файл *global.json* не требуется, поэтому, если он не содержит ничего, кроме узла `sdk`, можно удалить весь файл.</span><span class="sxs-lookup"><span data-stu-id="96e5d-144">The *global.json* file is not required, so if it doesn't contain anything other than the `sdk` node, you can delete the whole file.</span></span>

## <a name="directorybuildprops-file"></a><span data-ttu-id="96e5d-145">Файл Directory.build.props</span><span class="sxs-lookup"><span data-stu-id="96e5d-145">Directory.build.props file</span></span>

<span data-ttu-id="96e5d-146">Файл *Directory.build.props* является необязательным файлом MSBuild, который может задавать глобальные свойства.</span><span class="sxs-lookup"><span data-stu-id="96e5d-146">The *Directory.build.props* file is an optional MSBuild file that can set global properties.</span></span> <span data-ttu-id="96e5d-147">Проверьте наличие этих файлов в папке решения и всю цепочку каталогов до корня тома, поскольку они могут находиться в любом месте в структуре папок.</span><span class="sxs-lookup"><span data-stu-id="96e5d-147">Check for these files in the solution folder and up the directory chain to the root of the volume, since they can be anywhere in the folder structure.</span></span> <span data-ttu-id="96e5d-148">Найдите элементы `TargetFramework` или параметры `MSBuildSDKPath`, которые могут переопределить нужные параметры.</span><span class="sxs-lookup"><span data-stu-id="96e5d-148">Look for `TargetFramework` elements, or settings of `MSBuildSDKPath` that could override your desired settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="96e5d-149">См. также</span><span class="sxs-lookup"><span data-stu-id="96e5d-149">See also</span></span>

- [<span data-ttu-id="96e5d-150">Текущий пакет SDK для .NET не поддерживает .NET Core 3.0 в качестве целевого объекта — исправление</span><span class="sxs-lookup"><span data-stu-id="96e5d-150">The Current .NET SDK does not support targeting .NET Core 3.0 – Fix</span></span>](https://www.ryadel.com/current-net-sdk-not-support-net-core-3-0-fix/)
