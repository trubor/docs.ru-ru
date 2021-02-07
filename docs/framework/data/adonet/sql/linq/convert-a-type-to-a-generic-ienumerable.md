---
description: 'Дополнительные сведения: преобразование типа в универсальный интерфейс IEnumerable'
title: Практическое руководство. Преобразование типа в универсальный интерфейс IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: 9be9022bce84808e18514937116ea962065dc1a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712523"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="a44d7-103">Практическое руководство. Преобразование типа в универсальный интерфейс IEnumerable</span><span class="sxs-lookup"><span data-stu-id="a44d7-103">Convert a Type to a Generic IEnumerable</span></span>

<span data-ttu-id="a44d7-104">Для возвращения аргумента с типом универсальный <xref:System.Linq.Enumerable.AsEnumerable%2A> используется `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="a44d7-104">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a44d7-105">Пример</span><span class="sxs-lookup"><span data-stu-id="a44d7-105">Example</span></span>  

 <span data-ttu-id="a44d7-106">В этом примере [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (с помощью заданного по умолчанию универсального `Query`) предпримет попытку преобразовать запрос в SQL и выполнить его на сервере.</span><span class="sxs-lookup"><span data-stu-id="a44d7-106">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="a44d7-107">Однако предложение `where` ссылается на пользовательский метод на стороне клиента (`isValidProduct`), который не может быть преобразован в SQL.</span><span class="sxs-lookup"><span data-stu-id="a44d7-107">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="a44d7-108">Решением является задание клиентской универсальной реализации <xref:System.Collections.Generic.IEnumerable%601> предложения `where` для замены универсального <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a44d7-108">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a44d7-109">Для этого следует вызвать оператор <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="a44d7-109">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="a44d7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="a44d7-110">See also</span></span>

- [<span data-ttu-id="a44d7-111">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="a44d7-111">Query Examples</span></span>](query-examples.md)
