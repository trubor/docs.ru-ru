---
description: Дополнительные сведения см. в статье определение соответствия одного или всех элементов последовательности условию.
title: Проверка соответствия условию какого-либо или всех элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: a46cf7e4e213eba830dc203f9266a408103cee80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786112"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="15158-103">Проверка соответствия условию какого-либо или всех элементов</span><span class="sxs-lookup"><span data-stu-id="15158-103">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>

<span data-ttu-id="15158-104">Оператор <xref:System.Linq.Enumerable.All%2A> возвращает значение `true`, если все элементы в последовательности удовлетворяют указанному условию.</span><span class="sxs-lookup"><span data-stu-id="15158-104">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="15158-105">Оператор <xref:System.Linq.Queryable.Any%2A> возвращает значение `true`, если какой-либо элемент в коллекции удовлетворяет указанному условию.</span><span class="sxs-lookup"><span data-stu-id="15158-105">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15158-106">Пример</span><span class="sxs-lookup"><span data-stu-id="15158-106">Example</span></span>  

 <span data-ttu-id="15158-107">В следующем примере возвращается последовательность клиентов, сделавших хотя бы один заказ.</span><span class="sxs-lookup"><span data-stu-id="15158-107">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="15158-108">`Where` / `where` Предложение принимает значение, `true` Если у данного предложения `Customer` есть `Order` .</span><span class="sxs-lookup"><span data-stu-id="15158-108">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="15158-109">Пример</span><span class="sxs-lookup"><span data-stu-id="15158-109">Example</span></span>  

 <span data-ttu-id="15158-110">Следующий код Visual Basic определяет список клиентов, не оформивших заказы, и гарантирует наличие контактного имени для каждого клиента в этом списке.</span><span class="sxs-lookup"><span data-stu-id="15158-110">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="15158-111">Пример</span><span class="sxs-lookup"><span data-stu-id="15158-111">Example</span></span>  

 <span data-ttu-id="15158-112">В следующем примере C# возвращается последовательность клиентов, `ShipCity` в заказах которых начинается с буквы "С".</span><span class="sxs-lookup"><span data-stu-id="15158-112">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="15158-113">Кроме того, в полученном результате будут указаны клиенты, не сделавшие ни одного заказа.</span><span class="sxs-lookup"><span data-stu-id="15158-113">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="15158-114">(По проекту <xref:System.Linq.Queryable.All%2A> оператор возвращает `true` для пустой последовательности.) Клиенты без заказов устраняются в выходных данных консоли с помощью `Count` оператора.</span><span class="sxs-lookup"><span data-stu-id="15158-114">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="15158-115">См. также</span><span class="sxs-lookup"><span data-stu-id="15158-115">See also</span></span>

- [<span data-ttu-id="15158-116">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="15158-116">Query Examples</span></span>](query-examples.md)
