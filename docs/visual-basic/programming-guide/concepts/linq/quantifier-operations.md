---
description: 'Дополнительные сведения: Операции квантификаторов (Visual Basic)'
title: Операции, использующие квантификаторы
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 7cbd8a9cf18a0ad8b70ada58d7fa6602dce4bd1b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430096"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="25539-103">Операции квантификаторов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25539-103">Quantifier Operations (Visual Basic)</span></span>

<span data-ttu-id="25539-104">Квантификаторы возвращают значение <xref:System.Boolean>, которое указывает, удовлетворяют ли условию некоторые или все элементы в последовательности.</span><span class="sxs-lookup"><span data-stu-id="25539-104">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="25539-105">На приведенном ниже рисунке показаны два различных квантификатора, примененные к двум разным исходным последовательностям.</span><span class="sxs-lookup"><span data-stu-id="25539-105">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="25539-106">Первая операция проверяет, является ли один или несколько элементов буквой "А"; результатом является `true`.</span><span class="sxs-lookup"><span data-stu-id="25539-106">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="25539-107">Вторая операция проверяет, являются ли все элементы буквой "А"; результатом является `true`.</span><span class="sxs-lookup"><span data-stu-id="25539-107">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Операции, использующие квантификаторы LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="25539-109">В следующем разделе перечислены методы стандартных операторов запросов, которые выполняют операции с использованием квантификаторов.</span><span class="sxs-lookup"><span data-stu-id="25539-109">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25539-110">Методы</span><span class="sxs-lookup"><span data-stu-id="25539-110">Methods</span></span>  
  
|<span data-ttu-id="25539-111">Имя метода</span><span class="sxs-lookup"><span data-stu-id="25539-111">Method Name</span></span>|<span data-ttu-id="25539-112">Описание</span><span class="sxs-lookup"><span data-stu-id="25539-112">Description</span></span>|<span data-ttu-id="25539-113">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25539-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="25539-114">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="25539-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="25539-115">Все</span><span class="sxs-lookup"><span data-stu-id="25539-115">All</span></span>|<span data-ttu-id="25539-116">Определяет, все ли элементы последовательности удовлетворяют условию.</span><span class="sxs-lookup"><span data-stu-id="25539-116">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25539-117">Любой</span><span class="sxs-lookup"><span data-stu-id="25539-117">Any</span></span>|<span data-ttu-id="25539-118">Определяет, удовлетворяют ли условию какие-либо элементы последовательности.</span><span class="sxs-lookup"><span data-stu-id="25539-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25539-119">Содержит</span><span class="sxs-lookup"><span data-stu-id="25539-119">Contains</span></span>|<span data-ttu-id="25539-120">Определяет, содержит ли последовательность указанный элемент.</span><span class="sxs-lookup"><span data-stu-id="25539-120">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="25539-121">Не применяется</span><span class="sxs-lookup"><span data-stu-id="25539-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="25539-122">Примеры синтаксиса выражений запросов</span><span class="sxs-lookup"><span data-stu-id="25539-122">Query Expression Syntax Examples</span></span>  

 <span data-ttu-id="25539-123">В этих примерах используется `Aggregate` предложение в Visual Basic в качестве части условия фильтрации в запросе LINQ.</span><span class="sxs-lookup"><span data-stu-id="25539-123">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="25539-124">В следующем примере используется `Aggregate` предложение и <xref:System.Linq.Enumerable.All%2A> метод расширения для возврата из коллекции тех, чьи пользователи, pets все старше указанного возраста.</span><span class="sxs-lookup"><span data-stu-id="25539-124">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="25539-125">В следующем примере используется `Aggregate` предложение и <xref:System.Linq.Enumerable.Any%2A> метод расширения для возврата из коллекции пользователей, у которых есть по крайней мере один Pet, который старше указанного возраста.</span><span class="sxs-lookup"><span data-stu-id="25539-125">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="25539-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="25539-126">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="25539-127">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25539-127">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="25539-128">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="25539-128">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="25539-129">Практическое руководство. Запрос к предложениям, содержащим указанный набор слов (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25539-129">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
