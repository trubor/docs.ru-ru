---
title: Различия в размещении между ASP.NET MVC и ASP.NET Core
description: Обзор различий между размещением приложений ASP.NET MVC и ASP.NET Core приложениями.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 402dd5782cb215545ff2ef13f97ec269b8a2540b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401768"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="39908-103">Различия в размещении между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39908-103">Hosting differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="39908-104">Приложения ASP.NET MVC размещаются в IIS и могут полагаться на конфигурацию IIS для их поведения.</span><span class="sxs-lookup"><span data-stu-id="39908-104">ASP.NET MVC apps are hosted in IIS, and may rely on IIS configuration for their behavior.</span></span> <span data-ttu-id="39908-105">Это часто включает [модули IIS](/iis/get-started/introduction-to-iis/iis-modules-overview).</span><span class="sxs-lookup"><span data-stu-id="39908-105">This often includes [IIS modules](/iis/get-started/introduction-to-iis/iis-modules-overview).</span></span> <span data-ttu-id="39908-106">В рамках проверки приложения, чтобы подготовиться к его переносу из ASP.NET MVC в ASP.NET Core, команды должны выбрать, какие модули, если они используются, из списка модулей IIS, установленных на сервере.</span><span class="sxs-lookup"><span data-stu-id="39908-106">As part of reviewing an app to prepare to port it from ASP.NET MVC to ASP.NET Core, teams should identify which modules, if any, they're using from the list of IIS Modules installed on their server.</span></span>

<span data-ttu-id="39908-107">[ASP.NET Core приложения могут выполняться на нескольких разных серверах](/aspnet/core/fundamentals/servers/).</span><span class="sxs-lookup"><span data-stu-id="39908-107">[ASP.NET Core apps can run on a number of different servers](/aspnet/core/fundamentals/servers/).</span></span> <span data-ttu-id="39908-108">По умолчанию для кросс-платформенного сервера Kestrel является хорошим выбором.</span><span class="sxs-lookup"><span data-stu-id="39908-108">The default cross platform server, Kestrel, is a good default choice.</span></span> <span data-ttu-id="39908-109">Приложения, работающие в Kestrel, могут размещаться в службах IIS, выполняющихся в отдельном процессе.</span><span class="sxs-lookup"><span data-stu-id="39908-109">Apps running in Kestrel can be hosted by IIS, running in a separate process.</span></span> <span data-ttu-id="39908-110">В Windows приложения также могут выполняться в процессе в службах IIS или с помощью HTTP.sys.</span><span class="sxs-lookup"><span data-stu-id="39908-110">On Windows, apps can also run in process on IIS or using HTTP.sys.</span></span> <span data-ttu-id="39908-111">Как правило, для оптимальной производительности рекомендуется Kestrel.</span><span class="sxs-lookup"><span data-stu-id="39908-111">Kestrel is generally recommended for best performance.</span></span> <span data-ttu-id="39908-112">HTTP.sys можно использовать в сценариях, где приложение имеет доступ к Интернету и необходимые возможности поддерживаются HTTP.sys, но не Kestrel.</span><span class="sxs-lookup"><span data-stu-id="39908-112">HTTP.sys can be used in scenarios where the app is exposed to the Internet and required capabilities are supported by HTTP.sys but not Kestrel.</span></span>

<span data-ttu-id="39908-113">Kestrel не имеет эквивалента модулям IIS (хотя приложения, размещенные в IIS, по-прежнему могут использовать преимущества модулей IIS).</span><span class="sxs-lookup"><span data-stu-id="39908-113">Kestrel does not have an equivalent to IIS modules (though apps hosted in IIS can still take advantage of IIS modules).</span></span> <span data-ttu-id="39908-114">Для достижения эквивалентного поведения обычно используется промежуточный слой, настроенный в самом приложении ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="39908-114">To achieve equivalent behavior, middleware configured in the ASP.NET Core app itself is typically used.</span></span>

## <a name="references"></a><span data-ttu-id="39908-115">Ссылки</span><span class="sxs-lookup"><span data-stu-id="39908-115">References</span></span>

- [<span data-ttu-id="39908-116">Модули IIS</span><span class="sxs-lookup"><span data-stu-id="39908-116">IIS Modules</span></span>](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [<span data-ttu-id="39908-117">Серверы ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39908-117">ASP.NET Core Servers</span></span>](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
><span data-ttu-id="39908-118">[Назад](app-startup-differences.md)
>[Вперед](serving-static-files.md)</span><span class="sxs-lookup"><span data-stu-id="39908-118">[Previous](app-startup-differences.md)
[Next](serving-static-files.md)</span></span>
