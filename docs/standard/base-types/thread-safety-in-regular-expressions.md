---
title: Потокобезопасность в регулярных выражениях
ms.date: 03/30/2017
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: a10b5d01d308af3c808404608e6be1d77e6be8e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734170"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="f2e07-102">Потокобезопасность в регулярных выражениях</span><span class="sxs-lookup"><span data-stu-id="f2e07-102">Thread Safety in Regular Expressions</span></span>

<span data-ttu-id="f2e07-103">Сам по себе класс <xref:System.Text.RegularExpressions.Regex> является потокобезопасным и неизменяемым (предназначенным только для чтения).</span><span class="sxs-lookup"><span data-stu-id="f2e07-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="f2e07-104">Это означает, что объекты **Regex** могут создаваться в любом потоке и совместно использоваться несколькими потоками. Одни и те же методы могут вызываться из любого потока, никак не изменяя при этом глобальное состояние.</span><span class="sxs-lookup"><span data-stu-id="f2e07-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="f2e07-105">Тем не менее, объекты результатов (**Match** и **MatchCollection)** , возвращаемые **Regex**, следует использовать только в одном потоке.</span><span class="sxs-lookup"><span data-stu-id="f2e07-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="f2e07-106">Несмотря на то, что по своей логике многие из этих объектов неизменяемы, их реализации способны задерживать вычисление некоторых результатов для повышения эффективности работы, поэтому в итоге вызывающим объектам приходится сериализовывать доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="f2e07-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="f2e07-107">Если доступ к объектам результатов **Regex** необходимо предоставить нескольким потокам, то эти объекты можно преобразовать в потокобезопасные, вызвав их синхронизированные методы.</span><span class="sxs-lookup"><span data-stu-id="f2e07-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="f2e07-108">Все классы регулярных выражений, за исключением перечислителей, являются потокобезопасными или же могут быть преобразованы в потокобезопасные объекты с помощью синхронизированных методов.</span><span class="sxs-lookup"><span data-stu-id="f2e07-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="f2e07-109">Перечислители являются единственным исключением.</span><span class="sxs-lookup"><span data-stu-id="f2e07-109">Enumerators are the only exception.</span></span> <span data-ttu-id="f2e07-110">Вызовы, обращенные к перечислителям коллекций, в приложениях должны быть сериализованы.</span><span class="sxs-lookup"><span data-stu-id="f2e07-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="f2e07-111">Правило заключается в том, что если существует возможность одновременной работы перечислителей из нескольких потоков с одной коллекцией, то их методы необходимо синхронизировать в корневом объекте коллекции, по которой проходит перечислитель.</span><span class="sxs-lookup"><span data-stu-id="f2e07-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e07-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f2e07-112">See also</span></span>

- [<span data-ttu-id="f2e07-113">Регулярные выражения .NET</span><span class="sxs-lookup"><span data-stu-id="f2e07-113">.NET Regular Expressions</span></span>](regular-expressions.md)
