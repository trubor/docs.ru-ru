---
title: Отложенные выражения
description: 'Узнайте, как выражения F # Lazy могут улучшить производительность приложений и библиотек.'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425507"
---
# <a name="lazy-expressions"></a><span data-ttu-id="2595b-103">Отложенные выражения</span><span class="sxs-lookup"><span data-stu-id="2595b-103">Lazy Expressions</span></span>

<span data-ttu-id="2595b-104">*Отложенные выражения* — это выражения, которые не оцениваются немедленно, а оцениваются, когда требуется результат.</span><span class="sxs-lookup"><span data-stu-id="2595b-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="2595b-105">Это поможет повысить производительность кода.</span><span class="sxs-lookup"><span data-stu-id="2595b-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2595b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2595b-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="2595b-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="2595b-107">Remarks</span></span>

<span data-ttu-id="2595b-108">В приведенном выше синтаксисе *выражение* — это код, который вычисляется только тогда, когда требуется результат, а *идентификатор* — это значение, в котором хранится результат.</span><span class="sxs-lookup"><span data-stu-id="2595b-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="2595b-109">Значение имеет тип `Lazy<'T>` , где фактический тип, используемый для, `'T` определяется из результата выражения.</span><span class="sxs-lookup"><span data-stu-id="2595b-109">The value is of type `Lazy<'T>`, where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="2595b-110">Отложенные выражения позволяют повысить производительность за счет ограниченного выполнения выражений только теми ситуациями, в которых требуется результат.</span><span class="sxs-lookup"><span data-stu-id="2595b-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="2595b-111">Чтобы принудительно выполнить выражения, вызовите метод `Force` .</span><span class="sxs-lookup"><span data-stu-id="2595b-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="2595b-112">`Force` приводит к выполнению выполнения только один раз.</span><span class="sxs-lookup"><span data-stu-id="2595b-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="2595b-113">Последующие вызовы `Force` возвращают тот же результат, но не выполняют никакой код.</span><span class="sxs-lookup"><span data-stu-id="2595b-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="2595b-114">В следующем коде показано использование отложенных выражений и использование `Force` .</span><span class="sxs-lookup"><span data-stu-id="2595b-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="2595b-115">В этом коде тип `result` имеет значение `Lazy<int>` , а `Force` метод возвращает `int` .</span><span class="sxs-lookup"><span data-stu-id="2595b-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="2595b-116">Отложенная оценка, но не `Lazy` тип, также используется для последовательностей.</span><span class="sxs-lookup"><span data-stu-id="2595b-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="2595b-117">Дополнительные сведения см. в разделе [последовательности](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="2595b-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2595b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2595b-118">See also</span></span>

- [<span data-ttu-id="2595b-119">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="2595b-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2595b-120">Модуль Лазекстенсионс</span><span class="sxs-lookup"><span data-stu-id="2595b-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
