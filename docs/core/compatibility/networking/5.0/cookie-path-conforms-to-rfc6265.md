---
title: Критическое изменение. Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265
description: Узнайте о критическом изменении в .NET 5.0, где алгоритмы обработки путей, определенные в RFC 6265, реализованы для классов cookie и CookieContainer.
ms.date: 08/18/2020
ms.openlocfilehash: 4aea06f434c4bbbef7d94b4b39ff647dd954745e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759701"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="1c4a5-103">Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265</span><span class="sxs-lookup"><span data-stu-id="1c4a5-103">Cookie path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="1c4a5-104">Алгоритмы обработки путей, определенные в [RFC 6265](https://tools.ietf.org/html/rfc6265), реализованы для классов <xref:System.Net.Cookie> и <xref:System.Net.CookieContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c4a5-104">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1c4a5-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c4a5-105">Version introduced</span></span>

<span data-ttu-id="1c4a5-106">5.0</span><span class="sxs-lookup"><span data-stu-id="1c4a5-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="1c4a5-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="1c4a5-107">Change description</span></span>

- <span data-ttu-id="1c4a5-108">Свойство <xref:System.Net.Cookie.Path> больше не должно быть префиксом пути запроса.</span><span class="sxs-lookup"><span data-stu-id="1c4a5-108">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="1c4a5-109">Вычисление значения по умолчанию для <xref:System.Net.Cookie.Path> и алгоритмов сопоставления путей реализовано в RFC 6265 в [разделе 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4).</span><span class="sxs-lookup"><span data-stu-id="1c4a5-109">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1c4a5-110">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="1c4a5-110">Recommended action</span></span>

<span data-ttu-id="1c4a5-111">В большинстве случаев вам не нужно предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="1c4a5-111">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="1c4a5-112">Но если код зависел от проверки <xref:System.Net.Cookie.Path>, вам нужно реализовать необходимую проверку в коде.</span><span class="sxs-lookup"><span data-stu-id="1c4a5-112">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="1c4a5-113">Если код зависел от вычисления значения по умолчанию для <xref:System.Net.Cookie.Path>, попробуйте вручную указать значение <xref:System.Net.Cookie.Path>, а не использовать значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1c4a5-113">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1c4a5-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1c4a5-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
