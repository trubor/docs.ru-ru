---
title: Среда разработки приложений Docker
description: Ознакомьтесь с наиболее важными средствами разработки, поддерживающими жизненный цикл разработки Docker.
ms.date: 01/06/2021
ms.openlocfilehash: c6c4a1fda41131c00ba87808ed408f1d3250cabf
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970529"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="fdbb8-103">Среда разработки приложений Docker</span><span class="sxs-lookup"><span data-stu-id="fdbb8-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="fdbb8-104">Выбор средств разработки: интегрированная среда разработки или редактор</span><span class="sxs-lookup"><span data-stu-id="fdbb8-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="fdbb8-105">Предпочитаете ли вы использовать полнофункциональную среду IDE или упрощенный редактор, корпорация Майкрософт предлагает вам удобное решение для разработки приложений Docker.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="fdbb8-106">Visual Studio Code и CLI Docker (кроссплатформенные средства для Mac, Linux и Windows)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="fdbb8-107">Если вам нужен упрощенный кроссплатформенный редактор, поддерживающий любой язык программирования, вы можете использовать Visual Studio Code и CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="fdbb8-108">Эти решения обеспечивают простой, но в то же время эффективный рабочий процесс разработки.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="fdbb8-109">Установив Docker для Mac или Docker для Windows (среду разработки), разработчики приложений Docker могут использовать единый интерфейс CLI Docker (среду выполнения), чтобы создавать приложения как для Windows, так и для Linux.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="fdbb8-110">Кроме того, Visual Studio Code поддерживает расширения для Docker с IntelliSense для файлов Dockerfile и ярлыками для выполнения команд Docker из редактора.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="fdbb8-111">Чтобы скачать Visual Studio Code, перейдите на страницу <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="fdbb8-112">Чтобы скачать Docker для Mac и Windows, перейдите на страницу <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="fdbb8-113">Visual Studio со средствами Docker (компьютер Windows для разработки)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="fdbb8-114">Рекомендуется использовать Visual Studio 2019 с включенными встроенными средствами Docker.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-114">It's recommend that you use Visual Studio 2019 with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="fdbb8-115">С помощью Visual Studio вы можете разрабатывать, запускать и проверять приложения непосредственно в выбранной среде Docker.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="fdbb8-116">Нажмите клавишу F5 для отладки приложения (на основе одного контейнера или нескольких) непосредственно в узле Docker или клавиши CTRL+F5 для редактирования и обновления приложения без повторной сборки контейнера.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="fdbb8-117">Это самый простой и эффективный способ разработки в Windows контейнеров Docker для Linux или Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="fdbb8-118">Visual Studio для Mac (компьютер Mac для разработки)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="fdbb8-119">При разработке приложений на основе Docker можно использовать [Visual Studio для Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="fdbb8-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="fdbb8-120">Visual Studio для Mac — это интегрированная среда разработки с более широкими возможностями по сравнению с Visual Studio Code для Mac.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="fdbb8-121">Языки и платформы</span><span class="sxs-lookup"><span data-stu-id="fdbb8-121">Language and framework choices</span></span>

<span data-ttu-id="fdbb8-122">С помощью средств Майкрософт вы можете разрабатывать приложения Docker на самых современных языках.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="fdbb8-123">Вот лишь часть их списка:</span><span class="sxs-lookup"><span data-stu-id="fdbb8-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="fdbb8-124">.NET и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fdbb8-124">.NET and ASP.NET Core</span></span>
- <span data-ttu-id="fdbb8-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="fdbb8-125">Node.js</span></span>
- <span data-ttu-id="fdbb8-126">Go</span><span class="sxs-lookup"><span data-stu-id="fdbb8-126">Go</span></span>
- <span data-ttu-id="fdbb8-127">Java</span><span class="sxs-lookup"><span data-stu-id="fdbb8-127">Java</span></span>
- <span data-ttu-id="fdbb8-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="fdbb8-128">Ruby</span></span>
- <span data-ttu-id="fdbb8-129">Python</span><span class="sxs-lookup"><span data-stu-id="fdbb8-129">Python</span></span>

<span data-ttu-id="fdbb8-130">По сути, можно использовать любой современный язык, поддерживаемый Docker в Linux или Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbb8-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fdbb8-131">[Назад](deploy-azure-kubernetes-service.md)
>[Вперед](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fdbb8-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
