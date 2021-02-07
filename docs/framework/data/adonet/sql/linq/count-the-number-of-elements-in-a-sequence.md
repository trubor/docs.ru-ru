---
description: 'Дополнительные сведения о: подсчет числа элементов в последовательности'
title: Подсчет количества элементов в последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663083"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="25901-103">Подсчет количества элементов в последовательности</span><span class="sxs-lookup"><span data-stu-id="25901-103">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="25901-104">Для подсчета числа элементов в последовательности используется оператор <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="25901-104">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="25901-105">При выполнении данного запроса в учебной базе данных "Northwind" возвращается значение `91`.</span><span class="sxs-lookup"><span data-stu-id="25901-105">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25901-106">Пример</span><span class="sxs-lookup"><span data-stu-id="25901-106">Example</span></span>  

 <span data-ttu-id="25901-107">В следующем примере подсчитывается количество клиентов (`Customers`) в базе данных.</span><span class="sxs-lookup"><span data-stu-id="25901-107">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="25901-108">Пример</span><span class="sxs-lookup"><span data-stu-id="25901-108">Example</span></span>  

 <span data-ttu-id="25901-109">В следующем примере подсчитывается количество продуктов в базе данных, еще не снятых с производства.</span><span class="sxs-lookup"><span data-stu-id="25901-109">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="25901-110">При выполнении данного примера в учебной базе данных "Northwind" возвращается значение `69`.</span><span class="sxs-lookup"><span data-stu-id="25901-110">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="25901-111">См. также</span><span class="sxs-lookup"><span data-stu-id="25901-111">See also</span></span>

- [<span data-ttu-id="25901-112">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="25901-112">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="25901-113">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="25901-113">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
