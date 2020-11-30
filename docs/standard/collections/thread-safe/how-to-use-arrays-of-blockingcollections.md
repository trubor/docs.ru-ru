---
title: Практическое руководство. Использование массивов для блокировки коллекций в конвейере
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 55dc3e9934efa153c61322f63b7dde8077442fd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733468"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="0b612-102">Практическое руководство. Использование массивов для блокировки коллекций в конвейере</span><span class="sxs-lookup"><span data-stu-id="0b612-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>

<span data-ttu-id="0b612-103">В приведенном ниже примере показано, как использовать массивы объектов <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> со статическими методами, например методами <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> и <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A>, для реализации быстрой и гибкой передачи данных между компонентами.</span><span class="sxs-lookup"><span data-stu-id="0b612-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b612-104">Пример</span><span class="sxs-lookup"><span data-stu-id="0b612-104">Example</span></span>  

 <span data-ttu-id="0b612-105">В следующем примере показана основная реализация конвейера, в котором каждый объект выполняет параллельную операцию получения данных из входной коллекции, выполняет их преобразование и передает их в выходную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="0b612-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="0b612-106">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0b612-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="0b612-107">Потокобезопасные коллекции</span><span class="sxs-lookup"><span data-stu-id="0b612-107">Thread-Safe Collections</span></span>](index.md)
