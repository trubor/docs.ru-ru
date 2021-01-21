---
title: Общие рекомендации
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Общие рекомендации
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187955"
---
# <a name="general-guidance"></a><span data-ttu-id="0dfc7-103">Общие рекомендации</span><span class="sxs-lookup"><span data-stu-id="0dfc7-103">General guidance</span></span>

<span data-ttu-id="0dfc7-104">В этом разделе представлена сводка относительно выбора .NET 5 или .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-104">This section provides a summary of when to choose .NET 5 or .NET Framework.</span></span> <span data-ttu-id="0dfc7-105">Дополнительные сведения об этих вариантах представлены в последующих разделах.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="0dfc7-106">Используйте .NET 5 с контейнерами Windows или Linux для контейнерного серверного приложения Docker в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="0dfc7-106">Use .NET 5, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="0dfc7-107">для создания кроссплатформенных решений;</span><span class="sxs-lookup"><span data-stu-id="0dfc7-107">You have cross-platform needs.</span></span> <span data-ttu-id="0dfc7-108">Например, вы хотите использовать контейнеры и Windows, и Linux.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="0dfc7-109">Архитектура приложения основана на микрослужбах.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="0dfc7-110">Вам нужно быстро запустить контейнеры, и вы хотите использовать небольшой объем памяти на каждый контейнер, чтобы получить более высокую плотность или больше контейнеров на единицу оборудования для снижения затрат.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="0dfc7-111">Вкратце, при создании новых контейнерных приложений .NET следует рассматривать .NET 5 как вариант по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-111">In short, when you create new containerized .NET applications, you should consider .NET 5 as the default choice.</span></span> <span data-ttu-id="0dfc7-112">Он имеет множество преимуществ и лучше соответствует концепции и стилю работы с контейнерами.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="0dfc7-113">Дополнительное преимущество использования .NET 5 заключается в том, что можно параллельно запускать версии .NET для приложений на одной и той же машине.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-113">An extra benefit of using .NET 5 is that you can run side-by-side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="0dfc7-114">Данное преимущество более важно для серверов или виртуальных машин, которые не используют контейнеры, так как контейнеры изолируют версии .NET, нужные приложению.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="0dfc7-115">(При условии, что они совместимы с базовой ОС.)</span><span class="sxs-lookup"><span data-stu-id="0dfc7-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="0dfc7-116">Используйте .NET Framework для серверных приложений в контейнерах Docker в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="0dfc7-117">В настоящее время приложение использует .NET Framework и имеет строгие зависимости от Windows.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="0dfc7-118">Необходимо использовать API Windows, которые не поддерживаются .NET 5.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-118">You need to use Windows APIs that are not supported by .NET 5.</span></span>

- <span data-ttu-id="0dfc7-119">Требуются сторонние библиотеки .NET или пакеты NuGet, недоступные для .NET 5.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET 5.</span></span>

<span data-ttu-id="0dfc7-120">Использование .NET Framework в Docker может улучшить качество развертывания, сводя к минимуму проблемы развертывания.</span><span class="sxs-lookup"><span data-stu-id="0dfc7-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="0dfc7-121">Данный [сценарий "подъема и смены"](https://aka.ms/liftandshiftwithcontainersebook) важен для контейнеризации приложений прежних версий, которые изначально были разработаны с использованием классической платформы .NET Framework, например ASP.NET WebForms, веб-приложений MVC или служб WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="0dfc7-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0dfc7-122">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="0dfc7-122">Additional resources</span></span>

- <span data-ttu-id="0dfc7-123">**Электронная книга. модернизация существующих приложений .NET Framework с помощью Azure и контейнеров Windows**</span><span class="sxs-lookup"><span data-stu-id="0dfc7-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="0dfc7-124">**Примеры приложений: модернизация устаревших веб-приложений ASP.NET с помощью контейнеров Windows**</span><span class="sxs-lookup"><span data-stu-id="0dfc7-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="0dfc7-125">[Назад](index.md)
>[Вперед](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="0dfc7-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
