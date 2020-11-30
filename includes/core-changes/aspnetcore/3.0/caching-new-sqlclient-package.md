---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032726"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="8d3d2-101">Кэширование. Microsoft.Extensions.Caching.SqlServer использует новый пакет SqlClient</span><span class="sxs-lookup"><span data-stu-id="8d3d2-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="8d3d2-102">Пакет `Microsoft.Extensions.Caching.SqlServer` будет использовать новый пакет `Microsoft.Data.SqlClient` вместо пакета `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="8d3d2-103">Это изменение может привести к незначительным критическим изменениям в поведении.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="8d3d2-104">См. [обзор Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="8d3d2-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8d3d2-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8d3d2-105">Version introduced</span></span>

<span data-ttu-id="8d3d2-106">3.0</span><span class="sxs-lookup"><span data-stu-id="8d3d2-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8d3d2-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="8d3d2-107">Old behavior</span></span>

<span data-ttu-id="8d3d2-108">Пакет `Microsoft.Extensions.Caching.SqlServer` использовал пакет `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8d3d2-109">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="8d3d2-109">New behavior</span></span>

<span data-ttu-id="8d3d2-110">`Microsoft.Extensions.Caching.SqlServer` теперь использует пакет `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8d3d2-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8d3d2-111">Reason for change</span></span>

<span data-ttu-id="8d3d2-112">`Microsoft.Data.SqlClient` — это новый пакет, созданный на основе `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="8d3d2-113">С этого момента в нем будут поддерживаться все новые функции.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8d3d2-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8d3d2-114">Recommended action</span></span>

<span data-ttu-id="8d3d2-115">Клиентам не нужно беспокоиться об этом критическом изменении, если только они не использовали типы, возвращаемые пакетом `Microsoft.Extensions.Caching.SqlServer` и приводимые к типам `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="8d3d2-116">Например, при приведении `DbConnection` к [старому типу SqlConnection](xref:System.Data.SqlClient.SqlConnection), нужно будет изменить приведение на новый тип `Microsoft.Data.SqlClient.SqlConnection`.</span><span class="sxs-lookup"><span data-stu-id="8d3d2-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="8d3d2-117">Категория</span><span class="sxs-lookup"><span data-stu-id="8d3d2-117">Category</span></span>

<span data-ttu-id="8d3d2-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d3d2-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d3d2-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8d3d2-119">Affected APIs</span></span>

<span data-ttu-id="8d3d2-120">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="8d3d2-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
