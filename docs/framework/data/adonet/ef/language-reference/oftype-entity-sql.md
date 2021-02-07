---
description: 'Дополнительные сведения о: OFTYPE (Entity SQL)'
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: d916ea4487fcc7a21f5fb62aa7e6f8a23d73fed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739343"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="db65b-103">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db65b-103">OFTYPE (Entity SQL)</span></span>

<span data-ttu-id="db65b-104">Возвращает коллекцию объектов из выражения запроса, которое относится к заданному типу.</span><span class="sxs-lookup"><span data-stu-id="db65b-104">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db65b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db65b-105">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="db65b-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="db65b-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="db65b-107">Любое допустимое выражение запроса, возвращающее коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="db65b-107">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="db65b-108">Тип, по которому проверяется каждый объект, возвращаемый `expression` .</span><span class="sxs-lookup"><span data-stu-id="db65b-108">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="db65b-109">Для типа должно быть указано пространство имен.</span><span class="sxs-lookup"><span data-stu-id="db65b-109">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db65b-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="db65b-110">Return Value</span></span>  

 <span data-ttu-id="db65b-111">Коллекция объектов, которые имеют тип `test_type`, базовый тип или тип, производный от `test_type`.</span><span class="sxs-lookup"><span data-stu-id="db65b-111">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="db65b-112">Если задан параметр ONLY, возвращаются только экземпляры `test_type` или пустая коллекция.</span><span class="sxs-lookup"><span data-stu-id="db65b-112">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db65b-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="db65b-113">Remarks</span></span>  

 <span data-ttu-id="db65b-114">Выражение `OFTYPE` задает выражение с определением типа, которое применяется для проверки типа по отношению к каждому элементу коллекции.</span><span class="sxs-lookup"><span data-stu-id="db65b-114">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="db65b-115">Выражение `OFTYPE` позволяет получить новую коллекцию указанного типа, содержащую только те элементы, которые были эквивалентны либо этому типу, либо его подтипу.</span><span class="sxs-lookup"><span data-stu-id="db65b-115">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="db65b-116">Выражение `OFTYPE` представляет собой сокращение следующего выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="db65b-116">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="db65b-117">Например, если предположить, что тип Manager представляет собой подтип Employee, то следующее выражение позволяет извлечь из коллекции сотрудников данные только менеджеров:</span><span class="sxs-lookup"><span data-stu-id="db65b-117">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="db65b-118">Можно также выполнить приведение коллекции с помощью фильтра типов:</span><span class="sxs-lookup"><span data-stu-id="db65b-118">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="db65b-119">Все руководители являются менеджерами компании, поэтому полученная в результате коллекция по-прежнему содержит данные всех руководителей, несмотря на то что теперь по своему типу она рассматривается как коллекция менеджеров.</span><span class="sxs-lookup"><span data-stu-id="db65b-119">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="db65b-120">В следующей таблице показано поведение оператора `OFTYPE` по отношению к некоторым шаблонам.</span><span class="sxs-lookup"><span data-stu-id="db65b-120">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="db65b-121">Все исключения активизируются на стороне клиента перед вызовом поставщика.</span><span class="sxs-lookup"><span data-stu-id="db65b-121">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="db65b-122">Шаблон</span><span class="sxs-lookup"><span data-stu-id="db65b-122">Pattern</span></span>|<span data-ttu-id="db65b-123">Поведение</span><span class="sxs-lookup"><span data-stu-id="db65b-123">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="db65b-124">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="db65b-124">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="db65b-125">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="db65b-125">Collection(EntityType)</span></span>|  
|<span data-ttu-id="db65b-126">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="db65b-126">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="db65b-127">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="db65b-127">Throws</span></span>|  
|<span data-ttu-id="db65b-128">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="db65b-128">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="db65b-129">Активизирует исключение</span><span class="sxs-lookup"><span data-stu-id="db65b-129">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db65b-130">Пример</span><span class="sxs-lookup"><span data-stu-id="db65b-130">Example</span></span>  

 <span data-ttu-id="db65b-131">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор OFTYPE возвращает коллекцию объектов OnsiteCourse из коллекции объектов Course.</span><span class="sxs-lookup"><span data-stu-id="db65b-131">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="db65b-132">Запрос основан на [модели School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db65b-132">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="db65b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="db65b-133">See also</span></span>

- [<span data-ttu-id="db65b-134">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="db65b-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
