---
title: Различия архитектуры ASP.NET MVC и ASP.NET Core
description: Изучите архитектурные различия между ASP.NET и ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 96477f2393482380eee9891e9b2dbbb6445e15bd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401822"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="e8f2a-103">Различия архитектуры ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e8f2a-103">Architectural differences between ASP.NET MVC and ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e8f2a-104">Существует множество архитектурных различий между ASP.NET MVC на платформа .NET Framework и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-104">There are many architectural differences between ASP.NET MVC on .NET Framework and ASP.NET Core.</span></span> <span data-ttu-id="e8f2a-105">Важно иметь общее представление об этих различиях, так как команды оценивают работу, связанную с переносом приложений ASP.NET MVC в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-105">It's important to have a broad understanding of these differences as teams evaluate the work involved in porting their ASP.NET MVC apps to ASP.NET Core.</span></span> <span data-ttu-id="e8f2a-106">В этой главе рассматриваются все способы, в которых ASP.NET Core существенно отличаются от ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-106">This chapter looks at each of the ways in which ASP.NET Core differs substantially from ASP.NET MVC.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e8f2a-107">Критические изменения</span><span class="sxs-lookup"><span data-stu-id="e8f2a-107">Breaking changes</span></span>

<span data-ttu-id="e8f2a-108">.NET Core — это кросс-платформенная перезапись платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-108">.NET Core is a cross-platform rewrite of .NET Framework.</span></span> <span data-ttu-id="e8f2a-109">[Между двумя платформами существует много критических изменений](../../core/compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="e8f2a-109">There are many [breaking changes between the two frameworks](../../core/compatibility/fx-core.md).</span></span> <span data-ttu-id="e8f2a-110">В следующих разделах приведены определенные различия между разработкой и ASP.NET приложений MVC и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-110">The following sections identify specific differences between how ASP.NET MVC and ASP.NET Core apps are designed and developed.</span></span> <span data-ttu-id="e8f2a-111">Также ознакомьтесь с документацией, чтобы определить, какие библиотеки платформы вы используете, которые, возможно, потребуется изменить.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-111">Take care to also examine the documentation to determine which framework libraries you're using that may need to change.</span></span> <span data-ttu-id="e8f2a-112">Во многих случаях существует заменяющий пакет NuGet для заполнения всех пропусков, оставшихся между платформа .NET Framework и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-112">In many cases, a replacement NuGet package exists to fill in any gaps left between .NET Framework and .NET Core.</span></span> <span data-ttu-id="e8f2a-113">В редких случаях может потребоваться найти стороннее решение или реализовать новый пользовательский код для устранения несовместимости.</span><span class="sxs-lookup"><span data-stu-id="e8f2a-113">In rare cases, you may need to find a third-party solution or implement new custom code to address incompatibilities.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e8f2a-114">[Назад](additional-migration-resources.md)
>[Вперед](app-startup-differences.md)</span><span class="sxs-lookup"><span data-stu-id="e8f2a-114">[Previous](additional-migration-resources.md)
[Next](app-startup-differences.md)</span></span>
