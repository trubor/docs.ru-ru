---
description: Предложение where. Справочник по C#
title: Предложение where. Справочник по C#
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141690"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="79b08-103">Предложение where (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="79b08-103">where clause (C# Reference)</span></span>

<span data-ttu-id="79b08-104">Предложение `where` используется в выражении запроса для того, чтобы указать, какие элементы из источника данных будут возвращаться в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="79b08-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="79b08-105">Оно применяет логическое условие (*предикат*) к каждому исходному элементу (на который ссылается переменная диапазона) и возвращает те из них, для которых указанное условие имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="79b08-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="79b08-106">Одно выражение запроса может содержать сразу несколько предложений `where`, а одно предложение — несколько частей выражения предиката.</span><span class="sxs-lookup"><span data-stu-id="79b08-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="79b08-107">Пример</span><span class="sxs-lookup"><span data-stu-id="79b08-107">Example</span></span>

<span data-ttu-id="79b08-108">В следующем примере предложение `where` отфильтровывает все номера, кроме тех, которые меньше пяти.</span><span class="sxs-lookup"><span data-stu-id="79b08-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="79b08-109">Если удалить предложение `where`, возвращаются все номера из источника данных.</span><span class="sxs-lookup"><span data-stu-id="79b08-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="79b08-110">Выражение `num < 5` является предикатом, который применяется к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="79b08-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="79b08-111">Пример</span><span class="sxs-lookup"><span data-stu-id="79b08-111">Example</span></span>

<span data-ttu-id="79b08-112">В одном предложении `where` можно указать необходимое число предикатов, используя операторы [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) и [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="79b08-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="79b08-113">В следующем примере запрос определяет два предиката, позволяющие отобрать только четные номера меньше пяти.</span><span class="sxs-lookup"><span data-stu-id="79b08-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="79b08-114">Пример</span><span class="sxs-lookup"><span data-stu-id="79b08-114">Example</span></span>

<span data-ttu-id="79b08-115">Предложение `where` может содержать один или несколько методов, возвращающих логические значения.</span><span class="sxs-lookup"><span data-stu-id="79b08-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="79b08-116">В следующем примере предложение `where` использует метод для того, чтобы определить, является ли текущее значение диапазона четным или нечетным.</span><span class="sxs-lookup"><span data-stu-id="79b08-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="79b08-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="79b08-117">Remarks</span></span>

<span data-ttu-id="79b08-118">Предложение `where` представляет собой механизм фильтрации.</span><span class="sxs-lookup"><span data-stu-id="79b08-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="79b08-119">Он может располагаться практически в любом месте выражения запроса, но не может быть первым или последним предложением.</span><span class="sxs-lookup"><span data-stu-id="79b08-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="79b08-120">Предложение `where` может отображаться до или после предложения [group](group-clause.md) в зависимости от того, необходимо ли отфильтровать исходные элементы до или после их объединения в группы.</span><span class="sxs-lookup"><span data-stu-id="79b08-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="79b08-121">Если указанный предикат недопустим для элементов в источнике данных, это вызовет ошибку компиляции.</span><span class="sxs-lookup"><span data-stu-id="79b08-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="79b08-122">Это одно из преимуществ надежной проверки типов, предоставляемой LINQ.</span><span class="sxs-lookup"><span data-stu-id="79b08-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="79b08-123">Во время компиляции ключевое слово `where` преобразуется в вызов метода стандартного оператора запроса <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="79b08-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="79b08-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="79b08-124">See also</span></span>

- [<span data-ttu-id="79b08-125">Ключевые слова запроса (LINQ)</span><span class="sxs-lookup"><span data-stu-id="79b08-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="79b08-126">предложение from</span><span class="sxs-lookup"><span data-stu-id="79b08-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="79b08-127">предложение select</span><span class="sxs-lookup"><span data-stu-id="79b08-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="79b08-128">Фильтрация данных</span><span class="sxs-lookup"><span data-stu-id="79b08-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="79b08-129">LINQ в C#</span><span class="sxs-lookup"><span data-stu-id="79b08-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="79b08-130">LINQ</span><span class="sxs-lookup"><span data-stu-id="79b08-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
