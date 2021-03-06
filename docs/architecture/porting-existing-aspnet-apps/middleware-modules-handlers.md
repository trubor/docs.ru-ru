---
title: Сравнение по промежуточного слоя с модулями и обработчиками
description: В этом разделе рассматриваются различия в структуре для приложений ASP.NET, использующих обработчики и модули с ASP.NET Core приложениями, которые определяют по промежуточного слоя для конвейеров обработки запросов.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401733"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="7434e-103">Сравнение по промежуточного слоя с модулями и обработчиками</span><span class="sxs-lookup"><span data-stu-id="7434e-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="7434e-104">Если существующее приложение ASP.NET MVC или веб-API использует OWIN/Katana, скорее всего, вы уже знакомы с концепцией по промежуточного слоя и переносом их в ASP.NET Core должны быть довольно простыми.</span><span class="sxs-lookup"><span data-stu-id="7434e-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="7434e-105">Однако большинство приложений ASP.NET полагаются на HTTP-модули и обработчики HTTP, а не по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="7434e-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="7434e-106">Перенос этих данных в ASP.NET Core требует дополнительных усилий.</span><span class="sxs-lookup"><span data-stu-id="7434e-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="7434e-107">Модули и обработчики ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7434e-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="7434e-108">[Модули HTTP и обработчики HTTP](/troubleshoot/aspnet/http-modules-handlers) являются неотъемлемой частью архитектуры ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7434e-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="7434e-109">Во время обработки запроса каждый запрос обрабатывается несколькими модулями HTTP (например, модулем проверки подлинности и модулем сеанса) и обрабатывается одним HTTP-обработчиком.</span><span class="sxs-lookup"><span data-stu-id="7434e-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="7434e-110">После обработки запроса обработчиком запрос передается обратно через HTTP-модули.</span><span class="sxs-lookup"><span data-stu-id="7434e-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="7434e-111">Если приложение использует пользовательские модули HTTP или обработчики HTTP, вам потребуется план для их переноса в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7434e-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="7434e-112">Наиболее вероятной заменой в ASP.NET Core является по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="7434e-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="7434e-113">По промежуточного слоя ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7434e-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="7434e-114">ASP.NET Core определяет конвейер запросов в методе каждого приложения `Configure` .</span><span class="sxs-lookup"><span data-stu-id="7434e-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="7434e-115">Этот конвейер запросов определяет способ обработки входящего запроса приложением, при этом каждый метод в конвейере вызывает следующий метод до завершения метода, а цепочка по *промежуточного слоя* завершается и возвращает резервную копию стека.</span><span class="sxs-lookup"><span data-stu-id="7434e-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="7434e-116">По промежуточного слоя может быть нацелено на все запросы или может быть настроено на соответствие только определенным запросам в зависимости от запрошенного пути или других факторов.</span><span class="sxs-lookup"><span data-stu-id="7434e-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="7434e-117">Его можно настроить полностью в `Configure` методе приложения или реализовать в отдельном классе.</span><span class="sxs-lookup"><span data-stu-id="7434e-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="7434e-118">Поведение в приложении ASP.NET MVC, использующем модули HTTP, вероятно, лучше всего подходит для [пользовательского по промежуточного слоя](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="7434e-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="7434e-119">Пользовательские обработчики HTTP можно заменить пользовательскими маршрутами или конечными точками, которые отвечают на один и тот же путь.</span><span class="sxs-lookup"><span data-stu-id="7434e-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="references"></a><span data-ttu-id="7434e-120">Ссылки</span><span class="sxs-lookup"><span data-stu-id="7434e-120">References</span></span>

- [<span data-ttu-id="7434e-121">ASP.NET HTTP-модули и обработчики HTTP</span><span class="sxs-lookup"><span data-stu-id="7434e-121">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="7434e-122">По промежуточного слоя ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7434e-122">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="7434e-123">[Назад](dependency-injection-differences.md)
>[Вперед](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="7434e-123">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
