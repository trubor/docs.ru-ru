---
ms.openlocfilehash: d9489df1ba096109e60d663e3a3f4442d30b2bb1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105475"
---
### <a name="project-tools-now-included-in-sdk"></a>Средства проекта теперь включены в пакет SDK

Пакет SDK для .NET Core 2.1 теперь включает общие средства CLI, и больше не нужно включать в проект ссылки на эти средства.

#### <a name="change-description"></a>Описание изменений

В .NET Core 2.0 проекты ссылаются на внешние инструменты .NET с помощью параметра проекта `<DotNetCliToolReference>`. В .NET Core 2.1 некоторые из этих средств включены в пакет SDK для .NET Core, и этот параметр больше не требуется. Если включить в проект ссылки на эти средства, появится сообщение об ошибке следующего вида: **Средство "Microsoft.EntityFrameworkCore.Tools.DotNet" теперь включено в пакет SDK для .NET Core.**

Средства, которые теперь входят в пакет SDK для .NET Core 2.1:

| Значение \<DotNetCliToolReference>                   | Инструмент                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | [dotnet-watch](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-watch/README.md)               |
| `Microsoft.Extensions.SecretManager.Tools`     | [dotnet-user-secrets](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [dotnet-sql-cache](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [dotnet-ef](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a>Представленная версия

Пакет SDK для .NET Core 2.1.300

#### <a name="recommended-action"></a>Рекомендованное действие

Удалите параметр `<DotNetCliToolReference>` из проекта.

#### <a name="category"></a>Категория

MSBuild

#### <a name="affected-apis"></a>Затронутые API

Н/Д
