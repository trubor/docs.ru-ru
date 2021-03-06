---
title: Различия в внедрении зависимостей между ASP.NET MVC и ASP.NET Core
description: Рассмотрим, как внедрение зависимостей работает в ASP.NET MVC и ASP.NET Core, как они отличаются и как выполнить миграцию из ASP.NET MVC в ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401780"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="40e38-103">Различия в внедрении зависимостей между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40e38-103">Dependency injection differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="40e38-104">Несмотря на то, что внедрение зависимостей (DI) не встроено в ASP.NET MVC или веб-API, многие приложения включают его, добавляя пакет NuGet с контейнером инверсии управления (IOC).</span><span class="sxs-lookup"><span data-stu-id="40e38-104">Although dependency injection (DI) isn't built into ASP.NET MVC or Web API, many apps enable it by adding a NuGet package with an inversion of control (IOC) container.</span></span> <span data-ttu-id="40e38-105">Они иногда называются контейнерами DI для внедрения зависимостей (или инверсии).</span><span class="sxs-lookup"><span data-stu-id="40e38-105">These are sometimes referred to as DI containers, for dependency injection (or inversion).</span></span> <span data-ttu-id="40e38-106">Ниже перечислены некоторые из наиболее популярных контейнеров, используемых в приложениях ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="40e38-106">Some of the most popular containers used in ASP.NET MVC apps include:</span></span>

- <span data-ttu-id="40e38-107">[Autofac](https://www.autofac.org/);</span><span class="sxs-lookup"><span data-stu-id="40e38-107">[Autofac](https://www.autofac.org/)</span></span>
- [<span data-ttu-id="40e38-108">Unity</span><span class="sxs-lookup"><span data-stu-id="40e38-108">Unity</span></span>](https://unitycontainer.github.io/)
- [<span data-ttu-id="40e38-109">нинжект</span><span class="sxs-lookup"><span data-stu-id="40e38-109">Ninject</span></span>](http://www.ninject.org/)
- <span data-ttu-id="40e38-110">[StructureMap](http://structuremap.github.io/) *(не рекомендуется)*</span><span class="sxs-lookup"><span data-stu-id="40e38-110">[StructureMap](http://structuremap.github.io/) *(deprecated)*</span></span>
- [<span data-ttu-id="40e38-111">Castle Windsor</span><span class="sxs-lookup"><span data-stu-id="40e38-111">Castle Windsor</span></span>](http://www.castleproject.org/projects/windsor/)

<span data-ttu-id="40e38-112">Если приложение ASP.NET MVC не использует DI, возможно, вам потребуется изучить встроенную поддержку DI в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="40e38-112">If your ASP.NET MVC app isn't using DI, you will probably want to investigate the built-in support for DI in ASP.NET Core.</span></span> <span data-ttu-id="40e38-113">DI способствует слабой взаимосвязи модулей в приложении и обеспечивает лучшую пригодность к тестированию и соблюдение таких принципов, как [сплошная](https://www.weeklydevtips.com/episodes/047).</span><span class="sxs-lookup"><span data-stu-id="40e38-113">DI promotes loose coupling of modules in your app and enables better testability and adherence to principles like [SOLID](https://www.weeklydevtips.com/episodes/047).</span></span>

<span data-ttu-id="40e38-114">Если в приложении используется DI, то, вероятно, лучше всего подойдет, если используемый контейнер поддерживает ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="40e38-114">If your app does use DI, then probably your best course of action is to see if the container you're using supports ASP.NET Core.</span></span> <span data-ttu-id="40e38-115">Если это так, можно продолжить его использование и настраиваемые правила конфигурации, описывающие сопоставления типов и время существования.</span><span class="sxs-lookup"><span data-stu-id="40e38-115">If so, you may be able to continue using it and your custom configuration rules describing your type mappings and lifetimes.</span></span>

<span data-ttu-id="40e38-116">В любом случае следует рассмотреть возможность использования встроенной поддержки DI, поставляемой с ASP.NET Core, так как она может соответствовать потребностям вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="40e38-116">Either way, you should consider using the built-in support for DI that ships with ASP.NET Core, as it may meet your app's needs.</span></span>

## <a name="dependency-injection-in-aspnet-core"></a><span data-ttu-id="40e38-117">Внедрение зависимостей в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40e38-117">Dependency injection in ASP.NET Core</span></span>

<span data-ttu-id="40e38-118">ASP.NET Core предполагает, что приложения будут использовать DI.</span><span class="sxs-lookup"><span data-stu-id="40e38-118">ASP.NET Core assumes apps will use DI.</span></span> <span data-ttu-id="40e38-119">Она не только встроена в платформу, но и необходима для поддержки функций платформы в ASP.NET Coreных приложениях.</span><span class="sxs-lookup"><span data-stu-id="40e38-119">It's not just built into the framework, but is required in order to bring support for framework features into your ASP.NET Core apps.</span></span> <span data-ttu-id="40e38-120">При запуске приложения выполняется вызов, `ConfigureServices` который отвечает за регистрацию всех типов, которые могут создаваться и внедряться в контейнере di (служба коллекции или поставщик служб) в приложение.</span><span class="sxs-lookup"><span data-stu-id="40e38-120">In app startup, a call is made to `ConfigureServices` which is responsible for registering all of the types that the DI container (service collection/service provider) can create and inject in the app.</span></span> <span data-ttu-id="40e38-121">Встроенные функции ASP.NET Core, такие как Entity Framework Core, идентификация и даже MVC, передаются в приложение путем их настройки в качестве служб в `ConfigureServices` методе.</span><span class="sxs-lookup"><span data-stu-id="40e38-121">Built-in ASP.NET Core features like Entity Framework Core, Identity, and even MVC are brought into the app by configuring them as services in the `ConfigureServices` method.</span></span>

<span data-ttu-id="40e38-122">В дополнение к реализации по умолчанию приложения по-прежнему могут использовать пользовательские контейнеры.</span><span class="sxs-lookup"><span data-stu-id="40e38-122">In addition to using the default implementation, apps can still use custom containers.</span></span> <span data-ttu-id="40e38-123">В [документации описано, как заменить контейнер службы по умолчанию](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).</span><span class="sxs-lookup"><span data-stu-id="40e38-123">The [documentation covers how to replace the default service container](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).</span></span>

<span data-ttu-id="40e38-124">DI является фундаментальным для ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="40e38-124">DI is fundamental to ASP.NET Core.</span></span> <span data-ttu-id="40e38-125">Если ваша команда еще не была хорошо принята на практике, необходимо понять ее перед переносом приложения.</span><span class="sxs-lookup"><span data-stu-id="40e38-125">If your team isn't already well-versed in this practice, you'll want to understand it before porting your app.</span></span>

## <a name="references"></a><span data-ttu-id="40e38-126">Ссылки</span><span class="sxs-lookup"><span data-stu-id="40e38-126">References</span></span>

- [<span data-ttu-id="40e38-127">Внедрение зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="40e38-127">Dependency Injection in .NET</span></span>](../../core/extensions/dependency-injection.md)
- [<span data-ttu-id="40e38-128">Использование внедрения зависимостей в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40e38-128">Dependency Injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
><span data-ttu-id="40e38-129">[Назад](serving-static-files.md)
>[Вперед](middleware-modules-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="40e38-129">[Previous](serving-static-files.md)
[Next](middleware-modules-handlers.md)</span></span>
