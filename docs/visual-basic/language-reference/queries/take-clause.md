---
description: 'Дополнительные сведения о предложении: Take (Visual Basic)'
title: Предложение Take
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 6542d262490d9d4acff893b2a99ffb60dd1446a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653541"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="2ae22-103">Предложение Take (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ae22-103">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="2ae22-104">Возвращает указанное число идущих подряд элементов с начала коллекции.</span><span class="sxs-lookup"><span data-stu-id="2ae22-104">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae22-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2ae22-105">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="2ae22-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="2ae22-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="2ae22-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="2ae22-107">Required.</span></span> <span data-ttu-id="2ae22-108">Значение или выражение, результатом которого является число возвращаемых элементов последовательности.</span><span class="sxs-lookup"><span data-stu-id="2ae22-108">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae22-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ae22-109">Remarks</span></span>  

 <span data-ttu-id="2ae22-110">`Take`Предложение вызывает включение в запрос указанного числа смежных элементов из начала списка результатов.</span><span class="sxs-lookup"><span data-stu-id="2ae22-110">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="2ae22-111">Число включаемых элементов задается `count` параметром.</span><span class="sxs-lookup"><span data-stu-id="2ae22-111">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="2ae22-112">`Take`Предложение с `Skip` предложением можно использовать для возврата диапазона данных из любого сегмента запроса.</span><span class="sxs-lookup"><span data-stu-id="2ae22-112">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="2ae22-113">Для этого передайте индекс первого элемента диапазона в `Skip` предложение и размер диапазона в `Take` предложение.</span><span class="sxs-lookup"><span data-stu-id="2ae22-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="2ae22-114">В этом случае `Take` предложение должно быть указано после `Skip` предложения.</span><span class="sxs-lookup"><span data-stu-id="2ae22-114">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="2ae22-115">При использовании `Take` предложения в запросе может также потребоваться убедиться, что результаты возвращены в порядке, который позволит `Take` предложению включить предполагаемые результаты.</span><span class="sxs-lookup"><span data-stu-id="2ae22-115">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="2ae22-116">Дополнительные сведения о упорядочении результатов запроса см. в разделе [предложение ORDER BY](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2ae22-116">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="2ae22-117">С помощью предложения можно `TakeWhile` указать, что возвращаются только определенные элементы, в зависимости от указанного условия.</span><span class="sxs-lookup"><span data-stu-id="2ae22-117">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ae22-118">Пример</span><span class="sxs-lookup"><span data-stu-id="2ae22-118">Example</span></span>  

 <span data-ttu-id="2ae22-119">В следующем примере кода предложение используется `Take` вместе с `Skip` предложением для возврата данных из запроса на страницах.</span><span class="sxs-lookup"><span data-stu-id="2ae22-119">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="2ae22-120">Функция "клиенты" использует `Skip` предложение для обхода клиентов в списке до получения значения начального индекса и использует `Take` предложение для возврата страницы клиентов, начиная с этого значения индекса.</span><span class="sxs-lookup"><span data-stu-id="2ae22-120">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2ae22-121">См. также</span><span class="sxs-lookup"><span data-stu-id="2ae22-121">See also</span></span>

- <span data-ttu-id="2ae22-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ae22-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="2ae22-123">Запросы</span><span class="sxs-lookup"><span data-stu-id="2ae22-123">Queries</span></span>](index.md)
- [<span data-ttu-id="2ae22-124">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="2ae22-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="2ae22-125">Предложение From</span><span class="sxs-lookup"><span data-stu-id="2ae22-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="2ae22-126">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="2ae22-126">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="2ae22-127">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="2ae22-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="2ae22-128">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="2ae22-128">Skip Clause</span></span>](skip-clause.md)
