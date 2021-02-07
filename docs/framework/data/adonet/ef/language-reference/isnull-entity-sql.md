---
description: 'Дополнительные сведения: ISNULL (Entity SQL)'
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1dbaf964facf089ab6714ebd58baf8b040288cff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748496"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="e5042-103">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e5042-103">ISNULL (Entity SQL)</span></span>

<span data-ttu-id="e5042-104">Определяет, имеет ли выражение запроса значение null.</span><span class="sxs-lookup"><span data-stu-id="e5042-104">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5042-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5042-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5042-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e5042-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e5042-107">Любое допустимое выражение запроса.</span><span class="sxs-lookup"><span data-stu-id="e5042-107">Any valid query expression.</span></span> <span data-ttu-id="e5042-108">Не может быть коллекцией, содержать элементы коллекции или тип записи со свойствами типа коллекции.</span><span class="sxs-lookup"><span data-stu-id="e5042-108">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="e5042-109">NOT</span><span class="sxs-lookup"><span data-stu-id="e5042-109">NOT</span></span>  
 <span data-ttu-id="e5042-110">Логически инвертирует результат EDM.Boolean для IS NULL.</span><span class="sxs-lookup"><span data-stu-id="e5042-110">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5042-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e5042-111">Return Value</span></span>  

 <span data-ttu-id="e5042-112">Значение `true`, если выражение `expression` возвращает значение NULL, либо значение `false` - в противном случае.</span><span class="sxs-lookup"><span data-stu-id="e5042-112">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5042-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="e5042-113">Remarks</span></span>  

 <span data-ttu-id="e5042-114">Ключевое слово `IS NULL` позволяет определить, имеет ли элемент внешнего соединения значение NULL.</span><span class="sxs-lookup"><span data-stu-id="e5042-114">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="e5042-115">Ключевое слово `IS NULL` позволяет определить, имеет ли элемент фактическое значение.</span><span class="sxs-lookup"><span data-stu-id="e5042-115">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="e5042-116">В следующей таблице показан эффект применения оператора `IS NULL` в различных конструкциях.</span><span class="sxs-lookup"><span data-stu-id="e5042-116">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="e5042-117">Все исключения формируются на стороне клиента перед вызовом поставщика.</span><span class="sxs-lookup"><span data-stu-id="e5042-117">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e5042-118">Шаблон</span><span class="sxs-lookup"><span data-stu-id="e5042-118">Pattern</span></span>|<span data-ttu-id="e5042-119">Поведение</span><span class="sxs-lookup"><span data-stu-id="e5042-119">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e5042-120">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-120">null IS NULL</span></span>|<span data-ttu-id="e5042-121">Возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="e5042-121">Returns `true`.</span></span>|  
|<span data-ttu-id="e5042-122">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-122">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="e5042-123">Возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="e5042-123">Returns `true`.</span></span>|  
|<span data-ttu-id="e5042-124">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-124">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="e5042-125">Вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e5042-125">Throws an error.</span></span>|  
|<span data-ttu-id="e5042-126">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-126">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="e5042-127">Вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e5042-127">Throws an error.</span></span>|  
|<span data-ttu-id="e5042-128">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-128">EntityType IS NULL</span></span>|<span data-ttu-id="e5042-129">Возвращает значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="e5042-129">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="e5042-130">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-130">ComplexType IS NULL</span></span>|<span data-ttu-id="e5042-131">Вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e5042-131">Throws an error.</span></span>|  
|<span data-ttu-id="e5042-132">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="e5042-132">RowType IS NULL</span></span>|<span data-ttu-id="e5042-133">Вызывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="e5042-133">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5042-134">Пример</span><span class="sxs-lookup"><span data-stu-id="e5042-134">Example</span></span>  

 <span data-ttu-id="e5042-135">Следующий [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запрос использует оператор is not null, чтобы определить, имеет ли выражение запроса значение, не равное NULL.</span><span class="sxs-lookup"><span data-stu-id="e5042-135">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="e5042-136">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="e5042-136">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e5042-137">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="e5042-137">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e5042-138">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e5042-138">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e5042-139">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e5042-139">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="e5042-140">См. также</span><span class="sxs-lookup"><span data-stu-id="e5042-140">See also</span></span>

- [<span data-ttu-id="e5042-141">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e5042-141">Entity SQL Reference</span></span>](entity-sql-reference.md)
