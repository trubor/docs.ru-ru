---
title: Перенос крупных решений в ASP.NET Core
description: Рассмотрим, как перенести крупные приложения ASP.NET MVC в ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401727"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a><span data-ttu-id="68826-103">Перенос крупных решений в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="68826-103">Migrate large solutions to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="68826-104">Для переноса больших решений из платформа .NET Framework в .NET Core требуется определенное планирование.</span><span class="sxs-lookup"><span data-stu-id="68826-104">Migrating large solutions from .NET Framework to .NET Core requires some planning.</span></span> <span data-ttu-id="68826-105">Зависимости должны быть перенесены или обновлены до проектов, зависящих от них.</span><span class="sxs-lookup"><span data-stu-id="68826-105">Dependencies must be migrated or updated before the projects that depend on them.</span></span> <span data-ttu-id="68826-106">Существуют средства, которые могут определить зависимости и предложить помощь при переходе на .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68826-106">There are tools that can identify dependencies and offer help with migrating to .NET Core.</span></span> <span data-ttu-id="68826-107">В зависимости от приложения, его области действия и текущих шаблонов использования при миграции могут применяться различные стратегии.</span><span class="sxs-lookup"><span data-stu-id="68826-107">Depending on the app, its scope, and current usage patterns, different strategies may be employed when migrating.</span></span> <span data-ttu-id="68826-108">Переносите ли вы все это одновременно или со временем параллельно с текущей системой?</span><span class="sxs-lookup"><span data-stu-id="68826-108">Do you migrate it all at once, or over time, side-by-side with the current system?</span></span> <span data-ttu-id="68826-109">Вы переносите текущую систему в новую, а затем постепенно заменяете ее функциональность?</span><span class="sxs-lookup"><span data-stu-id="68826-109">Do you wrap the current system in the new one, and incrementally replace its functionality?</span></span>

<span data-ttu-id="68826-110">В этой главе вы узнаете, как создать план миграции для большого решения, как использовать средства для помощи в миграции, а также некоторые стратегии, которые следует учитывать при миграции.</span><span class="sxs-lookup"><span data-stu-id="68826-110">In this chapter, you'll learn how create a migration plan for a large solution, how to use tools to help with the migration, and some strategies to consider for the migration itself.</span></span>

## <a name="references"></a><span data-ttu-id="68826-111">Ссылки</span><span class="sxs-lookup"><span data-stu-id="68826-111">References</span></span>

- [<span data-ttu-id="68826-112">Какие разделы важны для переноса больших приложений MVC и веб-API в .NET Core?</span><span class="sxs-lookup"><span data-stu-id="68826-112">What topics are important to migrating large MVC and Web API apps to .NET Core?</span></span>](https://twitter.com/ardalis/status/1313669040859217921)
- [<span data-ttu-id="68826-113">Перенос кода в .NET Core из .NET Framework</span><span class="sxs-lookup"><span data-stu-id="68826-113">Porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="68826-114">[Назад](testing-differences.md)
>[Вперед](identify-migration-sequence.md)</span><span class="sxs-lookup"><span data-stu-id="68826-114">[Previous](testing-differences.md)
[Next](identify-migration-sequence.md)</span></span>
