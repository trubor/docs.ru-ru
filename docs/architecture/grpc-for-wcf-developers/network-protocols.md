---
title: Сетевые протоколы — gRPC для разработчиков WCF
description: Общие сведения о сетевых протоколах gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938563"
---
# <a name="network-protocols"></a><span data-ttu-id="db083-103">Сетевые протоколы</span><span class="sxs-lookup"><span data-stu-id="db083-103">Network protocols</span></span>

<span data-ttu-id="db083-104">В отличие от Windows Communication Foundation (WCF), gRPC использует HTTP/2 в качестве основы для своей сети.</span><span class="sxs-lookup"><span data-stu-id="db083-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="db083-105">Этот протокол обеспечивает значительные преимущества по сравнению с WCF и SOAP, которые работают только с HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="db083-105">This protocol offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="db083-106">Для разработчиков, желающих использовать gRPC, учитывая, что нет альтернативы HTTP/2, кажется идеальным моментом исследовать HTTP/2 более подробно и определять дополнительные преимущества использования gRPC.</span><span class="sxs-lookup"><span data-stu-id="db083-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="db083-107">HTTP/2, вызываемая веб-задачей инженерной разработки в 2015, была получена из экспериментального протокола SPDY, который уже использовался в Google.</span><span class="sxs-lookup"><span data-stu-id="db083-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="db083-108">Он был специально разработан для более эффективного, быстрого и более безопасного, чем HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="db083-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="db083-109">Основные функции HTTP/2</span><span class="sxs-lookup"><span data-stu-id="db083-109">Key features of HTTP/2</span></span>

<span data-ttu-id="db083-110">В этом списке показаны некоторые основные функции и преимущества HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="db083-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="db083-111">Двоичный протокол</span><span class="sxs-lookup"><span data-stu-id="db083-111">Binary protocol</span></span>

<span data-ttu-id="db083-112">Циклы запросов и ответов больше не требуют текстовых команд.</span><span class="sxs-lookup"><span data-stu-id="db083-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="db083-113">Это действие упрощает и ускоряет реализацию команд.</span><span class="sxs-lookup"><span data-stu-id="db083-113">This activity simplifies and speeds up the implementation of commands.</span></span> <span data-ttu-id="db083-114">В частности, анализ данных выполняется быстрее и использует меньше памяти, задержка сети сокращается с помощью очевидных улучшений, а также обеспечивается общее лучшее использование сетевых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="db083-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="db083-115">Потоки</span><span class="sxs-lookup"><span data-stu-id="db083-115">Streams</span></span>

<span data-ttu-id="db083-116">Потоки позволяют создавать долгосрочные соединения между отправителем и получателем, в течение которых несколько сообщений или кадров могут быть отправлены асинхронно.</span><span class="sxs-lookup"><span data-stu-id="db083-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="db083-117">Несколько потоков могут обрабатываться независимо друг от друга через одно соединение HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="db083-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="db083-118">Запрос мультиплексирования по одному TCP-соединению</span><span class="sxs-lookup"><span data-stu-id="db083-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="db083-119">Эта функция является одним из наиболее важных нововведений HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="db083-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="db083-120">Так как это позволяет выполнять несколько параллельных запросов к данным, теперь можно загружать веб-файлы параллельно с одного сервера.</span><span class="sxs-lookup"><span data-stu-id="db083-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="db083-121">Веб-сайты загружаются быстрее, и потребность в оптимизации уменьшается.</span><span class="sxs-lookup"><span data-stu-id="db083-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="db083-122">Блокировка до конца строки (HOL), где готовые ответы должны дожидаться отправки до завершения предыдущего запроса, также уменьшается (хотя блокировка HOL может выполняться на уровне TCP-транспорта).</span><span class="sxs-lookup"><span data-stu-id="db083-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="db083-123">NET. TCP-схожая производительность, кросс-платформенная</span><span class="sxs-lookup"><span data-stu-id="db083-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="db083-124">По сути, сочетание gRPC и HTTP/2 предоставляет разработчикам по крайней мере эквивалентную скорость и эффективность привязок NET. TCP для WCF, а в некоторых случаях еще более высокую скорость и эффективность.</span><span class="sxs-lookup"><span data-stu-id="db083-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="db083-125">Но, в отличие от net. TCP, gRPC через HTTP/2 не ограничивается приложениями .NET.</span><span class="sxs-lookup"><span data-stu-id="db083-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="db083-126">[Назад](interface-definition-language.md)
>[Вперед](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="db083-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
