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
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="f3aca-103">Socket.LocalEndPoint обновляется после вызова SendToAsync</span><span class="sxs-lookup"><span data-stu-id="f3aca-103">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="f3aca-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> теперь обновляет значение свойства <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>, используя локальный адрес сокета.</span><span class="sxs-lookup"><span data-stu-id="f3aca-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f3aca-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f3aca-105">Version introduced</span></span>

<span data-ttu-id="f3aca-106">5.0</span><span class="sxs-lookup"><span data-stu-id="f3aca-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="f3aca-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f3aca-107">Change description</span></span>

<span data-ttu-id="f3aca-108">В предыдущих версиях .NET <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> не изменяет значение свойства <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> для экземпляра сокета.</span><span class="sxs-lookup"><span data-stu-id="f3aca-108">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="f3aca-109">Начиная с .NET 5 при успешном завершении <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> в качестве значения <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> устанавливается локальный адрес неявно привязанного сокета.</span><span class="sxs-lookup"><span data-stu-id="f3aca-109">Starting in .NET 5, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="f3aca-110">Это согласуется с поведением <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> и <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span><span class="sxs-lookup"><span data-stu-id="f3aca-110">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f3aca-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="f3aca-111">Reason for change</span></span>

<span data-ttu-id="f3aca-112">Это изменение позволяет [исправить ошибку](https://github.com/dotnet/runtime/issues/915) и обеспечивает согласованность поведения в вариантах `SendTo`.</span><span class="sxs-lookup"><span data-stu-id="f3aca-112">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f3aca-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f3aca-113">Recommended action</span></span>

<span data-ttu-id="f3aca-114">Измените любой код, в котором предполагается, что <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> не изменяет значение <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3aca-114">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f3aca-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f3aca-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
