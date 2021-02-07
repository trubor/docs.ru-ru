---
description: 'Дополнительные сведения: выражения запроса (Entity SQL)'
title: Выражения запросов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 218e7db0e812bd43a92d3145bc4bf96244ef6a3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696039"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="3b31c-103">Выражения запросов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3b31c-103">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="3b31c-104">Выражение запроса объединяет в едином синтаксисе множество разных операторов запросов.</span><span class="sxs-lookup"><span data-stu-id="3b31c-104">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3b31c-105">предоставляет различные типы выражений, включая [литералы](literals-entity-sql.md), [Параметры](parameters-entity-sql.md), [переменные](variables-entity-sql.md), операторы, [функции](functions-entity-sql.md), операторы SET и т. д.</span><span class="sxs-lookup"><span data-stu-id="3b31c-105">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="3b31c-106">Дополнительные сведения см. в разделе [Справочник по Entity SQL](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="3b31c-106">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="3b31c-107">Предложения</span><span class="sxs-lookup"><span data-stu-id="3b31c-107">Clauses</span></span>  

 <span data-ttu-id="3b31c-108">Выражение запроса состоит из предложений, которые последовательно применяют операции к набору объектов.</span><span class="sxs-lookup"><span data-stu-id="3b31c-108">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="3b31c-109">Они основаны на тех же предложениях, которые находятся в стандартной инструкции SQL SELECT: [SELECT](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group By](group-by-entity-sql.md), [HAVING](having-entity-sql.md)и [ORDER BY](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3b31c-109">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="3b31c-110">Область</span><span class="sxs-lookup"><span data-stu-id="3b31c-110">Scope</span></span>  

 <span data-ttu-id="3b31c-111">Имена, определенные в предложении FROM, появляются в области FROM в порядке перечисления, слева направо.</span><span class="sxs-lookup"><span data-stu-id="3b31c-111">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="3b31c-112">В списке JOIN выражения могут ссылаться на имена, которые определены в списке ранее.</span><span class="sxs-lookup"><span data-stu-id="3b31c-112">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="3b31c-113">Открытые свойства элементов, указанные в предложении FROM, не добавляются в область FROM. На них всегда следует ссылаться через имя с псевдонимом.</span><span class="sxs-lookup"><span data-stu-id="3b31c-113">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="3b31c-114">Но обычно все части выражения выбора находятся в области FROM.</span><span class="sxs-lookup"><span data-stu-id="3b31c-114">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b31c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="3b31c-115">See also</span></span>

- [<span data-ttu-id="3b31c-116">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3b31c-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
