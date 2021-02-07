---
description: 'Дополнительные сведения: | | НИ (Entity SQL)'
title: '|| (ИЛИ) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 83af0211de1dd86b057237c36312e3ce33a3512a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696338"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="04bef-103">|| (ИЛИ) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="04bef-103">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="04bef-104">Объединяет два выражения типа `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="04bef-104">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bef-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04bef-105">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="04bef-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="04bef-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="04bef-107">Любое допустимое выражение, возвращающее значение типа `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="04bef-107">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04bef-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="04bef-108">Return Value</span></span>  

 <span data-ttu-id="04bef-109">`true` , если любое из условий есть `true`; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="04bef-109">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04bef-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="04bef-110">Remarks</span></span>  

 <span data-ttu-id="04bef-111">OR - это логический оператор [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="04bef-111">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="04bef-112">Он используется только для объединения двух условий.</span><span class="sxs-lookup"><span data-stu-id="04bef-112">It is used to combine two conditions.</span></span> <span data-ttu-id="04bef-113">Если в инструкции используется более одного логического оператора, то операторы OR вычисляются после операторов AND.</span><span class="sxs-lookup"><span data-stu-id="04bef-113">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="04bef-114">Однако порядок выполнения можно изменить с помощью скобок.</span><span class="sxs-lookup"><span data-stu-id="04bef-114">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="04bef-115">Двойные вертикальные черты (&#124;&#124;) имеют те же функциональные возможности, что и оператор OR.</span><span class="sxs-lookup"><span data-stu-id="04bef-115">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="04bef-116">В следующей таблице указаны возможные входные значения и возвращаемые типы.</span><span class="sxs-lookup"><span data-stu-id="04bef-116">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="04bef-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="04bef-117">TRUE</span></span>|<span data-ttu-id="04bef-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="04bef-118">TRUE</span></span>|<span data-ttu-id="04bef-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="04bef-119">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="04bef-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="04bef-120">TRUE</span></span>|<span data-ttu-id="04bef-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="04bef-121">FALSE</span></span>|<span data-ttu-id="04bef-122">NULL</span><span class="sxs-lookup"><span data-stu-id="04bef-122">NULL</span></span>|  
|`NULL`|<span data-ttu-id="04bef-123">TRUE</span><span class="sxs-lookup"><span data-stu-id="04bef-123">TRUE</span></span>|<span data-ttu-id="04bef-124">NULL</span><span class="sxs-lookup"><span data-stu-id="04bef-124">NULL</span></span>|<span data-ttu-id="04bef-125">NULL</span><span class="sxs-lookup"><span data-stu-id="04bef-125">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="04bef-126">Пример</span><span class="sxs-lookup"><span data-stu-id="04bef-126">Example</span></span>  

 <span data-ttu-id="04bef-127">Следующий запрос Entity SQL использует оператор OR, чтобы объединить два выражения типа `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="04bef-127">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="04bef-128">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="04bef-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="04bef-129">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="04bef-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="04bef-130">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="04bef-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="04bef-131">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="04bef-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="04bef-132">См. также</span><span class="sxs-lookup"><span data-stu-id="04bef-132">See also</span></span>

- [<span data-ttu-id="04bef-133">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="04bef-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
