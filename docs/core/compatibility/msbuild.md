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
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a>Критические изменения MSBuild в .NET Core 2.1–3.1

На этой странице описаны следующие критические изменения:

| Критическое изменение | Представленная версия |
| - | - |
| [Сборки времени разработки возвращают только ссылки на пакеты верхнего уровня](#design-time-builds-only-return-top-level-package-references) | 3.1 |
| [Изменение имен файлов манифеста ресурса](#resource-manifest-file-name-change) | 3.0 |
| [Средства проекта теперь включены в пакет SDK](#project-tools-now-included-in-sdk) | 2.1 |

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
