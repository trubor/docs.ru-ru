---
description: 'Дополнительные сведения: CAST (Entity SQL)'
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: f6a90c0ec2557391c2da6e46511a020f90d32ab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739486"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="4a483-103">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4a483-103">CAST (Entity SQL)</span></span>

<span data-ttu-id="4a483-104">Преобразует выражение из одного типа данных в другой.</span><span class="sxs-lookup"><span data-stu-id="4a483-104">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a483-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a483-105">Syntax</span></span>  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a483-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="4a483-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4a483-107">Любое допустимое выражение, которое можно преобразовать в `data_type`.</span><span class="sxs-lookup"><span data-stu-id="4a483-107">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="4a483-108">Целевой тип данных, предоставляемый системой.</span><span class="sxs-lookup"><span data-stu-id="4a483-108">The target system-supplied data type.</span></span> <span data-ttu-id="4a483-109">Это должен быть (скалярный) тип-примитив.</span><span class="sxs-lookup"><span data-stu-id="4a483-109">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="4a483-110">Какой тип `data_type` будет использован, зависит от области запроса.</span><span class="sxs-lookup"><span data-stu-id="4a483-110">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="4a483-111">Если запрос выполняется с командой <xref:System.Data.EntityClient.EntityCommand>, то типом данных будет тип, определенный в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="4a483-111">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="4a483-112">Для получения дополнительной информации см. [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="4a483-112">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span> <span data-ttu-id="4a483-113">Если запрос выполняется командой <xref:System.Data.Objects.ObjectQuery%601>, то этим типом данных будет тип CLR.</span><span class="sxs-lookup"><span data-stu-id="4a483-113">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a483-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4a483-114">Return Value</span></span>  

 <span data-ttu-id="4a483-115">Возвращает значение такого же типа, что и аргумент `data_type`.</span><span class="sxs-lookup"><span data-stu-id="4a483-115">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a483-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a483-116">Remarks</span></span>  

 <span data-ttu-id="4a483-117">Выражение приведения имеет аналогичную семантику выражения Transact-SQL CONVERT.</span><span class="sxs-lookup"><span data-stu-id="4a483-117">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="4a483-118">Выражение явного приведения используется для преобразования значения одного типа в значение другого типа.</span><span class="sxs-lookup"><span data-stu-id="4a483-118">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```csharp
CAST( e as T )  
```  
  
 <span data-ttu-id="4a483-119">Если «e» имеет некий тип S, а S можно преобразовать в T, то приведенное выше выражение является допустимым выражением явного приведения.</span><span class="sxs-lookup"><span data-stu-id="4a483-119">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="4a483-120">Т должно иметь (скалярный) тип-примитив.</span><span class="sxs-lookup"><span data-stu-id="4a483-120">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="4a483-121">При явном приведении к `Edm.Decimal`можно дополнительно указать значения аспектов точности и масштаба.</span><span class="sxs-lookup"><span data-stu-id="4a483-121">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="4a483-122">Если они не заданы явным образом, принимаются значения по умолчанию для точности и масштаба 18 и 0 соответственно.</span><span class="sxs-lookup"><span data-stu-id="4a483-122">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="4a483-123">В частности, для `Decimal`поддерживаются следующие перегрузки:</span><span class="sxs-lookup"><span data-stu-id="4a483-123">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="4a483-124">Использование выражения явного приведения считается явным преобразованием.</span><span class="sxs-lookup"><span data-stu-id="4a483-124">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="4a483-125">При явном преобразовании возможно усечение данных и потеря точности.</span><span class="sxs-lookup"><span data-stu-id="4a483-125">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a483-126">Операция CAST может выполняться только над типами-примитивами и типами элементов перечисления.</span><span class="sxs-lookup"><span data-stu-id="4a483-126">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a483-127">Пример</span><span class="sxs-lookup"><span data-stu-id="4a483-127">Example</span></span>  

 <span data-ttu-id="4a483-128">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор CAST используется для явного приведения выражения одного типа данных к другому.</span><span class="sxs-lookup"><span data-stu-id="4a483-128">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="4a483-129">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="4a483-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4a483-130">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="4a483-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4a483-131">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4a483-131">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="4a483-132">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="4a483-132">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="4a483-133">См. также</span><span class="sxs-lookup"><span data-stu-id="4a483-133">See also</span></span>

- [<span data-ttu-id="4a483-134">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4a483-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
