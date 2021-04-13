---
title: 'Критическое изменение: Blazor. Обновлен список поддерживаемых веб-браузеров'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Обновлен список поддерживаемых веб-браузеров
ms.author: scaddie
ms.date: 10/01/2020
no-loc:
- Blazor
- Blazor WebAssembly
- Blazor Server
ms.openlocfilehash: 25566a4b30aaa8484ec4bcf26ab1e8fde6af1279
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497870"
---
# <a name="blazor-updated-browser-support"></a>Blazor: Обновлен список поддерживаемых веб-браузеров

В ASP.NET Core 5.0 появились [новые функции Blazor](https://github.com/dotnet/aspnetcore/issues/21514), некоторые из которых несовместимы со старыми браузерами. Список браузеров, поддерживаемых Blazor в ASP.NET Core 5.0, обновлен соответствующим образом.

Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="old-behavior"></a>Старое поведение

Blazor Server поддерживает Microsoft Internet Explorer 11 с достаточным количеством заполнений. Blazor Server и Blazor WebAssembly также работают в [Microsoft Edge прежних версий](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).

## <a name="new-behavior"></a>Новое поведение

Blazor Server в ASP.NET Core 5.0 не поддерживается в Microsoft Internet Explorer 11. Blazor Server и Blazor WebAssembly не полностью работают в Microsoft Edge прежних версий.

## <a name="reason-for-change"></a>Причина изменения

Новые функции Blazor в ASP.NET Core 5.0 несовместимы с этими старыми браузерами, кроме того, уровень их использования снижается. Дополнительные сведения см. в следующих ресурсах:

* [Поддержка Windows устаревшей версии Microsoft Edge также прекращается 9 марта 2021 г.](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Приложения и службы Microsoft 365 перестанут поддерживать Microsoft Internet Explorer 11 17 августа 2021 г.](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a>Рекомендованное действие

Обновите эти старые браузеры до [нового Microsoft Edge, основанного на Chromium](https://www.microsoft.com/edge). Для приложений Blazor, которым требуется поддержка этих старых браузеров, используйте ASP.NET Core 3.1. Список поддерживаемых браузеров для Blazor в ASP.NET Core 3.1 не изменился и описан в разделе о [поддерживаемых платформах](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).

## <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
