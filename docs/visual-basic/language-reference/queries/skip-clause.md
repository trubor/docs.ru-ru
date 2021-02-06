---
description: Дополнительные сведения о предложении Skip (Visual Basic)
title: Предложение Skip
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 6af702f65a724ea8c3d5a6122fb5f7a0ed5f6755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653554"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="89444-103">Предложение Skip (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89444-103">Skip Clause (Visual Basic)</span></span>

<span data-ttu-id="89444-104">Пропускает заданное число элементов в коллекции и возвращает остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="89444-104">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89444-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89444-105">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="89444-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="89444-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="89444-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="89444-107">Required.</span></span> <span data-ttu-id="89444-108">Значение или выражение, результатом которого является число пропускаемых элементов последовательности.</span><span class="sxs-lookup"><span data-stu-id="89444-108">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89444-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="89444-109">Remarks</span></span>  

 <span data-ttu-id="89444-110">`Skip`Предложение заставляет запрос обходить элементы в начале списка результатов и возвращать оставшиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="89444-110">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="89444-111">Число пропускаемых элементов определяется `count` параметром.</span><span class="sxs-lookup"><span data-stu-id="89444-111">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="89444-112">`Skip`Предложение с `Take` предложением можно использовать для возврата диапазона данных из любого сегмента запроса.</span><span class="sxs-lookup"><span data-stu-id="89444-112">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="89444-113">Для этого передайте индекс первого элемента диапазона в `Skip` предложение и размер диапазона в `Take` предложение.</span><span class="sxs-lookup"><span data-stu-id="89444-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="89444-114">При использовании `Skip` предложения в запросе может также потребоваться убедиться, что результаты возвращаются в порядке, который позволит `Skip` использовать предложение для обхода предполагаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="89444-114">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="89444-115">Дополнительные сведения о упорядочении результатов запроса см. в разделе [предложение ORDER BY](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="89444-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="89444-116">Можно использовать предложение, `SkipWhile` чтобы указать, что игнорируются только определенные элементы, в зависимости от указанного условия.</span><span class="sxs-lookup"><span data-stu-id="89444-116">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89444-117">Пример</span><span class="sxs-lookup"><span data-stu-id="89444-117">Example</span></span>  

 <span data-ttu-id="89444-118">В следующем примере кода предложение используется `Skip` вместе с `Take` предложением для возврата данных из запроса на страницах.</span><span class="sxs-lookup"><span data-stu-id="89444-118">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="89444-119">`GetCustomers`Функция использует `Skip` предложение для обхода клиентов в списке до получения значения начального индекса и использует `Take` предложение для возврата страницы клиентов, начиная с этого значения индекса.</span><span class="sxs-lookup"><span data-stu-id="89444-119">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="89444-120">См. также</span><span class="sxs-lookup"><span data-stu-id="89444-120">See also</span></span>

- <span data-ttu-id="89444-121">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89444-121">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="89444-122">Запросы</span><span class="sxs-lookup"><span data-stu-id="89444-122">Queries</span></span>](index.md)
- [<span data-ttu-id="89444-123">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="89444-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="89444-124">Предложение From</span><span class="sxs-lookup"><span data-stu-id="89444-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="89444-125">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="89444-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="89444-126">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="89444-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="89444-127">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="89444-127">Take Clause</span></span>](take-clause.md)
