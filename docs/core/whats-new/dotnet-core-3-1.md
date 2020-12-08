---
title: Новые возможности .NET Core 3.1
description: Дополнительные сведения о новых возможностях .NET Core 3.1.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 9caecdcc3516db2bd71420184fbd21f7837552a7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437923"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="c627e-103">Новые возможности .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c627e-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="c627e-104">В этой статье описаны новые возможности в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c627e-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="c627e-105">Этот выпуск содержит небольшие улучшения относительно .NET Core 3.0. Внимание уделялось нескольким небольшим, но важным исправлениям.</span><span class="sxs-lookup"><span data-stu-id="c627e-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="c627e-106">Основная особенность .NET Core 3.1 заключается в том, что это выпуск [долгосрочной поддержки (LTS)](#long-term-support).</span><span class="sxs-lookup"><span data-stu-id="c627e-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="c627e-107">Если вы используете Visual Studio 2019, для работы с проектами .NET Core 3.1 необходимо обновить Visual Studio 2019 до [версии 16.4 или более поздней](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="c627e-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="c627e-108">Сведения о новых возможностях Visual Studio версии 16.4 см. на странице [Новые возможности Visual Studio 2019 версии 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="c627e-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="c627e-109">Visual Studio для Mac также поддерживает и содержит .NET Core 3.1 в версии Visual Studio для Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="c627e-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="c627e-110">Дополнительные сведения см. в [объявлении о выпуске .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="c627e-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="c627e-111">[Скачайте .NET Core 3.1 и начните работу](https://dotnet.microsoft.com/download/dotnet-core/3.1) в Windows, macOS или Linux.</span><span class="sxs-lookup"><span data-stu-id="c627e-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="c627e-112">Долгосрочная поддержка</span><span class="sxs-lookup"><span data-stu-id="c627e-112">Long-term support</span></span>

<span data-ttu-id="c627e-113">.NET Core 3.1 объявляется выпуском долгосрочной поддержки. Это означает, что корпорация Майкрософт будет поддерживать его в течение следующих трех лет.</span><span class="sxs-lookup"><span data-stu-id="c627e-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="c627e-114">Мы настоятельно рекомендуем перевести все приложения на .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c627e-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="c627e-115">Текущий жизненный цикл других основных выпусков:</span><span class="sxs-lookup"><span data-stu-id="c627e-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="c627e-116">Выпуск</span><span class="sxs-lookup"><span data-stu-id="c627e-116">Release</span></span> | <span data-ttu-id="c627e-117">Примечание.</span><span class="sxs-lookup"><span data-stu-id="c627e-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="c627e-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c627e-118">.NET Core 3.0</span></span> | <span data-ttu-id="c627e-119">Окончание жизненного цикла 3 марта 2020 г.</span><span class="sxs-lookup"><span data-stu-id="c627e-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="c627e-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c627e-120">.NET Core 2.2</span></span> | <span data-ttu-id="c627e-121">Окончание жизненного цикла 23 декабря 2019 г.</span><span class="sxs-lookup"><span data-stu-id="c627e-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="c627e-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c627e-122">.NET Core 2.1</span></span> | <span data-ttu-id="c627e-123">Окончание жизненного цикла 21 августа 2021 г.</span><span class="sxs-lookup"><span data-stu-id="c627e-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="c627e-124">Дополнительные сведения см. в статье о [политике поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c627e-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="c627e-125">Файл appHost в macOS и заверение</span><span class="sxs-lookup"><span data-stu-id="c627e-125">macOS appHost and notarization</span></span>

<span data-ttu-id="c627e-126">*Только macOS*</span><span class="sxs-lookup"><span data-stu-id="c627e-126">*macOS only*</span></span>

<span data-ttu-id="c627e-127">Начиная с заверенного пакета SDK для .NET Core 3.1 для macOS параметр appHost отключен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c627e-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="c627e-128">Дополнительные сведения см. в статье [Заверение macOS Catalina и влияние на скачиваемые файлы и проекты .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c627e-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="c627e-129">Если параметр appHost включен, .NET Core создает собственный исполняемый файл Mach-O, когда вы выполняете сборку или публикацию.</span><span class="sxs-lookup"><span data-stu-id="c627e-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="c627e-130">Приложение выполняется в контексте appHost при запуске из исходного кода с помощью команды `dotnet run` или путем непосредственного запуска исполняемого файла Mach-O.</span><span class="sxs-lookup"><span data-stu-id="c627e-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="c627e-131">Без appHost пользователь может запустить приложение, [зависящее от платформы](../deploying/index.md#publish-framework-dependent), только одним способом — с помощью команды `dotnet <filename.dll>`.</span><span class="sxs-lookup"><span data-stu-id="c627e-131">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="c627e-132">AppHost всегда создается при публикации приложения в [автономном виде](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="c627e-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="c627e-133">Можно либо настроить appHost на уровне проекта, либо переключить использование appHost для определенной команды `dotnet` с помощью параметра `-p:UseAppHost`:</span><span class="sxs-lookup"><span data-stu-id="c627e-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="c627e-134">Файл проекта</span><span class="sxs-lookup"><span data-stu-id="c627e-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="c627e-135">Параметр командной строки</span><span class="sxs-lookup"><span data-stu-id="c627e-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="c627e-136">Дополнительные сведения о параметре `UseAppHost` см. в разделе [Свойства MSBuild для Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="c627e-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="c627e-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c627e-137">Windows Forms</span></span>

<span data-ttu-id="c627e-138">*Только для Windows*</span><span class="sxs-lookup"><span data-stu-id="c627e-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="c627e-139">В Windows Forms внесены критические изменения.</span><span class="sxs-lookup"><span data-stu-id="c627e-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="c627e-140">В Windows Forms входили устаревшие элементы управления, которые уже некоторое время недоступны на панели элементов конструктора Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c627e-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="c627e-141">Они были заменены новыми элементами управления еще в .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c627e-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="c627e-142">Эти элементы управления удалены из пакета SDK для рабочего стола для .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c627e-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="c627e-143">Удаленный элемент управления</span><span class="sxs-lookup"><span data-stu-id="c627e-143">Removed control</span></span> | <span data-ttu-id="c627e-144">Рекомендуемая замена</span><span class="sxs-lookup"><span data-stu-id="c627e-144">Recommended replacement</span></span> | <span data-ttu-id="c627e-145">Соответствующие удаленные интерфейсы API</span><span class="sxs-lookup"><span data-stu-id="c627e-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="c627e-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="c627e-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="c627e-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="c627e-147">DataGridCell</span></span><br/><span data-ttu-id="c627e-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="c627e-148">DataGridRow</span></span><br/><span data-ttu-id="c627e-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="c627e-149">DataGridTableCollection</span></span><br/><span data-ttu-id="c627e-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="c627e-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="c627e-151">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="c627e-151">DataGridTableStyle</span></span><br/><span data-ttu-id="c627e-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="c627e-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="c627e-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="c627e-153">DataGridLineStyle</span></span><br/><span data-ttu-id="c627e-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="c627e-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="c627e-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="c627e-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="c627e-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="c627e-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="c627e-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="c627e-157">DataGridTextBox</span></span><br/><span data-ttu-id="c627e-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="c627e-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="c627e-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="c627e-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="c627e-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="c627e-160">HitTestType</span></span> |
| <span data-ttu-id="c627e-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="c627e-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="c627e-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="c627e-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="c627e-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="c627e-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="c627e-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="c627e-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="c627e-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="c627e-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="c627e-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="c627e-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="c627e-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="c627e-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="c627e-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c627e-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="c627e-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="c627e-169">MenuItemCollection</span></span> |
| <span data-ttu-id="c627e-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="c627e-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="c627e-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="c627e-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="c627e-172">Мы рекомендуем обновить все приложения до .NET Core 3.1 и перейти к использованию рекомендованных заменяющих элементов управления.</span><span class="sxs-lookup"><span data-stu-id="c627e-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="c627e-173">Замена элементов управления не представляет никаких сложностей. Достаточно найти и заменить все вхождения имени типа.</span><span class="sxs-lookup"><span data-stu-id="c627e-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="c627e-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="c627e-174">C++/CLI</span></span>

<span data-ttu-id="c627e-175">*Только для Windows*</span><span class="sxs-lookup"><span data-stu-id="c627e-175">*Windows only*</span></span>

<span data-ttu-id="c627e-176">Добавлена поддержка создания проектов C++/CLI ("управляемый C++").</span><span class="sxs-lookup"><span data-stu-id="c627e-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="c627e-177">Двоичные файлы из этих проектов совместимы с .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="c627e-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="c627e-178">Чтобы добавить поддержку C++/CLI в Visual Studio 2019 версии 16.4, установите рабочую нагрузку [Разработка классических приложений на C++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="c627e-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="c627e-179">При использовании этой рабочей нагрузки в Visual Studio добавляется два шаблона:</span><span class="sxs-lookup"><span data-stu-id="c627e-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="c627e-180">библиотека классов CLR (.NET Core);</span><span class="sxs-lookup"><span data-stu-id="c627e-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="c627e-181">пустой проект CLR (.NET Framework).</span><span class="sxs-lookup"><span data-stu-id="c627e-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="c627e-182">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="c627e-182">Next steps</span></span>

- [<span data-ttu-id="c627e-183">Изучите критические изменения при обновлении с .NET Core 3.0 и до NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c627e-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.1.md)
- [<span data-ttu-id="c627e-184">Изучите критические изменения в NET Core 3.1 для приложений Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c627e-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
