---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032790"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="499ba-101">Удостоверение. конструктор SignInManager принимает новый параметр</span><span class="sxs-lookup"><span data-stu-id="499ba-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="499ba-102">Начиная с ASP.NET Core 3.0 в конструктор `SignInManager` был добавлен новый параметр `IUserConfirmation<TUser>`.</span><span class="sxs-lookup"><span data-stu-id="499ba-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="499ba-103">Подробную информацию см. на странице [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="499ba-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="499ba-104">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="499ba-104">Version introduced</span></span>

<span data-ttu-id="499ba-105">3.0</span><span class="sxs-lookup"><span data-stu-id="499ba-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="499ba-106">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="499ba-106">Reason for change</span></span>

<span data-ttu-id="499ba-107">Изменение позволит добавить поддержку новых потоков сообщений электронной почты и подтверждений в удостоверении.</span><span class="sxs-lookup"><span data-stu-id="499ba-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="499ba-108">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="499ba-108">Recommended action</span></span>

<span data-ttu-id="499ba-109">При создании `SignInManager` вручную предоставьте реализацию `IUserConfirmation` или воспользуйтесь реализацией из внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="499ba-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="499ba-110">Категория</span><span class="sxs-lookup"><span data-stu-id="499ba-110">Category</span></span>

<span data-ttu-id="499ba-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="499ba-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="499ba-112">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="499ba-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
