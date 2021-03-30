---
ms.openlocfilehash: 49aa98edec8ed1ce35dd501c57aa82e4ca4cf286
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879768"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="7bb70-101">Средства проекта теперь включены в пакет SDK</span><span class="sxs-lookup"><span data-stu-id="7bb70-101">Project tools now included in SDK</span></span>

<span data-ttu-id="7bb70-102">Пакет SDK для .NET Core 2.1 теперь включает общие средства CLI, и больше не нужно включать в проект ссылки на эти средства.</span><span class="sxs-lookup"><span data-stu-id="7bb70-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7bb70-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="7bb70-103">Change description</span></span>

<span data-ttu-id="7bb70-104">В .NET Core 2.0 проекты ссылаются на внешние инструменты .NET с помощью параметра проекта `<DotNetCliToolReference>`.</span><span class="sxs-lookup"><span data-stu-id="7bb70-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="7bb70-105">В .NET Core 2.1 некоторые из этих средств включены в пакет SDK для .NET Core, и этот параметр больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="7bb70-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="7bb70-106">Если включить в проект ссылки на эти средства, появится сообщение об ошибке следующего вида: **Средство "Microsoft.EntityFrameworkCore.Tools.DotNet" теперь включено в пакет SDK для .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="7bb70-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="7bb70-107">Средства, которые теперь входят в пакет SDK для .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="7bb70-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="7bb70-108">Значение \<DotNetCliToolReference></span><span class="sxs-lookup"><span data-stu-id="7bb70-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="7bb70-109">Инструмент</span><span class="sxs-lookup"><span data-stu-id="7bb70-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="7bb70-110">dotnet-user-secrets</span><span class="sxs-lookup"><span data-stu-id="7bb70-110">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="7bb70-111">dotnet-sql-cache</span><span class="sxs-lookup"><span data-stu-id="7bb70-111">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="7bb70-112">dotnet-ef</span><span class="sxs-lookup"><span data-stu-id="7bb70-112">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="7bb70-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7bb70-113">Version introduced</span></span>

<span data-ttu-id="7bb70-114">Пакет SDK для .NET Core 2.1.300</span><span class="sxs-lookup"><span data-stu-id="7bb70-114">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7bb70-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7bb70-115">Recommended action</span></span>

<span data-ttu-id="7bb70-116">Удалите параметр `<DotNetCliToolReference>` из проекта.</span><span class="sxs-lookup"><span data-stu-id="7bb70-116">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="7bb70-117">Категория</span><span class="sxs-lookup"><span data-stu-id="7bb70-117">Category</span></span>

<span data-ttu-id="7bb70-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="7bb70-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7bb70-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7bb70-119">Affected APIs</span></span>

<span data-ttu-id="7bb70-120">Н/Д</span><span class="sxs-lookup"><span data-stu-id="7bb70-120">N/A</span></span>
