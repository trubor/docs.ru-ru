---
description: 'Дополнительные сведения о: DEREF (Entity SQL)'
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 9d0f29123c1459c6eab21ea9cd860b5c9e77f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724730"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="5d3d8-103">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5d3d8-103">DEREF (Entity SQL)</span></span>

<span data-ttu-id="5d3d8-104">Разыменовывает значение ссылки и выдает результат разыменования.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-104">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3d8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d3d8-105">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="5d3d8-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5d3d8-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="5d3d8-107">Любое допустимое выражение запроса, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d3d8-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5d3d8-108">Return Value</span></span>  

 <span data-ttu-id="5d3d8-109">Значение сущности, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-109">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d3d8-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d3d8-110">Remarks</span></span>  

 <span data-ttu-id="5d3d8-111">Оператор DEREF разыменовывает значение ссылки и выдает результат разыменования.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-111">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="5d3d8-112">Например, если `r` является ссылкой на тип ref \<T> , `Deref(r)` то является выражением типа `T` , который возвращает сущность, на которую ссылается `r` .</span><span class="sxs-lookup"><span data-stu-id="5d3d8-112">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="5d3d8-113">Если ссылка имеет значение null или висячее значение (т. е. цель ссылки не существует), то результатом оператора DEREF будет значение null.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-113">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d3d8-114">Пример</span><span class="sxs-lookup"><span data-stu-id="5d3d8-114">Example</span></span>  

 <span data-ttu-id="5d3d8-115">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор DEREF используется для разыменования значения ссылки и возврата результата разыменования.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="5d3d8-116">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5d3d8-117">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5d3d8-118">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5d3d8-118">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="5d3d8-119">Передайте методу ExecutePrimitiveTypeQuery следующий запрос в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="5d3d8-119">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="5d3d8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="5d3d8-120">See also</span></span>

- [<span data-ttu-id="5d3d8-121">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5d3d8-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5d3d8-122">ЗНАЧ</span><span class="sxs-lookup"><span data-stu-id="5d3d8-122">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="5d3d8-123">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="5d3d8-123">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="5d3d8-124">KEY</span><span class="sxs-lookup"><span data-stu-id="5d3d8-124">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="5d3d8-125">Допускающие значения NULL структурированные типы</span><span class="sxs-lookup"><span data-stu-id="5d3d8-125">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
