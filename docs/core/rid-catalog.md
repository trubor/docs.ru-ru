---
title: Каталог идентификаторов сред выполнения (RID) .NET
description: Сведения об идентификаторах сред выполнения и их использовании в .NET.
ms.date: 01/28/2021
ms.openlocfilehash: 15a2be8d3c2a903011e298d99c838baef731b9c2
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875100"
---
# <a name="net-rid-catalog"></a><span data-ttu-id="a5fa6-103">Каталог идентификаторов сред выполнения в .NET</span><span class="sxs-lookup"><span data-stu-id="a5fa6-103">.NET RID Catalog</span></span>

<span data-ttu-id="a5fa6-104">RID — это сокращение от *Runtime IDentifier* (идентификатор среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-104">RID is short for *Runtime Identifier*.</span></span> <span data-ttu-id="a5fa6-105">Идентификаторы RID служат для идентификации целевых платформ, на которых выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="a5fa6-106">Они используются пакетами .NET для представления ресурсов, специфичных для платформы, в пакетах NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="a5fa6-107">Некоторые примеры идентификаторов RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` или `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="a5fa6-108">Для пакетов с собственными зависимостями они указывают, на каких платформах можно восстановить пакет.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="a5fa6-109">Один идентификатор RID можно задать в элементе `<RuntimeIdentifier>` вашего файла проекта.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="a5fa6-110">Несколько идентификаторов RID можно определить в виде списка, разделенного точкой с запятой, в элементе `<RuntimeIdentifiers>` файла проекта.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="a5fa6-111">Они также используются с помощью параметра `--runtime` со следующими [командами интерфейса командной строки .NET](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="a5fa6-111">They're also used via the `--runtime` option with the following [.NET CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="a5fa6-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a5fa6-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="a5fa6-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a5fa6-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="a5fa6-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a5fa6-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="a5fa6-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a5fa6-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="a5fa6-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a5fa6-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="a5fa6-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a5fa6-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="a5fa6-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a5fa6-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="a5fa6-119">Идентификаторы RID, представляющие отдельные операционные системы, обычно имеют следующий формат: `[os].[version]-[architecture]-[additional qualifiers]`, где:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="a5fa6-120">`[os]` — это моникер платформы или операционной системы.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="a5fa6-121">Например, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="a5fa6-122">`[version]` — это версия операционной системы в виде номера, разделенного точкой (`.`).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="a5fa6-123">Например, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="a5fa6-124">Это **не должен быть** коммерческий номер версии, так как такой номер часто представляет отдельные версии операционной системы с различными контактными зонами API.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="a5fa6-125">`[architecture]` — это архитектура процессора.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="a5fa6-126">Например, `x86`, `x64`, `arm` или `arm64`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="a5fa6-127">`[additional qualifiers]` дополнительно дифференцируют разные платформы.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="a5fa6-128">Например, `aot`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="a5fa6-129">Схема RID</span><span class="sxs-lookup"><span data-stu-id="a5fa6-129">RID graph</span></span>

<span data-ttu-id="a5fa6-130">Схема RID или резервная схема среды выполнения — это список идентификаторов RID, которые совместимы друг с другом.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="a5fa6-131">Идентификаторы RID определены в пакете [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="a5fa6-132">Список поддерживаемых идентификаторов RID и схема RID содержатся в файле [*runtime.json*](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json), который находится в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file, which is located in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="a5fa6-133">В этом файле можно увидеть, что все идентификаторы RID, кроме основного, содержат оператор `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="a5fa6-134">Эти операторы указывают совместимые RID.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="a5fa6-135">Когда NuGet восстанавливает пакеты, он пытается найти точное совпадение для указанной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="a5fa6-136">Если его не удается найти, NuGet проходит схему до тех пор, пока не найдет ближайшую совместимую систему в соответствии со схемой RID.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="a5fa6-137">Ниже приведена запись для идентификатора RID `osx.10.12-x64`:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="a5fa6-138">Приведенный выше идентификатор RID указывает, что `osx.10.12-x64` импортирует `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="a5fa6-139">Таким образом, когда NuGet восстанавливает пакеты, он пытается найти в пакете точное совпадение для `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="a5fa6-140">Например, если NuGet не удается найти определенную среду выполнения, он может восстановить пакеты, которые определяют среды выполнения `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="a5fa6-141">В следующем примере показана немного большая схема RID, которая также указана в файле *runtime.json*:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="a5fa6-142">Все идентификаторы RID в конечном итоге сопоставляются с корневым идентификатором RID `any`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="a5fa6-143">При работе с идентификаторами RID следует учитывать некоторые моменты:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="a5fa6-144">Не пытайтесь анализировать идентификаторы RID для получения частей компонента.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-144">Don't try to parse RIDs to retrieve component parts.</span></span>
- <span data-ttu-id="a5fa6-145">Не следует создавать идентификаторы RID программным способом.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="a5fa6-146">Используйте только те идентификаторы RID, которые уже определены для платформы.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="a5fa6-147">Идентификаторы RID должны указываться точно. Предположения недопустимы.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="a5fa6-148">Использование идентификаторов RID</span><span class="sxs-lookup"><span data-stu-id="a5fa6-148">Using RIDs</span></span>

<span data-ttu-id="a5fa6-149">Для использования идентификаторов RID необходимо знать, какие идентификаторы RID существуют.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="a5fa6-150">В платформу регулярно добавляются новые идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="a5fa6-151">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="a5fa6-152">Переносимые идентификаторы RID — это новые значения, добавленными в схему RID, которые не привязаны к конкретной версии или дистрибутиву ОС.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-152">Portable RIDs are values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="a5fa6-153">Они рекомендуются для работы с несколькими дистрибутивами Linux, так как большинство идентификаторов RID дистрибутивов сопоставлено с переносными идентификаторами RID.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-153">They are the preferred choice, especially when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="a5fa6-154">Ниже представлена небольшая выборка наиболее распространенных RID, используемых для каждой ОС.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-154">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="a5fa6-155">Идентификаторы RID для Windows</span><span class="sxs-lookup"><span data-stu-id="a5fa6-155">Windows RIDs</span></span>

<span data-ttu-id="a5fa6-156">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-156">Only common values are listed.</span></span> <span data-ttu-id="a5fa6-157">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-157">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="a5fa6-158">Портативные</span><span class="sxs-lookup"><span data-stu-id="a5fa6-158">Portable</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="a5fa6-159">Windows 7 или Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a5fa6-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="a5fa6-160">Windows 8.1 или Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a5fa6-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="a5fa6-161">Windows 10 или Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a5fa6-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="a5fa6-162">Дополнительные сведения см. в статье [Зависимости и требования для .NET](./install/windows.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-162">For more information, see [.NET dependencies and requirements](./install/windows.md#dependencies).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="a5fa6-163">Идентификаторы RID для Linux</span><span class="sxs-lookup"><span data-stu-id="a5fa6-163">Linux RIDs</span></span>

<span data-ttu-id="a5fa6-164">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-164">Only common values are listed.</span></span> <span data-ttu-id="a5fa6-165">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-165">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="a5fa6-166">Устройства с дистрибутивами, не перечисленными ниже, могут работать с одним из переносных идентификаторов RID.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-166">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="a5fa6-167">Например, для устройств Raspberry Pi с дистрибутивом Linux, которого нет в списке, можно использовать `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-167">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="a5fa6-168">Портативные</span><span class="sxs-lookup"><span data-stu-id="a5fa6-168">Portable</span></span>
  - <span data-ttu-id="a5fa6-169">`linux-x64` (большинство дистрибутивов для компьютеров, например CentOS, Debian, Fedora, Ubuntu и производные от них);</span><span class="sxs-lookup"><span data-stu-id="a5fa6-169">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="a5fa6-170">`linux-musl-x64` (упрощенные дистрибутивы, которые используют [musl](https://wiki.musl-libc.org/projects-using-musl.html), например Alpine Linux);</span><span class="sxs-lookup"><span data-stu-id="a5fa6-170">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="a5fa6-171">`linux-arm` (дистрибутивы Linux, которые работают на архитектуре ARM, например Raspbian on Raspberry Pi Model 2+)</span><span class="sxs-lookup"><span data-stu-id="a5fa6-171">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="a5fa6-172">`linux-arm64` (дистрибутивы Linux, которые работают на 64-разрядной архитектуре ARM, например 64-разрядный Ubuntu Server на Raspberry Pi Model 3+)</span><span class="sxs-lookup"><span data-stu-id="a5fa6-172">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="a5fa6-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a5fa6-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="a5fa6-174">`rhel-x64` (заменен на `linux-x64` для RHEL новее версии 6);</span><span class="sxs-lookup"><span data-stu-id="a5fa6-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - `rhel.6-x64`
- <span data-ttu-id="a5fa6-175">Tizen</span><span class="sxs-lookup"><span data-stu-id="a5fa6-175">Tizen</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="a5fa6-176">Дополнительные сведения см. в статье [Зависимости и требования для .NET](./install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-176">For more information, see [.NET dependencies and requirements](./install/linux.md).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="a5fa6-177">Относительные идентификаторы macOS</span><span class="sxs-lookup"><span data-stu-id="a5fa6-177">macOS RIDs</span></span>

<span data-ttu-id="a5fa6-178">Относительные идентификаторы macOS используют старую фирменную символику "OSX".</span><span class="sxs-lookup"><span data-stu-id="a5fa6-178">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="a5fa6-179">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-179">Only common values are listed.</span></span> <span data-ttu-id="a5fa6-180">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa6-180">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="a5fa6-181">Портативные</span><span class="sxs-lookup"><span data-stu-id="a5fa6-181">Portable</span></span>
  - <span data-ttu-id="a5fa6-182">`osx-x64` (минимальная версия — macOS 10.12 Sierra).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-182">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="a5fa6-183">macOS 10.10 Yosemite:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-183">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="a5fa6-184">macOS 10.11 El Capitan:</span><span class="sxs-lookup"><span data-stu-id="a5fa6-184">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="a5fa6-185">macOS 10.12 Sierra</span><span class="sxs-lookup"><span data-stu-id="a5fa6-185">macOS 10.12 Sierra</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="a5fa6-186">macOS 10.13 High Sierra</span><span class="sxs-lookup"><span data-stu-id="a5fa6-186">macOS 10.13 High Sierra</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="a5fa6-187">macOS 10.14 Mojave</span><span class="sxs-lookup"><span data-stu-id="a5fa6-187">macOS 10.14 Mojave</span></span>
  - `osx.10.14-x64`
- <span data-ttu-id="a5fa6-188">macOS 10.15 Catalina</span><span class="sxs-lookup"><span data-stu-id="a5fa6-188">macOS 10.15 Catalina</span></span>
  - `osx.10.15-x64`
- <span data-ttu-id="a5fa6-189">macOS 11.01 Big Sur</span><span class="sxs-lookup"><span data-stu-id="a5fa6-189">macOS 11.01 Big Sur</span></span>
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

<span data-ttu-id="a5fa6-190">Дополнительные сведения см. в статье [Зависимости и требования для .NET](./install/macos.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="a5fa6-190">For more information, see [.NET dependencies and requirements](./install/macos.md#dependencies).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5fa6-191">См. также</span><span class="sxs-lookup"><span data-stu-id="a5fa6-191">See also</span></span>

- [<span data-ttu-id="a5fa6-192">Идентификаторы среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a5fa6-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/readme.md)
