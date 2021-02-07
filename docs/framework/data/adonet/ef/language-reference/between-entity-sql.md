---
description: 'Дополнительные сведения о: между (Entity SQL)'
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 35ac16e94f2e55f6a0f76591daf0f91f9708aa53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697118"
---
# <a name="between-entity-sql"></a><span data-ttu-id="adb0e-103">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="adb0e-103">BETWEEN (Entity SQL)</span></span>

<span data-ttu-id="adb0e-104">Определяет, находится ли значение выражения в указанном диапазоне.</span><span class="sxs-lookup"><span data-stu-id="adb0e-104">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="adb0e-105">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Выражение between имеет те же функциональные возможности, что и Transact-SQL между выражениями.</span><span class="sxs-lookup"><span data-stu-id="adb0e-105">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb0e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="adb0e-106">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="adb0e-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="adb0e-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="adb0e-108">Любое допустимое выражение для проверки на принадлежность диапазону в пределах от `begin_expression` до `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-108">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="adb0e-109">Аргумент `expression` должен быть того же типа данных, что и аргументы `begin_expression` и `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-109">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="adb0e-110">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="adb0e-110">Any valid expression.</span></span> <span data-ttu-id="adb0e-111">Аргумент `begin_expression` должен быть того же типа данных, что и аргументы `expression` и `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-111">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="adb0e-112">Значение `begin_expression` должно быть меньше `end_expression`, иначе возвращаемое значение будет инвертировано.</span><span class="sxs-lookup"><span data-stu-id="adb0e-112">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="adb0e-113">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="adb0e-113">Any valid expression.</span></span> <span data-ttu-id="adb0e-114">Аргумент `end_expression` должен быть того же типа данных, что и аргументы `expression` и `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-114">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="adb0e-115">NOT</span><span class="sxs-lookup"><span data-stu-id="adb0e-115">NOT</span></span>  
 <span data-ttu-id="adb0e-116">Указывает, что результат оператора BETWEEN должен быть инвертирован.</span><span class="sxs-lookup"><span data-stu-id="adb0e-116">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="adb0e-117">AND</span><span class="sxs-lookup"><span data-stu-id="adb0e-117">AND</span></span>  
 <span data-ttu-id="adb0e-118">Играет роль местозаполнителя и указывает на то, что значение выражения `expression` должно находиться в пределах заданных значений аргументов `begin_expression` и `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-118">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adb0e-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="adb0e-119">Return Value</span></span>  

 <span data-ttu-id="adb0e-120">Значение `true`, если аргумент `expression` находится в диапазоне между `begin_expression` и `end_expression`; в противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-120">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="adb0e-121">Возвращает `null`, если `expression` равно `null` или если `begin_expression` или `end_expression` равно `null`.</span><span class="sxs-lookup"><span data-stu-id="adb0e-121">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adb0e-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="adb0e-122">Remarks</span></span>  

 <span data-ttu-id="adb0e-123">Чтобы указать эксклюзивный диапазон, используйте операторы "больше" (>) и "меньше" (<), а не между ними.</span><span class="sxs-lookup"><span data-stu-id="adb0e-123">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb0e-124">Пример</span><span class="sxs-lookup"><span data-stu-id="adb0e-124">Example</span></span>  

 <span data-ttu-id="adb0e-125">В следующем запросе Entity SQL оператор BETWEEN определяет, входит ли значение выражения в указанный диапазон.</span><span class="sxs-lookup"><span data-stu-id="adb0e-125">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="adb0e-126">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="adb0e-126">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="adb0e-127">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="adb0e-127">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="adb0e-128">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="adb0e-128">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="adb0e-129">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="adb0e-129">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="adb0e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="adb0e-130">See also</span></span>

- [<span data-ttu-id="adb0e-131">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="adb0e-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
