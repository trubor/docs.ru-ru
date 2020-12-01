---
title: Работа со сборками и глобальным кэшем сборок
description: Работа со сборками и глобальным кэшем сборок в .NET. Узнайте, в каких случаях может потребоваться установка сборки в глобальный кэш сборок.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: e27fdd7def2d234e1e8eb7557e869bf478d68210
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279315"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="d4e07-104">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-104">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="d4e07-105">Если необходимо обеспечить возможность совместного использования сборки в нескольких приложениях, то ее можно поместить в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-105">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="d4e07-106">Этот кэш кода уровня компьютера присутствует на любом компьютере, где установлена среда CLR.</span><span class="sxs-lookup"><span data-stu-id="d4e07-106">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="d4e07-107">В глобальном кэше сборок сохраняются сборки, специально предназначенные для совместного использования на компьютере несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="d4e07-107">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="d4e07-108">Для установки в глобальном кэше сборка должна иметь строгое имя.</span><span class="sxs-lookup"><span data-stu-id="d4e07-108">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4e07-109">Имя сборки, установленной в глобальном кэше сборок, должно совпадать с именем файла (без учета расширения имени файла).</span><span class="sxs-lookup"><span data-stu-id="d4e07-109">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="d4e07-110">К примеру, файл сборки с именем myAssembly должен иметь имя myAssembly.exe или myAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="d4e07-110">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="d4e07-111">Прибегать к совместному использованию сборок путем их установки в глобальном кэше сборок следует только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="d4e07-111">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="d4e07-112">Как правило, зависимости между сборками следует сохранять закрытыми, а сами сборки нужно размещать в папке приложения, если они не предназначены для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="d4e07-112">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="d4e07-113">Кроме того, установка сборок в глобальном кэше сборок для обеспечения доступа к ним с помощью COM-взаимодействия или из неуправляемого кода не является обязательной.</span><span class="sxs-lookup"><span data-stu-id="d4e07-113">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="d4e07-114">Существует несколько причин для установки сборки в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-114">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="d4e07-115">Общее расположение.</span><span class="sxs-lookup"><span data-stu-id="d4e07-115">Shared location.</span></span>  
  
     <span data-ttu-id="d4e07-116">Используемые несколькими приложениями сборки можно располагать в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-116">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="d4e07-117">Например, если все приложения используют сборку, расположенную в глобальном кэше сборок, то в файл Machine.config можно добавить оператор политики выбора версий, который перенаправляет ссылки на эту сборку.</span><span class="sxs-lookup"><span data-stu-id="d4e07-117">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="d4e07-118">Безопасность файлов.</span><span class="sxs-lookup"><span data-stu-id="d4e07-118">File security.</span></span>  
  
     <span data-ttu-id="d4e07-119">Администраторы часто защищают папку systemroot с помощью списка управления доступом, определяющего права на запись и выполнение.</span><span class="sxs-lookup"><span data-stu-id="d4e07-119">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="d4e07-120">Так как глобальный кэш сборок размещается в корневом каталоге системы, он наследует список управления доступом этого каталога.</span><span class="sxs-lookup"><span data-stu-id="d4e07-120">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="d4e07-121">Рекомендуется разрешать удаление файлов из глобального кэша сборок только пользователям, имеющим права доступа администратора.</span><span class="sxs-lookup"><span data-stu-id="d4e07-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="d4e07-122">Управление параллельными версиями.</span><span class="sxs-lookup"><span data-stu-id="d4e07-122">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="d4e07-123">В глобальном кэше сборок может храниться несколько сборок, имеющих одинаковые имена, но различные сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="d4e07-123">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="d4e07-124">Дополнительное место для поиска.</span><span class="sxs-lookup"><span data-stu-id="d4e07-124">Additional search location.</span></span>  
  
     <span data-ttu-id="d4e07-125">Перед проверкой или использованием сведений о базе кода в файле конфигурации среда CLR ищет в глобальном кэше сборки, соответствующие запросу.</span><span class="sxs-lookup"><span data-stu-id="d4e07-125">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="d4e07-126">Обратите внимание, что существуют сценарии, в которых установка сборки в глобальный кэш сборок явно не требуется.</span><span class="sxs-lookup"><span data-stu-id="d4e07-126">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="d4e07-127">Если одна из составляющих приложение сборок помещается в глобальный кэш сборок, то после этого нельзя будет скопировать или установить приложение с помощью команды XCOPY путем копирования каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="d4e07-127">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="d4e07-128">В этом случае также требуется переместить сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-128">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4e07-129">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d4e07-129">In This Section</span></span>  

[<span data-ttu-id="d4e07-130">Практическое руководство. Установка сборки в глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-130">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="d4e07-131">Описание способов установки сборки в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-131">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="d4e07-132">Практическое руководство. Просмотр содержимого глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-132">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="d4e07-133">Описание того, как использовать [средство глобального кэша сборок (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) для просмотра содержимого глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="d4e07-134">Практическое руководство. Удаление сборки из глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-134">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="d4e07-135">Описание того, как использовать [средство глобального кэша сборок (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) для удаления сборки из глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-135">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="d4e07-136">Использование обслуживаемых компонентов с глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-136">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="d4e07-137">Содержит сведения о том, почему обслуживаемые компоненты (управляемые компоненты COM+) следует помещать в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-137">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4e07-138">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="d4e07-138">Related Sections</span></span>  

[<span data-ttu-id="d4e07-139">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-139">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="d4e07-140">Содержит общие сведения о создании сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-140">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="d4e07-141">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-141">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="d4e07-142">Содержит общие сведения о глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="d4e07-142">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="d4e07-143">Практическое руководство. Просмотр содержимого сборки</span><span class="sxs-lookup"><span data-stu-id="d4e07-143">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="d4e07-144">Описание того, как использовать [программу Ildasm.exe (дизассемблер IL)](../tools/ildasm-exe-il-disassembler.md) для просмотра данных MSIL в сборке.</span><span class="sxs-lookup"><span data-stu-id="d4e07-144">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="d4e07-145">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="d4e07-145">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="d4e07-146">Описание того, как среда CLR находит и загружает сборки, составляющие приложение.</span><span class="sxs-lookup"><span data-stu-id="d4e07-146">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="d4e07-147">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="d4e07-147">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d4e07-148">Описывает сборки, "кирпичики", с помощью которых создаются управляемые приложения.</span><span class="sxs-lookup"><span data-stu-id="d4e07-148">Describes assemblies, the building blocks of managed applications.</span></span>
