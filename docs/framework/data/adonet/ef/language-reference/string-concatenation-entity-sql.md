---
description: 'Дополнительные сведения о: + (объединение строк) (Entity SQL)'
title: + (Объединение строк) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 7b6aac5b865e2127bb23446248e20d83ea3c7ea3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791846"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="04f18-103">+ (объединение строк) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="04f18-103">+ (String Concatenation) (Entity SQL)</span></span>

<span data-ttu-id="04f18-104">Объединяет две строки.</span><span class="sxs-lookup"><span data-stu-id="04f18-104">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f18-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04f18-105">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="04f18-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="04f18-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="04f18-107">Любое допустимое выражение с типом данных EDM.String.</span><span class="sxs-lookup"><span data-stu-id="04f18-107">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="04f18-108">Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения.</span><span class="sxs-lookup"><span data-stu-id="04f18-108">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="04f18-109">Типы результата</span><span class="sxs-lookup"><span data-stu-id="04f18-109">Result Types</span></span>  

 <span data-ttu-id="04f18-110">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="04f18-110">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="04f18-111">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="04f18-111">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04f18-112">Пример</span><span class="sxs-lookup"><span data-stu-id="04f18-112">Example</span></span>  

 <span data-ttu-id="04f18-113">В следующем запросе Entity SQL с помощью оператора «+» объединяются две строки.</span><span class="sxs-lookup"><span data-stu-id="04f18-113">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="04f18-114">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="04f18-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="04f18-115">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="04f18-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="04f18-116">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="04f18-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="04f18-117">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="04f18-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="04f18-118">См. также</span><span class="sxs-lookup"><span data-stu-id="04f18-118">See also</span></span>

- [<span data-ttu-id="04f18-119">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="04f18-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="04f18-120">Типы концептуальной модели (CSDL)</span><span class="sxs-lookup"><span data-stu-id="04f18-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
