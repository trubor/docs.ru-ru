---
title: Различия в размещении между ASP.NET MVC и ASP.NET Core
description: Обзор различий между размещением приложений ASP.NET MVC и ASP.NET Core приложениями.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9881a40403f8109fa63e25167b753ed4ce8ade17
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122902"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="56329-103">Различия в размещении между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56329-103">Hosting differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="56329-104">Приложения ASP.NET MVC размещаются в IIS и могут полагаться на конфигурацию IIS для их поведения.</span><span class="sxs-lookup"><span data-stu-id="56329-104">ASP.NET MVC apps are hosted in IIS, and may rely on IIS configuration for their behavior.</span></span> <span data-ttu-id="56329-105">Это часто включает [модули IIS](/iis/get-started/introduction-to-iis/iis-modules-overview).</span><span class="sxs-lookup"><span data-stu-id="56329-105">This often includes [IIS modules](/iis/get-started/introduction-to-iis/iis-modules-overview).</span></span> <span data-ttu-id="56329-106">В рамках проверки приложения, чтобы подготовиться к его переносу из ASP.NET MVC в ASP.NET Core, команды должны выбрать, какие модули, если они используются, из списка модулей IIS, установленных на сервере.</span><span class="sxs-lookup"><span data-stu-id="56329-106">As part of reviewing an app to prepare to port it from ASP.NET MVC to ASP.NET Core, teams should identify which modules, if any, they're using from the list of IIS Modules installed on their server.</span></span>

<span data-ttu-id="56329-107">[ASP.NET Core приложения могут выполняться на нескольких разных серверах](/aspnet/core/fundamentals/servers/).</span><span class="sxs-lookup"><span data-stu-id="56329-107">[ASP.NET Core apps can run on a number of different servers](/aspnet/core/fundamentals/servers/).</span></span> <span data-ttu-id="56329-108">По умолчанию для кросс-платформенного сервера Kestrel является хорошим выбором.</span><span class="sxs-lookup"><span data-stu-id="56329-108">The default cross platform server, Kestrel, is a good default choice.</span></span> <span data-ttu-id="56329-109">Приложения, работающие в Kestrel, могут размещаться в службах IIS, выполняющихся в отдельном процессе.</span><span class="sxs-lookup"><span data-stu-id="56329-109">Apps running in Kestrel can be hosted by IIS, running in a separate process.</span></span> <span data-ttu-id="56329-110">В Windows приложения также могут выполняться в процессе в службах IIS или с помощью HTTP.sys.</span><span class="sxs-lookup"><span data-stu-id="56329-110">On Windows, apps can also run in process on IIS or using HTTP.sys.</span></span> <span data-ttu-id="56329-111">Как правило, для оптимальной производительности рекомендуется Kestrel.</span><span class="sxs-lookup"><span data-stu-id="56329-111">Kestrel is generally recommended for best performance.</span></span> <span data-ttu-id="56329-112">HTTP.sys можно использовать в сценариях, где приложение имеет доступ к Интернету и необходимые возможности поддерживаются HTTP.sys, но не Kestrel.</span><span class="sxs-lookup"><span data-stu-id="56329-112">HTTP.sys can be used in scenarios where the app is exposed to the Internet and required capabilities are supported by HTTP.sys but not Kestrel.</span></span>

<span data-ttu-id="56329-113">Kestrel не имеет эквивалента модулям IIS (хотя приложения, размещенные в IIS, по-прежнему могут использовать преимущества модулей IIS).</span><span class="sxs-lookup"><span data-stu-id="56329-113">Kestrel does not have an equivalent to IIS modules (though apps hosted in IIS can still take advantage of IIS modules).</span></span> <span data-ttu-id="56329-114">Для достижения эквивалентного поведения обычно используется [промежуточный](/aspnet/core/fundamentals/middleware/) слой, настроенный в самом приложении ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="56329-114">To achieve equivalent behavior, [middleware](/aspnet/core/fundamentals/middleware/) configured in the ASP.NET Core app itself is typically used.</span></span>

## <a name="references"></a><span data-ttu-id="56329-115">Ссылки</span><span class="sxs-lookup"><span data-stu-id="56329-115">References</span></span>

- [<span data-ttu-id="56329-116">Модули IIS</span><span class="sxs-lookup"><span data-stu-id="56329-116">IIS Modules</span></span>](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [<span data-ttu-id="56329-117">ПО промежуточного слоя ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56329-117">ASP.NET Core Middleware</span></span>](/aspnet/core/fundamentals/middleware/)
- [<span data-ttu-id="56329-118">Серверы ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56329-118">ASP.NET Core Servers</span></span>](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
><span data-ttu-id="56329-119">[Назад](app-startup-differences.md)
>[Вперед](serving-static-files.md)</span><span class="sxs-lookup"><span data-stu-id="56329-119">[Previous](app-startup-differences.md)
[Next](serving-static-files.md)</span></span>
