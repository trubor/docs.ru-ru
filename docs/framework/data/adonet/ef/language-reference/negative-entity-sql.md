---
description: 'Дополнительные сведения: (отрицательное значение) (Entity SQL)'
title: '- Отрицатель (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712887"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="36612-103">- (отрицательное) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="36612-103">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="36612-104">Возвращает значение числового выражения с противоположным знаком.</span><span class="sxs-lookup"><span data-stu-id="36612-104">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36612-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36612-105">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="36612-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="36612-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="36612-107">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="36612-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="36612-108">Типы результата</span><span class="sxs-lookup"><span data-stu-id="36612-108">Result Types</span></span>  

 <span data-ttu-id="36612-109">Тип данных `expression`.</span><span class="sxs-lookup"><span data-stu-id="36612-109">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36612-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="36612-110">Remarks</span></span>  

 <span data-ttu-id="36612-111">Если аргумент `expression` имеет тип данных без знака, то типом результата становится тип данных со знаком, который в наибольшей степени связан с типом аргумента `expression`.</span><span class="sxs-lookup"><span data-stu-id="36612-111">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="36612-112">Например, если аргумент `expression` имеет тип Byte, то возвращается значение типа Int16.</span><span class="sxs-lookup"><span data-stu-id="36612-112">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36612-113">Пример</span><span class="sxs-lookup"><span data-stu-id="36612-113">Example</span></span>  

 <span data-ttu-id="36612-114">В следующем запросе Entity SQL используется арифметический оператор «-» для возврата значения числового выражения с противоположным знаком.</span><span class="sxs-lookup"><span data-stu-id="36612-114">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="36612-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="36612-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="36612-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="36612-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="36612-117">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="36612-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="36612-118">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="36612-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="36612-119">См. также</span><span class="sxs-lookup"><span data-stu-id="36612-119">See also</span></span>

- [<span data-ttu-id="36612-120">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="36612-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
