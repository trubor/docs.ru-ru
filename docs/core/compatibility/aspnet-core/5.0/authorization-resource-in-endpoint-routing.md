---
title: Критическое изменение. Авторизация. Для маршрутизации конечных точек используется ресурс HttpContext
description: Сведения о критическом изменении в ASP.NET Core 5.0 — аутентификация. Для маршрутизации конечных точек используется ресурс HttpContext
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 90f15bcbc1fb05e67b1c6d7494938eebac7718fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497887"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>Авторизация. Для маршрутизации конечных точек используется ресурс HttpContext

При маршрутизации конечных точек в ASP.NET Core 3.1 в качестве ресурса для авторизации используется конечная точка. Такой подход не обеспечивал доступ к данным маршрута (<xref:Microsoft.AspNetCore.Routing.RouteData>). Ранее в MVC передавался ресурс <xref:Microsoft.AspNetCore.Http.HttpContext>, который обеспечивал доступ одновременно к конечной точке (<xref:Microsoft.AspNetCore.Http.Endpoint>) и данным маршрута. Это изменение гарантирует, что в качестве ресурса для авторизации всегда будет передаваться `HttpContext`.

## <a name="version-introduced"></a>Представленная версия

5.0 (предварительная версия 7)

## <a name="old-behavior"></a>Старое поведение

При использовании маршрутизации конечной точки и ПО промежуточного слоя авторизации (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) или атрибутов [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) в качестве ресурса для авторизации передается соответствующая конечная точка.

## <a name="new-behavior"></a>Новое поведение

При маршрутизации конечной точки для авторизации передается `HttpContext`.

## <a name="reason-for-change"></a>Причина изменения

Существует возможность перейти к конечной точке из `HttpContext`. Тем не менее, из конечной точки было невозможно получить информацию, например данные маршрута. Таким образом, утрачивались функциональные возможности из-за маршрутизации без конечной точки.

## <a name="recommended-action"></a>Рекомендованное действие

Если в вашем приложении используется ресурс конечной точки вызовите <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> для `HttpContext`, чтобы сохранить доступ к конечной точке.

В ASP.NET Core 5.0 предварительной версии 8 и более поздних вы можете восстановить поведение предыдущих версий с использованием <xref:System.AppContext.SetSwitch%2A>. Пример:

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
