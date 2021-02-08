---
description: 'Дополнительные сведения: удаление повторяющихся элементов из последовательности'
title: Удаление дубликатов элементов из последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: f371fc27794361e3ea92d342f845996d9291d30c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786099"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a><span data-ttu-id="8c544-103">Удаление дубликатов элементов из последовательности</span><span class="sxs-lookup"><span data-stu-id="8c544-103">Eliminate Duplicate Elements from a Sequence</span></span>

<span data-ttu-id="8c544-104">Чтобы исключить элементы-дубликаты из последовательности, воспользуйтесь оператором <xref:System.Linq.Queryable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c544-104">Use the <xref:System.Linq.Queryable.Distinct%2A> operator to eliminate duplicate elements from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c544-105">Пример</span><span class="sxs-lookup"><span data-stu-id="8c544-105">Example</span></span>  

 <span data-ttu-id="8c544-106">В следующем примере для выбора последовательности уникальных городов, в которых находятся клиенты, используется метод <xref:System.Linq.Queryable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c544-106">The following example uses <xref:System.Linq.Queryable.Distinct%2A> to select a sequence of the unique cities that have customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a><span data-ttu-id="8c544-107">См. также</span><span class="sxs-lookup"><span data-stu-id="8c544-107">See also</span></span>

- [<span data-ttu-id="8c544-108">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="8c544-108">Query Examples</span></span>](query-examples.md)
