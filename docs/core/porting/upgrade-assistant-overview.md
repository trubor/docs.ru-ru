---
title: Обзор помощника по обновлению .NET
description: Знакомство со средством "помощник по обновлению .NET", которое помогает переходить с платформы .NET Framework и обновляет проекты до .NET 5.
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: c667cfce40d4f740bc23606826eb2a058643b7be
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604779"
---
# <a name="overview-of-the-net-upgrade-assistant"></a><span data-ttu-id="53d76-103">Обзор помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-103">Overview of the .NET Upgrade Assistant</span></span>

<span data-ttu-id="53d76-104">Возможно, у вас есть приложения, которые сейчас выполняются в .NET Framework, и вы хотите перенести их в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="53d76-104">You might have apps that currently run on the .NET Framework that you're interested in porting to .NET 5.</span></span> <span data-ttu-id="53d76-105">Средство "помощник по обновлению .NET" может помочь в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="53d76-105">The .NET Upgrade Assistant tool can assist with this process.</span></span> <span data-ttu-id="53d76-106">В этой статье приводится следующее:</span><span class="sxs-lookup"><span data-stu-id="53d76-106">This article provides:</span></span>

- <span data-ttu-id="53d76-107">Обзор помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="53d76-107">An overview of the .NET Upgrade Assistant.</span></span>
- <span data-ttu-id="53d76-108">Установка помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="53d76-108">How to install the .NET Upgrade Assistant.</span></span>

## <a name="what-is-the-net-upgrade-assistant"></a><span data-ttu-id="53d76-109">Что такое помощник по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-109">What is the .NET Upgrade Assistant</span></span>

<span data-ttu-id="53d76-110">Помощник по обновлению .NET — это средство командной строки, которое можно запускать для различных приложений платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53d76-110">The .NET Upgrade Assistant is a command-line tool that can be run on different kinds of .NET Framework apps.</span></span> <span data-ttu-id="53d76-111">Это средство поможет вам в обновлении приложений .NET Framework до .NET 5.</span><span class="sxs-lookup"><span data-stu-id="53d76-111">It's designed to assist with upgrading .NET Framework apps to .NET 5.</span></span> <span data-ttu-id="53d76-112">После запуска средства **в большинстве случаев для завершения миграции приложения потребуются дополнительные действия**.</span><span class="sxs-lookup"><span data-stu-id="53d76-112">After running the tool, **in most cases the app will require more effort to complete the migration**.</span></span> <span data-ttu-id="53d76-113">Средство включает установку анализаторов, которые могут помочь в завершении миграции.</span><span class="sxs-lookup"><span data-stu-id="53d76-113">The tool includes the installation of analyzers that can assist with completing the migration.</span></span>

<span data-ttu-id="53d76-114">В настоящее время средство поддерживает следующие типы приложений платформы.NET Framework:</span><span class="sxs-lookup"><span data-stu-id="53d76-114">Currently the tool supports the following .NET Framework app types:</span></span>

- <span data-ttu-id="53d76-115">Приложения .NET Framework Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53d76-115">.NET Framework Windows Forms apps</span></span>
- <span data-ttu-id="53d76-116">Приложения .NET Framework WPF</span><span class="sxs-lookup"><span data-stu-id="53d76-116">.NET Framework WPF apps</span></span>
- <span data-ttu-id="53d76-117">Приложения .NET Framework ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="53d76-117">.NET Framework ASP.NET MVC apps</span></span>
- <span data-ttu-id="53d76-118">Консольные приложения .NET Framework</span><span class="sxs-lookup"><span data-stu-id="53d76-118">.NET Framework console apps</span></span>
- <span data-ttu-id="53d76-119">Библиотеки классов .NET Framework</span><span class="sxs-lookup"><span data-stu-id="53d76-119">.NET Framework class libraries</span></span>

<span data-ttu-id="53d76-120">Помощник по обновлению .NET сейчас находится на этапе предварительного выпуска и часто обновляется.</span><span class="sxs-lookup"><span data-stu-id="53d76-120">The .NET Upgrade Assistant is currently prerelease and is receiving frequent updates.</span></span> <span data-ttu-id="53d76-121">Если вы обнаружили проблемы при использовании этого средства, сообщите о них в [репозитории GitHub](https://github.com/dotnet/upgrade-assistant) средства.</span><span class="sxs-lookup"><span data-stu-id="53d76-121">If you discover problems using the tool, please report them in the tool's [GitHub repository](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="how-to-install-the-net-upgrade-assistant"></a><span data-ttu-id="53d76-122">Установка помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-122">How to install the .NET Upgrade Assistant</span></span>

<span data-ttu-id="53d76-123">В [руководстве по началу работы](https://aka.ms/dotnet-upgrade-assistant-install) описывается установка и использование помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="53d76-123">The [Get Started tutorial](https://aka.ms/dotnet-upgrade-assistant-install) walks through how to install and use the .NET Upgrade Assistant.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="53d76-124">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="53d76-124">Prerequisites</span></span>

1. <span data-ttu-id="53d76-125">Это средство использует MSBuild для работы с файлами проектов.</span><span class="sxs-lookup"><span data-stu-id="53d76-125">This tool uses MSBuild to work with project files.</span></span> <span data-ttu-id="53d76-126">Убедитесь, что установлена последняя версия MSBuild.</span><span class="sxs-lookup"><span data-stu-id="53d76-126">Make sure that a recent version of MSBuild is installed.</span></span> <span data-ttu-id="53d76-127">Простой способ сделать это — [установить Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="53d76-127">An easy way to do this is to [install Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span></span>
1. <span data-ttu-id="53d76-128">Это средство зависит от [try-convert](https://github.com/dotnet/try-convert).</span><span class="sxs-lookup"><span data-stu-id="53d76-128">This tool depends on [try-convert](https://github.com/dotnet/try-convert).</span></span> <span data-ttu-id="53d76-129">Чтобы помощник выполнялся правильно, необходимо установить средство try-convert для преобразования файлов проекта в новый стиль SDK.</span><span class="sxs-lookup"><span data-stu-id="53d76-129">In order for the tool to run correctly, you must install the try-convert tool for converting project files to the new SDK style.</span></span> <span data-ttu-id="53d76-130">Если вы уже установили средство **try-convert**, возможно, потребуется обновить его (**upgrade-assistant** зависит от версии _0.7.212201_ или более поздней).</span><span class="sxs-lookup"><span data-stu-id="53d76-130">If you already have **try-convert** installed, you may need to update it instead (since **upgrade-assistant** depends on version _0.7.212201_ or later)</span></span>
    1. <span data-ttu-id="53d76-131">Для установки try-convert: `dotnet tool install -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="53d76-131">To install try-convert: `dotnet tool install -g try-convert`</span></span>
    1. <span data-ttu-id="53d76-132">Для обновления try-convert: `dotnet tool update -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="53d76-132">To update try-convert: `dotnet tool update -g try-convert`</span></span>

### <a name="installation-steps"></a><span data-ttu-id="53d76-133">Шаги установки</span><span class="sxs-lookup"><span data-stu-id="53d76-133">Installation steps</span></span>

<span data-ttu-id="53d76-134">Помощник можно установить в качестве средства .NET CLI, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="53d76-134">The tool can be installed as a .NET CLI tool by running:</span></span>

```dotnet
dotnet tool install -g upgrade-assistant
```

<span data-ttu-id="53d76-135">Аналогично, поскольку помощник по обновлению .NET устанавливается как средство .NET CLI, его можно легко обновить, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="53d76-135">Similarly, because the .NET Upgrade Assistant is installed as a .NET CLI tool, it can be easily updated by running:</span></span>

```dotnet
dotnet tool update -g upgrade-assistant
```

<span data-ttu-id="53d76-136">Подробные инструкции по установке см. в файле [README](https://github.com/dotnet/upgrade-assistant) проекта.</span><span class="sxs-lookup"><span data-stu-id="53d76-136">For detailed installation instructions, please refer to the project's [README](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="see-also"></a><span data-ttu-id="53d76-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="53d76-137">See also</span></span>

- [<span data-ttu-id="53d76-138">Обновление приложения WPF до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-138">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="53d76-139">Обновление приложения Windows Forms до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-139">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="53d76-140">Обновление приложения ASP.NET MVC до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-140">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="53d76-141">Репозиторий GitHub помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="53d76-141">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
