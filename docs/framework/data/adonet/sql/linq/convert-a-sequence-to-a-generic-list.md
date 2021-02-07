---
description: 'Дополнительные сведения: Преобразование последовательности в универсальный список'
title: Преобразование последовательности в универсальный список
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: e9832fd366f22b77674fb4c83f6af7ce89a552c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663122"
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="f69d4-103">Преобразование последовательности в универсальный список</span><span class="sxs-lookup"><span data-stu-id="f69d4-103">Convert a Sequence to a Generic List</span></span>

<span data-ttu-id="f69d4-104">Для создания универсального списка из последовательности используется <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="f69d4-104">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f69d4-105">Пример</span><span class="sxs-lookup"><span data-stu-id="f69d4-105">Example</span></span>  

 <span data-ttu-id="f69d4-106">В следующем примере используется <xref:System.Linq.Enumerable.ToList%2A> для непосредственного преобразования запроса в универсальный <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f69d4-106">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="f69d4-107">См. также</span><span class="sxs-lookup"><span data-stu-id="f69d4-107">See also</span></span>

- [<span data-ttu-id="f69d4-108">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="f69d4-108">Query Examples</span></span>](query-examples.md)
