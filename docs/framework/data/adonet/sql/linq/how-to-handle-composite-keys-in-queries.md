---
description: Дополнительные сведения см. в статье как работать с составными ключами в запросах.
title: Практическое руководство. Как обрабатывать составные ключи в запросах
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 9d7c68495810bee6a383d98a75694e7cd24f1015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738875"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="f97a1-103">Практическое руководство. Как обрабатывать составные ключи в запросах</span><span class="sxs-lookup"><span data-stu-id="f97a1-103">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="f97a1-104">Некоторые операторы могут принимать только один аргумент.</span><span class="sxs-lookup"><span data-stu-id="f97a1-104">Some operators can take only one argument.</span></span> <span data-ttu-id="f97a1-105">Если аргумент должен содержать несколько столбцов базы данных, необходимо создать анонимный тип для представления комбинации столбцов.</span><span class="sxs-lookup"><span data-stu-id="f97a1-105">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f97a1-106">Пример</span><span class="sxs-lookup"><span data-stu-id="f97a1-106">Example</span></span>  

 <span data-ttu-id="f97a1-107">В следующем примере показан запрос, который вызывает оператор `GroupBy`, принимающий только один аргумент `key`.</span><span class="sxs-lookup"><span data-stu-id="f97a1-107">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="f97a1-108">Пример</span><span class="sxs-lookup"><span data-stu-id="f97a1-108">Example</span></span>  

 <span data-ttu-id="f97a1-109">Та же ситуация возникает в случае соединений, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f97a1-109">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f97a1-110">См. также</span><span class="sxs-lookup"><span data-stu-id="f97a1-110">See also</span></span>

- [<span data-ttu-id="f97a1-111">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="f97a1-111">Query Concepts</span></span>](query-concepts.md)
