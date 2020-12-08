---
title: Предупреждение SYSLIB0006
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0006.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: a5ab4fe4576bd336cb7de0a91b889fa48ac5650a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437462"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="b1ebe-103">SYSLIB0006. Thread.Abort не поддерживается</span><span class="sxs-lookup"><span data-stu-id="b1ebe-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="b1ebe-104">Следующие API помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="b1ebe-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="b1ebe-105">При использовании этих API во время компиляции создается предупреждение `SYSLIB0006`.</span><span class="sxs-lookup"><span data-stu-id="b1ebe-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="b1ebe-106">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="b1ebe-106">Workarounds</span></span>

<span data-ttu-id="b1ebe-107">Используйте <xref:System.Threading.CancellationToken>, чтобы прервать обработку единицы работы вместо вызова <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1ebe-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1ebe-108">В следующем примере демонстрируется применение <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="b1ebe-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

```csharp
void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
{
    if (QueryIsMoreWorkPending())
    {
        // If the CancellationToken is marked as "needs to cancel",
        // this will throw the appropriate exception.
        cancellationToken.ThrowIfCancellationRequested();

        WorkItem work = DequeueWorkItem();
        ProcessWorkItem(work);
    }
}
```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="b1ebe-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b1ebe-109">See also</span></span>

- [<span data-ttu-id="b1ebe-110">Thread.Abort устарел</span><span class="sxs-lookup"><span data-stu-id="b1ebe-110">Thread.Abort is obsolete</span></span>](core-libraries/5.0/thread-abort-obsolete.md)
- [<span data-ttu-id="b1ebe-111">Отмена в управляемых потоках</span><span class="sxs-lookup"><span data-stu-id="b1ebe-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
