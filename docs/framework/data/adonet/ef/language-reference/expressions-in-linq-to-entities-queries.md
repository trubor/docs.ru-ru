---
description: Дополнительные сведения о выражениях в запросах LINQ to Entities
title: Выражения в запросах LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 3ab9e04adb7e823538638ae262f0e481b6948a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786372"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="31aae-103">Выражения в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="31aae-103">Expressions in LINQ to Entities Queries</span></span>

<span data-ttu-id="31aae-104">Выражение представляет собой фрагмент кода, результатом вычисления которого является единственное значение, объект, метод или пространство имен.</span><span class="sxs-lookup"><span data-stu-id="31aae-104">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="31aae-105">Выражение может содержать литеральное значение, вызов метода, оператор с операндами или простое имя.</span><span class="sxs-lookup"><span data-stu-id="31aae-105">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="31aae-106">Простые имена могут быть именами переменной, элемента типа, параметра метода, пространства имен или типа.</span><span class="sxs-lookup"><span data-stu-id="31aae-106">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="31aae-107">В выражениях могут использоваться операторы, которые, в свою очередь, используют в качестве параметров другие выражения или вызовы методов, параметрами которых являются другие вызовы методов.</span><span class="sxs-lookup"><span data-stu-id="31aae-107">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="31aae-108">Таким образом, выражения могут быть как простыми, так и очень сложными.</span><span class="sxs-lookup"><span data-stu-id="31aae-108">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="31aae-109">В запросах LINQ to Entities выражения могут содержать все, что разрешено типами в <xref:System.Linq.Expressions> пространстве имен, включая лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="31aae-109">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="31aae-110">Выражения, которые могут использоваться в запросах LINQ to Entities, представляют собой надмножество выражений, которые можно использовать для запроса Entity Framework. выражения, которые являются частью запросов к Entity Framework, ограничены операциями, поддерживаемыми `ObjectQuery<T>` и базовым источником данных.</span><span class="sxs-lookup"><span data-stu-id="31aae-110">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="31aae-111">В следующем примере сравнение в предложении `Where` является следующим выражением.</span><span class="sxs-lookup"><span data-stu-id="31aae-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="31aae-112">Отдельные языковые конструкции, такие как C# `unchecked` , не имеют смысла в LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="31aae-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31aae-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="31aae-113">In This Section</span></span>  

 [<span data-ttu-id="31aae-114">Константные выражения</span><span class="sxs-lookup"><span data-stu-id="31aae-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="31aae-115">Выражения сравнения</span><span class="sxs-lookup"><span data-stu-id="31aae-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="31aae-116">Сравнения NULL</span><span class="sxs-lookup"><span data-stu-id="31aae-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="31aae-117">Выражения инициализации</span><span class="sxs-lookup"><span data-stu-id="31aae-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="31aae-118">Связи, свойства навигации и внешние ключи</span><span class="sxs-lookup"><span data-stu-id="31aae-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="31aae-119">См. также</span><span class="sxs-lookup"><span data-stu-id="31aae-119">See also</span></span>

- [<span data-ttu-id="31aae-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="31aae-120">ADO.NET Entity Framework</span></span>](../index.md)
