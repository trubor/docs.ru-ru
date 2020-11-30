---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032884"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="3c448-101">SignalR. Имя пакета клиента JavaScript изменено</span><span class="sxs-lookup"><span data-stu-id="3c448-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="3c448-102">В ASP.NET Core 3.0 (предварительная версия 7) имя клиентского пакета JavaScript для SignalR изменилось с `@aspnet/signalr` на `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="3c448-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="3c448-103">Изменение имени отражает тот факт, что SignalR используется не только в приложениях ASP.NET Core благодаря поддержке Службы Azure SignalR.</span><span class="sxs-lookup"><span data-stu-id="3c448-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="3c448-104">Чтобы отреагировать на это изменение, измените ссылки в файлах *package.JSON*, а также инструкциях `require` и `import` ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="3c448-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="3c448-105">Это переименование не повлияет на API.</span><span class="sxs-lookup"><span data-stu-id="3c448-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="3c448-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="3c448-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c448-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3c448-107">Version introduced</span></span>

<span data-ttu-id="3c448-108">3.0</span><span class="sxs-lookup"><span data-stu-id="3c448-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3c448-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="3c448-109">Old behavior</span></span>

<span data-ttu-id="3c448-110">Пакет клиента назывался `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="3c448-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3c448-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="3c448-111">New behavior</span></span>

<span data-ttu-id="3c448-112">Пакет клиента называется `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="3c448-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3c448-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="3c448-113">Reason for change</span></span>

<span data-ttu-id="3c448-114">Изменение имени отражает тот факт, что SignalR используется не только в приложениях ASP.NET Core благодаря поддержке Службы Azure SignalR.</span><span class="sxs-lookup"><span data-stu-id="3c448-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c448-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="3c448-115">Recommended action</span></span>

<span data-ttu-id="3c448-116">Переключитесь на новый пакет `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="3c448-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="3c448-117">Категория</span><span class="sxs-lookup"><span data-stu-id="3c448-117">Category</span></span>

<span data-ttu-id="3c448-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3c448-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c448-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3c448-119">Affected APIs</span></span>

<span data-ttu-id="3c448-120">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="3c448-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
