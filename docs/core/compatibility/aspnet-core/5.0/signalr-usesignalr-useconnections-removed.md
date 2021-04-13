---
title: Критическое изменение. SignalR. Методы UseSignalR и UseConnections удалены
description: Сведения о критическом изменении в ASP.NET Core 5.0 — SignalR. Методы UseSignalR и UseConnections удалены
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3b6e301ee8414a503f7b3697d3b1a01174a1cefb
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497103"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR. Методы UseSignalR и UseConnections удалены

В ASP.NET Core 3.0, SignalR приняла построение маршрутов конечных точек. В рамках этого изменения <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, а также некоторые связанные методы были помечены как устаревшие. В ASP.NET Core 5.0 эти устаревшие методы удалены. Полный список методов см. в разделе [Затронутые API](#affected-apis).

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).

## <a name="version-introduced"></a>Представленная версия

5.0 Предварительная версия 3

## <a name="old-behavior"></a>Старое поведение

Концентраторы SignalR и обработчики соединений можно зарегистрировать в конвейере ПО промежуточного слоя с помощью методов `UseSignalR` или `UseConnections`.

## <a name="new-behavior"></a>Новое поведение

Концентраторы SignalR и обработчики соединений следует зарегистрировать в <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> с помощью методов расширения <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> и <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> в <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.

## <a name="reason-for-change"></a>Причина изменения

Старые методы имели пользовательскую логику построения маршрутов, которая не взаимодействовала с другими компонентами построения маршрутов в ASP.NET Core. В ASP.NET Core 3.0 появилась новая система построения маршрутов общего назначения, называемая построением маршрутов конечных точек. Служба SignalR включила построение маршрутов конечных точек для взаимодействия с другими компонентами построения маршрутов. Переключение на эту модель позволяет пользователям реализовать все преимущества построения маршрутов конечных точек. Следовательно, старые методы были удалены.

## <a name="recommended-action"></a>Рекомендованное действие

Удалите код, который вызывает `UseSignalR` или `UseConnections` из метода `Startup.Configure` проекта. Замените его вызовами `MapHub` или `MapConnectionHandler`соответственно, в теле вызова `UseEndpoints`. Пример:

**Старый код:**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Новый код:**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

В целом, предыдущие вызовы `MapHub` и `MapConnectionHandler` можно передать непосредственно из тела `UseSignalR` и `UseConnections` в `UseEndpoints` с минимальными изменениями.

## <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
