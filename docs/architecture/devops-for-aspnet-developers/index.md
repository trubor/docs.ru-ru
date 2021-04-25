---
title: DevOps для разработчиков ASP.NET Core
author: CamSoper
description: Рекомендации по созданию сквозного решения конвейера DevOps для приложения ASP.NET Core, размещенного в Azure.
ms.author: casoper
ms.date: 04/13/2021
ms.custom: devx-track-csharp, mvc, seodec18
no-loc:
- appsettings.json
- ASP.NET Core Identity
- cookie
- Cookie
- Blazor
- Blazor Server
- Blazor WebAssembly
- Identity
- Let's Encrypt
- Razor
- SignalR
uid: azure/devops/index
ms.openlocfilehash: 5052c16e637260ede3a81578ba2280f760d086c4
ms.sourcegitcommit: 040b745ac19e4a5d23df17422ab30e72839f5754
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107810518"
---
# <a name="devops-for-aspnet-core-developers"></a><span data-ttu-id="e653d-103">DevOps для разработчиков ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e653d-103">DevOps for ASP.NET Core Developers</span></span>

<span data-ttu-id="e653d-104">[![Изображение обложки](./media/cover-large.png)](https://aka.ms/devopsbook)</span><span class="sxs-lookup"><span data-stu-id="e653d-104">[![Cover Image](./media/cover-large.png)](https://aka.ms/devopsbook)</span></span>

<span data-ttu-id="e653d-105">**Редакция 1.1.0**</span><span class="sxs-lookup"><span data-stu-id="e653d-105">**EDITION v1.1.0**</span></span>

<span data-ttu-id="e653d-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/devops-ebook-changelog).</span><span class="sxs-lookup"><span data-stu-id="e653d-106">Refer [changelog](https://aka.ms/devops-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="e653d-107">Это руководство доступно как [загружаемая электронная книга в формате PDF](https://aka.ms/devopsbook).</span><span class="sxs-lookup"><span data-stu-id="e653d-107">This guide is available as a [downloadable PDF e-book](https://aka.ms/devopsbook).</span></span>

<span data-ttu-id="e653d-108">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="e653d-108">PUBLISHED BY</span></span>

<span data-ttu-id="e653d-109">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e653d-109">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e653d-110">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="e653d-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e653d-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e653d-111">One Microsoft Way</span></span>

<span data-ttu-id="e653d-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e653d-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e653d-113">&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="e653d-113">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="e653d-114">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="e653d-114">All rights reserved.</span></span> <span data-ttu-id="e653d-115">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="e653d-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e653d-116">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="e653d-116">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="e653d-117">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="e653d-117">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e653d-118">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="e653d-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e653d-119">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="e653d-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e653d-120">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e653d-120">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e653d-121">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="e653d-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e653d-122">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="e653d-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e653d-123">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="e653d-123">All other marks and logos are property of their respective owners.</span></span>

## <a name="credits"></a><span data-ttu-id="e653d-124">Благодарности</span><span class="sxs-lookup"><span data-stu-id="e653d-124">Credits</span></span>

<span data-ttu-id="e653d-125">Авторы:</span><span class="sxs-lookup"><span data-stu-id="e653d-125">Authors:</span></span>

> [<span data-ttu-id="e653d-126">Кэм Сопер (Cam Soper)</span><span class="sxs-lookup"><span data-stu-id="e653d-126">Cam Soper</span></span>](https://twitter.com/camsoper)
>
> [<span data-ttu-id="e653d-127">Скотт Адди (Scott Addie)</span><span class="sxs-lookup"><span data-stu-id="e653d-127">Scott Addie</span></span>](https://twitter.com/scottaddie)
>
> [<span data-ttu-id="e653d-128">Колин Дембовски (Colin Dembovsky)</span><span class="sxs-lookup"><span data-stu-id="e653d-128">Colin Dembovsky</span></span>](https://twitter.com/colindembovsky)

## <a name="welcome"></a><span data-ttu-id="e653d-129">Приветствие</span><span class="sxs-lookup"><span data-stu-id="e653d-129">Welcome</span></span>

<span data-ttu-id="e653d-130">Руководство по жизненному циклу разработки Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="e653d-130">Welcome to the Azure Development Lifecycle guide for .NET!</span></span> <span data-ttu-id="e653d-131">В этом руководстве предоставляются основные сведения по созданию жизненного цикла разработки в Azure с помощью инструментов и процессов .NET.</span><span class="sxs-lookup"><span data-stu-id="e653d-131">This guide introduces the basic concepts of building a development lifecycle around Azure using .NET tools and processes.</span></span> <span data-ttu-id="e653d-132">После его прохождения вы сможете наиболее эффективно использовать цепочку инструментов DevOps.</span><span class="sxs-lookup"><span data-stu-id="e653d-132">After finishing this guide, you'll reap the benefits of a mature DevOps toolchain.</span></span>

## <a name="who-this-guide-is-for"></a><span data-ttu-id="e653d-133">Для кого предназначено это руководство</span><span class="sxs-lookup"><span data-stu-id="e653d-133">Who this guide is for</span></span>

<span data-ttu-id="e653d-134">Вы должны быть опытным разработчиком ASP.NET Core (уровень 200–300).</span><span class="sxs-lookup"><span data-stu-id="e653d-134">You should be an experienced ASP.NET Core developer (200-300 level).</span></span> <span data-ttu-id="e653d-135">Вам не нужно ничего знать об Azure, так как эти сведения есть во введении.</span><span class="sxs-lookup"><span data-stu-id="e653d-135">You don't need to know anything about Azure, as we'll cover that in this introduction.</span></span> <span data-ttu-id="e653d-136">Это руководство может также оказаться полезным для инженеров DevOps, которые преимущественно работают с операциями, а не занимаются разработкой.</span><span class="sxs-lookup"><span data-stu-id="e653d-136">This guide may also be useful for DevOps engineers who are more focused on operations than development.</span></span>

<span data-ttu-id="e653d-137">Это руководство предназначено для разработчиков Windows.</span><span class="sxs-lookup"><span data-stu-id="e653d-137">This guide targets Windows developers.</span></span> <span data-ttu-id="e653d-138">Linux и macOS также полностью поддерживаются в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e653d-138">However, Linux and macOS are fully supported by .NET Core.</span></span> <span data-ttu-id="e653d-139">Чтобы адаптировать это руководство для Linux или macOS, смотрите сноски, в которых приводятся характерные отличия.</span><span class="sxs-lookup"><span data-stu-id="e653d-139">To adapt this guide for Linux/macOS, watch for callouts for Linux/macOS differences.</span></span>

## <a name="what-this-guide-doesnt-cover"></a><span data-ttu-id="e653d-140">Темы, которые выходят за рамки этого руководства</span><span class="sxs-lookup"><span data-stu-id="e653d-140">What this guide doesn't cover</span></span>

<span data-ttu-id="e653d-141">В этом руководстве приводятся рекомендации для разработчиков .NET по сквозному непрерывному развертыванию.</span><span class="sxs-lookup"><span data-stu-id="e653d-141">This guide is focused on an end-to-end continuous deployment experience for .NET developers.</span></span> <span data-ttu-id="e653d-142">Это не исчерпывающее руководство по Azure, и в нем не рассматриваются подробно API .NET для служб Azure.</span><span class="sxs-lookup"><span data-stu-id="e653d-142">It's not an exhaustive guide to all things Azure, and it doesn't focus extensively on .NET APIs for Azure services.</span></span> <span data-ttu-id="e653d-143">Основное внимание уделяется непрерывной интеграции, развертыванию, мониторингу и отладке.</span><span class="sxs-lookup"><span data-stu-id="e653d-143">The emphasis is all around continuous integration, deployment, monitoring, and debugging.</span></span> <span data-ttu-id="e653d-144">В конце руководства предлагаются рекомендации по дальнейшим действиям.</span><span class="sxs-lookup"><span data-stu-id="e653d-144">Near the end of the guide, recommendations for next steps are offered.</span></span> <span data-ttu-id="e653d-145">В число предложений входят службы платформы Azure, полезные для разработчиков ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e653d-145">Included in the suggestions are Azure platform services that are useful to ASP.NET Core developers.</span></span>

## <a name="whats-in-this-guide"></a><span data-ttu-id="e653d-146">Содержание руководства</span><span class="sxs-lookup"><span data-stu-id="e653d-146">What's in this guide</span></span>

### <a name="tools-and-downloads"></a>[<span data-ttu-id="e653d-147">Инструменты и файлы для скачивания</span><span class="sxs-lookup"><span data-stu-id="e653d-147">Tools and downloads</span></span>](xref:azure/devops/tools-and-downloads)

<span data-ttu-id="e653d-148">Вы узнаете, где получить инструменты, используемые в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="e653d-148">Learn where to acquire the tools used in this guide.</span></span>

### <a name="deploy-to-app-service"></a>[<span data-ttu-id="e653d-149">Развертывание в службу приложений</span><span class="sxs-lookup"><span data-stu-id="e653d-149">Deploy to App Service</span></span>](xref:azure/devops/deploy-to-app-service)

<span data-ttu-id="e653d-150">Разные способы развертывания приложения ASP.NET Core в службе приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="e653d-150">Learn the various methods for deploying an ASP.NET Core app to Azure App Service.</span></span>

### <a name="continuous-integration-and-deployment-with-azure-devops"></a>[<span data-ttu-id="e653d-151">Непрерывная поставка и интеграция с помощью Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="e653d-151">Continuous integration and deployment with Azure DevOps</span></span>](xref:azure/devops/cicd)

<span data-ttu-id="e653d-152">Создание решения сквозной непрерывной интеграции и развертывания для приложения ASP.NET Core с помощью GitHub, Azure DevOps Services и Azure.</span><span class="sxs-lookup"><span data-stu-id="e653d-152">Build an end-to-end continuous integration and deployment solution for your ASP.NET Core app with GitHub, Azure DevOps Services, and Azure.</span></span>

### <a name="continuous-integration-and-deployment-with-github-actions"></a>[<span data-ttu-id="e653d-153">Непрерывная поставка и интеграция с помощью GitHub Actions</span><span class="sxs-lookup"><span data-stu-id="e653d-153">Continuous integration and deployment with GitHub Actions</span></span>](xref:azure/devops/github-actions)

<span data-ttu-id="e653d-154">Создайте комплексное решение непрерывной поставки и интеграции для своего приложения ASP.NET Core, использующее GitHub, GitHub Actions и Azure, а также функции CodeQL для проверки кода на качество и безопасность.</span><span class="sxs-lookup"><span data-stu-id="e653d-154">Build an end-to-end continuous integration and deployment solution for your ASP.NET Core app with GitHub, GitHub Actions, and Azure, including code scanning for security and quality using CodeQL.</span></span>

### <a name="monitor-and-debug"></a>[<span data-ttu-id="e653d-155">Мониторинг и отладка</span><span class="sxs-lookup"><span data-stu-id="e653d-155">Monitor and debug</span></span>](xref:azure/devops/monitor)

<span data-ttu-id="e653d-156">Мониторинг, устранение неполадок и настройка приложения с помощью инструментов Azure.</span><span class="sxs-lookup"><span data-stu-id="e653d-156">Use Azure's tools to monitor, troubleshoot, and tune your application.</span></span>

### <a name="next-steps"></a>[<span data-ttu-id="e653d-157">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="e653d-157">Next steps</span></span>](xref:azure/devops/next-steps)

<span data-ttu-id="e653d-158">Другие способы изучения Azure для разработчиков ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e653d-158">Other learning paths for the ASP.NET Core developer learning Azure.</span></span>

## <a name="additional-introductory-reading"></a><span data-ttu-id="e653d-159">Дополнительные справочные материалы</span><span class="sxs-lookup"><span data-stu-id="e653d-159">Additional introductory reading</span></span>

<span data-ttu-id="e653d-160">Если это ваш первый опыт работы с облачными вычислениями, в этой статье рассматриваются основы.</span><span class="sxs-lookup"><span data-stu-id="e653d-160">If this is your first exposure to cloud computing, these articles explain the basics.</span></span>

* [<span data-ttu-id="e653d-161">Что такое облачные вычисления?</span><span class="sxs-lookup"><span data-stu-id="e653d-161">What is Cloud Computing?</span></span>](https://azure.microsoft.com/overview/what-is-cloud-computing/)
* [<span data-ttu-id="e653d-162">Примеры облачных вычислений</span><span class="sxs-lookup"><span data-stu-id="e653d-162">Examples of Cloud Computing</span></span>](https://azure.microsoft.com/overview/examples-of-cloud-computing/)
* [<span data-ttu-id="e653d-163">Что такое IaaS?</span><span class="sxs-lookup"><span data-stu-id="e653d-163">What is IaaS?</span></span>](https://azure.microsoft.com/overview/what-is-iaas/)
* [<span data-ttu-id="e653d-164">Что такое PaaS?</span><span class="sxs-lookup"><span data-stu-id="e653d-164">What is PaaS?</span></span>](https://azure.microsoft.com/overview/what-is-paas/)

>[!div class="step-by-step"]
>[<span data-ttu-id="e653d-165">Вперед</span><span class="sxs-lookup"><span data-stu-id="e653d-165">Next</span></span>](tools-and-downloads.md)
