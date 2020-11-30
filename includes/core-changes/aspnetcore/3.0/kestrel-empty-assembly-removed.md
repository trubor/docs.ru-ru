---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032809"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="1df83-101">Kestrel. Удаление пустой сборки HTTPS</span><span class="sxs-lookup"><span data-stu-id="1df83-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="1df83-102">Сборка <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> была удалена.</span><span class="sxs-lookup"><span data-stu-id="1df83-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1df83-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1df83-103">Version introduced</span></span>

<span data-ttu-id="1df83-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1df83-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1df83-105">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="1df83-105">Reason for change</span></span>

<span data-ttu-id="1df83-106">В ASP.NET Core 2.1 содержимое `Microsoft.AspNetCore.Server.Kestrel.Https` перемещено в <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1df83-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="1df83-107">Это изменение выполнено некритическим образом с помощью атрибутов `[TypeForwardedTo]`.</span><span class="sxs-lookup"><span data-stu-id="1df83-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1df83-108">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="1df83-108">Recommended action</span></span>

- <span data-ttu-id="1df83-109">Библиотеки, ссылающиеся на `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0, должны обновить все зависимости ASP.NET Core до версии 2.1 и выше.</span><span class="sxs-lookup"><span data-stu-id="1df83-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="1df83-110">В противном случае они могут прерывать работу при загрузке в приложение ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1df83-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="1df83-111">Приложения и библиотеки, предназначенные для ASP.NET Core версии 2.1 и выше, должны удалять все прямые ссылки на пакет `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet.</span><span class="sxs-lookup"><span data-stu-id="1df83-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="1df83-112">Категория</span><span class="sxs-lookup"><span data-stu-id="1df83-112">Category</span></span>

<span data-ttu-id="1df83-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1df83-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1df83-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1df83-114">Affected APIs</span></span>

<span data-ttu-id="1df83-115">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="1df83-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
