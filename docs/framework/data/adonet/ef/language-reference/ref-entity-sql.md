---
description: 'Дополнительные сведения: REF (Entity SQL)'
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05f87ce8027e8e095722eb13d39f3f13d56f6faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802064"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="d13fa-103">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d13fa-103">REF (Entity SQL)</span></span>

<span data-ttu-id="d13fa-104">Возвращает ссылку на экземпляр сущности.</span><span class="sxs-lookup"><span data-stu-id="d13fa-104">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d13fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d13fa-105">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="d13fa-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d13fa-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="d13fa-107">Любое допустимое выражение, результатом которого является экземпляр типа сущности.</span><span class="sxs-lookup"><span data-stu-id="d13fa-107">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d13fa-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d13fa-108">Return Value</span></span>  

 <span data-ttu-id="d13fa-109">Ссылка на указанный экземпляр сущности.</span><span class="sxs-lookup"><span data-stu-id="d13fa-109">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d13fa-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d13fa-110">Remarks</span></span>  

 <span data-ttu-id="d13fa-111">Ссылка на сущность состоит из ключа сущности и имени набора сущности.</span><span class="sxs-lookup"><span data-stu-id="d13fa-111">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="d13fa-112">На одном и том же типе сущности могут быть основаны разные наборы сущностей, поэтому какой-то конкретный ключ сущности может появляться в нескольких наборах сущностей.</span><span class="sxs-lookup"><span data-stu-id="d13fa-112">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="d13fa-113">Но ссылка на сущность всегда является уникальной.</span><span class="sxs-lookup"><span data-stu-id="d13fa-113">However, an entity reference is always unique.</span></span> <span data-ttu-id="d13fa-114">Если входное выражение представляет сохраняемую сущность, то будет возвращена ссылка на эту сущность.</span><span class="sxs-lookup"><span data-stu-id="d13fa-114">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="d13fa-115">Если входное выражение не является сохраняемой сущностью, то возвращается ссылка null.</span><span class="sxs-lookup"><span data-stu-id="d13fa-115">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="d13fa-116">Если доступ к свойству сущности производится через оператор получения свойства (.), то ссылка автоматически разыменовывается.</span><span class="sxs-lookup"><span data-stu-id="d13fa-116">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d13fa-117">Пример</span><span class="sxs-lookup"><span data-stu-id="d13fa-117">Example</span></span>  

 <span data-ttu-id="d13fa-118">В следующем запросе Entity SQL используется оператор REF в целях получения ссылки для входного аргумента сущности.</span><span class="sxs-lookup"><span data-stu-id="d13fa-118">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="d13fa-119">Тот же запрос разыменовывает ссылку, поскольку для доступа к свойству сущности Product используется оператор получения свойства (.).</span><span class="sxs-lookup"><span data-stu-id="d13fa-119">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="d13fa-120">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="d13fa-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d13fa-121">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d13fa-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d13fa-122">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d13fa-122">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="d13fa-123">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="d13fa-123">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="d13fa-124">См. также</span><span class="sxs-lookup"><span data-stu-id="d13fa-124">See also</span></span>

- [<span data-ttu-id="d13fa-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="d13fa-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="d13fa-126">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="d13fa-126">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="d13fa-127">KEY</span><span class="sxs-lookup"><span data-stu-id="d13fa-127">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="d13fa-128">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d13fa-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="d13fa-129">Определения типов</span><span class="sxs-lookup"><span data-stu-id="d13fa-129">Type Definitions</span></span>](type-definitions-entity-sql.md)
