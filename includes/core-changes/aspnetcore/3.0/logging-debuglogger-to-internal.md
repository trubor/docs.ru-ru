---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032822"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="d0353-101">Ведение журнала: класс DebugLogger стал внутренним</span><span class="sxs-lookup"><span data-stu-id="d0353-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="d0353-102">До версии ASP.NET Core 3.0 модификатор доступа `DebugLogger` имел атрибут `public`.</span><span class="sxs-lookup"><span data-stu-id="d0353-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="d0353-103">В ASP.NET Core 3.0 модификатор доступа изменен на `internal`.</span><span class="sxs-lookup"><span data-stu-id="d0353-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d0353-104">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d0353-104">Version introduced</span></span>

<span data-ttu-id="d0353-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d0353-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d0353-106">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d0353-106">Reason for change</span></span>

<span data-ttu-id="d0353-107">Изменение реализуется с такой целью:</span><span class="sxs-lookup"><span data-stu-id="d0353-107">The change is being made to:</span></span>

* <span data-ttu-id="d0353-108">обеспечение согласованности с другими реализациями средства ведения журналов, например `ConsoleLogger`;</span><span class="sxs-lookup"><span data-stu-id="d0353-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="d0353-109">уменьшение контактной зоны API.</span><span class="sxs-lookup"><span data-stu-id="d0353-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d0353-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d0353-110">Recommended action</span></span>

<span data-ttu-id="d0353-111">Используйте метод расширения <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`, чтобы включить ведение журналов отладки.</span><span class="sxs-lookup"><span data-stu-id="d0353-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="d0353-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> также имеет атрибут `public` на тот случай, если потребуется зарегистрировать службу вручную.</span><span class="sxs-lookup"><span data-stu-id="d0353-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="d0353-113">Категория</span><span class="sxs-lookup"><span data-stu-id="d0353-113">Category</span></span>

<span data-ttu-id="d0353-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d0353-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d0353-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d0353-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
