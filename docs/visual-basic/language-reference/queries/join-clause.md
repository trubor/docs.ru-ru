---
description: Дополнительные сведения о предложении JOIN (Visual Basic)
title: Предложение Join
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 69d808e68a32b3f8799dabbbc8abc53acae42b57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700446"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="187bb-103">Предложение Join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="187bb-103">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="187bb-104">Объединяет две коллекции в одну.</span><span class="sxs-lookup"><span data-stu-id="187bb-104">Combines two collections into a single collection.</span></span> <span data-ttu-id="187bb-105">Операция Join основана на совпадающих ключах и использует `Equals` оператор.</span><span class="sxs-lookup"><span data-stu-id="187bb-105">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="187bb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="187bb-106">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="187bb-107">Компоненты</span><span class="sxs-lookup"><span data-stu-id="187bb-107">Parts</span></span>

<span data-ttu-id="187bb-108">`element` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="187bb-108">`element` Required.</span></span> <span data-ttu-id="187bb-109">Управляющая переменная для объединяемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="187bb-109">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="187bb-110">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="187bb-110">Required.</span></span> <span data-ttu-id="187bb-111">Коллекция для объединения с коллекцией, указанной в левой части `Join` оператора.</span><span class="sxs-lookup"><span data-stu-id="187bb-111">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="187bb-112">`Join`Предложение может быть вложенным в другое `Join` предложение или в `Group Join` предложении.</span><span class="sxs-lookup"><span data-stu-id="187bb-112">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="187bb-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="187bb-113">Optional.</span></span> <span data-ttu-id="187bb-114">Одно или несколько дополнительных `Join` предложений для дальнейшего уточнения запроса.</span><span class="sxs-lookup"><span data-stu-id="187bb-114">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="187bb-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="187bb-115">Optional.</span></span> <span data-ttu-id="187bb-116">Одно или несколько дополнительных `Group Join` предложений для дальнейшего уточнения запроса.</span><span class="sxs-lookup"><span data-stu-id="187bb-116">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="187bb-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="187bb-117">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="187bb-118">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="187bb-118">Required.</span></span> <span data-ttu-id="187bb-119">Определяет ключи для соединяемых коллекций.</span><span class="sxs-lookup"><span data-stu-id="187bb-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="187bb-120">`Equals`Для сравнения ключей из объединяемых коллекций необходимо использовать оператор.</span><span class="sxs-lookup"><span data-stu-id="187bb-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="187bb-121">Условия объединения можно комбинировать с помощью `And` оператора для обнаружения нескольких ключей.</span><span class="sxs-lookup"><span data-stu-id="187bb-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="187bb-122">`key1` должен быть из коллекции в левой части `Join` оператора.</span><span class="sxs-lookup"><span data-stu-id="187bb-122">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="187bb-123">`key2` должен находиться в коллекции с правой стороны `Join` оператора.</span><span class="sxs-lookup"><span data-stu-id="187bb-123">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="187bb-124">Ключи, используемые в условии объединения, могут быть выражениями, включающими более одного элемента из коллекции.</span><span class="sxs-lookup"><span data-stu-id="187bb-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="187bb-125">Однако каждое ключевое выражение может содержать только элементы из соответствующей коллекции.</span><span class="sxs-lookup"><span data-stu-id="187bb-125">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="187bb-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="187bb-126">Remarks</span></span>

<span data-ttu-id="187bb-127">`Join`Предложение объединяет две коллекции на основе совпадающих значений ключей из объединяемых коллекций.</span><span class="sxs-lookup"><span data-stu-id="187bb-127">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="187bb-128">Результирующая коллекция может содержать любое сочетание значений из коллекции, указанной в левой части `Join` оператора, и коллекции, указанной в `Join` предложении.</span><span class="sxs-lookup"><span data-stu-id="187bb-128">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="187bb-129">Запрос возвратит только результаты, для которых выполняется условие, заданное `Equals` оператором.</span><span class="sxs-lookup"><span data-stu-id="187bb-129">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="187bb-130">Это эквивалентно `INNER JOIN` в SQL.</span><span class="sxs-lookup"><span data-stu-id="187bb-130">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="187bb-131">`Join`Для объединения двух или более коллекций в одну коллекцию можно использовать несколько предложений в запросе.</span><span class="sxs-lookup"><span data-stu-id="187bb-131">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="187bb-132">Можно выполнить неявное соединение для объединения коллекций без `Join` предложения.</span><span class="sxs-lookup"><span data-stu-id="187bb-132">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="187bb-133">Для этого включите `In` в предложение несколько предложений `From` и укажите `Where` предложение, определяющее ключи, которые необходимо использовать для объединения.</span><span class="sxs-lookup"><span data-stu-id="187bb-133">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="187bb-134">Предложение можно использовать `Group Join` для объединения коллекций в одну иерархическую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="187bb-134">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="187bb-135">Это похоже на `LEFT OUTER JOIN` в SQL.</span><span class="sxs-lookup"><span data-stu-id="187bb-135">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="187bb-136">Пример</span><span class="sxs-lookup"><span data-stu-id="187bb-136">Example</span></span>

<span data-ttu-id="187bb-137">В следующем примере кода выполняется неявное соединение для объединения списка клиентов с их заказами.</span><span class="sxs-lookup"><span data-stu-id="187bb-137">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="187bb-138">Пример</span><span class="sxs-lookup"><span data-stu-id="187bb-138">Example</span></span>

<span data-ttu-id="187bb-139">В следующем примере кода две коллекции объединяются с помощью `Join` предложения.</span><span class="sxs-lookup"><span data-stu-id="187bb-139">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="187bb-140">В этом примере выводятся выходные данные, аналогичные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="187bb-140">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="187bb-141">Пример</span><span class="sxs-lookup"><span data-stu-id="187bb-141">Example</span></span>

<span data-ttu-id="187bb-142">В следующем примере кода две коллекции соединяются с помощью `Join` предложения с двумя ключевыми столбцами.</span><span class="sxs-lookup"><span data-stu-id="187bb-142">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="187bb-143">В примере будет выведен результат, аналогичный приведенному ниже:</span><span class="sxs-lookup"><span data-stu-id="187bb-143">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="187bb-144">См. также</span><span class="sxs-lookup"><span data-stu-id="187bb-144">See also</span></span>

- <span data-ttu-id="187bb-145">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="187bb-145">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="187bb-146">Запросы</span><span class="sxs-lookup"><span data-stu-id="187bb-146">Queries</span></span>](index.md)
- [<span data-ttu-id="187bb-147">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="187bb-147">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="187bb-148">Предложение From</span><span class="sxs-lookup"><span data-stu-id="187bb-148">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="187bb-149">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="187bb-149">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="187bb-150">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="187bb-150">Where Clause</span></span>](where-clause.md)
