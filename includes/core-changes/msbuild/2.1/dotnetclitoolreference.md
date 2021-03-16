---
ms.openlocfilehash: 370c6eb23a50ed388f0b10a5c5f4779ba2a1b144
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102623368"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="2fdad-101">Средства проекта теперь включены в пакет SDK</span><span class="sxs-lookup"><span data-stu-id="2fdad-101">Project tools now included in SDK</span></span>

<span data-ttu-id="2fdad-102">Пакет SDK для .NET Core 2.1 теперь включает общие средства CLI, и больше не нужно включать в проект ссылки на эти средства.</span><span class="sxs-lookup"><span data-stu-id="2fdad-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2fdad-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="2fdad-103">Change description</span></span>

<span data-ttu-id="2fdad-104">В .NET Core 2.0 проекты ссылаются на внешние инструменты .NET с помощью параметра проекта `<DotNetCliToolReference>`.</span><span class="sxs-lookup"><span data-stu-id="2fdad-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="2fdad-105">В .NET Core 2.1 некоторые из этих средств включены в пакет SDK для .NET Core, и этот параметр больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="2fdad-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="2fdad-106">Если включить в проект ссылки на эти средства, появится сообщение об ошибке следующего вида: **Средство "Microsoft.EntityFrameworkCore.Tools.DotNet" теперь включено в пакет SDK для .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="2fdad-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="2fdad-107">Средства, которые теперь входят в пакет SDK для .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="2fdad-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="2fdad-108">Значение \<DotNetCliToolReference></span><span class="sxs-lookup"><span data-stu-id="2fdad-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="2fdad-109">Инструмент</span><span class="sxs-lookup"><span data-stu-id="2fdad-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="2fdad-110">dotnet-user-secrets</span><span class="sxs-lookup"><span data-stu-id="2fdad-110">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="2fdad-111">dotnet-sql-cache</span><span class="sxs-lookup"><span data-stu-id="2fdad-111">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="2fdad-112">dotnet-ef</span><span class="sxs-lookup"><span data-stu-id="2fdad-112">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="2fdad-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="2fdad-113">Version introduced</span></span>

<span data-ttu-id="2fdad-114">Пакет SDK для .NET Core 2.1.300</span><span class="sxs-lookup"><span data-stu-id="2fdad-114">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2fdad-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="2fdad-115">Recommended action</span></span>

<span data-ttu-id="2fdad-116">Удалите параметр `<DotNetCliToolReference>` из проекта.</span><span class="sxs-lookup"><span data-stu-id="2fdad-116">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="2fdad-117">Категория</span><span class="sxs-lookup"><span data-stu-id="2fdad-117">Category</span></span>

<span data-ttu-id="2fdad-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="2fdad-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2fdad-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="2fdad-119">Affected APIs</span></span>

<span data-ttu-id="2fdad-120">Н/Д</span><span class="sxs-lookup"><span data-stu-id="2fdad-120">N/A</span></span>
