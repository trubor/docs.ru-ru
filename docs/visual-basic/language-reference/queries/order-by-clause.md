---
description: Дополнительные сведения о предложении ORDER BY (Visual Basic)
title: Предложение Order By
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: b5e7cc93b11393ef2f256e90e402975fbf6633a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653619"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="22505-103">Предложение Order By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22505-103">Order By Clause (Visual Basic)</span></span>

<span data-ttu-id="22505-104">Задает порядок сортировки для результата запроса.</span><span class="sxs-lookup"><span data-stu-id="22505-104">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22505-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="22505-105">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="22505-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="22505-106">Parts</span></span>  

 `orderExp1`  
 <span data-ttu-id="22505-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="22505-107">Required.</span></span> <span data-ttu-id="22505-108">Одно или несколько полей из текущего результата запроса, которые указывают порядок упорядочения возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="22505-108">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="22505-109">Имена полей должны быть разделены запятыми (,).</span><span class="sxs-lookup"><span data-stu-id="22505-109">The field names must be separated by commas (,).</span></span> <span data-ttu-id="22505-110">Каждое поле можно задать как отсортированное в порядке возрастания или убывания с помощью `Ascending` `Descending` ключевых слов или.</span><span class="sxs-lookup"><span data-stu-id="22505-110">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="22505-111">Если `Ascending` `Descending` ключевое слово or не указано, используется порядок сортировки по возрастанию.</span><span class="sxs-lookup"><span data-stu-id="22505-111">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="22505-112">Поля порядка сортировки получают приоритет слева направо.</span><span class="sxs-lookup"><span data-stu-id="22505-112">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22505-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="22505-113">Remarks</span></span>  

 <span data-ttu-id="22505-114">`Order By`Для сортировки результатов запроса можно использовать предложение.</span><span class="sxs-lookup"><span data-stu-id="22505-114">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="22505-115">`Order By`Предложение может сортировать результат только на основе переменной диапазона для текущей области.</span><span class="sxs-lookup"><span data-stu-id="22505-115">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="22505-116">Например, `Select` предложение вводит новую область в выражении запроса с новыми переменными итерации для этой области.</span><span class="sxs-lookup"><span data-stu-id="22505-116">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="22505-117">Переменные диапазона, определенные перед `Select` предложением в запросе, недоступны после `Select` предложения.</span><span class="sxs-lookup"><span data-stu-id="22505-117">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="22505-118">Поэтому, если требуется упорядочить результаты по полю, которое недоступно в `Select` предложении, необходимо поместить `Order By` предложение перед `Select` предложением.</span><span class="sxs-lookup"><span data-stu-id="22505-118">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="22505-119">Одним из примеров того, когда это потребуется, является то, что нужно отсортировать запрос по полям, которые не возвращаются как часть результата.</span><span class="sxs-lookup"><span data-stu-id="22505-119">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="22505-120">Порядок сортировки для поля по возрастанию и убыванию определяется реализацией <xref:System.IComparable> интерфейса для типа данных поля.</span><span class="sxs-lookup"><span data-stu-id="22505-120">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="22505-121">Если тип данных не реализует <xref:System.IComparable> интерфейс, порядок сортировки игнорируется.</span><span class="sxs-lookup"><span data-stu-id="22505-121">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22505-122">Пример</span><span class="sxs-lookup"><span data-stu-id="22505-122">Example</span></span>  

 <span data-ttu-id="22505-123">Следующее выражение запроса использует `From` предложение для объявления переменной диапазона `book` для `books` коллекции.</span><span class="sxs-lookup"><span data-stu-id="22505-123">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="22505-124">`Order By`Предложение сортирует результат запроса по цене в возрастающем порядке (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="22505-124">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="22505-125">Книги с одинаковой ценой сортируются по названию в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="22505-125">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="22505-126">`Select`Предложение выбирает `Title` Свойства и в `Price` качестве значений, возвращаемых запросом.</span><span class="sxs-lookup"><span data-stu-id="22505-126">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="22505-127">Пример</span><span class="sxs-lookup"><span data-stu-id="22505-127">Example</span></span>  

 <span data-ttu-id="22505-128">Следующее выражение запроса использует `Order By` предложение для сортировки результата запроса по цене в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="22505-128">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="22505-129">Книги с одинаковой ценой сортируются по названию в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="22505-129">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="22505-130">Пример</span><span class="sxs-lookup"><span data-stu-id="22505-130">Example</span></span>  

 <span data-ttu-id="22505-131">Следующее выражение запроса использует `Select` предложение для выбора названия книги, цены, даты публикации и автора.</span><span class="sxs-lookup"><span data-stu-id="22505-131">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="22505-132">Затем он заполняет `Title` `Price` поля,, `PublishDate` и `Author` переменной диапазона для новой области.</span><span class="sxs-lookup"><span data-stu-id="22505-132">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="22505-133">`Order By`Предложение упорядочивает новую переменную диапазона по имени автора, названию книги и стоимости.</span><span class="sxs-lookup"><span data-stu-id="22505-133">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="22505-134">Каждый столбец сортируется в порядке по умолчанию (по возрастанию).</span><span class="sxs-lookup"><span data-stu-id="22505-134">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="22505-135">См. также</span><span class="sxs-lookup"><span data-stu-id="22505-135">See also</span></span>

- <span data-ttu-id="22505-136">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22505-136">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="22505-137">Запросы</span><span class="sxs-lookup"><span data-stu-id="22505-137">Queries</span></span>](index.md)
- [<span data-ttu-id="22505-138">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="22505-138">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="22505-139">Предложение From</span><span class="sxs-lookup"><span data-stu-id="22505-139">From Clause</span></span>](from-clause.md)
