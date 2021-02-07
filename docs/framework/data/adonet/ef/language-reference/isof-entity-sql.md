---
description: 'Дополнительные сведения о: ISOF (Entity SQL)'
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 4a44ddc74ef16ec16285132f6567ca2500e173a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748353"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="ba38e-103">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ba38e-103">ISOF (Entity SQL)</span></span>

<span data-ttu-id="ba38e-104">Определяет, относится ли тип выражения к указанному типу или одному из его подтипов.</span><span class="sxs-lookup"><span data-stu-id="ba38e-104">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba38e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba38e-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba38e-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="ba38e-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ba38e-107">Любое допустимое выражение запроса для определения типа.</span><span class="sxs-lookup"><span data-stu-id="ba38e-107">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="ba38e-108">NOT</span><span class="sxs-lookup"><span data-stu-id="ba38e-108">NOT</span></span>  
 <span data-ttu-id="ba38e-109">Выполняет отрицание результата EDM.Boolean для IS OF.</span><span class="sxs-lookup"><span data-stu-id="ba38e-109">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="ba38e-110">ONLY</span><span class="sxs-lookup"><span data-stu-id="ba38e-110">ONLY</span></span>  
 <span data-ttu-id="ba38e-111">Указывает, что оператор IS OF возвращает значение `true` только в том случае, если выражение `expression` относится к типу `type`, а не одному из его подтипов.</span><span class="sxs-lookup"><span data-stu-id="ba38e-111">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="ba38e-112">Тип, по которому проверяется выражение `expression`.</span><span class="sxs-lookup"><span data-stu-id="ba38e-112">The type to test `expression` against.</span></span> <span data-ttu-id="ba38e-113">Для типа должно быть указано пространство имен.</span><span class="sxs-lookup"><span data-stu-id="ba38e-113">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba38e-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ba38e-114">Return Value</span></span>  

 <span data-ttu-id="ba38e-115">Значение `true`, если выражение `expression` относится к типу T, который является либо базовым типом, либо производным типом от типа `type`. Значение null, если выражение `expression` во время выполнения имеет значение null. В противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="ba38e-115">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba38e-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba38e-116">Remarks</span></span>  

 <span data-ttu-id="ba38e-117">Выражения `expression IS NOT OF (type)` и `expression IS NOT OF (ONLY type)` являются синтаксически эквивалентными для `NOT (expression IS OF (type))` и `NOT (expression IS OF (ONLY type))` соответственно.</span><span class="sxs-lookup"><span data-stu-id="ba38e-117">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="ba38e-118">В следующей таблице показано, каким образом оператор `IS OF` работает с некоторыми стандартными и нестандартными конструкциями.</span><span class="sxs-lookup"><span data-stu-id="ba38e-118">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="ba38e-119">Все исключения формируются на стороне клиента перед вызовом поставщика.</span><span class="sxs-lookup"><span data-stu-id="ba38e-119">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="ba38e-120">Шаблон</span><span class="sxs-lookup"><span data-stu-id="ba38e-120">Pattern</span></span>|<span data-ttu-id="ba38e-121">Поведение</span><span class="sxs-lookup"><span data-stu-id="ba38e-121">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="ba38e-122">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-122">null IS OF (EntityType)</span></span>|<span data-ttu-id="ba38e-123">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-123">Throws</span></span>|  
|<span data-ttu-id="ba38e-124">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-124">null IS OF (ComplexType)</span></span>|<span data-ttu-id="ba38e-125">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-125">Throws</span></span>|  
|<span data-ttu-id="ba38e-126">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-126">null IS OF (RowType)</span></span>|<span data-ttu-id="ba38e-127">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-127">Throws</span></span>|  
|<span data-ttu-id="ba38e-128">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-128">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="ba38e-129">Возвращает DBNull</span><span class="sxs-lookup"><span data-stu-id="ba38e-129">Returns DBNull</span></span>|  
|<span data-ttu-id="ba38e-130">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-130">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="ba38e-131">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-131">Throws</span></span>|  
|<span data-ttu-id="ba38e-132">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-132">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="ba38e-133">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-133">Throws</span></span>|  
|<span data-ttu-id="ba38e-134">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-134">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="ba38e-135">Возвращает значение true или false</span><span class="sxs-lookup"><span data-stu-id="ba38e-135">Returns true/false</span></span>|  
|<span data-ttu-id="ba38e-136">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-136">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="ba38e-137">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-137">Throws</span></span>|  
|<span data-ttu-id="ba38e-138">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="ba38e-138">RowType IS OF (RowType)</span></span>|<span data-ttu-id="ba38e-139">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="ba38e-139">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ba38e-140">Пример</span><span class="sxs-lookup"><span data-stu-id="ba38e-140">Example</span></span>  

 <span data-ttu-id="ba38e-141">В следующем [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запросе используется оператор is of для определения типа выражения запроса, а затем оператор TREAT используется для преобразования объекта курса типа в коллекцию объектов типа OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="ba38e-141">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="ba38e-142">Запрос основан на [модели School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ba38e-142">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="ba38e-143">[! code-SQL [DP Ентитисервицес основные понятия # TREAT_ISOF] ~/самплес/сниппетс/тскл/VS_Snippets_Data/DP ентитисервицес основные понятия/TSQL/ентитискл. SQL # treat_isof)]</span><span class="sxs-lookup"><span data-stu-id="ba38e-143">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba38e-144">См. также</span><span class="sxs-lookup"><span data-stu-id="ba38e-144">See also</span></span>

- [<span data-ttu-id="ba38e-145">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ba38e-145">Entity SQL Reference</span></span>](entity-sql-reference.md)
