---
title: Определение установленных версий платформы .NET Framework
description: Используйте код, regedit.exe или PowerShell, чтобы определить, какие версии .NET Framework установлены на компьютере, запросив реестр Windows.
ms.date: 12/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining installed versions
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: a219514fafdcb17db259e089afa8318dbab24811
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851833"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="476e7-103">Практическое руководство. Определение установленных версий платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476e7-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="476e7-104">На компьютере можно [установить](../install/index.md) и запустить несколько версий платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="476e7-105">При разработке или развертывании приложения могут потребоваться сведения о том, какие версии .NET Framework установлены на компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="476e7-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="476e7-106">Реестр содержит список версий .NET Framework, установленных на компьютере.</span><span class="sxs-lookup"><span data-stu-id="476e7-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

> [!NOTE]
> <span data-ttu-id="476e7-107">Эта статья относится к .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-107">This article is specific to .NET Framework.</span></span> <span data-ttu-id="476e7-108">Чтобы определить, какие пакеты SDK и среды выполнения .NET Core и .NET 5+ установлены, см. раздел [Как проверить, что .NET уже установлен](../../core/install/how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="476e7-108">To determine which .NET Core and .NET 5+ SDKs and runtimes are installed, see [How to check that .NET is already installed](../../core/install/how-to-detect-installed-versions.md).</span></span>

<span data-ttu-id="476e7-109">Платформа .NET Framework состоит из двух основных компонентов, версии которым присваиваются отдельно:</span><span class="sxs-lookup"><span data-stu-id="476e7-109">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="476e7-110">набор сборок, которые являются коллекциями типов и ресурсов, обеспечивающих функции приложений</span><span class="sxs-lookup"><span data-stu-id="476e7-110">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="476e7-111">(.NET Framework и сборкам назначается один номер версии);</span><span class="sxs-lookup"><span data-stu-id="476e7-111">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="476e7-112">Например, версии .NET Framework включают в себя 4.5, 4.6.1 и 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="476e7-112">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="476e7-113">среда CLR, которая выполняет код приложения и управляет им.</span><span class="sxs-lookup"><span data-stu-id="476e7-113">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="476e7-114">Одна версия среды CLR обычно поддерживает несколько версий .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-114">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="476e7-115">Например, CLR версии 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000, поддерживает .NET Framework версий с 4 по 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="476e7-115">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="476e7-116">Версия CLR не менее 4.0.30319.42000 поддерживает версии .NET Framework начиная с .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="476e7-116">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="476e7-117">Средства, поддерживаемые сообществом, помогают определить, какие версии .NET Framework установлены:</span><span class="sxs-lookup"><span data-stu-id="476e7-117">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="476e7-118">Программа командной строки .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="476e7-118">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="476e7-119">Модуль PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="476e7-119">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="476e7-120">Сведения об определении установленных обновлений для каждой версии платформы .NET Framework см. в статье [Практическое руководство. Определение установленных обновлений платформы .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="476e7-120">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="determine-which-net-implementation-and-version-an-app-is-running-on"></a><span data-ttu-id="476e7-121">Определение реализации и версии .NET, в которой работает приложение</span><span class="sxs-lookup"><span data-stu-id="476e7-121">Determine which .NET implementation and version an app is running on</span></span>

<span data-ttu-id="476e7-122">Для запроса реализации и версии .NET, в которой работает ваше приложение, можно использовать свойство <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="476e7-122">You can use the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property to query for which .NET implementation and version your app is running on.</span></span> <span data-ttu-id="476e7-123">Если приложение работает в .NET Framework, выходные данные будут выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="476e7-123">If the app is running on .NET Framework, the output will be similar to:</span></span>

```output
.NET Framework 4.8.4250.0
```

<span data-ttu-id="476e7-124">Если же приложение работает в .NET Core или .NET 5+, выходные данные будут выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="476e7-124">By comparison, if the app is running on .NET Core or .NET 5+, the output will be similar to:</span></span>

```output
.NET Core 3.1.9
.NET 5.0.0
```

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="476e7-125">Обнаружение .NET Framework 4.5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="476e7-125">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="476e7-126">Версия .NET Framework (4.5 и более поздние), установленная на компьютере, указана в реестре в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="476e7-126">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="476e7-127">Если отсутствует подраздел **Full**, то .NET Framework 4.5 или более поздней версии не установлен.</span><span class="sxs-lookup"><span data-stu-id="476e7-127">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="476e7-128">Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.</span><span class="sxs-lookup"><span data-stu-id="476e7-128">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="476e7-129">Значение **Release** REG_DWORD в реестре представляет установленную версию .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-129">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="476e7-130">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476e7-130">.NET Framework version</span></span> | <span data-ttu-id="476e7-131">Значение **Release**</span><span class="sxs-lookup"><span data-stu-id="476e7-131">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="476e7-132">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="476e7-132">.NET Framework 4.5</span></span>     | <span data-ttu-id="476e7-133">Все версии операционной системы Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="476e7-133">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="476e7-134">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="476e7-134">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="476e7-135">Windows 8.1 и Windows Server 2012 R2: 378675</span><span class="sxs-lookup"><span data-stu-id="476e7-135">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="476e7-136">Все другие версии операционной системы Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="476e7-136">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="476e7-137">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="476e7-137">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="476e7-138">Все версии операционной системы Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="476e7-138">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="476e7-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="476e7-139">.NET Framework 4.6</span></span>     | <span data-ttu-id="476e7-140">Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="476e7-140">On Windows 10: 393295</span></span><br /><span data-ttu-id="476e7-141">Все другие версии операционной системы Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="476e7-141">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="476e7-142">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="476e7-142">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="476e7-143">Windows 10 с ноябрьским обновлением: 394254</span><span class="sxs-lookup"><span data-stu-id="476e7-143">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="476e7-144">Все остальные версии операционной системы Windows (включая Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="476e7-144">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="476e7-145">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="476e7-145">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="476e7-146">В юбилейном обновлении Windows 10 и Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="476e7-146">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="476e7-147">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="476e7-147">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="476e7-148">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="476e7-148">.NET Framework 4.7</span></span>     | <span data-ttu-id="476e7-149">Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="476e7-149">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="476e7-150">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="476e7-150">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="476e7-151">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="476e7-151">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="476e7-152">Windows 10 Fall Creators Update и Windows Server версии 1709: 461308</span><span class="sxs-lookup"><span data-stu-id="476e7-152">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="476e7-153">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="476e7-153">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="476e7-154">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="476e7-154">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="476e7-155">Windows 10 за апрель 2018 г. Update и Windows Server версии 1803: 461808</span><span class="sxs-lookup"><span data-stu-id="476e7-155">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="476e7-156">Все остальные операционные системы, кроме Windows 10 с обновлением за апрель 2018 г. и Windows Server версии 1803: 461814</span><span class="sxs-lookup"><span data-stu-id="476e7-156">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="476e7-157">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="476e7-157">.NET Framework 4.8</span></span>     | <span data-ttu-id="476e7-158">Обновление Windows 10 за май 2019 года и обновление Windows 10 за ноябрь 2019 года: 528040</span><span class="sxs-lookup"><span data-stu-id="476e7-158">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="476e7-159">Обновление Windows 10 за май 2020 года и обновление Windows 10 за октябрь 2020 года: 528372</span><span class="sxs-lookup"><span data-stu-id="476e7-159">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="476e7-160">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="476e7-160">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="476e7-161">Минимальная версия</span><span class="sxs-lookup"><span data-stu-id="476e7-161">Minimum version</span></span>

<span data-ttu-id="476e7-162">Чтобы определить, присутствует ли *минимальная* версия .NET Framework, проверьте значение **Release** REG_DWORD, которое больше или равно соответствующему значению, указанному в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="476e7-162">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="476e7-163">Например, если приложение работает в .NET Framework 4.8 или более поздней версии, проверьте, является ли значение REG_DWORD **Release** *большим или равным* 528040.</span><span class="sxs-lookup"><span data-stu-id="476e7-163">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="476e7-164">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476e7-164">.NET Framework version</span></span> | <span data-ttu-id="476e7-165">Минимальное значение</span><span class="sxs-lookup"><span data-stu-id="476e7-165">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="476e7-166">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="476e7-166">.NET Framework 4.5</span></span>     | <span data-ttu-id="476e7-167">378389</span><span class="sxs-lookup"><span data-stu-id="476e7-167">378389</span></span> |
| <span data-ttu-id="476e7-168">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="476e7-168">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="476e7-169">378675</span><span class="sxs-lookup"><span data-stu-id="476e7-169">378675</span></span> |
| <span data-ttu-id="476e7-170">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="476e7-170">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="476e7-171">379893</span><span class="sxs-lookup"><span data-stu-id="476e7-171">379893</span></span> |
| <span data-ttu-id="476e7-172">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="476e7-172">.NET Framework 4.6</span></span>     | <span data-ttu-id="476e7-173">393295</span><span class="sxs-lookup"><span data-stu-id="476e7-173">393295</span></span> |
| <span data-ttu-id="476e7-174">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="476e7-174">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="476e7-175">394254</span><span class="sxs-lookup"><span data-stu-id="476e7-175">394254</span></span> |
| <span data-ttu-id="476e7-176">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="476e7-176">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="476e7-177">394802</span><span class="sxs-lookup"><span data-stu-id="476e7-177">394802</span></span> |
| <span data-ttu-id="476e7-178">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="476e7-178">.NET Framework 4.7</span></span>     | <span data-ttu-id="476e7-179">460798</span><span class="sxs-lookup"><span data-stu-id="476e7-179">460798</span></span> |
| <span data-ttu-id="476e7-180">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="476e7-180">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="476e7-181">461308</span><span class="sxs-lookup"><span data-stu-id="476e7-181">461308</span></span> |
| <span data-ttu-id="476e7-182">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="476e7-182">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="476e7-183">461808</span><span class="sxs-lookup"><span data-stu-id="476e7-183">461808</span></span> |
| <span data-ttu-id="476e7-184">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="476e7-184">.NET Framework 4.8</span></span>     | <span data-ttu-id="476e7-185">528040</span><span class="sxs-lookup"><span data-stu-id="476e7-185">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="476e7-186">Использование редактора реестра</span><span class="sxs-lookup"><span data-stu-id="476e7-186">Use Registry Editor</span></span>

1. <span data-ttu-id="476e7-187">В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="476e7-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="476e7-188">(Для запуска программы regedit необходимы учетные данные администратора.)</span><span class="sxs-lookup"><span data-stu-id="476e7-188">(You must have administrative credentials to run regedit.)</span></span>

1. <span data-ttu-id="476e7-189">В редакторе реестра откройте следующий подраздел: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="476e7-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="476e7-190">Если подраздел **Full** отсутствует, платформа .NET Framework 4.5 или более поздней версии не установлена.</span><span class="sxs-lookup"><span data-stu-id="476e7-190">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

1. <span data-ttu-id="476e7-191">Проверьте значение REG_DWORD с именем **Release**.</span><span class="sxs-lookup"><span data-stu-id="476e7-191">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="476e7-192">Если оно имеется, платформа .NET Framework 4.5 или более поздней версии установлена.</span><span class="sxs-lookup"><span data-stu-id="476e7-192">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="476e7-193">Это значение соответствует определенной версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-193">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="476e7-194">Например, на приведенном ниже рисунке значение параметра **Release** равно 528040, что является разделом выпуска для .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="476e7-194">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![Запись реестра для .NET Framework 4.5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="476e7-196">Использование PowerShell для проверки минимальной версии</span><span class="sxs-lookup"><span data-stu-id="476e7-196">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="476e7-197">Используйте команды PowerShell для проверки значения параметра **Release** в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="476e7-197">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="476e7-198">В приведенных ниже примерах значение **Release** проверяется с целью определить, установлена ли версия 4.6.2 или более поздняя версия .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-198">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="476e7-199">Код возвращает значение `True`, если одна из таких версий установлена, и `False` в противном случае.</span><span class="sxs-lookup"><span data-stu-id="476e7-199">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="476e7-200">Отправка запросов в реестр с помощью кода</span><span class="sxs-lookup"><span data-stu-id="476e7-200">Query the registry using code</span></span>

01. <span data-ttu-id="476e7-201">Используйте методы <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> и <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** в реестре Windows.</span><span class="sxs-lookup"><span data-stu-id="476e7-201">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="476e7-202">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="476e7-202">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="476e7-203">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="476e7-203">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="476e7-204">Например, подразделом реестра для .NET Framework 4.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="476e7-204">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="476e7-205">Проверьте значение REG_DWORD **Release**, чтобы определить установленную версию.</span><span class="sxs-lookup"><span data-stu-id="476e7-205">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="476e7-206">Для обеспечения совместимости с последующими версиями значение должно быть больше или равно значению, указанному в [таблице версий .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="476e7-206">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="476e7-207">В следующем примере проверяется значение **Release** в реестре для поиска установленных версий .NET Framework 4.5–4.8.</span><span class="sxs-lookup"><span data-stu-id="476e7-207">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="476e7-208">Этот пример выводит данные, подобные следующим:</span><span class="sxs-lookup"><span data-stu-id="476e7-208">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="476e7-209">В этом примере применяются рекомендации для проверки версии:</span><span class="sxs-lookup"><span data-stu-id="476e7-209">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="476e7-210">Проверяется, имеет ли параметр **Release** значение, *большее или равное* значению известных разделов выпуска.</span><span class="sxs-lookup"><span data-stu-id="476e7-210">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="476e7-211">Проверка выполняется с самой последней до самой ранней версии.</span><span class="sxs-lookup"><span data-stu-id="476e7-211">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="476e7-212">Обнаружение .NET Framework с 1.0 по 4.0</span><span class="sxs-lookup"><span data-stu-id="476e7-212">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="476e7-213">Каждая версия .NET Framework с 1.1 по 4.0 указана в виде подраздела в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span><span class="sxs-lookup"><span data-stu-id="476e7-213">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="476e7-214">В следующей таблице перечислены пути к каждой версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476e7-214">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="476e7-215">Для большинства версий существует значение REG_DWORD **Install**, равное `1`, чтобы указать, что эта версия установлена.</span><span class="sxs-lookup"><span data-stu-id="476e7-215">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="476e7-216">В этих подразделах также имеется значение REG_SZ **Version**, содержащее строку версии.</span><span class="sxs-lookup"><span data-stu-id="476e7-216">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="476e7-217">Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.</span><span class="sxs-lookup"><span data-stu-id="476e7-217">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="476e7-218">Версия платформы</span><span class="sxs-lookup"><span data-stu-id="476e7-218">Framework Version</span></span>  | <span data-ttu-id="476e7-219">Подраздел реестра</span><span class="sxs-lookup"><span data-stu-id="476e7-219">Registry Subkey</span></span> | <span data-ttu-id="476e7-220">Значение</span><span class="sxs-lookup"><span data-stu-id="476e7-220">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="476e7-221">1.0</span><span class="sxs-lookup"><span data-stu-id="476e7-221">1.0</span></span>                | <span data-ttu-id="476e7-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="476e7-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="476e7-223">REG_SZ **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-223">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="476e7-224">1.1</span><span class="sxs-lookup"><span data-stu-id="476e7-224">1.1</span></span>                | <span data-ttu-id="476e7-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="476e7-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="476e7-226">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-226">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="476e7-227">2.0</span><span class="sxs-lookup"><span data-stu-id="476e7-227">2.0</span></span>                | <span data-ttu-id="476e7-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="476e7-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="476e7-229">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="476e7-230">3.0</span><span class="sxs-lookup"><span data-stu-id="476e7-230">3.0</span></span>                | <span data-ttu-id="476e7-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span><span class="sxs-lookup"><span data-stu-id="476e7-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="476e7-232">Значение REG_DWORD **InstallSuccess** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-232">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="476e7-233">3.5</span><span class="sxs-lookup"><span data-stu-id="476e7-233">3.5</span></span>                | <span data-ttu-id="476e7-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="476e7-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="476e7-235">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-235">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="476e7-236">Клиентский профиль 4.0</span><span class="sxs-lookup"><span data-stu-id="476e7-236">4.0 Client Profile</span></span> | <span data-ttu-id="476e7-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span><span class="sxs-lookup"><span data-stu-id="476e7-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="476e7-238">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-238">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="476e7-239">Полный профиль 4.0</span><span class="sxs-lookup"><span data-stu-id="476e7-239">4.0 Full Profile</span></span>   | <span data-ttu-id="476e7-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span><span class="sxs-lookup"><span data-stu-id="476e7-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="476e7-241">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="476e7-241">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="476e7-242">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="476e7-242">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="476e7-243">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="476e7-243">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="476e7-244">Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="476e7-244">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="476e7-245">Обратите внимание, что путь реестра к подразделу .NET Framework 1.0 отличается от остальных.</span><span class="sxs-lookup"><span data-stu-id="476e7-245">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="476e7-246">Использование редактора реестра (более ранние версии платформы)</span><span class="sxs-lookup"><span data-stu-id="476e7-246">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="476e7-247">В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="476e7-247">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="476e7-248">Для запуска программы regedit необходимы учетные данные администратора.</span><span class="sxs-lookup"><span data-stu-id="476e7-248">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="476e7-249">Откройте подраздел, соответствующий версии, которую необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="476e7-249">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="476e7-250">Используйте таблицу в разделе [Обнаружение .NET Framework с 1.0 по 4.0](#detect-net-framework-10-through-40).</span><span class="sxs-lookup"><span data-stu-id="476e7-250">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="476e7-251">На приведенном ниже рисунке показан подраздел для версии .NET Framework 3.5 вместе со значением **Version**.</span><span class="sxs-lookup"><span data-stu-id="476e7-251">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="476e7-252">![Запись реестра для .NET Framework 3.5.](./media/net-4-and-earlier.png "NET Framework 3.5 и предыдущие версии")</span><span class="sxs-lookup"><span data-stu-id="476e7-252">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="476e7-253">Запрос реестра с помощью кода (более ранние версии платформы)</span><span class="sxs-lookup"><span data-stu-id="476e7-253">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="476e7-254">Используйте класс <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** в реестре Windows.</span><span class="sxs-lookup"><span data-stu-id="476e7-254">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="476e7-255">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="476e7-255">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="476e7-256">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="476e7-256">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="476e7-257">Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="476e7-257">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="476e7-258">В следующем примере ищутся установленные версии .NET Framework 1–4:</span><span class="sxs-lookup"><span data-stu-id="476e7-258">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="476e7-259">В этом примере отобразятся выходные данные, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="476e7-259">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="476e7-260">Поиск версий CLR</span><span class="sxs-lookup"><span data-stu-id="476e7-260">Find CLR versions</span></span>

<span data-ttu-id="476e7-261">.NET Framework CLR, установленный с .NET Framework, имеет отдельную версию.</span><span class="sxs-lookup"><span data-stu-id="476e7-261">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="476e7-262">Есть два способа определить версию среды выполнения .NET Framework CLR:</span><span class="sxs-lookup"><span data-stu-id="476e7-262">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="476e7-263">**Инструмент Clrver.exe**</span><span class="sxs-lookup"><span data-stu-id="476e7-263">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="476e7-264">Для определения версий среды CLR, установленных на компьютере, можно использовать [средство CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="476e7-264">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="476e7-265">Откройте [командную строку разработчика для Visual Studio](../tools/developer-command-prompt-for-vs.md) и введите `clrver`.</span><span class="sxs-lookup"><span data-stu-id="476e7-265">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="476e7-266">Пример результатов выполнения:</span><span class="sxs-lookup"><span data-stu-id="476e7-266">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="476e7-267">**Класс `Environment`**</span><span class="sxs-lookup"><span data-stu-id="476e7-267">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="476e7-268">Для .NET Framework 4.5 и более поздних версий не следует использовать свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> для определения версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="476e7-268">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="476e7-269">Вместо этого выполните запрос к реестру, как описано в разделе [Обнаружение .NET Framework 4.5 и более поздних версий](#detect-net-framework-45-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="476e7-269">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="476e7-270">Выполните запрос к свойству <xref:System.Environment.Version?displayProperty=nameWithType>, чтобы получить объект <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="476e7-270">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="476e7-271">Возвращенный объект `System.Version` указывает версию среды выполнения, в которой в настоящее время выполняется код.</span><span class="sxs-lookup"><span data-stu-id="476e7-271">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="476e7-272">Он не содержит версий сборок или других версий среды выполнения, которые установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="476e7-272">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="476e7-273">Для платформы .NET Framework версий 4, 4.5, 4.5.1 и 4.5.2 возвращаемый объект <xref:System.Version> имеет строковое представление 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000.</span><span class="sxs-lookup"><span data-stu-id="476e7-273">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="476e7-274">Для .NET Framework 4.6 и более поздних версий оно имеет форму 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="476e7-274">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="476e7-275">Получив объект **Version**, выполните к нему запрос:</span><span class="sxs-lookup"><span data-stu-id="476e7-275">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="476e7-276">Чтобы получить идентификатор основного выпуска (например, *4* в случае версии 4.0), используйте свойство <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="476e7-276">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="476e7-277">Чтобы получить идентификатор дополнительной версии (например, *0* в случае версии 4.0), используйте свойство <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="476e7-277">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="476e7-278">Чтобы получить всю строку версии (например, *4.0.30319.18010*), используйте метод <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="476e7-278">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="476e7-279">Он возвращает одно значение, соответствующее версии среды выполнения, в которой выполняется код.</span><span class="sxs-lookup"><span data-stu-id="476e7-279">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="476e7-280">Он не возвращает версий сборок или других версий среды выполнения, которые установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="476e7-280">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="476e7-281">В следующем примере свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> используется для получения сведений о версии среды CLR:</span><span class="sxs-lookup"><span data-stu-id="476e7-281">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="476e7-282">В этом примере отобразятся выходные данные, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="476e7-282">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="476e7-283">См. также</span><span class="sxs-lookup"><span data-stu-id="476e7-283">See also</span></span>

- [<span data-ttu-id="476e7-284">Практическое руководство. Определение установленных обновлений платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476e7-284">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="476e7-285">Установка .NET Framework для разработчиков</span><span class="sxs-lookup"><span data-stu-id="476e7-285">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="476e7-286">Версии и зависимости платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="476e7-286">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
