---
title: Критическое изменение. Socket.LocalEndPoint обновляется после вызова SendToAsync
description: Сведения о критическом изменении в .NET 5, где SendToAsync теперь обновляет значение свойства локальной конечной точки, используя локальный адрес сокета.
ms.date: 10/18/2020
ms.openlocfilehash: 4be62f8bf6596cc3531d59f3e65eda005bff778a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256430"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket.LocalEndPoint обновляется после вызова SendToAsync

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> теперь обновляет значение свойства <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>, используя локальный адрес сокета.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> не изменяет значение свойства <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> для экземпляра сокета. Начиная с .NET 5 при успешном завершении <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> в качестве значения <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> устанавливается локальный адрес неявно привязанного сокета. Это согласуется с поведением <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> и <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.

## <a name="reason-for-change"></a>Причина изменения

Это изменение позволяет [исправить ошибку](https://github.com/dotnet/runtime/issues/915) и обеспечивает согласованность поведения в вариантах `SendTo`.

## <a name="recommended-action"></a>Рекомендованное действие

Измените любой код, в котором предполагается, что <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> не изменяет значение <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
