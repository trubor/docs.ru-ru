---
title: Организация проектов для .NET Framework и .NET Core
description: Эта статья поможет владельцам проектов, которые хотят скомпилировать свое решение одновременно для .NET Framework и .NET Core.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: 0d495ce7b21b45d3fabe444f117667e5908ac81a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873670"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="9d9ff-103">Организация проекта для параллельной поддержки .NET Framework и .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d9ff-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="9d9ff-104">Вы можете создать решение, которое выполняет параллельную сборку для .NET Framework и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="9d9ff-105">В этой статье рассматриваются несколько вариантов организации проекта, которые помогут вам достичь этой цели.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="9d9ff-106">Ниже приведено несколько типичных сценариев, которые следует принять во внимание при выборе способа компоновки проекта с помощью .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="9d9ff-107">Этот список может охватывать не все необходимые случаи. Устанавливайте приоритеты в зависимости от потребностей вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="9d9ff-108">**Объединение существующих проектов и проектов .NET Core в единые проекты**</span><span class="sxs-lookup"><span data-stu-id="9d9ff-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="9d9ff-109">*Преимущества*</span><span class="sxs-lookup"><span data-stu-id="9d9ff-109">*What this is good for:*</span></span>
  - <span data-ttu-id="9d9ff-110">Упрощает процесс сборки благодаря компиляции одного, а не нескольких проектов, каждый из которых предназначен для отдельной версии .NET Framework или платформы.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="9d9ff-111">Упрощает управление файлами исходного кода для проектов, предназначенных для различных платформ, благодаря тому, что вам приходится управлять только одним файлом проекта.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="9d9ff-112">При использовании альтернативных подходов добавление или удаление файлов исходного кода требует синхронизации этих изменений с другими проектами вручную.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="9d9ff-113">Простое создание пакета NuGet для использования.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="9d9ff-114">Позволяет писать код для конкретной версии .NET Framework в библиотеках посредством директив компилятора.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="9d9ff-115">*Неподдерживаемые сценарии*</span><span class="sxs-lookup"><span data-stu-id="9d9ff-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="9d9ff-116">Для открытия существующих проектов разработчики должны использовать Visual Studio 2017 или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="9d9ff-117">Для поддержки предыдущих версий Visual Studio лучше [хранить файлы проектов в разных папках](#support-vs).</span><span class="sxs-lookup"><span data-stu-id="9d9ff-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="9d9ff-118">[**Разделение существующих и новых проектов .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="9d9ff-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="9d9ff-119">*Преимущества*</span><span class="sxs-lookup"><span data-stu-id="9d9ff-119">*What this is good for:*</span></span>
  - <span data-ttu-id="9d9ff-120">Поддерживает разработки в существующих проектах для разработчиков и участников, которые могут не иметь Visual Studio 2017 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="9d9ff-121">Снижает вероятности появления новых ошибок в существующих проектах, так как не требуется обработка кода.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="9d9ff-122">Пример</span><span class="sxs-lookup"><span data-stu-id="9d9ff-122">Example</span></span>

<span data-ttu-id="9d9ff-123">Рассмотрим показанный ниже репозиторий.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-123">Consider the repository below:</span></span>

![Существующий проект](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="9d9ff-125">**Исходный код**</span><span class="sxs-lookup"><span data-stu-id="9d9ff-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library/)

<span data-ttu-id="9d9ff-126">В зависимости от ограничений и сложности существующих проектов добавить поддержку .NET Core для этого репозитория можно несколькими способами, которые описаны ниже.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="9d9ff-127">Замена существующих проектов на проект .NET Core, предназначенный для нескольких платформ</span><span class="sxs-lookup"><span data-stu-id="9d9ff-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="9d9ff-128">Измените файлы в репозитории, удалив все существующие файлы *\*.csproj* и создав единственный файл *\*.csproj*, предназначенный для нескольких платформ.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="9d9ff-129">Это удобно по той причине, что один проект можно компилировать для разных платформ.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="9d9ff-130">Это также позволяет управлять различными параметрами компиляции и зависимостями для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Создание файла CSPROJ, предназначенного для нескольких платформ](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="9d9ff-132">**Исходный код**</span><span class="sxs-lookup"><span data-stu-id="9d9ff-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="9d9ff-133">Обратите внимание на следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="9d9ff-133">Changes to note are:</span></span>

- <span data-ttu-id="9d9ff-134">Замена файлов *packages.config* и *\*.csproj* на новый файл [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="9d9ff-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="9d9ff-135">Пакеты NuGet указываются с помощью `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="9d9ff-136">Сохранение существующих проектов и создание проекта .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d9ff-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="9d9ff-137">При наличии существующих проектов, предназначенных для более старых платформ, можно оставить эти проекты без изменения и использовать проект .NET Core для новых платформ.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Проект .NET Core с существующим проектом в другой папке](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="9d9ff-139">**Исходный код**</span><span class="sxs-lookup"><span data-stu-id="9d9ff-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="9d9ff-140">Проект .NET Core и существующие проекты хранятся в разных папках.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="9d9ff-141">Размещение проектов в разных папках позволяет обойтись без Visual Studio 2017 или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="9d9ff-142">Вы можете создать отдельное решение, которое открывает только старые проекты.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d9ff-143">См. также</span><span class="sxs-lookup"><span data-stu-id="9d9ff-143">See also</span></span>

- [<span data-ttu-id="9d9ff-144">Документация по переносу .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d9ff-144">.NET Core porting documentation</span></span>](index.md)
