---
title: Определение установленных версий платформы .NET Framework
description: Используйте код, regedit.exe или PowerShell, чтобы определить, какие версии .NET Framework установлены на компьютере, запросив реестр Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b4c5b6911a4be4f9ac156b600646c649549f88f8
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438141"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="690c1-103">Практическое руководство. Определение установленных версий платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="690c1-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="690c1-104">На компьютере можно [установить](../install/index.md) и запустить несколько версий платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="690c1-105">При разработке или развертывании приложения могут потребоваться сведения о том, какие версии .NET Framework установлены на компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="690c1-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="690c1-106">Реестр содержит список версий .NET Framework, установленных на компьютере.</span><span class="sxs-lookup"><span data-stu-id="690c1-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="690c1-107">Платформа .NET Framework состоит из двух основных компонентов, версии которым присваиваются отдельно:</span><span class="sxs-lookup"><span data-stu-id="690c1-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="690c1-108">набор сборок, которые являются коллекциями типов и ресурсов, обеспечивающих функции приложений</span><span class="sxs-lookup"><span data-stu-id="690c1-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="690c1-109">(.NET Framework и сборкам назначается один номер версии);</span><span class="sxs-lookup"><span data-stu-id="690c1-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="690c1-110">Например, версии .NET Framework включают в себя 4.5, 4.6.1 и 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="690c1-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="690c1-111">среда CLR, которая выполняет код приложения и управляет им.</span><span class="sxs-lookup"><span data-stu-id="690c1-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="690c1-112">Одна версия среды CLR обычно поддерживает несколько версий .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="690c1-113">Например, CLR версии 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000, поддерживает .NET Framework версий с 4 по 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="690c1-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="690c1-114">Версия CLR не менее 4.0.30319.42000 поддерживает версии .NET Framework начиная с .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="690c1-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="690c1-115">Средства, поддерживаемые сообществом, помогают определить, какие версии .NET Framework установлены:</span><span class="sxs-lookup"><span data-stu-id="690c1-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="690c1-116">Программа командной строки .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="690c1-116">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="690c1-117">Модуль PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="690c1-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="690c1-118">Сведения об определении установленных обновлений для каждой версии платформы .NET Framework см. в статье [Практическое руководство. Определение установленных обновлений платформы .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="690c1-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="690c1-119">Обнаружение .NET Framework 4.5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="690c1-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="690c1-120">Версия .NET Framework (4.5 и более поздние), установленная на компьютере, указана в реестре в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="690c1-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="690c1-121">Если отсутствует подраздел **Full**, то .NET Framework 4.5 или более поздней версии не установлен.</span><span class="sxs-lookup"><span data-stu-id="690c1-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="690c1-122">Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.</span><span class="sxs-lookup"><span data-stu-id="690c1-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="690c1-123">Значение **Release** REG_DWORD в реестре представляет установленную версию .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="690c1-124">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="690c1-124">.NET Framework version</span></span> | <span data-ttu-id="690c1-125">Значение **Release**</span><span class="sxs-lookup"><span data-stu-id="690c1-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="690c1-126">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="690c1-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="690c1-127">Все версии операционной системы Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="690c1-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="690c1-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="690c1-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="690c1-129">Windows 8.1 и Windows Server 2012 R2: 378675</span><span class="sxs-lookup"><span data-stu-id="690c1-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="690c1-130">Все другие версии операционной системы Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="690c1-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="690c1-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="690c1-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="690c1-132">Все версии операционной системы Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="690c1-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="690c1-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="690c1-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="690c1-134">Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="690c1-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="690c1-135">Все другие версии операционной системы Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="690c1-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="690c1-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="690c1-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="690c1-137">Windows 10 с ноябрьским обновлением: 394254</span><span class="sxs-lookup"><span data-stu-id="690c1-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="690c1-138">Все остальные версии операционной системы Windows (включая Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="690c1-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="690c1-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="690c1-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="690c1-140">В юбилейном обновлении Windows 10 и Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="690c1-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="690c1-141">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="690c1-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="690c1-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="690c1-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="690c1-143">Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="690c1-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="690c1-144">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="690c1-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="690c1-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="690c1-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="690c1-146">Windows 10 Fall Creators Update и Windows Server версии 1709: 461308</span><span class="sxs-lookup"><span data-stu-id="690c1-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="690c1-147">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="690c1-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="690c1-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="690c1-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="690c1-149">Windows 10 за апрель 2018 г. Update и Windows Server версии 1803: 461808</span><span class="sxs-lookup"><span data-stu-id="690c1-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="690c1-150">Все остальные операционные системы, кроме Windows 10 с обновлением за апрель 2018 г. и Windows Server версии 1803: 461814</span><span class="sxs-lookup"><span data-stu-id="690c1-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="690c1-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="690c1-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="690c1-152">Обновление Windows 10 за май 2019 года и обновление Windows 10 за ноябрь 2019 года: 528040</span><span class="sxs-lookup"><span data-stu-id="690c1-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="690c1-153">Обновление Windows 10 за май 2020 года и обновление Windows 10 за октябрь 2020 года: 528372</span><span class="sxs-lookup"><span data-stu-id="690c1-153">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="690c1-154">Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="690c1-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="690c1-155">Минимальная версия</span><span class="sxs-lookup"><span data-stu-id="690c1-155">Minimum version</span></span>

<span data-ttu-id="690c1-156">Чтобы определить, присутствует ли *минимальная* версия .NET Framework, проверьте значение **Release** REG_DWORD, которое больше или равно соответствующему значению, указанному в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="690c1-156">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="690c1-157">Например, если приложение работает в .NET Framework 4.8 или более поздней версии, проверьте, является ли значение REG_DWORD **Release** *большим или равным* 528040.</span><span class="sxs-lookup"><span data-stu-id="690c1-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="690c1-158">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="690c1-158">.NET Framework version</span></span> | <span data-ttu-id="690c1-159">Минимальное значение</span><span class="sxs-lookup"><span data-stu-id="690c1-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="690c1-160">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="690c1-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="690c1-161">378389</span><span class="sxs-lookup"><span data-stu-id="690c1-161">378389</span></span> |
| <span data-ttu-id="690c1-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="690c1-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="690c1-163">378675</span><span class="sxs-lookup"><span data-stu-id="690c1-163">378675</span></span> |
| <span data-ttu-id="690c1-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="690c1-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="690c1-165">379893</span><span class="sxs-lookup"><span data-stu-id="690c1-165">379893</span></span> |
| <span data-ttu-id="690c1-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="690c1-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="690c1-167">393295</span><span class="sxs-lookup"><span data-stu-id="690c1-167">393295</span></span> |
| <span data-ttu-id="690c1-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="690c1-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="690c1-169">394254</span><span class="sxs-lookup"><span data-stu-id="690c1-169">394254</span></span> |
| <span data-ttu-id="690c1-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="690c1-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="690c1-171">394802</span><span class="sxs-lookup"><span data-stu-id="690c1-171">394802</span></span> |
| <span data-ttu-id="690c1-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="690c1-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="690c1-173">460798</span><span class="sxs-lookup"><span data-stu-id="690c1-173">460798</span></span> |
| <span data-ttu-id="690c1-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="690c1-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="690c1-175">461308</span><span class="sxs-lookup"><span data-stu-id="690c1-175">461308</span></span> |
| <span data-ttu-id="690c1-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="690c1-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="690c1-177">461808</span><span class="sxs-lookup"><span data-stu-id="690c1-177">461808</span></span> |
| <span data-ttu-id="690c1-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="690c1-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="690c1-179">528040</span><span class="sxs-lookup"><span data-stu-id="690c1-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="690c1-180">Использование редактора реестра</span><span class="sxs-lookup"><span data-stu-id="690c1-180">Use Registry Editor</span></span>

01. <span data-ttu-id="690c1-181">В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="690c1-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="690c1-182">(Для запуска программы regedit необходимы учетные данные администратора.)</span><span class="sxs-lookup"><span data-stu-id="690c1-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="690c1-183">В редакторе реестра откройте следующий подраздел: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="690c1-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="690c1-184">Если подраздел **Full** отсутствует, платформа .NET Framework 4.5 или более поздней версии не установлена.</span><span class="sxs-lookup"><span data-stu-id="690c1-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="690c1-185">Проверьте значение REG_DWORD с именем **Release**.</span><span class="sxs-lookup"><span data-stu-id="690c1-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="690c1-186">Если оно имеется, платформа .NET Framework 4.5 или более поздней версии установлена.</span><span class="sxs-lookup"><span data-stu-id="690c1-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="690c1-187">Это значение соответствует определенной версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="690c1-188">Например, на приведенном ниже рисунке значение параметра **Release** равно 528040, что является разделом выпуска для .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="690c1-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![Запись реестра для .NET Framework 4.5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="690c1-190">Использование PowerShell для проверки минимальной версии</span><span class="sxs-lookup"><span data-stu-id="690c1-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="690c1-191">Используйте команды PowerShell для проверки значения параметра **Release** в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="690c1-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="690c1-192">В приведенных ниже примерах значение **Release** проверяется с целью определить, установлена ли версия 4.6.2 или более поздняя версия .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="690c1-193">Код возвращает значение `True`, если одна из таких версий установлена, и `False` в противном случае.</span><span class="sxs-lookup"><span data-stu-id="690c1-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="690c1-194">Отправка запросов в реестр с помощью кода</span><span class="sxs-lookup"><span data-stu-id="690c1-194">Query the registry using code</span></span>

01. <span data-ttu-id="690c1-195">Используйте методы <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> и <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** в реестре Windows.</span><span class="sxs-lookup"><span data-stu-id="690c1-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="690c1-196">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="690c1-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="690c1-197">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="690c1-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="690c1-198">Например, подразделом реестра для .NET Framework 4.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="690c1-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="690c1-199">Проверьте значение REG_DWORD **Release**, чтобы определить установленную версию.</span><span class="sxs-lookup"><span data-stu-id="690c1-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="690c1-200">Для обеспечения совместимости с последующими версиями значение должно быть больше или равно значению, указанному в [таблице версий .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="690c1-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="690c1-201">В следующем примере проверяется значение **Release** в реестре для поиска установленных версий .NET Framework 4.5–4.8.</span><span class="sxs-lookup"><span data-stu-id="690c1-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="690c1-202">Этот пример выводит данные, подобные следующим:</span><span class="sxs-lookup"><span data-stu-id="690c1-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="690c1-203">В этом примере применяются рекомендации для проверки версии:</span><span class="sxs-lookup"><span data-stu-id="690c1-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="690c1-204">Проверяется, имеет ли параметр **Release** значение, *большее или равное* значению известных разделов выпуска.</span><span class="sxs-lookup"><span data-stu-id="690c1-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="690c1-205">Проверка выполняется с самой последней до самой ранней версии.</span><span class="sxs-lookup"><span data-stu-id="690c1-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="690c1-206">Обнаружение .NET Framework с 1.0 по 4.0</span><span class="sxs-lookup"><span data-stu-id="690c1-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="690c1-207">Каждая версия .NET Framework с 1.1 по 4.0 указана в виде подраздела в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span><span class="sxs-lookup"><span data-stu-id="690c1-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="690c1-208">В следующей таблице перечислены пути к каждой версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="690c1-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="690c1-209">Для большинства версий существует значение REG_DWORD **Install**, равное `1`, чтобы указать, что эта версия установлена.</span><span class="sxs-lookup"><span data-stu-id="690c1-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="690c1-210">В этих подразделах также имеется значение REG_SZ **Version**, содержащее строку версии.</span><span class="sxs-lookup"><span data-stu-id="690c1-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="690c1-211">Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.</span><span class="sxs-lookup"><span data-stu-id="690c1-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="690c1-212">Версия платформы</span><span class="sxs-lookup"><span data-stu-id="690c1-212">Framework Version</span></span>  | <span data-ttu-id="690c1-213">Подраздел реестра</span><span class="sxs-lookup"><span data-stu-id="690c1-213">Registry Subkey</span></span> | <span data-ttu-id="690c1-214">Значение</span><span class="sxs-lookup"><span data-stu-id="690c1-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="690c1-215">1.0</span><span class="sxs-lookup"><span data-stu-id="690c1-215">1.0</span></span>                | <span data-ttu-id="690c1-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="690c1-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="690c1-217">REG_SZ **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="690c1-218">1.1</span><span class="sxs-lookup"><span data-stu-id="690c1-218">1.1</span></span>                | <span data-ttu-id="690c1-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="690c1-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="690c1-220">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="690c1-221">2.0</span><span class="sxs-lookup"><span data-stu-id="690c1-221">2.0</span></span>                | <span data-ttu-id="690c1-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="690c1-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="690c1-223">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="690c1-224">3.0</span><span class="sxs-lookup"><span data-stu-id="690c1-224">3.0</span></span>                | <span data-ttu-id="690c1-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span><span class="sxs-lookup"><span data-stu-id="690c1-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="690c1-226">Значение REG_DWORD **InstallSuccess** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="690c1-227">3.5</span><span class="sxs-lookup"><span data-stu-id="690c1-227">3.5</span></span>                | <span data-ttu-id="690c1-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="690c1-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="690c1-229">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="690c1-230">Клиентский профиль 4.0</span><span class="sxs-lookup"><span data-stu-id="690c1-230">4.0 Client Profile</span></span> | <span data-ttu-id="690c1-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span><span class="sxs-lookup"><span data-stu-id="690c1-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="690c1-232">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="690c1-233">Полный профиль 4.0</span><span class="sxs-lookup"><span data-stu-id="690c1-233">4.0 Full Profile</span></span>   | <span data-ttu-id="690c1-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span><span class="sxs-lookup"><span data-stu-id="690c1-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="690c1-235">REG_DWORD **Install** равно `1`</span><span class="sxs-lookup"><span data-stu-id="690c1-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="690c1-236">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="690c1-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="690c1-237">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="690c1-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="690c1-238">Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="690c1-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="690c1-239">Обратите внимание, что путь реестра к подразделу .NET Framework 1.0 отличается от остальных.</span><span class="sxs-lookup"><span data-stu-id="690c1-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="690c1-240">Использование редактора реестра (более ранние версии платформы)</span><span class="sxs-lookup"><span data-stu-id="690c1-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="690c1-241">В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="690c1-241">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="690c1-242">Для запуска программы regedit необходимы учетные данные администратора.</span><span class="sxs-lookup"><span data-stu-id="690c1-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="690c1-243">Откройте подраздел, соответствующий версии, которую необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="690c1-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="690c1-244">Используйте таблицу в разделе [Обнаружение .NET Framework с 1.0 по 4.0](#detect-net-framework-10-through-40).</span><span class="sxs-lookup"><span data-stu-id="690c1-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="690c1-245">На приведенном ниже рисунке показан подраздел для версии .NET Framework 3.5 вместе со значением **Version**.</span><span class="sxs-lookup"><span data-stu-id="690c1-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="690c1-246">![Запись реестра для .NET Framework 3.5.](./media/net-4-and-earlier.png "NET Framework 3.5 и предыдущие версии")</span><span class="sxs-lookup"><span data-stu-id="690c1-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="690c1-247">Запрос реестра с помощью кода (более ранние версии платформы)</span><span class="sxs-lookup"><span data-stu-id="690c1-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="690c1-248">Используйте класс <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** в реестре Windows.</span><span class="sxs-lookup"><span data-stu-id="690c1-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="690c1-249">Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее.</span><span class="sxs-lookup"><span data-stu-id="690c1-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="690c1-250">64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** .</span><span class="sxs-lookup"><span data-stu-id="690c1-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="690c1-251">Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="690c1-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="690c1-252">В следующем примере ищутся установленные версии .NET Framework 1–4:</span><span class="sxs-lookup"><span data-stu-id="690c1-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="690c1-253">В этом примере отобразятся выходные данные, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="690c1-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="690c1-254">Поиск версий CLR</span><span class="sxs-lookup"><span data-stu-id="690c1-254">Find CLR versions</span></span>

<span data-ttu-id="690c1-255">.NET Framework CLR, установленный с .NET Framework, имеет отдельную версию.</span><span class="sxs-lookup"><span data-stu-id="690c1-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="690c1-256">Есть два способа определить версию среды выполнения .NET Framework CLR:</span><span class="sxs-lookup"><span data-stu-id="690c1-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="690c1-257">**Инструмент Clrver.exe**</span><span class="sxs-lookup"><span data-stu-id="690c1-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="690c1-258">Для определения версий среды CLR, установленных на компьютере, можно использовать [средство CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="690c1-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="690c1-259">Откройте [командную строку разработчика для Visual Studio](../tools/developer-command-prompt-for-vs.md) и введите `clrver`.</span><span class="sxs-lookup"><span data-stu-id="690c1-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="690c1-260">Пример результатов выполнения:</span><span class="sxs-lookup"><span data-stu-id="690c1-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="690c1-261">**Класс `Environment`**</span><span class="sxs-lookup"><span data-stu-id="690c1-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="690c1-262">Для .NET Framework 4.5 и более поздних версий не следует использовать свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> для определения версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="690c1-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="690c1-263">Вместо этого выполните запрос к реестру, как описано в разделе [Обнаружение .NET Framework 4.5 и более поздних версий](#detect-net-framework-45-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="690c1-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="690c1-264">Выполните запрос к свойству <xref:System.Environment.Version?displayProperty=nameWithType>, чтобы получить объект <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="690c1-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="690c1-265">Возвращенный объект `System.Version` указывает версию среды выполнения, в которой в настоящее время выполняется код.</span><span class="sxs-lookup"><span data-stu-id="690c1-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="690c1-266">Он не содержит версий сборок или других версий среды выполнения, которые установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="690c1-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="690c1-267">Для платформы .NET Framework версий 4, 4.5, 4.5.1 и 4.5.2 возвращаемый объект <xref:System.Version> имеет строковое представление 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000.</span><span class="sxs-lookup"><span data-stu-id="690c1-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="690c1-268">Для .NET Framework 4.6 и более поздних версий оно имеет форму 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="690c1-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="690c1-269">Получив объект **Version**, выполните к нему запрос:</span><span class="sxs-lookup"><span data-stu-id="690c1-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="690c1-270">Чтобы получить идентификатор основного выпуска (например, *4* в случае версии 4.0), используйте свойство <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="690c1-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="690c1-271">Чтобы получить идентификатор дополнительной версии (например, *0* в случае версии 4.0), используйте свойство <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="690c1-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="690c1-272">Чтобы получить всю строку версии (например, *4.0.30319.18010*), используйте метод <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="690c1-272">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="690c1-273">Он возвращает одно значение, соответствующее версии среды выполнения, в которой выполняется код.</span><span class="sxs-lookup"><span data-stu-id="690c1-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="690c1-274">Он не возвращает версий сборок или других версий среды выполнения, которые установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="690c1-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="690c1-275">В следующем примере свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> используется для получения сведений о версии среды CLR:</span><span class="sxs-lookup"><span data-stu-id="690c1-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="690c1-276">В этом примере отобразятся выходные данные, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="690c1-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="690c1-277">См. также</span><span class="sxs-lookup"><span data-stu-id="690c1-277">See also</span></span>

- [<span data-ttu-id="690c1-278">Практическое руководство. Определение установленных обновлений платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="690c1-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="690c1-279">Установка .NET Framework для разработчиков</span><span class="sxs-lookup"><span data-stu-id="690c1-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="690c1-280">Версии и зависимости платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="690c1-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
