---
title: Критические изменения MSBuild
description: В этой статье приведен список критических изменений в MSBuild для .NET Core 2.1–3.1.
ms.date: 02/22/2021
ms.openlocfilehash: 03fcd9807a83c4f679dc659b009c857e351b9b2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105647"
---
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a><span data-ttu-id="50420-103">Критические изменения MSBuild в .NET Core 2.1–3.1</span><span class="sxs-lookup"><span data-stu-id="50420-103">MSBuild breaking changes in .NET Core 2.1 - 3.1</span></span>

<span data-ttu-id="50420-104">На этой странице описаны следующие критические изменения:</span><span class="sxs-lookup"><span data-stu-id="50420-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="50420-105">Критическое изменение</span><span class="sxs-lookup"><span data-stu-id="50420-105">Breaking change</span></span> | <span data-ttu-id="50420-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="50420-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="50420-107">Сборки времени разработки возвращают только ссылки на пакеты верхнего уровня</span><span class="sxs-lookup"><span data-stu-id="50420-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="50420-108">3.1</span><span class="sxs-lookup"><span data-stu-id="50420-108">3.1</span></span> |
| [<span data-ttu-id="50420-109">Изменение имен файлов манифеста ресурса</span><span class="sxs-lookup"><span data-stu-id="50420-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="50420-110">3.0</span><span class="sxs-lookup"><span data-stu-id="50420-110">3.0</span></span> |
| [<span data-ttu-id="50420-111">Средства проекта теперь включены в пакет SDK</span><span class="sxs-lookup"><span data-stu-id="50420-111">Project tools now included in SDK</span></span>](#project-tools-now-included-in-sdk) | <span data-ttu-id="50420-112">2.1</span><span class="sxs-lookup"><span data-stu-id="50420-112">2.1</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="50420-113">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="50420-113">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="50420-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="50420-114">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="50420-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="50420-115">.NET Core 2.1</span></span>

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
