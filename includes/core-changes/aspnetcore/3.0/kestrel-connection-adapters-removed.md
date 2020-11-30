---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032801"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="c9e76-101">Kestrel. Адаптеры подключений удалены</span><span class="sxs-lookup"><span data-stu-id="c9e76-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="c9e76-102">В рамках переноса API pubternal в `public` концепция `IConnectionAdapter` была удалена из Kestrel.</span><span class="sxs-lookup"><span data-stu-id="c9e76-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="c9e76-103">Адаптеры подключений заменяются соответствующим ПО промежуточного слоя, которое похоже на ПО промежуточного слоя HTTP в конвейере ASP.NET Core, но для подключений более низкого уровня.</span><span class="sxs-lookup"><span data-stu-id="c9e76-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="c9e76-104">Журналы подключений и HTTPS перемещены из адаптеров соединений в соответствующее ПО промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="c9e76-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="c9e76-105">Эти методы расширения должны и дальше работать без проблем, но детали реализации изменились.</span><span class="sxs-lookup"><span data-stu-id="c9e76-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="c9e76-106">Подробную информацию см. на странице [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="c9e76-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="c9e76-107">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="c9e76-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c9e76-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c9e76-108">Version introduced</span></span>

<span data-ttu-id="c9e76-109">3.0</span><span class="sxs-lookup"><span data-stu-id="c9e76-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c9e76-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="c9e76-110">Old behavior</span></span>

<span data-ttu-id="c9e76-111">Компоненты расширяемости Kestrel были созданы с помощью `IConnectionAdapter`.</span><span class="sxs-lookup"><span data-stu-id="c9e76-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c9e76-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="c9e76-112">New behavior</span></span>

<span data-ttu-id="c9e76-113">Компоненты расширяемости Kestrel созданы с помощью [ПО промежуточного слоя](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="c9e76-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c9e76-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c9e76-114">Reason for change</span></span>

<span data-ttu-id="c9e76-115">Это изменение предназначено для обеспечения более гибкой архитектуры расширяемости.</span><span class="sxs-lookup"><span data-stu-id="c9e76-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c9e76-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c9e76-116">Recommended action</span></span>

<span data-ttu-id="c9e76-117">Преобразуйте все реализации `IConnectionAdapter`, чтобы [использовать новый шаблон ПО промежуточного слоя](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="c9e76-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="c9e76-118">Категория</span><span class="sxs-lookup"><span data-stu-id="c9e76-118">Category</span></span>

<span data-ttu-id="c9e76-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c9e76-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c9e76-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c9e76-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
