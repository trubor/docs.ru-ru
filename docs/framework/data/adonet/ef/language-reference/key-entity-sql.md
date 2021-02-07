---
description: 'Дополнительные сведения: KEY (Entity SQL)'
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 83901a378c3bcc92436df734a04cb7fdf639ecb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748301"
---
# <a name="key-entity-sql"></a><span data-ttu-id="ea7a4-103">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ea7a4-103">KEY (Entity SQL)</span></span>

<span data-ttu-id="ea7a4-104">Извлекает ключ ссылки или выражение сущности.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-104">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7a4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ea7a4-105">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="ea7a4-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="ea7a4-106">Remarks</span></span>  

 <span data-ttu-id="ea7a4-107">Ключ сущности содержит значения ключа в правильном порядке указанной сущности или ссылки на сущность.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-107">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="ea7a4-108">На одном и том же типе сущности могут быть основаны разные наборы сущностей, поэтому в каждом наборе сущностей может появиться одинаковый ключ.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-108">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="ea7a4-109">Для получения уникальной ссылки используйте `REF`.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-109">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="ea7a4-110">Возвращаемый тип оператора KEY – это тип строки, включающий одно поле для каждого ключа сущности в том же порядке.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-110">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="ea7a4-111">В следующем примере оператору ключа передается ссылка на сущность BadOrder, и он возвращает ключевую часть этой ссылки.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-111">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="ea7a4-112">В данном случае – тип записи точно с одним полем, соответствующим свойству `Id` .</span><span class="sxs-lookup"><span data-stu-id="ea7a4-112">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="ea7a4-113">Пример</span><span class="sxs-lookup"><span data-stu-id="ea7a4-113">Example</span></span>  

 <span data-ttu-id="ea7a4-114">В следующем запросе Entity SQL используется оператор KEY с целью извлечения ключевой части выражения со ссылкой на тип.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-114">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="ea7a4-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ea7a4-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="ea7a4-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ea7a4-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ea7a4-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ea7a4-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ea7a4-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="ea7a4-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ea7a4-119">See also</span></span>

- [<span data-ttu-id="ea7a4-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ea7a4-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ea7a4-121">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ea7a4-121">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="ea7a4-122">ЗНАЧ</span><span class="sxs-lookup"><span data-stu-id="ea7a4-122">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="ea7a4-123">DEREF</span><span class="sxs-lookup"><span data-stu-id="ea7a4-123">DEREF</span></span>](deref-entity-sql.md)
