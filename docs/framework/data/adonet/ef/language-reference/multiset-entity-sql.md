---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: abdcce0e98c924052e07b9001d7dd92051c13747
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427036"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="d9e5e-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d9e5e-102">MULTISET (Entity SQL)</span></span>

<span data-ttu-id="d9e5e-103">Создает экземпляр мультинабора из списка значений.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="d9e5e-104">Все значения конструктора MULTISET должны принадлежать совместимому типу `T`.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="d9e5e-105">Применение пустых конструкторов мультинаборов не допускается.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-105">Empty multiset constructors are not allowed.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9e5e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9e5e-106">Syntax</span></span>

```sql
MULTISET ( expression [{, expression }] )
-- or
{ expression [{, expression }] }
```

## <a name="arguments"></a><span data-ttu-id="d9e5e-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d9e5e-107">Arguments</span></span>

`expression`  
 <span data-ttu-id="d9e5e-108">Любой допустимый список значений.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-108">Any valid list of values.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9e5e-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9e5e-109">Return Value</span></span>

<span data-ttu-id="d9e5e-110">Коллекция МУЛЬТИНАБОРов типов \<T> .</span><span class="sxs-lookup"><span data-stu-id="d9e5e-110">A collection of type MULTISET\<T>.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9e5e-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9e5e-111">Remarks</span></span>

<!-- markdownlint-disable DOCSMD001 -->

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="d9e5e-112">предоставляет три типа конструкторов: конструкторы строк, конструкторы объектов и конструкторы мультинаборов (или коллекций).</span><span class="sxs-lookup"><span data-stu-id="d9e5e-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="d9e5e-113">Дополнительные сведения см. в разделе [Создание типов](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d9e5e-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>

<span data-ttu-id="d9e5e-114">Конструктор мультинаборов создает экземпляр мультинабора из списка значений.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="d9e5e-115">Все значения конструктора MULTISET должны принадлежать совместимому типу.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-115">All the values in the constructor must be of a compatible type.</span></span>

<span data-ttu-id="d9e5e-116">Например, следующее выражение создает мультинабор целых чисел.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-116">For example, the following expression creates a multiset of integers.</span></span>

`MULTISET(1, 2, 3)`

`{1, 2, 3}`

> [!NOTE]
> <span data-ttu-id="d9e5e-117">Вложенные литералы мультинабора поддерживаются только в том случае, если в Мультинаборе с несколькими элементами есть один элемент мультинабора; Например, `{{1, 2, 3}}` .</span><span class="sxs-lookup"><span data-stu-id="d9e5e-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="d9e5e-118">Когда же мультинабор-упаковщик имеет несколько элементов мультинабора (например, `{{1, 2}, {3, 4}}`), вложенные литералы мультинаборов не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>

## <a name="example"></a><span data-ttu-id="d9e5e-119">Пример</span><span class="sxs-lookup"><span data-stu-id="d9e5e-119">Example</span></span>

<span data-ttu-id="d9e5e-120">В следующем запросе Entity SQL оператор MULTISET используется для создания экземпляра мультинабора из списка значений.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="d9e5e-121">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d9e5e-122">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d9e5e-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="d9e5e-123">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d9e5e-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="d9e5e-124">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="d9e5e-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

[!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]

## <a name="see-also"></a><span data-ttu-id="d9e5e-125">См. также статью</span><span class="sxs-lookup"><span data-stu-id="d9e5e-125">See also</span></span>

- [<span data-ttu-id="d9e5e-126">Сборка типов</span><span class="sxs-lookup"><span data-stu-id="d9e5e-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="d9e5e-127">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9e5e-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
