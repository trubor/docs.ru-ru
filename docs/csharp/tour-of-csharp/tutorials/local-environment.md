---
title: Знакомство со средствами разработки. Вводное руководство по C#
description: Эта статья содержит базовое описание средств разработки, которые вы будете использовать для создания приложений C# и .NET на локальном компьютере.
ms.date: 02/02/2021
ms.openlocfilehash: 72116154126b0a97fffe417b2807576b1d9689df
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626663"
---
# <a name="set-up-your-local-environment"></a><span data-ttu-id="c67fc-103">Настройка локальной среды</span><span class="sxs-lookup"><span data-stu-id="c67fc-103">Set up your local environment</span></span>

<span data-ttu-id="c67fc-104">Для выполнения этого руководства прежде всего нужно настроить на компьютере среду разработки.</span><span class="sxs-lookup"><span data-stu-id="c67fc-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span> <span data-ttu-id="c67fc-105">Выберите один из следующих вариантов:</span><span class="sxs-lookup"><span data-stu-id="c67fc-105">Choose one of the following alternatives:</span></span>

* <span data-ttu-id="c67fc-106">Сведения об использовании .NET CLI и любого текстового редактора или редактора кода см. в статье [Руководство по .NET — Hello World за 10 минут](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span><span class="sxs-lookup"><span data-stu-id="c67fc-106">To use the .NET CLI and your choice of text or code editor, see the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span> <span data-ttu-id="c67fc-107">В этом руководстве содержатся инструкции по настройке локальной среды разработки в macOS, Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="c67fc-107">The tutorial has instructions for setting up a development environment on Windows, Linux, or macOS.</span></span>
* <span data-ttu-id="c67fc-108">Чтобы использовать .NET CLI и Visual Studio Code, установите пакет [SDK для .NET](https://dotnet.microsoft.com/download) и [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c67fc-108">To use the .NET CLI and Visual Studio Code, install the [.NET SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>
* <span data-ttu-id="c67fc-109">Сведения об использовании Visual Studio 2019, см. в статье [Руководство. Создание простого консольного приложения C# в Visual Studio](/visualstudio/get-started/csharp/tutorial-console).</span><span class="sxs-lookup"><span data-stu-id="c67fc-109">To use Visual Studio 2019, see [Tutorial: Create a simple C# console app in Visual Studio](/visualstudio/get-started/csharp/tutorial-console).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="c67fc-110">Базовый поток разработки приложения</span><span class="sxs-lookup"><span data-stu-id="c67fc-110">Basic application development flow</span></span>

<span data-ttu-id="c67fc-111">В инструкциях, приведенных в этих руководствах, предполагается, что вы используете .NET CLI для создания, сборки и запуска приложений.</span><span class="sxs-lookup"><span data-stu-id="c67fc-111">The instructions in these tutorials assume that you're using the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="c67fc-112">Вы будете использовать следующие команды:</span><span class="sxs-lookup"><span data-stu-id="c67fc-112">You'll use the following commands:</span></span>

* <span data-ttu-id="c67fc-113">[`dotnet new`](../../../core/tools/dotnet-new.md) создает приложение.</span><span class="sxs-lookup"><span data-stu-id="c67fc-113">[`dotnet new`](../../../core/tools/dotnet-new.md) creates an application.</span></span> <span data-ttu-id="c67fc-114">Эта команда создает файлы и ресурсы, необходимые для приложения.</span><span class="sxs-lookup"><span data-stu-id="c67fc-114">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="c67fc-115">Во всех ознакомительных руководствах по C# используется тип приложения `console`.</span><span class="sxs-lookup"><span data-stu-id="c67fc-115">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="c67fc-116">Освоив описанные здесь основы, вы сможете перейти и к другим типам приложений.</span><span class="sxs-lookup"><span data-stu-id="c67fc-116">Once you've got the basics, you can expand to other application types.</span></span>
* <span data-ttu-id="c67fc-117">[`dotnet build`](../../../core/tools/dotnet-build.md) выполняет сборку исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="c67fc-117">[`dotnet build`](../../../core/tools/dotnet-build.md) builds the executable.</span></span>
* <span data-ttu-id="c67fc-118">[`dotnet run`](../../../core/tools/dotnet-run.md) запускает исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="c67fc-118">[`dotnet run`](../../../core/tools/dotnet-run.md) runs the executable.</span></span>

<span data-ttu-id="c67fc-119">Если вы используете Visual Studio 2019 для работы с этими руководствами, выберите вариант с меню Visual Studio, когда в руководстве будет предложено выполнить одну из следующих команд CLI:</span><span class="sxs-lookup"><span data-stu-id="c67fc-119">If you use Visual Studio 2019 for these tutorials, you'll choose a Visual Studio menu selection when a tutorial directs you to run one of these CLI commands:</span></span>

* <span data-ttu-id="c67fc-120">**Файл** > **Создать** > **Проект** — создание приложения;</span><span class="sxs-lookup"><span data-stu-id="c67fc-120">**File** > **New** > **Project** creates an application.</span></span>
* <span data-ttu-id="c67fc-121">**Сборка** >  **Собрать решение** — сборка исполняемого файла;</span><span class="sxs-lookup"><span data-stu-id="c67fc-121">**Build** >  **Build Solution** builds the executable.</span></span>
* <span data-ttu-id="c67fc-122">**Отладка** > **Запуск без отладки** — запуск исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="c67fc-122">**Debug** > **Start Without Debugging** runs the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="c67fc-123">Выбор руководства</span><span class="sxs-lookup"><span data-stu-id="c67fc-123">Pick your tutorial</span></span>

<span data-ttu-id="c67fc-124">Вы можете начать изучение с любого из следующих руководств:</span><span class="sxs-lookup"><span data-stu-id="c67fc-124">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-c"></a><span data-ttu-id="c67fc-125">Числа в C\#</span><span class="sxs-lookup"><span data-stu-id="c67fc-125">Numbers in C\#</span></span>

<span data-ttu-id="c67fc-126">Из руководства [Числа в C#](numbers-in-csharp-local.md) вы узнаете, как на компьютере хранятся числа и как выполнять вычисления с разными числовыми типами.</span><span class="sxs-lookup"><span data-stu-id="c67fc-126">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="c67fc-127">Вы ознакомитесь с основами округления и научитесь выполнять математические вычисления с помощью C#.</span><span class="sxs-lookup"><span data-stu-id="c67fc-127">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="c67fc-128">В этом руководстве предполагается, что вы уже прошли занятие [Hello World](hello-world.yml).</span><span class="sxs-lookup"><span data-stu-id="c67fc-128">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loops"></a><span data-ttu-id="c67fc-129">Ветви и циклы</span><span class="sxs-lookup"><span data-stu-id="c67fc-129">Branches and loops</span></span>

<span data-ttu-id="c67fc-130">В руководстве [Ветви и циклы](branches-and-loops-local.md) представлены общие принципы организации ветвления кода в зависимости от значений, хранящихся в переменных.</span><span class="sxs-lookup"><span data-stu-id="c67fc-130">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="c67fc-131">Вы узнаете, что такое поток управления, являющийся основой принятия решений и выбора различных действий в программах.</span><span class="sxs-lookup"><span data-stu-id="c67fc-131">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="c67fc-132">В этом руководстве предполагается, что вы уже прошли занятия [Hello World](hello-world.yml) и [Числа в C#](numbers-in-csharp-local.md).</span><span class="sxs-lookup"><span data-stu-id="c67fc-132">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collection"></a><span data-ttu-id="c67fc-133">Коллекция списков</span><span class="sxs-lookup"><span data-stu-id="c67fc-133">List collection</span></span>

<span data-ttu-id="c67fc-134">Занятие [Коллекция списков](arrays-and-collections.md) содержит обзор типа "Коллекция списков", в котором хранятся последовательности данных.</span><span class="sxs-lookup"><span data-stu-id="c67fc-134">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="c67fc-135">Вы узнаете, как добавлять и удалять элементы, выполнять их поиск и сортировать списки.</span><span class="sxs-lookup"><span data-stu-id="c67fc-135">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="c67fc-136">Вы ознакомитесь с различными типами списков.</span><span class="sxs-lookup"><span data-stu-id="c67fc-136">You'll explore different kinds of lists.</span></span>

<span data-ttu-id="c67fc-137">В этом руководстве предполагается, что вы уже прошли перечисленные выше занятия.</span><span class="sxs-lookup"><span data-stu-id="c67fc-137">This tutorial assumes that you have finished the lessons listed above.</span></span>
