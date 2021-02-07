---
description: 'Дополнительные сведения о: CREATEREF (Entity SQL)'
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c4e96f97bd3587e50b34f6cbd63c5ae9ed8d94ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724782"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="64a1d-103">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="64a1d-103">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="64a1d-104">Формирует ссылки на сущность в наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="64a1d-104">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a1d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64a1d-105">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="64a1d-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="64a1d-106">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="64a1d-107">Идентификатор набора сущностей, а не строковый литерал.</span><span class="sxs-lookup"><span data-stu-id="64a1d-107">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="64a1d-108">Выражение типа строки таблицы, соответствующее свойствам ключа типа сущности.</span><span class="sxs-lookup"><span data-stu-id="64a1d-108">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a1d-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="64a1d-109">Remarks</span></span>  

 <span data-ttu-id="64a1d-110">Выражение`row_typed_expression` должно быть структурно эквивалентно типу ключа для данной сущности.</span><span class="sxs-lookup"><span data-stu-id="64a1d-110">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="64a1d-111">Это значит, что оно должно иметь такое же число и типы полей, расположенные в том же порядке, как и ключи сущности.</span><span class="sxs-lookup"><span data-stu-id="64a1d-111">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="64a1d-112">В приведенном далее примере Orders и BadOrders являются наборами сущностей типа Order, и предполагается, что идентификатор Id является единственным свойством ключа для типа Order.</span><span class="sxs-lookup"><span data-stu-id="64a1d-112">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="64a1d-113">Этот пример иллюстрирует, как можно сформировать ссылку на сущность в наборе сущностей BadOrders.</span><span class="sxs-lookup"><span data-stu-id="64a1d-113">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="64a1d-114">Отметим, что ссылка может быть висячей.</span><span class="sxs-lookup"><span data-stu-id="64a1d-114">Note that the reference may be dangling.</span></span>  <span data-ttu-id="64a1d-115">Это значит, что в действительности ссылка может не указывать на конкретную сущность.</span><span class="sxs-lookup"><span data-stu-id="64a1d-115">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="64a1d-116">В этом случае оператор `DEREF` для этой ссылки возвратит значение null.</span><span class="sxs-lookup"><span data-stu-id="64a1d-116">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="64a1d-117">Пример</span><span class="sxs-lookup"><span data-stu-id="64a1d-117">Example</span></span>  

 <span data-ttu-id="64a1d-118">В следующем запросе Entity SQL оператор CREATEREF используется для формирования ссылок на сущность в наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="64a1d-118">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="64a1d-119">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="64a1d-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="64a1d-120">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="64a1d-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="64a1d-121">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="64a1d-121">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="64a1d-122">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="64a1d-122">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="64a1d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="64a1d-123">See also</span></span>

- [<span data-ttu-id="64a1d-124">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="64a1d-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="64a1d-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="64a1d-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="64a1d-126">KEY</span><span class="sxs-lookup"><span data-stu-id="64a1d-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="64a1d-127">ЗНАЧ</span><span class="sxs-lookup"><span data-stu-id="64a1d-127">REF</span></span>](ref-entity-sql.md)
