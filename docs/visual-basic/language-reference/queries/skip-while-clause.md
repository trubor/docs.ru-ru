---
description: Дополнительные сведения о предложении Skip While (Visual Basic)
title: Предложение Skip While
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 6f2785fde1a62c10c914904ccba51510dbb1a041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773853"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="ed140-103">Предложение Skip While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed140-103">Skip While Clause (Visual Basic)</span></span>

<span data-ttu-id="ed140-104">Пропускает элементы в коллекции, если заданное условие имеет значение `true`, и возвращает остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="ed140-104">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed140-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed140-105">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ed140-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="ed140-106">Parts</span></span>  
  
|<span data-ttu-id="ed140-107">Термин</span><span class="sxs-lookup"><span data-stu-id="ed140-107">Term</span></span>|<span data-ttu-id="ed140-108">Определение</span><span class="sxs-lookup"><span data-stu-id="ed140-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="ed140-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="ed140-109">Required.</span></span> <span data-ttu-id="ed140-110">Выражение, представляющее условие для проверки элементов.</span><span class="sxs-lookup"><span data-stu-id="ed140-110">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="ed140-111">Выражение должно возвращать `Boolean` значение или функциональный эквивалент, например, `Integer` для вычисления в виде `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ed140-111">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed140-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed140-112">Remarks</span></span>  

 <span data-ttu-id="ed140-113">`Skip While`Предложение обходит элементы из начала результата запроса до тех пор, пока не будут `expression` возвращены `false` .</span><span class="sxs-lookup"><span data-stu-id="ed140-113">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="ed140-114">После `expression` возврата `false` запрос возвращает все остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="ed140-114">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="ed140-115">`expression`Для оставшихся результатов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="ed140-115">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="ed140-116">`Skip While`Предложение отличается от `Where` предложения в том, что `Where` предложение может использоваться для исключения всех элементов из запроса, которые не соответствуют определенному условию.</span><span class="sxs-lookup"><span data-stu-id="ed140-116">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="ed140-117">`Skip While`Предложение исключает элементы только до первого момента, когда условие не будет удовлетворено.</span><span class="sxs-lookup"><span data-stu-id="ed140-117">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="ed140-118">`Skip While`Предложение наиболее полезно при работе с упорядоченным результатом запроса.</span><span class="sxs-lookup"><span data-stu-id="ed140-118">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="ed140-119">Можно обойти определенное количество результатов с начала результата запроса с помощью `Skip` предложения.</span><span class="sxs-lookup"><span data-stu-id="ed140-119">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed140-120">Пример</span><span class="sxs-lookup"><span data-stu-id="ed140-120">Example</span></span>  

 <span data-ttu-id="ed140-121">В следующем примере кода предложение используется `Skip While` для обхода результатов до тех пор, пока не будет найден первый клиент из США.</span><span class="sxs-lookup"><span data-stu-id="ed140-121">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ed140-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ed140-122">See also</span></span>

- <span data-ttu-id="ed140-123">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed140-123">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="ed140-124">Запросы</span><span class="sxs-lookup"><span data-stu-id="ed140-124">Queries</span></span>](index.md)
- [<span data-ttu-id="ed140-125">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="ed140-125">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="ed140-126">Предложение From</span><span class="sxs-lookup"><span data-stu-id="ed140-126">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="ed140-127">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="ed140-127">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="ed140-128">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="ed140-128">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="ed140-129">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="ed140-129">Where Clause</span></span>](where-clause.md)
