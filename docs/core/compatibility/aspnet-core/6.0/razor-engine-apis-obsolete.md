---
title: Критическое изменение. Razor. Интерфейсы API RazorEngine помечены как устаревшие
description: Сведения о критическом изменении в ASP.NET Core 6.0 — Razor. Интерфейсы API RazorEngine помечены как устаревшие
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: a312fb2fda6245e529d59d82b72ffe64ae6d6ff5
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255107"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a>Razor. Интерфейсы API RazorEngine помечены как устаревшие

Типы, связанные с типом <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> в Blazor, помечены как устаревшие.

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0 (предварительная версия 1)

## <a name="old-behavior"></a>Старое поведение

Интерфейсы API `RazorEngine` не являются устаревшими.

## <a name="new-behavior"></a>Новое поведение

API `RazorEngine` являются устаревшими.

## <a name="reason-for-change"></a>Причина изменения

Вместо типа `RazorEngine` теперь следует использовать тип <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.

## <a name="recommended-action"></a>Рекомендованное действие

Перенос исходного кода из типа `RazorEngine` в тип `RazorProjectEngine`.

## <a name="affected-apis"></a>Затронутые API

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register`
- `T:Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder`

-->
