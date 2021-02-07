---
description: Дополнительные сведения о предложении GROUP BY (Visual Basic)
title: Предложение Group By
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: f5cfb76b0f4b1d191f959ae1812140c6872e93bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700511"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="124ed-103">Предложение Group By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="124ed-103">Group By Clause (Visual Basic)</span></span>

<span data-ttu-id="124ed-104">Группирует элементы результата запроса.</span><span class="sxs-lookup"><span data-stu-id="124ed-104">Groups the elements of a query result.</span></span> <span data-ttu-id="124ed-105">Может также использоваться для применения агрегатных функций к каждой группе.</span><span class="sxs-lookup"><span data-stu-id="124ed-105">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="124ed-106">Операция группирования основана на одном или нескольких ключах.</span><span class="sxs-lookup"><span data-stu-id="124ed-106">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124ed-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="124ed-107">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="124ed-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="124ed-108">Parts</span></span>  
  
- <span data-ttu-id="124ed-109">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="124ed-109">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="124ed-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="124ed-110">Optional.</span></span> <span data-ttu-id="124ed-111">Одно или несколько полей переменной или переменных запроса, которые явно определяют поля для включения в сгруппированный результат.</span><span class="sxs-lookup"><span data-stu-id="124ed-111">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="124ed-112">Если поля не указаны, в сгруппированный результат включаются все поля из переменной или переменных запроса.</span><span class="sxs-lookup"><span data-stu-id="124ed-112">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="124ed-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="124ed-113">Required.</span></span> <span data-ttu-id="124ed-114">Выражение, которое определяет ключ, используемый для определения групп элементов.</span><span class="sxs-lookup"><span data-stu-id="124ed-114">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="124ed-115">Вы можете указать несколько ключей, чтобы задать составной ключ.</span><span class="sxs-lookup"><span data-stu-id="124ed-115">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="124ed-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="124ed-116">Optional.</span></span> <span data-ttu-id="124ed-117">Один или несколько дополнительных ключей, которые объединяются с `keyExp1` для создания составного ключа.</span><span class="sxs-lookup"><span data-stu-id="124ed-117">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="124ed-118">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="124ed-118">Required.</span></span> <span data-ttu-id="124ed-119">Одно или несколько выражений, определяющих способ агрегирования групп.</span><span class="sxs-lookup"><span data-stu-id="124ed-119">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="124ed-120">Чтобы определить имя элемента для результатов группирования, используйте ключевое слово `Group` , которое может быть в одной из следующих форм:</span><span class="sxs-lookup"><span data-stu-id="124ed-120">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="124ed-121">-или-</span><span class="sxs-lookup"><span data-stu-id="124ed-121">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="124ed-122">Вы также можете включать агрегатные функции для применения к группе.</span><span class="sxs-lookup"><span data-stu-id="124ed-122">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="124ed-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="124ed-123">Remarks</span></span>  

 <span data-ttu-id="124ed-124">Чтобы разбить результат ы запроса на группы, можно использовать предложение `Group By` .</span><span class="sxs-lookup"><span data-stu-id="124ed-124">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="124ed-125">Группирование основывается на ключе или составном ключе, состоящем из нескольких ключей.</span><span class="sxs-lookup"><span data-stu-id="124ed-125">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="124ed-126">Элементы, связанные с соответствующими значениями ключа, включаются в одну и ту же группу.</span><span class="sxs-lookup"><span data-stu-id="124ed-126">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="124ed-127">Чтобы определить имя элемента, используемое для ссылки на группу, применяется параметр `aggregateList` предложения `Into` и ключевое слово `Group` .</span><span class="sxs-lookup"><span data-stu-id="124ed-127">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="124ed-128">Вы также можете включать в предложение `Into` агрегатные функции, чтобы вычислять значения для сгруппированных элементов.</span><span class="sxs-lookup"><span data-stu-id="124ed-128">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="124ed-129">Список стандартных агрегатных функций см. в разделе [Aggregate Clause](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="124ed-129">For a list of standard aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="124ed-130">Пример</span><span class="sxs-lookup"><span data-stu-id="124ed-130">Example</span></span>  

 <span data-ttu-id="124ed-131">Следующий пример кода группирует список клиентов по их расположению (стране или региону) и предоставляет количество клиентов в каждой группе.</span><span class="sxs-lookup"><span data-stu-id="124ed-131">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="124ed-132">Результаты упорядочиваются по названию страны или региона.</span><span class="sxs-lookup"><span data-stu-id="124ed-132">The results are ordered by country/region name.</span></span> <span data-ttu-id="124ed-133">Результаты группирования упорядочиваются по названию города.</span><span class="sxs-lookup"><span data-stu-id="124ed-133">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="124ed-134">См. также</span><span class="sxs-lookup"><span data-stu-id="124ed-134">See also</span></span>

- <span data-ttu-id="124ed-135">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="124ed-135">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="124ed-136">Запросы</span><span class="sxs-lookup"><span data-stu-id="124ed-136">Queries</span></span>](index.md)
- [<span data-ttu-id="124ed-137">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="124ed-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="124ed-138">Предложение From</span><span class="sxs-lookup"><span data-stu-id="124ed-138">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="124ed-139">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="124ed-139">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="124ed-140">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="124ed-140">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="124ed-141">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="124ed-141">Group Join Clause</span></span>](group-join-clause.md)
