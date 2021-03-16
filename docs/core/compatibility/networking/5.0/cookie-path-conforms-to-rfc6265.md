---
title: Критическое изменение. Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265
description: Узнайте о критическом изменении в .NET 5, где алгоритмы обработки путей, определенные в RFC 6265, реализованы для классов cookie и CookieContainer.
ms.date: 08/18/2020
ms.openlocfilehash: 5ee1bccc79a5ac271904dd3223b58cc168f18cfa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256469"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="42530-103">Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265</span><span class="sxs-lookup"><span data-stu-id="42530-103">Cookie path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="42530-104">Алгоритмы обработки путей, определенные в [RFC 6265](https://tools.ietf.org/html/rfc6265), реализованы для классов <xref:System.Net.Cookie> и <xref:System.Net.CookieContainer>.</span><span class="sxs-lookup"><span data-stu-id="42530-104">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="42530-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="42530-105">Version introduced</span></span>

<span data-ttu-id="42530-106">5.0</span><span class="sxs-lookup"><span data-stu-id="42530-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="42530-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="42530-107">Change description</span></span>

- <span data-ttu-id="42530-108">Свойство <xref:System.Net.Cookie.Path> больше не должно быть префиксом пути запроса.</span><span class="sxs-lookup"><span data-stu-id="42530-108">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="42530-109">Вычисление значения по умолчанию для <xref:System.Net.Cookie.Path> и алгоритмов сопоставления путей реализовано в RFC 6265 в [разделе 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4).</span><span class="sxs-lookup"><span data-stu-id="42530-109">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="42530-110">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="42530-110">Recommended action</span></span>

<span data-ttu-id="42530-111">В большинстве случаев вам не нужно предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="42530-111">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="42530-112">Но если код зависел от проверки <xref:System.Net.Cookie.Path>, вам нужно реализовать необходимую проверку в коде.</span><span class="sxs-lookup"><span data-stu-id="42530-112">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="42530-113">Если код зависел от вычисления значения по умолчанию для <xref:System.Net.Cookie.Path>, попробуйте вручную указать значение <xref:System.Net.Cookie.Path>, а не использовать значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="42530-113">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="42530-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="42530-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
