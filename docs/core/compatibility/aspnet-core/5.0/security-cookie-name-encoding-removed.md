---
title: Критическое изменение. Безопасность. Удалена кодировка имен файлов cookie
description: Сведения о критическом изменении в ASP.NET Core 5.0 — безопасность. Удалена кодировка имен файлов cookie
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3cd40d2b04d0cdf0863e3a3fb6d790c2b35692bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760033"
---
# <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="99761-103">Безопасность. Удалена кодировка имен файлов cookie</span><span class="sxs-lookup"><span data-stu-id="99761-103">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="99761-104">В соответствии со [стандартом HTTP](https://tools.ietf.org/html/rfc6265#section-4.1.1) в именах и значениях файлов cookie могут использоваться только определенные символы.</span><span class="sxs-lookup"><span data-stu-id="99761-104">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="99761-105">Поддержка недопустимых символов в ASP.NET Core реализуется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="99761-105">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="99761-106">Кодирование при создании файла cookie ответа.</span><span class="sxs-lookup"><span data-stu-id="99761-106">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="99761-107">Декодирование при чтении файла cookie запроса.</span><span class="sxs-lookup"><span data-stu-id="99761-107">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="99761-108">В ASP.NET Core 5.0 это поведение кодирования изменилось в связи выявленными проблемами с безопасностью.</span><span class="sxs-lookup"><span data-stu-id="99761-108">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="99761-109">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="99761-109">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="99761-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="99761-110">Version introduced</span></span>

<span data-ttu-id="99761-111">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="99761-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="99761-112">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="99761-112">Old behavior</span></span>

<span data-ttu-id="99761-113">Имена файлов cookie ответов кодируются.</span><span class="sxs-lookup"><span data-stu-id="99761-113">Response cookie names are encoded.</span></span> <span data-ttu-id="99761-114">Имена файлов cookie запросов декодируются.</span><span class="sxs-lookup"><span data-stu-id="99761-114">Request cookie names are decoded.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="99761-115">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="99761-115">New behavior</span></span>

<span data-ttu-id="99761-116">Кодирование и декодирование имен файлов cookie было исключено.</span><span class="sxs-lookup"><span data-stu-id="99761-116">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="99761-117">Для предшествующих [поддерживаемых версий](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ASP.NET Core команда разработчиков планирует устранять проблемы с декодированием на местах.</span><span class="sxs-lookup"><span data-stu-id="99761-117">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="99761-118">Кроме того, при вызове <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> с указанием недопустимого имени файла cookie возникает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="99761-118">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="99761-119">Способ кодирования и декодирования значений файлов cookie не изменился.</span><span class="sxs-lookup"><span data-stu-id="99761-119">Encoding and decoding of cookie values remains unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="99761-120">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="99761-120">Reason for change</span></span>

<span data-ttu-id="99761-121">На [нескольких веб-платформах](https://github.com/advisories/GHSA-j6w9-fv6q-3q52) были обнаружены проблемы.</span><span class="sxs-lookup"><span data-stu-id="99761-121">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="99761-122">В процессе кодирования и декодирования злоумышленник получал возможность обойти защитную функцию [префиксов файлов cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) путем подмены зарезервированных префиксов, таких как `__Host-`, закодированными значениями, например `__%48ost-`.</span><span class="sxs-lookup"><span data-stu-id="99761-122">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="99761-123">Для проведения такой атаки требуется использовать дополнительную уязвимость веб-сайта для внедрения ложных файлов cookie, например уязвимость межсайтовых сценариев (XSS).</span><span class="sxs-lookup"><span data-stu-id="99761-123">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="99761-124">По умолчанию эти префиксы не используются в ASP.NET Core, а также в библиотеках или шаблонах `Microsoft.Owin`.</span><span class="sxs-lookup"><span data-stu-id="99761-124">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="99761-125">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="99761-125">Recommended action</span></span>

<span data-ttu-id="99761-126">Если вы переносите проекты в ASP.NET Core 5.0 или более поздней версии, убедитесь, что используемые имена файлов cookie соответствуют [требованиям спецификации токенов](https://tools.ietf.org/html/rfc2616#section-2.2): символы ASCII, за исключением управляющих символов и разделителей `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span><span class="sxs-lookup"><span data-stu-id="99761-126">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="99761-127">Если в именах файлов cookie или других заголовках HTTP используются не входящие в набор ASCII символы, это может привести к возникновению исключения на сервере или некорректной передаче данных клиенту и обратно.</span><span class="sxs-lookup"><span data-stu-id="99761-127">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="99761-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="99761-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
