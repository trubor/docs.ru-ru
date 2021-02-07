---
description: 'Дополнительные сведения: ROW (Entity SQL)'
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2d0bcf3c5be8ef3b67e170af5159ae7dd8744630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739278"
---
# <a name="row-entity-sql"></a><span data-ttu-id="6b115-103">ROW (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6b115-103">ROW (Entity SQL)</span></span>

<span data-ttu-id="6b115-104">Создает анонимные структурно типизированные записи из одного или нескольких значений.</span><span class="sxs-lookup"><span data-stu-id="6b115-104">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b115-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b115-105">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b115-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="6b115-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6b115-107">Любое допустимое выражение запроса, которое возвращает значение для создания в типе строки.</span><span class="sxs-lookup"><span data-stu-id="6b115-107">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="6b115-108">Определяет псевдоним для значения, указанного в типе строки.</span><span class="sxs-lookup"><span data-stu-id="6b115-108">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="6b115-109">Если псевдоним не указан, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается сформировать его на основе правил создания псевдонимов [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6b115-109">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b115-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6b115-110">Return Value</span></span>  

 <span data-ttu-id="6b115-111">Тип строки.</span><span class="sxs-lookup"><span data-stu-id="6b115-111">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b115-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="6b115-112">Remarks</span></span>  

 <span data-ttu-id="6b115-113">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] конструкторы строк можно использовать для создания анонимных структурно типизированных записей из одного или нескольких значений.</span><span class="sxs-lookup"><span data-stu-id="6b115-113">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="6b115-114">Итоговый тип конструктора строк является типом строки, типы полей которого соответствуют типам значений, которые использовались для создания этой строки.</span><span class="sxs-lookup"><span data-stu-id="6b115-114">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="6b115-115">Например, следующее выражение создает значение типа `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="6b115-115">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="6b115-116">Если в конструкторе строк не указан псевдоним для выражения, то платформа Entity Framework попытается сформировать его.</span><span class="sxs-lookup"><span data-stu-id="6b115-116">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="6b115-117">Дополнительные сведения см. в разделе «Правила присвоения псевдонимов» темы [Идентификаторы](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6b115-117">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="6b115-118">В конструкторе строк псевдонимы присваиваются выражениям по следующим правилам.</span><span class="sxs-lookup"><span data-stu-id="6b115-118">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="6b115-119">Выражение в конструкторе строк не может ссылаться на другие псевдонимы в этом же конструкторе.</span><span class="sxs-lookup"><span data-stu-id="6b115-119">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="6b115-120">Два выражения в одном конструкторе строк не могут иметь одинаковый псевдоним.</span><span class="sxs-lookup"><span data-stu-id="6b115-120">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="6b115-121">Дополнительные сведения о конструкторах запросов см. в разделе [Создание типов](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6b115-121">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b115-122">Пример</span><span class="sxs-lookup"><span data-stu-id="6b115-122">Example</span></span>  

 <span data-ttu-id="6b115-123">В следующем запросе Entity SQL оператор ROW используется для создания анонимных структурно типизированных записей.</span><span class="sxs-lookup"><span data-stu-id="6b115-123">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="6b115-124">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="6b115-124">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6b115-125">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="6b115-125">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6b115-126">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6b115-126">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6b115-127">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="6b115-127">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="6b115-128">См. также</span><span class="sxs-lookup"><span data-stu-id="6b115-128">See also</span></span>

- [<span data-ttu-id="6b115-129">Сборка типов</span><span class="sxs-lookup"><span data-stu-id="6b115-129">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="6b115-130">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6b115-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6b115-131">Определения типов</span><span class="sxs-lookup"><span data-stu-id="6b115-131">Type Definitions</span></span>](type-definitions-entity-sql.md)
