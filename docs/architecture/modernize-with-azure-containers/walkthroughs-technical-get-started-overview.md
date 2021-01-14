---
title: Обзор пошаговых руководств и технических описаний по началу работы
description: Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows | Обзор пошаговых руководств и технических описаний по началу работы
ms.date: 12/21/2020
ms.openlocfilehash: 6bfa25e3eeeecf5a936f378df3ae548d6fa37a30
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025281"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="77676-103">Обзор пошаговых руководств и технических описаний по началу работы</span><span class="sxs-lookup"><span data-stu-id="77676-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="77676-104">Чтобы ограничить размер этой электронной книги, в репозитории GitHub размещена дополнительная техническая документация и полные пошаговые руководства.</span><span class="sxs-lookup"><span data-stu-id="77676-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="77676-105">В интерактивной серии пошаговых руководств, описанных в этой главе, рассматривается пошаговая настройка нескольких сред на основе контейнеров Windows и развертывание в Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="77676-106">В следующих разделах объясняется, что представляет собой каждое пошаговое руководство, его цели и общее описание, а также приводится задействованная схема задач.</span><span class="sxs-lookup"><span data-stu-id="77676-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="77676-107">Вы можете ознакомиться с пошаговыми руководствами в вики-разделе репозитория приложений *eShopModernizing* на сайте GitHub по адресу <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="77676-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="77676-108">Список технических пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="77676-108">Technical walkthrough list</span></span>

<span data-ttu-id="77676-109">Приведенные ниже пошаговые руководства по началу работы предоставляют согласованные и исчерпывающие технические рекомендации по работе с примерами приложений, которые можно переместить с помощью контейнеров, а затем с использованием нескольких вариантов развертывания в Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="77676-110">В каждом из приведенных ниже пошаговых руководств используются новые примеры приложений eShopLegacy и eShopModernizing, которые доступны на сайте GitHub по адресу <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="77676-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="77676-111">**Обзор приложений eShop прежних версий (базовые приложения для модернизации)**</span><span class="sxs-lookup"><span data-stu-id="77676-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="77676-112">**Контейнеризация имеющихся веб-приложений ASP NET (веб-формы и MVC) с помощью контейнеров Windows**</span><span class="sxs-lookup"><span data-stu-id="77676-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="77676-113">**Контейнеризация имеющихся служб WCF (n-уровневых приложений) с помощью контейнеров Windows**</span><span class="sxs-lookup"><span data-stu-id="77676-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="77676-114">**Развертывание приложений на основе контейнеров Windows на виртуальных машинах Azure**</span><span class="sxs-lookup"><span data-stu-id="77676-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="77676-115">**Развертывание приложений на основе контейнеров Windows в Kubernetes в Службе контейнеров Azure**</span><span class="sxs-lookup"><span data-stu-id="77676-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="77676-116">Пошаговое руководство 1. Обзор приложений eShop прежних версий</span><span class="sxs-lookup"><span data-stu-id="77676-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="77676-117">Доступность технического пошагового руководства</span><span class="sxs-lookup"><span data-stu-id="77676-117">Technical walkthrough availability</span></span>

<span data-ttu-id="77676-118">Полное техническое руководство доступно в вики-разделе репозитория eShopModernizing на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="77676-119">Пошаговые руководства в вики-разделе eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="77676-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="77676-120">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-120">Overview</span></span>

<span data-ttu-id="77676-121">В этом пошаговом руководстве приведены сведения о первоначальной реализации трех примеров приложений прежних версий.</span><span class="sxs-lookup"><span data-stu-id="77676-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="77676-122">Первые два примера веб-приложений имеют монолитную архитектуру и созданы с помощью классической платформы ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="77676-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="77676-123">Одно приложение основано на ASP.NET 4.x MVC, а второе — на веб-формах ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="77676-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="77676-124">Третье приложение — это 3-уровневое приложение, состоящее из клиентского приложения WinForms и серверной службы [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="77676-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="77676-125">Все эти приложения доступны в репозитории [eShopModernizing на сайте GitHub](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="77676-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="77676-126">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-126">Goals</span></span>

<span data-ttu-id="77676-127">Основной целью этого пошагового руководства является знакомство с этими приложениями, а также с их кодом и конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="77676-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="77676-128">В целях тестирования можно настроить приложения таким образом, чтобы они создавали и использовали фиктивные данные без применения базы данных SQL.</span><span class="sxs-lookup"><span data-stu-id="77676-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="77676-129">Эта необязательная конфигурация основана на внедрении зависимостей в несвязанном виде.</span><span class="sxs-lookup"><span data-stu-id="77676-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="77676-130">Сценарий 1. Веб-приложения ASP.NET</span><span class="sxs-lookup"><span data-stu-id="77676-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="77676-131">На рисунке ниже показан простой вариант исходных веб-приложений ASP.NET прежних версий.</span><span class="sxs-lookup"><span data-stu-id="77676-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Простой вариант архитектуры исходных веб-приложений ASP.NET прежних версий](./media/image5-1.png)

<span data-ttu-id="77676-133">С точки зрения предметной области бизнеса оба приложения предлагают одни и те же функции управления каталогом.</span><span class="sxs-lookup"><span data-stu-id="77676-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="77676-134">Участники корпоративной команды eShop будут использовать приложение для просмотра и редактирования каталога продуктов.</span><span class="sxs-lookup"><span data-stu-id="77676-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="77676-135">На рисунке ниже показаны снимки экрана первоначального приложения.</span><span class="sxs-lookup"><span data-stu-id="77676-135">The next figure shows the initial app screenshots.</span></span>

![Приложения ASP.NET MVC ASP.NET MVC и веб-форм ASP.NET (имеющиеся и устаревшие технологии)](./media/image5-2.png)

<span data-ttu-id="77676-137">Наличие зависимостей в ASP.NET 4.x или более ранних версиях (для MVC или для веб-форм) означает, что эти приложения не будут работать в .NET Core, если код не будет полностью переписан с использованием MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="77676-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="77676-138">Сценарий 2. Служба WCF и клиентское приложение WinForms (3-уровневое)</span><span class="sxs-lookup"><span data-stu-id="77676-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="77676-139">На рисунке ниже показан простой вариант исходного 3-уровневого приложения прежних версий.</span><span class="sxs-lookup"><span data-stu-id="77676-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Вариант простой архитектуры исходного 3-уровневого приложения прежних версий со службой WCF и клиентским приложением WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="77676-141">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-141">Benefits</span></span>

<span data-ttu-id="77676-142">В этом пошаговом руководстве вы ознакомитесь с кодом и начальными приложениями.</span><span class="sxs-lookup"><span data-stu-id="77676-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-143">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-143">Next steps</span></span>

<span data-ttu-id="77676-144">Подробно изучите это содержимое в вики-разделе на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="77676-145">Обзор базовых приложений ASP.NET MVC и веб-форм прежних версий</span><span class="sxs-lookup"><span data-stu-id="77676-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="77676-146">Обзор базовой службы WCF и приложения WinForms (3-уровневого) прежних версий</span><span class="sxs-lookup"><span data-stu-id="77676-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="77676-147">Пошаговое руководство 2. Контейнеризация имеющихся приложений .NET с помощью контейнеров Windows</span><span class="sxs-lookup"><span data-stu-id="77676-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="77676-148">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-148">Overview</span></span>

<span data-ttu-id="77676-149">Контейнеры Windows можно использовать для улучшения развертывания имеющихся приложений .NET, например, на основе MVC, веб-форм или WCF, в рабочей среде, среде разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="77676-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="77676-150">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-150">Goals</span></span>

<span data-ttu-id="77676-151">Цель этого пошагового руководства — продемонстрировать несколько вариантов контейнеризации имеющегося приложения .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77676-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="77676-152">Можно выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="77676-152">You can:</span></span>

- <span data-ttu-id="77676-153">Контейнеризовать приложение с помощью [средств Visual Studio 2017 для DOCKER](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="77676-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="77676-154">Контейнеризовать приложение, вручную добавив [Dockerfile](https://docs.docker.com/engine/reference/builder/), а затем используя [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="77676-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="77676-155">Контейнеризовать приложение с помощью средства [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (средство с открытым кодом из Docker).</span><span class="sxs-lookup"><span data-stu-id="77676-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="77676-156">В этом пошаговом руководстве рассматривается подход с применением средств Visual Studio 2017 для Docker, но два других подхода довольно схожи в контексте использования файлов Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="77676-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="77676-157">Сценарий 1. Контейнерные веб-приложения ASP.NET</span><span class="sxs-lookup"><span data-stu-id="77676-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="77676-158">На рисунке ниже показан сценарий для контейнерных приложений веб-приложений eShop прежних версий.</span><span class="sxs-lookup"><span data-stu-id="77676-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Упрощенная схема архитектуры контейнерных приложений ASP.NET в среде разработки](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="77676-160">Сценарий 2. Контейнерная служба WCF</span><span class="sxs-lookup"><span data-stu-id="77676-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="77676-161">На рисунке ниже показан сценарий для 3-уровневого приложения с контейнерной службой WCF.</span><span class="sxs-lookup"><span data-stu-id="77676-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Упрощенная схема архитектуры контейнерной службы WCF в среде разработки](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="77676-163">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-163">Benefits</span></span>

<span data-ttu-id="77676-164">Выполнение монолитного приложения в контейнере имеет свои преимущества.</span><span class="sxs-lookup"><span data-stu-id="77676-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="77676-165">Вы создаете образ для приложения.</span><span class="sxs-lookup"><span data-stu-id="77676-165">First, you create an image for the application.</span></span> <span data-ttu-id="77676-166">В дальнейшем каждое развертывание будет производиться в одной и той же среде.</span><span class="sxs-lookup"><span data-stu-id="77676-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="77676-167">Каждый контейнер использует одну и ту же версию ОС, в нем установлены одни и те же версии зависимостей, применяется одна и та же версия платформы .NET Framework, и для сборки применяется один и тот же процесс.</span><span class="sxs-lookup"><span data-stu-id="77676-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="77676-168">По сути, вы управляете зависимостями приложения с помощью образа Docker.</span><span class="sxs-lookup"><span data-stu-id="77676-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="77676-169">Зависимости передаются вместе с приложением при развертывании контейнеров.</span><span class="sxs-lookup"><span data-stu-id="77676-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="77676-170">Дополнительное преимущество заключается в том, что разработчики могут запускать приложение в единообразной среде, предоставляемой контейнерами Windows.</span><span class="sxs-lookup"><span data-stu-id="77676-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="77676-171">Проблемы, которые появляются только с определенными версиями, можно обнаружить немедленно, а не в процессе взаимодействия с промежуточной или рабочей средой.</span><span class="sxs-lookup"><span data-stu-id="77676-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="77676-172">Когда приложения выполняются в контейнерах, различия между средами разработки, используемыми участниками команды разработчиков, не так важны.</span><span class="sxs-lookup"><span data-stu-id="77676-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="77676-173">Контейнерные приложения также имеют более плоскую кривую горизонтального масштабирования.</span><span class="sxs-lookup"><span data-stu-id="77676-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="77676-174">Контейнерные приложения позволяют создавать больше экземпляров приложений и служб (на основе контейнеров) на виртуальной машине или физическом компьютере по сравнению с обычными развертываниями приложений на каждом компьютере.</span><span class="sxs-lookup"><span data-stu-id="77676-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="77676-175">Такой подход обеспечивает высокую плотность и снижает требования к количеству требуемых ресурсов, особенно при использовании средства оркестрации, например Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="77676-175">This approach translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="77676-176">В идеальной ситуации не требуется вносить изменения в код приложения (C\#).</span><span class="sxs-lookup"><span data-stu-id="77676-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="77676-177">В большинстве случаев требуются только файлы метаданных развертывания Docker (файлы Dockerfile и Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="77676-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-178">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-178">Next steps</span></span>

<span data-ttu-id="77676-179">Подробно изучите это содержимое в вики-разделе на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="77676-180">Контейнеризация веб-приложений .NET Framework с помощью контейнеров Windows и Docker</span><span class="sxs-lookup"><span data-stu-id="77676-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="77676-181">Добавление поддержки Docker в службу WCF</span><span class="sxs-lookup"><span data-stu-id="77676-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="77676-182">Пошаговое руководство 3. Развертывание приложений на основе контейнеров Windows на виртуальных машинах Azure</span><span class="sxs-lookup"><span data-stu-id="77676-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="77676-183">Доступность технического пошагового руководства</span><span class="sxs-lookup"><span data-stu-id="77676-183">Technical walkthrough availability</span></span>

<span data-ttu-id="77676-184">Полное техническое руководство доступно в вики-разделе репозитория eShopModernizing на сайте GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="77676-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="77676-185">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-185">Overview</span></span>

<span data-ttu-id="77676-186">Развертывание на узле Docker на виртуальной машине Windows Server 2016 в Azure позволяет быстро настроить среды разработки, тестирования и промежуточного хранения.</span><span class="sxs-lookup"><span data-stu-id="77676-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="77676-187">Это также позволяет тестировщикам или бизнес-пользователям часто проверять приложение.</span><span class="sxs-lookup"><span data-stu-id="77676-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="77676-188">Виртуальные машины также можно использовать в качестве рабочих сред модели "инфраструктура как услуга" (IaaS).</span><span class="sxs-lookup"><span data-stu-id="77676-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="77676-189">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-189">Goals</span></span>

<span data-ttu-id="77676-190">Цель этого пошагового руководства — продемонстрировать несколько вариантов, которые можно использовать при развертывании контейнеров Windows на виртуальных машинах Azure с Windows Server 2016 или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="77676-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="77676-191">Сценарии</span><span class="sxs-lookup"><span data-stu-id="77676-191">Scenarios</span></span>

<span data-ttu-id="77676-192">В этом пошаговом руководстве рассматривается несколько сценариев.</span><span class="sxs-lookup"><span data-stu-id="77676-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="77676-193">Сценарий А. Развертывание на виртуальной машине Azure с компьютера разработки с помощью подключения к модулю Docker</span><span class="sxs-lookup"><span data-stu-id="77676-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Развертывание на виртуальной машине Azure с компьютера разработки с помощью подключения к модулю Docker](./media/image5-4.png)

<span data-ttu-id="77676-195">**Рис. 5-4.**</span><span class="sxs-lookup"><span data-stu-id="77676-195">**Figure 5-4.**</span></span> <span data-ttu-id="77676-196">Развертывание на виртуальной машине Azure с компьютера разработки с помощью подключения к модулю Docker</span><span class="sxs-lookup"><span data-stu-id="77676-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="77676-197">Сценарий Б. Развертывание на виртуальной машине Azure с помощью реестра Docker</span><span class="sxs-lookup"><span data-stu-id="77676-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Развертывание на виртуальной машине Azure с помощью реестра Docker](./media/image5-5.png)

<span data-ttu-id="77676-199">**Рис. 5-5.**</span><span class="sxs-lookup"><span data-stu-id="77676-199">**Figure 5-5.**</span></span> <span data-ttu-id="77676-200">Развертывание на виртуальной машине Azure с помощью реестра Docker</span><span class="sxs-lookup"><span data-stu-id="77676-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="77676-201">Сценарий В. Развертывание на виртуальной машине Azure из конвейеров CI/CD в Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="77676-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Развертывание на виртуальной машине Azure из конвейеров CI/CD в Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="77676-203">**Рис. 5-6**.</span><span class="sxs-lookup"><span data-stu-id="77676-203">**Figure 5-6.**</span></span> <span data-ttu-id="77676-204">Развертывание на виртуальной машине Azure из конвейеров CI/CD в Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="77676-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="77676-205">Виртуальные машины Azure для контейнеров Windows</span><span class="sxs-lookup"><span data-stu-id="77676-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="77676-206">Виртуальные машины Azure для контейнеров Windows — это виртуальные машины с Windows Server 2016, Windows 10 или более поздних версий с установленным модулем Docker.</span><span class="sxs-lookup"><span data-stu-id="77676-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="77676-207">В большинстве случаев Windows Server 2016 используется на виртуальных машинах Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="77676-208">В настоящее время Azure предоставляет виртуальную машину с именем **Windows Server 2016 с контейнерами**.</span><span class="sxs-lookup"><span data-stu-id="77676-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="77676-209">Она подходит для испытания новой функции контейнера Windows Server с Windows Server Core или Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="77676-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="77676-210">После установки образов ОС контейнера виртуальную машину можно использовать вместе с Docker.</span><span class="sxs-lookup"><span data-stu-id="77676-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="77676-211">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-211">Benefits</span></span>

<span data-ttu-id="77676-212">Несмотря на то что контейнеры Windows можно развертывать на локальных виртуальных машинах Windows Server 2016, при развертывании в Azure вам проще начать работу благодаря готовым к использованию виртуальным машинам контейнеров Windows Server.</span><span class="sxs-lookup"><span data-stu-id="77676-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="77676-213">Вы также получите общее сетевое расположение, доступное для инженеров-тестировщиков, и возможность автоматического масштабирования с помощью масштабируемых наборов виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-214">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-214">Next steps</span></span>

<span data-ttu-id="77676-215">Подробно изучите это содержимое в вики-разделе на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="77676-216">Пошаговое руководство 4. Развертывание приложений на основе контейнеров Windows в службе "Экземпляры контейнеров Azure" (ACI)</span><span class="sxs-lookup"><span data-stu-id="77676-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="77676-217">Доступность технического пошагового руководства</span><span class="sxs-lookup"><span data-stu-id="77676-217">Technical walkthrough availability</span></span>

<span data-ttu-id="77676-218">Полное техническое руководство доступно в вики-разделе репозитория eShopModernizing на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="77676-219">[Развертывание приложений в ACI (служба "Экземпляры контейнеров Azure")](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="77676-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="77676-220">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-220">Overview</span></span>

<span data-ttu-id="77676-221">[Служба "Экземпляры контейнеров Azure" (ACI)](/azure/container-instances/) предоставляет самый быстрый способ использовать среду разработки, тестирования и промежуточного хранения контейнеров, где можно развернуть отдельные экземпляры контейнеров.</span><span class="sxs-lookup"><span data-stu-id="77676-221">[Azure Container Instances (ACI)](/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="77676-222">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-222">Goals</span></span>

<span data-ttu-id="77676-223">В этом пошаговом руководстве продемонстрированы основные сценарии развертывания контейнеров Windows в службе "Экземпляры контейнеров Azure", а также способы развертывания приложений eShopModernizing в ACI.</span><span class="sxs-lookup"><span data-stu-id="77676-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="77676-224">Сценарии</span><span class="sxs-lookup"><span data-stu-id="77676-224">Scenarios</span></span>

<span data-ttu-id="77676-225">В ACI можно по-разному развертывать приложения eShopModernizing, например развернуть только одно или все приложения (приложение MVC, приложение веб-форм или служба WCF).</span><span class="sxs-lookup"><span data-stu-id="77676-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="77676-226">В приведенном ниже сценарии показано приложение ASP.NET MVC и контейнер SQL Server, развернутые в виде контейнеров в ACI (Экземпляры контейнеров Azure).</span><span class="sxs-lookup"><span data-stu-id="77676-226">In the following scenario shown below, you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Развертывание в ACI из среды разработки](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="77676-228">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-228">Benefits</span></span>

<span data-ttu-id="77676-229">Служба "Экземпляры контейнеров Azure" упрощает создание контейнеров Docker и управление ими в Azure, избавляя от необходимости подготавливать виртуальные машины или применять службу более высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="77676-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="77676-230">С помощью ACI можно напрямую развернуть контейнер Windows в Azure и моментально предоставить его в Интернете с полным доменным именем (FQDN) (при условии, что образ контейнера Windows готов в реестре Docker, например в Docker Hub или в Реестре контейнеров Azure).</span><span class="sxs-lookup"><span data-stu-id="77676-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="77676-231">Особенности</span><span class="sxs-lookup"><span data-stu-id="77676-231">Considerations</span></span>

<span data-ttu-id="77676-232">Развертывание контейнеров Windows с полной платформой .NET Framework, ASP.NET или SQL Server в службе "Экземпляры контейнеров Azure" (ACI) выполняется не так быстро, как развертывание на обычном узле Docker (например, Windows Server 2016 с контейнерами Windows), так как образ Docker должен загружаться (извлекаться из реестра Docker) каждый раз, а размеры образов контейнера SQL (15,1 ГБ) и ASP.NET (13,9 ГБ) существенно больше. Тем не менее это намного дешевле, чем поддерживать свой собственный узел Docker (постоянно работающий экземпляр Windows Server 2016 с виртуальной машиной контейнеров Windows в Azure), не говоря уже о целом оркестраторе, таком как Kubernetes в Azure (AKS), что, с другой стороны, отлично подходит для рабочих развертываний.</span><span class="sxs-lookup"><span data-stu-id="77676-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="77676-233">Таким образом, использование службы "Экземпляры контейнеров Azure" является очень удобным вариантом для реализации сценариев разработки и тестирования, а также для конвейеров непрерывной поставки и непрерывной интеграции.</span><span class="sxs-lookup"><span data-stu-id="77676-233">As the main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-234">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-234">Next steps</span></span>

<span data-ttu-id="77676-235">Подробно изучите это содержимое в вики-разделе на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="77676-236">Пошаговое руководство 5. Развертывание приложений на основе контейнеров Windows в Kubernetes в Службе контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="77676-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="77676-237">Доступность технического пошагового руководства</span><span class="sxs-lookup"><span data-stu-id="77676-237">Technical walkthrough availability</span></span>

<span data-ttu-id="77676-238">Полное техническое руководство доступно в вики-разделе репозитория eShopModernizing на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="77676-239">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-239">Overview</span></span>

<span data-ttu-id="77676-240">Приложению на основе контейнеров Windows очень скоро потребуется использовать платформы, отходя от виртуальных машин IaaS.</span><span class="sxs-lookup"><span data-stu-id="77676-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="77676-241">Такой подход требуется, чтобы упростить обеспечение высокого уровня масштабируемости и улучшить автоматическое масштабирование, а также значительно улучшить автоматизированные развертывания и управление версиями.</span><span class="sxs-lookup"><span data-stu-id="77676-241">This approach is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="77676-242">Этого можно достичь с помощью оркестратора [Kubernetes](https://kubernetes.io/), доступного в [Службе контейнеров Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="77676-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="77676-243">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-243">Goals</span></span>

<span data-ttu-id="77676-244">Цель этого пошагового руководства — узнать, как развернуть приложение на основе контейнеров Windows в Kubernetes (также называется *K8s*) в Службе контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="77676-245">Развертывание в Kubernetes с нуля состоит из двух этапов:</span><span class="sxs-lookup"><span data-stu-id="77676-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="77676-246">Развертывание кластера Kubernetes в Службе контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="77676-247">Развертывание приложения и связанных ресурсов в кластере Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="77676-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="77676-248">Сценарии</span><span class="sxs-lookup"><span data-stu-id="77676-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="77676-249">Сценарий А. Развертывание непосредственно в кластере Kubernetes из среды разработки</span><span class="sxs-lookup"><span data-stu-id="77676-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Развертывание непосредственно в кластере Kubernetes из среды разработки](./media/image5-7.png)

<span data-ttu-id="77676-251">**Рис. 5-7.**</span><span class="sxs-lookup"><span data-stu-id="77676-251">**Figure 5-7.**</span></span> <span data-ttu-id="77676-252">Развертывание непосредственно в кластере Kubernetes из среды разработки</span><span class="sxs-lookup"><span data-stu-id="77676-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="77676-253">Сценарий Б. Развертывание в кластере Kubernetes из конвейеров CI/CD в Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="77676-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Развертывание в кластере Kubernetes из конвейеров CI/CD в Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="77676-255">**Рис. 5-8.**</span><span class="sxs-lookup"><span data-stu-id="77676-255">**Figure 5-8.**</span></span> <span data-ttu-id="77676-256">Развертывание в кластере Kubernetes из конвейеров CI/CD в Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="77676-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="77676-257">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-257">Benefits</span></span>

<span data-ttu-id="77676-258">Развертывание в кластер в Kubernetes имеет множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="77676-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="77676-259">Главное преимущество заключается в том, что вы получаете готовую к работе среду, в которой можно горизонтально масштабировать приложение на основе количества экземпляров контейнера, которые требуется использовать (внутренняя масштабируемость в имеющихся узлах), и на основе количества узлов или виртуальных машин в кластере (глобальная масштабируемость кластера).</span><span class="sxs-lookup"><span data-stu-id="77676-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="77676-260">Служба контейнеров Azure оптимизирует популярные средства и технологии с открытым исходным кодом специально для Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="77676-261">Вы получаете открытое решение, которое обеспечивает переносимость как контейнеров, так и конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="77676-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="77676-262">Вы выбираете размер, число узлов и средства оркестрации, а Служба контейнеров делает все остальное.</span><span class="sxs-lookup"><span data-stu-id="77676-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="77676-263">Благодаря Kubernetes разработчики могут рассмотреть возможность использования физических и виртуальных машин, а также планировать инфраструктуру, ориентированную на контейнер, которая упростит такие возможности:</span><span class="sxs-lookup"><span data-stu-id="77676-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="77676-264">Приложения на основе нескольких контейнеров.</span><span class="sxs-lookup"><span data-stu-id="77676-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="77676-265">Репликация экземпляров контейнеров и горизонтальное автомасштабирование.</span><span class="sxs-lookup"><span data-stu-id="77676-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="77676-266">Именование и обнаружение (например, внутренняя служба DNS).</span><span class="sxs-lookup"><span data-stu-id="77676-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="77676-267">Балансировка нагрузки.</span><span class="sxs-lookup"><span data-stu-id="77676-267">Balancing loads</span></span>

- <span data-ttu-id="77676-268">Последовательное обновление.</span><span class="sxs-lookup"><span data-stu-id="77676-268">Rolling updates</span></span>

- <span data-ttu-id="77676-269">Распространение секретов.</span><span class="sxs-lookup"><span data-stu-id="77676-269">Distributing secrets</span></span>

- <span data-ttu-id="77676-270">Проверка работоспособности приложений.</span><span class="sxs-lookup"><span data-stu-id="77676-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-271">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-271">Next steps</span></span>

<span data-ttu-id="77676-272">Подробно изучите это содержимое в вики-разделе на сайте GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="77676-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="77676-273">Пошаговое руководство 6. Развертывание приложений на основе контейнеров Windows в Службе приложений Azure для контейнеров</span><span class="sxs-lookup"><span data-stu-id="77676-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="77676-274">Доступность технического пошагового руководства</span><span class="sxs-lookup"><span data-stu-id="77676-274">Technical walkthrough availability</span></span>

<span data-ttu-id="77676-275">Полное техническое руководство доступно в вики-разделе репозитория eShopModernizing на сайте GitHub:</span><span class="sxs-lookup"><span data-stu-id="77676-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="77676-276">Обзор</span><span class="sxs-lookup"><span data-stu-id="77676-276">Overview</span></span>

<span data-ttu-id="77676-277">Простое контейнерное приложение, использующее контейнеры Windows, можно легко развернуть в Службе приложений Azure для контейнеров.</span><span class="sxs-lookup"><span data-stu-id="77676-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="77676-278">Это рекомендуемый подход для большинства приложений на основе контейнеров Windows.</span><span class="sxs-lookup"><span data-stu-id="77676-278">This approach is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="77676-279">Цели</span><span class="sxs-lookup"><span data-stu-id="77676-279">Goals</span></span>

<span data-ttu-id="77676-280">Цель этого пошагового руководства — узнать, как развернуть приложение на основе контейнера Windows в Службе приложений Azure для контейнеров из реестра (Docker Hub или Реестра контейнеров Azure).</span><span class="sxs-lookup"><span data-stu-id="77676-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="77676-281">Сценарий</span><span class="sxs-lookup"><span data-stu-id="77676-281">Scenario</span></span>

![Развертывание приложений на основе контейнеров Windows в Службе приложений Azure для контейнеров](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="77676-283">Преимущества</span><span class="sxs-lookup"><span data-stu-id="77676-283">Benefits</span></span>

<span data-ttu-id="77676-284">Развертывание в Службе приложений Azure для контейнеров предоставляет преимущества контейнеров в паре с преимуществами PaaS Службы приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="77676-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="77676-285">Службу приложений можно легко масштабировать как по вертикали, так и по горизонтали, а также настроить для автоматического масштабирования в соответствии с изменяющимися потребностями.</span><span class="sxs-lookup"><span data-stu-id="77676-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="77676-286">Обновления можно выполнять с нулевым временем простоя, а также можно легко настроить непрерывное развертывание из реестра.</span><span class="sxs-lookup"><span data-stu-id="77676-286">Updates can be performed with zero downtime and the configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="77676-287">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="77676-287">Next steps</span></span>

<span data-ttu-id="77676-288">Подробно изучите это содержимое в вики-разделе на сайте GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="77676-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="77676-289">[Назад](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Вперед](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="77676-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
