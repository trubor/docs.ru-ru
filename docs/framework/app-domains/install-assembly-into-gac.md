---
title: Практическое руководство. установку сборки в глобальный кэш сборок
description: Установка сборки в глобальный кэш сборок в .NET для ее совместного использования несколькими приложениями. Использование установщика Windows или средства глобального кэша сборок.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 0034c6d7a7184e8fc3a6384c829f6bf13aad6cdd
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653469"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="ee711-104">Практическое руководство. установку сборки в глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="ee711-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="ee711-105">В глобальном кэше сборок сохраняются сборки, которые могут использоваться несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="ee711-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="ee711-106">Установите сборку в [глобальный кэш сборок](gac.md) с одним из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="ee711-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="ee711-107">Установщик Windows</span><span class="sxs-lookup"><span data-stu-id="ee711-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="ee711-108">Средство глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="ee711-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="ee711-109">В глобальный кэш сборок можно установить только сборки со строгими именами.</span><span class="sxs-lookup"><span data-stu-id="ee711-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="ee711-110">Дополнительные сведения о создании сборки со строгим именем см. в разделе [Практическое руководство. Подписание сборки со строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="ee711-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="ee711-111">Установщик Windows</span><span class="sxs-lookup"><span data-stu-id="ee711-111">Windows Installer</span></span>

<span data-ttu-id="ee711-112">[Установщик Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache) — средство установки Windows, которое рекомендуется использовать для добавления сборок в GAC.</span><span class="sxs-lookup"><span data-stu-id="ee711-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="ee711-113">Установщик Windows предоставляет возможность подсчета ссылок на сборки в GAC и другие дополнительные возможности.</span><span class="sxs-lookup"><span data-stu-id="ee711-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="ee711-114">Создать пакет установщика для установщика Windows можно с помощью [расширения Wix Toolset для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="ee711-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="ee711-115">Средство глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="ee711-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="ee711-116">[Служебную программу глобального кэша сборок .NET (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) можно использовать для добавления сборок в глобальный кэш сборок и для просмотра содержимого указанного кэша.</span><span class="sxs-lookup"><span data-stu-id="ee711-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ee711-117">*Gacutil.exe* предназначен только для разработки.</span><span class="sxs-lookup"><span data-stu-id="ee711-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="ee711-118">Не используйте его для установки рабочих сборок в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="ee711-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="ee711-119">Синтаксис для использования *gacutil.exe* для установки сборки в глобальном кэше сборок выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ee711-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="ee711-120">В этой команде *\<assembly name>* представляет собой имя сборки, устанавливаемой в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="ee711-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="ee711-121">Если *gacutil.exe* не находится в системном пути, используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="ee711-121">If *gacutil.exe* isn't in your system path, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="ee711-122">В следующем примере выполняется установка сборки с именем файла *hello.dll* в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="ee711-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="ee711-123">В предыдущих версиях .NET Framework расширение оболочки Windows *Shfusion.dll* позволяло устанавливать сборки, перетаскивая их в проводнике.</span><span class="sxs-lookup"><span data-stu-id="ee711-123">In earlier versions of .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="ee711-124">Начиная с версии .NET Framework 4 расширение оболочки *Shfusion.dll* является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="ee711-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee711-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ee711-125">See also</span></span>

- [<span data-ttu-id="ee711-126">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="ee711-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="ee711-127">Практическое руководство. Удаление сборки из глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="ee711-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="ee711-128">Gacutil.exe (программа глобального кэша сборок)</span><span class="sxs-lookup"><span data-stu-id="ee711-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="ee711-129">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="ee711-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
