---
title: 'Критическое изменение. Blazor: Функция ProtectedBrowserStorage перемещена на общую платформу'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Функция ProtectedBrowserStorage перемещена на общую платформу
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 36ba6c16ac970aa8acb0d0faab42b151addae888
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497844"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Blazor: Функция ProtectedBrowserStorage перемещена на общую платформу

В ASP.NET Core 5.0 RC2 функция `ProtectedBrowserStorage` перемещена в общую платформу ASP.NET Core.

## <a name="version-introduced"></a>Представленная версия

5.0 RC2

## <a name="old-behavior"></a>Старое поведение

В ASP.NET Core 5.0 предварительной версии 8 эта функция доступна в составе пакета [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions), но ее можно использовать только в Blazor WebAssembly.

В ASP.NET Core 5.0 RC1 эта функция доступна как часть пакета [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage), который ссылается на общую платформу `Microsoft.AspNetCore.App`.

## <a name="new-behavior"></a>Новое поведение

В ASP.NET Core 5.0 RC2 ссылка на пакет NuGet больше не требуется для обращения к этой функции и ее использования.

## <a name="reason-for-change"></a>Причина изменения

Переход на общую платформу больше соответствует ожиданиям клиентов.

## <a name="recommended-action"></a>Рекомендованное действие

При обновлении с ASP.NET Core 5.0 RC1 выполните следующие действия:

1. удалите ссылку на пакет `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` из проекта;
1. Замените `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` на `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. удалите вызов `AddProtectedBrowserStorage` из класса `Startup`.

При обновлении с ASP.NET Core 5.0 предварительной версии 8 выполните следующие действия:

1. удалите ссылку на пакет `Microsoft.AspNetCore.Components.Web.Extensions` из проекта;
1. Замените `using Microsoft.AspNetCore.Components.Web.Extensions;` на `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. удалите вызов `AddProtectedBrowserStorage` из класса `Startup`.

## <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
