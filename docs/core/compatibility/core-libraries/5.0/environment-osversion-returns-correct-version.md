---
title: Критическое изменение. Environment.OSVersion возвращает правильную версию операционной системы
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где Environment.OSVersion возвращает фактическую версию операционной системы, а не, например, ОС, выбранную для совместимости приложений.
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257535"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment.OSVersion возвращает правильную версию операционной системы

<xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы (ОС), а не, например, ту ОС, которая выбрана для совместимости приложений.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает версию ОС, которая может быть неверной, если приложение работает в режиме совместимости Windows. Дополнительные сведения см. в [примечаниях к функции GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks). В macOS <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает базовую версию ядра Darwin.

Начиная с .NET 5 <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы для Windows и macOS.

В следующей таблице приведены различия в поведении.

|  | Предыдущие версии .NET | .NET 5.+ |
|--|------------------------|---------|
| Windows | 6.2.9200.0 | 10.0.19042.0 |
| macOS | 19.6.0.0 | 10.15.7 |

## <a name="reason-for-change"></a>Причина изменения

Пользователи этого свойства предполагают, что оно будет возвращать фактическую версию операционной системы. Большинство приложений .NET не указывают поддерживаемую версию в манифесте приложения и поэтому получают поддерживаемую по умолчанию версию из узла dotnet. В результате оболочка совместимости редко применяется для работающего приложения. Когда Windows выпускает новую версию, а более старый узел dotnet по-прежнему используется, эти приложения могут получить неверную версию ОС. Возврат фактической версии более соответствует ожиданиям разработчиков этого API.

С появлением <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> и <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> в .NET 5 <xref:System.Environment.OSVersion?displayProperty=nameWithType> были изменены для согласованности с Windows и macOS.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Проверьте и протестируйте код, который использует <xref:System.Environment.OSVersion?displayProperty=nameWithType>, чтобы убедиться, что он ведет себя должным образом.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
