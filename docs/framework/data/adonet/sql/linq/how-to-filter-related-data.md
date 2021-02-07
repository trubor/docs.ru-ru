---
description: Дополнительные сведения см. в статье как фильтровать связанные данные.
title: Практическое руководство. Как фильтровать взаимосвязанные данные
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: d44e0805b82c0c58f9ee19808e078f9f9b337050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738953"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="a2f77-103">Практическое руководство. Как фильтровать взаимосвязанные данные</span><span class="sxs-lookup"><span data-stu-id="a2f77-103">How to: Filter Related Data</span></span>

<span data-ttu-id="a2f77-104">Чтобы указать вложенные запросы для ограничения объема извлекаемых данных, используется метод <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2f77-104">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f77-105">Пример</span><span class="sxs-lookup"><span data-stu-id="a2f77-105">Example</span></span>  

 <span data-ttu-id="a2f77-106">В следующем примере метод <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> ограничивает количество извлеченных заказов (`Orders`) заказами, которые сегодня не были доставлены.</span><span class="sxs-lookup"><span data-stu-id="a2f77-106">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="a2f77-107">Если не использовать этот подход, будут извлечены все заказы (`Orders`) даже в том случае, когда необходим только вложенный набор.</span><span class="sxs-lookup"><span data-stu-id="a2f77-107">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a2f77-108">См. также</span><span class="sxs-lookup"><span data-stu-id="a2f77-108">See also</span></span>

- [<span data-ttu-id="a2f77-109">Запрос к базе данных</span><span class="sxs-lookup"><span data-stu-id="a2f77-109">Querying the Database</span></span>](querying-the-database.md)
