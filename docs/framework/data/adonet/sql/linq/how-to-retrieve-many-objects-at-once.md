---
description: Дополнительные сведения см. в статье как получить много объектов одновременно
title: Практическое руководство. Как получить несколько объектов одновременно
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 2bc202e09c64f2a1956b8688be30cfd87fb655c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802012"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="21254-103">Практическое руководство. Как получить несколько объектов одновременно</span><span class="sxs-lookup"><span data-stu-id="21254-103">How to: Retrieve Many Objects At Once</span></span>

<span data-ttu-id="21254-104">Для извлечения нескольких объектов из одного запроса используется <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="21254-104">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21254-105">Пример</span><span class="sxs-lookup"><span data-stu-id="21254-105">Example</span></span>  

 <span data-ttu-id="21254-106">В следующем коде для извлечения объекта <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> и `Customer` используется метод `Order`.</span><span class="sxs-lookup"><span data-stu-id="21254-106">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="21254-107">См. также</span><span class="sxs-lookup"><span data-stu-id="21254-107">See also</span></span>

- [<span data-ttu-id="21254-108">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="21254-108">Query Concepts</span></span>](query-concepts.md)
