---
description: 'Дополнительные сведения: определения типов (Entity SQL)'
title: Определения типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: e5a66ed9ea456733bab9c68d96ef5c176dad5651
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673418"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="7009c-103">Определения типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7009c-103">Type Definitions (Entity SQL)</span></span>

<span data-ttu-id="7009c-104">Определение типа используется в операторе объявления встраиваемой функции [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7009c-104">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7009c-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="7009c-105">Remarks</span></span>  

 <span data-ttu-id="7009c-106">Оператор объявления для встроенной функции состоит из ключевого слова [Function](function-entity-sql.md) , за которым следует идентификатор, представляющий имя функции (например, "мявг"), за которым следует список определений параметров в круглых скобках (например, "коллекция взносов (десятичное число)").</span><span class="sxs-lookup"><span data-stu-id="7009c-106">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="7009c-107">Список определений параметров содержит ноль или более определений параметров.</span><span class="sxs-lookup"><span data-stu-id="7009c-107">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="7009c-108">Каждое определение параметра состоит из идентификатора (имя параметра для функции, например «dues»), за которым следует определение типа (например, «Collection(Decimal)»).</span><span class="sxs-lookup"><span data-stu-id="7009c-108">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="7009c-109">Определения типов могут представлять:</span><span class="sxs-lookup"><span data-stu-id="7009c-109">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="7009c-110">Тип идентификатора (например, «Int32» или «AdventureWorks.Order»).</span><span class="sxs-lookup"><span data-stu-id="7009c-110">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="7009c-111">Ключевое слово `COLLECTION`, за которым следует определение другого типа в скобках (например, «Collection(AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="7009c-111">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="7009c-112">Ключевое слово ROW, за которым следует список определений свойств в скобках (например, «Row(x AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="7009c-112">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="7009c-113">Определения свойств имеют формат, например " `identifier type_definition` , `identifier type_definition` ,...".</span><span class="sxs-lookup"><span data-stu-id="7009c-113">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="7009c-114">Ключевое слово REF, за которым следует тип идентификатора в скобках (например, «Ref(AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="7009c-114">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="7009c-115">Для оператора определения типа REF требуется присутствие типа сущности в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="7009c-115">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="7009c-116">В качестве аргумента нельзя указать тип-примитив.</span><span class="sxs-lookup"><span data-stu-id="7009c-116">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="7009c-117">Определения типов также можно вкладывать друг в друга (например, «Collection(Row(x Ref(AdventureWorks.Order)))»).</span><span class="sxs-lookup"><span data-stu-id="7009c-117">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="7009c-118">Определения типов имеют следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="7009c-118">The type definition options are:</span></span>  
  
- <span data-ttu-id="7009c-119">`IdentifierName supported_type`или</span><span class="sxs-lookup"><span data-stu-id="7009c-119">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="7009c-120">`IdentifierName` COLLECTION(`type_definition`), или</span><span class="sxs-lookup"><span data-stu-id="7009c-120">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="7009c-121">`IdentifierName` ROW(`property_definition`), или</span><span class="sxs-lookup"><span data-stu-id="7009c-121">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="7009c-122">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="7009c-122">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="7009c-123">Параметр, определяющий свойство, - `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="7009c-123">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="7009c-124">Поддерживаются все типы в текущем пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="7009c-124">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="7009c-125">Включаются как типы-примитивы, так и типы сущностей.</span><span class="sxs-lookup"><span data-stu-id="7009c-125">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="7009c-126">В поддерживаемые типы сущностей входят только типы сущностей текущего пространства имен.</span><span class="sxs-lookup"><span data-stu-id="7009c-126">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="7009c-127">Сюда не входят типы-примитивы.</span><span class="sxs-lookup"><span data-stu-id="7009c-127">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7009c-128">Примеры</span><span class="sxs-lookup"><span data-stu-id="7009c-128">Examples</span></span>  

 <span data-ttu-id="7009c-129">Ниже приводится пример простого определения типа.</span><span class="sxs-lookup"><span data-stu-id="7009c-129">The following is an example of a simple type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="7009c-130">Ниже приводится пример определения типа COLLECTION.</span><span class="sxs-lookup"><span data-stu-id="7009c-130">The following is an example of a COLLECTION type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="7009c-131">Ниже приводится пример определения типа ROW.</span><span class="sxs-lookup"><span data-stu-id="7009c-131">The following is an example of a ROW type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="7009c-132">Ниже приводится пример определения типа REF.</span><span class="sxs-lookup"><span data-stu-id="7009c-132">The following is an example of a REF type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="7009c-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7009c-133">See also</span></span>

- [<span data-ttu-id="7009c-134">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7009c-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="7009c-135">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7009c-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
