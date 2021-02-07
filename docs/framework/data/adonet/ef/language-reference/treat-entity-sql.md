---
description: 'Дополнительные сведения о: TREAT (Entity SQL)'
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 3f014cac631d246b35d145cdb80c9aa6ac401524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673431"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="14e71-103">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14e71-103">TREAT (Entity SQL)</span></span>

<span data-ttu-id="14e71-104">Обрабатывает объект некоторого базового типа, как объект указанного производного типа.</span><span class="sxs-lookup"><span data-stu-id="14e71-104">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e71-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14e71-105">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="14e71-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="14e71-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="14e71-107">Любое допустимое выражение запроса, возвращающее сущность.</span><span class="sxs-lookup"><span data-stu-id="14e71-107">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14e71-108">Тип указанного выражения должен быть подтипом указанного типа данных, либо тип данных должен быть подтипом типа выражения.</span><span class="sxs-lookup"><span data-stu-id="14e71-108">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="14e71-109">Тип сущности.</span><span class="sxs-lookup"><span data-stu-id="14e71-109">An entity type.</span></span> <span data-ttu-id="14e71-110">Для типа должно быть указано пространство имен.</span><span class="sxs-lookup"><span data-stu-id="14e71-110">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14e71-111">Указанное выражение должно быть подтипом указанного типа данных, либо тип данных должен быть подтипом данного выражения.</span><span class="sxs-lookup"><span data-stu-id="14e71-111">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14e71-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="14e71-112">Return Value</span></span>  

 <span data-ttu-id="14e71-113">Значение указанного типа данных.</span><span class="sxs-lookup"><span data-stu-id="14e71-113">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e71-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="14e71-114">Remarks</span></span>  

 <span data-ttu-id="14e71-115">Оператор TREAT предназначен для приведения связанных классов к базовому типу.</span><span class="sxs-lookup"><span data-stu-id="14e71-115">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="14e71-116">Например, если тип `Employee` является производным от типа `Person` , а «p» относится к типу `Person`, то выражение `TREAT(p AS NamespaceName.Employee)` приводит общий экземпляр типа `Person` к типу `Employee`. Иными словами, он позволяет обрабатывать «p» как тип `Employee`.</span><span class="sxs-lookup"><span data-stu-id="14e71-116">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="14e71-117">Оператор TREAT используется в сценариях наследования, в которых можно выполнить запрос наподобие следующего.</span><span class="sxs-lookup"><span data-stu-id="14e71-117">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="14e71-118">Этот запрос приводит сущности `Person` к типу `Employee` .</span><span class="sxs-lookup"><span data-stu-id="14e71-118">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="14e71-119">Если значение «p» фактически не относится к типу `Employee`, то выражение имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="14e71-119">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14e71-120">Указанное выражение `Employee` должно быть подтипом указанного типа данных `Person` , либо тип данных должен быть подтипом выражения.</span><span class="sxs-lookup"><span data-stu-id="14e71-120">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="14e71-121">В противном случае это выражение вызовет ошибку во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="14e71-121">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="14e71-122">Следующая таблица показывает, каким образом оператор TREAT работает с некоторыми стандартными и не очень часто используемыми конструкциями.</span><span class="sxs-lookup"><span data-stu-id="14e71-122">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="14e71-123">Все исключения формируются на стороне клиента перед вызовом поставщика.</span><span class="sxs-lookup"><span data-stu-id="14e71-123">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="14e71-124">Шаблон</span><span class="sxs-lookup"><span data-stu-id="14e71-124">Pattern</span></span>|<span data-ttu-id="14e71-125">Поведение</span><span class="sxs-lookup"><span data-stu-id="14e71-125">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="14e71-126">Возвращает `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="14e71-126">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="14e71-127">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="14e71-127">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="14e71-128">Создает исключение/</span><span class="sxs-lookup"><span data-stu-id="14e71-128">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="14e71-129">Возвращает значение `EntityType` или `null`.</span><span class="sxs-lookup"><span data-stu-id="14e71-129">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="14e71-130">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="14e71-130">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="14e71-131">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="14e71-131">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14e71-132">Пример</span><span class="sxs-lookup"><span data-stu-id="14e71-132">Example</span></span>  

 <span data-ttu-id="14e71-133">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор TREAT используется для преобразования объекта типа Course в коллекцию объектов типа OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="14e71-133">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="14e71-134">Запрос основан на [модели School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14e71-134">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="14e71-135">См. также</span><span class="sxs-lookup"><span data-stu-id="14e71-135">See also</span></span>

- [<span data-ttu-id="14e71-136">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14e71-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="14e71-137">Допускающие значения NULL структурированные типы</span><span class="sxs-lookup"><span data-stu-id="14e71-137">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
