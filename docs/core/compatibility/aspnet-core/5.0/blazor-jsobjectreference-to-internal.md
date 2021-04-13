---
title: 'Критическое изменение. Blazor: Типы JSObjectReference и JSInProcessObjectReference изменены на internal'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Типы JSObjectReference и JSInProcessObjectReference изменены на internal
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 44e4c902ff22e18fa9ab8b484952082e5b81be94
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497857"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor: Типы JSObjectReference и JSInProcessObjectReference изменены на internal

Новые типы `Microsoft.JSInterop.JSObjectReference` и `Microsoft.JSInterop.JSInProcessObjectReference`, появившиеся в ASP.NET Core 5.0 RC1, помечены как `internal`.

## <a name="version-introduced"></a>Представленная версия

5.0 RC2

## <a name="old-behavior"></a>Старое поведение

`JSObjectReference` можно получить из вызова взаимодействия JavaScript через `IJSRuntime`. Пример:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a>Новое поведение

`JSObjectReference` использует модификатор доступа [internal](../../../../csharp/language-reference/keywords/internal.md). Вместо этого необходимо использовать интерфейс `public` `IJSObjectReference`. Пример:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` также помечен как `internal` и изменен на `IJSInProcessObjectReference`.

## <a name="reason-for-change"></a>Причина изменения

Это изменение делает функцию взаимодействия JavaScript более совместимой с другими шаблонами в Blazor. `IJSObjectReference` можно использовать как `IJSRuntime` в контексте назначения и методов и расширения.

## <a name="recommended-action"></a>Рекомендованное действие

Измените вхождения `JSObjectReference` и `JSInProcessObjectReference` на `IJSObjectReference` и `IJSInProcessObjectReference`соответственно.

## <a name="affected-apis"></a>Затронутые API

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
