---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032814"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="d6039-101">Kestrel: Трейлеры запроса перемещены из заголовков в новую коллекцию</span><span class="sxs-lookup"><span data-stu-id="d6039-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="d6039-102">В предыдущих версиях Kestrel поблочные трейлеры стандарта HTTP/1.1 добавлялись в коллекцию заголовков запроса, когда завершалось чтение текста запроса.</span><span class="sxs-lookup"><span data-stu-id="d6039-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="d6039-103">Такое поведение вызывало проблемы, связанные с неоднозначностью между заголовками и трейлерами.</span><span class="sxs-lookup"><span data-stu-id="d6039-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="d6039-104">Было принято решение выделить трейлеры в собственную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="d6039-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="d6039-105">Трейлеры запросов HTTP/2 были ранее недоступны в ASP.NET Core 2.2, но теперь также включены в эту новую коллекцию, начиная с ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6039-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="d6039-106">Для доступа к этим трейлерам были добавлены новые методы расширения для запроса.</span><span class="sxs-lookup"><span data-stu-id="d6039-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="d6039-107">Трейлеры HTTP/1.1 теперь становятся доступны, когда завершится считывание текста запроса.</span><span class="sxs-lookup"><span data-stu-id="d6039-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="d6039-108">Трейлеры HTTP/2 становятся доступны, когда они получены от клиента.</span><span class="sxs-lookup"><span data-stu-id="d6039-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="d6039-109">Клиент не будет отправлять трейлеры, пока весь текст запроса не передан по крайней мере в буфер сервера.</span><span class="sxs-lookup"><span data-stu-id="d6039-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="d6039-110">Возможно, потребуется прочитать весь текст запроса, чтобы освободить место в буфере.</span><span class="sxs-lookup"><span data-stu-id="d6039-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="d6039-111">Трейлеры всегда доступны, если текст запроса считан полностью.</span><span class="sxs-lookup"><span data-stu-id="d6039-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="d6039-112">Трейлеры обозначают конец этого текста.</span><span class="sxs-lookup"><span data-stu-id="d6039-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d6039-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d6039-113">Version introduced</span></span>

<span data-ttu-id="d6039-114">3.0</span><span class="sxs-lookup"><span data-stu-id="d6039-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d6039-115">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="d6039-115">Old behavior</span></span>

<span data-ttu-id="d6039-116">Трейлеры запроса добавляются вместо заголовков в коллекцию `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="d6039-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d6039-117">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="d6039-117">New behavior</span></span>

<span data-ttu-id="d6039-118">Трейлеры запроса теперь **отсутствуют** в коллекции `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="d6039-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="d6039-119">Примените к `HttpRequest` следующие методы расширения, чтобы получить их:</span><span class="sxs-lookup"><span data-stu-id="d6039-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="d6039-120">`GetDeclaredTrailers()` получает заголовок запроса Trailer, который содержит список трейлеров, ожидаемых после текста запроса;</span><span class="sxs-lookup"><span data-stu-id="d6039-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="d6039-121">`SupportsTrailers()` указывает, поддерживает ли текущий запрос трейлеры;</span><span class="sxs-lookup"><span data-stu-id="d6039-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="d6039-122">`CheckTrailersAvailable()` определяет, поддерживает ли запрос трейлеры и доступны ли они для чтения;</span><span class="sxs-lookup"><span data-stu-id="d6039-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="d6039-123">`GetTrailer(string trailerName)` получает запрошенный трейлер из ответа.</span><span class="sxs-lookup"><span data-stu-id="d6039-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d6039-124">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d6039-124">Reason for change</span></span>

<span data-ttu-id="d6039-125">Трейлеры являются ключевой функциях в некоторых сценариях, например gRPC.</span><span class="sxs-lookup"><span data-stu-id="d6039-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="d6039-126">Объединение трейлеров с заголовками вызывало путаницу у пользователей.</span><span class="sxs-lookup"><span data-stu-id="d6039-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6039-127">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d6039-127">Recommended action</span></span>

<span data-ttu-id="d6039-128">Для доступа к трейлерам используйте специальные методы расширения в `HttpRequest`.</span><span class="sxs-lookup"><span data-stu-id="d6039-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="d6039-129">Категория</span><span class="sxs-lookup"><span data-stu-id="d6039-129">Category</span></span>

<span data-ttu-id="d6039-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6039-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6039-131">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d6039-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
