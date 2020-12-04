---
title: Критическое изменение. NegotiateStream и SslStream поддерживают последовательные операции Begin
description: Сведения о критическом изменении в .NET 5.0, где случаи ошибок в потоках безопасности обрабатываются по-разному, а последовательные вызовы BeginAuthenticateAsServer или BeginAuthenticateAsClient больше не завершаются сбоями.
ms.date: 10/18/2020
ms.openlocfilehash: e0226d0f5586efca050ca3497ca1490fa21fd943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759689"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="d01f0-103">NegotiateStream и SslStream поддерживают последовательные операции Begin</span><span class="sxs-lookup"><span data-stu-id="d01f0-103">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="d01f0-104">Случаи ошибок в потоках безопасности обрабатываются по-разному, а последовательные вызовы `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` больше не завершаются сбоями.</span><span class="sxs-lookup"><span data-stu-id="d01f0-104">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d01f0-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d01f0-105">Version introduced</span></span>

<span data-ttu-id="d01f0-106">5.0</span><span class="sxs-lookup"><span data-stu-id="d01f0-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="d01f0-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d01f0-107">Change description</span></span>

<span data-ttu-id="d01f0-108">В предыдущих версиях .NET последовательный вызов `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` без предварительного вызова `EndAuthenticateAsServer` или `EndAuthenticateAsClient` приводит к возникновению исключения <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="d01f0-108">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="d01f0-109">Начиная с версии .NET 5.0 последовательные вызовы `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` больше не приводят к возникновению исключения <xref:System.NotSupportedException>, так как эти API поддерживаются реализацией на основе <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d01f0-109">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d01f0-110">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d01f0-110">Reason for change</span></span>

<span data-ttu-id="d01f0-111">Переход внутренней реализации от модели асинхронного программирования (APM) к <xref:System.Threading.Tasks.Task> позволяет повысить производительность и снизить сложность кода.</span><span class="sxs-lookup"><span data-stu-id="d01f0-111">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d01f0-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d01f0-112">Recommended action</span></span>

<span data-ttu-id="d01f0-113">От разработчика не требуется никаких действий.</span><span class="sxs-lookup"><span data-stu-id="d01f0-113">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d01f0-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d01f0-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
