---
title: Критическое изменение. Атрибуты OSPlatform переименованы или удалены
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где атрибуты платформы ОС, появившиеся в предварительной версии, были удалены или переименованы.
ms.date: 11/01/2020
ms.openlocfilehash: 118c5360eb02c1b4d57fccbd3b2cfdeff0b9fe12
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257262"
---
# <a name="osplatform-attributes-renamed-or-removed"></a>Атрибуты OSPlatform переименованы или удалены

Следующие атрибуты, появившиеся в предварительной версии 8 .NET 5, были удалены или переименованы: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute` и `ObsoletedInOSPlatformAttribute`.

## <a name="change-description"></a>Описание изменений

В предварительной версии 8 .NET 5 в пространстве имен <xref:System.Runtime.Versioning> появились следующие атрибуты:

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

Если в предварительной версии 8 .NET 5 проект предназначен для использования в конкретной ОС .NET 5 с помощью [моникера целевой платформы](../../../../standard/frameworks.md), например `net5.0-windows`, сборка добавляет атрибут `System.Runtime.Versioning.MinimumOSPlatformAttribute` уровня сборки.

В .NET 5 RC1 атрибут `ObsoletedInOSPlatformAttribute` был удален, а атрибуты `MinimumOSPlatformAttribute` и `RemovedInOSPlatformAttribute` переименованы следующим образом.

| Имя предварительной версии 8 | Имя RC1 и более поздних версий |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

Если в .NET 5 RC1 и более поздних версиях проект предназначен для использования в конкретной ОС .NET 5 с помощью [моникера целевой платформы](../../../../standard/frameworks.md), например `net5.0-windows`, сборка добавляет атрибут <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> уровня сборки.

## <a name="reason-for-change"></a>Причина изменения

В предварительной версии 8 .NET 5 в <xref:System.Runtime.Versioning> появились атрибуты для указания поддерживаемых платформ для API-интерфейсов. [Анализатор совместимости платформ](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) использует эти атрибуты для создания предупреждений сборки, когда интерфейсы API, зависящие от платформы, работают на платформах, их не поддерживающих.

В .NET 5 RC1 в анализатор совместимости платформ была добавлена дополнительная возможность исключения платформы. Эта функция позволяет помечать API-интерфейсы как полностью не поддерживаемые на платформах ОС. Она предлагает изменить атрибуты или использовать более подходящие имена. `ObsoletedInOSPlatformAttribute` был удален, так как он больше не требуется.

## <a name="version-introduced"></a>Представленная версия

5.0 (RC1)

## <a name="recommended-action"></a>Рекомендованное действие

При изменении целевой платформы проекта с предварительной версии 8 .NET 5 на .NET 5 RC1 могут возникать ошибки сборки или времени выполнения. Например, переименование `MinimumOSPlatformAttribute`, скорее всего, приведет к появлению ошибок, поскольку атрибут применяется к сборкам для конкретных платформ во время сборки, а старые артефакты сборки по-прежнему ссылаются на старое имя API.

Примеры ошибок во время сборки:

- **Ошибка CS0246. Не удалось найти тип или имя пространства имен "MinimumOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**
- **Ошибка CS0246. Не удалось найти тип или имя пространства имен "RemovedInOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**
- **Ошибка CS0246. Не удалось найти тип или имя пространства имен "ObsoletedInOSPlatformAttribute" (возможно, отсутствует директива using или ссылка на сборку).**

Пример ошибки во время выполнения:

**Необработанное исключение. System.TypeLoadException: Не удалось загрузить тип "System.Runtime.Versioning.MinimumOSPlatformAttribute"из сборки "System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".**

Чтобы устранить эти ошибки, выполните следующие действия.

- Обновите все ссылки `MinimumOSPlatformAttribute` до <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.
- Обновите все ссылки `RemovedInOSPlatformAttribute` до <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.
- Удалите все ссылки на `ObsoletedInOSPlatformAttribute`.
- Перестройте проект (или выполните очистку и сборку), чтобы удалить старые артефакты сборки.

## <a name="affected-apis"></a>Затронутые API

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
