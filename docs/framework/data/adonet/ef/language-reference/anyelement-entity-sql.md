---
description: 'Дополнительные сведения о: ANYELEMENT (Entity SQL)'
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 3330c1b0bed69084bc83c5a689762ff529539d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697157"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="43b89-103">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="43b89-103">ANYELEMENT (Entity SQL)</span></span>

<span data-ttu-id="43b89-104">Извлекает элемент из многозначной коллекции.</span><span class="sxs-lookup"><span data-stu-id="43b89-104">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b89-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="43b89-105">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="43b89-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="43b89-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="43b89-107">Любое допустимое выражение запроса, возвращающее коллекцию, из которой извлекается элемент.</span><span class="sxs-lookup"><span data-stu-id="43b89-107">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43b89-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="43b89-108">Return Value</span></span>  

 <span data-ttu-id="43b89-109">Единственный элемент коллекции или произвольный элемент, если в коллекции их несколько. Если коллекция пустая, возвращается значение `null`.</span><span class="sxs-lookup"><span data-stu-id="43b89-109">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="43b89-110">Если `collection` является коллекцией типа `Collection<T>` , то `ANYELEMENT(collection)` является допустимым выражением, результатом которого является экземпляр типа `T` .</span><span class="sxs-lookup"><span data-stu-id="43b89-110">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43b89-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="43b89-111">Remarks</span></span>  

 <span data-ttu-id="43b89-112">Оператор ANYELEMENT извлекает произвольный элемент из многозначной коллекции.</span><span class="sxs-lookup"><span data-stu-id="43b89-112">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="43b89-113">Например, в следующем примере извлекается один элемент из набора `Customers`.</span><span class="sxs-lookup"><span data-stu-id="43b89-113">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="43b89-114">Пример</span><span class="sxs-lookup"><span data-stu-id="43b89-114">Example</span></span>  

 <span data-ttu-id="43b89-115">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор ANYELEMENT используется для извлечения элемента из многозначной коллекции.</span><span class="sxs-lookup"><span data-stu-id="43b89-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="43b89-116">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="43b89-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="43b89-117">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="43b89-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="43b89-118">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="43b89-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="43b89-119">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="43b89-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="43b89-120">См. также</span><span class="sxs-lookup"><span data-stu-id="43b89-120">See also</span></span>

- [<span data-ttu-id="43b89-121">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="43b89-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="43b89-122">Допускающие значения NULL структурированные типы</span><span class="sxs-lookup"><span data-stu-id="43b89-122">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
