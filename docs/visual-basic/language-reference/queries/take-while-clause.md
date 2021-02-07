---
description: 'Дополнительные сведения о предложении: Take While (Visual Basic)'
title: Предложение Take While
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: a413223d4a85670c66f71e24addb92ae4d38a4a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719712"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="4f32a-103">Предложение Take While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f32a-103">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="4f32a-104">Включает элементы в коллекцию, если заданное условие имеет значение `true`, и пропускает остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="4f32a-104">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f32a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4f32a-105">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4f32a-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="4f32a-106">Parts</span></span>  
  
|<span data-ttu-id="4f32a-107">Термин</span><span class="sxs-lookup"><span data-stu-id="4f32a-107">Term</span></span>|<span data-ttu-id="4f32a-108">Определение</span><span class="sxs-lookup"><span data-stu-id="4f32a-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="4f32a-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="4f32a-109">Required.</span></span> <span data-ttu-id="4f32a-110">Выражение, представляющее условие для проверки элементов.</span><span class="sxs-lookup"><span data-stu-id="4f32a-110">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="4f32a-111">Выражение должно возвращать `Boolean` значение или функциональный эквивалент, например, `Integer` для вычисления в виде `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4f32a-111">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f32a-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="4f32a-112">Remarks</span></span>  

 <span data-ttu-id="4f32a-113">`Take While`Предложение включает элементы из начала результата запроса до тех пор, пока не будут `expression` возвращены `false` .</span><span class="sxs-lookup"><span data-stu-id="4f32a-113">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="4f32a-114">После `expression` возврата `false` запрос будет обходить все оставшиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="4f32a-114">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="4f32a-115">`expression`Для оставшихся результатов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="4f32a-115">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="4f32a-116">`Take While`Предложение отличается от `Where` предложения в том, что `Where` предложение может использоваться для включения всех элементов из запроса, удовлетворяющего определенному условию.</span><span class="sxs-lookup"><span data-stu-id="4f32a-116">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="4f32a-117">`Take While`Предложение включает элементы только до первого момента, когда условие не будет удовлетворено.</span><span class="sxs-lookup"><span data-stu-id="4f32a-117">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="4f32a-118">`Take While`Предложение наиболее полезно при работе с упорядоченным результатом запроса.</span><span class="sxs-lookup"><span data-stu-id="4f32a-118">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f32a-119">Пример</span><span class="sxs-lookup"><span data-stu-id="4f32a-119">Example</span></span>  

 <span data-ttu-id="4f32a-120">В следующем примере кода предложение используется `Take While` для получения результатов до тех пор, пока не будет найден первый клиент без заказов.</span><span class="sxs-lookup"><span data-stu-id="4f32a-120">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4f32a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="4f32a-121">See also</span></span>

- <span data-ttu-id="4f32a-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f32a-122">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="4f32a-123">Запросы</span><span class="sxs-lookup"><span data-stu-id="4f32a-123">Queries</span></span>](index.md)
- [<span data-ttu-id="4f32a-124">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="4f32a-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="4f32a-125">Предложение From</span><span class="sxs-lookup"><span data-stu-id="4f32a-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4f32a-126">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="4f32a-126">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="4f32a-127">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="4f32a-127">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="4f32a-128">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="4f32a-128">Where Clause</span></span>](where-clause.md)
