---
title: Глобальный кэш сборок
description: Сведения о глобальном кэше сборок, который представляет собой кэш кода на уровне компьютера с установленной средой CLR для .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 57d18c01bd6261e8207d8ad3849a3a7da9a24b6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264612"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="c2aa8-103">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="c2aa8-103">Global Assembly Cache</span></span>

<span data-ttu-id="c2aa8-104">На каждом компьютере с установленной средой CLR имеется кэш кода на уровне компьютера, называемый глобальным кэшем сборок.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="c2aa8-105">В глобальном кэше сборок сохраняются сборки, специально предназначенные для совместного использования на компьютере несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="c2aa8-106">Организовывать совместное использование сборок путем установки их в глобальный кэш следует только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="c2aa8-107">Как правило, зависимости между сборками следует сохранять закрытыми, а сами сборки нужно размещать в папке приложения, если они не предназначены для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="c2aa8-108">Кроме того, не обязательно устанавливать сборки в глобальный кэш сборок для доступа к ним из COM-взаимодействия или из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2aa8-109">Существуют случаи, в которых явно не требуется установка сборки в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="c2aa8-110">Если одна из составляющих приложения сборок помещается в глобальный кэш сборок, то после этого вы не сможете скопировать или установить приложение с помощью команды **xcopy** путем копирования каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="c2aa8-111">Для этого также потребуется переместить сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="c2aa8-112">Существует два способа развертывания сборки в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="c2aa8-113">Использование программы установки, предназначенной для работы с глобальным кэшем сборок.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="c2aa8-114">Данный подход является предпочтительным при установке сборок в глобальный кэш.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="c2aa8-115">Используйте инструмент разработчика под названием [средство глобального кэша сборок (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) из Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2aa8-116">В сценариях развертывания для установки сборок в глобальный кэш используйте установщик Windows.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="c2aa8-117">Средство глобального кэша сборок используйте только при разработке, поскольку оно не обеспечивает подсчет ссылок на сборку и другие возможности, предоставляемые при использовании установщика Windows.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="c2aa8-118">Начиная с .NET Framework 4 расположение глобального кэша сборок по умолчанию — **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="c2aa8-119">В более ранних версиях платформы .NET Framework расположение по умолчанию — **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="c2aa8-120">Администраторы часто защищают папку systemroot с помощью списка управления доступом, определяющего права на запись и выполнение.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="c2aa8-121">Так как глобальный кэш сборок устанавливается в подкаталоге каталога SystemRoot, он наследует этот список управления доступом.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="c2aa8-122">Рекомендуется разрешать удаление файлов из глобального кэша сборок только пользователям, имеющим права доступа администратора.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="c2aa8-123">Сборки, развернутые в глобальном кэше сборок, должны иметь строгие имена.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="c2aa8-124">При добавлении сборки в глобальный кэш сборок выполняется проверка целостности всех входящих в нее файлов.</span><span class="sxs-lookup"><span data-stu-id="c2aa8-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="c2aa8-125">Кэш выполняет такую проверку целостности, чтобы гарантировать, что сборка не была изменена (например, если файл был изменен, но изменения не были отражены в манифесте сборки).</span><span class="sxs-lookup"><span data-stu-id="c2aa8-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2aa8-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c2aa8-126">See also</span></span>

- [<span data-ttu-id="c2aa8-127">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="c2aa8-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="c2aa8-128">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="c2aa8-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="c2aa8-129">Сборки со строгими именами</span><span class="sxs-lookup"><span data-stu-id="c2aa8-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
