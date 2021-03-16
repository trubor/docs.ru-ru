---
title: Критическое изменение. NegotiateStream и SslStream поддерживают последовательные операции Begin
description: Сведения о критическом изменении в .NET 5, где случаи ошибок в потоках безопасности обрабатываются по-разному, а последовательные вызовы BeginAuthenticateAsServer или BeginAuthenticateAsClient больше не завершаются сбоями.
ms.date: 10/18/2020
ms.openlocfilehash: 5c042be01873849cc154111a31fc007521508c7b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256443"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream и SslStream поддерживают последовательные операции Begin

Случаи ошибок в потоках безопасности обрабатываются по-разному, а последовательные вызовы `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` больше не завершаются сбоями.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET последовательный вызов `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` без предварительного вызова `EndAuthenticateAsServer` или `EndAuthenticateAsClient` приводит к возникновению исключения <xref:System.NotSupportedException>. Начиная с версии .NET 5 последовательные вызовы `BeginAuthenticateAsServer` или `BeginAuthenticateAsClient` больше не приводят к возникновению исключения <xref:System.NotSupportedException>, так как эти API поддерживаются реализацией на основе <xref:System.Threading.Tasks.Task>.

## <a name="reason-for-change"></a>Причина изменения

Переход внутренней реализации от модели асинхронного программирования (APM) к <xref:System.Threading.Tasks.Task> позволяет повысить производительность и снизить сложность кода.

## <a name="recommended-action"></a>Рекомендованное действие

От разработчика не требуется никаких действий.

## <a name="affected-apis"></a>Затронутые API

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
